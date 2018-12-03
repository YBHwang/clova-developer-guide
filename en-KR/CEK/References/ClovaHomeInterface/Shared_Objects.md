# Shared objects {#SharedObjects}
These shared objects are used in the message `payload` when sending [Clova Home extension messages](/CEK/References/CEK_API.md#ClovaHomeExtMessage):

| Object name            | Description                                            |
|--------------------|---------------------------------------------------|
| [ActionInfoObject](#ActionInfoObject)                   | Object containing information on appliance control actions.  |
| [AirQualityInfoObject](#AirQualityInfoObject)             | Object containing information on air quality.            |
| [ApplianceInfoObject](#ApplianceInfoObject)               | Object containing information on an IoT appliance.        |
| [BatteryInfoObject](#BatteryInfoObject)                   | Object containing information on battery.            |
| [BillInfoObject](#BillInfoObject)                         | Object containing information on billing.             |
| [BrightnessInfoObject](#BrightnessInfoObject)             | Object containing information on light or screen brightness. |
| [ColorInfoObject](#ColorInfoObject)                       | Object containing information on the color of lights, screens, or lamps of the target appliance.  |
| [ColorTemperatureInfoObject](#ColorTemperatureInfoObject) | Object containing information on the color temperature of lights, screens, or lamps of the target appliance.  |
| [ConsumptionInfoObject](#ConsumptionInfoObject)           | Object containing information on energy consumption.       |
| [CustomCommandInfoObject](#CustomCommandInfoObject)       | Object containing information on custom commands.   |
| [CustomInfoObject](#CustomInfoObject)                     | Object containing information directly entered by the user such as an customized name, required units, or figures. |
| [EndpointInfoObject](#EndpointInfoObject)                 | Object containing information on the endpoint, which the target appliance must ultimately control.  |
| [ExpendableInfoObject](#ExpendableInfoObject)             | Object containing information on usage or remaining lifespan of appliance parts.  |
| [FineDustInfoObject](#FineDustInfoObject)                 | Object containing information on fine dust.          |
| [IntensityLevelInfoObject](#IntensityLevelInfoObject)     | Object containing information on pressure or water pressure intensity.   |
| [ModeInfoObject](#ModeInfoObject)                         | Object containing information on the operation mode.          |
| [HumidityInfoObject](#HumidityInfoObject)                 | Object containing information on humidity.              |
| [PeriodInfoObject](#PeriodInfoObject)                     | Object containing information on the period.          |
| [PhaseInfoObject](#PhaseInfoObject)                       | Object containing information on the phase of appliance actions.     |
| [ProgressiveTaxBracketInfoObject](#ProgressiveTaxBracketInfoObject)  | Object containing information on progressive tax brackets. |
| [RatioInfoObject](#RatioInfoObject)                       | Object containing information on the ratio.          |
| [SittingStateInfoObject](#SittingStateInfoObject)         | Object containing the sit-down information of the user on appliances such as a smart chair.  |
| [SleepScoreInfoObject](#SleepScoreInfoObject)             | Object containing information on sleep score.          |
| [SpeedInfoObject](#SpeedInfoObject)                       | Object containing information on speed.              |
| [TemperatureInfoObject](#TemperatureInfoObject)           | Object containing information on temperature.          |
| [TVChannelNameInfoObject](#TVChannelNameInfoObject)       | Object containing information on a TV channel name.      |
| [TVChannelInfoObject](#TVChannelInfoObject)               | Object containing information on a TV channel.           |
| [UltraFineDustInfoObject](#UltraFineDustInfoObject)       | Object containing information on ultrafine dust.         |
| [VolumeInfoObject](#VolumeInfoObject)                     | Object containing information on volume.          |

## ActionInfoObject {#ActionInfoObject}
ActionInforObject contains information on appliance control actions and expresses a command for an action to be performed on an appliance.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------:|
| `applianceId` | string  | Device ID                      | Required     |
| `action`      | string  | The action of appliance control. See the [Actions](#Actions) table under the [ApplianceInfoObject](#ApplianceInfoObject) section for the list of actions.     | Required/Always     |

### Object Example
{% raw %}

```json
// Example: An example used in DiscoverAppliancesResponse message
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "customCommands": [
      {
        "name": "Good morning",
        "actions": [
          {
            "applianceId": "device-001",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-0012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-0013",
            "action": "TurnOn"
          }
        ]
      },
      {
        "name": "Good evening",
        "actions": [
          {
            "applianceId": "device-0011",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-0012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-0013",
            "action": "TurnOn"
          }
        ]
      }
    ],
    "discoveredAppliances": [
      {
        "applianceId": "device-001",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "Smart lamp",
        "version": "v1.0",
        "friendlyName": "Living room lamp",
        "friendlyDescription": "A lamp that can be controlled using a smartphone",
        "isIr": false,
        "isReachable": true,
          "actions": [
            "DecrementBrightness",
            "HealthCheck",
            "IncrementBrightness",
            "SetBrightness",
            "TurnOn",
            "TurnOff"
        ],
        "applianceTypes": ["LIGHT"],
        "additionalApplianceDetails": {}
      },
      {
        "applianceId": "device-002",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "Smart plug",
        "version": "v1.0",
        "friendlyName": "Kitchen plug",
        "friendlyDescription": "An energy-saving plug",
        "isIr": false,
        "isReachable": true,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {},
        "location": "LIVING_ROOM",
        "tags": ["Study", "Johnroom", "Poweroffdeviceforawaymode"]
      }
    ]
  }
}
```

{% endraw %}

### See also
* [CustomCommandInfoObject](#CustomCommandInfoObject)
* [`DiscoverAppliancesResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DiscoverAppliancesResponse)

## AirQualityInfoObject {#AirQualityInfoObject}
AirQualityInfoObject contains information on air quality. This is used to indicate the air quality measured by the appliance. It is expressed as a string.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `index`       | string  | Air quality level. It is limited to the following values.<ul><li><code>"good"</code>: Good</li><li><code>"normal"</code>: Normal</li><li><code>"bad"</code>: Bad</li><li><code>"verybad"</code>: Very bad</li></ul> | Required   |

### Object Example
{% raw %}

```json
// Example: An example used in the GetAirQualityResponse message
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
    }
  }
}
```

{% endraw %}

### See also
* [`GetAirQualityRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAirQualityRequest)
* [`GetAirQualityResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAirQualityResponse)

## ApplianceInfoObject {#ApplianceInfoObject}
ApplianceInfoObject contains the information on IoT appliances. This is used to send a list of appliances registered in the user account to CEK or to request the Clova Home extension to control a specific appliance.

### Object fields used in requests
| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:-------------:|
| `additionalApplianceDetails` | object        | Additional information provided by the manufacturer or IoT service.                                 | Conditional    |
| `applianceId`                | string        | Device ID                                                                         | Always     |

### Object fields used in responses

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `actions[]`                  | string array  | List of actions supported by an appliance. The client must restrict the user to controlling the IoT device within the scope of actions supported by the appliance. | Optional    |
| `additionalApplianceDetails` | object        | Additional information provided by the manufacturer or IoT service.                                 | Optional    |
| `applianceId`                | string        | Device ID                                                                        | Required    |
| `applianceTypes[]`           | string array  | The appliance type. The `applicationType` determines the value of the `actions` field, which is the action that can be performed an appliance. You must designate the type of appliance registered to the user account of the IoT service as one of the following values: Select the appliance type by referring to the items in the Remarks section.                                                                              | Required    |
| `friendlyName`               | string        | The name of the appliance given by the user.                                                           | Optional    |
| `friendlyDescription`        | string        | The description of the appliance.                                                                  | Optional    |
| `isIr`                       | boolean       | Whether the appliance is controlled by infrared communication.<ul><li><code>true</code>: By infrared communication</li><li><code>false</code>: Not by infrared communication</li></ul> <div class="note"><p><strong>Note!</strong></p><p>The following restrictions apply when controlling appliances via infrared communication (<code>true</code>):</p><ul><li>Clova does not send the results of device control to users.</li><li>Even if the appliance type supports the <code>HealthCheck</code> action, Clova does not send <code>HealthCheck</code> action-related requests to the extension.</li></ul></div>  | Optional  |
| `isReachable`                | boolean       | Whether or not remote control is available.<ul><li>true: Remote control is available</li><li>false: Remote control is not available</li></ul>  | Optional    |
| `manufacturerName`           | string        | The name of the appliance manufacturer.                                                                  | Optional    |
| `modelName`                  | string        | The name of the appliance model.                                                                   | Optional    |
| `version`                    | string        | The software version of the manufacturer.                                                            | Optional    |
| `location`                   | string        | The location of the appliance installation. Enter the code value in the [Locations](#Locations) field. The Korean text that corresponds to the inputted code value is added to the `tags` field.            | Optional    |
| `tags[]`                     | string array  | The list of tags added to the appliance by the user. The user can add various attributes as tags such as location of installation, purpose of use, or product brand to the appliance from the Clova app or the IoT service. Appliances with the same attributes (tags) are grouped together, and simultaneous control is possible if the appliances in the same group have identical permitted actions.  | Optional  |

### Remarks
If the user requests the appliance list using the [`DiscoverAppliancesRequest`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesRequest) message, the Clova Home extension must fill out all the fields except the `additionalApplianceDetails` field, and deliver the information. Here, the value of the `actions` field is normally determined by the `applianceTypes` field and may have the following values depending on the value of the `applianceTypes` field:

| applianceTypes | Description         | Permitted actions                                  |
|----------------|-------------|-------------------------------------------------|
| `"AIRCONDITIONER"`  | Type of an air conditioner         | DecrementFanSpeed, DecrementTargetTemperature, GetCurrentTemperature, GetDeviceState, GetTargetTemperature, HealthCheck, IncrementFanSpeed, IncrementTargetTemperature, SetFanSpeed, SetMode, SetTargetTemperature, TurnOff, TurnOn               |
| `"AIRPURIFIER"`     | Type of an air purifier        | DecrementFanSpeed, GetAirQuality, GetDeviceState, GetFineDust, GetUltraFineDust, HealthCheck, IncrementFanSpeed, ReleaseMode, SetFanSpeed, SetMode, TurnOff, TurnOn  |
| `"AIRSENSOR"`       | Type of an air sensor     | GetAirQuality, GetCurrentTemperature, GetDeviceState, GetFineDust, GetHumidity, GetUltraFineDust, HealthCheck                                     |
| `"BIDET"`           | Type of a bidet            | Close, GetDeviceState, GetExpendableState, HealthCheck, Open, TurnOff, TurnOn                                                                     |
| `"BODYWEIGHTSCALE"` | Type of a weighing scale           | GetDeviceState, HealthCheck                                                                                                                       |
| `"CLOTHESCAREMACHINE"` | Type of a clothing care machine    | GetDeviceState, GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                          |
| `"CLOTHESDRYER"`    | Type of a drying machine       | GetDeviceState, GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                          |
| `"CLOTHESWASHER"`   | Type of a washing machine       | GetDeviceState, GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                          |
| `"DEHUMIDIFIER"`    | Type of a dehumidifier           | GetCurrentTemperature, GetDeviceState, GetHumidity, HealthCheck, SetFanSpeed, TurnOff, TurnOn                                                     |
| `"DISHWASHER"`      | Type of a dishwasher       | GetDeviceState, GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                          |
| `"ELECTRICKETTLE"`  | Type of an electric kettle       | GetCurrentTemperature, GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                               |
| `"ELECTRICTOOTHBRUSH"` | Type of an electric toothbrush     | GetDeviceState, HealthCheck                                                                                                                        |
| `"FAN"`             | Type of a fan           | GetDeviceState, HealthCheck, SetMode, TurnOff, TurnOn                                                                                             |
| `"HEATER"`          | Type of a heater            | DecrementTargetTemperature, GetCurrentTemperature, GetDeviceState, GetTargetTemperature, HealthCheck, IncrementTargetTemperature, TurnOff, TurnOn |
| `"HUMIDIFIER"`      | Type of a humidifier           | GetCurrentTemperature, GetDeviceState, GetHumidity, HealthCheck, ReleaseMode, SetFanSpeed, SetMode, TurnOff, TurnOn                               |
| `"KIMCHIREFRIGERATOR"` | Type of a kimchi refrigerator    | GetDeviceState, HealthCheck                                                                                                                       |
| `"LIGHT"`           | Type of a smart lighting   | DecrementBrightness, DecrementVolume HealthCheck, GetDeviceState, IncrementBrightness, IncrementVolume SetBrightness, SetColor, SetColorTemperature, SetMode, TurnOff, TurnOn            |
| `"MASSAGECHAIR"`    | Type of a massage chair        | DecrementIntensityLevel, GetDeviceState, HealthCheck, IncrementIntensityLevel, TurnOff, TurnOn                                                     |
| `"MICROWAVE"`       | Type of a microwave      | GetDeviceState, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                                      |
| `"MOTIONSENSOR"`    | Type of a motion detector    | GetDeviceState, HealthCheck                                                                                                                        |
| `"OPENCLOSESENSOR"` | Type of an open-close sensor    | GetCloseTime, GetDeviceState, GetOpenState, GetOpenTime, HealthCheck                                                                               |
| `"OVEN"`            | Type of an oven            | GetDeviceState, GetRemainingTime, HealthCheck                                                                                                      |
| `"POWERSTRIP"`      | Type of a power strip         | GetConsumption, GetDeviceState, GetEstimateBill, GetProgressiveTaxBracket, HealthCheck, TurnOff, TurnOn                                             |
| `"PURIFIER"`        | Type of a water purifier          | GetDeviceState, GetExpendableState, HealthCheck, ReleaseMode, SetMode, SetTargetTemperature                                                         |
| `"RANGE"`           | Type of an electric range          | GetDeviceState, HealthCheck                                                                                                                         |
| `"RANGEHOOD"`       | Type of a range hood      | GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                                                        |
| `"REFRIGERATOR"`    | Type of a refrigerator          | GetDeviceState, HealthCheck, ReleaseMode, SetMode, SetTargetTemperature                                                                             |
| `"RICECOOKER"`      | Type of a rice cooker        | GetCleaningCycle, GetDeviceState, GetExpendableState, GetKeepWarmTime, GetPhase, GetRemainingTime, HealthCheck, ReleaseMode, SetMode, Stop, TurnOff, TurnOn          |
| `"ROBOTVACUUM"`     | Type of a robot vacuum       | Charge, GetBatteryInfo, GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                               |
| `"SETTOPBOX"`       | Type of a set-top box     | DecrementChannel, DecrementVolume, GetDeviceState, HealthCheck, IncrementChannel, IncrementVolume, Mute, SetChannel, SetChannelByName, TurnOff, TurnOn, Unmute |
| `"SLEEPINGMONITOR"` | Type of a sleep sensor        | GetAsleepDuration, GetAwakeDuration, GetDeviceState, GetSleepScore, GetSleepStartTime, HealthCheck, TurnOff, TurnOn                                |
| `"SMARTBED"`        | Type of a smart bed      | GetDeviceState, HealthCheck, Lower, Raise, Stop                                                                                                     |
| `"SMARTCHAIR"`      | Type of a smart chair      | GetCurrentSittingState, GetDeviceState, GetRightPostureRatio, GetUsageTime, HealthCheck                                                             |
| `"SMARTCURTAIN"`    | Type of a smart curtain      | Close, GetDeviceState, HealthCheck, Open, Stop                                                                                                      |
| `"SMARTHUB"`        | Type of a smart hub      | GetCurrentTemperature, GetDeviceState, GetHumidity, GetTargetTemperature, HealthCheck, SetMode                                                      |
| `"SMARTMETER"`      | Type of a smart meter      | GetConsumption, GetCurrentBill, GetDeviceState, GetEstimateBill, GetProgressiveTaxBracket, HealthCheck                                              |
| `"SMARTPLUG"`       | Type of a smart plug     | GetConsumption, GetDeviceState, GetEstimateBill, HealthCheck, TurnOff, TurnOn                                                                       |
| `"SMARTTV"`         | Type of a smart TV       | DecrementChannel, DecrementVolume, GetDeviceState, HealthCheck, IncrementChannel, IncrementVolume, Mute, SetChannel, SetChannelByName, TurnOff, TurnOn, Unmute |
| `"SMARTVALVE"`      | Type of a smart valve      | GetDeviceState, GetLockState, SetLockState                                                                                                           |
| `"SMOKESENSOR"`     | Type of a smoke sensor        | GetDeviceState, HealthCheck                                                                                                                         |
| `"SWITCH"`          | Type of a switch to control outlets in homes | GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                                          |
| `"THERMOSTAT"`      | Type of a thermostat   | DecrementTargetTemperature, GetConsumption, GetCurrentTemperature, GetDeviceState, GetEstimateConsumption, GetTargetTemperature, HealthCheck, IncrementTargetTemperature, SetMode, SetTargetTemperature TurnOff, TurnOn       |
| `"VENTILATOR"`      | Type of a ventilator          | GetAirQuality, GetDeviceState, GetHumidity, GetTargetTemperature, HealthCheck, ReleaseMode, SetFanSpeed, SetMode, TurnOff, TurnOn                    |
| `"WATERBOILER"`     | Type of a water boiler          | GetDeviceState, HealthCheck, SetMode, TurnOff, TurnOn                                                                                                |

<div class="note">
<p><strong>Note!</strong></p>
<p>You can restrict actions to allow fewer actions than are permitted by the applianceTypes depending on the functional limitations of the actual appliance. For example, if there is no function to adjust the fan speed on the air purifier (<code>AIRPURIFIER</code> type), the DiscoverAppliancesResponse message must be sent without the IncrementFanSpeed and DecrementFanSpeed fields from the permitted actions. Note that if a user requests an unsupported action, CEK informs the user immediately that the request is not within the permitted range.</p>
</div>

### Actions {#Actions}
The table below lists the [interfaces](/CEK/References/CEK_API.md#ClovaHomeExtInterface) related to each action:

| Action                    | Related interface                            |
|----------------------------|------------------------------------------|
| Charge                     | [`ChargeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ChargeConfirmation), [`ChargeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ChargeRequest) |
| Close                      | [`CloseConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#CloseConfirmation), [`CloseRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#CloseRequest)  |
| DecrementBrightness        | [`DecrementBrightnessConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementBrightnessConfirmation), [`DecrementBrightnessRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementBrightnessRequest) |
| DecrementChannel           | [`DecrementChannelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementChannelConfirmation), [`DecrementChannelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementChannelRequest) |
| DecrementFanSpeed          | [`DecrementFanSpeedConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementFanSpeedConfirmation), [`DecrementFanSpeedRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementFanSpeedRequest) |
| DecrementIntensityLevel    | [`DecrementIntensityLevelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementIntensityLevelConfirmation), [`DecrementIntensityLevelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementIntensityLevelRequest)  |
| DecrementTargetTemperature | [`DecrementTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementTargetTemperatureConfirmation), [`DecrementTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementTargetTemperatureRequest) |
| DecrementVolume            | [`DecrementVolumeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementVolumeConfirmation), [`DecrementVolumeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementVolumeRequest) |
| GetAirQuality              | [`GetAirQualityRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAirQualityRequest), [`GetAirQualityResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAirQualityResponse) |
| GetAsleepDuration              | [`GetAsleepDurationRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAsleepDurationRequest), [`GetAsleepDurationResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAsleepDurationResponse) |
| GetAwakeDuration              | [`GetAwakeDurationRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAwakeDurationRequest), [`GetAwakeDurationResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAwakeDurationResponse) |
| GetBatteryInfo              | [`GetBatteryInfoRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetBatteryInfoRequest), [`GetBatteryInfoResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetBatteryInfoResponse) |
| GetCleaningCycle                | [`GetCleaningCycleRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCleaningCycleRequest), [`GetCleaningCycleResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCleaningCycleResponse)  |
| GetCloseTime                | [`GetCloseTimeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCloseTimeRequest), [`GetCloseTimeResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCloseTimeResponse)  |
| GetConsumption              | [`GetConsumptionRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetConsumptionRequest), [`GetConsumptionResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetConsumptionResponse)  |
| GetCurrentBill              | [`GetCurrentBillRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentBillRequest), [`GetCurrentBillResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentBillResponse)  |
| GetCurrtentSittingState     | [`GetCurrentSittingStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentSittingStateRequest), [`GetCurrentSittingStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentSittingStateResponse) |
| GetCurrentTemperature       | [`GetCurrentTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentTemperatureRequest), [`GetCurrentTemperatureResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentTemperatureResponse) |
| GetDeviceState             | [`GetDeviceStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateRequest), [`GetDeviceStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateResponse)  |
| GetEstimateBill            | [`GetEstimateBillRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateBillRequest), [`GetEstimateBillResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateBillResponse)  |
| GetEstimateConsumption     | [`GetEstimateConsumptionRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateConsumptionRequest), [`GetEstimateConsumptionResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateConsumptionResponse)  |
| GetExpendableState         | [`GetExpendableStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetExpendableStateRequest), [`GetExpendableStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetExpendableStateResponse)  |
| GetFineDust                | [`GetFineDustRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetFineDustRequest), [`GetFineDustResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetFineDustResponse) |
| GetHumidity                | [`GetHumidityRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetHumidityRequest), [`GetHumidityResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetHumidityResponse) |
| GetKeepWarmTime            | [`GetKeepWarmTimeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetKeepWarmTimeRequest), [`GetKeepWarmTimeResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetKeepWarmTimeResponse) |
| GetLockState               | [`GetLockStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetLockStateRequest), [`GetLockStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetLockStateResponse) |
| GetOpenState                | [`GetOpenStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetOpenStateRequest), [`GetOpenStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetOpenStateResponse)  |
| GetOpenTime                | [`GetOpenTimeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetOpenTimeRequest), [`GetOpenTimeResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetOpenTimeResponse)  |
| GetPhase                   | [`GetPhaseRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetPhaseRequest), [`GetPhaseResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetPhaseResponse)  |
| GetProgressiveTaxBracket   | [`GetProgressiveTaxBracketRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetProgressiveTaxBracketRequest), [`GetProgressiveTaxBracketResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetProgressiveTaxBracketResponse) |
| GetRemainingTime           | [`GetRemainingTimeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetRemainingTimeRequest), [`GetRemainingTimeResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetRemainingTimeResponse)  |
| GetRightPostureRatio       | [`GetRightPostureRatioRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetRightPostureRatioRequest), [`GetRightPostureRatioResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetRightPostureRatioResponse)  |
| GetSleepScore              | [`GetSleepScoreRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetSleepScoreRequest), [`GetSleepScoreResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetSleepScoreResponse) |
| GetSleepStartTime          | [`GetSleepStartTimeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetSleepStartTimeRequest), [`GetSleepStartTimeResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetSleepStartTimeResponse) |
| GetTargetTemperature       | [`GetTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetTargetTemperatureRequest), [`GetTargetTemperatureResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetTargetTemperatureResponse) |
| GetUltraFineDust           | [`GetUltraFineDustRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetUltraFineDustRequest), [`GetUltraFineDustResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetUltraFineDustResponse) |
| GetUsageTime               | [`GetUsageTimeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetUsageTimeRequest), [`GetUsageTimeResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetUsageTimeResponse)  |
| HealthCheck                | [`HealthCheckRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#HealthCheckRequest), [`HealthCheckResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#HealthCheckResponse) |
| IncrementBrightness        | [`IncrementBrightnessConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementBrightnessConfirmation), [`IncrementBrightnessRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementBrightnessRequest)  |
| IncrementChannel           | [`IncrementChannelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementChannelConfirmation), [`IncrementChannelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementChannelRequest) |
| IncrementFanSpeed          | [`IncrementFanSpeedConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementFanSpeedConfirmation), [`IncrementFanSpeedRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementFanSpeedRequest) |
| IncrementIntensityLevel    | [`IncrementIntensityLevelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementIntensityLevelConfirmation), [`IncrementIntensityLevelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementIntensityLevelConfirmation)  |
| IncrementTargetTemperature | [`IncrementTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementTargetTemperatureConfirmation), [`IncrementTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementTargetTemperatureConfirmation) |
| IncrementVolume            | [`IncrementVolumeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementVolumeConfirmation), [`IncrementVolumeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementVolumeRequest) |
| Lower                      | [`LowerConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#LowerConfirmation), [`LowerRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#LowerRequest)  |
| Mute                       | [`MuteConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#MuteConfirmation), [`MuteRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#MuteRequest) |
| Open                       | [`OpenConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#OpenConfirmation), [`OpenRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#OpenRequest)  |
| Raise                      | [`RaiseConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#RaiseConfirmation), [`RaiseRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#RaiseRequest)  |
| ReleaseMode              | [`ReleaseModeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ReleaseModeConfirmation), [`ReleaseModeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ReleaseModeRequest)  |
| SetBrightness              | [`SetBrightnessConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetBrightnessConfirmation), [`SetBrightnessRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetBrightnessRequest)  |
| SetChannel                 | [`SetChannelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetChannelConfirmation), [`SetChannelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetChannelRequest) |
| SetChannelByName           | [`SetChannelByNameConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetChannelByNameConfirmation), [`SetChannelByNameRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetChannelByNameRequest) |
| SetColor                   | [`SetColorConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorConfirmation), [`SetColorRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorRequest)  |
| SetColorTemperature        | [`SetColorTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorTemperatureConfirmation), [`SetColorTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorTemperatureRequest)  |
| SetFanSpeed                | [`SetFanSpeedConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFanSpeedConfirmation), [`SetFanSpeedRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFanSpeedRequest)  |
| SetLockState               | [`SetLockStateConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetLockStateConfirmation), [`SetLockStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetLockStateRequest)  |
| SetMode                    | [`SetModeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeConfirmation), [`SetModeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeRequest) |
| SetTargetTemperature       | [`SetTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureConfirmation), [`SetTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureConfirmation)  |
| Stop                       | [`StopConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StopConfirmation), [`StopRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StopRequest)  |
| TurnOff                    | [`TurnOffConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#TurnOffConfirmation), [`TurnOffRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#TurnOffRequest) |
| TurnOn                     | [`TurnOnConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#TurnOnConfirmation), [`TurnOnRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#TurnOnRequest) |
| Unmute                     | [`UnmuteConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#UnmuteConfirmation), [`UnmuteRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#UnmuteRequest) |

<div class="note">
<p><strong>Note!</strong></p>
<p>You can automatically set the location of the IoT appliances of the user by using the `location` field for each appliance in the <a href="/CEK/References/ClovaHomeInterface/Discovery_Interfaces.html#DiscoverAppliancesResponse"><code>DiscoverAppliancesResponse</code></a> message when sending the list of user registered appliance to CEK.</p>
</div>

### Locations {#Locations}

The table below shows the location information supported by `location` field. This information is used for analyzing the user utterance or showing the location of the appliance to the user.

{% include "/CEK/References/ClovaHomeInterface/Location.md" %}

### Object Example
{% raw %}

```json
// Example 1: An example used in DiscoverAppliancesResponse message
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "discoveredAppliances": [
      {
        "applianceId": "device-001",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "Smart lamp",
        "version": "v1.0",
        "friendlyName": "Living room lamp",
        "friendlyDescription": "A lamp that can be controlled using a smartphone",
        "isIr": false,
        "isReachable": true,
          "actions": [
            "HealthCheck",
            "TurnOn",
            "TurnOff"
        ],
        "applianceTypes": ["LIGHT"],
        "additionalApplianceDetails": {},
        "location": "LIVING_ROOM"
      },
      {
        "applianceId": "device-002",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "Smart plug",
        "version": "v1.0",
        "friendlyName": "Kitchen plug",
        "friendlyDescription": "An energy-saving plug",
        "isIr": false,
        "isReachable": true,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {},
        "location": ""
      }
    ]
  }
}

// Example 2: An example used in the TurnOnRequest message
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
* [`DiscoverAppliancesResponse`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse)
* [`DiscoverAppliancesRequest`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesRequest)

## BatteryInfoObject {#BatteryInfoObject}
BatteryInfoObject contains information on the appliance battery. This is used to indicate battery information and expressed as an integer (0-100) that represents a percentage.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------:|
| `value`       | number  | Remaining battery (%)                 | Required     |

### Object Example
{% raw %}

```json
// Example: An example used in the GetBatteryInfoResponse message
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "GetBatteryInfoResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "batteryInfo": {
      "value": 40
    }
  }
}
```

{% endraw %}

### See also
* [`GetBatteryInfoResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetBatteryInfoResponse)

## BillInfoObject {#BillInfoObject}
BillInfoObject contains the information on billing derived from the amount of energy consumption measured by the appliance. The billing information is displayed in two components: amount and currency unit.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `currency`    | string  | Currency unit (<a href="https://en.wikipedia.org/wiki/ISO_4217" target="_blank">ISO 4217</a>)  | Required |
| `value`       | number  | Amount of bill                    | Required   |

### Object Example
{% raw %}

```json
// Example: An example used in the GetCurrentBillResponse message
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetCurrentBillResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "currentBill": {
        "value": 29900,
        "currency": "KRW"
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetCurrentBillRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentBillRequest)
* [`GetCurrentBillResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentBillResponse)
* [`GetEstimateBillRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateBillRequest)
* [`GetEstimateBillResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateBillResponse)

## BrightnessInfoObject {#BrightnessInfoObject}
BrightnessInfoObject contains information on light or screen brightness. This is used to indicate the light or screen brightness to change, or the brightness before and after the change. It is expressed as an integer (0-100) that represents a percentage.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Brightness (%)                      | Required/Always     |

### Object Example
{% raw %}

```json
// Example 1: An example used in the IncrementBrightnessRequest message
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
      "value": 40
    }
  }
}

// Example 2: An example used in the IncrementBrightnessConfirmation message
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "DecrementBrightnessConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetBrightness": {
      "value": 40
    },
    "previousState": {
      "targetBrightness": {
        "value": 20
      }
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementBrightnessConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementBrightnessConfirmation)
* [`DecrementBrightnessRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementBrightnessRequest)
* [`IncrementBrightnessConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementBrightnessConfirmation)
* [`IncrementBrightnessRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementBrightnessRequest)
* [`SetBrightnessConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetBrightnessConfirmation)
* [`SetBrightnessRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetBrightnessRequest)

## ColorInfoObject {#ColorInfoObject}
ColorInfoObject contains information on the color of lights, the screen, or lamps of the target appliance. This is used to indicate the light or screen color to change, or the color before and after the change. The color information is expressed in the (<a href="https://en.wikipedia.org/wiki/HSL_and_HSV" target="_blank">HSV</a>) model.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `brightness`  | number  | Value (0-100). This field is omissible if [BrightnessInfoObject](#BrightnessInfoObject) is used on the brightness settings of a specific appliance.  | Optional/Conditional |
| `hue`         | number  | Hue (0-360)                  | Required/Always |
| `saturation`  | number  | Saturation (0-100)                  | Required/Always |

### Object Example
{% raw %}

```json
// Example 1: An example used in the SetColorRequest message
{
  "header": {
    "messageId": "a97dff79-5684-4535-8df3-193713c478aa",
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

// Example 2: An example used in the SetColorConfirmation message
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
* [`SetColorConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorConfirmation)
* [`SetColorRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorRequest)

## ColorTemperatureInfoObject {#ColorTemperatureInfoObject}
ColorTemperatureInfoObject contains information on the color temperature of lights, the screen, or lamps of the target appliance. This is used to indicate the light or screen color temperature to change, or the color temperature before and after the change. It is expressed using the Kelvin (K) scale.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Color temperature (K, Kelvin)             | Required/Always     |

### Object Example
{% raw %}

```json
// Example 1: An example used in the SetColorTemperatureRequest message
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

// Example 2: An example used in the SetColorTemperatureConfirmation message
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
* [`SetColorTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorTemperatureConfirmation)
* [`SetColorTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorTemperatureRequest)

## ConsumptionInfoObject {#ConsumptionInfoObject}
ConsumptionInfoObject contains information on energy or resource measured by the appliance. The consumption information is displayed in two components: energy consumption amount and unit.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `name`        | string  | The name of item consuming energy or resource.                   | Required  |
| `unit`        | string  | Energy or resource consumption unit (e.g., kW for electricity).        | Required  |
| `value`       | number  | Energy or resource consumption amount.                    | Required   |

### Object Example
{% raw %}

```json
// Example: An example used in GetConsumptionResponse message
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
        "name": "Electricity consumption",
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
* [`GetConsumptionResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetConsumptionResponse)

## CustomCommandInfoObject {#CustomCommandInfoObject}

CustomCommandInfoObject contains information on custom commands. The object contains information on the command that the user registered via the Clova app. The commands registered to the user account are returned with the appliance information retrieval results of the [`DiscoverAppliancesResponse`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse) message. This object includes the control actions of an appliance that is performed when custom command is invoked.

### Object fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `name`        | string  | The name of the custom command.             | Required      |
| `actions[]`   | [ActionInfoObject](#ActionInfoObject) array | The list of appliance control actions to perform through the custom command.  | Required  |

### Object Example
{% raw %}

```json
// Example: An example used in DiscoverAppliancesResponse message
{
  "header": {
    "messageId": "99f9d8ff-9366-4cab-a90c-b4c7eca0abbe",
    "name": "DiscoverAppliancesResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "customCommands": [
      {
        "name": "Good morning",
        "actions": [
          {
            "applianceId": "device-001",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-0012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-0013",
            "action": "TurnOn"
          }
        ]
      },
      {
        "name": "Good evening",
        "actions": [
          {
            "applianceId": "device-0011",
            "action": "TurnOn"
          },
          {
            "applianceId": "device-0012",
            "action": "TurnOff"
          },
          {
            "applianceId": "device-0013",
            "action": "TurnOn"
          }
        ]
      }
    ],
    "discoveredAppliances": [
      {
        "applianceId": "device-001",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "Smart lamp",
        "version": "v1.0",
        "friendlyName": "Living room lamp",
        "friendlyDescription": "A lamp that can be controlled using a smartphone",
        "isIr": false,
        "isReachable": true,
          "actions": [
            "DecrementBrightness",
            "HealthCheck",
            "IncrementBrightness",
            "SetBrightness",
            "TurnOn",
            "TurnOff"
        ],
        "applianceTypes": ["LIGHT"],
        "additionalApplianceDetails": {}
      },
      {
        "applianceId": "device-002",
        "manufacturerName": "device-manufacturer-name",
        "modelName": "Smart plug",
        "version": "v1.0",
        "friendlyName": "Kitchen plug",
        "friendlyDescription": "An energy-saving plug",
        "isIr": false,
        "isReachable": true,
        "actions": [
          "HealthCheck",
          "TurnOn",
          "TurnOff"
        ],
        "applianceTypes": ["SMARTPLUG"],
        "additionalApplianceDetails": {},
        "location": "LIVING_ROOM",
        "tags": ["Study", "Johnroom", "Poweroffdeviceforawaymode"]
      }
    ]
  }
}
```

{% endraw %}

### See also
* [ActionInfoObject](#ActionInfoObject)
* [`DiscoverAppliancesResponse`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesResponse)

## CustomInfoObject {#CustomInfoObject}

CustomInfoObject contains information directly entered by the user such as customized name, required unit, or values. This object is used when the [shared objects](#SharedObjects) provided by default cannot express the object information or when providing all information of the appliance using the [`GetDeviceStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateResponse) message.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `name`        | string            | The customized name to indicate an appliance state or measurement target. When responding to the user, the state name entered in this field is output as speech. | Required |
| `value`       | number or string | The state value or measurement value.                                                                             | Required |
| `unit`        | string            | The value of the appliance state or the unit information of the measurement. This is omitted if the data type of the `value` field is a string and may have the following units if it is a numeric value.<ul><li><code>"celcius"</code>: Celsius</li><li><code>"percentage"</code>: Percentage</li></ul> | Optional |

### Object Example
{% raw %}

```json
// Example: An example used in GetDeviceStateResponse message
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetDeviceStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "states": [
      {
        "name": "Temperature of the freezer",
        "value": -11,
        "unit": "celsius"
      },
      {
        "name": "Temperature of the fridge",
        "value": 2,
        "unit": "celsius"
      },
      {
        "name": "Humidity of fridge",
        "value": 10,
        "unit": "percentage"
      },
    ],
    "applianceResponseTimestamp": "2017-11-23T20:31:18+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetDeviceStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateResponse)

## EndpointInfoObject {#EndpointInfoObject}
EndpointInfoObject contains information on the endpoint, which the target appliance must ultimately control. A user can specify the endpoint for the target appliance to apply a specific setting value or temperature. An endpoint refers to a specific part of an appliance, the operation method, or area of application. For example, when a user controls the temperature of the refrigerator, the user can additionally specify whether to change the temperature of the freezer or the fridge. {{ "Also, when the user controls an air conditioner with a heating function, the user can separately specify the temperature of the cooling mode and the temperature of the heating mode for further control." if book.L10N.TargetCountryCode == "JP" }}

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | The endpoint. For more information, see [Endpoint references](#EndpointReferences).    | Required/Always |

### Endpoint references {#EndpointReferences}

| Endpoint code.   | Description                                   |
|----------------|---------------------------------------|
| coldwater      | The cold water temperature of a water purifier or thermostat.              |
| freezer        | The freezer compartment of a refrigerator.                           |
| fridge         | The fridge compartment of a refrigerator.                           |
| hotwater       | The hot water temperature of a water purifier or thermostat.              |

<div class="note">
  <p><strong>Note!</strong></p>
  <p>Additions to the endpoint list may be made.</p>
</div>


### Object Example
{% raw %}

```json
// Example 1: An example used in the SetTargetTemperatureRequest message
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

// Example 2: An example used in the SetTargetTemperatureConfirmation message
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

{% endraw %}

### See also
* [`SetTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureConfirmation)
* [`SetTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureRequest)

## ExpendableInfoObject {#ExpendableInfoObject}
ExpendableInfoObject contains information on usage or remaining lifespan of device parts. This is used to indicate the usage amount of the appliance parts or their remaining lifespans.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `name`          | string  | The name of the part.                  | Required |
| `remainingTime` | string   | The remaining lifespan of the part (Duration, <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601</a>).    | Optional |
| `usage`         | [CustomInfoObject](#CustomInfoObject)          | The usage amount of the part (can be expressed as the number of uses or percentage of usage).      | Optional |

### Object Example
{% raw %}

```json
// Example: An example used in the GetExpendableStateResponse message
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetExpendableStateResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "expendableInfo": [
      {
        "name": "Packing",
        "remainingTime": "P0001-04-10"
      },
      {
        "name": "Filter 1",
        "usage": {
          "value": 80,
          "unit": "percentage"
        }
      }
    ],
    "applianceResponseTimestamp": "2017-11-23T20:31:18+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetExpendableStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetExpendableStateResponse)

## FineDustInfoObject {#FineDustInfoObject}
FineDustInfoObject contains information on fine dust. This is used to indicate the fine dust index or level measured by the appliance. It is expressed as a number.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Fine dust index.                  | Optional    |
| `index`       | string  | Fine dust level. It is limited to the following values.<ul><li><code>"good"</code>: Good</li><li><code>"normal"</code>: Normal</li><li><code>"bad"</code>: Bad</li><li><code>"verybad"</code>: Very bad</li></ul> | Required     |

### Object Example
{% raw %}

```json
// Example: An example used in the GetFineDustResponse message
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
    }
  }
}
```

{% endraw %}

### See also
* [`GetFineDustResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetFineDustResponse)

## IntensityLevelInfoObject {#IntensityLevelInfoObject}
IntensityLevelInfoObject contains information on pressure or water pressure intensity. This is displayed according to the pressure or water pressure intensities in each appliance.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Intensity of pressure or water pressure.            | Optional/Conditional    |

### Object Example
{% raw %}

```json
// Example 1: An example used in the IncrementIntensityLevelRequest message
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
    "deltaIntensity": {
      "value": 1
    }
  }
}

// Example 2: An example used in the IncrementIntensityLevelConfirmation message
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

* [`DecrementIntensityLevelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementIntensityLevelConfirmation)
* [`DecrementIntensityLevelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementIntensityLevelRequest)
* [`IncrementIntensityLevelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementIntensityLevelConfirmation)
* [`IncrementIntensityLevelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementIntensityLevelRequest)

## ModeInfoObject {#ModeInfoObject}
ModeInfoObject contains information on the operation mode. This is used to indicate the name of the operation mode to change or the operation mode before and after the change. It is expressed as a string.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | [Operation mode](#OperationModes)    | Required/Always     |

### Operation modes {#OperationModes}

<table>
  <thead>
    <tr>
      <th style="width:20%">Appliance type</th><th style="width:80%">Operation mode list and description</th>
    </tr>
  </thead>
  <tdoby>
    <tr>
      <td><code>"AIRCONDITIONER"</code></td>
      <td>
        <ul>
          <li><code>"auto"</code>: Auto mode. A mode mainly used in air conditioners.</li>
          <li><code>"cool"</code>: Cooling mode. A mode mainly used in air conditioners.</li>
          <li><code>"dehumidify"</code>: Dehumidifier mode. A mode mainly used in appliances such as air conditioners or dehumidifiers.</li>
          {% if book.L10N.TargetCountryCode == "JP" %}
          <li><code>"heat"</code>: Heating mode. A mode mainly used in air conditioners.</li>
          {% endif %}
          <li><code>"sleep"</code>: Sleep mode. A mode mainly used in appliances such as smart hubs.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"AIRPURIFIER"</code></td>
      <td>
        <ul>
          <li><code>"auto"</code>: Auto mode.</li>
          <li><code>"autohumidify"</code>: Auto humidify mode.</li>
          <li><code>"infant"</code>: Infant mode.</li>
          <li><code>"roomcare"</code>: Room care mode.</li>
          <li><code>"yellowsand"</code>: Yellow sand mode.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"FAN"</code></td>
      <td>
        <ul>
          <li><code>"auto"</code>: Auto mode.</li>
          <li><code>"baby"</code>: Baby mode.</li>
          <li><code>"sleep"</code>: Sleep mode.</li>
      </td>
    </tr>
    <tr>
      <td><code>"HUMIDIFIER"</code></td>
      <td>
        <ul>
          <li><code>"light"</code>: Light mode.</li>
      </td>
    </tr>
    <tr>
      <td><code>"LIGHT"</code></td>
      <td>
        <ul>
          <li><code>"concentration"</code>: Concentrating mode.</li>
          <li><code>"reading"</code>: Reading mode.</li>
          <li><code>"rest"</code>: Resting mode.</li>
          <li><code>"sleep"</code>: Sleep mode.</li>
          <li><code>"vitality"</code>: Vitality mode.</li>
          <li><code>"wakeup"</code>: Wake up mode.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"PURIFIER"</code></td>
      <td>
        <ul>
          <li><code>"coldwater"</code>: Cold water mode.</li>
          <li><code>"general"</code>: General mode.</li>
          <li><code>"hotwater"</code>: Hot water mode.</li>
          <li><code>"smartchecking"</code>: Smart inspection mode.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"REFRIGERATOR"</code></td>
      <td>
        <ul>
          <li><code>"filter"</code>: Filter mode.</li>
          <li><code>"freeze"</code>: Express freeze mode.</li>
          <li><code>"powersaving"</code>: Power saving mode.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"RICECOOKER"</code></td>
      <td>
        <ul>
          <li><code>"general"</code>: General mode.</li>
          <li><code>"keepwarm"</code>: Warm mode.</li>
          <li><code>"powersaving"</code>: Power saving mode.</li>
          <li><code>"reheating"</code>: Reheating mode.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"SMARTHUB"</code></td>
      <td>
        <ul>
          <li><code>"away"</code>: Away mode.</li>
          <li><code>"hotwater"</code>: Hot water mode.</li>
          <li><code>"indoor"</code>: Indoor mode.</li>
          <li><code>"sleep"</code>: Sleep mode.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"THERMOSTAT"</code></td>
      <td>
        <ul>
          <li><code>"away"</code>: Away mode.</li>
          <li><code>"hotwater"</code>: Hot water mode.</li>
          <li><code>"indoor"</code>: Indoor mode.</li>
          <li><code>"sleep"</code>: Sleep mode.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"VENTILATOR"</code></td>
      <td>
        <ul>
          <li><code>"auto"</code>: Auto mode.</li>
          <li><code>"dehumidify"</code>: Dehumidify mode.</li>
          <li><code>"dry"</code>: Dry mode.</li>
          <li><code>"ventilating"</code>: Ventilating mode.</li>
          <li><code>"warmwind"</code>: Warm wind mode.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"WATERBOILER"</code></td>
      <td>
        <ul>
          <li><code>"hotwater"</code>: Hot water supply mode.</li>
          <li><code>"reheating"</code>: Reheating mode.</li>
        </ul>
      </td>
    </tr>
  </tdoby>
</table>

<div class="note">
<p><strong>Note!</strong></p>
<p>The modes mentioned above may not exist or have a different supporting method, depending on the manufacturer or the product itself. In this case, we recommend that you provide the features or operation modes that are similar to the ones of the product.</p>
</div>

### Object Example
{% raw %}

```json
// Example 1: An example used in the SetModeRequest message for a thermostat
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

// Example 2: An example used in the SetModeRequest message - smart hub
{
  "header": {
    "messageId": "b4151a0d-1ec5-4ed0-a39a-1538c356b93b",
    "name": "SetModeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-011"
    },
    "mode": {
        "value": "indoor"
    }
  }
}

// Example 3: An example used in the SetModeConfirmation message
{
  "header": {
    "messageId": "b7434bd2-c397-461d-b08d-a4a427455c8f",
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
* [`ReleaseModeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ReleaseModeConfirmation)
* [`ReleaseModeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ReleaseModeRequest)
* [`SetModeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeConfirmation)
* [`SetModeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeRequest)

## HumidityInfoObject {#HumidityInfoObject}
HumidityInfoObject contains information on humidity. This is used to indicate the humidity condition measured by the appliance. It is expressed as a string.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Humidity (%)                      | Required     |

### Object Example
{% raw %}

```json
// Example: An example used in the GetHumidityResponse message
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetHumidityResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "fineDust": {
        "value": 40
    }
  }
}
```

{% endraw %}

### See also
* [`GetHumidityResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetHumidityResponse)

## PeriodInfoObject {#PeriodInfoObject}

PeriodInfoObject contains information for periods used to retrieve measured data such as amount of consumption or estimated bills. Upon user request for cumulative statistics or change in trend for a specific period, the information is sent through the field that is in the same name as `period`. The extension must send the result by collecting and calculating information for the period specified by the user.

### Object fields

| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:-------------:|
| `end`         | string  | The end time of the period (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>).    | Always      |
| `start`       | string  | The start time of the period (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>).    | Always      |

### Remarks
Expressions such as "today," "this week," or "this month" used by the user are defined by the following range of time:

* "Today": The time range begins at 00:00:00 of the current date and ends at 23:59:59 of the current date.
* "This week": The time range begins at 00:00:00 of the {{ book.ServiceEnv.FirstDayOfWeekInClovaHome }} of the current week and ends at 23:59:59 of the {{ book.ServiceEnv.LastDayOfWeekInClovaHome }} of the current week.
* "This month": The time range begins at 00:00:00 of the first day of the current month and ends at 23:59:59 of the last day of the current month.

At the time of processing a request, the end time (`end`) of the period used in special expressions like above can be a time in the future that is yet to come. Depending on the situation, data must be handled by considering the handling time as the end time.

Both the start time (`start`) and end time (`end`) can be a time in the future like "tomorrow," "next week," or "next month" and such expressions may be used when the user requests for predictive information.

* "Tomorrow": The time range begins at 00:00:00 of the day after the current date and ends at 23:59:59 of the day after the current date.
* "Next week": The time range begins at 00:00:00 of the {{ book.ServiceEnv.FirstDayOfWeekInClovaHome }} of the week after the current week and ends at 23:59:59 of the {{ book.ServiceEnv.LastDayOfWeekInClovaHome }} of the week after the current week.
* "Next month": The time range begins at 00:00:00 of the first day of the month after the current month and ends at 23:59:59 of the last day of the month after the current month.

### Object Example
{% raw %}

```json
// Example 1: An example used in the GetUsageTimeRequest message
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
      "start": "2018-03-28T00:10:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

{% endraw %}

### See also
* [`GetAsleepDurationRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAsleepDurationRequest)
* [`GetAwakeDurationRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetAwakeDurationRequest)
* [`GetCurrentSittingStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentSittingStateResponse)
* [`GetDeviceStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateRequest)
* [`GetRightPostureRatioRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetRightPostureRatioRequest)
* [`GetSleepScoreRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetSleepScoreRequest)
* [`GetSleepStartTimeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetSleepStartTimeRequest)
* [`GetUsageTimeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetUsageTimeRequest)

## PhaseInfoObject {#PhaseInfoObject}

PhaseInfoObject contains information on the phase of device actions. This is used to indicate the current phase of the action or the previous phase of the action.

### Object fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | The string to express the phase of action.        | Required      |

### Object Example
{% raw %}

```json
// Example: An example used in the GetPhaseResponse message
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetPhaseResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "phase": {
        "value": "Spin-dry",
    },
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

{% endraw %}

### See also
* [`GetPhaseResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetPhaseResponse)
* [`StopConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StopConfirmation)

## ProgressiveTaxBracketInfoObject {#ProgressiveTaxBracketInfoObject}
ProgressiveTaxBracketInfoObject contains information on progressive tax brackets.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Progressive tax bracket                    | Required     |

### Object Example
{% raw %}

```json
// Example: An example used in the GetProgressiveTaxBracketResponse message
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
* [`GetProgressiveTaxBracketResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetProgressiveTaxBracketResponse)

## RatioInfoObject {#RatioInfoObject}

RatioInfoObject contains information on the ratio.

### Object fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | The ratio value. The unit is a percentage (%).   | Required      |

### Object Example
{% raw %}

```json
// Example: An example used in the GetRightPostureRatioResponse message
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
* [`GetRightPostureRatioResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetRightPostureRatioResponse)

## SittingStateInfoObject {#SittingStateInfoObject}
SittingStateInfoObject contains the sit-down information of the user on appliances such as a smart chair.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | boolean | Sit-down state<ul><li><code>true</code>: A state of sitting down</li><li><code>false</code>: A state of not sitting down</li></ul>       | Required    |

### Object Example
{% raw %}

```json
// Example: An example used in the GetCurrentSittingStateResponse message
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
* [`GetCurrentSittingStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentSittingStateResponse)

## SleepScoreInfoObject {#SleepScoreInfoObject}
SleepScoreInfoObject contains information on sleep score. When showing results over a period, this object holds the average value.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | The sleep score.                     | Required     |

### Object Example
{% raw %}

```json
// Example: An example used in the GetSleepScoreResponse message
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
* [`GetSleepScoreResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetSleepScoreResponse)

## SpeedInfoObject {#SpeedInfoObject}
SpeedInfoObject contains information on speed. This is used to indicate the speed to change or the desired speed before and after the change. It is expressed as an integer.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Speed value                       | Required/Always     |

### Object Example
{% raw %}

```json
// Example 1: An example used in the IncrementFanSpeedRequest message
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

// Example 2: An example used in the IncrementFanSpeedConfirmation message
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "IncrementFanSpeedConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "targetFanSpeed": {
      "value": 3
    },
    "previousState": {
      "targetFanSpeed": {
        "value": 2
      }
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementFanSpeedConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementFanSpeedConfirmation)
* [`DecrementFanSpeedRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementFanSpeedRequest)
* [`IncrementFanSpeedConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementFanSpeedConfirmation)
* [`IncrementFanSpeedRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementFanSpeedRequest)
* [`SetFanSpeedConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFanSpeedConfirmation)
* [`SetFanSpeedRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFanSpeedRequest)

## TemperatureInfoObject {#TemperatureInfoObject}
TemperatureInfoObject contains information on temperature. This is used to indicate the amount of temperature to change, the temperature before and after the change, or the currently set desired temperature. It is expressed up to one decimal place.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Temperature value                       | Required/Always     |

### Object Example
{% raw %}

```json
// Example 1: An example used in the IncrementTargetTemperatureRequest message
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
      "value": 1
    }
  }
}

// Example 2: An example used in the IncrementTargetTemperatureConfirmation message
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
        "value": 21
      }
    }
  }
}
```

{% endraw %}

### See also
* [`DecrementTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementTargetTemperatureConfirmation)
* [`DecrementTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementTargetTemperatureRequest)
* [`GetCurrentTemperatureResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentTemperatureResponse)
* [`GetTargetTemperatureResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetTargetTemperatureResponse)
* [`IncrementTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementTargetTemperatureConfirmation)
* [`IncrementTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementTargetTemperatureRequest)
* [`SetTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureConfirmation)
* [`SetTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureRequest)

## TVChannelNameInfoObject {#TVChannelNameInfoObject}
TVChannelNameInfoObject contains information on a TV channel name. This is used to indicate the name of TV channel to change or the TV channel before and after the change. It is expressed as a string.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | Name of a TV channel                  | Required/Always     |

### Object Example
{% raw %}

```json
// Example 1: An example used in the SetChannelByNameRequest message
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

// Example 2: An example used in the SetChannelByNameConfirmation message
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
* [`SetChannelByNameConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetChannelByNameConfirmation)
* [`SetChannelByNameRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetChannelByNameRequest)

## TVChannelInfoObject {#TVChannelInfoObject}
TVChannelInfoObject contains information on a TV channel number. This is used to indicate the channel number of TV channel to change or the TV channel before and after the change. It is expressed as a number.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`             | number  | TV channel number                      | Required/Always     |

### Object Example
{% raw %}

```json
// Example 1: An example used in the SetChannelRequest message
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "SetChannelRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-007"
    },
    "channel": {
      "value": 15
    },
    "subChannel": {
      "value": 1
    }
  }
}

// Example 2: An example used in the SetChannelConfirmation message
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "SetChannelConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
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
* [`DecrementChannelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementChannelConfirmation)
* [`DecrementChannelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementChannelRequest)
* [`IncrementChannelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementChannelConfirmation)
* [`IncrementChannelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementChannelRequest)
* [`SetChannelConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetChannelConfirmation)
* [`SetChannelRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetChannelRequest)

## UltraFineDustInfoObject {#UltraFineDustInfoObject}
UltraFineDustInfoObject contains information on ultrafine dust. This is used to indicate the ultrafine dust index or the level measured by the appliance. It is expressed as a number.

### Object fields
| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Ultrafine dust index.                | Optional    |
| `index`       | number  | Ultrafine dust level. It is limited to the following values.<ul><li><code>"good"</code>: Good</li><li><code>"normal"</code>: Normal</li><li><code>"bad"</code>: Bad</li><li><code>"verybad"</code>: Very bad</li></ul> | Required     |

### Object Example
{% raw %}

```json
// Example: An example used in the GetUltraFineDustResponse message
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
    }
  }
}
```

{% endraw %}

### See also
* [`GetUltraFineDustResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetUltraFineDustResponse)

## VolumeInfoObject {#VolumeInfoObject}
VolumeInfoObject contains information on the speaker volume. This is used to indicate the new volume to change or the volume before and after the change. It is expressed as an integer.

### Object fields
| Field name       | Data type    | Description                     | Required/Included |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Value of the volume                       | Required/Always     |

### Object Example
{% raw %}

```json
// Example 1: An example used in the IncrementVolumeRequest message
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

// Example 2: An example used in the IncrementVolumeConfirmation message
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
* [`DecrementVolumeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementVolumeConfirmation)
* [`DecrementVolumeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DecrementVolumeRequest)
* [`IncrementVolumeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementVolumeConfirmation)
* [`IncrementVolumeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementVolumeRequest)