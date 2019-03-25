## GetConsumptionRequest {#GetConsumptionRequest}
전기, 수도 등의 자원을 측정하거나 소모하는 기기에서 현재까지 측정한 정보를 확인할 때 사용되며, 대상 기기가 측정한 정보를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetConsumptionResponse`](#GetConsumptionResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | 기간 정보를 담고 있는 객체. 이 필드가 요청에 포함되어 있으면 지정된 기간에 관련된 데이터를 제공해야 합니다.     | 조건부  |

### Message example

```json
{
  "header": {
    "messageId": "2d8b8c3b-5905-4355-b4bb-fa359c46c308",
    "name": "GetConsumptionRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-019"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

### See also
* [`GetConsumptionResponse`](#GetConsumptionResponse)

## GetConsumptionResponse {#GetConsumptionResponse}
[`GetConsumptionRequest`](#GetConsumptionRequest) 메시지에 대한 응답으로 대상 기기가 현재까지 측정한 에너지 또는 자원 사용량 정보를 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `consumption[]`              | [ConsumptionInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ConsumptionInfoObject) array | 기기가 현재까지 측정한 에너지 또는 자원 사용량 정보를 담고 있는 객체   | 필수    |

### Message example

```json
// 예제 1: 전기 사용량 표현
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetConsumptionResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "consumption": [
      {
        "name": "전기사용량",
        "value": 79.7,
        "unit": "KW"
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}

// 예제 2: 물 사용량 표현
{
  "header": {
    "messageId": "962f7543-05e9-4b4e-8bda-5615e40dca6b",
    "name": "GetConsumptionResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "consumption": [
      {
        "name": "마신물",
        "value": 24,
        "unit": "l"
      }
    ],
    "applianceResponseTimestamp": "2019-12-23T20:30:54+09:00"
  }
}
```

### See also
* [GetConsumptionRequest](#GetConsumptionRequest)
