# ActionTimerテンプレート
CICは、ユーザーがアクションタイマーを作成すると、そのアクションタイマーの情報をActionTimerテンプレート形式でクライアントに送信します。クライアントは、このテンプレートを使って、ユーザーが作成したアクションタイマーの情報を画面に表示する必要があります。

<div class="note">
<p><strong>メモ</strong></p>
<p>ActionTimerテンプレートには、現在、次のような制約事項があります。</p>
<ul>
  <li>ユーザーは、音声を使って、アクションタイマーの設定と、アクションタイマーのリストの照会のみリクエストできます。</li>
  <li>ユーザーがアクションタイマーを編集または削除するには、Clovaアプリを使用する必要があります。</li>
</ul>
</div>

## Template fields

| フィールド名       | データ型    | 説明                     |
|---------------|---------|-----------------------------|
| `action`       | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)      | 追加されたアクションタイマーにユーザーが設定したアクションを持つオブジェクト。**現在、空文字列(`""`)が入力されます。将来の拡張のために予約されているフィールドです。** |
| `label`        | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)      | ユーザーが設定したアクションの内容を持つオブジェクト |
| `repeatDay[]`     | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject) array | 毎週繰り返しのアクションタイマーで、繰り返しの曜日を持つオブジェクト配列 |
| `repeatPeriod`  | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)     | 繰り返しの周期を持つオブジェクトです。このオブジェクトの`value`フィールドは、以下の値を持ちます。<ul><li>空文字列(<code>""</code>)：一回性のアクションタイマー</li><li><code>"daily"</code>：毎日繰り返しのアクションタイマー</li><li><code>"weekly"</code>：毎週繰り返しのアクションタイマー</li></ul> |
| `scheduledTime` | [DateTimeObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateTimeObject) | アクションタイマーを鳴らす日付と時間を持つオブジェクト      |
| `token`         | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)     | 追加されたアクションタイマーの識別子を持つオブジェクト  |
| `type`          | string                                                                              | コンテンツテンプレートのタイプを示す値。`"ActionTimer"`を持ちます。  |

## Template example

{% raw %}

```json
// 一回性のアクションタイマー
{
  "type": "ActionTimer",
  "token": {
    "type": "string",
    "value": "072c72b9-cfc5-4127-b4fe-557a10457232"
  },
  "scheduledTime": {
    "type": "datetime",
    "value": "2017-10-01T14:00:00Z"
  },
  "action": {
    "type": "string",
    "value": ""
  },
  "label": {
    "type": "string",
    "value": "音楽を再生する"
  },
  "repeatPeriod": {
    "type": "string",
    "value": ""
  },
  "repeatDay": []
}

// 毎日繰り返しのアクションタイマー
{
  "type": "ActionTimer",
  "token": {
    "type": "string",
    "value": "b5403bd0-1598-495b-a466-9385c2b1103a"
  },
  "scheduledTime": {
    "type": "datetime",
    "value": "2017-10-02T09:00:00Z"
  },
  "action": {
    "type": "string",
    "value": ""
  },
  "label": {
    "type": "string",
    "value": "音楽を再生する"
  },
  "repeatPeriod": {
    "type": "string",
    "value": "daily"
  },
  "repeatDay": []
}

// 毎週繰り返しのアクションタイマー
{
  "type": "ActionTimer",
  "token": {
    "type": "string",
    "value": "da740e2a-01cd-4f2e-aedf-6c4285bae785"
  },
  "scheduledTime": {
    "type": "datetime",
    "value": "2017-10-03T11:00:00Z"
  },
  "action": {
    "type": "string",
    "value": ""
  },
  "label": {
    "type": "string",
    "value": "音楽を再生する"
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
```

{% endraw %}

## UI example {#UIExample}

以下は、{{ book.OrientedService }}が配布したClovaのモバイルアプリで、ActionTimerテンプレートの内容を表したUIサンプルです。

![](/CIC/Resources/Images/Content_Template-ActionTimer.png)

## 次の項目も参照してください。
* [ActionTimerList](/CIC/References/ContentTemplates/ActionTimerList.md)
* [Alerts](/CIC/References/CICInterface/Alerts.md)インターフェース