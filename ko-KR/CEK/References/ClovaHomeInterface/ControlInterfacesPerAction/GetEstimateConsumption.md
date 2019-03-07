## GetEstimateConsumptionRequest {#GetEstimateConsumptionRequest}
주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 현재까지 측정된 에너지 또는 자원 사용량을 확인할 때 사용되며, 대상 기기가 측정한 에너지 또는 자원 사용량 정보를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetConsumptionResponse`](#GetConsumptionResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "2d8b8c3b-5905-4355-b4bb-fa359c46c308",
    "name": "GetEstimateConsumptionRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-019"
    }
  }
}
```

### See also
* [`GetEstimateConsumptionResponse`](#GetEstimateConsumptionResponse)

## GetEstimateConsumptionResponse {#GetEstimateConsumptionResponse}
[`GetEstimateConsumptionRequest`](#GetEstimateConsumptionRequest) 메시지에 대한 응답으로 대상 기기가 현재까지 측정한 에너지 또는 자원 사용량 정보를 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`<a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601</a> 형식)     | 선택    |
| `consumption[]`              | [ConsumptionInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ConsumptionInfoObject) array | 기기가 현재까지 측정한 에너지 또는 자원 사용량 정보를 담고 있는 객체   | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetEstimateConsumptionResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "consumption": [
      {
        "name": "전기사용량",
        "value": 79.7,
        "unit": "kW"
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}
```

### See also
* [GetEstimateConsumptionRequest](#GetEstimateConsumptionRequest)
