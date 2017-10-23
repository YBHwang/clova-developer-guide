# Reminder

Creates, looks up or deletes user's reminders. Reminder provides the following event and directive messages.

| Message name         | Message type  | Message description                                   |
|------------------|-----------|---------------------------------------------|
| [`Created`](#Created) | Event  | Requests CIC to create a specified reminder.          |
| [`Deleted`](#Deleted) | Event  | Requests CIC to delete a specified reminder.          |
| [`Get`](#Get)         | Event  | Requests CIC to get a full list of reminders created by a user.  |
| [`Updated`](#Updated) | Event  | Requests CIC to update a specified reminder.          |

## Created event {#Created}
Requests CIC to create a specified reminder. Send this event message in the following scenario.

1. Your client sends CIC a user's spoken request to create a reminder, using a [`SpeechRecognizer.Recognize`](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize) event message.
2. The Clova platform recognizes the reminder creation request and CIC returns it to your client, using a [`Clova.AddReminder`](/CIC/References/CICInterface/Clova.md#AddReminder) directive message.
3. Your client displays the reminder creation request to confirm the intent of the user.
4. Your client receives final confirmation from the user.
   * **When the user accepts the reminder creation,** you send a `Reminder.Created` event message to CIC.
   * **When the user rejects the reminder creation,** you do not have to send any event message.

### Context field

There is no required state information

### Payload field
| Field name       | Type    | Field description                     | Required |
|---------------|---------|-----------------------------|---------|
| `content`       | string  | Content of the reminder to add           | Yes     |
| `done`          | boolean | Whether the reminder was completed or not        | No     |
| `id`            | string  | The ID of the reminder to add            | Yes     |

### Remarks
* Depending on your UX design (usability), you may skip the scenario step 3, 4 and directly proceed to the step of sending the event message to CIC.

* You must return execution results when sending this event message to CIC. For example, display messages such as "Created a reminder" or "Canceled reminder creation."

### Message example

{% raw %}

```json
{
  "context": [],
  "event": {
    "header": {
      "namespace": "Reminder",
      "name": "Created",
      "messageId": "447d7a2f-875c-4d70-84ce-61787811de8c"
    },
    "payload": {
      "id": "100ab3901-bb08-4b36-980a-47fb46c25fcd",
      "content": "비타민 먹기",
      "done": false
    }
  }
}
```
{% endraw %}

### See also
* [`Clova.AddReminder`](/CIC/References/CICInterface/Clova.md#AddReminder)
* [`SpeechRecognizer.Recognize`](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize)


## Deleted event {#Deleted}

Requests CIC to delete a specified reminder. Send this event message in the following scenario.

1. Your client sends CIC a user's spoken request to delete a reminder, using a [`SpeechRecognizer.Recognize`](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize) event message.
2. The Clova platform recognizes the reminder deletion request and CIC returns it to your client, using a [`Clova.DeleteReminder`](/CIC/References/CICInterface/Clova.md#DeleteReminder) directive message.
3. Your client displays the reminder deletion request to confirm the intent of the user.
4. Your client receives final confirmation from the user.
   * **When the user accepts the reminder deletion,** you send a `Reminder.Deleted` event message to CIC.
   * **When the user rejects the reminder deletion,** you do not have to send any event message.

### Context field

There is no required state information

### Payload field

| Field name       | Type    | Field description                     | Required |
|---------------|---------|-----------------------------|---------|
| `id`            | string  | The ID of the reminder to delete            | Yes     |

### Remarks
* Depending on your UX design (usability), you may skip the scenario step 3, 4 and directly proceed to the step of sending the event message to CIC.

* You must return execution results when sending this event message to CIC. For example, display messages such as "Deleted the reminder" or "Canceled reminder deletion."

* Deleting a reminder requires the process of selecting the reminder to delete. This means that you may have to send CIC a [`Reminder.Get`](#Get) event message first so that the user can view the list of reminders.

### Message example

{% raw %}

```json
{
  "context": [],
  "event": {
    "header": {
      "namespace": "Reminder",
      "name": "Deleted",
      "messageId": "1ead8b31-aac4-46c6-9c6e-f6a302196065"
    },
    "payload": {
      "id": "100ab3901-bb08-4b36-980a-47fb46c25fcd"
    }
  }
}
```

{% endraw %}

### See also
* [`Clova.DeleteReminder`](/CIC/References/CICInterface/Clova.md#DeleteReminder)
* [`Reminder.Get`](#Get)
* [`SpeechRecognizer.Recognize`](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize)

## Get event {#Get}

Requests CIC for information of all memos. Send this event message in the following scenario.

1. Your client sends CIC a user's spoken request to look up reminders, using a [`SpeechRecognizer.Recognize`](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize) event message.
2. The Clova platform recognizes the reminder lookup request and CIC returns it to your client, using a [`Clova.GetReminder`](/CIC/References/CICInterface/Clova.md#GetReminder) directive message.
3. Your client displays the reminder lookup request to confirm the intent of the user.
4. Your client receives final confirmation from the user.
   * **When the user accepts the reminder looup,** you send a `Reminder.Get` event message to CIC.
   * **When the user rejects the reminder lookup,** you do not have to send any event message.

### Context field

There is no required state information

### Payload field

None

### Remarks
* Depending on your UX design (usability), you may skip the scenario step 3, 4 and directly proceed to the step of sending the event message to CIC.

* You must return execution results when sending this event message to CIC. For example, display messages such as "Looking up reminders" or "Canceled reminder lookup."

* After you send the Get event message to CIC, CIC returns the user's list of reminders by a [`Clova.RenderReminderList`](/CIC/References/CICInterface/Clova.md#RenderReminderList) directive message.

### Message example

{% raw %}

```json
{
  "context": [],
  "event": {
    "header": {
      "namespace": "Reminder",
      "name": "Get",
      "messageId": "2346313b-2b82-4522-85d8-385b43f2d981"
    },
    "payload": {}
  }
}
```

{% endraw %}

### See also
* [`Clova.GetReminder`](/CIC/References/CICInterface/Clova.md#GetReminder)
* [`Clova.RenderReminderList`](/CIC/References/CICInterface/Clova.md#RenderReminderList)
* [`SpeechRecognizer.Recognize`](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize)

## Updated event {#Updated}

Requests CIC to update a specified reminder.

### Context field

There is no required state information

### Payload field

| Field name       | Type    | Field description                     | Required |
|---------------|---------|-----------------------------|---------|
| `content`       | string  | Content of the reminder to update             | Yes     |
| `id`            | string  | The ID of the reminder to update            | Yes     |

### Remarks

* To update a reminder, users must make changes to the reminder on a UI screen, not with speech input. This means that the request does not require a preceding scenario, such as [reminder creation](#Created) or [reminder deletion](#Deleted).

* An Updated event message changes the entire payload. This means that, if the message has any field left empty, such field will be replaced with an empty value. Make sure not to send only those fields to update. For example, if you send only the done field, the `content` field will be filled with an empty value.

* You can check field values for each reminder when a [`Clova.RenderReminderList`](/CIC/References/CICInterface/Clova.md#RenderReminderList) directive message is returned in response to the [`Reminder.Get`](#Get) event message.

### Message example

{% raw %}

```json
{
  "context": [],
  "event": {
    "header": {
      "namespace": "Reminder",
      "name": "Updated",
      "messageId": "f1f0442f-720c-4264-b709-88f7b52dd14f"
    },
    "payload": {
      "id": "100ab3901-bb08-4b36-980a-47fb46c25fcd",
      "content": "비타민 먹기",
      "done": true
    }
  }
}
```

{% endraw %}

### See also
* [`Reminder.Get`](#Get)
* [`Clova.RenderReminderList`](/CIC/References/CICInterface/Clova.md#RenderReminderList)