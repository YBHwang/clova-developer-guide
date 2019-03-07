## OpenConfirmation {#OpenConfirmation}
[`OpenRequest`](#OpenRequest) 메시지에 대한 응답으로 스마트 커튼이 일광 차단을 해제하거나, 비데의 뚜껑을 열도록 요청한 후 처리된 결과를 CEK에게 전달합니다.

### Payload fields

없음

### Message example

```json
{
  "header": {
    "messageId": "a4349fd5-7c1c-4fae-9bbd-291749bdd63a",
    "name": "OpenConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

### See also
* [`OpenRequest`](#OpenRequest)

## OpenRequest {#OpenRequest}
스마트 커튼이나 비데 등의 제품을 제어할 때 사용되며, 스마트 커튼이 일광 차단을 해제하거나, 비데의 뚜껑을 열도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`OpenConfirmation`](#OpenConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "8030275d-0e71-463d-b1d8-3e761e5389ad",
    "name": "OpenRequest",
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
* [`OpenConfirmation`](#OpenConfirmation)
