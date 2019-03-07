## GetOpenStateRequest {#GetOpenStateRequest}
주로 열림 감지 센서가 감지한 내용 중 감지 대상의 현재 상태 정보(열림 또는 닫힘)를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetOpenStateResponse`](#GetOpenStateResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetOpenStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-012"
    }
  }
}
```

### See also
* [`GetOpenStateResponse`](#GetOpenStateResponse)

## GetOpenStateResponse {#GetOpenStateResponse}
[`GetOpenStateRequest`](#GetOpenStateRequest) 메시지에 대한 응답으로 주로 감지 대상의 현재 상태 정보(열림 또는 닫힘)를 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`<a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601</a> 형식)     | 선택    |
| `openState`                  | string | 커버나 문, 창문 따위를 감지한 상태 정보.<ul><li><code>"CLOSED"</code>: 커버나 문, 창문 따위가 닫힌 상태</li><li><code>"OPENED"</code>: 커버나 문, 창문 따위가 열린 상태</li></ul> | 필수    |


### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetOpenStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "OpenState": "LOCKED",
    "applianceResponseTimestamp": "2017-11-23T20:31:08+09:00"
  }
}
```

### See also
* [`GetOpenStateRequest`](#GetOpenStateRequest)
