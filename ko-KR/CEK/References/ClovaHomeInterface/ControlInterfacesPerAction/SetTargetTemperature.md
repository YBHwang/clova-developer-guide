## SetTargetTemperatureConfirmation {#SetTargetTemperatureConfirmation}
[`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest) 메시지에 대한 응답으로 희망 온도를 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `endpoint`     | [EndpointInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#EndpointInfoObject)    | 희망 온도가 적용된 최종 대상. 대상 기기가 온도를 적용할 최종 대상(endpoint)이 지정될 수 있으며, 최종 대상은 기기의 특정 부분, 구동 방식이나 이를 적용할 영역 등을 의미합니다. 예를 들어 사용자는 냉장고 온도를 조절할 때 냉동실의 온도를 변경할지 냉장실의 온도를 변경할지 추가로 지정할 수 있습니다. {{ "또, 난방 기능이 있는 에어컨을 조절할 때는 냉방 모드로 동작할 때의 온도와 난방 모드로 동작할 때의 온도를 구분하여 제어할 수 있습니다." if book.L10N.TargetCountryCode == "JP" }}  | 선택  |
| `targetTemperature`               | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | 대상 기기에 설정되었거나 extension이 대상 기기에게 설정하도록 요청한 희망 온도 정보를 담고 있는 객체                                | 선택    |

### Remarks

대상 기기에서 payload에 입력할 정보를 얻어올 수 없으면 값을 입력하지 않아도 됩니다. 이때 사용자에게 구체적인 정보 없이 기기 제어 요청이 정상 처리되었음을 알려줍니다.

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetTargetTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": 22
    },
    "endpoint": {
      "value": "freezer"
    }
  }
}
```

### See also
* [`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest)

## SetTargetTemperatureRequest {#SetTargetTemperatureRequest}
주로 에어컨이나 온도 조절 장치와 같은 기기를 제어할 때 사용되며, 대상 기기가 희망 온도를 지정한 값으로 변경하도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`SetTargetTemperatureConfirmation`](#SetTargetTemperatureConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |
| `endpoint`     | [EndpointInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#EndpointInfoObject)    | 희망 온도를 적용할 최종 대상. 대상 기기가 온도를 적용할 최종 대상(endpoint)이 지정될 수 있으며, 최종 대상은 기기의 특정 부분, 구동 방식이나 이를 적용할 영역 등을 의미합니다. 예를 들어 사용자는 냉장고 온도를 조절할 때 냉동실의 온도를 변경할지 냉장실의 온도를 변경할지 추가로 지정할 수 있습니다. {{ "또, 난방 기능이 있는 에어컨을 조절할 때는 냉방 모드로 동작할 때의 온도와 난방 모드로 동작할 때의 온도를 구분하여 제어할 수 있습니다." if book.L10N.TargetCountryCode == "JP" }}  | 조건부  |
| `targetTemperature`       | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | 대상 기기에 설정해야 할 희망 온도 정보를 담고 있는 객체                | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetTargetTemperatureRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-001"
    },
    "targetTemperature": {
      "value": 22
    },
    "endpoint": {
      "value": "freezer"
    }
  }
}
```

### See also
* [`SetTargetTemperatureConfirmation`](#SetTargetTemperatureConfirmation)
