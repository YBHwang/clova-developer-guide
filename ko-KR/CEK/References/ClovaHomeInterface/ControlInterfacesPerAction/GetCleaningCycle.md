## GetCleaningCycleRequest {#GetCleaningCycleRequest}
기기의 세척 주기를 확인할 때 사용되며, 대상 기기의 다음 세척 주기까지 남은 시간에 대한 정보를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetCleaningCycleResponse`](#GetCleaningCycleResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "9a1a7237-f1c0-44f8-b4db-2a2abb1f0e1c",
    "name": "GetCleaningCycleRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-045"
    }
  }
}
```

### See also
* [`GetCleaningCycleResponse`](#GetCleaningCycleResponse)

## GetCleaningCycleResponse {#GetCleaningCycleResponse}

[`GetCleaningCycleRequest`](#GetCleaningCycleRequest) 메시지에 대한 응답으로 대상 기기의 다음 세척 주기까지 남은 시간을 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`<a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601</a> 형식)     | 선택    |
| `remainingTime`              | string | 세척 필요 시점까지 남은 시간(<a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601 Durations</a>)    | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetCleaningCycleResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "remainingTime": "PT8H40M",
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

### See also
* [`GetCleaningCycleRequest`](#GetCleaningCycleRequest)
