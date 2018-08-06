# Settings

The Settings namespace provides interfaces for updating or synchronizing the client settings information between Clova and the client. The Settings namespace provides the following events and directives.

| Message name         | Type  | Description                                 |
|------------------|-----------|-------------------------------------------|
| [`ExpectReport`](#ExpectReport) | Directive | Instructs the client to report the current settings information. Upon receiving the directive, the client must send the [`Settings.Report`](#Report) event to CIC. |
| [`Report`](#Report)             | Event     | Reports the current settings information to CIC. If the [`Settings.ExpectReport`](#ExpectReport) directive is received from CIC, the client must send the `Settings.Report` event to CIC. |
| [`Update`](#Update)             | Directive | Instructs the client to apply the values saved to the `payload` as the setting value.  |

<div class="note">
  <p><strong>Note!</strong></p>
  <p>See the <a href="#WorkFlow">interaction structure</a> for updating or synchronizing the settings information.</p>
</div>

## Interaction structure {#WorkFlow}

You must update or synchronize the settings information using Settings in the following situations:

* When the user is looking up the client device settings information from the Clova app, **the settings information needs to be synchronized**.
* When the user has **changed the device settings information from the Clova app**, you need to update the changes in the device settings information.
* When the user has **changed the settings information directly** from the client device, you need to update the changes in the Clova app.

The structure for updating or synchronizing the settings information using Settings is shown below.

![](/CIC/Resources/Images/CIC_Settings_Work_Flow.png)

Once CIC receives the request for **synchronizing the settings information** of the client device from the Clova app, CIC and the client device operates in the following order:

1. CIC sends the `Settings.ExpectReport` directive to the client device.
2. The client device must send the current settings information to CIC using the `Settings.Report` event.
3. CIC sends the reported settings information to the Clova app.

When the user has **changed the settings information of the client device** from the Clova app, CIC receives a request to update the device settings. Here, CIC and the client device operates in the following order:

1. CIC sends the `Settings.Update` directive to the client device.
2. The client device must send the changed settings information to CIC using the `Settings.Report` event.
3. CIC sends the reported settings information to the Clova app.

When the user has **changed the settings information directly** on the client device, the action of updating the settings information of the Clova app is performed as follows:

1. The client device must send the settings information with changed settings to CIC using the `Settings.Report` event.
2. CIC sends the reported settings information to the Clova app.

## ExpectReport directive {#ExpectReport}
Instructs the client to report the current settings information. Upon receiving the directive, the client must send the [`Settings.Report`](#Report) event to CIC.

### Payload fields

None

### Remarks

* This directive is sent through a [downchannel](/CIC/Guides/Interact_with_CIC.md#CreateConnection), not as a response to an event.

### Message example

```json
{
  "directive": {
    "header": {
      "namespace": "Settings",
      "name": "ExpectReport",
      "messageId": "29745c13-0d70-408e-a4cc-946afba67524"
    },
    "payload": {}
  }
}
```

### See also
* [`Settings.Report`](#Report)

## Report event {#Report}
Reports the current settings information to CIC. If the [`Settings.ExpectReport`](#ExpectReport) directive is received from CIC, the client must send the `Settings.Report` event to CIC.

### Context fields

{% include "/CIC/References/CICInterface/Context_Objects_List.md" %}

### Payload fields

| Field name       | Data type    | Description                     | Required |
|---------------|---------|-----------------------------|:---------:|
| `configuration` | object | Object containing the settings information of the predefined client. All sub-fields of this object have a string type.<div class="note"><p><strong>Note!</strong></p><p>Contact your Clova representative to predefine the client settings information.</p></div> | Required   |

### Message example
{% raw %}
```json
{
  "context": [
    {{Alerts.AlertsState}},
    {{AudioPlayer.PlayerState}},
    {{Device.DeviceState}},
    {{Device.Display}},
    {{Clova.Location}},
    {{Clova.SavedPlace}},
    {{Speaker.VolumeState}},
    {{SpeechSynthesizer.SpeechState}}
  ],
  "event": {
    "header": {
      "namespace": "Settings",
      "name": "Report",
      "messageId": "b120c3e0-e6b9-4a3d-96de-71539e5f6214"
    },
    "payload": {
      "configuration": {
        "key1": "value1",
        "key2": "value2",
        ...
      }
    }
  }
}
```
{% endraw %}

### See also
* [`Settings.ExpectReport`](#ExpectReport)

## Update directive {#Update}
Instructs the client to apply the values saved to the `payload` as the setting value.

### Payload fields

| Field name       | Data type    | Description                     | Included |
|---------------|---------|-----------------------------|:---------:|
| `configuration` | object | Object containing the settings information of the predefined client. All sub-fields of this object have a string type.<div class="note"><p><strong>Note!</strong></p><p>Contact your Clova representative to predefine the client settings information.</p></div> | Always   |

### Remarks

* This directive is sent through a [downchannel](/CIC/Guides/Interact_with_CIC.md#CreateConnection), not as a response to an event.

### Message example

{% raw %}

```json
{
  "directive": {
    "header": {
      "namespace": "Settings",
      "name": "Update",
      "messageId": "29745c13-0d70-408e-a4cc-946afba67524"
    },
    "payload": {
      "configuration": {
        "key1": "value1",
        "key2": "value2",
        ...
      }
    }
  }
}
```

{% endraw %}

### See also
* [`Settings.Report`](#Report)
