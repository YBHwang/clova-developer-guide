# Custom ExtensionとLINEを連携する

LINEでは、ボットとClovaで共通してLINEのIDを軸にしたユーザー管理を実施しています。そのため、ボットで会話した内容をCustom Extensionの応答に反映したり、Custom Extensionでの会話を元に詳細情報をLINEで送信したりすることができます。​  

このドキュメントでは、次の内容について説明します。
* [利用条件](#Conditions)
* [利用方法](#Settings)
* [コードの記述例](#Example)

## 利用条件 {#Conditions}

Custom ExtensionとLINEの連携を実施するには、以下の条件を満たしている必要があります。  

1. Messaging APIを利用していること  
  * 公式アカウントの場合は、API型であること
  * LINE@の場合は、webhookを用いてメッセージのやり取りを実現していること  

  LINE@の場合は、LINE@ Managerの **Messaging APIリファレンス設定** の画面で、以下のように設定されているかを確認します。
  - **webhookを送信** → 利用する
  - **自動応答メッセージ** → 利用しない  
  ![](/CEK/Resources/Images/CEK_Messaging_API_LineManager.png)

  設定方法については、こちらのドキュメントもご確認ください。  
  [LINE Developers ドキュメント > Messaging API > ボットを作成する](https://developers.line.me/ja/docs/messaging-api/building-bot/)

2. ユーザーがボットを友だち追加していること

## 利用方法 {#Settings}
Clovaに対しての操作を行うuserIdと、LINEのMessaging APIを操作するuserIDが一致すると、連携が行われます。必要に応じてユーザー情報の保存や、メッセージ送信を行ってください。
​
具体的には、以下2つのuserIdが一致する必要があります。
* Custom Extensionのリクエストに含まれるuserId  

  Message fieldsの`session.user.userId`​をご参照ください。  
  [CEK APIリファレンス > Custom Extensionメッセージ > リクエストメッセージ](/CEK/References/CEK_API.md#CustomExtRequestMessage)

* Messaging APIの送信元ユーザのuserId  

  送信元ユーザーの`userId`をご参照ください。  
  [LINE Developers ドキュメント > Messaging API > APIリファレンス > 共通プロパティ > 送信元ユーザー](https://developers.line.me/ja/docs/messaging-api/reference/#anchor-ff6d9a0f9685bb1dfdde749b9044d243cadd542e)

## コードの記述例 {#Example}
以下のようなコードを記述すると、リクエストに発話時のClovaからのリクエストを代入して、LINEメッセージを送信できます。

```js
const line = require('@line/bot-sdk');

const client = new line.Client({
  channelAccessToken: '<channel access token>'
});

const message = {
  type: 'text',
  text: 'Hello World!'
};

client.pushMessage(request.​session.user.userId​​​, message)
  .then(() => {
    ...
  })
  .catch((err) => {
    // error handling
  });​
```
Messaging APIのプッシュメッセージの詳細な仕様については、こちらをご確認ください。  
[LINE Developers ドキュメント > Messaging API > APIリファレンス > プッシュメッセージを送る](https://developers.line.me/ja/docs/messaging-api/reference/#anchor-0c00cb0f42b970892f7c3382f92620dca5a110fc)
​
<div class="note">
  <p><strong>メモ</strong></p>
  <ul>
    <li>Custom Extensionとボットの紐付けは、同一サービスの範囲内でのみ許可されます。</li>
    <li>Custom Extensionとボットの不適切な紐付けが発見された場合は、当該のCustom Extensionを停止します。あらかじめご了承ください。</li>
  </ul>
</div>
