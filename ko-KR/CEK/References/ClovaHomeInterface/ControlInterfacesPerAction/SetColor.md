## SetColorConfirmation {#SetColorConfirmation}
[`SetColorRequest`](#SetColorRequest) 메시지에 대한 응답으로 대상기기의 조명이나 화면, 전등의 색을 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `color`   | [ColorInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ColorInfoObject) | 대상 기기에 설정되었거나 extension이 대상 기기에게 설정하도록 요청한 조명이나 화면, 전등의 색 정보를 담고 있는 객체                                | 선택    |

### Remarks

대상 기기에서 payload에 입력할 정보를 얻어올 수 없으면 값을 입력하지 않아도 됩니다. 이때 사용자에게 구체적인 정보 없이 기기 제어 요청이 정상 처리되었음을 알려줍니다.

### Message example

```json
{
  "header": {
    "messageId": "0e380076-59f1-4417-9d30-895be4b34cea",
    "name": "SetColorConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
  	"color": {
  		"hue": 100,
      "saturation": 100,
      "brightness": 100
  	}
  }
}
```

### See also
* [`SetColorRequest`](#SetColorRequest)

## SetColorRequest {#SetColorRequest}
주로 스마트 전등과 같은 기기를 제어할 때 사용되며, 대상 기기의 조명이나 화면, 전등의 색을 변경하도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`SetColorConfirmation`](#SetColorConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |
| `color`         | [ColorInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ColorInfoObject) | 대상 기기의 조명이나 화면, 전등에 설정할 색 정보를 담고 있는 객체            | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "a130f6de-d2ac-45d5-86b7-936a841a3c63",
    "name": "SetColorRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-020"
    },
    "color": {
  		"hue": 100,
      "saturation": 100,
      "brightness": 100
  	}
  }
}
```

### See also
* [`SetColorConfirmation`](#SetColorConfirmation)
