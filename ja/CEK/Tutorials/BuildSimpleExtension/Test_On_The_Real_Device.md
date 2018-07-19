対話モデルが正しく動作することを確認したら、審査をリクエストする前に、実際のデバイスでテストして、音声の認識と応答が想定した通りに動作するか確認する必要があります。
開発しているアカウントで初期化しているClovaデバイスからは、テスターの追加作業を実施しなくてもテストをすることができます。
別のアカウントで初期化したClovaデバイスからスキルをテストしたい場合に以下のドキュメントを参照してください。

* [テスターを登録する](/CEK/Guides/Register_Collaborator.md#RegisterTester)

<div class="danger">
 <p><strong>注意</strong></p>
 <p>Custom Extensionは、現時点ではClova WAVEでは動作確認することができません。</p>
</div>

<div class="danger">
<p><strong>注意</strong></p>
  <p>実際のデバイスでテストするには、<strong>{{ book.DevConsole.cek_skill_info }}</strong>に外部からアクセスできる実際のExtensionサーバーのURLを必ず登録する必要があります。</p></li>
</div>

{% if book.language !== "ja" %}
### Clovaアプリで実行する
ClovaアプリでサンプルサイコロExtensionを実行します。

1. テストするデバイスにClovaアプリをインストールします。
2. テスターIDとして入力した{{ book.OrientedService }}アカウントでログインします。
3. テスト用のExtensionの呼び出し名で、音声指示を出します。例えば、「ねぇClova、サンプルサイコロを起動して」と指示します。
4. Clovaアプリが「サイコロを1つ振ります」と応答するか確認します。

現在、テスター登録はご利用いただけません。
Clova Developer CenterでExtensionを登録したLINEアカウントでログインしているClova端末から、開発中のExtensionを利用可能です。
テスト用のExtensionの呼び出し名で、音声指示を出します。例えば、「ねぇClova、サンプルサイコロを起動して」と指示します。

{% endif %}

Extensionが実際のデバイスでも正しく動作したら、サービスの準備は完了です。Clova Developer Centerで審査をリクエストして、Extensionを配布することができます。
