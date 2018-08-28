サンプルサイコロExtensionがスロットを処理できるように、コードを変更する必要があります。
ここでは、あらかじめ作成されたソースコードを参考にして、どの部分が変更されたかを確認するために、[1番目のチュートリアル](/CEK/Tutorials/Build_Simple_Extension.md)のリポジトリを再び使用します。
次のようにローカルリポジトリにアクセスして、`tutorial3`ブランチに切り替えます。

{% raw %}
```bash
cd /path/to/your_sample_dice_directory
git fetch
git checkout tutorial3
```
{% endraw %}

サンプルサイコロExtensionは、`clova/index.js`ファイルの`intentRequest()`でスロットを処理します。

{% raw %}
```javascript
intentRequest(cekResponse) {
  const intent = this.request.intent.name
  const slots = this.request.intent.slots

  switch (intent) {
    case "ThrowDiceIntent":
      let diceCount = 1
      if (!!slots) {
        const diceCountSlot = slots.diceCount
        if (slots.length != 0 && diceCountSlot) {
          diceCount = parseInt(diceCountSlot.value)
        }

        if (isNaN(diceCount)) {
          diceCount = 1
        }
      }
      ...
  }
  ...
}
```
{% endraw %}

上記のコードでみられるように、Clovaからのリクエストからスロットの情報を抽出(`this.request.intent.slots`)し、先ほど対話モデルに登録した「diceCount」というスロット(`slots.diceCount`)がある場合、その値を整数形式で読み取ります。そうやって読み取った値が振るサイコロの数になります。スロットがなかったり、整数形式でない場合、デフォルト値の1として判断されます。

変更されたコードをExtensionサーバーで実行します。
