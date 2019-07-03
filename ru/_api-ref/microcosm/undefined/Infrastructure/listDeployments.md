---
editable: false
---

# Метод listDeployments

 

 
## HTTP-запрос {#https-request}
```
GET undefined/microcosm/v1/infrastructures/{infrastructureId}/deployments
```
 
## Path-параметры {#path_params}
 
Параметр | Описание
--- | ---
infrastructureId | Обязательное поле. Максимальная длина строки в символах — 50.
 
## Query-параметры {#query_params}
 
Параметр | Описание
--- | ---
pageSize | Максимальное значение — 1000.
pageToken | Максимальная длина строки в символах — 100.
filter | Максимальная длина строки в символах — 1000.
 
## Ответ {#responses}
**HTTP Code: 200 - OK**

```json 
{
  "deployments": [
    {
      "deploymentId": "string",
      "infrastructureId": "string",
      "deploymentNumber": "string",
      "createdAt": "string",
      "status": "string",
      "deploymentSpec": {
        "resources": [
          {
            "name": "string",
            "dependsOn": [
              "string"
            ],

            // `deployments[].deploymentSpec.resources[]` включает только одно из полей `computeV1Instance`, `computeV1Disk`, `computeV1Image`, `computeV1InstanceGroup`
            "computeV1Instance": {
              "name": "string",
              "description": "string",
              "labels": "object",
              "zoneId": "string",
              "platformId": "string",
              "resources": {
                "memory": "string",
                "cores": "string"
              },
              "metadata": "object",
              "bootDisk": {
                "mode": "string",
                "deviceName": "string",
                "autoDelete": true,

                // `deployments[].deploymentSpec.resources[].computeV1Instance.bootDisk` включает только одно из полей `diskSpec`, `diskId`
                "diskSpec": {
                  "name": "string",
                  "description": "string",
                  "typeId": "string",
                  "zoneId": "string",
                  "size": "string",
                  "labels": "object",

                  // `deployments[].deploymentSpec.resources[].computeV1Instance.bootDisk.diskSpec` включает только одно из полей `sourceImageId`, `sourceSnapshotId`
                  "sourceImageId": "string",
                  "sourceSnapshotId": "string",
                  // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1Instance.bootDisk.diskSpec`

                },
                "diskId": "string",
                // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1Instance.bootDisk`

              },
              "secondaryDisks": [
                {
                  "mode": "string",
                  "deviceName": "string",
                  "autoDelete": true,

                  // `deployments[].deploymentSpec.resources[].computeV1Instance.secondaryDisks[]` включает только одно из полей `diskSpec`, `diskId`
                  "diskSpec": {
                    "name": "string",
                    "description": "string",
                    "typeId": "string",
                    "zoneId": "string",
                    "size": "string",
                    "labels": "object",

                    // `deployments[].deploymentSpec.resources[].computeV1Instance.secondaryDisks[].diskSpec` включает только одно из полей `sourceImageId`, `sourceSnapshotId`
                    "sourceImageId": "string",
                    "sourceSnapshotId": "string",
                    // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1Instance.secondaryDisks[].diskSpec`

                  },
                  "diskId": "string",
                  // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1Instance.secondaryDisks[]`

                }
              ],
              "networkInterfaceSpecs": [
                {
                  "subnetId": "string",
                  "primaryV4AddressSpec": {
                    "address": "string",
                    "ipVersion": "string",
                    "natSpec": {
                      "name": "string",
                      "ipVersion": "string"
                    }
                  }
                }
              ],
              "warmupPeriod": "string",
              "hostname": "string"
            },
            "computeV1Disk": {
              "name": "string",
              "description": "string",
              "typeId": "string",
              "zoneId": "string",
              "size": "string",
              "labels": "object",

              // `deployments[].deploymentSpec.resources[].computeV1Disk` включает только одно из полей `sourceImageId`, `sourceSnapshotId`
              "sourceImageId": "string",
              "sourceSnapshotId": "string",
              // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1Disk`

            },
            "computeV1Image": {
              "name": "string",
              "description": "string",
              "family": "string",
              "minDiskSize": "string",
              "labels": "object",

              // `deployments[].deploymentSpec.resources[].computeV1Image` включает только одно из полей `sourceDiskId`, `sourceSnapshotId`, `sourceUri`
              "sourceDiskId": "string",
              "sourceSnapshotId": "string",
              "sourceUri": "string",
              // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1Image`

            },
            "computeV1InstanceGroup": {
              "name": "string",
              "description": "string",
              "labels": "object",
              "instanceTemplate": {
                "description": "string",
                "labels": "object",
                "platformId": "string",
                "resourcesSpec": {
                  "memory": "string",
                  "cores": "string",
                  "coreFraction": "string"
                },
                "metadata": "object",
                "bootDiskSpec": {
                  "mode": "string",
                  "deviceName": "string",
                  "autoDelete": true,

                  // `deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.bootDiskSpec` включает только одно из полей `diskSpec`, `diskId`
                  "diskSpec": {
                    "name": "string",
                    "description": "string",
                    "typeId": "string",
                    "size": "string",

                    // `deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.bootDiskSpec.diskSpec` включает только одно из полей `imageId`, `snapshotId`
                    "imageId": "string",
                    "snapshotId": "string",
                    // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.bootDiskSpec.diskSpec`

                  },
                  "diskId": "string",
                  // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.bootDiskSpec`

                },
                "secondaryDiskSpecs": [
                  {
                    "mode": "string",
                    "deviceName": "string",
                    "autoDelete": true,

                    // `deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.secondaryDiskSpecs[]` включает только одно из полей `diskSpec`, `diskId`
                    "diskSpec": {
                      "name": "string",
                      "description": "string",
                      "typeId": "string",
                      "size": "string",

                      // `deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.secondaryDiskSpecs[].diskSpec` включает только одно из полей `imageId`, `snapshotId`
                      "imageId": "string",
                      "snapshotId": "string",
                      // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.secondaryDiskSpecs[].diskSpec`

                    },
                    "diskId": "string",
                    // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.secondaryDiskSpecs[]`

                  }
                ],
                "networkInterfaceSpecs": [
                  {
                    "subnetId": "string",
                    "primaryV4AddressSpec": {
                      "address": "string",
                      "oneToOneNatSpec": {
                        "ipVersion": "string"
                      }
                    },
                    "primaryV6AddressSpec": {
                      "address": "string",
                      "oneToOneNatSpec": {
                        "ipVersion": "string"
                      }
                    }
                  }
                ]
              },
              "scalePolicy": {

                // `deployments[].deploymentSpec.resources[].computeV1InstanceGroup.scalePolicy` включает только одно из полей `fixedScale`, `autoScale`
                "fixedScale": {
                  "size": "string"
                },
                "autoScale": {
                  "scope": "string",
                  "measurementDuration": "string",
                  "warmupDuration": "string",
                  "cooldownDuration": "string",
                  "initialSize": "string",
                  "cpuUtilizationRule": {
                    "utilizationTarget": "string"
                  }
                },
                // конец списка возможных полей`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.scalePolicy`

              },
              "deployPolicy": {
                "maxUnavailable": "string",
                "maxDeleting": "string",
                "maxCreating": "string",
                "expansion": "string",
                "zoneByZone": "string",
                "startingDuration": "string"
              },
              "allocationPolicy": {
                "minSize": "string",
                "maxSize": "string",
                "zones": [
                  {
                    "zoneId": "string",
                    "minSize": "string",
                    "maxSize": "string"
                  }
                ]
              }
            },
            // конец списка возможных полей`deployments[].deploymentSpec.resources[]`

          }
        ],
        "variables": [
          {
            "name": "string",
            "defaultValue": "string",
            "description": "string"
          }
        ]
      },
      "deploymentYaml": "string",
      "deploymentTemplateId": "string"
    }
  ],
  "nextPageToken": "string"
}
```

 
Поле | Описание
--- | ---
deployments[] | **object**<br>
deployments[].<br>deploymentId | **string**<br>
deployments[].<br>infrastructureId | **string**<br>
deployments[].<br>deploymentNumber | **string**<br>
deployments[].<br>createdAt | **string** (date-time)<br><p>Строка в формате <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a>.</p> 
deployments[].<br>status | **string**<br>
deployments[].<br>deploymentSpec | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[] | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>name | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>dependsOn[] | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance | **object** <br>`deployments[].deploymentSpec.resources[]` включает только одно из полей `computeV1Instance`, `computeV1Disk`, `computeV1Image`, `computeV1InstanceGroup`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>name | **string**<br><p>Обязательное поле. Значение должно соответствовать регулярному выражению <code>\|[a-z][-a-z0-9]{1,61}[a-z0-9]</code>.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>description | **string**<br><p>Максимальная длина строки в символах — 256.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>labels | **object**<br><p>Не более 64 на ресурс. Длина строки в символах для каждого ключа должна быть от 1 до 63. Каждый ключ должен соответствовать регулярному выражению <code>[a-z][-_0-9a-z]*</code>. Максимальная длина строки в символах для каждого значения — 63. Каждое значение должно соответствовать регулярному выражению <code>[-_0-9a-z]*</code>.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>zoneId | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>platformId | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>resources | **object**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>resources.<br>memory | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>resources.<br>cores | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>metadata | **object**<br><p>Не более 128 на ресурс. Длина строки в символах для каждого ключа должна быть от 1 до 63. Каждый ключ должен соответствовать регулярному выражению <code>[a-z][-_0-9a-z]*</code>. Максимальная длина строки в символах для каждого значения — 262144.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk | **object**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>mode | **string**<br>Обязательное поле.<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>deviceName | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>autoDelete | **boolean** (boolean)<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskSpec | **object** <br>`deployments[].deploymentSpec.resources[].computeV1Instance.bootDisk` включает только одно из полей `diskSpec`, `diskId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskSpec.<br>name | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskSpec.<br>description | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskSpec.<br>typeId | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskSpec.<br>zoneId | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskSpec.<br>size | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskSpec.<br>labels | **object**<br><p>Не более 64 на ресурс. Длина строки в символах для каждого ключа должна быть от 1 до 63. Каждый ключ должен соответствовать регулярному выражению <code>[a-z][-_0-9a-z]*</code>. Максимальная длина строки в символах для каждого значения — 63. Каждое значение должно соответствовать регулярному выражению <code>[-_0-9a-z]*</code>.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskSpec.<br>sourceImageId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Instance.bootDisk.diskSpec` включает только одно из полей `sourceImageId`, `sourceSnapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskSpec.<br>sourceSnapshotId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Instance.bootDisk.diskSpec` включает только одно из полей `sourceImageId`, `sourceSnapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>bootDisk.<br>diskId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Instance.bootDisk` включает только одно из полей `diskSpec`, `diskId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[] | **object**<br><p>Максимальное количество элементов — 3.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>mode | **string**<br>Обязательное поле.<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>deviceName | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>autoDelete | **boolean** (boolean)<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskSpec | **object** <br>`deployments[].deploymentSpec.resources[].computeV1Instance.secondaryDisks[]` включает только одно из полей `diskSpec`, `diskId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskSpec.<br>name | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskSpec.<br>description | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskSpec.<br>typeId | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskSpec.<br>zoneId | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskSpec.<br>size | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskSpec.<br>labels | **object**<br><p>Не более 64 на ресурс. Длина строки в символах для каждого ключа должна быть от 1 до 63. Каждый ключ должен соответствовать регулярному выражению <code>[a-z][-_0-9a-z]*</code>. Максимальная длина строки в символах для каждого значения — 63. Каждое значение должно соответствовать регулярному выражению <code>[-_0-9a-z]*</code>.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskSpec.<br>sourceImageId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Instance.secondaryDisks[].diskSpec` включает только одно из полей `sourceImageId`, `sourceSnapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskSpec.<br>sourceSnapshotId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Instance.secondaryDisks[].diskSpec` включает только одно из полей `sourceImageId`, `sourceSnapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>secondaryDisks[].<br>diskId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Instance.secondaryDisks[]` включает только одно из полей `diskSpec`, `diskId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>networkInterfaceSpecs[] | **object**<br><p>Максимальное количество элементов — 3.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>networkInterfaceSpecs[].<br>subnetId | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec.<br>address | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec.<br>ipVersion | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec.<br>natSpec | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec.<br>natSpec.<br>name | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec.<br>natSpec.<br>ipVersion | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>warmupPeriod | **string**<br><p>Максимальная длина строки в символах — 10.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Instance.<br>hostname | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Disk | **object** <br>`deployments[].deploymentSpec.resources[]` включает только одно из полей `computeV1Instance`, `computeV1Disk`, `computeV1Image`, `computeV1InstanceGroup`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Disk.<br>name | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Disk.<br>description | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Disk.<br>typeId | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Disk.<br>zoneId | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Disk.<br>size | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Disk.<br>labels | **object**<br><p>Не более 64 на ресурс. Длина строки в символах для каждого ключа должна быть от 1 до 63. Каждый ключ должен соответствовать регулярному выражению <code>[a-z][-_0-9a-z]*</code>. Максимальная длина строки в символах для каждого значения — 63. Каждое значение должно соответствовать регулярному выражению <code>[-_0-9a-z]*</code>.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Disk.<br>sourceImageId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Disk` включает только одно из полей `sourceImageId`, `sourceSnapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Disk.<br>sourceSnapshotId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Disk` включает только одно из полей `sourceImageId`, `sourceSnapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Image | **object** <br>`deployments[].deploymentSpec.resources[]` включает только одно из полей `computeV1Instance`, `computeV1Disk`, `computeV1Image`, `computeV1InstanceGroup`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Image.<br>name | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Image.<br>description | **string**<br><p>Максимальная длина строки в символах — 256.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Image.<br>family | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Image.<br>minDiskSize | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Image.<br>labels | **object**<br><p>Не более 64 на ресурс. Длина строки в символах для каждого ключа должна быть от 1 до 63. Каждый ключ должен соответствовать регулярному выражению <code>[a-z][-_0-9a-z]*</code>. Максимальная длина строки в символах для каждого значения — 63. Каждое значение должно соответствовать регулярному выражению <code>[-_0-9a-z]*</code>.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Image.<br>sourceDiskId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Image` включает только одно из полей `sourceDiskId`, `sourceSnapshotId`, `sourceUri`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Image.<br>sourceSnapshotId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Image` включает только одно из полей `sourceDiskId`, `sourceSnapshotId`, `sourceUri`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1Image.<br>sourceUri | **string** <br>`deployments[].deploymentSpec.resources[].computeV1Image` включает только одно из полей `sourceDiskId`, `sourceSnapshotId`, `sourceUri`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup | **object** <br>`deployments[].deploymentSpec.resources[]` включает только одно из полей `computeV1Instance`, `computeV1Disk`, `computeV1Image`, `computeV1InstanceGroup`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>name | **string**<br><p>Обязательное поле. Максимальная длина строки в символах — 100.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>description | **string**<br><p>Максимальная длина строки в символах — 10000.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>labels | **object**<br><p>Не более 64 на ресурс. Длина строки в символах для каждого ключа должна быть от 1 до 63. Каждый ключ должен соответствовать регулярному выражению <code>[a-z][-_0-9a-z]*</code>. Максимальная длина строки в символах для каждого значения — 63. Каждое значение должно соответствовать регулярному выражению <code>[-_0-9a-z]*</code>.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate | **object**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>description | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>labels | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>platformId | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>resourcesSpec | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>resourcesSpec.<br>memory | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>resourcesSpec.<br>cores | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>resourcesSpec.<br>coreFraction | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>metadata | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>mode | **string**<br>Обязательное поле.<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>deviceName | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>autoDelete | **boolean** (boolean)<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>diskSpec | **object** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.bootDiskSpec` включает только одно из полей `diskSpec`, `diskId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>diskSpec.<br>name | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>diskSpec.<br>description | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>diskSpec.<br>typeId | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>diskSpec.<br>size | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>diskSpec.<br>imageId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.bootDiskSpec.diskSpec` включает только одно из полей `imageId`, `snapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>diskSpec.<br>snapshotId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.bootDiskSpec.diskSpec` включает только одно из полей `imageId`, `snapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>bootDiskSpec.<br>diskId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.bootDiskSpec` включает только одно из полей `diskSpec`, `diskId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[] | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>mode | **string**<br>Обязательное поле.<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>deviceName | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>autoDelete | **boolean** (boolean)<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>diskSpec | **object** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.secondaryDiskSpecs[]` включает только одно из полей `diskSpec`, `diskId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>diskSpec.<br>name | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>diskSpec.<br>description | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>diskSpec.<br>typeId | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>diskSpec.<br>size | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>diskSpec.<br>imageId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.secondaryDiskSpecs[].diskSpec` включает только одно из полей `imageId`, `snapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>diskSpec.<br>snapshotId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.secondaryDiskSpecs[].diskSpec` включает только одно из полей `imageId`, `snapshotId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>secondaryDiskSpecs[].<br>diskId | **string** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.instanceTemplate.secondaryDiskSpecs[]` включает только одно из полей `diskSpec`, `diskId`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[] | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[].<br>subnetId | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec.<br>address | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec.<br>oneToOneNatSpec | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[].<br>primaryV4AddressSpec.<br>oneToOneNatSpec.<br>ipVersion | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[].<br>primaryV6AddressSpec | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[].<br>primaryV6AddressSpec.<br>address | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[].<br>primaryV6AddressSpec.<br>oneToOneNatSpec | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>instanceTemplate.<br>networkInterfaceSpecs[].<br>primaryV6AddressSpec.<br>oneToOneNatSpec.<br>ipVersion | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy | **object**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>fixedScale | **object** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.scalePolicy` включает только одно из полей `fixedScale`, `autoScale`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>fixedScale.<br>size | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>autoScale | **object** <br>`deployments[].deploymentSpec.resources[].computeV1InstanceGroup.scalePolicy` включает только одно из полей `fixedScale`, `autoScale`<br><br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>autoScale.<br>scope | **string**<br><p>Обязательное поле.</p> <ul> <li>ZONE: Autoscaling works for each zone independently, allocation_policy zones/regions weights can be violated.</li> <li>REGION: Autoscaling works for each region independently, allocation_policy regions weights can be violated, zones' weights are preserved.</li> </ul> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>autoScale.<br>measurementDuration | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>autoScale.<br>warmupDuration | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>autoScale.<br>cooldownDuration | **string**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>autoScale.<br>initialSize | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>autoScale.<br>cpuUtilizationRule | **object**<br>
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>scalePolicy.<br>autoScale.<br>cpuUtilizationRule.<br>utilizationTarget | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>deployPolicy | **object**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>deployPolicy.<br>maxUnavailable | **string**<br><p>How many instances can be unavailable at the same time during update process. If expansion is not specified or set to zero, max_unavailable must be set to non-zero value.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>deployPolicy.<br>maxDeleting | **string**<br><p>How many instances can be in DELETING state at the same time during update process. 0 means unlimited</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>deployPolicy.<br>maxCreating | **string**<br><p>How many instances can be in DEPLOYING state at the same time during update process. 0 means unlimited</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>deployPolicy.<br>expansion | **string**<br><p>How many temporary instances can be created during update process. If max_unavailable is not specified or set to zero, expansion must be set to non-zero value.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>deployPolicy.<br>zoneByZone | **string**<br><p>Experimental. Internal use only! True - next zone is deployed strictly after previous zone is completely deployed. False - all zones are deployed at the same time.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>deployPolicy.<br>startingDuration | **string**<br><p>Just deployed instance will be in STARTING state at leaast this time. It may last longer if a health-check present and not healthy at the end of this duration.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>allocationPolicy | **object**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>allocationPolicy.<br>minSize | **string**<br><p>lower limit for sum of instances in all zones.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>allocationPolicy.<br>maxSize | **string**<br><p>upper limit for sum of instances in all zones. 0 means maximum limit = 1000.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>allocationPolicy.<br>zones[] | **object**<br><p>Обязательное поле. Количество элементов должно находиться в диапазоне от 1 до 3.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>allocationPolicy.<br>zones[].<br>zoneId | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>allocationPolicy.<br>zones[].<br>minSize | **string**<br><p>Optional bound for min number of instances in the zone.</p> 
deployments[].<br>deploymentSpec.<br>resources[].<br>computeV1InstanceGroup.<br>allocationPolicy.<br>zones[].<br>maxSize | **string**<br><p>Optional bound for max number of instances in the zone. 0 means maximum limit = 1000.</p> 
deployments[].<br>deploymentSpec.<br>variables[] | **object**<br>
deployments[].<br>deploymentSpec.<br>variables[].<br>name | **string**<br><p>Обязательное поле.</p> 
deployments[].<br>deploymentSpec.<br>variables[].<br>defaultValue | **string**<br><p>Длина строки в символах должна быть менее 1000.</p> 
deployments[].<br>deploymentSpec.<br>variables[].<br>description | **string**<br><p>Максимальная длина строки в символах — 256.</p> 
deployments[].<br>deploymentYaml | **string**<br>
deployments[].<br>deploymentTemplateId | **string**<br>
nextPageToken | **string**<br>