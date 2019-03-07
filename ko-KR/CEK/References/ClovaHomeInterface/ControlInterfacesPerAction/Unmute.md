## UnmuteConfirmation {#UnmuteConfirmation}
[`UnmuteRequest`](#UnmuteRequest) 메시지에 대한 응답으로 대상 기기의 소리를 켜도록 설정(음소거 해제)한 결과를 CEK에게 전달합니다.

### Payload fields
없음

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "UnmuteConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

### See also
* [`UnmuteRequest`](#UnmuteRequest)

## UnmuteRequest {#UnmuteRequest}
주로 TV나 셋톱박스와 같은 기기를 제어할 때 사용되며, 대상 기기의 소리를 켜도록(음소거 해제) Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`UnmuteConfirmation`](#UnmuteConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "UnmuteRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-005"
    }
  }
}
```

### See also
* [`UnmuteConfirmation`](#UnmuteConfirmation)
