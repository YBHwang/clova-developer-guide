# Control

These control interfaces are used to check IoT device information and carry out requests and responses for device control.

| Message name         | Type  | Description                                   |
|------------------|-----------|---------------------------------------------|
| [`ChangeInputSourceConfirmation`](#ChangeInputSourceConfirmation)             | Response |  Sends the result of requesting the target appliance to change the input source to CEK as a response to the [`ChangeInputSourceRequest`](#ChangeInputSourceRequest) message. |
| [`ChangeInputSourceRequest`](#ChangeInputSourceRequest)                       | Request  | Requests the Clova Home extension to change the input source. |
| [`ChargeConfirmation`](#ChargeConfirmation)                                   | Response |  Sends the result of requesting the target appliance to start charging the appliance to CEK as a response to the [`ChargeRequest`](#ChargeRequest) message.  |
| [`ChargeRequest`](#ChargeRequest)                                             | Request  | Requests the Clova Home extension to set the target appliance to self-charge. |
| [`CloseConfirmation`](#CloseConfirmation)                                     | Response |  Sends the result of closing the smart curtain or bidet lid to CEK as a response to the [`CloseRequest`](#CloseRequest) message. |
| [`CloseRequest`](#CloseRequest)                                               | Request  | Used to control appliances such as smart curtains or bidets. Requests the Clova Home extension to close the smart curtain or the bidet lid.  |
| [`DecrementBrightnessConfirmation`](#DecrementBrightnessConfirmation)         | Response |  Sends the result of requesting the target appliance to dim the lights to CEK as a response to the [`DecrementBrightnessRequest`](#DecrementBrightnessRequest) message. |
| [`DecrementBrightnessRequest`](#DecrementBrightnessRequest)                   | Request  | Requests the Clova Home extension to set the target appliance to dim the lights by the designated amount. |
| [`DecrementChannelConfirmation`](#DecrementChannelConfirmation)               | Response |  Sends the result of requesting the target appliance to channel down the TV to CEK as a response to the [`DecrementChannelRequest`](#DecrementChannelRequest) message. |
| [`DecrementChannelRequest`](#DecrementChannelRequest)                         | Request  | Requests the Clova Home extension to set the target appliance to channel down the TV by the designated amount. |
| [`DecrementFanSpeedConfirmation`](#DecrementFanSpeedConfirmation)             | Response |  Sends the result of requesting the target appliance to lower the fan speed to CEK as a response to the [`DecrementFanSpeedRequest`](#DecrementFanSpeedRequest) message. |
| [`DecrementFanSpeedRequest`](#DecrementFanSpeedRequest)                       | Request  | Requests the Clova Home extension to set the target appliance to lower the fan speed by the designated amount. |
| [`DecrementIntensityLevelConfirmation`](#DecrementIntensityLevelConfirmation) | Response |  Sends the result of requesting the target appliance to lower the pressure level, such as air or water pressure, to CEK as a response to the [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest) message.  |
| [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest)           | Request  | Mainly used to control appliances such as air conditioners and thermostats. Requests the Clova Home extension set the target appliance to decrease the pressure level, such as air or water pressure, by the designated amount.  |
| [`DecrementTargetTemperatureConfirmation`](#DecrementTargetTemperatureConfirmation) | Response |  Sends the result of requesting the target appliance to reduce the temperature to CEK as a response to the [`DecrementTargetTemperatureRequest`](#DecrementTargetTemperatureRequest) message. |
| [`DecrementTargetTemperatureRequest`](#DecrementTargetTemperatureRequest)     | Request  | Requests the Clova Home extension to set the target appliance to lower the temperature by the designated amount.      |
| [`DecrementVolumeConfirmation`](#DecrementVolumeConfirmation)                 | Response |  Sends the result of requesting the target appliance to lower the speaker volume to CEK as a response to the [`DecrementVolumeRequest`](#DecrementVolumeRequest) message. |
| [`DecrementVolumeRequest`](#DecrementVolumeRequest)                           | Request  | Requests the Clova Home extension to set the target appliance to lower the speaker volume by the designated amount. |
| [`GetAirQualityRequest`](#GetAirQualityRequest)                               | Request  | Requests the Clova Home extension for the air quality information measured by the target appliance. |
| [`GetAirQualityResponse`](#GetAirQualityResponse)                             | Response |  Sends the air quality information measured by the target appliance to CEK as a response to the [`GetAirQualityRequest`](#GetAirQualityRequest) message. |
| [`GetAsleepDurationRequest`](#GetAsleepDurationRequest)                       | Request  | Mainly used o check information measured from a sleep sensor. Requests the Clova Home extension for the sleep time of the user measured by the target appliance.  |
| [`GetAsleepDurationResponse`](#GetAsleepDurationResponse)                     | Response |  Sends the duration of the user sleep time measured by the target appliance to CEK as a response to the [`GetAsleepDurationRequest`](#GetAsleepDurationRequest) message.  |
| [`GetAwakeDurationRequest`](#GetAwakeDurationRequest)                         | Request  | Mainly used o check information measured from a sleep sensor. Requests the Clova Home extension for the sleep onset latency measured by the target appliance–in other words, the amount of time from going to bed until falling asleep.  |
| [`GetAwakeDurationResponse`](#GetAwakeDurationResponse)                       | Response |  Sends the amount of time the measured by the target appliance of the user going to bed until falling asleep to CEK as a response to the [`GetAwakeDurationRequest`](#GetAwakeDurationRequest) message.  |
| [`GetBatteryInfoRequest`](#GetBatteryInfoRequest)                             | Request  | Requests the Clova Home extension for the battery information of the target appliance. |
| [`GetBatteryInfoResponse`](#GetBatteryInfoResponse)                           | Response |  Sends the battery information of the target appliance to CEK as a response to the [`GetBatteryInfoRequest`](#GetBatteryInfoRequest) message. |
| [`GetCleaningCycleRequest`](#GetCleaningCycleRequest)                                                   | Request  | Mainly used to check the cleaning cycle of an appliance. Requests the Clova Home extension for the information on the remaining time until the next cleaning cycle of the target appliance.  |
| [`GetCleaningCycleResponse`](#GetCleaningCycleResponse)                                                  | Response |  Sends the information on the remaining time until the next cleaning cycle of the target appliance to CEK as a response to the [`GetCleaningCycleRequest`](#GetCleaningCycleRequest) message.  |
| [`GetCloseTimeRequest`](#GetCloseTimeRequest)                                 | Request  | Requests the Clova Home extension for the recent close time of the target, mainly from the detection details of the open-close sensor. |
| [`GetCloseTimeResponse`](#GetCloseTimeResponse)                               | Response |  Sends the recent close time of the target from the detection details of the open-close sensor to CEK response to the [`GetCloseTimeRequest`](#GetCloseTimeRequest) message.  |
| [`GetConsumptionRequest`](#GetConsumptionRequest)                             | Request  | Mainly used to check for energy consumption or resource information to date measured from appliances such as smart plugs or smart power strips. Requests the Clova Home extension for the energy consumption or resource information measured from an appliance.  |
| [`GetConsumptionResponse`](#GetConsumptionResponse)                           | Response |  Sends the information on energy consumption or resource information measured by the target appliance to date to CEK as a response to the [`GetConsumptionRequest`](#GetConsumptionRequest) message.  |
| [`GetCurrentBillRequest`](#GetCurrentBillRequest)                             | Request  | Mainly used to check billing information based on energy consumption to date measured from appliances such as smart plugs or smart power strips. Requests the Clova Home extension for the billing information measured by the target appliance.  |
| [`GetCurrentBillResponse`](#GetCurrentBillResponse)                           | Response |  Sends the information on billing measured by the target appliance to date to CEK as a response to the [`GetCurrentBillRequest`](#GetCurrentBillRequest) message.   |
| [`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest)             | Request  | Used to check the use states of the user in appliances such as a smart chair. Requests the Clova Home Extension for the sit-down information of the user detected by the target appliance and the latest time of use.  |
| [`GetCurrentSittingStateResponse`](#GetCurrentSittingStateResponse)           | Response |  Sends the sit-down information of the user detected by the target appliance and the latest time of use to CEK as a response to the [`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest) message.  |
| [`GetCurrentTemperatureRequest`](#GetCurrentTemperatureRequest)               | Request  | Requests the Clova Home extension for the current temperature measured by the target appliance. |
| [`GetCurrentTemperatureResponse`](#GetCurrentTemperatureResponse)             | Response |  Sends the information on current temperature measured by the target appliance to CEK as a response to the [`GetCurrentTemperatureRequest`](#GetCurrentTemperatureRequest) message. |
| [`GetDeviceStateRequest`](#GetDeviceStateRequest)                             | Request  | Used to check all state information provided by the target appliance.  |
| [`GetDeviceStateResponse`](#GetDeviceStateResponse)                           | Response |  Sends all state information provided by the target appliance to CEK as a response to the [`GetDeviceStateRequest`](#GetDeviceStateRequest) message.  |
| [`GetEstimateBillRequest`](#GetEstimateBillRequest)                           | Request  | Mainly used to check the estimated billing based on energy usage measured from appliances such as smart plugs or smart power strips. Requests the Clova Home Extension for the estimated billing information.  |
| [`GetEstimateBillResponse`](#GetEstimateBillResponse)                         | Response |  Sends the estimated billing information measure by the target appliance to CEK as a response to the [`GetEstimateBillRequest`](#GetEstimateBillRequest) message.  |
| [`GetExpendableStateRequest`](#GetExpendableStateRequest)                     | Request  | Used to check the amount of usage or remaining lifespan on appliances such as filters or parts. Requests the Clova Home extension for information on usage and remaining lifespan on parts of the target appliance.  |
| [`GetExpendableStateResponse`](#GetExpendableStateResponse)                   | Response |  Sends the information on usage or remaining lifespan of all parts of the target appliance to CEK as a response to the [`GetExpendableStateRequest`](#GetExpendableStateRequest) message. |
| [`GetFineDustRequest`](#GetFineDustRequest)                                   | Request  | Requests the Clova Home extension for the information on fine dust (PM10) measured by the target appliance. |
| [`GetFineDustResponse`](#GetFineDustResponse)                                 | Response |  Sends the information on fine dust (PM10) measured by the target appliance to CEK as a response to the [`GetFineDustRequest`](#GetFineDustRequest) message. |
| [`GetHumidityRequest`](#GetHumidityRequest)                                   | Request  | Requests the Clova Home extension for the information on humidity measured by the target appliance. |
| [`GetHumidityResponse`](#GetHumidityResponse)                                 | Response |  Sends the information on humidity measured by the target appliance to CEK as a response to the [`GetHumidityRequest`](#GetHumidityRequest) message. |
| [`GetKeepWarmTimeRequest`](#GetKeepWarmTimeRequest)                           | Request  | Mainly used to check the time spent on the food warming mode of appliances such as rice cookers. Requests the Clova Home extension for the time spent on the warming mode on the target appliance.  |
| [`GetKeepWarmTimeResponse`](#GetKeepWarmTimeResponse)                         | Response |  Sends the information on the time spent on the warming mode of the target appliance to CEK as a response to the [`GetKeepWarmTimeRequest`](#GetKeepWarmTimeRequest) message.  |
| [`GetLockStateRequest`](#GetLockStateRequest)                                 | Request  | Mainly used to check the appliance state such as a smart valve. Requests the Clova Home extension for the current lock state of the lock device on the target appliance.  |
| [`GetLockStateResponse`](#GetLockStateResponse)                               | Response |  Sends the information on the current lock state of the lock device on the target appliance to CEK as a response to the [`GetLockStateRequest`](#GetLockStateRequest) message.  |
| [`GetOpenStateRequest`](#GetOpenStateRequest)                                 | Request  | Requests the Clova Home extension for the current state information of the detection target (open or close), mainly from the detection details of the open-close sensor.  |
| [`GetOpenStateResponse`](#GetOpenStateResponse)                               | Response |  Sends the current state information (open/close) of the detection target to CEK as a response to the [`GetOpenStateRequest`](#GetOpenStateRequest) message.  |
| [`GetOpenTimeRequest`](#GetOpenTimeRequest)                                   | Request  | Requests the Clova Home extension for the recent open time of the target, mainly from the detection details of the open-close sensor.   |
| [`GetOpenTimeResponse`](#GetOpenTimeResponse)                                 | Response |  Sends the recent open time of the target from the detection details of the open-close sensor to CEK as a response to the [`GetOpenTimeRequest`](#GetOpenTimeRequest) message.  |
| [`GetPhaseRequest`](#GetPhaseRequest)                                         | Request  | Mainly used to check the action phase of appliances that operate in phases such as rice cookers or washers. Requests the Clova Home extension for the current action phase of the target appliance.  |
| [`GetPhaseResponse`](#GetPhaseResponse)                                       | Response |  Sends the current action phase of the target appliance to CEK as a response to the [`GetPhaseRequest`](#GetPhaseRequest) message.  |
| [`GetProgressiveTaxBracketRequest`](#GetProgressiveTaxBracketRequest)         | Request  | Mainly used to check the progressive tax bracket in appliances such as smart meters or smart plugs. Requests the Clova Home extension for the progressive tax bracket determined by the target appliance.  |
| [`GetProgressiveTaxBracketResponse`](#GetProgressiveTaxBracketResponse)         | Response |  Sends the information on the progressive tax bracket determined by the target appliance to CEK as a response to the [`GetProgressiveTaxBracketRequest`](#GetProgressiveTaxBracketRequest) message. |
| [`GetRemainingTimeRequest`](#GetRemainingTimeRequest)                         | Request  | Mainly used to check the remaining time until the end of an action on appliances such as rice cookers or washers. Requests the Clova Home extension for the remaining time until the end of the action of the target appliance.  |
| [`GetRemainingTimeResponse`](#GetRemainingTimeResponse)                       | Response |  Sends the information on the time remaining until the end of the action of the target appliance to CEK as a response to the [`GetRemainingTimeRequest`](#GetRemainingTimeRequest) message. |
| [`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest)                 | Request  | Used to check the ratio of a user using the target appliance in good posture. Requests the Clova Home extension for the ratio of the user using the target appliance in good posture during a specific or whole period of use.  |
| [`GetRightPostureRatioResponse`](#GetRightPostureRatioResponse)               | Response |  Sends the information on the ratio of a user using the target appliance in good posture to CEK as a response to the [`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest) message.  |
| [`GetSleepScoreRequest`](#GetSleepScoreRequest)                               | Request  | Mainly used to check the sleep score of the user in appliances such as a sleep sensor. Requests the Clova Home extension for the sleep time of the user measured by the target appliance.  |
| [`GetSleepScoreResponse`](#GetSleepScoreResponse)                             | Response |  Sends the sleep score of the user assessed by the target appliance to CEK as a response to the [`GetSleepScoreRequest`](#GetSleepScoreRequest) message.  |
| [`GetSleepStartTimeRequest`](#GetSleepStartTimeRequest)                       | Request  | Mainly used to check the sleep score of the user in appliances such as a sleep sensor. Requests the Clova Home extension for the sleep start time of the user measured by the target appliance.  |
| [`GetSleepStartTimeResponse`](#GetSleepStartTimeRequest)                      | Response |  Sends the information on sleep onset time of the user measured by the target appliance to CEK as a response to the [`GetSleepStartTimeRequest`](#GetSleepStartTimeRequest) message.  |
| [`GetTargetTemperatureRequest`](#GetTargetTemperatureRequest)                 | Request  | Requests the Clova Home extension for the desired temperature set by the target appliance. |
| [`GetTargetTemperatureResponse`](#GetTargetTemperatureResponse)               | Response |  Sends the information on the desired temperature set by the target appliance to CEK as a response to the [`GetTargetTemperatureRequest`](#GetTargetTemperatureRequest) message. |
| [`GetUltraFineDustRequest`](#GetUltraFineDustRequest)                         | Request  | Requests the Clova Home extension for the information on ultrafine dust (PM2.5) measured by the target appliance. |
| [`GetUltraFineDustResponse`](#GetUltraFineDustResponse)                       | Response |  Sends the information on ultrafine dust (PM2.5) measured by the target appliance to CEK as a response to the [`GetUltraFineDustRequest`](#GetUltraFineDustRequest) message. |
| [`GetUsageTimeRequest`](#GetUsageTimeRequest)                                 | Request | Used to check the usage time of the target appliance by user. Requests the Clova Home extension for the usage time within a specific period or the total usage time of the target appliance.  |
| [`GetUsageTimeResponse`](#GetUsageTimeResponse)                               | Response |  Sends the information on the cumulative usage time of the target appliance to CEK as a response to the [`GetUsageTimeRequest`](#GetUsageTimeRequest) message.  |
| [`HealthCheckRequest`](#HealthCheckRequest)                                   | Request  | Used to check the state of a target appliance. Requests the Clova Home extension for the state of the target appliance. |
| [`HealthCheckResponse`](#HealthCheckResponse)                                 | Response |  Sends the state information of the target appliance to CEK as a response to the [`HealthCheckRequest`](#HealthCheckRequest) message. |
| [`IncrementBrightnessConfirmation`](#IncrementBrightnessConfirmation)         | Response |  Sends the result of requesting the target appliance to increase brightness of lights to CEK as a response to the [`IncrementBrightnessRequest`](#IncrementBrightnessRequest) message. |
| [`IncrementBrightnessRequest`](#IncrementBrightnessRequest)                   | Request  | Requests the Clova Home extension to set the target appliance to increase the brightness of lights by the designated amount. |
| [`IncrementChannelConfirmation`](#IncrementChannelConfirmation)               | Response |  Sends the result of requesting the target appliance to channel up the TV to CEK as a response to the [`IncrementChannelRequest`](#IncrementChannelRequest) message. |
| [`IncrementChannelRequest`](#IncrementChannelRequest)                         | Request  | Requests the Clova Home extension to set the target appliance to channel up the TV by the designated amount. |
| [`IncrementFanSpeedConfirmation`](#IncrementFanSpeedConfirmation)             | Response |  Sends the result of requesting the target appliance to increase the fan speed to CEK as a response to the [`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest) message. |
| [`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest)                       | Request | Requests the Clova Home extension to set the target appliance to increase the fan speed by the designated amount. |
| [`IncrementIntensityLevelConfirmation`](#IncrementIntensityLevelConfirmation) | Response |  Sends the result of requesting the target appliance to increase the pressure level, such as air or water pressure, to CEK as a response to the [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest) message.  |
| [`IncrementIntensityLevelRequest`](#IncrementIntensityLevelRequest)           | Request  | Requests the Clova Home extension to set the target appliance to increase the pressure level, such as air or water pressure, by the designated amount. |
| [`IncrementTargetTemperatureConfirmation`](#IncrementTargetTemperatureConfirmation) | Response |  Sends the result of requesting the target appliance to increase the temperature to CEK as a response to the [`IncrementTargetTemperatureRequest`](#IncrementTargetTemperatureRequest) message. |
| [`IncrementTargetTemperatureRequest`](#IncrementTargetTemperatureRequest)     | Request  | Requests the Clova Home extension to set the target appliance to increase the temperature by the designated amount.     |
| [`IncrementVolumeConfirmation`](#IncrementVolumeConfirmation)                 | Response |  Sends the result of requesting the target appliance to increase the speaker volume to CEK as a response to the [`IncrementVolumeRequest`](#IncrementVolumeRequest) message. |
| [`IncrementVolumeRequest`](#IncrementVolumeRequest)                           | Request | Requests the Clova Home extension to set the target appliance to increase the speaker volume by the designated amount. |
| [`LowerConfirmation`](#LowerConfirmation)                                     | Response |  Sends the result of requesting the target appliance to lower the height to CEK as a response to the [`LowerRequest`](#LowerRequest) message.  |
| [`LowerRequest`](#LowerRequest)                                               | Request  | Mainly used to control appliances such as curtains, blinds, or beds. Requests the Clova Home extension to lower the height of the target appliance.  |
| [`MuteConfirmation`](#MuteConfirmation)                                       | Response |  Sends the result of muting the target appliance to CEK as a response to the [`MuteRequest`](#MuteRequest) message. |
| [`MuteRequest`](#MuteRequest)                                                 | Request  | Requests the Clova Home extension to mute the target appliance. |
| [`OpenConfirmation`](#OpenConfirmation)                                       | Response |  Sends the result of opening the smart curtain or the bidet lid to CEK as a response to the [`OpenRequest`](#OpenRequest) message. |
| [`OpenRequest`](#OpenRequest)                                                 | Request  | Used to control appliances such as smart curtains or bidets. Requests the Clova Home extension to open the smart curtain or the bidet lid.  |
| [`RaiseConfirmation`](#RaiseConfirmation)                                     | Response |  Sends the result of requesting the target appliance to raise the height to CEK as a response to the [`RaiseRequest`](#RaiseRequest) message.  |
| [`RaiseRequest`](#RaiseRequest)                                               | Request  | Mainly used to control appliances such as curtains, blinds, or beds. Requests the Clova Home extension to raise the height of the target appliance.  |
| [`ReleaseModeConfirmation`](#ReleaseModeConfirmation)                         | Response |  Sends the result of requesting to disable the operation mode of the current appliance to CEK as a response to the [`ReleaseModeRequest`](#ReleaseModeRequest) message.  |
| [`ReleaseModeRequest`](#ReleaseModeRequest)                                   | Request  | Used to disable the operation mode set on the current appliance. Requests the Clova Home extension to return to the previous operation mode or the default operation mode by disabling the operation mode of the appliance.  |
| [`SetBrightnessConfirmation`](#SetBrightnessConfirmation)                     | Response |  Sends the result of requesting the target appliance to change brightness of lights to CEK as a response to the [`SetBrightnessRequest`](#SetBrightnessRequest) message. |
| [`SetBrightnessRequest`](#SetBrightnessRequest)                               | Request  | Requests the Clova Home extension to set the target appliance to change the brightness of lights to the designated value. |
| [`SetChannelByNameConfirmation`](#SetChannelByNameConfirmation)               | Response |  Sends the result of requesting the target appliance to change the TV channel using the name of channel to CEK as a response to the [`SetChannelByNameRequest`](#SetChannelByNameRequest) message. |
| [`SetChannelByNameRequest`](#SetChannelByNameRequest)                         | Request  | Requests the Clova Home extension to set the target appliance to change the TV channel to the designated channel name. |
| [`SetChannelConfirmation`](#SetChannelConfirmation)                           | Response |  Sends the result of requesting the target appliance to change the TV channel using the number of the channel to CEK as a response to the [`SetChannelRequest`](#SetChannelRequest) message. |
| [`SetChannelRequest`](#SetChannelRequest)                                     | Request  | Requests the Clova Home extension to set the target appliance to change the TV channel to the designated channel number. |
| [`SetColorConfirmation`](#SetColorConfirmation)                               | Response |  Sends the result of requesting the target appliance to change the color of lights, screens, or lamps to CEK as a response to the [`SetColorRequest`](#SetColorRequest) message. |
| [`SetColorRequest`](#SetColorRequest)                                         | Request  | Mainly used to control appliances such as smart lamps. Requests the Clova Home extension to change the color of lights, screens, or lamps of the target appliance.  |
| [`SetColorTemperatureConfirmation`](#SetColorTemperatureConfirmation)         | Response |  Sends the result of requesting the target appliance to change the color temperature of lights, screens, or lamps to CEK as a response to the [`SetColorTemperatureRequest`](#SetColorTemperatureRequest) message.  |
| [`SetColorTemperatureRequest`](#SetColorTemperatureRequest)                   | Request  | Mainly used to control appliances such as smart lamps. Requests the Clova Home extension to change the color temperature of lights, screens, or lamps of the target appliance.  |
| [`SetFanSpeedConfirmation`](#SetFanSpeedConfirmation)                         | Response |  Sends the result of requesting the target appliance to change the fan speed to CEK as a response to the [`SetFanSpeedRequest`](#SetFanSpeedRequest) message. |
| [`SetFanSpeedRequest`](#SetFanSpeedRequest)                                   | Request  | Requests the Clova Home extension to change the fan speed of the target appliance to the designated value. |
| [`SetFreezerTargetTemperatureConfirmation`](#SetFreezerTargetTemperatureConfirmation)  | Response  |   Sends the result of requesting the freezer to change the desired temperature to CEK as a response to the [`SetFreezerTargetTemperatureRequest`](#SetFreezerTargetTemperatureRequest) message. |
| [`SetFreezerTargetTemperatureRequest`](#SetFreezerTargetTemperatureRequest)   | Request  | Used to control appliances such as refrigerators. Requests the Clova Home extension to change the desired temperature of the freezer compartment to the designated value.  |
| [`SetFridgeTargetTemperatureConfirmation`](#SetFridgeTargetTemperatureConfirmation) | Response |  Sends the result of requesting the fridge to change the desired temperature to CEK as a response to the [`SetFridgeTargetTemperatureRequest`](#SetFridgeTargetTemperatureRequest) message.  |
| [`SetFridgeTargetTemperatureRequest`](#SetFridgeTargetTemperatureRequest)     | Request  | Used to control appliances such as refrigerators. Requests the Clova Home extension to change the desired temperature of the fridge compartment to the designated value.  |
| [`SetInputSourceByNameConfirmation`](#SetInputSourceByNameConfirmation)       | Response |  Sends the result of requesting the target appliance to change to a specified TV input source to CEK as a response to the [`SetInputSourceByNameRequest`](#SetInputSourceByNameRequest) message.  |
| [`SetInputSourceByNameRequest`](#SetInputSourceByNameRequest)                 | Request  | Requests the Clova Home extension to change to a specified TV input source.  |
| [`SetLockStateConfirmation`](#SetLockStateConfirmation)                       | Response |  Sends the result of requesting the target appliance to lock or unlock to CEK as a response to the [`SetLockStateRequest`](#SetLockStateRequest) message. |
| [`SetLockStateRequest`](#SetLockStateRequest)                                 | Request  | Requests the Clova Home extension to lock or unlock the target appliance.  |
| [`SetModeConfirmation`](#SetModeConfirmation)                                 | Response |  Sends the result of requesting the target appliance to change the operation mode to CEK as a response to the [`SetModeRequest`](#SetModeRequest) message. |
| [`SetModeRequest`](#SetModeRequest)                                           | Request  | Requests the Clova Home extension to change the operation mode of the target appliance to the designated mode. |
| [`SetTargetTemperatureConfirmation`](#SetTargetTemperatureConfirmation)       | Response |  Sends the result of requesting the target appliance to change the set temperature to CEK as a response to the [`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest) message. |
| [`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest)                 | Request  | Requests the Clova Home extension to set the target appliance to change the desired temperature to the designated value. |
| [`StartRecordingConfirmation`](#StartRecordingConfirmation)                   | Response |  Sends the result of requesting the target appliance to start recording on the current channel to CEK as a response to the [`StartRecordingRequest`](#StartRecordingRequest) message.  |
| [`StartRecordingRequest`](#StartRecordingRequest)                             | Request  | Requests the Clova Home extension to start recording the program on the current channel.  |
| [`StopConfirmation`](#StopConfirmation)                                       | Response |  Sends the result of stopping the current action of the target appliance to CEK as a response to the [`StopRequest`](#StopRequest) message.  |
| [`StopRequest`](#StopRequest)                                                 | Request  | Requests the Clova Home extension to stop the current action of the appliance.  |
| [`StopRecordingConfirmation`](#StopRecordingConfirmation)                     | Response |  Sends the result of requesting the target appliance to stop recording on the current channel to CEK as a response to the [`StopRequest`](#StopRequest) message.  |
| [`StopRecordingRequest`](#StopRecordingRequest)                               | Request  | Requests the Clova Home extension to stop recording the program on the current channel.  |
| [`TurnOffConfirmation`](#TurnOffConfirmation)                                 | Response |  Sends the result of requesting the target appliance to turn off to CEK as a response to the [`TurnOffRequest`](#TurnOffRequest) message.|
| [`TurnOffRequest`](#TurnOffRequest)                                           | Request  | Requests the Clova Home extension to turn off the target appliance.                        |
| [`TurnOnConfirmation`](#TurnOnConfirmation)                                   | Response |  Sends the result of requesting the target appliance to turn on to CEK as a response to the [`TurnOnRequest`](#TurnOnRequest) message. |
| [`TurnOnRequest`](#TurnOnRequest)                                             | Request  | Requests the Clova Home extension to turn on the target appliance.                        |
| [`UnmuteConfirmation`](#UnmuteConfirmation)                                   | Response |  Sends the result of turning on (unmuting) the sound of the target appliance to CEK as a response to the [`UnmuteRequest`](#UnmuteRequest) message. |
| [`UnmuteRequest`](#UnmuteRequest)                                             | Request  | Requests the Clova Home extension to turn on (unmute) the sound of the target appliance. |

## ChangeInputSourceConfirmation {#ChangeInputSourceConfirmation}
Sends the result of requesting the target appliance to start charging the appliance to CEK as a response to the [`ChangeInputSourceRequest`](#ChangeInputSourceRequest) message.

### Payload fields

None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "ChangeInputSourceConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

{% endraw %}

### See also
* [`ChangeInputSourceRequest`](#ChangeInputSourceRequest)

## ChangeInputSourceRequest {#ChangeInputSourceRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to change the input source (e.g. HDMI1, HDMI2). The extension must use the [`ChangeInputSourceConfirmation`](#ChargeConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     |  Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string| Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `count`        | [CountInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#CountInfoObject)  | Object containing the count information based on the user utterance such as the number of times the user changes the command. This is mainly used for IR operations. | Optional    |


### Message example

{% raw %}

```json
// Example of user "changing the input of television 3 times"
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "ChangeInputSourceRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-009"
    },
    "count": {
      "value": "3"
    }
  }
}
```

{% endraw %}

### See also
* [`ChangeInputSourceConfirmation`](#ChangeInputSourceConfirmation)

## ChargeConfirmation {#ChargeConfirmation}
Sends the result of requesting the target appliance to start charging the appliance to CEK as a response to the [`ChangeInputSourceRequest`](#ChangeInputSourceRequest) message.

### Payload fields

None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "ChargeConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

{% endraw %}

### See also
* [`ChargeRequest`](#ChargeRequest)

## ChargeRequest {#ChargeRequest}
Mainly used to control robot vacuums. Requests the Clova Home extension to set the target appliance to self-charge. The extension must use the [`ChargeConfirmation`](#ChargeConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     |  Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "ChargeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-009"
    }
  }
}
```

{% endraw %}

### See also
* [`ChargeConfirmation`](#ChargeConfirmation)

## CloseConfirmation {#CloseConfirmation}
Sends the result of closing the smart curtain or bidet lid to CEK as a response to the [`CloseRequest`](#CloseRequest) message.

### Payload fields

None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "a4349fd5-7c1c-4fae-9bbd-291749bdd63a",
    "name": "CloseConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

{% endraw %}

### See also
* [`CloseRequest`](#CloseRequest)

## CloseRequest {#CloseRequest}
Used to control appliances such as smart curtains or bidets. Requests the Clova Home extension to close the smart curtain or the bidet lid. The extension must use the [`CloseConfirmation`](#CloseConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "8030275d-0e71-463d-b1d8-3e761e5389ad",
    "name": "CloseRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-012"
    }
  }
}
```

{% endraw %}

### See also
* [`CloseConfirmation`](#CloseConfirmation)

## DecrementBrightnessConfirmation {#DecrementBrightnessConfirmation}
Sends the result of requesting the target appliance to dim the lights to CEK as a response to the [`DecrementBrightnessRequest`](#DecrementBrightnessRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `brightness`               | [BrightnessInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BrightnessInfoObject) | Object containing information on current brightness.                               | Optional    |
| `previousState`            | object | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.brightness` | [BrightnessInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BrightnessInfoObject) | Object containing information on previous brightness.                                | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "DecrementBrightnessConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "brightness": {
      "value": 20
    },
    "previousState": {
      "brightness": {
        "value": 40
      }
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementBrightnessRequest`](#DecrementBrightnessRequest)

## DecrementBrightnessRequest {#DecrementBrightnessRequest}
Mainly used to control the brightness on appliances such as lights. Requests the Clova Home extension to set the target appliance to dim the lights by the designated amount. The extension must use the [`DecrementBrightnessConfirmation`](#DecrementBrightnessConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `deltaBrightness`       | [BrightnessInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BrightnessInfoObject)             | Object containing information on the amount of change in brightness.                              |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "DecrementBrightnessRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-010"
    },
    "deltaBrightness": {
      "value": 20
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementBrightnessConfirmation`](#DecrementBrightnessConfirmation)

## DecrementChannelConfirmation {#DecrementChannelConfirmation}
Sends the result of requesting the target appliance to channel down the TV to CEK as a response to the [`DecrementChannelRequest`](#DecrementChannelRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `channel`               | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing information on the current TV channel.                                | Optional    |
| `subChannel`            | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing the subchannel information on the current TV channel.                         | Optional    |
| `previousState`            | object | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.channel`    | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing information on the previous TV channel.                                | Optional    |
| `previousState.subChannel` | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing the subchannel information on the previous TV channel.                         | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "DecrementChannelConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "channel": {
      "value": 12
    },
    "subChannel": {
      "value": 1
    },
    "previousState": {
      "channel": {
        "value": 13
      },
      "subChannel": {
        "value": 1
      }
    }
  }
}
```
{% endraw %}

### See also
* [`DecrementChannelRequest`](#DecrementChannelRequest)

## DecrementChannelRequest {#DecrementChannelRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to set the target appliance to channel down the TV by the designated amount. The extension must use the [`DecrementChannelConfirmation`](#DecrementChannelConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `deltaChannel`       | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject)             | Object containing information on the amount of TV channels to change.                              |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "DecrementChannelRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-011"
    },
    "deltaChannel": {
      "value": 1
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementChannelConfirmation`](#DecrementChannelConfirmation)

## DecrementFanSpeedConfirmation {#DecrementFanSpeedConfirmation}
Sends the result of requesting the target appliance to lower the fan speed to CEK as a response to the [`DecrementFanSpeedRequest`](#DecrementFanSpeedRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `fanSpeed`       | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject)             | Object containing information on the current fan speed. The fan speed represents wind speed and is limited to the following values.<ul><li><code>1</code> : Low wind (phase 1)</li><li><code>2</code>: Medium wind (phase 2)</li><li><code>3</code>: High wind (phase 3)</li></ul> | Optional    |
| `previousState`     | object                                  | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.fanSpeed` | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject)     | Object containing information on the previous fan speed. The fan speed represents wind speed and is limited to the following values.<ul><li><code>1</code> : Low wind (phase 1)</li><li><code>2</code>: Medium wind (phase 2)</li><li><code>3</code>: High wind (phase 3)</li></ul> | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "DecrementFanSpeedConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "fanSpeed": {
      "value": 2
    },
    "previousState": {
      "fanSpeed": {
        "value": 3
      }
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementFanSpeedRequest`](#DecrementFanSpeedRequest)

## DecrementFanSpeedRequest {#DecrementFanSpeedRequest}
Mainly used to control appliances such as air purifiers. Requests the Clova Home extension to set the target appliance to lower the fan speed by the designated amount. The extension must use the [`DecrementFanSpeedConfirmation`](#DecrementFanSpeedConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `deltaFanSpeed`       | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject)             | Object containing information on the amount of fan speed to change. The fan speed represents wind speed and is limited to the following values.<ul><li><code>1</code> : Low wind (phase 1)</li><li><code>2</code>: Medium wind (phase 2)</li><li><code>3</code>: High wind (phase 3)</li></ul> |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "DecrementFanSpeedRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-004"
    },
    "deltaFanSpeed": {
      "value": 2
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementFanSpeedConfirmation`](#DecrementFanSpeedConfirmation)

## DecrementIntensityLevelConfirmation {#DecrementIntensityLevelConfirmation}
Sends the result of requesting the target appliance to lower the pressure level, such as air or water pressure, to CEK as a response to the [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `intensityLevel` | [IntensityLevelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#IntensityLevelInfoObject) | Object containing current information on pressure or water pressure intensity.                  | Optional    |
| `previousState`  | object                                  | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.intensityLevel` | [IntensityLevelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#IntensityLevelInfoObject) | Object containing previous information on pressure or water pressure intensity.    | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest)

## DecrementIntensityLevelRequest {#DecrementIntensityLevelRequest}
Mainly used to control appliances such as air conditioners and thermostats. Requests the Clova Home extension set the target appliance to decrease the pressure level, such as air or water pressure, by the designated amount. The extension must use the [`DecrementIntensityLevelConfirmation`](#DecrementIntensityLevelConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `deltaIntensity`   | [IntensityLevelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing information on the amount of intensity to change.                            |<!-- -->|

### Message example

{% raw %}

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
    "deltaTemperature": {
      "value": 1
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementIntensityLevelConfirmation`](#DecrementIntensityLevelConfirmation)

## DecrementTargetTemperatureConfirmation {#DecrementTargetTemperatureConfirmation}
Sends the result of requesting the target appliance to reduce the temperature to CEK as a response to the [`DecrementTargetTemperatureRequest`](#DecrementTargetTemperatureRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `previousState`     | object                                  | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.targetTemperature` | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing previous information on the desired temperature.             | Optional    |
| `targetTemperature` | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing the desired temperature information to set on the target appliance or that the extension has requested to be set on the target appliance.                            | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "DecrementTargetTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": 23
    },
    "previousState": {
      "targetTemperature": {
        "value": 25
      }
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementTargetTemperatureRequest`](#DecrementTargetTemperatureRequest)

## DecrementTargetTemperatureRequest {#DecrementTargetTemperatureRequest}
Mainly used to control appliances such as air conditioners and thermostats. Requests the Clova Home extension to set the target appliance to lower the temperature by the designated amount. The extension must use the [`DecrementTargetTemperatureConfirmation`](#DecrementTargetTemperatureConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `deltaTemperature` | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing information on the amount of temperature to change.                              |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "DecrementTargetTemperatureRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-001"
    },
    "deltaTemperature": {
      "value": 2
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementTargetTemperatureConfirmation`](#DecrementTargetTemperatureConfirmation)

## DecrementVolumeConfirmation {#DecrementVolumeConfirmation}
Sends the result of requesting the target appliance to lower the speaker volume to CEK as a response to the [`DecrementVolumeRequest`](#DecrementVolumeRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `previousState`     | object                                  | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.targetVolume` | [VolumeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject)    | Object containing information on the previous volume.                             | Optional    |
| `targetVolume`      | [VolumeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject)            | Object containing information on the volume set on the target appliance or that the extension has requested to be set on the target appliance.                             | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "DecrementVolumeConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetVolume": {
      "value": 10
    },
    "previousState": {
      "targetVolume": {
        "value": 20
      }
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementVolumeRequest`](#DecrementVolumeRequest)

## DecrementVolumeRequest {#DecrementVolumeRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to set the target appliance to lower the speaker volume by the designated amount. The extension must use the [`DecrementVolumeConfirmation`](#DecrementVolumeConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `deltaVolume`       | [VolumeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#VolumeInfoObject)             | Object containing information on the amount of volume to change.                           |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "DecrementVolumeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-005"
    },
    "deltaVolume": {
      "value": 10
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementVolumeConfirmation`](#DecrementVolumeConfirmation)

## GetAirQualityRequest {#GetAirQualityRequest}
Mainly used to check air quality measured by an appliance such as an air purifier. Requests the Clova Home extension for the air quality information. The extension must use the [`GetAirQualityResponse`](#GetAirQualityResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetAirQualityRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-011"
    }
  }
}
```

{% endraw %}

### See also
* [`GetAirQualityResponse`](#GetAirQualityResponse)

## GetAirQualityResponse {#GetAirQualityResponse}
Sends the air quality information measured by the target appliance to CEK as a response to the [`GetAirQualityRequest`](#GetAirQualityRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `airQuality`                 | [AirQualityInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#AirQualityInfoObject) | Object containing information on the air quality measured by the current appliance.   |<!-- -->|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetAirQualityResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "airQuality": {
        "index": "good"
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:04+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetAirQualityRequest`](#GetAirQualityRequest)

## GetAsleepDurationRequest {#GetAsleepDurationRequest}
Mainly used o check information measured from a sleep sensor. Requests the Clova Home extension for the sleep time of the user measured by the target appliance. The extension must use the [`GetAsleepDurationResponse`](#GetAsleepDurationResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | Object containing information on the period of time.                                      | Optional  |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetAsleepDurationRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-032"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

{% endraw %}

### See also
* [`GetAsleepDurationResponse`](#GetAsleepDurationResponse)

## GetAsleepDurationResponse {#GetAsleepDurationResponse}
Sends the duration of the user sleep time measured by the target appliance to CEK as a response to the [`GetAsleepDurationRequest`](#GetAsleepDurationRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp`  | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `asleepDuration`                    | string | The average sleep time. (Duration, <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601</a>)   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetAsleepDurationResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "asleepDuration": "PT8H40M",
    "applianceResponseTimestamp": "2018-03-29T16:22:22+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetAsleepDurationRequest`](#GetAsleepDurationRequest)

## GetAwakeDurationRequest {#GetAwakeDurationRequest}
Mainly used o check information measured from a sleep sensor. Requests the Clova Home extension for the sleep onset latency measured by the target appliance–in other words, the amount of time from going to bed until falling asleep. The extension must use the [`GetAwakeDurationResponse`](#GetAwakeDurationResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | Object containing information on the period of time.                                      | Optional  |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetAwakeDurationRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-032"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

{% endraw %}

### See also
* [`GetAwakeDurationResponse`](#GetAwakeDurationResponse)

## GetAwakeDurationResponse {#GetAwakeDurationResponse}
Sends the amount of time the measured by the target appliance of the user going to bed until falling asleep to CEK as a response to the [`GetAwakeDurationRequest`](#GetAwakeDurationRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp`  | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `awakeDuration`                    | string | The average awake time after going to bed. (Duration, <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601</a>)   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetAwakeDurationResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "awakeDuration": "PT0H20M",
    "applianceResponseTimestamp": "2018-03-29T16:22:22+00:00"
  }
}
```

{% endraw %}

### See also
* [`GetAwakeDurationRequest`](#GetAwakeDurationRequest)

## GetBatteryInfoRequest {#GetBatteryInfoRequest}
Mainly used to check built-in battery information of a wireless appliance such as a robot vacuum. Requests the Clova Home extension for the current battery information. The extension must use the [`GetBatteryInfoResponse`](#GetBatteryInfoResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetBatteryInfoRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-011"
    }
  }
}
```

{% endraw %}

### See also
* [`GetBatteryInfoResponse`](#GetBatteryInfoResponse)

## GetBatteryInfoResponse {#GetBatteryInfoResponse}
Sends the battery information of the target appliance to CEK as a response to the [`GetBatteryInfoRequest`](#GetBatteryInfoRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `batteryInfo`                 | [BatteryInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BatteryInfoObject) | Object containing battery information of the current appliance.   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetBatteryInfoResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "batteryInfo": {
        "value": 50
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetBatteryInfoRequest`](#GetBatteryInfoRequest)

## GetCleaningCycleRequest {#GetCleaningCycleRequest}
Mainly used to check the cleaning cycle of an appliance. Requests the Clova Home extension for the information on the remaining time until the next cleaning cycle of the target appliance. The extension must use the [`GetCleaningCycleResponse`](#GetCleaningCycleResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "9a1a7237-f1c0-44f8-b4db-2a2abb1f0e1c",
    "name": "GetCleaningCycleRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-045"
    }
  }
}
```

{% endraw %}

### See also
* [`GetCleaningCycleResponse`](#GetCleaningCycleResponse)

## GetCleaningCycleResponse {#GetCleaningCycleResponse}

Sends the information on the remaining time until the next cleaning cycle of the target appliance to CEK as a response to the [`GetCleaningCycleRequest`](#GetCleaningCycleRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `remainingTime`              | string | The time remaining until cleaning is required. (Duration, <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601</a>    |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetCleaningCycleResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "remainingTime": "PT8H40M",
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetCleaningCycleRequest`](#GetGetCleaningCycleRequest)

## GetCloseTimeRequest {#GetCloseTimeRequest}
Requests the Clova Home extension for the recent close time of the target, mainly from the detection details of the open-close sensor. The extension must use the [`GetCloseTimeResponse`](#GetCloseTimeResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetCloseTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-025"
    }
  }
}
```

{% endraw %}

### See also
* [`GetCloseTimeResponse`](#GetCloseTimeResponse)

## GetCloseTimeResponse {#GetCloseTimeResponse}

Sends the recent close time of the target from the detection details of the open-close sensor to CEK response to the [`GetCloseTimeRequest`](#GetCloseTimeRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `closeTimestamp`             | string | The recent close time of the detection target. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetCloseTimeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "closeTimestamp": "2018-03-13T23:17:50+09:00",
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetCloseTimeRequest`](#GetCloseTimeRequest)

## GetConsumptionRequest {#GetConsumptionRequest}
Mainly used to check for energy consumption or resource information to date measured from appliances such as smart plugs or smart power strips. Requests the Clova Home extension for the energy consumption or resource information measured from an appliance. The extension must use the [`GetConsumptionResponse`](#GetConsumptionResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "2d8b8c3b-5905-4355-b4bb-fa359c46c308",
    "name": "GetConsumptionRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-019"
    }
  }
}
```

{% endraw %}

### See also
* [`GetConsumptionResponse`](#GetConsumptionResponse)

## GetConsumptionResponse {#GetConsumptionResponse}
Sends the information on energy consumption or resource information measured by the target appliance to date to CEK as a response to the [`GetConsumptionRequest`](#GetConsumptionRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `consumption[]`              | [ConsumptionInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ConsumptionInfoObject) array | Object containing information on energy consumption or resource information to date measured by the appliance.   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetConsumptionResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "consumption": [
      {
        "name": "energy usage",
        "value": 79.7,
        "unit": "kW"
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}
```

{% endraw %}

### See also
* [GetConsumptionRequest](#GetConsumptionRequest)

## GetCurrentBillRequest {#GetCurrentBillRequest}
Mainly used to check billing information based on energy consumption to date measured from appliances such as smart plugs or smart power strips. Requests the Clova Home extension for the billing information measured by the target appliance. The extension must use the [`GetCurrentBillResponse`](#GetCurrentBillResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "2d8b8c3b-5905-4355-b4bb-fa359c46c308",
    "name": "GetCurrentBillRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-019"
    }
  }
}
```

{% endraw %}

### See also
* [`GetCurrentBillResponse`](#GetCurrentBillResponse)

## GetCurrentBillResponse {#GetCurrentBillResponse}
Sends the information on billing measured by the target appliance to date to CEK as a response to the [`GetCurrentBillRequest`](#GetCurrentBillRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `currentBill`                 | [BillInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BillInfoObject) | Object containing the billing information measured by the appliance to date.   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetCurrentBillResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "currentBill": {
        "value": 2990,
        "currency": "JPY"
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}
```

{% endraw %}

### See also
* [GetCurrentBillRequest](#GetCurrentBillRequest)

## GetCurrentTemperatureRequest {#GetCurrentTemperatureRequest}
Mainly used to check for the current temperature measured from appliances such as air conditioners or thermostats. Requests the Clova Home extension for the current temperature measured by the target appliance. The extension must use the [`GetCurrentTemperatureResponse`](#GetCurrentTemperatureResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "3085a017-919f-4708-8748-fb68af10faba",
    "name": "GetCurrentTemperatureRequest",
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

{% endraw %}

### See also
* [`GetCurrentTemperatureResponse`](#GetCurrentTemperatureResponse)
* [`GetTargetTemperatureRequest`](#GetTargetTemperatureRequest)

## GetCurrentTemperatureResponse {#GetCurrentTemperatureResponse}
Sends the information on current temperature measured by the target appliance to CEK as a response to the [`GetCurrentTemperatureRequest`](#GetCurrentTemperatureRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `currentTemperature`          | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing information on the current temperature measured by the target appliance.  |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "7eef3a17-675d-4bbd-bd8a-f379855d05ca",
    "name": "GetCurrentTemperatureResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "currentTemperature": {
        "value": 22
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:32+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetCurrentTemperatureRequest`](#GetCurrentTemperatureRequest)
* [`GetTargetTemperatureResponse`](#GetTargetTemperatureResponse)

## GetDeviceStateRequest {#GetDeviceStateRequest}

Requests to all state and measurement information provided by the target appliance. Information on air quality, fine dust (PM10), and ultrafine dust (PM2.5) measured from an air purifier can be obtained from the [`GetAirQualityRequest`](#GetAirQualityRequest), [`GetHumidityRequest`](#GetHumidityRequest), [`GetFineDustRequest`](#GetFineDustRequest), and [`GetUltraFineDustRequest`](#GetUltraFineDustRequest) messages respectively. Or, all the information can be obtained at once using the `GetDeviceStateRequest` message. Some measurements require information on a specific period which is delivered via the `period` field. The extension must use the [`GetDeviceStateResponse`](#GetDeviceStateResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | Object containing information on the period of time.                                         | Optional   |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetDeviceStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-012"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

{% endraw %}

### See also
* [`GetDeviceStateResponse`](#GetDeviceStateResponse)

## GetDeviceStateResponse {#GetDeviceStateResponse}
Sends all state information provided by the target appliance to CEK as a response to the [`GetDeviceStateRequest`](#GetDeviceStateRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `states[]`                   | [CustomInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#CustomInfoObject) array  | Object containing information on all states provided by the appliance.                    |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetDeviceStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "states" : [
      {
        "name": "Temperature of the freezer",
        "value" : -11,
        "unit" : "celsius"
      },
      {
        "name": "Temperature of the fridge",
        "value" : 2,
        "unit" : "celsius"
      },
      {
        "name": "Humidity of fridge",
        "value" : 10,
        "unit" : "percentage"
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:31:18+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetDeviceStateRequest`](#GetDeviceStateRequest)

## GetEstimateBillRequest {#GetEstimateBillRequest}
Mainly used to check the estimated billing based on energy usage measured from appliances such as smart plugs or smart power strips. Requests the Clova Home Extension for the estimated billing information. The extension must use the [`GetEstimateBillResponse`](#GetEstimateBillResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

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
    }
  }
}
```

{% endraw %}

### See also
* [`GetEstimateBillResponse`](#GetEstimateBillResponse)

## GetEstimateBillResponse {#GetEstimateBillResponse}
Sends the estimated billing information measure by the target appliance to CEK as a response to the [`GetEstimateBillRequest`](#GetEstimateBillRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `estimateBill`                 | [BillInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BillInfoObject) | Object containing billing information estimated by the appliance.   |<!-- -->|

### Message example

{% raw %}

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
        "value": 6000,
        "currency": "JPY"
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}
```

{% endraw %}

### See also
* [GetEstimateBillRequest](#GetEstimateBillRequest)

## GetExpendableStateRequest {#GetExpendableStateRequest}

Used to check the amount of usage or remaining lifespan on appliances such as filters or parts. Requests the Clova Home extension for information on usage and remaining lifespan on parts of the target appliance. The extension must use the [`GetExpendableStateResponse`](#GetExpendableStateResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetExpendableStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-030"
    }
  }
}
```

{% endraw %}

### See also
* [`GetExpendableStateResponse`](#GetExpendableStateResponse)

## GetExpendableStateResponse {#GetExpendableStateResponse}
Sends the information on usage or remaining lifespan of all parts of the target appliance to CEK as a response to the [`GetExpendableStateRequest`](#GetExpendableStateRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `expendableInfo[]`           | [ExpendableInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ExpendableInfoObject) array  | Object containing information on usage or remaining lifespan of appliance parts.                    |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetExpendableStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "expendableInfo" : [
      {
        "name": "Packing",
        "remainingTime": "P0001-04-10"
      },
      {
        "name": "Filter 1",
        "usage": {
          "value" : 80,
          "unit" : "percentage"
        }
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:31:18+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetExpendableStateRequest`](#GetExpendableStateRequest)

## GetFineDustRequest {#GetFineDustRequest}
Mainly used to check information on fine dust (PM10) measured from an appliance such as an air purifier. Requests the Clova Home extension for the fine dust information measured by the target appliance. The extension must use the [`GetFineDustResponse`](#GetFineDustResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetFineDustRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-011"
    }
  }
}
```

{% endraw %}

### See also
* [`GetFineDustResponse`](#GetFineDustResponse)

## GetFineDustResponse {#GetFineDustResponse}
Sends the information on fine dust (PM10) measured by the target appliance to CEK as a response to the [`GetFineDustRequest`](#GetFineDustRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `fineDust`                 | [FineDustInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#FineDustInfoObject) | Object containing information on fine dust measured by the current appliance.   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetFineDustResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "fineDust": {
      "value": 77,
      "index": "normal"
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:44+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetFineDustRequest`](#GetFineDustRequest)

## GetHumidityRequest {#GetHumidityRequest}
Mainly used to check information on humidity measured from an appliance such as a humidifier. Requests the Clova Home extension for the humidity measured by the target appliance. The extension must use the [`GetHumidityResponse`](#GetHumidityResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetHumidityRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-012"
    }
  }
}
```

{% endraw %}

### See also
* [`GetHumidityResponse`](#GetHumidityResponse)

## GetHumidityResponse {#GetHumidityResponse}
Sends the information on humidity measured by the target appliance to CEK as a response to the [`GetHumidityRequest`](#GetHumidityRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `humidity`                 | [HumidityInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#HumidityInfoObject) | Object containing information on humidity measured by the current appliance.   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetHumidityResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "humidity": {
        "value": 40
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}
```

{% endraw %}

### See also
* [GetHumidityRequest](#GetHumidityRequest)

## GetKeepWarmTimeRequest {#GetKeepWarmTimeRequest}
Mainly used to check the time spent on the food warming mode of appliances such as rice cookers. Requests the Clova Home extension for the time spent on the warming mode on the target appliance. The extension must use the [`GetKeepWarmTimeResponse`](#GetKeepWarmTimeResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetKeepWarmTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-029"
    }
  }
}
```

{% endraw %}

### See also
* [`GetKeepWarmTimeResponse`](#GetKeepWarmTimeResponse)

## GetKeepWarmTimeResponse {#GetKeepWarmTimeResponse}

Sends the information on the time spent on the warming mode of the target appliance to CEK as a response to the [`GetKeepWarmTimeRequest`](#GetKeepWarmTimeRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)        | Optional    |
| `keepWarmTime`               | string | The time spent on the warming mode. (Duration, <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601</a>)       |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetKeepWarmTimeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "keepWarmTime": "PT5H00M",
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetKeepWarmTimeRequest`](#GetKeepWarmTimeRequest)

## GetLockStateRequest {#GetLockStateRequest}
Mainly used to check the appliance state such as a smart valve. Requests the Clova Home extension for the current lock state of the lock device on the target appliance. The extension must use the [`GetLockStateResponse`](#GetLockStateResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetLockStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-012"
    }
  }
}
```

{% endraw %}

### See also
* [`GetLockStateResponse`](#GetLockStateResponse)

## GetLockStateResponse {#GetLockStateResponse}
Sends the information on the current lock state of the lock device on the target appliance to CEK as a response to the [`GetLockStateRequest`](#GetLockStateRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `lockState`                  | string | The lock state of an appliance lock device. Available values are:<ul><li><code>"LOCKED"</code> : The device is locked</li><li><code>"UNLOCKED"</code>: The device is unlocked</li></ul> |<!-- -->|


### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetLockStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "lockState": "LOCKED",
    "applianceResponseTimestamp": "2017-11-23T20:31:08+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetLockStateRequest`](#GetLockStateRequest)

## GetOpenStateRequest {#GetOpenStateRequest}
Requests the Clova Home extension for the current state information of the detection target (open or close), mainly from the detection details of the open-close sensor. The extension must use the [`GetOpenStateResponse`](#GetOpenStateResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetOpenStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-012"
    }
  }
}
```

{% endraw %}

### See also
* [`GetOpenStateResponse`](#GetOpenStateResponse)

## GetOpenStateResponse {#GetOpenStateResponse}
Sends the current state information (open/close) of the detection target to CEK as a response to the [`GetOpenStateRequest`](#GetOpenStateRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `openState`                  | string | The detected state of a target such as cover, door, or window.<ul><li><code>"CLOSED"</code> : The target is closed</li><li><code>"OPENED"</code>: The target is open</li></ul> |<!-- -->|


### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetOpenStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "OpenState": "CLOSED",
    "applianceResponseTimestamp": "2017-11-23T20:31:08+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetOpenStateRequest`](#GetOpenStateRequest)

## GetOpenTimeRequest {#GetOpenTimeRequest}
Requests the Clova Home extension for the recent open time of the target, mainly from the detection details of the open-close sensor. The extension must use the [`GetOpenTimeResponse`](#GetOpenTimeResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetOpenTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-025"
    }
  }
}
```

{% endraw %}

### See also
* [`GetOpenTimeResponse`](#GetOpenTimeResponse)

## GetOpenTimeResponse {#GetOpenTimeResponse}

Sends the recent open time of the target from the detection details of the open-close sensor to CEK as a response to the [`GetOpenTimeRequest`](#GetOpenTimeRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `openTimestamp`              | string | The recent open time of the detection target. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetOpenTimeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "openTimestamp": "2018-03-13T23:20:15+09:00",
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetOpenTimeRequest`](#GetOpenTimeRequest)

## GetPhaseRequest {#GetPhaseRequest}
Mainly used to check the action phase of appliances that operate in phases such as rice cookers or washers. Requests the Clova Home extension for the current action phase of the target appliance. The extension must use the [`GetPhaseResponse`](#GetPhaseResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "0e25429d-b7c2-4588-aa85-3c46168e8776",
    "name": "GetPhaseRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-017"
    }
  }
}
```

{% endraw %}

### See also
* [`GetPhaseResponse`](#GetPhaseResponse)

## GetPhaseResponse {#GetPhaseResponse}
Sends the current action phase of the target appliance to CEK as a response to the [`GetPhaseRequest`](#GetPhaseRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `phase`                 | [PhaseInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PhaseInfoObject) | Object containing information on the current phase of the appliance.   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetPhaseResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "phase": {
        "value": "wash",
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetPhaseRequest`](#GetPhaseRequest)

## GetProgressiveTaxBracketRequest {#GetProgressiveTaxBracketRequest}
Mainly used to check the progressive tax bracket in appliances such as smart meters or smart plugs. Requests the Clova Home extension for the progressive tax bracket determined by the target appliance. The extension must use the [`GetProgressiveTaxBracketResponse`](#GetProgressiveTaxBracketResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetProgressiveTaxBracketRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-017"
    }
  }
}
```

{% endraw %}

### See also
* [`GetProgressiveTaxBracketResponse`](#GetProgressiveTaxBracketResponse)

## GetProgressiveTaxBracketResponse {#GetProgressiveTaxBracketResponse}

Sends the information on the progressive tax bracket determined by the target appliance to CEK as a response to the [`GetProgressiveTaxBracketRequest`](#GetProgressiveTaxBracketRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `progressiveTaxBracket`      | [ProgressiveTaxBracketInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ProgressiveTaxBracketInfoObject) | Object containing information on progressive tax bracket.  |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetProgressiveTaxBracketResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "progressiveTaxBracket": {
      "value": 1
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetProgressiveTaxBracketRequest`](#GetProgressiveTaxBracketRequest)

## GetRemainingTimeRequest {#GetRemainingTimeRequest}
Mainly used to check the remaining time until the end of an action on appliances such as rice cookers or washers. Requests the Clova Home extension for the remaining time until the end of the action of the target appliance. The extension must use the [`GetRemainingTimeResponse`](#GetRemainingTimeResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetRemainingTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-017"
    }
  }
}
```

{% endraw %}

### See also
* [`GetRemainingTimeResponse`](#GetRemainingTimeResponse)

## GetRemainingTimeResponse {#GetRemainingTimeResponse}

Sends the information on the time remaining until the end of the action of the target appliance to CEK as a response to the [`GetRemainingTimeRequest`](#GetRemainingTimeRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `remainingTime`              | string | The time remaining until the end of action. (Duration, <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601</a>)    |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetRemainingTimeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "remainingTime": "PT8H40M",
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetRemainingTimeRequest`](#GetRemainingTimeRequest)

## GetRightPostureRatioRequest {#GetRightPostureRatioRequest}
Used to check the ratio of a user using the target appliance in good posture. Requests the Clova Home extension for the ratio of the user using the target appliance in good posture during a specific or whole period of use. The extension must use the [`GetRightPostureRatioResponse`](#GetRightPostureRatioResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | Object containing information on the period of time.                                     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetRightPostureRatioRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-028"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

{% endraw %}

### See also
* [`GetRightPostureRatioResponse`](#GetRightPostureRatioResponse)

## GetRightPostureRatioResponse {#GetRightPostureRatioResponse}

Sends the information on the ratio of a user using the target appliance in good posture to CEK as a response to the [`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `rightPostureRatio`          | [RatioInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#RatioInfoObject) | Object containing information on the ratio of the user using the target appliance in good posture.   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetRightPostureRatioResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "rightPostureRatio": {
      "value": 80
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetRightPostureRatioRequest`](#GetRightPostureRatioRequest)

## GetCurrentSittingStateRequest {#GetCurrentSittingStateRequest}
Used to check the use states of the user in appliances such as a smart chair. Requests the Clova Home Extension for the sit-down information of the user detected by the target appliance and the latest time of use. The extension must use the [`GetCurrentSittingStateResponse`](#GetCurrentSittingStateResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetCurrentSittingStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-032"
    }
  }
}
```

{% endraw %}

### See also
* [`GetCurrentSittingStateResponse`](#GetCurrentSittingStateResponse)

## GetCurrentSittingStateResponse {#GetCurrentSittingStateResponse}
Sends the sit-down information of the user detected by the target appliance and the latest time of use to CEK as a response to the [`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string  | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `sittingState`               | [SittingStateInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SittingStateInfoObject) |  Object containing the sit-down information of the user on appliances such as a smart chair.              |<!-- -->|
| `recentlySittingPeriod`      | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject) | Object containing information on the latest time of use.              | Optional    |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetCurrentSittingStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "sittingState": {
      "value": true
    },
    "recentlySittingPeriod": {
      "start": "2018-03-28T00:10:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    },
    "applianceResponseTimestamp": "2018-03-29T14:32:13+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetCurrentSittingStateRequest`](#GetCurrentSittingStateRequest)

## GetSleepScoreRequest {#GetSleepScoreRequest}
Mainly used to check the sleep score of the user in appliances such as a sleep sensor. Requests the Clova Home extension for the sleep time of the user measured by the target appliance. The extension must use the [`GetSleepScoreResponse`](#GetSleepScoreResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | Object containing information on the period of time.                                          | Optional  |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetSleepScoreRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-032"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

{% endraw %}

### See also
* [`GetSleepScoreResponse`](#GetSleepScoreResponse)

## GetSleepScoreResponse {#GetSleepScoreResponse}
Sends the sleep score of the user assessed by the target appliance to CEK as a response to the [`GetSleepScoreRequest`](#GetSleepScoreRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string  | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `sleepScore`                 | [SleepScoreInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SleepScoreInfoObject)  | Object containing information on sleep score.                                                       |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetSleepScoreResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "sleepScore": {
      "value": 80
    },
    "applianceResponseTimestamp": "2018-03-29T14:32:13+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetSleepScoreRequest`](#GetSleepScoreRequest)

## GetSleepStartTimeRequest {#GetSleepStartTimeRequest}
Mainly used to check the sleep score of the user in appliances such as a sleep sensor. Requests the Clova Home extension for the sleep start time of the user measured by the target appliance. The extension must use the [`GetSleepStartTimeResponse`](#GetSleepStartTimeResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | Object containing information on the period of time.                                          | Optional  |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetSleepStartTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-032"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

{% endraw %}

### See also
* [`GetSleepStartTimeResponse`](#GetSleepStartTimeResponse)

## GetSleepStartTimeResponse {#GetSleepStartTimeResponse}
Sends the information on sleep onset time of the user measured by the target appliance to CEK as a response to the [`GetSleepStartTimeRequest`](#GetSleepStartTimeRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string  | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `startTimestampList[]`       | string  | The array of sleep start time in date order.                                      |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetSleepStartTimeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "startTimestampList": [
      "2018-03-22T20:44:43+09:00",
      "2018-03-23T22:12:12+09:00",
      "2018-03-24T21:11:55+09:00"
    ],
    "applianceResponseTimestamp": "2018-03-29T14:32:13+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetSleepStartTimeRequest`](#GetSleepStartTimeRequest)

## GetTargetTemperatureRequest {#GetTargetTemperatureRequest}
Mainly used to check for the desired temperature set in appliances such as air conditioners or thermostats. Requests the Clova Home extension for the desired temperature set by the target appliance. The extension must use the [`GetTargetTemperatureResponse`](#GetTargetTemperatureResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetTargetTemperatureRequest",
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

{% endraw %}

### See also
* [`GetTargetTemperatureResponse`](#GetTargetTemperatureResponse)

## GetTargetTemperatureResponse {#GetTargetTemperatureResponse}
Sends the information on the desired temperature set by the target appliance to CEK as a response to the [`GetTargetTemperatureRequest`](#GetTargetTemperatureRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `targetTemperature`          | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing the desired temperature information to set on the target appliance or that the extension has requested to be set on the target appliance.  |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetTargetTemperatureResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
        "value": 24
    },
    "applianceResponseTimestamp": "2017-11-23T20:31:18+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetTargetTemperatureRequest`](#GetTargetTemperatureRequest)

## GetUltraFineDustRequest {#GetUltraFineDustRequest}
Mainly used to check information on ultrafine dust (PM2.5) measured from an appliance such as an air purifier. Requests the Clova Home extension for the information on ultrafine dust (PM2.5) measured by the target appliance. The extension must use the [`GetUltraFineDustResponse`](#GetUltraFineDustResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetUltraFineDustRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-011"
    }
  }
}
```

{% endraw %}

### See also
* [`GetUltraFineDustResponse`](#GetUltraFineDustResponse)

## GetUltraFineDustResponse {#GetUltraFineDustResponse}
Sends the information on ultrafine dust (PM2.5) measured by the target appliance to CEK as a response to the [`GetUltraFineDustRequest`](#GetUltraFineDustRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `ultraFineDust`                 | [UltraFineDustInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#UltraFineDustInfoObject) | Object containing information on the ultrafine index dust measured by the current appliance.   |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetUltraFineDustResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "ultraFineDust": {
      "value": 44,
      "index": "good"
    },
    "applianceResponseTimestamp": "2017-11-23T20:26:48+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetUltraFineDustRequest`](#GetUltraFineDustRequest)

## GetUsageTimeRequest {#GetUsageTimeRequest}
Used to check the usage time of the target appliance by user. Requests the Clova Home extension for the usage time within a specific period or the total usage time of the target appliance. The extension must use the [`GetUsageTimeResponse`](#GetUsageTimeResponse) message as a response to this request.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `period`           | [PeriodInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | Object containing information on the period of time.                                     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetUsageTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-028"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

{% endraw %}

### See also
* [`GetUsageTimeResponse`](#GetUsageTimeResponse)

## GetUsageTimeResponse {#GetUsageTimeResponse}

Sends the information on the cumulative usage time of the target appliance to CEK as a response to the [`GetUsageTimeRequest`](#GetUsageTimeRequest) message.

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | The time of checking the requested information from the appliance. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)     | Optional    |
| `usageTime`                  | string | The usage time. (Duration, <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601</a>)               |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetUsageTimeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "usageTime": "P12DT8H40M",
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetUsageTimeRequest`](#GetUsageTimeRequest)

## HealthCheckRequest {#HealthCheckRequest}
Used to check the state of a target appliance. Requests the Clova Home extension for the state of the target appliance. The extension must use the [`HealthCheckResponse`](#HealthCheckResponse) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string  | Access token of the Clova Home extension |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`HealthCheckResponse`](#HealthCheckResponse)

## HealthCheckResponse {#HealthCheckResponse}
Sends the state information of the target appliance to CEK as a response to the [`HealthCheckRequest`](#HealthCheckRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `isReachable` | boolean | The value indicating whether it is possible to access the target appliance via the network.<ul><li><code>true</code> : Accessible (online)</li><li><code>false</code>: Inaccessible (offline)</li></ul> |<!-- -->|
| `isTurnOn`    | boolean | The value indicating the operating state of the target appliance.<ul><li><code>true</code> : Working state</li><li><code>false</code>: Idle state</li></ul>                  |<!-- -->|

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`HealthCheckRequest`](#HealthCheckRequest)

## IncrementBrightnessConfirmation {#IncrementBrightnessConfirmation}
Sends the result of requesting the target appliance to increase brightness of lights to CEK as a response to the [`IncrementBrightnessRequest`](#IncrementBrightnessRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `brightness`               | [BrightnessInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BrightnessInfoObject) | Object containing information on current brightness.                               | Optional    |
| `previousState`            | object | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.brightness` | [BrightnessInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BrightnessInfoObject) | Object containing information on previous brightness.                                | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementBrightnessConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "brightness": {
      "value": 40
    },
    "previousState": {
      "brightness": {
        "value": 20
      }
    }
  }
}
```

{% endraw %}

### See also
* [`IncrementBrightnessRequest`](#IncrementBrightnessRequest)

## IncrementBrightnessRequest {#IncrementBrightnessRequest}
Mainly used to control the brightness on appliances such as lights. Requests the Clova Home extension to set the target appliance to increase the brightness of lights by the designated amount. The extension must use the [`IncrementBrightnessConfirmation`](#IncrementBrightnessConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `deltaBrightness`       | [BrightnessInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BrightnessInfoObject)             | Object containing information on the amount of change in brightness.                              |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementBrightnessRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-010"
    },
    "deltaBrightness": {
      "value": 20
    }
  }
}
```

{% endraw %}

### See also
* [`IncrementBrightnessConfirmation`](#IncrementBrightnessConfirmation)

## IncrementChannelConfirmation {#IncrementChannelConfirmation}
Sends the result of requesting the target appliance to channel up the TV to CEK as a response to the [`IncrementChannelRequest`](#IncrementChannelRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `channel`               | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing information on the current TV channel.                                | Optional    |
| `subChannel`            | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing the subchannel information on the current TV channel.                         | Optional    |
| `previousState`            | object | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.channel`    | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing information on the previous TV channel.                                | Optional    |
| `previousState.subChannel` | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing the subchannel information on the previous TV channel.                         | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementChannelConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "channel": {
      "value": 14
    },
    "subChannel": {
      "value": 1
    }
    "previousState": {
      "channel": {
        "value": 15
      },
      "subChannel": {
        "value": 1
      }
    }
  }
}
```

{% endraw %}

### See also
* [`IncrementChannelRequest`](#IncrementChannelRequest)

## IncrementChannelRequest {#IncrementChannelRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to set the target appliance to channel up the TV by the designated amount. The extension must use the [`IncrementChannelConfirmation`](#IncrementChannelConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|
| `deltaChannel`       | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject)             | Object containing information on the amount of TV channels to change.                              |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementChannelRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-011"
    },
    "deltaChannel": {
      "value": 1
    }
  }
}
```

{% endraw %}

### See also
* [`IncrementChannelConfirmation`](#IncrementChannelConfirmation)

## IncrementFanSpeedConfirmation {#IncrementFanSpeedConfirmation}
Sends the result of requesting the target appliance to increase the fan speed to CEK as a response to the [`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `fanSpeed`            | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject) | Object containing information on the current fan speed. The fan speed represents wind speed and is limited to the following values.<ul><li><code>1</code> : Low wind (phase 1)</li><li><code>2</code>: Medium wind (phase 2)</li><li><code>3</code>: High wind (phase 3)</li></ul> | Optional    |
| `previousState`          | object                      | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.FanSpeed` | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject) | Object containing information on the previous fan speed. The fan speed represents wind speed and is limited to the following values.<ul><li><code>1</code> : Low wind (phase 1)</li><li><code>2</code>: Medium wind (phase 2)</li><li><code>3</code>: High wind (phase 3)</li></ul> | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`IncrementFanSpeedRequest`](#IncrementFanSpeedRequest)

## IncrementFanSpeedRequest {#IncrementFanSpeedRequest}
Mainly used to control appliances such as air purifiers. Requests the Clova Home extension to set the target appliance to increase the fan speed by the designated amount. The extension must use the [`IncrementFanSpeedConfirmation`](#IncrementFanSpeedConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `deltaFanSpeed` | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject) | Object containing information on the amount of speed to change. The fan speed represents wind speed and is limited to the following values.<ul><li><code>1</code> : Low wind (phase 1)</li><li><code>2</code>: Medium wind (phase 2)</li><li><code>3</code>: High wind (phase 3)</li></ul>  |<!-- -->|

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`IncrementFanSpeedConfirmation`](#IncrementFanSpeedConfirmation)

## IncrementIntensityLevelConfirmation {#IncrementIntensityLevelConfirmation}
Sends the result of requesting the target appliance to increase the pressure level, such as air or water pressure, to CEK as a response to the [`DecrementIntensityLevelRequest`](#DecrementIntensityLevelRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `intensityLevel` | [IntensityLevelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#IntensityLevelInfoObject) | Object containing current information on pressure or water pressure intensity.                  | Optional    |
| `previousState`  | object                                  | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.intensityLevel` | [IntensityLevelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#IntensityLevelInfoObject) | Object containing previous information on pressure or water pressure intensity.    | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "be3dde71-84c0-48cf-80d8-440c1ede54d8",
    "name": "IncrementIntensityLevelConfirmation",
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

{% endraw %}

### See also
* [`IncrementIntensityLevelRequest`](#IncrementIntensityLevelRequest)

## IncrementIntensityLevelRequest {#IncrementIntensityLevelRequest}
Requests the Clova Home extension to set the target appliance to increase the pressure level, such as air or water pressure, by the designated amount. The extension must use the [`IncrementIntensityLevelConfirmation`](#IncrementIntensityLevelConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `deltaIntensity`   | [IntensityLevelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#IntensityLevelInfoObject) | Object containing information on the amount of pressure or water pressure intensity to change.           |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementIntensityLevelRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-015"
    },
    "deltaTemperature": {
      "value": 1
    }
  }
}
```

{% endraw %}

### See also
* [`IncrementIntensityLevelConfirmation`](#IncrementIntensityLevelConfirmation)

## IncrementTargetTemperatureConfirmation {#IncrementTargetTemperatureConfirmation}
Sends the result of requesting the target appliance to increase the temperature to CEK as a response to the [`IncrementTargetTemperatureRequest`](#IncrementTargetTemperatureRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `previousState`     | object                                  | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.targetTemperature` | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing previous information on the desired temperature.                 | Optional    |
| `targetTemperature` | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing the desired temperature information to set on the target appliance or that the extension has requested to be set on the target appliance.                               | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementTargetTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": 25
    },
    "previousState": {
      "targetTemperature": {
        "value": 22
      }
    }
  }
}
```

{% endraw %}

### See also
* [`IncrementTargetTemperatureRequest`](#IncrementTargetTemperatureRequest)

## IncrementTargetTemperatureRequest {#IncrementTargetTemperatureRequest}
Mainly used to control appliances such as air conditioners or thermostats. Requests the Clova Home extension to set the target appliance to increase the temperature by the designated amount. The extension must use the [`IncrementTargetTemperatureConfirmation`](#IncrementTargetTemperatureConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md). |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `deltaTemperature` | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing information on the amount of temperature to change.                              |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementTargetTemperatureRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-001"
    },
    "deltaTemperature": {
      "value": 3
    }
  }
}
```

{% endraw %}

### See also
* [`IncrementTargetTemperatureConfirmation`](#IncrementTargetTemperatureConfirmation)

## IncrementVolumeConfirmation {#IncrementVolumeConfirmation}
Sends the result of requesting the target appliance to increase the speaker volume to CEK as a response to the [`IncrementVolumeRequest`](#IncrementVolumeRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `previousState`     | Object                                 | Object containing information on the previous state of the appliance.                           | Optional    |
| `previousState.targetVolume` | [VolumeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#VolumeInfoObject) | Object containing information on the previous volume.                 | Optional    |
| `targetVolume` | [VolumeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#VolumeInfoObject)               | Object containing information on the volume set on the target appliance or that the extension has requested to be set on the target appliance.                 | Optional    |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementVolumeConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetVolume": {
      "value": 20
    },
    "previousState": {
      "targetVolume": {
        "value": 10
      }
    }
  }
}
```

{% endraw %}

### See also
* [`IncrementVolumeRequest`](#IncrementVolumeRequest)

## IncrementVolumeRequest {#IncrementVolumeRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to set the target appliance to increase the speaker volume by the designated amount. The extension must use the [`IncrementVolumeConfirmation`](#IncrementVolumeConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `deltaVolume` | [VolumeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#VolumeInfoObject)                | Object containing information on the amount of volume to change.                              |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "IncrementVolumeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-005"
    },
    "deltaVolume": {
      "value": 10
    }
  }
}
```

{% endraw %}

### See also
* [`IncrementVolumeConfirmation`](#IncrementVolumeConfirmation)

## LowerConfirmation {#LowerConfirmation}
Sends the result of requesting the target appliance to lower the height to CEK as a response to the (#LowerRequest)[`LowerRequest`] message.

### Payload fields

None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "LowerConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

{% endraw %}

### See also
* [`LowerRequest`](#LowerRequest)

## LowerRequest {#LowerRequest}
Mainly used to control an appliance such as a smart bed. Requests the Clova Home extension to lower the height of the target appliance. The extension must use the [`LowerConfirmation`](#LowerConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Remarks
The appliance will move to its maximum position when adjusting the appliance height. To stop while adjusting, the Clova Home extension must receive the [StopRequest](#StopRequest) message.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "253f1f01-c157-411d-8c3f-96ea6173fcc6",
    "name": "LowerRequest",
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

{% endraw %}

### See also
* [`RaiseRequest`](#RaiseRequest)
* [`LowerConfirmation`](#LowerConfirmation)

## MuteConfirmation {#MuteConfirmation}
Sends the result of muting the target appliance to CEK as a response to the [`MuteRequest`](#MuteRequest) message.

### Payload fields
None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "MuteConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

{% endraw %}

### See also
* [`MuteRequest`](#MuteRequest)

## MuteRequest {#MuteRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to mute the target appliance. The extension must use the [`MuteConfirmation`](#MuteConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "MuteRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-005"
    }
  }
}
```

{% endraw %}

### See also
* [`MuteConfirmation`](#MuteConfirmation)

## OpenConfirmation {#OpenConfirmation}
Sends the result of opening the smart curtain or the bidet lid to CEK as a response to the [`OpenRequest`](#OpenRequest) message.

### Payload fields

None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "a4349fd5-7c1c-4fae-9bbd-291749bdd63a",
    "name": "OpenConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

{% endraw %}

### See also
* [`OpenRequest`](#OpenRequest)

## OpenRequest {#OpenRequest}
Used to control appliances such as smart curtains or bidets. Requests the Clova Home extension to open the smart curtain or the bidet lid. The extension must use the [`OpenConfirmation`](#OpenConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "8030275d-0e71-463d-b1d8-3e761e5389ad",
    "name": "OpenRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-012"
    }
  }
}
```

{% endraw %}

### See also
* [`OpenConfirmation`](#OpenConfirmation)

## RaiseConfirmation {#RaiseConfirmation}
Sends the result of requesting the target appliance to raise the height to CEK as a response to the [`RaiseRequest`](#RaiseRequest) message.

### Payload fields

None

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`RaiseRequest`](#RaiseRequest)

## RaiseRequest {#RaiseRequest}
Mainly used to control an appliance such as a smart bed. Requests the Clova Home extension to raise the height of the target appliance. The extension must use the [`RaiseConfirmation`](#RaiseConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Remarks
The appliance will move to its maximum position when adjusting the appliance height. To stop while adjusting, the Clova Home extension must receive the [StopRequest](#StopRequest) message.

### Message example

{% raw %}

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

{% endraw %}

### See also

* [`LowerRequest`](#LowerRequest)
* [`RaiseConfirmation`](#RaiseConfirmation)

## ReleaseModeConfirmation {#ReleaseModeConfirmation}
Sends the result of requesting to disable the operation mode of the current appliance to CEK as a response to the [`ReleaseModeRequest`](#ReleaseModeRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `mode`          | [ModeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject)  | Object containing the operation mode set on the target appliance by the request to disable the operation mode or that has the information to return the extension to the target appliance.      | Optional    |
| `previousState` | [ModeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject)  | Object containing information on the operation mode set on the target appliance before the request to disable the operation mode was made.      | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "ReleaseModeConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "previousState": {
      "mode": {
        "value": "sleep"
      }
    },
    "mode": {
      "value": "wakeup"
    }
  }
}
```

{% endraw %}

### See also
* [`ReleaseModeRequest`](#ReleaseModeRequest)

## ReleaseModeRequest {#ReleaseModeRequest}
Used to disable the operation mode set on the current appliance. Requests the Clova Home extension to return to the previous operation mode or the default operation mode by disabling the operation mode of the appliance. The extension must use the [`ReleaseModeConfirmation`](#ReleaseModeConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken` | string  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md). |<!-- -->|
| `appliance`   | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `mode`        | [ModeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject) | Object containing information on the operation mode to disable in the target appliance.                         |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "ReleaseModeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-006"
    },
    "mode": "sleep"
  }
}
```

{% endraw %}

### See also
* [`ReleaseModeConfirmation`](#ReleaseModeConfirmation)

## SetBrightnessConfirmation {#SetBrightnessConfirmation}
Sends the result of requesting the target appliance to change brightness of lights to CEK as a response to the [`SetBrightnessRequest`](#SetBrightnessRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `brightness`               | [BrightnessInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BrightnessInfoObject) | Object containing the brightness information to set on the target appliance or that the extension has requested to be set on the target appliance.                                | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetBrightnessConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "brightness": {
      "value": 80
    }
  }
}
```

{% endraw %}

### See also
* [`SetBrightnessRequest`](#SetBrightnessRequest)

## SetBrightnessRequest {#SetBrightnessRequest}
Mainly used to control the brightness on appliances such as lights. Requests the Clova Home extension to set the target appliance to change the brightness of lights to the designated value. The extension must use the [`SetBrightnessConfirmation`](#SetBrightnessConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `brightness`       | [BrightnessInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#BrightnessInfoObject) | Object containing information on brightness to set on the target appliance.                |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetBrightnessRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-006"
    },
    "brightness": {
      "value": 80
    }
  }
}
```

{% endraw %}

### See also
* [`SetBrightnessConfirmation`](#SetBrightnessConfirmation)

## SetChannelByNameConfirmation {#SetChannelByNameConfirmation}
Sends the result of requesting the target appliance to change the TV channel using the name of channel to CEK as a response to the [`SetChannelByNameRequest`](#SetChannelByNameRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `channelName`               | [TVChannelNameInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelNameInfoObject) | Object containing the name of the TV channel set on the target appliance or that the extension has requested to be set on the target appliance.                                | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetChannelByNameConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
  	"channelName": {
  		"value": "sbs"
  	}
  }
}
```

{% endraw %}

### See also
* [`SetChannelByNameRequest`](#SetChannelByNameRequest)

## SetChannelByNameRequest {#SetChannelByNameRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to set the target appliance to change the TV channel to the designated channel name. The extension must use the [`SetChannelByNameConfirmation`](#SetChannelByNameConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `channelName`       | [TVChannelNameInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelNameInfoObject) | Object containing information on the name of a TV channel to set on the target appliance.                |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetChannelByNameRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-006"
    },
    "channel": {
      "value": "sbs"
    }
  }
}
```

{% endraw %}

### See also
* [`SetChannelByNameConfirmation`](#SetChannelByNameConfirmation)

## SetChannelConfirmation {#SetChannelConfirmation}
Sends the result of requesting the target appliance to change the TV channel using the number of the channel to CEK as a response to the [`SetChannelRequest`](#SetChannelRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `channel`     | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject)  | Object containing the TV channel information set on the target appliance or that the extension has requested to be set on the target appliance.      | Optional    |
| `subChannel`  | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject)  | Object containing the subchannel information of the TV channel set on the target appliance or of that the extension has requested to be set on the target appliance. | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetChannelConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "channel": {
      "value":15
    },
    "subChannel": {
      "value": 1
    }
  }
}
```

{% endraw %}

### See also
* [`SetChannelRequest`](#SetChannelRequest)

## SetChannelRequest {#SetChannelRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to set the target appliance to change the TV channel to the designated channel number. The extension must use the [`SetChannelConfirmation`](#SetChannelConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `channel`       | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing information on the TV channel to set on the target appliance.                |<!-- -->|
| `subChannel`    | [TVChannelInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVChannelInfoObject) | Object containing the subchannel information of the TV channel to be set on the target appliance.         | Optional   |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetChannelRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-006"
    },
    "channel": {
      "value": 15
    },
    "subChannel": {
      "value": 1
    }
  }
}
```

{% endraw %}

### See also
* [`SetChannelConfirmation`](#SetChannelConfirmation)

## SetColorConfirmation {#SetColorConfirmation}
Sends the result of requesting the target appliance to change the color of lights, screens, or lamps to CEK as a response to the [`SetColorRequest`](#SetColorRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `color`   | [ColorInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ColorInfoObject) | Object containing the color information on lights, screens, or lamps set on the target appliance or that the extension has requested to be set on the target appliance.                                | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`SetColorRequest`](#SetColorRequest)

## SetColorRequest {#SetColorRequest}
Mainly used to control appliances such as smart lamps. Requests the Clova Home extension to change the color of lights, screens, or lamps of the target appliance. The extension must use the [`SetColorConfirmation`](#SetColorConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `color`         | [ColorInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ColorInfoObject) | Object containing color information to set on lights, screens, or lamps of the target appliance.            |<!-- -->|

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`SetColorConfirmation`](#SetColorConfirmation)

## SetColorTemperatureConfirmation {#SetColorTemperatureConfirmation}
Sends the result of requesting the target appliance to change the color temperature of lights, screens, or lamps to CEK as a response to the [`SetColorTemperatureRequest`](#SetColorTemperatureRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `colorTemperature`   | [ColorTemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ColorTemperatureInfoObject) | Object containing the color temperature information on lights, screens, or lamps set on the target appliance or that the extension has requested to be set on the target appliance.                                | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`SetColorTemperatureRequest`](#SetColorTemperatureRequest)

## SetColorTemperatureRequest {#SetColorTemperatureRequest}
Mainly used to control appliances such as smart lamps. Requests the Clova Home extension to change the color temperature of lights, screens, or lamps of the target appliance. The extension must use the [`SetColorTemperatureConfirmation`](#SetColorTemperatureConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `colorTemperature` | [ColorTemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ColorTemperatureInfoObject) | Object containing the color temperature information to set on lights, screens, or lamps of the target appliance.                |<!-- -->|

### Message example

{% raw %}

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

{% endraw %}

### See also
* [`SetColorTemperatureConfirmation`](#SetColorTemperatureConfirmation)

## SetFanSpeedConfirmation {#SetFanSpeedConfirmation}
Sends the result of requesting the target appliance to change the fan speed to CEK as a response to the [`SetFanSpeedRequest`](#SetFanSpeedRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `fanSpeed`               | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject) | Object containing the fan speed information set on the target appliance or that the extension has requested to be set on the target appliance. The fan speed represents wind speed and is limited to the following values.<ul><li><code>1</code> : Low wind (phase 1)</li><li><code>2</code>: Medium wind (phase 2)</li><li><code>3</code>: High wind (phase 3)</li></ul> | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetFanSpeedConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "fanSpeed": {
      "value": 2
    }
  }
}
```

{% endraw %}

### See also
* [`SetFanSpeedRequest`](#SetFanSpeedRequest)

## SetFanSpeedRequest {#SetFanSpeedRequest}
Mainly used to control appliances such as air purifiers. Requests the Clova Home extension to change the fan speed of the target appliance to the designated value. The extension must use the [`SetFanSpeedConfirmation`](#SetFanSpeedConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `fanSpeed`       | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject) | The fan speed represents wind speed and is limited to the following values.<ul><li><code>1</code> : Low wind (phase 1)</li><li><code>2</code>: Medium wind (phase 2)</li><li><code>3</code>: High wind (phase 3)</li></ul>     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetFanSpeedRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-004"
    },
    "fanSpeed": {
      "value": 2
    }
  }
}
```

{% endraw %}

### See also
* [`SetFanSpeedConfirmation`](#SetFanSpeedConfirmation)

## SetFreezerTargetTemperatureConfirmation {#SetFreezerTargetTemperatureConfirmation}
Sends the result of requesting the freezer to change the desired temperature to CEK as a response to the [`SetFreezerTargetTemperatureRequest`](#SetFreezerTargetTemperatureRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `targetTemperature`               | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing the desired temperature information to set on the target appliance or that the extension has requested to be set on the target appliance.                                | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetFreezerTargetTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": -18
    }
  }
}
```

{% endraw %}

### See also
* [`SetFreezerTargetTemperatureRequest`](#SetFreezerTargetTemperatureRequest)

## SetFreezerTargetTemperatureRequest {#SetFreezerTargetTemperatureRequest}
Used to control appliances such as refrigerators. Requests the Clova Home extension to change the desired temperature of the freezer compartment to the designated value. The extension must use the [`SetFreezerTargetTemperatureConfirmation`](#SetFreezerTargetTemperatureConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included.        |<!-- -->|
| `targetTemperature`       | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing the desired temperature information to set on the target appliance.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetFreezerTargetTemperatureRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-021"
    },
    "targetTemperature": {
      "value": -18
    }
  }
}
```

{% endraw %}

### See also
* [`SetFreezerTargetTemperatureConfirmation`](#SetFreezerTargetTemperatureConfirmation)

## SetFridgeTargetTemperatureConfirmation {#SetFridgeTargetTemperatureConfirmation}
Sends the result of requesting the fridge to change the desired temperature to CEK as a response to the [`SetFridgeTargetTemperatureRequest`](#SetFridgeTargetTemperatureRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `targetTemperature`               | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing the desired temperature information to set on the target appliance or that the extension has requested to be set on the target appliance.                                | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetFridgeTargetTemperatureConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetTemperature": {
      "value": 5
    }
  }
}
```

{% endraw %}

### See also
* [`SetFridgeTargetTemperatureRequest`](#SetFridgeTargetTemperatureRequest)

## SetFridgeTargetTemperatureRequest {#SetFridgeTargetTemperatureRequest}
Used to control appliances such as refrigerators. Requests the Clova Home extension to change the desired temperature of the fridge compartment to the designated value. The extension must use the [`SetFridgeTargetTemperatureConfirmation`](#SetFridgeTargetTemperatureConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included.        |<!-- -->|
| `targetTemperature`       | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing the desired temperature information to set on the target appliance.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetFridgeTargetTemperatureRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-021"
    },
    "targetTemperature": {
      "value": 5
    }
  }
}
```

{% endraw %}

### See also
* [`SetFridgeTargetTemperatureConfirmation`](#SetFridgeTargetTemperatureConfirmation)

## SetInputSourceByNameConfirmation {#SetInputSourceByNameConfirmation}
Sends the result of requesting the target appliance to change to a specified TV input source to CEK as a response to the [`SetInputSourceByNameRequest`](#SetInputSourceByNameRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `sourceName`               | [TVInputSourceNameInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVInputSourceNameInfoObject) | Object containing the input source name to set on the target appliance or that the extension has requested to be set on the target appliance     | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetInputSourceByNameConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "sourceName": {
      "value": "HDMI1"
    }
  }
}
```

{% endraw %}

### See also
* [`SetInputSourceByNameRequest`](#SetInputSourceByNameRequest)

## SetInputSourceByNameRequest {#SetInputSourceByNameRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to change to a specified input source. The extension must use the [`SetInputSourceByNameConfirmation`](#SetInputSourceByNameConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included.        |<!-- -->|
| `sourceName`       | [TVInputSourceNameInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TVInputSourceNameInfoObject) | Object containing the input source information to set on the target appliance.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetInputSourceByNameRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-021"
    },
    "sourceName": {
      "value": "HDMI1"
    }
  }
}
```

{% endraw %}

### See also
* [`SetInputSourceByNameConfirmation`](#SetInputSourceByNameConfirmation)

## SetLockStateConfirmation {#SetLockStateConfirmation}
Sends the result of requesting the target appliance to lock or unlock to CEK as a response to the [`SetLockStateRequest`](#SetLockStateRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `lockState`   | string  | The lock state of an appliance set on the target appliance or that the extension has requested to be set on the target appliance. Available values are: <ul><li><code>"LOCKED"</code></li><li><code>"UNLOCKED"</code></li></ul> |<!-- -->|


### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetLockStateConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "lockState": "LOCKED"
  }
}
```

{% endraw %}

### See also
* [`SetLockStateRequest`](#SetLockStateRequest)

## SetLockStateRequest {#SetLockStateRequest}
Mainly used to control an appliance such as a smart valve. Requests the Clova Home extension to lock or unlock the target appliance. The extension must use the [`SetLockStateConfirmation`](#SetLockStateConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `lockState`       | string | The lock state of an appliance to set. Available values are: <ul><li><code>"LOCKED"</code></li><li><code>"UNLOCKED"</code></li></ul> |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "SetLockStateRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-012"
    },
    "lockState": "LOCKED"
  }
}
```

{% endraw %}

### See also
* [`SetLockStateConfirmation`](#SetLockStateConfirmation)

## SetModeConfirmation {#SetModeConfirmation}
Sends the result of requesting the target appliance to change the operation mode to CEK as a response to the [`SetModeRequest`](#SetModeRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `mode`        | [ModeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject)  | Object containing the operation mode set on the target appliance or that the extension has requested to be set on the target appliance.      | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetModeConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "mode": {
      "value": "sleep"
    }
  }
}
```

{% endraw %}

### See also
* [`SetModeRequest`](#SetModeRequest)

## SetModeRequest {#SetModeRequest}
Used to control the operation mode of an appliance. Requests the Clova Home extension to change the operation mode of the appliance to the designated value. The extension must use the [`SetModeConfirmation`](#SetModeConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken` | string  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md). |<!-- -->|
| `appliance`   | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `mode`        | [ModeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject) | Object containing information on the operation mode to set on the target appliance.                         |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "SetModeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-006"
    },
    "mode": {
        "value": "hotwater"
    }
  }
}
```

{% endraw %}

### See also
* [`SetModeConfirmation`](#SetModeConfirmation)

## SetTargetTemperatureConfirmation {#SetTargetTemperatureConfirmation}
Sends the result of requesting the target appliance to change the set temperature to CEK as a response to the [`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `targetTemperature`               | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing the desired temperature information to set on the target appliance or that the extension has requested to be set on the target appliance.                                | Optional    |

### Remarks

You do not have to enter the value if the information to enter for the payload cannot be retrieved from the target appliance. You can simply notify the user that the appliance control request is successfully processed without stating specific information.

### Message example

{% raw %}

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
    }
  }
}
```

{% endraw %}

### See also
* [`SetTargetTemperatureRequest`](#SetTargetTemperatureRequest)

## SetTargetTemperatureRequest {#SetTargetTemperatureRequest}
Mainly used to control appliances such as air conditioners and thermostats. Requests the Clova Home extension to set the target appliance to change the desired temperature to the designated value. The extension must use the [`SetTargetTemperatureConfirmation`](#SetTargetTemperatureConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`   | string | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`     | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject) | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|
| `targetTemperature`       | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing the desired temperature information to set on the target appliance.                |<!-- -->|

### Message example

{% raw %}

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
    }
  }
}
```

{% endraw %}

### See also
* [`SetTargetTemperatureConfirmation`](#SetTargetTemperatureConfirmation)

## StartRecordingConfirmation {#StartRecordingConfirmation}
Sends the result of requesting the target appliance to start recording on the current channel to CEK as a response to the [`StartRecordingRequest`](#StartRecordingRequest) message.

### Payload fields

None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "a4349fd5-7c1c-4fae-9bbd-291749bdd63a",
    "name": "StartRecordingConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": { }
}
```

{% endraw %}

### See also
* [`StartRecordingRequest`](#StartRecordingRequest)

## StartRecordingRequest {#StartRecordingRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to start recording the program on the current channel. The extension must use the [`StartRecordingConfirmation`](#StartRecordingConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "8030275d-0e71-463d-b1d8-3e761e5389ad",
    "name": "StartRecordingRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-016"
    }
  }
}
```

{% endraw %}

### See also
* [`StartRecordingConfirmation`](#StartRecordingConfirmation)

## StopConfirmation {#StopConfirmation}
Sends the result of stopping the current action of the target appliance to CEK as a response to the [`StopRequest`](#StopRequest) message.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `phase`       | [PhaseInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#PhaseInfoObject) | Object containing information on the last phase of action performed by the appliance before stopping.   | Optional  |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "a4349fd5-7c1c-4fae-9bbd-291749bdd63a",
    "name": "StopConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "phase": {
      "value": "Wash"
    }
  }
}
```

{% endraw %}

### See also
* [`StopRequest`](#StopRequest)

## StopRequest {#StopRequest}
Requests the Clova Home extension to stop the current action of the appliance. The extension must use the [`StopConfirmation`](#StopConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "8030275d-0e71-463d-b1d8-3e761e5389ad",
    "name": "StopRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-016"
    }
  }
}
```

{% endraw %}

### See also
* [`StopConfirmation`](#StopConfirmation)

## StopRecordingConfirmation {#StopRecordingConfirmation}
Sends the result of requesting the target appliance to stop recording on the current channel to CEK as a response to the [`StopRecordingRequest`](#StopRecordingRequest) message.

### Payload fields

None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "a4349fd5-7c1c-4fae-9bbd-291749bdd63a",
    "name": "StopRecordingConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": { }
}
```

{% endraw %}

### See also
* [`StopRecordingRequest`](#StopRecordingRequest)

## StopRecordingRequest {#StopRecordingRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to stop recording the program on the current channel. The extension must use the [`StopRecordingConfirmation`](#StopRecordingConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included.     |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "8030275d-0e71-463d-b1d8-3e761e5389ad",
    "name": "StopRecordingRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-016"
    }
  }
}
```

{% endraw %}

### See also
* [`StopRecordingConfirmation`](#StopRecordingConfirmation)

## TurnOffConfirmation {#TurnOffConfirmation}
Sends the result of requesting the target appliance to turn off to CEK as a response to the [`TurnOffRequest`](#TurnOffRequest) message.

### Payload fields
None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "TurnOffConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

{% endraw %}

### See also
* [`TurnOffRequest`](#TurnOffRequest)

## TurnOffRequest {#TurnOffRequest}
Requests the Clova Home extension to turn off the target appliance. The extension must use the [`TurnOffConfirmation`](#TurnOffConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "TurnOffRequest",
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

{% endraw %}

### See also
* [`TurnOffConfirmation`](#TurnOffConfirmation)

## TurnOnConfirmation {#TurnOnConfirmation}
Sends the result of requesting the target appliance to turn on to CEK as a response to the [`TurnOnRequest`](#TurnOnRequest) message.

### Payload fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:---------:|
| `targetTemperature`               | [TemperatureInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#TemperatureInfoObject) | Object containing information on current temperature. | Optional |
| `fanSpeed`            | [SpeedInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#SpeedInfoObject)  | Object containing information on the current fan speed.| Optional |
| `mode`            | [ModeInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ModeInfoObject)  | Object containing information on current operation mode.| Optional |

### Remarks
When there is information to notify to the user, you can return a response to CEK with a value in payload. The fields available for the response depends on the value of `applianceTypes`.

| applianceTypes     | Field available for response     |
|--------------------|---------------------------------|
| `"AIRCONDITIONER"` | `mode`、 `fanSpeed`、 `targetTemperature` |
| `"AIRPURIFIER"`    | `fanSpeed`   |
| `"HEATER"`         | `targetTemperature` |
| `"HUMIDIFIER"`     | `fanSpeed` |
| `"WATERBOILER"`    | `mode`、 `targetTemperature` |

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "TurnOnConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

{% endraw %}

### See also
* [`TurnOnRequest`](#TurnOnRequest)

## TurnOnRequest {#TurnOnRequest}
Requests the Clova Home extension to turn on the target appliance. The extension must use the [`TurnOnConfirmation`](#TurnOnConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "TurnOnRequest",
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

{% endraw %}

### See also
* [`TurnOnConfirmation`](#TurnOnConfirmation)

## UnmuteConfirmation {#UnmuteConfirmation}
Sends the result of turning on (unmuting) the sound of the target appliance to CEK as a response to the [`UnmuteRequest`](#UnmuteRequest) message.

### Payload fields
None

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "UnmuteConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```

{% endraw %}

### See also
* [`UnmuteRequest`](#UnmuteRequest)

## UnmuteRequest {#UnmuteRequest}
Mainly used to control appliances such as TVs or set-top boxes. Requests the Clova Home extension to turn on (unmute) the sound of the target appliance. The extension must use the [`UnmuteConfirmation`](#UnmuteConfirmation) message as a response to this request.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | Access token of the user account for an IoT service. CEK sends the access token of a user account acquired from the authorization server of a third-party service. For more information, see [Linking user accounts](/CEK/Guides/Link_User_Account.md).                          |<!-- -->|
| `appliance`        | [ApplianceInfoObject](/CEK/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | Object containing the appliance information. The `applianceId` field is always included. |<!-- -->|

### Message example

{% raw %}

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "UnmuteRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-005"
    }
  }
}
```

{% endraw %}

### See also
* [`UnmuteConfirmation`](#UnmuteConfirmation)
