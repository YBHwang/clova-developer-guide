# ScheduleList Template
When the user requests for a list of calender schedule, CIC passes the schedule list registered to the user in ScheduleList template format to the client. The client should display the schedule list registered by the user on the screen using the received template.

<div class="note">
<p><strong>Note!</strong></p>
<p>Currently, there are limits to the ScheduleList template as below.</p>
<ul>
  <li>In order to create, modify, delete a calendar account, the user should use the Clova app.</li>
  <li>With the voice command, the user can only request to add a calendar schedule or to check the list.</li>
  <li>In order to modify or delete a calendar schedule, the user should use the Clova app.</li>
</ul>
</div>

## Template field

| Field name       | Type    | Field description                     |
|---------------|---------|-----------------------------|
| `scheduledList[]`        | object array | An object array containing the schedule list registered by the user.   |
| `scheduledList[].content`       | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)     | An object containing contents of the added schedule entered by the user |
| `scheduledList[].end`           | [DateTimeObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateTimeObject) or [DateObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateObject)  | Termination date and time of the added schedule. In case of all day schedule, it is in DateObject format type with date information only. |
| `scheduledList[].start`         | [DateTimeObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateTimeObject) or [DateObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateObject)  | Starting date and time of the added schedule. In case of all day schedule, it is in DateObject format type with date information only. |
| `scheduledList[].repeatDay`     | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) array | An object array containing repeated date information if it is a weekly repeated alarm |
| `scheduledList[].repeatPeriod`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)     | An object containing repeat cycle. The `value` field of the object has the following values. <ul><li>Empty string(<code>""</code>) : One-time schedule </li><li><code>"daily"</code> : Daily repeated schedule</li><li><code>"weekly"</code> : Every week repeated schedule</li></ul> |
| `type`        | string                                                                              | A content template delimiter. The value is always `"ScheduleList"`.             |

## Template Example

{% raw %}

```json
{
  "type": "ScheduleList",
  "scheduledList": [
    {
      "type": "Schedule",
      "start": {
        "type": "datetime",
        "dateTime": "2017-09-30T12:00:00+09:00"
      },
      "end": {
        "type": "datetime",
        "dateTime": "2017-09-30T13:00:00+09:00"
      },
      "content": {
        "type": "string",
        "value": "친구 결혼식"
      },
      "repeatPeriod": {
        "type": "string",
        "value": ""
      },
      "repeatDay": []
    },
    {
      "type": "Schedule",
      "start": {
        "type": "datetime",
        "dateTime": "2017-08-02T10:00:00+09:00"
      },
      "end": {
        "type": "datetime",
        "dateTime": "2017-08-02T11:00:00+09:00"
      },
      "content": {
        "type": "string",
        "value": "데일리 스크럼"
      },
      "repeatPeriod": {
        "type": "string",
        "value": "daily"
      },
      "repeatDay": []
    },
    {
      "type": "Schedule",
      "start": {
        "type": "datetime",
        "dateTime": "2017-08-02T10:00:00+09:00"
      },
      "end": {
        "type": "datetime",
        "dateTime": "2017-08-02T11:00:00+09:00"
      },
      "content": {
        "type": "string",
        "value": "주간 회의"
      },
      "repeatPeriod": {
        "type": "string",
        "value": "weekly"
      },
      "repeatDay": [
        {
          "type": "string",
          "value": "monday"
        }
      ]
    },
    {
      "type": "Schedule",
      "start": {
        "type": "date",
        "dateTime": "2017-09-29"
      },
      "end": {
        "type": "datetime",
        "dateTime": "2017-09-29"
      },
      "content": {
        "type": "string",
        "value": "플레이숍"
      },
      "repeatPeriod": {
        "type": "string",
        "value": ""
      },
      "repeatDay": []
    }
  ]
}
```

{% endraw %}

## Screen UI example {#UIExample}

<div>
<p><strong>Note!</strong></p>
<p>Preparing for an example of a screen which applied a ScheduleList template.</p>
</div>

## See also
* [Alerts](/CIC/References/CICInterface/Alerts.md) Interface
* [ScheduleListList](/CIC/References/ContentTemplates/ScheduleListList.md)