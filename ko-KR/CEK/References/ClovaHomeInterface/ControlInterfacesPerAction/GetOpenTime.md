## GetOpenTimeRequest {#GetOpenTimeRequest}
주로 열림 감지 센서가 감지한 내용 중 감지 대상이 마지막으로 열렸던 시점의 시간 정보를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetOpenTimeResponse`](#GetOpenTimeResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetOpenTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-025"
    }
  }
}
```

### See also
* [`GetOpenTimeResponse`](#GetOpenTimeResponse)

## GetOpenTimeResponse {#GetOpenTimeResponse}

[`GetOpenTimeRequest`](#GetOpenTimeRequest) 메시지에 대한 응답으로 대상 기기가 감지한 내용 중 감지 대상이 마지막으로 열렸던 시점의 시간 정보를 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `openTimestamp`              | string | 감지 대상이 마지막으로 열렸던 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetOpenTimeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "openTimestamp": "2018-03-13T23:20:15+09:00",
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

### See also
* [`GetOpenTimeRequest`](#GetOpenTimeRequest)
