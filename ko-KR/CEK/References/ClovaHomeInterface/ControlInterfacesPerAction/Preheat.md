## PreheatConfirmation {#PreheatConfirmation}
[`PreheatRequest`](#PreheatRequest) 메시지에 대한 응답으로 예열 요청을 처리한 후 그 결과를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `targetTemperature`               | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | 대상 기기에 설정되었거나 extension이 대상 기기에게 설정하도록 요청한 희망 예열 온도 정보를 담고 있는 객체                                | 선택    |

### Remarks

대상 기기에서 payload에 입력할 정보를 얻어올 수 없으면 값을 입력하지 않아도 됩니다. 이때 사용자에게 구체적인 정보 없이 기기 제어 요청이 정상 처리되었음을 알려줍니다.

### Message example

```json
{
  "header": {
    "messageId": "ec9ab261-528e-4b19-94e5-6e35a2494a6d",
    "name": "PreheatConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": 180
    }
  }
}
```

### See also
* [`PreheatRequest`](#PreheatRequest)

## PreheatRequest {#PreheatRequest}
주로 오븐과 같은 기기를 제어할 때 사용되며, 대상 기기가 예열하도록 Clova Home extension에게 요청합니다. 희망 예열 온도가 메시지에 포함될 수 있습니다. 이 요청에 대한 응답으로 [`PreheatConfirmation`](#PreheatConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |
| `targetTemperature`       | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | 희망 예열 온도 정보를 담고 있는 객체             | 선택    |

### Message example

```json
{
  "header": {
    "messageId": "d68661e9-dc78-4556-a0db-87ffb3ad30c5",
    "name": "PreheatRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-044"
    },
    "targetTemperature": {
      "value": 180
    }
  }
}
```

### See also
* [`PreheatConfirmation`](#PreheatConfirmation)
