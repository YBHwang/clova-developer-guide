## DecrementIntensityLevelConfirmation {#DecrementIntensityLevelConfirmation}
[`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest) 메시지에 대한 응답으로 대상 기기가 압력이나 수압 등의 세기를 낮추도록 요청한 후 처리된 결과를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `intensityLevel` | [IntensityLevelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#IntensityLevelInfoObject) | 현재 압력/수압 등의 세기 정보를 담고 있는 객체                  | 선택    |
| `previousState`  | object                                  | 기기의 이전 상황 정보를 담고 있는 객체                           | 선택    |
| `previousState.intensityLevel` | [IntensityLevelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#IntensityLevelInfoObject) | 이전 압력/수압 등의 세기 정보를 담고 있는 객체    | 선택    |

### Remarks

대상 기기에서 payload에 입력할 정보를 얻어올 수 없으면 값을 입력하지 않아도 됩니다. 이때 사용자에게 구체적인 정보 없이 기기 제어 요청이 정상 처리되었음을 알려줍니다.

### Message example

```json
{
  "header": {
    "messageId": "be3dde71-84c0-48cf-80d8-440c1ede54d8",
    "name": "DecrementIntensityLevelConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "intensityLevel": {
      "value": 1
    },
    "previousState": {
      "intensityLevel": {
        "value": 2
      }
    }
  }
}
```

### See also
* [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest)

## DecrementIntensityLevelRequest {#DecrementIntensityLevelRequest}
주로 에어컨이나 온도 조절 장치와 같은 기기를 제어할 때 사용되며, 대상 기기가 지정한 값만큼 압력이나 수압의 세기를 낮추도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`DecrementIntensityLevelConfirmation`](#DecrementIntensityLevelConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |
| `deltaIntensity`   | [IntensityLevelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | 변경할 세기의 정보를 담고 있는 객체                            | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "DecrementIntensityLevelRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-015"
    },
    "deltaIntensity": {
      "value": 1
    }
  }
}
```

### See also
* [`DecrementIntensityLevelConfirmation`](#DecrementIntensityLevelConfirmation)
