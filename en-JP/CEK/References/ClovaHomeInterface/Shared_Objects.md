# Shared objects {#SharedObjects}
These shared objects are used in the message `payload` when sending [Clova Home Extension messages](/CEK/References/CEK_API.md#ClovaHomeExtMessage):

| Object            | Description                                            |
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
| [CountInfoObject](#CountInfoObject)                       | Object containing information on the number of counts.           |
| [CustomCommandInfoObject](#CustomCommandInfoObject)       | Object containing information on custom commands.   |
| [CustomInfoObject](#CustomInfoObject)                     | Object containing information directly entered by the user such as an customized name, required units, or figures. |
| [ExpendableInfoObject](#ExpendableInfoObject)             | Object containing information on usage or remaining lifespan of appliance parts.  |
| [FineDustInfoObject](#FineDustInfoObject)                 | Object containing information on fine dust.          |
| [IntensityLevelInfoObject](#IntensityLevelInfoObject)     | Object containing information on pressure or water pressure intensity.   |
| [ModeInfoObject](#ModeInfoObject)                         | Object containing information on the operation mode.          |
| [HumidityInfoObject](#HumidityInfoObject)                 | Object containing information on humidity.              |
| [PeriodInfoObject](#PeriodInfoObject)                     | Object containing information on the period.          |
| [PhaseInfoObject](#PhaseInfoObject)                       | Object containing information on the phase of appliance actions.
| [ProgressiveTaxBracketInfoObject](#ProgressiveTaxBracketInfoObject)  | Object containing information on progressive tax brackets.       |
| [SittingStateInfoObject](#SittingStateInfoObject)         | Object containing the sit-down information of the user on appliances such as a smart chair.  |
| [SleepScoreInfoObject](#SleepScoreInfoObject)             | Object containing information on sleep score.          |
| [SpeedInfoObject](#SpeedInfoObject)                       | Object containing information on speed.              |
| [TemperatureInfoObject](#TemperatureInfoObject)           | Object containing information on temperature.          |
| [TVChannelNameInfoObject](#TVChannelNameInfoObject)       | Object containing information on a TV channel name.      |
| [TVChannelInfoObject](#TVChannelInfoObject)               | Object containing information on a TV channel.           |
| [TVInputSourceNameInfoObject](#TVInputSourceNameInfoObject) | Object containing information on the TV input source.           |
| [UltraFineDustInfoObject](#UltraFineDustInfoObject)       | Object containing information on ultrafine dust.         |
| [VolumeInfoObject](#VolumeInfoObject)                     | Object containing information on volume.          |

## ActionInfoObject {#ActionInfoObject}
ActionInfoObject contains information on appliance control actions and expresses a command for an action to be performed on an appliance.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `applianceId` | String  | Appliance ID.                      | Required/Always     |
| `action`      | String  | For more information on the list of control actions on an appliance, see the [Actions](#Actions) table under the [ApplianceInfoObject](#ApplianceInfoObject) section.     | Required/Always     |

### Object example
{% raw %}

```json
// Example: An example used in the DiscoverAppliancesResponse message
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
        "name": "Good night",
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
AirQualityInfoObject contains information on air quality. It indicates the air quality status measured by the appliance and is represented as a string.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `index`       | string  | Air quality level. Available values are:<ul><li><code>"good"</code> : Good</li><li><code>"normal"</code>: Normal</li><li><code>"bad"</code>: Bad</li><li><code>"verybad"</code>: Very bad</li></ul> | Required/Always     |

### Object example
{% raw %}

```json
// Sample: A sample used for GetAirQualityResponse message
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
ApplianceInfoObject contains the information on IoT appliances. This object is used to send a list of appliances registered in the user account to CEK or to request the Clova Home Extension to control a specific appliance.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `actions[]`                  | string array  | List of actions supported by an appliance. The client must restrict the user controlling the IoT device within the scope of actions supported by the appliance. | Optional/Always    |
| `actionsNeededUserConfirmation[]`  | string array  | A list of actions for which an action check with the user is required. `TurnOn`, `TurnOff`, `SetMode` and `ReleaseMode` can be selected for this `actions` field. Before making a request for the operation specified here, a question such as "Are you sure you want to turn on the air conditioner?" is asked to the user to confirm the operation. | Optional/Conditional    |
| `additionalApplianceDetails` | object        | A field that holds additional information provided by the manufacture or the IoT service provider                                 | Optional/Conditional    |
| `applianceId`                | string        | Appliance ID.                                                                        | Required/Always    |
| `applianceTypes[]`           | string array  | The type of appliance. By `applicationType`, the value of the `actions` field that indicates operations supported by the appliance may vary. You must designate the type of an appliance registered to the user account of the IoT service. Input a type of the appliance by referring to the Remarks.                                                                              | Required/Always    |
| `friendlyName`               | string        | The name of the appliance given by the user.                                                           | Optional/Always    |
| `friendlyDescription`        | string        | The appliance description.                                                                  | Optional/Always    |
| `isIr`                       | boolean       | Whether or not the appliance is controlled by infrared communication<ul><li>true: Controlled by infrared communication</li><li>false: Not controlled by infrared communication</li></ul><div class="note"><p><strong>Note!</strong></p><p>For appliances that are controlled with infrared communication, Clova will not notify the user of the result of controlling the appliance.</p></div>  | Optional/Conditional  |
| `isReachable`                | boolean       | Whether or not the appliance can be controlled remotely<ul><li>true: Remote control is possible</li><li>false: Remote control is not possible</li></ul>  | Optional/Always    |
| `manufacturerName`           | string        | The name of the appliance manufacturer.                                                                  | Optional/Always    |
| `modelName`                  | string        | The name of the appliance model.                                                                   | Optional/Always    |
| `version`                    | string        | The software version of the manufacturer.                                                            | Optional/Always    |
| `location`                   | string        | The location of the appliance. Enter the code value in the [Locations](#Locations) field. The text that corresponds to the inputted code is added to the `tags` field.            | Optional/Always    |
| `tags[]`                       | string array  | The list of tags added to the appliance by the user. The user can add various attributes as tags such as location of installation, purpose of use, or product brand to the appliance from the Clova app or the IoT service. Appliances with the same attributes (tags) are grouped together. Simultaneous control is possible if the appliances in the same group have identical permitted actions.  | Optional/Always  |

### Remarks
If the user requests the appliance list using the [`DiscoverAppliancesRequest`](/CEK/References/ClovaHomeInterface/Discovery_Interfaces.md#DiscoverAppliancesRequest) message, the Clova Home Extension must fill out all the fields except the `additionalApplianceDetails` field, and deliver the information. Here, the value of the `actions` field is normally determined by the `applianceTypes` field and may have the following values depending on the value of the `applianceTypes` field:

| applianceTypes | Description| Permitted actions                                  |
|----------------|-------------|-------------------------------------------------|
| `"AIRCONDITIONER"`  | Type of an air conditioner         | DecrementFanSpeed, DecrementTargetTemperature, GetCurrentTemperature, GetDeviceState, GetTargetTemperature, HealthCheck, IncrementFanSpeed, IncrementTargetTemperature, ReleaseMode, SetFanSpeed, SetMode, SetTargetTemperature, TurnOff, TurnOn          |
| `"AIRPURIFIER"`     | Type of an air purifier        | DecrementFanSpeed, GetAirQuality, GetDeviceState, GetHumidity, HealthCheck, IncrementFanSpeed, ReleaseMode, SetFanSpeed, SetMode, TurnOff, TurnOn       |
| `"AIRSENSOR"`       | Type of an air sensor     | GetAirQuality, GetCurrentTemperature, GetFineDust, GetHumidity, GetUltraFineDust, HealthCheck                                     |
| `"BIDET"`           | Type of a bidet            | Close, GetDeviceState, GetExpendableState, HealthCheck, Open, TurnOff, TurnOn                                                         |
| `"BODYWEIGHTSCALE"` | Type of a weighing scale          | GetDeviceState, HealthCheck                                                                                                             |
| `"CLOTHESCAREMACHINE"` | Type of a clothing care machine    | GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                                     |
| `"CLOTHESDRYER"`    | Type of a drying machine       | GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                                           |
| `"CLOTHESWASHER"`   | Type of a washing machine       | GetDeviceState, GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                           |
| `"DEHUMIDIFIER"`    | Type of a dehumidifier           |  GetCurrentTemperature, GetDeviceState, GetHumidity, HealthCheck, SetFanSpeed, TurnOff, TurnOn                                                     |
| `"DISHWASHER"`      | Type of a dishwasher       | GetPhase, GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                           |
| `"ELECTRICKETTLE"`  | Type of a an electric kettle       | GetCurrentTemperature, HealthCheck, TurnOff, TurnOn                                                                              |
| `"ELECTRICTOOTHBRUSH"` | Type of am electric toothbrush     | GetDeviceState, HealthCheck                                                                                                            |
| `"FAN"`             | Type of a fan           | DecrementFanSpeed, HealthCheck, IncrementFanSpeed, ReleaseMode, SetFanSpeed, SetMode, TurnOff, TurnOn          |
| `"HEATER"`          | Type of a heater            | DecrementTargetTemperature, GetCurrentTemperature, GetDeviceState, GetTargetTemperature, HealthCheck, IncrementTargetTemperature, SetTargetTemperature, TurnOff, TurnOn                      |
| `"HUMIDIFIER"`      | Type of a humidifier           | GetCurrentTemperature, GetDeviceState, GetHumidity, HealthCheck, SetFanSpeed, TurnOff, TurnOn                                                     |
| `"LIGHT"`           | Type of a smart lighting   | DecrementBrightness, DecrementVolume HealthCheck, IncrementBrightness, IncrementVolume SetBrightness, SetColor, SetColorTemperature, SetMode, TurnOff, TurnOn            |
| `"MASSAGECHAIR"`    | Type of a massage chair        | DecrementIntensityLevel, HealthCheck, IncrementIntensityLevel, TurnOff, TurnOn                                                     |
| `"MICROWAVE"`       | Type of a microwave      | GetRemainingTime, HealthCheck, TurnOff, TurnOn                                                                                      |
| `"MOTIONSENSOR"`    | Type of a motion detector    | GetDeviceState, HealthCheck                                                                                                             |
| `"OPENCLOSESENSOR"` | Type of an open-close sensor    | GetCloseTime, GetDeviceState, GetOpenState, GetOpenTime, HealthCheck                                                                                   |
| `"OVEN"`            | Type of an oven            | GetDeviceState, HealthCheck                                                                                                             |
| `"POWERSTRIP"`      | Type of a power strip         | GetConsumption, GetEstimateBill, GetProgressiveTaxBracket, HealthCheck, TurnOff, TurnOn                                                                     |
| `"PURIFIER"`        | Type of a water purifier          | GetDeviceState, GetExpendableState, GetTargetTemperature, HealthCheck, ReleaseMode, SetMode, SetTargetTemperature  |
| `"RANGE"`           | Type of an electric range          | GetDeviceState, HealthCheck                                                                                                             |
| `"RANGEHOOD"`       | Type of a range hood      | GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                                                      |
| `"REFRIGERATOR"`    | Type of a refrigerator          | GetDeviceState, HealthCheck, SetFreezerTargetTemperature, SetFridgeTargetTemperature, SetMode                                           |
| `"RICECOOKER"`      | Type of a rice cooker        | GetCleaningCycle, GetDeviceState, GetExpendableState, GetKeepWarmTime, GetPhase, GetRemainingTime, HealthCheck, ReleaseMode, SetMode, Stop, TurnOff, TurnOn          |
| `"ROBOTVACUUM"`     | Type of a robot vacuum       |Charge, GetBatteryInfo, GetDeviceState, HealthCheck, TurnOff, TurnOn           |
| `"SETTOPBOX"`       | Type of a set-top box     | ChangeInputSource, DecrementChannel, DecrementVolume, HealthCheck, IncrementChannel, IncrementVolume, Mute, SetChannel, SetChannelByName, SetInputSourceByName, StartRecording, StopRecording, TurnOff, TurnOn, Unmute |
| `"SLEEPINGMONITOR"` | Type of a sleep sensor        | GetAsleepDuration, GetAwakeDuration, GetDeviceState, GetSleepScore, GetSleepStartTime, HealthCheck, TurnOff, TurnOn              |
| `"SMARTBED"`        | Type of a smart bed      | HealthCheck, Lower, Raise, Stop                                                                                                   |
| `"SMARTCHAIR"`      | Type of a smart chair      | GetCurrentSittingState, GetRightPostureRatio, GetUsageTime, HealthCheck                                                                                       |
| `"SMARTCURTAIN"`    | Type of a smart curtain      | Close, GetDeviceState, GetOpenState, HealthCheck, Open, Stop |
| `"SMARTHUB"`        | Type of a smart hub      | GetCurrentTemperature, GetDeviceState, GetHumidity, GetTargetTemperature, HealthCheck, SetMode     |
| `"SMARTLOCK"`      | Type of a smart lock     | GetDeviceState, GetLockState, SetLockState                                            |
| `"SMARTMETER"`      | Type of a smart meter      | GetConsumption, GetDeviceState, GetCurrentBill, GetEstimateBill, GetProgressiveTaxBracket, HealthCheck  |
| `"SMARTPLUG"`       | Type of a smart plug      | GetConsumption, GetDeviceState, GetEstimateBill, HealthCheck, TurnOff, TurnOn    |
| `"SMARTTV"`         | Type of a smart TV      | ChangeInputSource, DecrementChannel, DecrementVolume, HealthCheck, IncrementChannel, IncrementVolume, Mute, SetChannel, SetChannelByName, SetInputSourceByName, StartRecording, StopRecording, TurnOff, TurnOn, Unmute |
| `"SMARTVALVE"`      | Type of a smart valve      | GetLockState, SetLockState                                                                                                        |
| `"SMOKESENSOR"`     | Type of a smoke sensor      | GetDeviceState, HealthCheck                                                                                                             |
| `"SWITCH"`          | Type of a switch to control outlets in homes | HealthCheck, TurnOff, TurnOn                                                                                       |
| `"THERMOSTAT"`      | Type of a thermostat   | DecrementTargetTemperature, GetCurrentTemperature, GetTargetTemperature, HealthCheck, IncrementTargetTemperature, SetMode, SetTargetTemperature, TurnOff, TurnOn    |
| `"VENTILATOR"`      | Type of a ventilator          | GetDeviceState, HealthCheck, TurnOff, TurnOn                                                                                            |
| `"WATERBOILER"`     | Type of a water heater          | GetDeviceState, HealthCheck, ReleaseMode, SetMode, TurnOff, TurnOn  |

<div class="note">
<p><strong>Note!</strong></p>
<p>Depending on the functional conditions of the actual appliance, you can limit the actions supported by the applianceTypes of the appliance. For example, if there is no function to adjust the fan speed on the air purifier (<code>AIRPURIFIER</code> type), a DiscoverAppliancesResponse message can be sent to exclude the IncrementFanSpeed and DecrementFanSpeed fields from the permitted actions. Note that if the user requests an unsupported action, CEK informs the user immediately that the request is not within the permitted range.</p>
</div>

### Actions {#Actions}
The table below lists the [interfaces](/CEK/References/CEK_API.md#ClovaHomeExtInterface) related to each action:

| actions                    | Related interface                            |
|----------------------------|------------------------------------------|
| ChangeInputSource          | [`ChangeInputSourceConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ChangeInputSourceConfirmation), [`ChangeInputSourceRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ChangeInputSourceRequest)  |
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
| GetCurrtentSittingState     | [`GetCurrtentSittingStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrtentSittingStateRequest), [`GetCurrtentSittingStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrtentSittingStateResponse) |
| GetCurrentTemperature       | [`GetCurrentTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentTemperatureRequest), [`GetCurrentTemperatureResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentTemperatureResponse) |
| GetDeviceState             | [`GetDeviceStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateRequest), [`GetDeviceStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateResponse)  |
| GetEstimateBill            | [`GetEstimateBillRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateBillRequest), [`GetEstimateBillResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateBillResponse)  |
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
| SetFreezerTargetTemperature | [`SetFreezerTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFreezerTargetTemperatureConfirmation), [`SetFreezerTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFreezerTargetTemperatureRequest)  |
| SetFridgeTargetTemperature | [`SetFridgeTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFridgeTargetTemperatureConfirmation), [`SetFridgeTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFridgeTargetTemperatureRequest)  |
| SetInputSourceByName       | [`SetInputSourceByNameConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetInputSourceByNameConfirmation), [`SetInputSourceByNameRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetInputSourceByNameRequest)  |
| SetLockState               | [`SetLockStateConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetLockStateConfirmation), [`SetLockStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetLockStateRequest)  |
| SetMode                    | [`SetModeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeConfirmation), [`SetModeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeRequest) |
| SetTargetTemperature       | [`SetTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureConfirmation), [`SetTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureConfirmation)  |
| StartRecording             | [`StartRecordingConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StartRecordingConfirmation), [`StartRecordingRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StartRecordingRequest)  |
| Stop                       | [`StopConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StopConfirmation), [`StopRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StopRequest)  |
| StopRecording             | [`StopRecordingConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StopRecordingConfirmation), [`StopRecordingRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StopRecordingRequest)  |
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

### Object example
{% raw %}

```json
// Example 1: An example used in the DiscoverAppliancesResponse message
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
BatteryInfoObject contains information on the appliance battery. It indicates the remaining battery with integer numbers (0-100) as a percentage.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Remaining battery (%)                 | Required/Always     |

### Object example
{% raw %}

```json
// Example 1: An example used in the GetBatteryInfoRequest message
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
      "applianceId": "device-010"
    }
  }
}

// Example 2: An example used in the GetBatteryInfoResponse message
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
* [`GetBatteryInfoRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetBatteryInfoRequest)
* [`GetBatteryInfoResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetBatteryInfoResponse)

## BillInfoObject {#BillInfoObject}
BillInfoObject contains the information on billing based on the power usage measured by the appliance. The billing information is displayed in two components: amount and currency unit.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `currency`    | string  | Currency unit (<a href="https://en.wikipedia.org/wiki/ISO_4217" target="_blank">ISO 4217</a>)  | Required/Always |
| `value`       | number  | Amount of bill                    | Required/Always   |

### Object example
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
        "value": 2990,
        "currency": "JPY"
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
BrightnessInfoObject contains information on light or screen brightness. It indicates the brightness to set on a light or a screen, or the brightness before and after change with integer numbers (0-100) as a percentage.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Brightness (%)                      | Required/Always     |

### Object example
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
ColorInfoObject contains information on the color of lights, the screen, or the lamp of the target appliance. It indicates the color of the light, screen color, or lamp color to change, or the color before and after the change. The color information is expressed in the (<a href="https://en.wikipedia.org/wiki/HSL_and_HSV" target="_blank">HSV</a>) model.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `brightness`  | number  | Brightness (0 - 100). This field is omissible if [BrightnessInfoObject](#BrightnessInfoObject) is used on the brightness settings of a specific appliance.  | Optional/Conditional |
| `hue`         | number  | Hue (0 - 360).                  | Required/Always |
| `saturation`  | number  | Saturation (0 - 100).                  | Required/Always |

### Object example
{% raw %}

```json
// Example: An example used in the SetColorRequest message
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
```

{% endraw %}

### See also
* [`SetColorConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorConfirmation)
* [`SetColorRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorRequest)

## ColorTemperatureInfoObject {#ColorTemperatureInfoObject}
ColorTemperatureInfoObject contains information on the color temperature of a light, a screen, or lamp of the target appliance. It indicates the color temperature of a light, a screen, or lamp of the target appliance, or the color temperature before and after the change. The unit is in Kelvin (K).

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | The color temperature (K, Kelvin).             | Required/Always     |

### Object example
{% raw %}

```json
// Example: An example used in the SetColorTemperatureRequest message
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
* [`SetColorTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorTemperatureConfirmation)
* [`SetColorTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetColorTemperatureRequest)

## ConsumptionInfoObject {#ConsumptionInfoObject}
ConsumptionInfoObject contains usage information on energy or resources measured by the appliance. The consumption information is displayed in two components: energy consumption amount and unit.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `name`        | string  | The name of item consuming energy or resource.                   | Required/Always  |
| `unit`        | string  | Energy or resource consumption unit (e.g. Electricity: kW)        | Required/Always  |
| `value`       | number  | Energy or resource consumption amount.                    | Required/Always   |

### Object example
{% raw %}

```json
// Example: An example used in the GetConsumptionResponse message
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
* [`GetCurrentBillRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentBillRequest)
* [`GetCurrentBillResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentBillResponse)
* [`GetEstimateBillRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateBillRequest)
* [`GetEstimateBillResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetEstimateBillResponse)


## CountInfoObject {#CountInfoObject}
CountInfoObject contains information on the number of count. It indicates the specified number of times the user changes the command.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `value`             | number  | The number of count.                      | Required/Always     |

### Object example
{% raw %}

```json
// Example: An example used in the ChangeInputSourceRequest message
// A command to "change input of television 3 times"
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "ChangeInputSourceRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
        "applianceId": "device-007"
    },
    "count": {
      "value": 3
    }
  }
}
```
{% endraw %}

### See also
* [`ChangeInputSourceRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#ChangeInputSourceRequest)

## CustomCommandInfoObject {#CustomCommandInfoObject}

CustomCommandInfoObject contains information on custom commands. It holds information on a customized command that the user registered with the Clova app. The commands registered to the user account are returned with the appliance information in the retrieval results of the [`DiscoverAppliancesResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DiscoverAppliancesResponse) message. This object includes the control actions of an appliance that is performed when custom command is invoked.

### Object fields

| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `name`        | string  | The name of the custom command.             | Required/Always      |
| `actions[]`   | [ActionInfoObject](#ActionInfoObject) array | The list of appliance control actions to be processed by the custom command.  | Required/Always  |

### Object example
{% raw %}

```json
// Example: An example used in the DiscoverAppliancesResponse message
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
        "name": "Good night",
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
* [`DiscoverAppliancesResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#DiscoverAppliancesResponse)

## CustomInfoObject {#CustomInfoObject}

CustomInfoObject contains information directly entered by the user such as customized name, required unit, or values. This object is used when the [shared objects](#SharedObjects) provided by default cannot express the object information or when providing all information of the appliance using the [`GetDeviceStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateResponse) message.

### Object fields
| Field name       | Data type    | Field description                     | Required |
|---------------|---------|-----------------------------|:-------------:|
| `name`        | string            | The customized name to indicate an appliance state or measurement target. When responding to the user, the state name entered in this field is output as speech. | Required/Always |
| `value`       | number or string | The state value or measurement value.                                                                             | Required/Always |
| `unit`        | string            | The value of the appliance state or the unit information of the measurement. This is omitted if the data type of the `value` field is a string and may have the following units if it is a numeric value.<ul><li><code>"celcius"</code> : Celsius</li><li><code>"percentage"</code>: Percentage</li></ul> | Optional/Conditional |

### Object example
{% raw %}

```json
// Example: An example used in the GetDeviceStateResponse message
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
* [`GetDeviceStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateRequest)
* [`GetDeviceStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetDeviceStateResponse)

## ExpendableInfoObject {#ExpendableInfoObject}
ExpendableInfoObject contains information on usage or remaining lifespan of appliance parts. It is used to indicate the usage amount of the appliance parts or their remaining lifespans.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `name`          | string  | The name of the part.                  | Required/Always |
| `remainingTime` | string   | The remaining lifespan of the part. (Duration, <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601</a>)    | Optional/Conditional |
| `usage`         | [CustomInfoObject](#CustomInfoObject)          | The usage amount of the part (can be expressed as the number of uses or percentage of usage).      | Optional/Conditional |

### Object example
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
* [`GetExpendableStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetExpendableStateRequest)
* [`GetExpendableStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetExpendableStateResponse)

## FineDustInfoObject {#FineDustInfoObject}
FineDustInfoObject contains information on fine dust. This is used to indicate the fine dust index or level measured by the appliance. It is expressed as a number.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | PM10 air quality index.                  | Optional/Conditional    |
| `index`       | string  | The PM10 level. Available values are:<ul><li><code>"good"</code> : Good</li><li><code>"normal"</code>: Normal</li><li><code>"bad"</code>: Bad</li><li><code>"verybad"</code>: Very bad</li></ul> | Required/Always     |

### Object example
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
* [`GetFineDustRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetFineDustRequest)
* [`GetFineDustResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetFineDustResponse)

## IntensityLevelInfoObject {#IntensityLevelInfoObject}
IntensityLevelInfoObject contains information on pressure or water pressure intensity. This is displayed according to the pressure or water pressure intensities in each appliance.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Intensity of pressure or water pressure.            | Optional/Conditional    |

### Object example
{% raw %}

```json
// Example: An example used in the IncrementIntensityLevelConfirmation message
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
ModeInfoObject contains information on the operation mode. This is used to indicate the name of the operation mode to change or the operation mode before and after the change. It is represented as a string.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | [The operation mode](#OperationModes).    | Required/Always     |

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
          {% if book.TargetCountryCode == "JP" %}
          <li><code>"auto"</code>: Auto mode. A mode mainly used in air conditioners.</li>
          <li><code>"away"</code>: Away mode.</li>
          <li><code>"blower"</code>: Blower mode.</li>
          {% endif %}
          <li><code>"cool"</code>: Cooling mode. A mode mainly used in air conditioners.</li>
          <li><code>"dehumidify"</code>: Dehumidifier mode. A mode mainly used in appliances such as air conditioners or dehumidifiers.</li>
          {% if book.TargetCountryCode == "JP" %}
          <li><code>"heat"</code>: Heating mode. A mode mainly used in air conditioners.</li>
          <li><code>"indoor"</code>: Indoor mode.</li>
          {% endif %}
          <li><code>"sleep"</code>: Sleep mode. A mode mainly used in appliances such as smart hubs.</li>
          {% if book.TargetCountryCode == "JP" %}          
          <li><code>"wakeup"</code>: Wake up mode.</li>
          {% endif %}
        </ul>
      </td>
    </tr>
    <tr>
      <td><code>"AIRPURIFIER"</code></td>
      <td>
        <ul>
          {% if book.TargetCountryCode == "JP" %}
          <li><code>"auto"</code>：Auto mode. A mode mainly used in air conditioners.</li>
          <li><code>"dehumidify"</code>：Dehumidifier mode. A mode mainly used in appliances such as air conditioners or dehumidifiers.</li>
          <li><code>"humidify"</code>：Humidifier mode. A mode mainly used in appliances such as air conditioners or humidifiers.</li>
          <li><code>"removepollen"</code>：Remove pollen mode. A mode mainly used in appliances such as air purifier. </li>
          <li><code>"sleep"</code>：Sleep mode. A mode mainly used in appliances such as smart hubs.</li>
          {% endif %}
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
          {% if book.TargetCountryCode != "JP" %}
          <li><code>"hotwater"</code>: Hot water mode.</li>
          {% endif %}
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
          {% if book.TargetCountryCode != "JP" %}
          <li><code>"hotwater"</code>: Hot water mode.</li>
          {% endif %}
          <li><code>"indoor"</code>: Indoor mode.</li>
          <li><code>"sleep"</code>: Sleep mode.</li>
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

### Object example
{% raw %}

```json
// Example 1: An example used in the SetModeRequest message - Thermostat
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

// Example 2: An example used in the SetModeRequest message - Smart hub
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
* [`SetModeConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeConfirmation)
* [`SetModeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeRequest)

## HumidityInfoObject {#HumidityInfoObject}
HumidityInfoObject contains information on humidity. This is used to indicate the humidity condition measured by the appliance. It is represented as a string.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | The humidity (%).                      | Required/Always     |

### Object example
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
* [`GetHumidityRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetHumidityRequest)
* [`GetHumidityResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetHumidityResponse)

## PeriodInfoObject {#PeriodInfoObject}

PeriodInfoObject contains information for periods used to retrieve measured data such as amount of consumption or estimated bills.

### Object fields

| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `end`         | string  | The end time of the period. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)    | Required/Always      |
| `start`       | string  | The start time of the period. (Timestamp, <a href="https://en.wikipedia.org/wiki/ISO_8601" target="_blank">ISO 8601</a>)    | Required/Always      |

### Object example
{% raw %}

```json
// Example: An example used in the GetUsageTimeRequest message
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
* [`GetUsageTimeRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetUsageTimeRequest)

## PhaseInfoObject {#PhaseInfoObject}

PhaseInfoObject contains information on the phase of appliance actions. This is used to indicate the current phase of the action or the previous phase of the action.

### Object fields

| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | The string to express the phase of action.        | Required/Always      |

### Object example
{% raw %}

```json
// Example 1: An example used in the GetPhaseResponse message
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

// Example 2: An example used in the StopConfirmation message
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
* [`GetPhaseRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetPhaseRequest)
* [`GetPhaseResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetPhaseResponse)
* [`StopConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StopConfirmation)
* [`StopRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#StopRequest)

## ProgressiveTaxBracketInfoObject {#ProgressiveTaxBracketInfoObject}
ProgressiveTaxBracketInfoObject contains information on progressive tax brackets.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Progressive tax bracket                    | Required/Always     |

### Object example
{% raw %}

```json
// Example 1: An example used in the GetProgressiveTaxBracketResponse message
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
* [`GetProgressiveTaxBracketRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetProgressiveTaxBracketRequest)
* [`GetProgressiveTaxBracketResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetProgressiveTaxBracketResponse)

## SittingStateInfoObject {#SittingStateInfoObject}
SittingStateInfoObject contains the sit-down information of the user on appliances such as a smart chair.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | boolean | The sit-down state.<ul><li><code>true</code>: Seated</li><li><code>false</code>: Not seated</li></ul>       | Required/Always     |

### Object example
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
* [`GetCurrentSittingStateRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentSittingStateRequest)
* [`GetCurrentSittingStateResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentSittingStateResponse)

## SleepScoreInfoObject {#SleepScoreInfoObject}
SleepScoreInfoObject contains information on sleep score. This object contains the average value if the sleep score result represents a time period.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | The sleep score.                     | Required/Always     |

### Object example
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
* [`GetSleepScoreRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetSleepScoreRequest)
* [`GetSleepScoreResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetSleepScoreResponse)

## SpeedInfoObject {#SpeedInfoObject}
SpeedInfoObject contains information on speed. This is used to indicate the speed to change or the desired speed before and after the change. It is expressed as an integer.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | Speed value                       | Required/Always     |

### Object example
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
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | The temperature value.                       | Required/Always     |

### Object example
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
* [`GetCurrentTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentTemperatureRequest)
* [`GetCurrentTemperatureResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetCurrentTemperatureResponse)
* [`GetTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetTargetTemperatureRequest)
* [`GetTargetTemperatureResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetTargetTemperatureResponse)
* [`IncrementTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementTargetTemperatureConfirmation)
* [`IncrementTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#IncrementTargetTemperatureRequest)
* [`SetFreezerTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFreezerTargetTemperatureConfirmation)
* [`SetFreezerTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFreezerTargetTemperatureRequest)
* [`SetFridgeTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFridgeTargetTemperatureConfirmation)
* [`SetFridgeTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetFridgeTargetTemperatureRequest)
* [`SetTargetTemperatureConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureConfirmation)
* [`SetTargetTemperatureRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetTargetTemperatureRequest)

## TVChannelNameInfoObject {#TVChannelNameInfoObject}
TVChannelNameInfoObject contains information on a TV channel name. This is used to indicate the name of TV channel to change or the TV channel before and after the change. It is represented as a string.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | The name of the TV channel.                  | Required/Always     |

### Object example
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
TVChannelInfoObject contains information on a TV channel number. This is used to indicate the number of TV channel to change or the TV channel number before and after the change. It is expressed as a number.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`             | number  | The TV channel number.                      | Required/Always     |

### Object example
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

## TVInputSourceNameInfoObject {#TVInputSourceNameInfoObject}
TVInputSourceNameInfoObject contains information on the TV input source name. This is used to indicate the input source name to change, or the input source name before and after the change. It is represented as a string.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | string  | The name of the TV input source.	                  | Required/Always     |

### Object example
{% raw %}

```json
// Example 1: An example used in the SetInputSourceByNameRequest message
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
      "applianceId": "device-006"
    },
    "sourceName": {
      "value": "HDMI1"
    }
  }
}

// Example 2: An example used in the SetInputSourceByNameConfirmation message
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
* [`SetInputSourceByNameConfirmation`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetInputSourceByNameConfirmation)
* [`SetInputSourceByNameRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetInputSourceByNameRequest)

## UltraFineDustInfoObject {#UltraFineDustInfoObject}
UltraFineDustInfoObject contains information on ultrafine dust. This is used to indicate the PM2.5 index measured by the appliance. It is expressed as a number.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | PM2.5 air quality index.                | Optional/Conditional    |
| `index`       | number  | The PM2.5 level. Available values are:<ul><li><code>"good"</code> : Good</li><li><code>"normal"</code>: Normal</li><li><code>"bad"</code>: Bad</li><li><code>"verybad"</code>: Very bad</li></ul> | Required/Always     |

### Object example
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
* [`GetUltraFineDustRequest`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetUltraFineDustRequest)
* [`GetUltraFineDustResponse`](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#GetUltraFineDustResponse)

## VolumeInfoObject {#VolumeInfoObject}
VolumeInfoObject contains information on the speaker volume. This is used to indicate the new volume to change or the volume before and after the change. It is expressed as an integer.

### Object fields
| Field name       | Data type    | Field description                     | Required/Optional |
|---------------|---------|-----------------------------|:-------------:|
| `value`       | number  | The value of the volume.                       | Required/Always     |

### Object example
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
