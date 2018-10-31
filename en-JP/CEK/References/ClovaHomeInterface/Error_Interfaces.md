# Error
Error interfaces are used when the Clova Home Extension returns errors to CEK. You can use the error messages below.


| Message name         | Type  | Description                                   |
|------------------|-----------|---------------------------------------------|
| [`ConditionsNotMetError`](#ConditionsNotMetError)          | Error response | Sent to CEK as a response if a certain condition (state) required for operating the target appliance is not satisfied. |
| [`DeviceFailureError`](#DeviceFailureError)                | Error response | Sent to CEK as a response if a defect occurs in the target appliance.              |
| [`DriverInternalError`](#DriverInternalError)              | Error response | Sent to CEK as a response if an internal error occurs.                |
| [`ExpiredAccessTokenError`](#ExpiredAccessTokenError)      | Error response | Sent to CEK as a response if the access token issued by the [authorization server](/CEK/Guides/Link_User_Account.md#BuildAuthServer) during the [account linking](/CEK/Guides/Link_User_Account.md) process is expired.  |
| [`InvalidAccessTokenError`](#InvalidAccessTokenError)      | Error response | Sent to CEK as a response if the user has disabled permissions on the access token being used.         |
| [`NoSuchTargetError`](#NoSuchTargetError)                  | Error response | Sent to CEK as a response if the target device is not found.                            |
| [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError) | Error response | Sent to CEK as a response, if a directive that is not supported in the current mode of the appliance is received.  |
| [`TargetOfflineError`](#TargetOfflineError)                | Error response | Sent to CEK as a response if the target device is offline and cannot be connected. |
| [`UnsupportedOperationError`](#UnsupportedOperationError)  | Error response | Sent to CEK as a response if an action unsupported by the target appliance is requested.   |
| [`ValueNotFoundError`](#ValueNotFoundError)                | Error response | Sent to CEK as a response, if the requested value cannot be provided because the target device has failed to measure or store the measurement value or the state value.  |
| [`ValueOutOfRangeError`](#ValueOutOfRangeError)            | Error response | Sent to CEK as a response if the requested action is outside of the range that can be processed by the target device. |

<div class="note">
<p><strong>Note!</strong></p>
<p>More error message types are coming soon.</p>
</div>

## ConditionsNotMetError {#ConditionsNotMetError}
Sent to CEK as a response if a certain condition (state) required for operating the target appliance is not satisfied. When CEK receives this message, a predefined error message is sent to the client.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `state`       | string  | The value that explains the unsatisfied condition or state. This field must be written in a language comprehensible to users, as the value is sent to users as TTS. The value in this field is used in the following format to inform the user of the current situation:<pre><code>This feature is not supported when the {target device} is in {state}. Please check and try again.</code></pre>  |<!-- -->|

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "4ea1e527-7be3-4b54-b531-93d245b97303",
    "namespace": "ClovaHome",
    "name": "ConditionsNotMetError",
    "payloadVersion": "1.0"
  },
  "payload": {
    "state": "Power-saving mode"
  }
}
```
{% endraw %}

### See also
* [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError)

## DeviceFailureError {#DeviceFailureError}
Sent to CEK as a response if a defect occurs in the target appliance. When CEK receives this message, a predefined error message is sent to the client.

### Payload fields

None

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* A separate `payload` is not required because the names of the error messages provide information on the situation.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "4ea1e527-7be3-4b54-b531-93d245b97303",
    "namespace": "ClovaHome",
    "name": "DeviceFailureError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`DriverInternalError`](#DriverInternalError)
* [`TargetOfflineError`](#TargetOfflineError)

## DriverInternalError {#DriverInternalError}
Sent to CEK as a response if an internal error occurs. When CEK receives this message, a predefined error message is sent to the client.

### Payload fields

None

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* A separate `payload` is not required because the names of the error messages provide information on the situation.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "DriverInternalError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`DeviceFailureError`](#DeviceFailureError)
* [`TargetOfflineError`](#TargetOfflineError)

## ExpiredAccessTokenError {#ExpiredAccessTokenError}
Sent to CEK as a response if the access token issued by the [authorization server](/CEK/Guides/Link_User_Account.md#BuildAuthServer) during the [account linking](/CEK/Guides/Link_User_Account.md) process is expired. When CEK receives this message, a predefined error message is sent to the client.

### Payload fields

None

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* A separate `payload` is not required because the names of the error messages provide information on the situation.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "1abd6113-4a36-47c3-851e-bee3254fe183",
    "namespace": "ClovaHome",
    "name": "ExpiredAccessTokenError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`InvalidAccessTokenError`](#InvalidAccessTokenError)

## InvalidAccessTokenError {#InvalidAccessTokenError}
Sent to CEK as a response if the user has disabled permissions on the access token being used. When CEK receives this message, a predefined error message is sent to the client.

### Payload fields

None

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* A separate `payload` is not required because the names of the error messages provide information on the situation.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "b8ac8b45-9fb9-4dc4-97ca-d55e9fc1ff8f",
    "namespace": "ClovaHome",
    "name": "InvalidAccessTokenError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`ExpiredAccessTokenError`](#ExpiredAccessTokenError)

## NoSuchTargetError {#NoSuchTargetError}
Sent to CEK as a response if the target device is not found. For example, this message must be sent if the user has deleted an appliance from an IoT service, but a control request for the appliance has been made before the information is reflected on the Clova app. When CEK receives this message, a predefined error message is sent to the client.

### Payload fields

None

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* A separate `payload` is not required because the names of the error messages provide information on the situation.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "d458e46c-6827-4940-9340-a7a9d427d7ab",
    "namespace": "ClovaHome",
    "name": "NoSuchTargetError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`ConditionsNotMetError`](#ConditionsNotMetError)
* [`TargetOfflineError`](#TargetOfflineError)

## NotSupportedInCurrentModeError {#NotSupportedInCurrentModeError}
Sent to CEK as a response, if a directive that is not supported in the current mode of the appliance is received. For example, template-related controls may be restricted for some air conditioners operating in dehumidifier mode. This message must be sent to users of those products if a control request for temperature is made in dehumidifier mode. When CEK receives this message, a predefined error message is sent to the client.

### Payload fields

None

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* A separate `payload` is not required because the names of the error messages provide information on the situation.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "f321b946-b593-4279-a840-8e5af5a00146",
    "namespace": "ClovaHome",
    "name": "NotSupportedInCurrentModeError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`UnsupportedOperationError`](#UnsupportedOperationError)

## TargetOfflineError {#TargetOfflineError}
Sent to CEK as a response if the target device is offline and cannot be connected. When CEK receives this message, a predefined error message is sent to the client.

### Payload fields

None

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* A separate `payload` is not required because the names of the error messages provide information on the situation.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "TargetOfflineError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`DeviceFailureError`](#DeviceFailureError)
* [`DriverInternalError`](#DriverInternalError)

## UnsupportedOperationError {#UnsupportedOperationError}

Sent to CEK as a response if an action unsupported by the target appliance is requested. If the user requests an action that is unsupported by default, CEK informs the user immediately that the request is not within the permitted range. However, the permitted range of actions, such as `SetMode`, cannot be checked until the Clova Home Extension receives the [SetModeRequest](/CEK/References/ClovaHomeInterface/Control_Interfaces.md#SetModeRequest) message and checks the `mode` field value. When the Clova Home Extension sends a message and the action is not supported, an error response must be sent. The `UnsupportedOperationError` message can be used to send to CEK.

For example, let us assume that the thermostat (`"THERMOSTAT"` type) of a user can perform the `SetMode` action and supports `"sleep"` and `"away"` modes. If the user requests to set the `"cool"` mode on the appliance, the Clova Home Extension must send an `UnsupportedOperationError` message to CEK.

### Payload fields

None

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* A separate `payload` is not required because the names of the error messages provide information on the situation.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "e9a77ef6-748b-4f9b-aa3e-c14ece3fa726",
    "namespace": "ClovaHome",
    "name": "UnsupportedOperationError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError)

## ValueNotFoundError {#ValueNotFoundError}
Sent to CEK as a response, if the requested value cannot be provided because the target device has failed to measure or store the measurement value or the state value. For example, an air conditioner must provide values, such as the current temperature, by default but it may not be able to provide it due to a defect or temporarily failure. This message can be used in such situations.

### Payload fields
None

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* A separate `payload` is not required because the names of the error messages provide information on the situation.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "57109b11-ee04-45df-9dd2-c979bc8608ea",
    "namespace": "ClovaHome",
    "name": "ValueNotFoundError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`ValueOutOfRangeError`](#ValueOutOfRangeError)

## ValueOutOfRangeError {#ValueOutOfRangeError}
Sent to CEK as a response if the requested action is outside of the range that can be processed by the target device. For example, this message can be sent if a user requests to set a temperature such as 16 or 30 on the air conditioning when the available setting is 18-28. The `payload` field must deliver the maximum and minimum values that can be processed by the target appliance.

### Payload fields

| Field name       | Data type    | Field description                     | Optional |
|---------------|---------|-----------------------------|:---------:|
| `maximumValue` | number | Maximum setting value permitted on the target appliance. |<!-- -->|
| `minimumValue` | number | Minimum setting value permitted on the target appliance. |<!-- -->|

### Remarks
* The extension must send the error messages to CEK as a normal HTTP response (200 OK).
* The values entered in `payload` fields can be used to inform users.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "ValueOutOfRangeError",
    "payloadVersion": "1.0"
  },
  "payload": {
    "minimumValue":18.0,
    "maximumValue":30.0
  }
}
```
{% endraw %}

### See also
* [`ValueNotFoundError`](#ValueNotFoundError)
