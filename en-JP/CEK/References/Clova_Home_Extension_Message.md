## Clova Home extension messages {#ClovaHomeExtMessage}
A Clova Home extension message is a message specification used by your extension when it exchanges information with CEK to control IoT appliances. This section explains the [message formats](#ClovaHomeExtMessageFormat) and [interfaces](#ClovaHomeExtInterface) of a Clova Home extension message.

### Message format {#ClovaHomeExtMessageFormat}

A Clova Home extension message consists of a `header` field and a `payload`. This is the same for both request messages and response messages. However, the configuration of the `payload` may vary depending on the [interface](#ClovaHomeExtInterface) used. The following explains the common format of a Clova Home extension message.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>A Clova Home extension message is divided into a request message and a response message. Request messages sent from CEK to an extension have a name format such as `XxxxRequest`. Response messages returned from an extension to CEK have a name format such as `XxxxConfirmation` or `XxxxResponse`. Also, when an error occurs, you must return a 200 OK HTTP response. Such response messages follow the `XxxxError` name format.</p>
</div>

#### Message structure
{% raw %}
```json
{
  "header": {
    "messageId": {{string}},
    "namespace": {{string}},
    "name": {{string}},
    "payloadVersion": {{string}}
  },
  "payload": {{object}}
}
```
{% endraw %}


#### Message fields
| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:-------------:|
| `header`                 | object | The header of the message.                                                                                            |<!-- -->|
| `header.messageId`       | string | The message ID (UUID). An identifier created by Clova to distinguish individual messages.                                         |<!-- -->|
| `header.name`            | string | The API name of the message.                                                                                        |<!-- -->|
| `header.namespace`       | string | The value is always `"ClovaHome"`.                                                                     |<!-- -->|
| `header.payloadVersion`  | string | The version of the Clova Home extension message specified in `header.name`. Configuration of the `payload` field may vary depending on this version.  |<!-- -->|
| `payload`                | object | Configuration of the payload object and its field values can vary depending on which [interface](#ClovaHomeExtInterface) is specified in `header.name`.       |<!-- -->|

#### Message example
{% raw %}
```json
Example 1: DiscoverAppliancesRequest - Request message
{
  "header": {
    "messageId": "8ddd7f05-7703-4cb4-a6dd-93c209c6647b",
    "name": "DiscoverAppliancesRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33"
  }
}

Example 2: DiscoverAppliancesResponse - Response message
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "discoveredAppliances": [
      {
        "applianceId": "device-001",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "Smart lamp",
        "version": "v1.0",
        "friendlyName": "Living room lamp",
        "friendlyDescription": "A lamp that can be controlled using a smartphone",
        "isIr": false,
        "isReachable": true,
          "actions": [
            "DecrementBrightness",
            "HealthCheck",
            "IncrementBrightness",
            "SetBrightness",
            "TurnOn",
            "TurnOff"
        ],
        "applianceTypes": ["LIGHT"],
        "additionalApplianceDetails": {
        }
      },
      {
        "applianceId": "device-002",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "Smart plug",
        "version": "v1.0",
        "friendlyName": "Kitchen plug",
        "friendlyDescription": "An energy-saving plug",
        "isIr": false,
        "isReachable": true,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {
        }
      }
    ]
  }
}

Example 3: IncrementTargetTemperatureConfirmation - Response message
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementTargetTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": 25.0
    },
    "previousState": {
      "targetTemperature": {
        "value": 22.0
      }
    }
  }
}

Example 4: TargetOffLineError - Error response message
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "TargetOfflineError",
    "payloadVersion": "1.0"
  },
  "payload": {
  }
}
```
{% endraw %}

#### See also
* [Creating a Clova Home extension](/CEK/Guides/Build_Clova_Home_Extension.md)
* [Interface](#ClovaHomeExtInterface)

### Interface {#ClovaHomeExtInterface}
Clova Home extension messages are categorized into the following interfaces:

* Interface
  * [Discovery interface](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md)
  * [Control interface](/CEK/References/ClovaHomeInterface/Control_Interfaces.md)
  * [Error interface](/CEK/References/ClovaHomeInterface/Error_Interfaces.md)

* Shared objects
  * [Shared objects](/CEK/References/ClovaHomeInterface/Shared_Objects.md)
