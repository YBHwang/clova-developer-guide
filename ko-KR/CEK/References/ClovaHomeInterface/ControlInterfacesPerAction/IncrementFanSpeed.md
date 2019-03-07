## IncrementFanSpeedConfirmation {#IncrementFanSpeedConfirmation}
[`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest) 메시지에 대한 응답으로 대상 기기가 팬의 속도를 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `fanSpeed`            | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject) | 현재 팬의 속도 정보를 담고 있는 객체. 팬의 속도는 풍속을 의미하며 팬 속도를 다음과 같은 값으로 제한합니다.<ul><li><code>1</code>: 약한 바람(1단)</li><li><code>2</code>: 중간 바람(2단)</li><li><code>3</code>: 강한 바람(3단)</li></ul> | 선택    |
| `previousState`          | object                      | 기기의 이전 상황 정보를 담고 있는 객체                 | 선택    |
| `previousState.fanSpeed` | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject) | 이전 팬의 속도 정보를 담고 있는 객체. 팬의 속도는 풍속을 의미하며 팬 속도를 다음과 같은 값으로 제한합니다.<ul><li><code>1</code>: 약한 바람(1단)</li><li><code>2</code>: 중간 바람(2단)</li><li><code>3</code>: 강한 바람(3단)</li></ul> | 선택    |

### Remarks

대상 기기에서 payload에 입력할 정보를 얻어올 수 없으면 값을 입력하지 않아도 됩니다. 이때 사용자에게 구체적인 정보 없이 기기 제어 요청이 정상 처리되었음을 알려줍니다.

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementFanSpeedConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "fanSpeed": {
      "value": 3
    },
    "previousState": {
      "fanSpeed": {
        "value": 2
      }
    }
  }
}
```

### See also
* [`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest)

## IncrementFanSpeedRequest {#IncrementFanSpeedRequest}
주로 공기청정기와 같은 기기를 제어할 때 사용되며, 대상 기기가 지정한 값만큼 팬의 속도를 높이도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`IncrementFanSpeedConfirmation`](#IncrementFanSpeedConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다. | 항상    |
| `deltaFanSpeed` | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject) | 변경할 속도의 크기 정보를 담고 있는 객체.  | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementFanSpeedRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-004"
    },
    "deltaFanSpeed": {
      "value": 1
    }
  }
}
```

### See also
* [`IncrementFanSpeedConfirmation`](#IncrementFanSpeedConfirmation)
