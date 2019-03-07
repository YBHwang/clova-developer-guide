## StopConfirmation {#StopConfirmation}
[`StopRequest`](#StopRequest) 메시지에 대한 응답으로 대상 기기에게 동작 중지를 요청한 결과를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 |
|---------------|---------|-----------------------------|:---------:|
| `phase`       | [PhaseInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PhaseInfoObject) | 기기가 정지하기 직전에 수행하던 동작 단계의 정보를 담고 있는 객체   | 선택  |

### Message example

```json
{
  "header": {
    "messageId": "a4349fd5-7c1c-4fae-9bbd-291749bdd63a",
    "name": "StopConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "phase": {
      "value": "세탁"
    }
  }
}
```

### See also
* [`StopRequest`](#StopRequest)

## StopRequest {#StopRequest}
기기의 현재 동작을 중지하도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`StopConfirmation`](#StopConfirmation) 메시지를 사용해야 합니다.

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
    "name": "StopRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-016"
    }
  }
}
```

### See also
* [`StopConfirmation`](#StopConfirmation)
