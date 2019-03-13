# Control

IoT 기기 정보 확인 및 기기 제어와 관련된 요청 및 응답을 수행할 때 사용되는 인터페이스입니다.

| 메시지 이름         | 메시지 타입  | 메시지 설명                                   |
|------------------|-----------|---------------------------------------------|
| [`ChargeConfirmation`](#ChargeConfirmation)                                   | Response | [`ChargeRequest`](#ChargeRequest) 메시지에 대한 응답으로 대상 기기가 스스로 충전하도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`ChargeRequest`](#ChargeRequest)                                             | Request  | 대상 기기가 스스로를 충전하도록 Clova Home extension에게 요청합니다. |
| [`CloseConfirmation`](#CloseConfirmation)                                     | Response | [`CloseRequest`](#CloseRequest) 메시지에 대한 응답으로 스마트 커튼이 일광 차단하거나, 비데의 뚜껑을 닫도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`CloseRequest`](#CloseRequest)                                               | Request  | 스마트 커튼이나 비데 등의 제품을 제어할 때 사용되며, 스마트 커튼이 일광 차단하거나, 비데의 뚜껑을 닫도록 Clova Home extension에게 요청합니다.  |
| [`DecrementBrightnessConfirmation`](#DecrementBrightnessConfirmation)         | Response | [`DecrementBrightnessRequest`](#DecrementBrightnessRequest) 메시지에 대한 응답으로 대상 기기가 조명 밝기를 낮추도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`DecrementBrightnessRequest`](#DecrementBrightnessRequest)                   | Request  | 대상 기기가 지정한 수준만큼 조명의 밝기를 낮추도록 Clova Home extension에게 요청합니다. |
| [`DecrementChannelConfirmation`](#DecrementChannelConfirmation)               | Response | [`DecrementChannelRequest`](#DecrementChannelRequest) 메시지에 대한 응답으로 대상 기기가 TV 채널을 낮추도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`DecrementChannelRequest`](#DecrementChannelRequest)                         | Request  | 대상 기기가 지정한 수준만큼 TV 채널을 낮추도록 Clova Home extension에게 요청합니다. |
| [`DecrementFanSpeedConfirmation`](#DecrementFanSpeedConfirmation)             | Response | [`DecrementFanSpeedRequest`](#DecrementFanSpeedRequest) 메시지에 대한 응답으로 대상 기기가 팬 속도를 낮추도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`DecrementFanSpeedRequest`](#DecrementFanSpeedRequest)                       | Request  | 대상 기기가 지정한 값만큼 팬 속도를 낮추도록 Clova Home extension에게 요청합니다. |
| [`DecrementIntensityLevelConfirmation`](#DecrementIntensityLevelConfirmation) | Response | [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest) 메시지에 대한 응답으로 대상 기기가 압력이나 수압 등의 세기를 낮추도록 요청한 후 처리된 결과를 CEK에게 전달합니다.  |
| [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest)           | Request  | 주로 에어컨이나 온도 조절 장치와 같은 기기를 제어할 때 사용되며, 대상 기기가 지정한 값만큼 압력이나 수압의 세기를 낮추도록 Clova Home extension에게 요청합니다.  |
| [`DecrementTargetTemperatureConfirmation`](#DecrementTargetTemperatureConfirmation) | Response | [`DecrementTargetTemperatureRequest`](#DecrementTargetTemperatureRequest) 메시지에 대한 응답으로 대상 기기가 온도를 낮추도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`DecrementTargetTemperatureRequest`](#DecrementTargetTemperatureRequest)     | Request  | 대상 기기가 지정한 값만큼 온도를 낮추도록 Clova Home extension에게 요청합니다.      |
| [`DecrementVolumeConfirmation`](#DecrementVolumeConfirmation)                 | Response | [`DecrementVolumeRequest`](#DecrementVolumeRequest) 메시지에 대한 응답으로 대상 기기가 스피커 볼륨 크기를 낮추도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`DecrementVolumeRequest`](#DecrementVolumeRequest)                           | Request  | 대상 기기가 지정한 값만큼 볼륨 크기를 낮추도록 Clova home extension에게 요청합니다. |
| [`GetAirQualityRequest`](#GetAirQualityRequest)                               | Request  | 대상 기기가 측정한 공기질 정보를 Clova Home extension에게 요청합니다. |
| [`GetAirQualityResponse`](#GetAirQualityResponse)                             | Response | [`GetAirQualityRequest`](#GetAirQualityRequest) 메시지에 대한 응답으로 대상 기기가 측정한 공기질 정보를 CEK에게 전달합니다. |
| [`GetAsleepDurationRequest`](#GetAsleepDurationRequest)                       | Request  | 주로 수면 센서에서 측정된 정보를 확인할 때 사용되며, 대상 기기가 측정한 사용자의 수면 시간을 Clova Home extension에게 요청합니다.  |
| [`GetAsleepDurationResponse`](#GetAsleepDurationResponse)                     | Response | [`GetAsleepDurationRequest`](#GetAsleepDurationRequest) 메시지에 대한 응답으로 대상 기기가 측정한 사용자의 수면 시간을 CEK에게 전달합니다.  |
| [`GetAwakeDurationRequest`](#GetAwakeDurationRequest)                         | Request  | 주로 수면 센서에서 측정된 정보를 확인할 때 사용되며, 대상 기기가 측정한 사용자의 취침 후 비수면 시간, 즉 사용자가 취침을 시작한 순간부터 수면에 진입한 순간까지의 시간을 Clova Home extension에게 요청합니다.  |
| [`GetAwakeDurationResponse`](#GetAwakeDurationResponse)                       | Response | [`GetAwakeDurationRequest`](#GetAwakeDurationRequest) 메시지에 대한 응답으로 대상 기기가 측정한 사용자의 취침 후 비수면 시간, 즉 사용자가 취침을 시작한 순간부터 수면에 진입한 순간까지의 시간을 CEK에게 전달합니다.  |
| [`GetBatteryInfoRequest`](#GetBatteryInfoRequest)                             | Request  | 대상 기기의 배터리 정보를 Clova Home extension에게 요청합니다. |
| [`GetBatteryInfoResponse`](#GetBatteryInfoResponse)                           | Response | [`GetBatteryInfoRequest`](#GetBatteryInfoRequest) 메시지에 대한 응답으로 대상 기기의 배터리 정보를 CEK에게 전달합니다. |
| [`GetCleaningCycleRequest`](#GetCleaningCycleRequest)                         | Request  | 기기의 세척 주기를 확인할 때 사용되며, 대상 기기의 다음 세척 주기까지 남은 시간에 대한 정보를 Clova Home extension에게 요청합니다.  |
| [`GetCleaningCycleResponse`](#GetCleaningCycleResponse)                       | Response | [`GetCleaningCycleRequest`](#GetCleaningCycleRequest) 메시지에 대한 응답으로 대상 기기의 다음 세척 주기까지 남은 시간을 CEK에게 전달합니다.  |
| [`GetCloseTimeRequest`](#GetCloseTimeRequest)                                 | Request  | 주로 열림 감지 센서가 감지한 내용 중 감지 대상이 마지막으로 닫혔던 시점의 시간 정보를 Clova Home extension에게 요청합니다. |
| [`GetCloseTimeResponse`](#GetCloseTimeResponse)                               | Response | [`GetCloseTimeRequest`](#GetCloseTimeRequest) 메시지에 대한 응답으로 대상 기기가 감지한 내용 중 감지 대상이 마지막으로 닫혔던 시점의 시간 정보를 CEK에게 전달합니다.  |
| [`GetConsumptionRequest`](#GetConsumptionRequest)                             | Request  | 주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 현재까지 측정된 에너지 또는 자원 사용량을 확인할 때 사용되며, 대상 기기가 측정한 에너지 또는 자원 사용량 정보를 Clova Home extension에게 요청합니다.  |
| [`GetConsumptionResponse`](#GetConsumptionResponse)                           | Response | [`GetConsumptionRequest`](#GetConsumptionRequest) 메시지에 대한 응답으로 대상 기기가 현재까지 측정한 에너지 또는 자원 사용량 정보를 CEK에게 전달합니다.  |
| [`GetCurrentBillRequest`](#GetCurrentBillRequest)                             | Request  | 주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 측정된 현재까지의 사용량의 기반으로 요금을 확인할 때 사용되며, 대상 기기가 측정한 요금 정보를 Clova Home extension에게 요청합니다.  |
| [`GetCurrentBillResponse`](#GetCurrentBillResponse)                           | Response | [`GetCurrentBillRequest`](#GetCurrentBillRequest) 메시지에 대한 응답으로 대상 기기가 현재까지 측정한 요금 정보를 CEK에게 전달합니다.   |
| [`GetCurrentTemperatureRequest`](#GetCurrentTemperatureRequest)               | Request  | 대상 기기가 측정한 현재 온도 정보를 Clova Home extension에게 요청합니다. |
| [`GetCurrentTemperatureResponse`](#GetCurrentTemperatureResponse)             | Response | [`GetCurrentTemperatureRequest`](#GetCurrentTemperatureRequest) 메시지에 대한 응답으로 대상 기기가 측정한 현재 온도 정보를 CEK에게 전달합니다. |
| [`GetDeviceStateRequest`](#GetDeviceStateRequest)                             | Request  | 대상 기기가 제공하는 모든 상태 정보를 확인할 때 사용됩니다.  |
| [`GetDeviceStateResponse`](#GetDeviceStateResponse)                           | Response | [`GetDeviceStateRequest`](#GetDeviceStateRequest) 메시지에 대한 응답으로 대상 기기가 제공하는 모든 상태 정보를 CEK에게 전달합니다.  |
| [`GetEstimateBillRequest`](#GetEstimateBillRequest)                           | Request  | 주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 측정된 사용량의 기반으로 예상 요금을 확인할 때 사용되며, 대상 기기가 예측한 요금 정보를 Clova Home extension에게 요청합니다.  |
| [`GetEstimateBillResponse`](#GetEstimateBillResponse)                         | Response | [`GetEstimateBillRequest`](#GetEstimateBillRequest) 메시지에 대한 응답으로 대상 기기가 예측한 요금 정보를 CEK에게 전달합니다.  |
| [`GetEstimateConsumptionRequest`](#GetEstimateConsumptionRequest)             | Request  | 주로 스마트 플러그나 스마트 멀티탭과 같은 기기에서 예상되는 에너지 또는 자원 사용량을 확인할 때 사용되며, 대상 기기가 예측한 에너지 또는 자원 사용량 정보를 Clova Home extension에게 요청합니다.  |
| [`GetEstimateConsumptionResponse`](#GetEstimateConsumptionResponse)           | Response | [`GetEstimateConsumptionRequest`](#GetEstimateConsumptionRequest) 메시지에 대한 응답으로 대상 기기가 현재까지 측정한 에너지 또는 자원 정보를 CEK에게 전달합니다.  |
| [`GetExpendableStateRequest`](#GetExpendableStateRequest)                     | Request  | 기기의 필터나 소모품의 사용량이나 남은 수명을 확인할 때 사용되며, 대상 기기가 보유하고 있는 소모품의 사용량이나 수명 정보를 Clova extension에게 요청합니다.  |
| [`GetExpendableStateResponse`](#GetExpendableStateResponse)                   | Response | [`GetExpendableStateRequest`](#GetExpendableStateRequest) 메시지에 대한 응답으로 대상 기기가 제공하는 모든 소모품의 사용량이나 수명 정보를 CEK에게 전달합니다. |
| [`GetFineDustRequest`](#GetFineDustRequest)                                   | Request  | 대상 기기가 측정한 미세 먼지(PM10) 정보를 Clova Home extension에게 요청합니다. |
| [`GetFineDustResponse`](#GetFineDustResponse)                                 | Response | [`GetFineDustRequest`](#GetFineDustRequest) 메시지에 대한 응답으로 대상 기기가 측정한 미세 먼지(PM10) 정보를 CEK에게 전달합니다. |
| [`GetHumidityRequest`](#GetHumidityRequest)                                   | Request  | 대상 기기가 측정한 습도 정보를 Clova Home extension에게 요청합니다. |
| [`GetHumidityResponse`](#GetHumidityResponse)                                 | Response | [`GetHumidityRequest`](#GetHumidityRequest) 메시지에 대한 응답으로 대상 기기가 측정한 습도 정보를 CEK에게 전달합니다. |
| [`GetKeepWarmTimeRequest`](#GetKeepWarmTimeRequest)                           | Request  | 밥솥과 같은 기기에서 음식의 보온에 사용된 시간을 확인할 때 사용되며, 대상 기기가 보온 모드를 유지한 시간 정보를 Clova Home extension에게 요청합니다.  |
| [`GetKeepWarmTimeResponse`](#GetKeepWarmTimeResponse)                         | Response | [`GetKeepWarmTimeRequest`](#GetKeepWarmTimeRequest) 메시지에 대한 응답으로 대상 기기가 보온 모드를 유지한 시간 정보를 CEK에게 전달합니다.  |
| [`GetLockStateRequest`](#GetLockStateRequest)                                 | Request  | 주로 스마트 밸브와 같은 기기의 상태를 확인할 때 사용되며, 대상 기기가 가진 잠금 장치의 현재 잠금 상태 정보를 Clova Home extension에게 요청합니다.  |
| [`GetLockStateResponse`](#GetLockStateResponse)                               | Response | [`GetLockStateRequest`](#GetLockStateRequest) 메시지에 대한 응답으로 대상 기기가 가진 잠금 장치의 현재 잠금 상태를 CEK에게 전달합니다.  |
| [`GetOpenStateRequest`](#GetOpenStateRequest)                                 | Request  | 주로 열림 감지 센서가 감지한 내용 중 감지 대상의 현재 상태 정보(열림 또는 닫힘)를 Clova Home extension에게 요청합니다.  |
| [`GetOpenStateResponse`](#GetOpenStateResponse)                               | Response | [`GetOpenStateRequest`](#GetOpenStateRequest) 메시지에 대한 응답으로 주로 감지 대상의 현재 상태 정보(열림 또는 닫힘)를 CEK에게 전달합니다.  |
| [`GetOpenTimeRequest`](#GetOpenTimeRequest)                                   | Request  | 주로 열림 감지 센서가 감지한 내용 중 감지 대상이 마지막으로 열렸던 시점의 시간 정보를 Clova Home extension에게 요청합니다.   |
| [`GetOpenTimeResponse`](#GetOpenTimeResponse)                                 | Response | [`GetOpenTimeRequest`](#GetOpenTimeRequest) 메시지에 대한 응답으로 대상 기기가 감지한 내용 중 감지 대상이 마지막으로 열렸던 시점의 시간 정보를 CEK에게 전달합니다.  |
| [`GetPhaseRequest`](#GetPhaseRequest)                                         | Request  | 주로 밥솥이나 세탁기와 같이 동작 단계가 있는 기기에서 현재 동작 단계 정보를 확인할 때 사용되며, 대상 기기의 현재 동작 단계 정보를 Clova Home extension에게 요청합니다.  |
| [`GetPhaseResponse`](#GetPhaseResponse)                                       | Response | [`GetPhaseRequest`](#GetPhaseRequest) 메시지에 대한 응답으로 대상 기기의 현재 동작 단계 정보를 CEK에게 전달합니다.  |
| [`GetProgressiveTaxBracketRequest`](#GetProgressiveTaxBracketRequest)         | Request  | 주로 전기 계량기나 스마트 플러그와 같은 기기에서 누진세 단계를 확인할 때 사용되며, 대상 기기가 판단한 누진세 단계 정보를 Clova Home extension에게 요청합니다.  |
| [`GetProgressiveTaxBracketResponse`](#GetProgressiveTaxBracketResponse)         | Response | [`GetProgressiveTaxBracketRequest`](#GetProgressiveTaxBracketRequest) 메시지에 대한 응답으로 대상 기기가 판단한 누진세 단계 정보를 CEK에게 전달합니다. |
| [`GetRemainingTimeRequest`](#GetRemainingTimeRequest)                         | Request  | 주로 밥솥이나 세탁기와 같은 기기에서 동작 종료까지 남은 시간을 확인할 때 사용되며, 대상 기기의 동작 종료까지 남은 시간에 대한 정보를 Clova Home extension에게 요청합니다.  |
| [`GetRemainingTimeResponse`](#GetRemainingTimeResponse)                       | Response | [`GetRemainingTimeRequest`](#GetRemainingTimeRequest) 메시지에 대한 응답으로 대상 기기가 동작 종료하기까지 남은 시간을 CEK에게 전달합니다. |
| [`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest)                 | Request  | 사용자가 바른 자세로 대상 기기를 사용한 비율이 얼마인지 확인할 때 사용하며, 사용자가 대상 기기를 사용할 때 특정 기간이나 현재까지 바른 자세를 유지한 비율 정보를 Clova Home extension에게 요청합니다.  |
| [`GetRightPostureRatioResponse`](#GetRightPostureRatioResponse)               | Response | [`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest) 메시지에 대한 응답으로 사용자가 대상 기기를 바른 자세로 사용한 비율 정보를 CEK에게 전달합니다.  |
| [`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest)             | Request  | 스마트 의자와 같은 기기에서 사용자의 사용 상태를 확인할 때 사용되며, 대상 기기가 사용자 착석 여부를 감지한 정보와 최근 사용자가 사용한 시간 정보를 Clova Home extension에게 요청합니다.  |
| [`GetCurrentSittingStateResponse`](#GetCurrentSittingStateResponse)           | Response | [`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest) 메시지에 대한 응답으로 대상 기기가 사용자 착석 여부를 감지한 정보와 최근 사용자가 사용한 시간 정보를 CEK에게 전달합니다.  |
| [`GetSleepScoreRequest`](#GetSleepScoreRequest)                               | Request  | 수면 센서와 같은 기기에서 사용자 수면 점수 정보를 확인할 때 사용되며, 대상 기기가 평가한 사용자의 수면 점수를 Clova Home extension에게 요청합니다.  |
| [`GetSleepScoreResponse`](#GetSleepScoreResponse)                             | Response | [`GetSleepScoreRequest`](#GetSleepScoreRequest) 메시지에 대한 응답으로 대상 기기가 평가한 사용자의 수면 점수를 CEK에게 전달합니다.  |
| [`GetSleepStartTimeRequest`](#GetSleepStartTimeRequest)                       | Request  | 수면 센서와 같은 기기에서 사용자 수면 점수 정보를 확인할 때 사용되며, 대상 기기가 측정한 사용자의 수면 시작 시간을 Clova Home extension에게 요청합니다.  |
| [`GetSleepStartTimeResponse`](#GetSleepStartTimeRequest)                      | Response | [`GetSleepStartTimeRequest`](#GetSleepStartTimeRequest) 메시지에 대한 응답으로 대상 기기가 측정한 사용자의 수면 시작 시간을 CEK에게 전달합니다.  |
| [`GetTargetTemperatureRequest`](#GetTargetTemperatureRequest)                 | Request  | 대상 기기가 설정한 희망 온도 정보를 Clova Home extension에게 요청합니다. |
| [`GetTargetTemperatureResponse`](#GetTargetTemperatureResponse)               | Response | [`GetTargetTemperatureRequest`](#GetTargetTemperatureRequest) 메시지에 대한 응답으로 대상 기기가 설정한 희망 온도 정보를 CEK에게 전달합니다. |
| [`GetUltraFineDustRequest`](#GetUltraFineDustRequest)                         | Request  | 대상 기기가 측정한 초미세 먼지(PM2.5) 정보를 Clova Home extension에게 요청합니다. |
| [`GetUltraFineDustResponse`](#GetUltraFineDustResponse)                       | Response | [`GetUltraFineDustRequest`](#GetUltraFineDustRequest) 메시지에 대한 응답으로 대상 기기가 측정한 초미세 먼지(PM2.5) 정보를 CEK에게 전달합니다. |
| [`GetUsageTimeRequest`](#GetUsageTimeRequest)                                 | Request | 사용자가 대상 기기를 얼마나 사용했는지 확인할 때 사용하며, 대상 기기가 특정 기간이나 현재까지 누적 사용된 시간 정보를 Clova Home extension에게 요청합니다.  |
| [`GetUsageTimeResponse`](#GetUsageTimeResponse)                               | Response | [`GetUsageTimeRequest`](#GetUsageTimeRequest) 메시지에 대한 응답으로 대상 기기가 사용된 시간 정보를 CEK에게 전달합니다.  |
| [`HealthCheckRequest`](#HealthCheckRequest)                                   | Request  | 지정한 기기의 상태를 파악할 때 사용되며, 대상 기기의 상태 정보를 Clova Home extension에게 요청합니다. |
| [`HealthCheckResponse`](#HealthCheckResponse)                                 | Response | [`HealthCheckRequest`](#HealthCheckRequest) 메시지에 대한 응답으로 지정한 기기의 상태 정보를 CEK에게 전달합니다. |
| [`IncrementBrightnessConfirmation`](#IncrementBrightnessConfirmation)         | Response | [`IncrementBrightnessRequest`](#IncrementBrightnessRequest) 메시지에 대한 응답으로 대상 기기가 조명 밝기를 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`IncrementBrightnessRequest`](#IncrementBrightnessRequest)                   | Request  | 대상 기기가 지정한 수준만큼 조명의 밝기를 높이도록 Clova Home extension에게 요청합니다. |
| [`IncrementChannelConfirmation`](#IncrementChannelConfirmation)               | Response | [`IncrementChannelRequest`](#IncrementChannelRequest) 메시지에 대한 응답으로 대상 기기가 TV 채널을 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`IncrementChannelRequest`](#IncrementChannelRequest)                         | Request  | 대상 기기가 지정한 수준만큼 TV 채널을 높이도록 Clova Home extension에게 요청합니다. |
| [`IncrementFanSpeedConfirmation`](#IncrementFanSpeedConfirmation)             | Response | [`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest) 메시지에 대한 응답으로 대상 기기가 팬의 속도를 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest)                       | Request | 대상 기기가 지정한 값만큼 팬 속도를 높이도록 Clova Home extension에게 요청합니다. |
| [`IncrementIntensityLevelConfirmation`](#IncrementIntensityLevelConfirmation) | Response | [`IncrementIntensityLevelRequest`](#IncrementIntensityLevelRequest) 메시지에 대한 응답으로 대상 기기가 압력이나 수압 등의 세기를 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다.  |
| [`IncrementIntensityLevelRequest`](#IncrementIntensityLevelRequest)           | Request  | 대상 기기가 지정한 값만큼 압력이나 수압의 세기를 높이도록 Clova Home extension에게 요청합니다. |
| [`IncrementTargetTemperatureConfirmation`](#IncrementTargetTemperatureConfirmation) | Response | [`IncrementTargetTemperatureRequest`](#IncrementTargetTemperatureRequest) 메시지에 대한 응답으로 대상 기기가 온도를 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`IncrementTargetTemperatureRequest`](#IncrementTargetTemperatureRequest)     | Request  | 대상 기기가 지정한 값만큼 온도를 높이도록 Clova Home extension에게 요청합니다.     |
| [`IncrementVolumeConfirmation`](#IncrementVolumeConfirmation)                 | Response | [`IncrementVolumeRequest`](#IncrementVolumeRequest) 메시지에 대한 응답으로 대상 기기가 스피커 볼륨을 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`IncrementVolumeRequest`](#IncrementVolumeRequest)                           | Request | 대상 기기가 지정한 값만큼 볼륨 크기를 높이도록 Clova Home extension에게 요청합니다. |
| [`LowerConfirmation`](#LowerConfirmation)                                     | Response | [`LowerRequest`](#LowerRequest) 메시지에 대한 응답으로 대상 기기의 높낮이를 낮추도록 요청한 후 처리된 결과를 CEK에게 전달합니다.  |
| [`LowerRequest`](#LowerRequest)                                               | Request  | 주로 커튼이나 블라인드, 침대 같은 기기를 제어할 때 사용되며, 대상 기기의 높낮이를 내리도록 Clova Home extension에게 요청합니다.  |
| [`MuteConfirmation`](#MuteConfirmation)                                       | Response | [`MuteRequest`](#MuteRequest) 메시지에 대한 응답으로 대상 기기의 소리를 끄도록 설정(음소거)한 결과를 CEK에게 전달합니다. |
| [`MuteRequest`](#MuteRequest)                                                 | Request  | 대상 기기의 소리를 끄도록(음소거) Clova Home extension에게 요청합니다. |
| [`OpenConfirmation`](#OpenConfirmation)                                       | Response | [`OpenRequest`](#OpenRequest) 메시지에 대한 응답으로 스마트 커튼이 일광 차단을 해제하거나, 비데의 뚜껑을 열도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`OpenRequest`](#OpenRequest)                                                 | Request  | 스마트 커튼이나 비데 등의 제품을 제어할 때 사용되며, 스마트 커튼이 일광 차단을 해제하거나, 비데의 뚜껑을 열도록 Clova Home extension에게 요청합니다.  |
| [`PreheatConfirmation`](#PreheatConfirmation)                                 | Response | [`PreheatRequest`](#PreheatRequest) 메시지에 대한 응답으로 예열 요청을 처리한 후 그 결과를 CEK에게 전달합니다.  |
| [`PreheatRequest`](#PreheatRequest)                                           | Response | 주로 오븐과 같은 기기를 제어할 때 사용되며, 대상 기기가 예열하도록 Clova Home extension에게 요청합니다.                        |
| [`RaiseConfirmation`](#RaiseConfirmation)                                     | Response | [`RaiseRequest`](#RaiseRequest) 메시지에 대한 응답으로 대상 기기의 높낮이를 높이도록 요청한 후 처리된 결과를 CEK에게 전달합니다.  |
| [`RaiseRequest`](#RaiseRequest)                                               | Request  | 주로 커튼이나 블라인드, 침대 같은 기기를 제어할 때 사용되며, 대상 기기의 높낮이를 높이도록 Clova Home extension에게 요청합니다.  |
| [`ReleaseModeConfirmation`](#ReleaseModeConfirmation)                         | Response | [`ReleaseModeRequest`](#ReleaseModeRequest) 메시지에 대한 응답으로 현재 기기의 운전 모드(operation mode)를 해제하도록 요청한 후 처리된 결과를 CEK에게 전달합니다.  |
| [`ReleaseModeRequest`](#ReleaseModeRequest)                                   | Request  | 현재 기기에 설정된 운전 모드(operation mode)를 해제할 때 사용되며, 기기의 운전 모드를 해제하여 이전 운전 모드나 기본 운전 모드로 돌아가도록 Clova Home extension에게 요청합니다.  |
| [`SetBrightnessConfirmation`](#SetBrightnessConfirmation)                     | Response | [`SetBrightnessRequest`](#SetBrightnessRequest) 메시지에 대한 응답으로 조명 밝기를 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`SetBrightnessRequest`](#SetBrightnessRequest)                               | Request  | 대상 기기가 조명 밝기를 지정한 값으로 변경하도록 Clova Home extension에게 요청합니다. |
| [`SetChannelByNameConfirmation`](#SetChannelByNameConfirmation)               | Response | [`SetChannelByNameRequest`](#SetChannelByNameRequest) 메시지에 대한 응답으로 채널 이름으로 TV 채널을 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`SetChannelByNameRequest`](#SetChannelByNameRequest)                         | Request  | 대상 기기가 지정한 채널 이름으로 채널을 변경하도록 Clova Home extension에게 요청합니다. |
| [`SetChannelConfirmation`](#SetChannelConfirmation)                           | Response | [`SetChannelRequest`](#SetChannelRequest) 메시지에 대한 응답으로 채널 번호로 TV 채널을 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`SetChannelRequest`](#SetChannelRequest)                                     | Request  | 대상 기기가 지정한 채널 번호로 TV 채널을 변경하도록 Clova Home extension에게 요청합니다. |
| [`SetColorConfirmation`](#SetColorConfirmation)                               | Response | [`SetColorRequest`](#SetColorRequest) 메시지에 대한 응답으로 대상기기의 조명이나 화면, 전등의 색을 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`SetColorRequest`](#SetColorRequest)                                         | Request  | 주로 스마트 전등과 같은 기기를 제어할 때 사용되며, 대상 기기의 조명이나 화면, 전등의 색을 변경하도록 Clova Home extension에게 요청합니다.  |
| [`SetColorTemperatureConfirmation`](#SetColorTemperatureConfirmation)         | Response | [`SetColorTemperatureRequest`](#SetColorTemperatureRequest) 메시지에 대한 응답으로 대상기기의 조명이나 화면, 전등의 색온도를 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다.  |
| [`SetColorTemperatureRequest`](#SetColorTemperatureRequest)                   | Request  | 주로 스마트 전등과 같은 기기를 제어할 때 사용되며, 대상 기기의 조명이나 화면, 전등의 색온도를 변경하도록 Clova Home extension에게 요청합니다.  |
| [`SetFanSpeedConfirmation`](#SetFanSpeedConfirmation)                         | Response | [`SetFanSpeedRequest`](#SetFanSpeedRequest) 메시지에 대한 응답으로 팬 속도를 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`SetFanSpeedRequest`](#SetFanSpeedRequest)                                   | Request  | 대상 기기가 지정한 값으로 팬 속도를 변경하도록 Clova Home extension에게 요청합니다. |
| [`SetLockStateConfirmation`](#SetLockStateConfirmation)                       | Response | [`SetLockStateRequest`](#SetLockStateRequest) 메시지에 대한 응답으로 대상 기기가 잠기거나 열리도록 요청한 후 처리된 결과를 CEK에게 전달합니다.  |
| [`SetLockStateRequest`](#SetLockStateRequest)                                 | Request  | 대상 기기를 잠그거나 열도록 Clova Home extension에게 요청합니다.  |
| [`SetModeConfirmation`](#SetModeConfirmation)                                 | Response | [`SetModeRequest`](#SetModeRequest) 메시지에 대한 응답으로 운전 모드(operation mode)를 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`SetModeRequest`](#SetModeRequest)                                           | Request  | 대상 기기가 지정한 모드로 운전 모드(operation mode)를 변경하도록 Clova Home extension에게 요청합니다. |
| [`SetTargetTemperatureConfirmation`](#SetTargetTemperatureConfirmation)       | Response | [`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest) 메시지에 대한 응답으로 희망 온도를 변경하도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest)                 | Request  | 대상 기기가 희망 온도를 지정한 값으로 변경하도록 Clova Home extension에게 요청합니다. |
| [`StopConfirmation`](#StopConfirmation)                                       | Response | [`StopRequest`](#StopRequest) 메시지에 대한 응답으로 대상 기기에게 동작 중지를 요청한 결과를 CEK에게 전달합니다.  |
| [`StopRequest`](#StopRequest)                                                 | Request  | 기기의 현재 동작을 중지하도록 Clova Home extension에게 요청합니다.  |
| [`TurnOffConfirmation`](#TurnOffConfirmation)                                 | Response | [`TurnOffRequest`](#TurnOffRequest) 메시지에 대한 응답으로 대상 기기를 끄도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`TurnOffRequest`](#TurnOffRequest)                                           | Request  | 대상 기기를 끄도록 Clova Home extension에게 요청합니다.                        |
| [`TurnOnConfirmation`](#TurnOnConfirmation)                                   | Response | [`TurnOnRequest`](#TurnOnRequest) 메시지에 대한 응답으로 대상 기기를 켜도록 요청한 후 처리된 결과를 CEK에게 전달합니다. |
| [`TurnOnRequest`](#TurnOnRequest)                                             | Request  | 대상 기기를 켜도록 Clova Home extension에게 요청합니다.                        |
| [`UnmuteConfirmation`](#UnmuteConfirmation)                                   | Response | [`UnmuteRequest`](#UnmuteRequest) 메시지에 대한 응답으로 대상 기기의 소리를 켜도록 설정(음소거 해제)한 결과를 CEK에게 전달합니다. |
| [`UnmuteRequest`](#UnmuteRequest)                                             | Request  | 대상 기기의 소리를 켜도록(음소거 해제) Clova Home extension에게 요청합니다. |

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Charge.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Close.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Close.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/DecrementBrightness.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/DecrementFanSpeed.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/DecrementIntensityLevel.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/DecrementTargetTemperature.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/DecrementVolume.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetAirQuality.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetAsleepDuration.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetAwakeDuration.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetBatteryInfo.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetCleaningCycle.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetCloseTime.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetConsumption.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetCurrentBill.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetCurrentTemperature.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetDeviceState.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetEstimateBill.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetEstimateConsumption.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetExpendableState.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetFineDust.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetHumidity.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetKeepWarmTime.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetLockState.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetOpenState.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetOpenTime.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetPhase.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetProgressiveTaxBracket.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetRemainingTime.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetRightPostureRatio.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetCurrentSittingState.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetSleepScore.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetSleepStartTime.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetTargetTemperature.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetUltraFineDust.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/GetUsageTime.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/HealthCheck.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/IncrementBrightness.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/IncrementChannel.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/IncrementFanSpeed.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/IncrementIntensityLevel.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/IncrementTargetTemperature.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/IncrementVolume.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Lower.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Mute.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Open.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Preheat.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Raise.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/ReleaseMode.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/SetBrightness.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/SetChannelByName.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/SetChannel.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/SetColor.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/SetColorTemperature.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/SetFanSpeed.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/SetLockState.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/SetMode.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/SetTargetTemperature.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Stop.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/TurnOff.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/TurnOn.md" %}

{% include "/CEK/References/ClovaHomeInterface/ControlInterfacesPerAction/Unmute.md" %}
