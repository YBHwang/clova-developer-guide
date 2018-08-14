# 始める前に

<a target="_blank" href="http://clova.ai">Clova</a>は、NAVERが開発およびサービスを提供しているAIプラットフォームです。ユーザーの音声やイメージを認識し、それを解析して、ユーザーの希望する情報やサービスを提供します。Clovaプラットフォームを使用するサードパーティの開発者は、以下の2つのグループに分けられます。

* [CICプラットフォーム](/CIC/CIC_Overview.md#WhatisCIC)のユーザー：ClovaのAIアシスタントサービスを提供するデバイスまたはアプリを開発するクライアント開発者
* [CEKプラットフォーム](/CEK/CEK_Overview.md#WhatisCEK)のユーザー：保有しているオンラインコンテンツやサービスを、Clovaを介して提供する拡張機能(Extension)の開発者

<div class="note">
  <p><strong>メモ</strong></p>
  <p>金銭の取引や決済が含まれるクライアントやExtension、またはIoTサービスを提供するExtensionを開発する会社や個人は、<a target="_blank" href="https://www.navercorp.com/ko/company/proposalRegister.nhn">NAVERとの提携を提案する</a>ページで、事前に提携を結ぶ必要があります。</p>
</div>

Clovaプラットフォームでは、クライアント開発者とExtension開発者のためにClova Interface Connection(CIC)、Clova Extension Kit(CEK)、そしてClova Developer Centerを提供しています。開発者は、必要に応じて以下のドキュメントを参照します。

<table>
  <thead>
    <tr>
      <th width="12%">区分</th>
      <th width="44%">クライアント開発者</th>
      <th width="44%">Extension開発者</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: center;">概念の理解</td>
      <td>
        <ul>
          <li><a href="/CIC/CIC_Overview.md#WhatisCIC">CICとは?</a></li>
          <li><a href="/CIC/CIC_Overview.md#DialogModel">ダイアログモデル</a></li>
        </ul>
      </td>
      <td>
        <ul>
          <li><a href="/CEK/CEK_Overview.md#WhatisCEK">CEKとは?</a></li>
          <li><a href="/Design/Design_Guideline_For_Extension.md#DefineInteractionModel">対話モデルについて</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align: center;">デザイン</td>
      <td>
        <ul>
          <li><a href="/Design/Design_Guideline_For_Client_Hardware.md">クライアントデバイスのデザインガイドライン</a></li>
        </ul>
      </td>
      <td>
        <ul>
          <li><a href="/Design/Design_Guideline_For_Extension.md">Extensionのデザインガイドライン</a></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align: center;">開発</td>
      <td>
        <ul>
          <li>ガイド</li>
          <ul>
            <li><a href="/CIC/Guides/Interact_with_CIC.md">CICと連携する</a></li>
          </ul>
          <li>リファレンス</li>
          <ul>
            <li><a href="/CIC/References/CIC_API.md">CIC APIリファレンス</a></li>
            <li><a href="/CIC/References/CIC_API.md#CICInterface">CICメッセージのインターフェース</a></li>
            <li><a href="/CIC/References/Content_Templates.md">コンテンツテンプレート</a></li>
            <li><a href="/CIC/References/Clova_Auth_API.md">CIC認証APIのリファレンス</a></li>
          </ul>
        </ul>
      </td>
      <td>
        <ul>
          <li>チュートリアル</li>
          <ul>
            <li><a href="/CEK/Tutorials/Build_Simple_Extension.md">簡単なExtensionを作成する</a></li>
            <li><a href="/CEK/Tutorials/Handle_Builtin_Intents.md">基本的な意思表現を処理する</a></li>
            <li><a href="/CEK/Tutorials/Use_Builtin_Type_Slots.md">ユーザーから入力された情報を活用する</a></li>
          </ul>
          <li>ガイド</li>
          <ul>
            <li><a href="/CEK/Guides/Build_Custom_Extension.md">Custom Extensionを作成する</a></li>
            <li><a href="/CEK/Guides/Build_Clova_Home_Extension.md">Clova Home Extensionを作成する</a></li>
            <li><a href="/CEK/Guides/Link_User_Account.md">ユーザーアカウントをリンクする</a></li>
            <li><a href="/DevConsole/Guides/CEK/Register_Extension.md">Extensionを登録する</a></li>
            <li><a href="/DevConsole/Guides/CEK/Register_Interaction_Model.md">対話モデルを登録する</a></li>
          </ul>
          <li>リファレンス</li>
          <ul>
            <li><a href="/CEK/References/CEK_API.md#CustomExtMessage">Custom Extensionメッセージ</a></li>
            <li><a href="/CEK/References/CEK_API.md#ClovaHomeExtMessage">Clova Home Extensionメッセージ</a></li>
          </ul>
          <li>Extensionサンプル</li>
          <ul>
            <li><a href="/CEK/Examples/Extension_Examples.md#MagicBall">マジックボール(Magic ball)</a></li>
            <li><a href="/CEK/Examples/Extension_Examples.md#RainSound">雨音(Rain sound)</a></li>
            <li><a href="/CEK/Examples/Extension_Examples.md#DiceDrawer">サイコロ遊び(Dice drawer)</a></li>
            <li><a href="/CEK/Examples/Extension_Examples.md#CoinHelper">コインヘルパー(Coin helper)</a></li>
          </ul>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align: center;">配布</td>
      <td>
        <ul>
          <li>クライアントを登録する(追加予定)</li>
        </ul>
      </td>
      <td>
        <ul>
          <li><a href="/DevConsole/Guides/CEK/Deploy_Extension.md">Extensionを配布する</a></li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

<div class="note">
  <p><strong>メモ</strong></p>
  <p>Clovaは、現在も開発が進められています。このドキュメントの内容は随時変更される可能性があります。</p>
</div>
