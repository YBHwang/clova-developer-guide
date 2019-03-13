## SetColorTemperatureConfirmation {#SetColorTemperatureConfirmation}
[`SetColorTemperatureRequest`](#SetColorTemperatureRequest) 메시지에 대한 응답으로 대상기기의 조명이나 화면, 전등의 색온도를 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `colorTemperature`   | [ColorTemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ColorTemperatureInfoObject) | 대상 기기에 설정되었거나 extension이 대상 기기에게 설정하도록 요청한 조명이나 화면, 전등의 색온도 정보를 담고 있는 객체                                | 선택    |

### Remarks

대상 기기에서 payload에 입력할 정보를 얻어올 수 없으면 값을 입력하지 않아도 됩니다. 이때 사용자에게 구체적인 정보 없이 기기 제어 요청이 정상 처리되었음을 알려줍니다.

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetColorTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
  	"colorTemperature": {
  		"value": 3600
  	}
  }
}
```

### See also
* [`SetColorTemperatureRequest`](#SetColorTemperatureRequest)

## SetColorTemperatureRequest {#SetColorTemperatureRequest}
주로 스마트 전등과 같은 기기를 제어할 때 사용되며, 대상 기기의 조명이나 화면, 전등의 색온도를 변경하도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`SetColorTemperatureConfirmation`](#SetColorTemperatureConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |
| `colorTemperature` | [ColorTemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ColorTemperatureInfoObject) | 대상 기기의 조명이나 화면, 전등에 설정할 색온도 정보를 담고 있는 객체                | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "a97dff79-5684-4535-8df3-193713c478aa",
    "name": "SetColorTemperatureRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-020"
    },
    "colorTemperature": {
      "value": 3600
    }
  }
}
```

### See also
* [`SetColorTemperatureConfirmation`](#SetColorTemperatureConfirmation)
