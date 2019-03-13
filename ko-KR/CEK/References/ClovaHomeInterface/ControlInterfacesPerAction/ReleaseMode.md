## ReleaseModeConfirmation {#ReleaseModeConfirmation}
[`ReleaseModeRequest`](#ReleaseModeRequest) 메시지에 대한 응답으로 현재 기기의 운전 모드(operation mode)를 해제하도록 요청한 후 처리된 결과를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `mode`          | [ModeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject)  | 운전 모드 해제 요청에 의해 대상 기기에 설정되었거나 extension이 대상 기기에게 되돌아가도록 요청한 운전 모드 정보를 담고 있는 객체      | 선택    |
| `previousState` | [ModeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject)  | 운전 모드 해제 요청 전에 대상 기기에 설정되어 있던 운전 모드 정보를 담고 있는 객체      | 선택    |

### Remarks

대상 기기에서 payload에 입력할 정보를 얻어올 수 없으면 값을 입력하지 않아도 됩니다. 이때 사용자에게 구체적인 정보 없이 기기 제어 요청이 정상 처리되었음을 알려줍니다.

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "ReleaseModeConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "previousState": {
      "mode": {
        "value": "sleep"
      }
    },
    "mode": {
      "value": "wakeup"
    }
  }
}
```

### See also
* [`ReleaseModeRequest`](#ReleaseModeRequest)

## ReleaseModeRequest {#ReleaseModeRequest}
현재 기기에 설정된 운전 모드(operation mode)를 해제할 때 사용되며, 기기의 운전 모드를 해제하여 이전 운전 모드나 기본 운전 모드로 돌아가도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`ReleaseModeConfirmation`](#ReleaseModeConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken` | string  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다. | 항상    |
| `appliance`   | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |
| `mode`        | [ModeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject) | 대상 기기에서 해제할 운전 모드 정보를 담고 있는 객체                         | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "ReleaseModeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-006"
    },
    "mode": "sleep"
  }
}
```

### See also
* [`ReleaseModeConfirmation`](#ReleaseModeConfirmation)
