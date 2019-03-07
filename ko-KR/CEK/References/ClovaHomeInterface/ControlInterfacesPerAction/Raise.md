## RaiseConfirmation {#RaiseConfirmation}
[`RaiseRequest`](#RaiseRequest) 메시지에 대한 응답으로 대상 기기의 높낮이를 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다.

### Payload fields

없음

### Message example

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "RaiseConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

### See also
* [`RaiseRequest`](#RaiseRequest)

## RaiseRequest {#RaiseRequest}
스마트 침대 같은 기기를 제어할 때 사용되며, 대상 기기의 높낮이를 높이도록 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`RaiseConfirmation`](#RaiseConfirmation) 메시지를 사용해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |

### Remarks
기기의 높낮이를 조정할 때 이동될 수 있는 최대 위치까지 이동됩니다. 높낮이 조정 중에 기기를 멈추려면 [StopRequest](#StopRequest) 메시지를 받아야 합니다.

### Message example

```json
{
  "header": {
    "messageId": "253f1f01-c157-411d-8c3f-96ea6173fcc6",
    "name": "RaiseRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-014"
    }
  }
}
```

### See also

* [`LowerRequest`](#LowerRequest)
* [`RaiseConfirmation`](#RaiseConfirmation)
