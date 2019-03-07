## HealthCheckRequest {#HealthCheckRequest}
지정한 기기의 상태를 파악할 때 사용되며, 대상 기기의 상태 정보를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`HealthCheckResponse`](#HealthCheckResponse) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string  | Clova Home extension의 access token | 항상    |
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포합됩니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "HealthCheckRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-001"
    }
  }
}
```

### See also
* [`HealthCheckResponse`](#HealthCheckResponse)

## HealthCheckResponse {#HealthCheckResponse}
[`HealthCheckRequest`](#HealthCheckRequest) 메시지에 대한 응답으로 지정된 기기의 상태를 CEK에게 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `isReachable` | boolean | 네트워크를 통해 대상 기기에 접근 가능한지 나타내는 값. <ul><li><code>true</code>: 접근 가능(online)</li><li><code>false</code>: 접근 불가(offline)</li></ul> | 필수    |
| `isTurnOn`    | boolean | 대상 기기의 동작 상태를 나타내는 값. <ul><li><code>true</code>: 동작 상태(working)</li><li><code>false</code>: 대기 상태(idle)</li></ul>                  | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "HealthCheckResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "isReachable": true,
    "isTurnOn": false
  }
}
```

### See also
* [`HealthCheckRequest`](#HealthCheckRequest)
