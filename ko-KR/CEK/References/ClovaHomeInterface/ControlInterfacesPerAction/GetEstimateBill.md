## GetEstimateBillRequest {#GetEstimateBillRequest}
주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 측정된 사용량의 기반으로 예상 요금을 확인할 때 사용되며, 대상 기기가 예측한 요금 정보를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetEstimateBillResponse`](#GetEstimateBillResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/CEK/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | 기간 정보를 담고 있는 객체. 이 필드가 요청에 포함되어 있으면 지정된 기간에 관련된 데이터를 제공해야 합니다.     | 조건부  |

### Message example

```json
{
  "header": {
    "messageId": "eadd9f02-6bf9-47b1-b07e-12f5e39fd37e",
    "name": "GetEstimateBillRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-019"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

### See also
* [`GetEstimateBillResponse`](#GetEstimateBillResponse)

## GetEstimateBillResponse {#GetEstimateBillResponse}
[`GetEstimateBillRequest`](#GetEstimateBillRequest) 메시지에 대한 응답으로 대상 기기가 예측한 요금 정보를 CEK에게 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`YYYY-MM-DDThh:mm:ss±hh:mm`<a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601</a> 형식)     | 선택    |
| `estimateBill`                 | [BillInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BillInfoObject) | 기기가 예측한 요금 정보를 담고 있는 객체   | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "34e79706-f626-4c76-8bfb-3f4661d4aa74",
    "name": "GetEstimateBillResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "estimateBill": {
        "value": 60000,
        "currency": "KRW"
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}
```

### See also
* [GetEstimateBillRequest](#GetEstimateBillRequest)
