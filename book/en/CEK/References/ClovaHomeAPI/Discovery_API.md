## Discovery API {#DiscoveryAPI}

Use this API to obtain a list of IoT appliances registered to a user account.

| Message name         | Message type  | Message description                                   |
|------------------|-----------|---------------------------------------------|
| [DiscoverAppliancesRequest](#DiscoverAppliancesRequest)                     | Request  | Requests Clova Home extension to provide a list of IoT appliances registered to the user.             |
| [DiscoverAppliancesResponse](#DiscoverAppliancesResponse)                   | Response | Returns a list of IoT appliances registered to the user back to CEK as a response to the [DiscoverAppliancesRequest](#DiscoverAppliancesRequest) message. |

### DiscoverAppliancesRequest {#DiscoverAppliancesRequest}
Requests Clova Home extension to provide a list of appliances registered to the user. Use a *[ClovaHome.DiscoverAppliancesResponse](DiscoverAppliancesResponse)* message to respond to the request.

#### Payload field

| Field name       | Type    | Field description                     | Required |
|---------------|---------|-----------------------------|---------|
| accessToken   | string  | Access token for Clova Home extension  | Yes     |

#### Message example

{% raw %}
```json
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
```
{% endraw %}

#### See also
* [ClovaHome.DiscoverAppliancesResponse](DiscoverAppliancesResponse)

### DiscoverAppliancesResponse {#DiscoverAppliancesResponse}
Returns a list of appliances registered to the user back to CEK. Use this message to respond to a *[ClovaHome.DiscoverAppliancesRequest](DiscoverAppliancesRequest)* message.

#### Payload field

| Field name       | Type    | Field description                     | Required |
|---------------|---------|-----------------------------|---------|
| discoveredAppliances[]  | [ApplianceObject](#ApplianceObject) array  | Object array displaying the list of appliances registered to the user account          | Yes    |

#### Remarks
When providing an IoT service, it is required to provide a list of appliances registered to each user account.

#### Message example

{% raw %}
```json
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
        "modelName": "스마트 전등",
        "version": "v1.0",
        "friendlyName": "거실 전등",
        "friendlyDescription": "스마트폰으로 제어할 수 있는 전등",
        "isReachable": true,
          "actions": [
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
        "modelName": "스마트 플러그",
        "version": "v1.0",
        "friendlyName": "부엌 플러그",
        "friendlyDescription": "에너지를 절약하는 플러그",
        "isReachable": true,
        "actions": [
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
```
{% endraw %}

#### See also
* [ClovaHome.DiscoverAppliancesRequest](DiscoverAppliancesRequest)