# Discovery

ユーザーアカウントに登録されているIoTデバイスのリストを確認する際に使用されるインターフェースです。

| メッセージ         | タイプ  | 説明                                   |
|------------------|-----------|---------------------------------------------|
| [`DiscoverAppliancesRequest`](#DiscoverAppliancesRequest)   | Request  | ユーザーが登録したIoTデバイスのリストをClova Home Extensionにリクエストします。             |
| [`DiscoverAppliancesResponse`](#DiscoverAppliancesResponse) | Response | [`DiscoverAppliancesRequest`](#DiscoverAppliancesRequest)メッセージに対するレスポンスです。ユーザーが登録したIoTデバイスのリストをCEKに返します。 |

## DiscoverAppliancesRequest {#DiscoverAppliancesRequest}
ユーザーが登録したデバイスのリストをClova Home Extensionにリクエストします。このリクエストに対するレスポンスとして、[`DiscoverAppliancesResponse`](#DiscoverAppliancesResponse)メッセージを使用する必要があります。

### Payload fields

| フィールド名       | データ型    | フィールドの説明                     | 任意 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string  | Clova Home Extensionのアクセストークン  | 常時     |

### Message example

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

### 次の項目も参照してください。
* [`DiscoverAppliancesResponse`](#DiscoverAppliancesResponse)

## DiscoverAppliancesResponse {#DiscoverAppliancesResponse}
ユーザーが登録したデバイスのリストをCEKに返します。このメッセージは、[`DiscoverAppliancesRequest`](#DiscoverAppliancesRequest)メッセージに対するレスポンスとして使用します。

### Payload fields

| フィールド名       | データ型    | フィールドの説明                     | 必須/選択 |
|---------------|---------|-----------------------------|:---------:|
| `discoveredAppliances[]`  | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) array  | ユーザーアカウントに登録されているデバイスを説明するオブジェクト配列          | 必須    |

### 備考
IoTサービスを提供する際、ユーザーアカウントに登録されているデバイスのリストを提供する必要があります。

### Message example

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
<<<<<<< HEAD:ja/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md
        "modelName": "スマート照明",
        "version": "v1.0",
        "friendlyName": "リビングの照明",
        "friendlyDescription": "スマートフォンで制御できる照明",
=======
        "modelName": "Smart lamp,"
        "version": "v1.0",
        "friendlyName": "Living room lamp,"
        "friendlyDescription": "A lamp that can be controlled using a smartphone,"
>>>>>>> parent of 2c4b30d... Merge pull request #448 from leejungho86/Review-Clova-Home-extension-translations:en/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md
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
        "additionalApplianceDetails": {}
      },
      {
        "applianceId": "device-002",
        "manufacturerName": "device-manufacturer-name",
<<<<<<< HEAD:ja/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md
        "modelName": "スマートコンセント",
        "version": "v1.0",
        "friendlyName": "キッチンのコンセント",
        "friendlyDescription": "節電コンセント",
=======
        "modelName": "Smart plug,"
        "version": "v1.0",
        "friendlyName": "Kitchen plug,"
        "friendlyDescription": "An energy-saving plug,"
>>>>>>> parent of 2c4b30d... Merge pull request #448 from leejungho86/Review-Clova-Home-extension-translations:en/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md
        "isReachable": true,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {}
      }
    ]
  }
}
```
{% endraw %}

### 次の項目も参照してください。
* [`DiscoverAppliancesRequest`](#DiscoverAppliancesRequest)
