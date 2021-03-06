# Time to Live (TTL)

В разделе описан принцип работы TTL, его ограничения, а также приведены примеры команд и фрагменты кода, с помощью которых можно включить, настроить и выключить TTL.

## Принцип работы {#how-it-works}

{{ ydb-short-name }} позволяет указать для таблицы колонку (TTL-колонка), значения которой будут использоваться для определения времени жизни строк. TTL автоматически удаляет из таблицы строки, когда проходит указанное количество секунд от времени, записанного в TTL-колонку.

{% note warning %}

Строка с `NULL` в TTL-колонке никогда не будет удалена.

{% endnote %}

Момент времени, когда строка таблицы может быть удалена, определяется по следующей формуле:

```
expiration_time = valueof(ttl_column) + expire_after_seconds
```

{% note info %}

Не гарантируется, что удаление произойдет именно в `expiration_time` — оно может случиться позже. Если важно исключить из выборки логически устаревшие, но пока ещё физически неудалённые строки, нужно использовать фильтрацию уровня запроса.

{% endnote %}

Непосредственно удалением данных занимается фоновая операция удаления — *Background Removal Operation* (*BRO*), состоящая из 2 стадий:
1. Проверка значений в TTL-колонке.
2. Удаление устаревших данных.

*BRO* обладает следующими свойствами:
* Единицей параллельности является [шард таблицы](./datamodel.md#sharding).
* Для таблиц без [вторичных индексов](./secondary_indexes.md) осуществляется "слепое" удаление. То есть, если между стадиями 1 и 2 значение в TTL-колонке модифицируется (например, запросом `UPDATE`), изменившееся значение не будет проверено повторно.
* Для таблиц со вторичными индексами стадия удаления является [распределённой транзакцией](./transactions.md#distributed-tx).

## Гарантии {#guarantees}

* В каждый момент времени *BRO* запущен не более, чем в 1 экземпляре на таблицу.
* *BRO* запускается не чаще одного раза в час для одного и того же шарда.
* Для таблиц со вторичными индексами гарантируется согласованность данных.

## Ограничения {#restrictions}

* TTL-колонка должна быть одного из следующих типов:
  - `Date`;
  - `Datetime`;
  - `Timestamp`.
* Нельзя указать несколько TTL-колонок.
* Нельзя удалить TTL-колонку. Если это всё же требуется, сначала нужно [выключить TTL](#disable) на таблице.

## Настройка {#setting}

Управление настройками TTL в настоящий момент возможно с использованием:
* [Консольного клиента {{ ydb-short-name }}](../quickstart/examples-ydb-cli.md).
* [{{ ydb-short-name }} Python SDK](https://github.com/yandex-cloud/ydb-python-sdk).

### Включение TTL для существующей таблицы {#enable-on-existent-table}

В приведённом ниже примере строки таблицы `mytable` будут удаляться спустя час после наступления времени, записанного в колонке `created_at`:

{% list tabs %}

- CLI
  ```bash
  $ ydb -e <endpoint> -d <database> table ttl set --column created_at --expire-after 3600 mytable
  ```


- Python
  ```python
  session.alter_table('mytable', set_ttl_settings=ydb.TtlSettings().with_date_type_column('created_at', 3600))
  ```

{% endlist %}

### Включение TTL для вновь создаваемой таблицы {#enable-for-new-table}

Для вновь создаваемой таблицы можно передать настройки TTL вместе с её описанием:

{% list tabs %}


- Python
  ```python
  session.create_table(
      'mytable',
      ydb.TableDescription()
      .with_column(ydb.Column('id', ydb.OptionalType(ydb.DataType.Uint64)))
      .with_column(ydb.Column('expire_at', ydb.OptionalType(ydb.DataType.Timestamp)))
      .with_primary_key('id')
      .with_ttl(ydb.TtlSettings().with_date_type_column('expire_at'))
  )
  ```

{% endlist %}

### Выключение TTL {#disable}

{% list tabs %}

- CLI
  ```bash
  $ ydb -e <endpoint> -d <database> table ttl drop mytable
  ```


- Python
  ```python
  session.alter_table('mytable', drop_ttl_settings=True)
  ```

{% endlist %}
