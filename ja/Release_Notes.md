# リリースノート
このページはClovaプラットフォームと文書の変更履歴を提供しています。


# 2018-02-05

* CEK
  - Extension起動の呼び出し([LaunchRequest](CEK/Guides/Build_Custom_Extension.html#HandleLaunchRequest))の説明を修正および[Extensionのデザインガイドラインドキュメントの内容を反映](/Design/Design_Guideline_For_Extension.md)
  - CEKとExtensionの通信に使用される[HTTPプロトコルのバージョン](/CEK/CEK_Overview.md#WhatisCEK)を明示
  - [チュートリアル](/CEK/Tutorials/Introduction.md)ページに[基本的な意思表現を処理する](/CEK/Tutorials/Handle_Builtin_Intents.md)ページを追加

* Clova Developer Center
  - Extensionサーバーで使用する[ポート](/DevConsole/Guides/CEK/Register_Extension.md#SetServerConnection)を明示

* Common
  - 一部のドキュメントの誤りを訂正

# 2018-01-29

* Clova Developer Center
  - [Extensionサーバーとの連携を設定する](/DevConsole/Guides/CEK/Register_Extension.md#SetServerConnection)前に接続を確認する方法を追加および[テスターIDの自動適用](/DevConsole/Guides/CEK/Test_Extension.md#TestOnClovaApp)に関する案内を追加
  - Clova Developer Centerの一部のUIをアップデート

# 2018-01-22

* CEK
  - [チュートリアル](/CEK/Tutorials/Introduction.md)ページと[簡単なExtensionを作成する](/CEK/Tutorials/Build_Simple_Extension.md)ページを追加

* Clova Developer Center
  - [ビルトインインテントのリストの表示](/DevConsole/Guides/CEK/Register_Interaction_Model.md#AddCustomSlotType)、[審査をリクエスト](/DevConsole/Guides/CEK/Deploy_Extension.md#InputComplianceInfo)する際に、審査リクエストのメッセージを作成するUIを追加

* Common
  - UMLダイアグラムの画像フォーマットを変更

# 2018-01-08

* Design
  - プラットフォームの実装状況に合わせて[ビルトインインテント](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)の説明を修正

* CEK
  - [Extensionの例題](/CEK/Examples/Extension_Examples.md)ページを追加

* Clova Developer Center
  - <strong>テスターID</strong>フィールドの追加による[Extensionをテストする](/DevConsole/Guides/CEK/Test_Extension.md)の説明を更新

# 2018-01-02

  * Common
    - 一部のドキュメントの誤りと誤字・脱字を訂正

# 2017-12-18

* Design
  - [Interaction を登録する](/DevConsole/Guides/CEK/Register_Interaction_Model.md)で[interaction を定義する](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)セクションの内容を[Extensionデザインガイドライン](/Design/Design_Guideline_For_Extension.md)ドキュメントに移動
  - [Interaction を定義する](/Design/Design_Guideline_For_Extension.md#DefineInteractionModel)セクションの内容に[サンプル発話](/Design/Design_Guideline_For_Extension.md#UtteranceExample)フレーズの作成ガイドラインを追加

* Clova Developer Center
  - [Extensionをテストする](/DevConsole/Guides/CEK/Test_Extension.md)にテストモードを使用するを追加
  - UIの改善による画像および説明を修正
  - [Extensionをアップデートする](/DevConsole/Guides/CEK/Update_Extension.md)、[Extensionを中止および削除する](/DevConsole/Guides/CEK/Remove_Extension.md)を追加

# 2017-12-11

* Design
  - [Extensionのデザインガイドライン](/Design/Design_Guideline_For_Extension.md)を追加

# 2017-12-04

* CEK
  - ユーザーのマルチターン対話のためにrepromptフィールドを[レスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)に追加
  - 一部のドキュメントのエラーを訂正

# 2017-11-06

* CEK
  - [Custom Extensionメッセージ](/CEK/References/CEK_API.md#CustomExtMessage)のうちリクエストメッセージでcontext.System.device.displayTypeフィールドの名前をcontext.System.device.displayに変更し、サブフィールドの構成を変更

# 2017-10-30

* Clova Developer Center
  - [Clova Developer Centerの概要](/DevConsole/ClovaDevConsole_Overview.md)説明を追加
  - [Extensionを登録する](/DevConsole/Guides/CEK/Register_Extension.md)ガイドを追加
  - [対話モデルを登録する](/DevConsole/Guides/CEK/Register_Interaction_Model.md)ガイドを追加
  - [Extensionを配布する](/DevConsole/Guides/CEK/Deploy_Extension.md)ガイドを追加

# 2017-10-23

* CEK
  - [Custom Extensionメッセージ](/CEK/References/CEK_API.md#CustomExtMessage)のうち、リクエストメッセージにcontext.System.device.displayTypeフィールドを追加

# 2017-10-16

* Common
  - 一部のドキュメントで画像を修正およびドキュメントのエラーを訂正

# 2017-09-04

- Common
  - 一部のドキュメントのエラーを訂正

# 2017-08-14

* CEK
  - [マルチターン対話をする](/CEK/Guides/Build_Custom_Extension.md#DoMultiturnDialog)セクションを追加およびsessionAttributesフィールドの説明を更新

# 2017-07-07

* CEK
  - [Custom Extensionレスポンスメッセージ](/CEK/References/CEK_API.md#CustomExtResponseMessage)の[outputSpeech](/CEK/References/CEK_API.md#CustomExtResponseMessage)オブジェクト構成更新を反映

* Common
  - [用語集を追加](/Terms.md)
  - CEKのメッセージフォーマット部分の目次を更新

# 2017-07-03
* CEK
  - CEKドキュメントの画像を更新

* Common
  - ドキュメントのレビュー結果を反映

# 2017-06-19
* CEK
  - CEKドキュメント部分を作成
