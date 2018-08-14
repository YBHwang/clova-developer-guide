# Scheduleテンプレート
CICは、ユーザーがカレンダー上にスケジュールを作成すると、そのスケジュールの情報をScheduleテンプレート形式でクライアントに送信します。クライアントは、このテンプレートを使って、ユーザーが作成したスケジュールの情報を画面に表示する必要があります。

<div class="note">
<p><strong>メモ</strong></p>
<p>Scheduleテンプレートには、現在、次のような制約事項があります。</p>
<ul>
  <li>ユーザーがカレンダー上のスケジュールを編集または削除するには、Clovaアプリを使用する必要があります。</li>
  <li>ユーザーは、音声を使って、スケジュールの登録とスケジュールのリストの照会のみリクエストできます。</li>
  <li>ユーザーがカレンダー上のスケジュールを編集または削除するには、Clovaアプリを使用する必要があります。</li>
</ul>
</div>

## Template fields

| フィールド名       | データ型    | 説明                     |
|---------------|---------|-----------------------------|
| `content`       | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)     | 追加されたスケジュールにユーザーが入力した内容を持つオブジェクト |
| `end`           | [DateTimeObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateTimeObject)または[DateObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateObject)  | 追加されたスケジュールが終了する日付と時間。終日のスケジュールの場合、DateObjectデータ型で、時刻のみ持ちます。 |
| `start`         | [DateTimeObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateTimeObject)または[DateObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateObject)  | 追加されたスケジュールが開始する日付と時間。終日のスケジュールの場合、DateObjectデータ型で、時刻のみ持ちます。 |
| `repeatDay[]`     | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) array | 毎週繰り返しのスケジュールの場合、繰り返しの曜日を持つオブジェクト配列 |
| `repeatPeriod`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)     | 繰り返しの周期を持つオブジェクトです。このオブジェクトの`value`フィールドは、以下の値を持ちます。<ul><li>空文字列(<code>""</code>)：一回性のスケジュール</li><li><code>"daily"</code>：毎日繰り返しのスケジュール</li><li><code>"weekly"</code>: 毎週繰り返しのスケジュール</li></ul> |
| `token`         | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)     | 追加されたスケジュールの識別子を持つオブジェクト  |
| `type`          | string                                                                              | コンテンツテンプレートのタイプを示す値。`"Schedule"`に固定されています。             |

## Template example

{% raw %}

```json
// 一回性のスケジュール
{
  "type": "Schedule",
  "token": {
    "type": "string",
    "value": "072c72b9-cfc5-4127-b4fe-557a10457232"
  },
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
    "value": "友達の結婚式"
  },
  "repeatPeriod": {
    "type": "string",
    "value": ""
  },
  "repeatDay": []
}

// 毎日繰り返しのスケジュール
{
  "type": "Schedule",
  "token": {
    "type": "string",
    "value": "b5403bd0-1598-495b-a466-9385c2b1103a"
  },
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
    "value": "デイリー・スクラム"
  },
  "repeatPeriod": {
    "type": "string",
    "value": "daily"
  },
  "repeatDay": []
}

// 毎週繰り返しのスケジュール
{
  "type": "Schedule",
  "token": {
    "type": "string",
    "value": "da740e2a-01cd-4f2e-aedf-6c4285bae785"
  },
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
    "value": "定例会議"
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
}

// 終日のスケジュール
{
  "type": "Schedule",
  "token": {
    "type": "string",
    "value": "5c8b4f7b-d8bd-4817-a1c3-eb9c9522277e"
  },
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
    "value": "プレイストア"
  },
  "repeatPeriod": {
    "type": "string",
    "value": ""
  },
  "repeatDay": []
}
```

{% endraw %}

## UI example {#UIExample}

以下は、{{ book.OrientedService }}が配布したClovaのモバイルアプリで、Scheduleテンプレートの内容を表したUIサンプルです。

![](/CIC/Resources/Images/Content_Template-Schedule.png)

## 次の項目も参照してください。
* [Alerts](/CIC/References/CICInterface/Alerts.md)インターフェース
* [ScheduleList](/CIC/References/ContentTemplates/ScheduleList.md)