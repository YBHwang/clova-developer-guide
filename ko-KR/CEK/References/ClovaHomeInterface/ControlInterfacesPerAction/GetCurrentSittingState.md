## GetCurrentSittingStateRequest {#GetCurrentSittingStateRequest}
스마트 의자와 같은 기기에서 사용자의 사용 상태를 확인할 때 사용되며, 대상 기기가 사용자 착석 여부를 감지한 정보와 최근 사용자가 사용한 시간 정보를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetCurrentSittingStateResponse`](#GetCurrentSittingStateResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | 기간 정보를 담고 있는 객체. 이 필드가 요청에 포함되어 있으면 지정된 기간에 관련된 데이터를 제공해야 합니다.         | 조건부   |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetCurrentSittingStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-032"
    }
  }
}
```

### See also
* [`GetCurrentSittingStateResponse`](#GetCurrentSittingStateResponse)

## GetCurrentSittingStateResponse {#GetCurrentSittingStateResponse}
[`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest) 메시지에 대한 응답으로 대상 기기가 사용자 착석 여부를 감지한 정보와 최근 사용자가 사용한 시간 정보를 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string  | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `sittingState`               | [SittingStateInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SittingStateInfoObject) |  스마트 의자와 같은 기기에 대한 사용자의 착석 정보가 담긴 객체              | 필수    |
| `recentlySittingPeriod`      | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject) | 최근 사용 시간 정보를 담고 있는 객체              | 선택    |

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetCurrentSittingStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "sittingState": {
      "value": true
    },
    "recentlySittingPeriod": {
      "start": "2018-03-28T00:10:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    },
    "applianceResponseTimestamp": "2018-03-29T14:32:13+09:00"
  }
}
```

### See also
* [`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest)
