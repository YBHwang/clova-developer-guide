# このドキュメントについて
このドキュメントは、ClovaのCICとCEKプラットフォームの開発ガイドおよびAPIリファレンスを提供します。対象となる読者は、CICを使用してClovaのサービスと連携するデバイスまたはアプリを開発するクライアント開発者と、CEKを使用したオンラインコンテンツおよびサービスの提供を希望するExtension開発者です。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>Clovaは、現在も開発が進められています。このドキュメントの内容は随時変更される可能性があります。</p>
</div>

## お問い合わせ
ドキュメントの内容に関するお問い合わせは、指定のClova提携担当者、または<a href="{{ book.DeveloperCenterForumURL }}" target="_blank">{{ book.DeveloperCenterName }}フォーラム</a>までお願いします。

## ドキュメントの変更履歴

このドキュメントの変更履歴は、以下のとおりです。

<table>
  <thead>
    <tr>
      <th style="width:10%">新しいバージョンのルール</th><th style="width:10%">以前のバージョンのルール</th><th style="width:15%">配布日時</th><th style="width:75%">変更履歴</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>v3.40.0</td><td>未適用</td><td>2018/09/21</td>
      <td>
        <ul>
          <li>[CIC] コンテンツのMIMEタイプを表すために、<a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a> <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a>のpayloadにformatフィールドを追加</li>
          <li>[CIC] コンテンツを再生するときに、「いいね」および購読機能を処理するために、<a href="/CIC/References/CICInterface/TemplateRuntime">TemplateRuntime</a>名前空間にSubscribeCommandIssued、UnsubscribeCommandIssuedイベントとUpdateLike、UpdateSubscribeディレクティブを追加</li>
          <li>[CIC] コンテンツを再生するときに表示するボタンやコントロールUIの種類を<a href="/CIC/References/CICInterface/TemplateRuntime.html#RenderPlayerInfo">TemplateRuntime.RenderPlayerInfo</a>ディレクティブに追加</li>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">対応デバイス</a>の説明のうち、Actions項目に抜けていたアクション(GetCleaningCycle、GetOpenState、ReleaseMode)を追加</li>
          <li>[CEK] Clovaから送信されるメッセージの検証のために、<a href="/CEK/References/CEK_API.html#HTTPHeader">HTTPヘッダー</a>にSignatureCEKフィールドの説明を追加し、<a href="/CEK/Guides/Build_Custom_Extension.html">Custom Extensionを作成する</a>ドキュメントと<a href="/CEK/Guides/Build_Clova_Home_Extension.html">Clova Home Extensionを作成する</a>ドキュメントに、それぞれリクエストメッセージの検証セクションを追加</li>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html">エラーメッセージ(Error)</a>に<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ActionTemporarilyBlockedError">ActionTemporarilyBlockedError</a>と<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ValueNotSupportedError">ValueNotSupportedError</a>エラーメッセージを追加</li>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">共有オブジェクト</a>に<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#RatioInfoObject">RatioInfoObject</a>オブジェクトを追加</li>
          <li>[Common] 誤りがあった一部のサンプールコードを訂正</li>
          <li>[Common] 誤りがあった一部のリンクを訂正</li>
          <li>[Common] ユーザータッチポイントにある一部のExtensionの表記をスキルに変更(UIのキャプチャ画像を一緒に更新)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.39.0</td><td>未適用</td><td>2018/09/07</td>
      <td>
        <ul>
          <li>[Design] Extensionのデザインガイドラインの<a href="/Design/Design_Guideline_For_Extension.html#SupportedAudioCompressionFormat">プラットフォームでサポートされるオーディオ圧縮形式</a>に、オーディオコンテンツごとのオーディオ属性とラウドネスに関する推奨事項を追加</li>
          <li>[CIC] <a href="/CIC/Guides/Implement_Client_Features.html#HandleAlerts">アラームを処理する</a>セクションのリンクの誤り、サンプルコードの表記の誤りを訂正</li>
          <li>[Common] サンプルの説明で、「yourdomain.com」になっていたサンプルを、ドキュメント作成用のドメイン名である「example.com」に変更</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.38.0</td><td>未適用</td><td>2018/08/29</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.html">クライアントデバイスのデザインガイドライン</a>で<a href="/Design/Design_Guideline_For_Client_Hardware.html#LightColor">ライトの色</a>のRGB値を変更</li>
          <li>[CIC] <a href="/CIC/Guides/Implement_Client_Features.html">クライアントの機能を実装する</a>セクションを追加</li>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">対応デバイス</a>のうち、 ヒーター(HEATER)とサーモスタット(THERMOSTAT)タイプにGetTargetTemperature動作を追加</li>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">共有オブジェクト</a>フィールドで必須/任意の表記を改善</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a>、<a href="/CIC/References/CICInterface/TemplateRuntime.html">TemplateRuntime</a>名前空間で一部のフィールドを更新</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.37.2</td><td>未適用</td><td>2018/08/24</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Alerts.html#StopAlert">Alerts.StopAlert</a>ディレクティブのサンプルで誤りを訂正</li>
          <li>[CIC] 表記による混同を避けるため、<a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a>ディレクティブのinitiator.inputSourceフィールドの説明を修正</li>
          <li>[CEK] <a href="/CEK/References/CEK_API.html#CustomExtMessage">Custom Extensionのメッセージ</a>の<a href="/CEK/References/CEK_API.html#CustomExtEventRequest">EventRequest</a>リクエストタイプのサンプルで誤りを訂正</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.37.1</td><td>未適用</td><td>2018/08/09</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/CIC_Overview.html#DialogModel">ダイアログモデル</a>の説明を補充</li>
          <li>[CEK] <a href="/CEK/Guides/Build_Custom_Extension.html#ProvidingMetaDataForDisplay">オーディオコンテンツのメタデータを提供する</a>セクションで一部の誤字・脱字を訂正</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.37.0</td><td>未適用</td><td>2018/07/23</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.html">クライアントデバイスのデザインガイドライン</a>の<a href="/Design/Design_Guideline_For_Client_Hardware.html#SoundEffect">効果音</a>のうち、Attending状態への遷移に対する効果音を更新</li>
          <li>[CIC] <a href="/CIC/References/Clova_Auth_API.html">CIC認証API</a>の<a href="/CIC/References/Clova_Auth_API.html#RequestAuthorizationCode">認可コードをリクエストする</a>の説明に423 Lockedステータスコードを追加</li>
          <li>[CEK] Clova Home Extension APIからSetFreezerTargetTemperature、 SetFridgeTargetTemperature動作を削除し、 それに関連するインターフェースを削除</li>
          <li>[CEK] Clova Home Extension APIの <a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#SetTargetTemperatureRequest">SetTargetTemperatureRequest</a>にendpointフィールドを追加し、<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#EndpointInfoObject">EndpointInfoObject</a>オブジェクトを追加</li>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">対応デバイス</a>のうち、 換気扇(VENTILATOR)タイプにSetFanSpeed動作を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.36.0</td><td>未適用</td><td>2018/07/09</td>
      <td>
        <ul>
          <li>[Design] Extensionの<a href="/Design/Design_Guideline_For_Extension.html#DefineInvocationName">名前を定義する</a>のガイドラインを追加</li>
          <li>[Design] Extensionの<a href="/Design/Design_Guideline_For_Extension.html#ContentGuideline">コンテンツ提供時の遵守事項</a>に関するガイドラインを追加</li>
          <li>[CIC] クライアントデバイスの設定を更新および同期するために、<a href="/CIC/References/CICInterface/Settings.html">Settings</a>名前空間を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.35.0</td><td>v4.6</td><td>2018/06/25</td>
      <td>
        <ul>
          <li>[Design] Extensionの<a href="/Design/Design_Guideline_For_Extension.html#DecideSoundOutputType">応答タイプ</a>のガイドラインを追加</li>
          <li>[CEK] Custom Extensionを作成するドキュメントに<a href="/CEK/Guides/Build_Custom_Extension.html#ProvideAudioContent">オーディオコンテンツを提供する</a>セクションを追加</li>
          <li>[CEK] Custom Extensionのメッセージの<a href="/CEK/References/CEK_API.html#CustomExtRequestType">リクエストタイプ</a>に<a href="/CEK/References/CEK_API.html#CustomExtEventRequest">EventRequestタイプ</a>を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.34.2</td><td>v4.5</td><td>2018/06/17</td>
      <td>
        <ul>
          <li>[CIC] リアルタイム配信コンテンツを区別するために、<a href="/CIC/References/CICInterface/TemplateRuntime.html#RenderPlayerInfo">TemplateRuntime.RenderPlayerInfo</a>にisLiveフィールドを追加</li>
          <li>[CEK] <a href="/CIC/References/Content_Templates.html">コンテンツテンプレート</a>の<a href="/CIC/References/ContentTemplates/Common_Fields.html">共通フィールド</a>にsubtitleフィールドを追加</li>
          <li>[CEK] 赤外線通信でコントロールするデバイスのために、Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">ApplianceInfoObject</a>にisIrフィールドを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.34.1</td><td>v4.4</td><td>2018/05/28</td>
      <td>
        <ul>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ConditionsNotMetError">ConditionsNotMetError</a>にstateフィールドを追加</li>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#TVChannelInfoObject">TVChannelInfoObject</a>にサブチャンネルの情報を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.34.0</td><td>v4.3</td><td>2018/05/21</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a>コンテキストオブジェクトの<a href="/CIC/References/Context_Objects.html#BluetoothInfoObject">BluetoothInfoObject</a>に抜け落ちの(btlist[].role)を追加</li>
          <li>[CEK] Clova Home Extension APIに<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ValueNotFoundError">ValueNotFoundError</a>を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.33.0</td><td>v4.2</td><td>2018/05/14</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Clova.html#LaunchURI">LaunchURI</a>ディレクティブをDeviceControl名前空間から<a href="/CIC/References/CICInterface/Clova.html">Clova</a>名前空間に移動</li>
          <li>[CEK] HTTPリクエストメッセージにヘッダー(SignatureCEK、SignatureCEKCertChainUrl)を追加およびリクエストメッセージを検証するセクションを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.32.0</td><td>v4.1</td><td>2018/05/07</td>
      <td>
        <ul>
          <li>[CIC] DeviceControl名前空間にLaunchURIディレクティブを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a>名前空間の<a href="/CIC/References/CICInterface/DeviceControl.html#LaunchApp">LaunchApp</a>ディレクティブと<a href="/CIC/References/CICInterface/DeviceControl.html#OpenScreen">OpenScreen</a>ディレクティブのサポートを中断(Deprecated)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.31.0</td><td>v4.0</td><td>2018/04/30</td>
      <td>
        <ul>
          <li>[CEK] Clova Home extension APIに<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetOpenStateRequest">GetOpenStateRequest</a>、<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetOpenStateResponse">GetOpenStateResponse</a>を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.30.0</td><td>v3.9</td><td>2018/04/23</td>
      <td>
        <ul>
          <li>[CEK] Clova Home extension APIに<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#ReleaseModeConfirmation">ReleaseModeConfirmation</a>、<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#ReleaseModeRequest">ReleaseModeRequest</a>を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.29.0</td><td>v3.8</td><td>2018/04/16</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a>イベントのwakeWordフィールドの説明およびAudio dataの説明を更新</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a>名前空間に<a href="/CIC/References/CICInterface/DeviceControl.html#Open">Open</a>ディレクティブを追加</li>
          <li>[CEK] Clova Home extension APIの<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetLockStateResponse">GetLockStateResponse</a>にopenStateフィールドを追加</li>
          <li>[CEK] Clova Home extension APIに<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetCleaningCycleRequest">GetCleaningCycleRequest</a>、<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetCleaningCycleResponse">GetCleaningCycleResponse</a>を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.28.1</td><td>v3.7</td><td>2018/04/09</td>
      <td>
        <ul>
          <li>[CIC] クライアントデバイスのデザインガイドラインで、<a href="Design/Design_Guideline_For_Client_Hardware.html#BootingScreen">起動画面</a>に関する説明およびサンプル画像を更新</li>
          <li>[CEK] Clova Home extension APIの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ColorInfoObject">ColorInfoObject</a>のbrightnessフィールドの説明および必須有無を変更</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.28.0</td><td>v3.6</td><td>2018/04/02</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a>名前空間にメッセージ仕様を追加および一部のフィールドを更新
            <ul>
              <li><a href="/CIC/References/CICInterface/AudioPlayer.html#ExpectReportPlaybackState">AudioPlayer.ExpectReportPlaybackState</a>ディレクティブ、<a href="/CIC/References/CICInterface/AudioPlayer.html#ReportPlaybackState">AudioPlayer.ReportPlaybackStateイベント</a>{% if book.TargetReaderType == "Internal" %}、<a href="/CIC/References/CICInterface/AudioPlayer.html#RequestPlaybackState">AudioPlayer.RequestPlaybackState</a>イベント、<a href="/CIC/References/CICInterface/AudioPlayer.html#SynchronizePlaybackState">SynchronizePlaybackStateディレクティブ</a>{% endif %}を追加</li>
              <li><a href="/CIC/References/CICInterface/AudioPlayer.html#Play">AudioPlayer.Play</a>ディレクティブのpayloadフィールドの内容を更新</li>
              <li>ProgressReportXXX、PlayXXXの形式の名前を持っているイベントフィールドにtokenフィールド値を必須として追加</li>
            </ul>
          </li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.html#PlaybackState">AudioPlayer.PlaybackState</a>コンテキストオブジェクトにrepeatModeを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController</a>名前空間に、全部で12件のメッセージ仕様を追加
            <ul>
              <li><a href="/CIC/References/CICInterface/PlaybackController.html#PauseCommandIssued">PlaybackController.PauseCommandIssued</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#PlayCommandIssued">PlaybackController.PlayCommandIssued</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#ResumeCommandIssued">PlaybackController.ResumeCommandIssued</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#SetRepeatModeCommandIssued">PlaybackController.SetRepeatModeCommandIssued</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#StopCommandIssued">PlaybackController.StopCommandIssued</a>イベントを追加</li>
              <li><a href="/CIC/References/CICInterface/PlaybackController.html#ExpectNextCommand">PlaybackController.ExpectNextCommand</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#ExpectPauseCommand">PlaybackController.ExpectPauseCommand</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#ExpectPlayCommand">PlaybackController.ExpectPlayCommand</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#ExpectPreviousCommand">PlaybackController.ExpectPreviousCommand</a>、
<a href="/CIC/References/CICInterface/PlaybackController.html#ExpectResumeCommand">PlaybackController.ExpectResumeCommand</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#ExpectStopCommand">PlaybackController.ExpectStopCommand</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#SetRepeatMode">PlaybackController.SetRepeatMode</a>ディレクティブを追加</li>
              <li><a href="/CIC/References/CICInterface/PlaybackController.html#TurnOnRepeatMode">PlaybackController.TurnOnRepeatMode</a>ディレクティブと<a href="/CIC/References/CICInterface/PlaybackController.html#TurnOffRepeatMode">PlaybackController.TurnOffRepeatMode</a>は削除予定</li>
            </ul>
          </li>
          <li>[CIC] メディアストリームのための情報と、プレイリストを表示するための再生メタデータを分離するため、<a href="/CIC/References/CICInterface/TemplateRuntime.html">TemplateRuntime</a>名前空間を追加</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a>の<a href="/CIC/References/Context_Objects.html#BluetoothInfoObject">BluetoothInfoObject</a>にscanlistフィールドを追加</li>
          <li>[CIC] PINコードを使用する外部のBluetoothデバイスと接続できるように、<a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a>名前空間に<a href="/CIC/References/CICInterface/DeviceControl.html#BtConnectByPINCode">BtConnectByPINCode</a>ディレクティブと<a href="/CIC/References/CICInterface/DeviceControl.html#BtRequestForPINCode">BtRequestForPINCode</a>、<a href="/CIC/References/CICInterface/DeviceControl.html#BtRequestToCancelPinCodeInput">BtRequestToCancelPinCodeInput</a>イベントを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a>名前空間の<a href="/CIC/References/CICInterface/DeviceControl.html#BtConnect">BtConnect</a>ディレクティブにpayloadを追加</li>
          <li>[CEK] Clova Home Extension APIにGetSleepStartTimeRequestの他9件の<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control API</a>と4件の<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">共有オブジェクト</a>を追加</li>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Discovery_Interfaces.html#DiscoverAppliancesResponse">DiscoverAppliancesResponse</a>に<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#CustomCommandInfoObject">CustomCommandInfoObject</a>を追加</li>
          <li>[CEK] Clova Home Extension APIからTimeAmountInfoObject<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">共有オブジェクト</a>を削除およびそれに伴って<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control API</a>の一部の内容を変更</li>
          <li>[CEK] Clova Home Extension APIの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">ApplianceInfoObject</a>にtagsフィールドを追加およびlocationフィールドの説明を変更</li>
          <li>[Dev.Console] Clova Developer Centerの一部のUIを更新</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.27.0</td><td>v3.5</td><td>2018/03/19</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a>に<a href="/CIC/References/Context_Objects.html#SoundOutputInfoObject">SoundOutputInfoObject</a>を追加</li>
          <li>[CIC] ユーザーが設定した任意のコマンドを実行する<a href="/CIC/References/CICInterface/PlaybackController.html#CustomCommandIssued">CustomCommandIssued</a>イベントを<a href="/CIC/References/CICInterface/PlaybackController.html#CustomCommandIssued">PlaybackController</a>名前空間に追加</li>
          <li>[CEK] Clova Home Extension  APIにCloseConfirmationの他47件の<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control API</a>とおよそ10種類の<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">共有オブジェクト</a>を追加</li>
          <li>[CEK] Clova Home Extension  API<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">対応デバイス</a>を30種類追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.26.0</td><td>v3.4</td><td>2018/03/05</td>
      <td>
        <ul>
          <li>[CIC] <a  href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a>イベントのinitiatorフィールドの説明を修正</li>
          <li>[CIC] <a href="/Design/Design_Guideline_For_Client_Hardware.html">クライアントデバイスのデザインガイドライン</a>で、クライアントのステータスのうち、Hearingステータスの名前をListeningに修正</li>
          <li>[CIC] クライアントデバイスのデザインガイドラインの<a href="/Design/Design_Guideline_For_Client_Hardware.html#Audio">音声</a>で、オーディオコンテンツのタイプにFeedbackタイプを追加し、説明に関連ルールを追加</li>
          <li>[CEK] <a href="/CEK/Tutorials/Introduction.html">チュートリアル</a>ページに<a href="/CEK/Tutorials/Use_Builtin_Type_Slots.html">ユーザーから入力された情報を活用する</a>ページを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.25.0</td><td>v3.3</td><td>2018/02/26</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a>イベントのinitiatorフィールドにdeviceUUIDフィールドを追加</li>
          <li>[CIC] アラームの同期に関連する<a href="/CIC/References/CICInterface/Alerts.html#RequestSynchronizeAlert">RequestSynchronizeAlert</a>イベントと<a href="/CIC/References/CICInterface/Alerts.html#SynchronizeAlert">SynchronizeAlert</a>ディレクティブを<a href="/CIC/References/CICInterface/Alerts.html">Alerts</a>名前空間に追加</li>
          <li>[CIC] System名前空間から、アラームの同期に関連する一部のフィールドを削除する予定</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.24.0</td><td>v3.2</td><td>2018/02/19</td>
      <td>
        <ul>
          <li>[CIC] ユーザーの呼び出しを正確に認識するため、<a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a>イベントにinitiatorフィールドを追加</li>
          <li>[CIC] リマインダーおよびアクション予約の内容を確認するため、<a href="/CIC/References/CICInterface/Alerts.html#SetAlert">Alerts.SetAlert</a>ディレクティブにlabelフィールドを追加</li>
          <li>[CIC] リマインダーおよびアクション予約の内容を表示するため、<a href="/CIC/References/ContentTemplates/ActionTimer.html">ActionTimer</a>、<a href="/CIC/References/ContentTemplates/ActionTimerList.html">ActionTimerList</a>、<a href="/CIC/References/ContentTemplates/Reminder.html">Reminder</a>、<a href="/CIC/References/ContentTemplates/ReminderList.html">ReminderList</a>テンプレートにlabelフィールドを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.23.0</td><td>v3.1</td><td>2018/02/05</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a>のdurationInMillisecondsフィールドの説明を修正</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Atmosphere.html">Atmosphere</a>、<a href="/CIC/References/ContentTemplates/CardList.html">CardList</a>、<a href="/CIC/References/ContentTemplates/Humidity.html">Humidity</a>、<a href="/CIC/References/ContentTemplates/TodayWeather.html">TodayWeather</a>、<a href="CIC/References/ContentTemplates/TomorrowWeather.html">TomorrowWeather</a>、<a href="/CIC/References/ContentTemplates/WeeklyWeather.html">WeeklyWeather</a>、<a href="CIC/References/ContentTemplates/WindSpeed.html">WindSpeed</a>テンプレートにコンテンツの提供元に関連するフィールドなどの内容を追加</li>
          <li>[CEK] Extensionを開始する呼び出し(<a href="CEK/Guides/Build_Custom_Extension.html#HandleLaunchRequest">LaunchRequest</a>)の説明を修正および<a href="/Design/Design_Guideline_For_Extension.html">Extensionのデザインガイドラインドキュメントに反映</a></li>
          <li>[CEK] CEKとExtension間の通信に使用される<a href="/CEK/CEK_Overview.html#WhatisCEK">HTTPプロトコルのバージョン</a>を明記</li>
          <li>[CEK] <a href="/CEK/Tutorials/Introduction.html">チュートリアル</a>ページに<a href="/CEK/Tutorials/Handle_Builtin_Intents.html">基本的な意思表現を処理する</a>ページを追加</li>
          <li>[Dev.Console] Extensionサーバーで使用すべき<a href="/DevConsole/Guides/CEK/Register_Extension.html#SetServerConnection">ポート</a>を明記</li>
          <li>[Common] 一部のドキュメントの誤りを訂正</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.22.0</td><td>v3.0</td><td>2018/01/29</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.html">クライアントデバイスのデザインガイドライン</a>に<a href="/Design/Design_Guideline_For_Client_Hardware.html#SoundEffect">リマインダーのための効果音</a>を追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/Notifier.html">Notifier</a>名前空間に<a href="/CIC/References/CICInterface/Notifier.html#Notify">Notifier.Notify</a>イベントを追加およびその名前空間で使用されるメッセージのpayloadフィールドを更新</li>
          <li>[CIC] <a href="/CIC/References/ContextObjects/SpeechState.html">SpeechSynthesizer.SpeechState</a>および<a href="/CIC/References/CICInterface/SpeechSynthesizer.html">SpeechSynthesizer</a>名前空間に<a href="/CIC/References/CICInterface/SpeechSynthesizer.html#SpeechFinished">SpeechFinished</a>、<a href="/CIC/References/CICInterface/SpeechSynthesizer.html#SpeechStarted">SpeechStarted</a>、<a href="/CIC/References/CICInterface/SpeechSynthesizer.html#SpeechStopped">SpeechStopped</a>イベントを追加</li>
          <li>[CIC] マルチターン対話のため、<a href="/CIC/References/CICInterface/TextRecognizer.html">TextRecognizer.Recognize</a>イベントにspeechId、explicitフィールドを追加</li>
          <li>[CEK] Clova Home extensionメッセージリファレンスの<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html">Errorインターフェース</a>に、<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#NoSuchTargetError">NoSuchTargetError</a>、<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#NotSupportedInCurrentModeError">NotSupportedInCurrentModeError</a>、<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#UnsupportedOperationError">UnsupportedOperationError</a>および<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ValueOutOfRangeError">ValueOutOfRangeError</a>を追加</li>
          <li>[Dev.Console] <a href="/DevConsole/Guides/CEK/Register_Extension.html#SetServerConnection">Extensionサーバーとの連携を設定する</a>前に接続を確認する方法および<a href="/DevConsole/Guides/CEK/Test_Extension.html#TestOnClovaApp">テスターID適用の自動化</a>の案内を追加</li>
          <li>[Dev.Console] Clova Developer Centerの一部のUIを更新</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.21.0</td><td>v2.9</td><td>2018/01/22</td>
      <td>
        <ul>
          <li>[Design] プラットフォームでサポートされる音声圧縮形式を<a href="/Design/Design_Guideline_For_Client_Hardware.html#SupportedAudioCompressionFormat">クライアントデバイスのデザインガイドライン</a>および<a href="/Design/Design_Guideline_For_Extension.html#SupportedAudioCompressionFormat">Extensionのデザインガイドライン</a>に追加</li>
          <li>[CEK] <a href="/CEK/Tutorials/Introduction.html">チュートリアル</a>ページと<a href="/CEK/Tutorials/Build_Simple_Extension.html">簡単なExtensionを作成する</a>ページを追加</li>
          <li>[Dev.Console] <a href="/DevConsole/Guides/CEK/Register_Interaction_Model.html#AddCustomSlotType">ビルトインインテントリストの表示</a>、<a href="/DevConsole/Guides/CEK/Deploy_Extension.html#InputComplianceInfo">審査をリクエストする</a>際に、審査リクエストのメッセージを作成するUIを追加</li>
          <li>[Common] UMLダイアグラムの画像フォーマットを変更</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.20.0</td><td>v2.8</td><td>2018/01/15</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.html">クライアントデバイスのデザインガイドライン</a>にアラーム、リマインダー、タイマーの照明効果および効果音のガイドラインの説明を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.19.0</td><td>v2.7</td><td>2018/01/08</td>
      <td>
        <ul>
          <li>[Design] プラットフォームの実装状況に合わせて<a href="/Design/Design_Guideline_For_Extension.html#DefineInteractionModel">ビルトインインテント</a>の説明を修正</li>
          <li>[CIC] <a href="/CIC/Guides/Implement_Client_Features.html#HandleDelegation">委任されたユーザーのリクエストを処理する</a>セクションを追加および<a href="/CIC/References/CICInterface/Clova.html#HandleDelegatedEvent">Clova.HandleDelegatedEvent</a>ディレクティブと<a href="/CIC/References/CICInterface/Clova.html#ProcessDelegatedEvent">Clova.ProcessDelegatedEvent</a>イベントを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/PlaybackController.html#NextCommandIssued">PlaybackController.NextCommandIssued</a>と<a href="/CIC/References/CICInterface/PlaybackController.html#PreviousCommandIssued">PlaybackController.PreviousCommandIssued</a>イベントに<a href="/CIC/References/Context_Objects.html#PlaybackState">AudioPlayer.PlaybackState</a>コンテキストを含めるように説明を追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/Alerts.html">Alerts</a> APIの仕組みの説明を改善</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a> APIの<a href="/CIC/References/CICInterface/DeviceControl.html#DeviceContorlWorkFlow">仕組み</a>の説明を追加</li>
          <li>[CIC] 一部のコンテンツテンプレートおよび共有オブジェクトの誤りの訂正内容を修正</li>
          <li>[CEK] <a href="/CEK/Examples/Extension_Examples.html">Extensionのサンプル</a>ページを追加</li>
          <li>[Dev.Console] <strong>テスターID</strong>フィールドの追加による<a href="/DevConsole/Guides/CEK/Test_Extension.html">Extensionをテストする</a>の説明を更新</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.18.1</td><td>v2.6</td><td>2018/01/02</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CIC_API.html#EstablishDownchannel">ダウンチャネルを構成する</a>セクションに429エラーコードおよび関連説明を備考に追加</li>
          <li>[CIC] ルート検索のテンプレート(CarRoute, TransportationRoute)を削除、ルート検索のUI表現をImageTextテンプレートで代替</li>
          <li>[Common] 一部のドキュメントの誤り、誤字・脱字を訂正</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.18.0</td><td>v2.5</td><td>2017/12/18</td>
      <td>
        <ul>
          <li>[Design] <a href="/DevConsole/Guides/CEK/Register_Interaction_Model.html">対話モデルを登録する</a>で<a href="/Design/Design_Guideline_For_Extension.html#DefineInteractionModel">対話モデルを定義する</a>セクションの内容を<a href="/Design/Design_Guideline_For_Extension.html">Extensionデザインガイドライン</a>ドキュメントに移動</li>
          <li>[Design] <a href="/Design/Design_Guideline_For_Extension.html#DefineInteractionModel">対話モデルを定義する</a>セクションの内容に<a href="/Design/Design_Guideline_For_Extension.html#UtteranceExample">サンプル発話</a>フレーズの作成ガイドラインを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.html">SpeechRecognizer</a>インターフェースからExpectSpeechTimedOutイベントを削除</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.html">コンテキスト</a>からClova.FreetalkStateオブジェクトを削除</li>
          <li>[Dev.console] <a href="/DevConsole/Guides/CEK/Test_Extension.html">Extensionをテストする</a>にテストモードを使用するを追加</li>
          <li>[Dev.console] UIの改善による画像および説明を修正</li>
          <li>[Dev.console] <a href="/DevConsole/Guides/CEK/Update_Extension.html">Extensionをアップデートする</a>、<a href="/DevConsole/Guides/CEK/Remove_Extension.html">Extensionを中止および削除する</a>を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.17.0</td><td>v2.4</td><td>2017/12/11</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Extension.html">Extensionのデザインガイドライン</a>を追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a>インターフェースに<a href="/CIC/References/CICInterface/AudioPlayer.html#ClearQueue">ClearQueue</a>ディレクティブを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.16.0</td><td>v2.3</td><td>2017/12/04</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.html#AudioInterruptionRule">オーディオ再生のルール(audio interruption rule)</a>を<a href="/Design/Design_Guideline_For_Client_Hardware.html">クライアントデバイスのデザインガイドライン</a>に追加</li>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.html">クライアントデバイスのデザインガイドライン</a>の画像を改善</li>
          <li>[CIC] CICと連携するための事前準備に<a href="/CIC/Guides/Interact_with_CIC.html#UserAgentString">User-Agent string</a>を追加</li>
          <li>[CIC] <a href="/CIC/References/CIC_API.html">CIC APIリファレンス</a>の<a href="/CIC/References/CIC_API.html#SendEvent">イベントを送信する</a>セクションに、412 Precondition Failedステータスコードの説明を追加</li>
          <li>[CEK] ユーザーのマルチターン対話のため、repromptフィールドを<a href="/CEK/References/CEK_API.html#CustomExtResponseMessage">レスポンスメッセージ</a>に追加</li>
          <li>[CEK] 一部のドキュメントの誤りを訂正</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.15.0</td><td>v2.2</td><td>2017/11/20</td>
      <td>
        <ul>
          <li>[Design] <a href="/Design/Design_Guideline_For_Client_Hardware.html">クライアントデバイスのデザインガイドライン</a>を追加</li>
          <li>[CIC] オーディオコンテンツおよび画像のサムネイル表示のため<a href="/CIC/References/ContentTemplates/CardList.html">CardListテンプレート</a>のsubType値にType5、Type6を追加</li>
          <li>[CEK] Clova Home Extensionメッセージの<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html">共有オブジェクト</a>のHeatingModeInfoObjectを<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ModeInfoObject">ModeInfoObject</a>に名前を変更し、汎用的なデバイスの運転モードを示すオブジェクトに説明を修正</li>
          <li>[CEK] Clova Home Extensionメッセージの<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control</a>インターフェースに<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetCurrentTemperatureRequest">GetCurrentTemperatureRequest</a>メッセージと<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html#GetCurrentTemperatureResponse">GetCurrentTemperatureResponse</a>メッセージを追加</li>
          <li>[CEK] Clova Home Extensionメッセージの<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html">Error</a>インターフェースに<a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#UnsupportedOperationError">UnsupportedOperationError</a>メッセージを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.14.0</td><td>v2.1</td><td>2017/11/13</td>
      <td>
        <ul>
          <li>[CIC] ボリュームのコントロールに関連するディレクティブ(<a href="/CIC/References/CICInterface/DeviceControl.html#Decrease">DeviceControl.Decrease</a>、<a href="/CIC/References/CICInterface/DeviceControl.html#Increase">DeviceControl.Increase</a>、<a href="/CIC/References/CICInterface/DeviceControl.html#SetValue">DeviceControl.SetValue</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#Mute">PlaybackController.Mute</a>、<a href="/CIC/References/CICInterface/PlaybackController.html#Unmute">PlaybackController.Unmute</a>)の備考にUX関連内容を追加</li>
          <li>[CEK] <a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">ApplianceInfoObject</a>のエアコンタイプ(AIRCONDITIONER)にDecrementFanSpeed、IncrementFanSpeed、SetFanSpeed、SetModeアクションを、加湿器タイプ(HUMIDIFIER)にSetFanSpeedを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.13.0</td><td>v2.0</td><td>2017/11/06</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.html#KeepRecording">SpeechRecognizer.KeepRecording</a>ディレクティブを追加</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.html#Display">Device.Display</a>コンテキストを追加</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/ActionTimer.html">ActionTimer</a>、<a href="/CIC/References/ContentTemplates/ActionTimerList.html">ActionTimerList</a>、<a href="/CIC/References/ContentTemplates/Alarm.html">Alarm</a>、<a href="/CIC/References/ContentTemplates/AlarmList.html">AlarmList</a>、<a href="/CIC/References/ContentTemplates/Memo.html">Memo</a>、<a href="/CIC/References/ContentTemplates/MemoList.html">MemoList</a>、<a href="/CIC/References/ContentTemplates/Reminder.html">Reminder</a>、<a href="/CIC/References/ContentTemplates/ReminderList.html">ReminderList</a>、<a href="/CIC/References/ContentTemplates/Schedule.html">Schedule</a>、<a href="/CIC/References/ContentTemplates/ScheduleList.html">ScheduleList</a>、<a href="/CIC/References/ContentTemplates/Timer.html">Timer</a>、<a href="/CIC/References/ContentTemplates/TimerList.html">TimerList</a>テンプレートにtokenフィールドを追加</li>
          <li>[CEK] <a href="/CEK/References/CEK_API.html#CustomExtMessage">Custom Extensionのメッセージ</a>のうち、リクエストメッセージのcontext.System.device.displayTypeフィールドの名前をcontext.System.device.displayに変更し、サブフィールドの構成を変更</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.12.0</td><td>v1.9</td><td>2017/10/30</td>
      <td>
        <ul>
          <li>[Dev.console] <a href="/DevConsole/ClovaDevConsole_Overview.html">Clova Developer Centerの概要</a>の説明を追加</li>
          <li>[Dev.console] <a href="/DevConsole/Guides/CEK/Register_Extension.html">Extensionを登録する</a>ガイドを追加</li>
          <li>[Dev.console] <a href="/DevConsole/Guides/CEK/Register_Interaction_Model.html">対話モデルを登録する</a>ガイドを追加</li>
          <li>[Dev.console] <a href="/DevConsole/Guides/CEK/Deploy_Extension.html">Extensionを配布する</a>ガイドを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.11.0</td><td>v1.8</td><td>2017/10/23</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Text.html">Text</a>テンプレートにemotionCodeフィールドとmotionCodeフィールドを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/Alerts.html#SetAlert">Alerts.SetAlert</a>ディレクティブのassets[].urlフィールドの内容を変更</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html#StreamRequested">AudioPlayer.StreamRequested</a>イベントのサンプルのエラーを訂正</li>
          <li>[CEK] <a href="/CEK/References/CEK_API.html#CustomExtMessage">Custom Extensionのメッセージ</a>のうち、リクエストメッセージにcontext.System.device.displayTypeフィールドを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.10.0</td><td>v1.7</td><td>2017/10/16</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController</a>名前空間に<a href="/CIC/References/CICInterface/PlaybackController.html#Replay">Replay</a>ディレクティブを追加</li>
          <li>[CIC] アラーム同期の補足説明をアラームの仕組みセクションに追加</li>
          <li>[CIC] contentフィールドを<a href="/CIC/References/Context_Objects.html#AlertsState">Alert.AlertsState</a>コンテキストの<a href="/CIC/References/Context_Objects.html#AlertInfoObject">AlertInfoObject</a>から削除</li>
          <li>[共通] 一部のドキュメントで画像を修正およびドキュメントのエラーを訂正</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.9.0</td><td>v1.6</td><td>2017/10/02</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Alerts.html">Alerts</a>名前空間およびアラーム関連インターフェースを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/System.html">System</a>名前空間およびアラーム関連インターフェースを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.html#ExpectSpeech">SpeechRecognizer.ExpectSpeech</a>ディレクティブにexpectContentTypeフィールドを追加</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a>の<a href="/CIC/References/Context_Objects.html#VolumeInfoObject">VolumeInfoObject</a>にwarningフィールドを追加</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/ActionTimer.html">ActionTimer</a>、<a href="/CIC/References/ContentTemplates/ActionTimerList.html">ActionTimerList</a>、<a href="/CIC/References/ContentTemplates/Alarm.html">Alarm</a>、<a href="/CIC/References/ContentTemplates/AlarmList.html">AlarmList</a>、<a href="/CIC/References/ContentTemplates/Memo.html">Memo</a>、<a href="/CIC/References/ContentTemplates/MemoList.html">MemoList</a>、<a href="/CIC/References/ContentTemplates/Reminder.html">Reminder</a>、<a href="/CIC/References/ContentTemplates/ReminderList.html">ReminderList</a>、<a href="/CIC/References/ContentTemplates/Schedule.html">Schedule</a>、<a href="/CIC/References/ContentTemplates/ScheduleList.html">ScheduleList</a>、<a href="/CIC/References/ContentTemplates/Timer.html">Timer</a>、<a href="/CIC/References/ContentTemplates/TimerList.html">TimerList</a>テンプレートを追加</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/ImageText.html">ImageText</a>テンプレートの一部のコードサンプルを修正</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Popup.html">Popupテンプレート</a>の一部のフィールドを修正</li>
          <li>[CIC] <a href="/CIC/Guides/Interact_with_CIC.html#CreateClovaAccessToken">Clovaアクセストークンを作成する</a>と<a href="/CIC/References/Clova_Auth_API.html#RequestAuthorizationCode">認可コードをリクエストする</a>にサービスの利用規約に関する内容を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.8.0</td><td>v1.5</td><td>2017/09/25</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController API</a>にオーディオ再生コントロールのための<a href="/CIC/References/CICInterface/PlaybackController.html#NextCommandIssued">PlaybackController.NextCommandIssued</a>イベントと<a href="/CIC/References/CICInterface/PlaybackController.html#PreviousCommandIssued">PlaybackController.PreviousCommandIssued</a>イベントを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.html#ExpectSpeech">SpeechRecognizer.ExpectSpeech</a>ディレクティブにexpectSpeechIdフィールドを、<a href="/CIC/References/CICInterface/SpeechRecognizer.html#Recognize">SpeechRecognizer.Recognize</a>イベントにspeechIdとexplicitフィールドを追加</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Popup.html">Popupテンプレート</a>を追加</li>
          <li>[CEK] Clova Home Extension APIにChargeConfirmationの他33件の<a href="/CEK/References/ClovaHomeInterface/Control_Interfaces.html">Control API</a>を追加</li>
          <li>[CEK] Clova Home Extension API<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">対応デバイス</a>を6種類追加およびlocationフィールドを追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.7.0</td><td>v1.4</td><td>2017/09/18</td>
      <td>
        <ul>
          <li>[CIC] DeviceControl APIに<a href="/CIC/References/CICInterface/DeviceControl.html#ExpectReportState">DeviceControl.ExpectReportState</a>ディレクティブ、<a href="/CIC/References/CICInterface/DeviceControl.html#ReportState">DeviceControl.ReportState</a>イベント、<a href="/CIC/References/CICInterface/DeviceControl.html#RequestStateSynchronization">DeviceControl.RequestStateSynchronization</a>イベントを追加およびDeviceControl.UpdateDeviceStateディレクティブを<a href="/CIC/References/CICInterface/DeviceControl.html#SynchronizeState">DeviceControl.SynchronizeState</a>に名前を変更</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Text.html">Text</a>テンプレートにitem3フィールドを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html#Play">AudioPlayer.Play</a>ディレクティブに、コンテンツの提供元に関連するsourceフィールドを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a>のdurationInMillisecondsフィールドを追加</li>
          <li>[CIC] Notifier名前空間および<a href="/CIC/References/CICInterface/Notifier.html#ClearIndicator">ClearIndicator</a>、<a href="/CIC/References/CICInterface/Notifier.html#SetIndicator">SetIndicator</a>ディレクティブを追加</li>
          <li>[CIC] <a href="/CIC/References/ContentTemplates/Atmosphere.html">空気情報(Atmosphere)テンプレート</a>を追加</li>
          <li>[CIC] ライセンス問題により、天気テンプレートのbgClipURLフィールドを使用できないという内容を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.6.0</td><td>v1.3</td><td>2017/09/11</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/SpeechRecognizer.html#ExpectSpeech">SpeechRecognizer.ExpectSpeech</a>ディレクティブにexplicitフィールドを追加</li>
          <li>[CIC] <a href="/CIC/References/Content_Templates.html">コンテンツテンプレート</a>に<a href="/CIC/References/ContentTemplates/Common_Fields.html">共通フィールド</a>の仕様を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.5.0</td><td>v1.2</td><td>2017/09/04</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Clova.html#Help">Clova.Help</a>ディレクティブを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.html#LaunchApp">DeviceControl.LaunchApp</a>ディレクティブを追加</li>
          <li>[CIC] TextRecognizer名前空間および<a href="/CIC/References/CICInterface/TextRecognizer.html">TextRecognizer.Recognize</a>イベントを追加</li>
          <li>[CIC] <a href="/CIC/References/CIC_API.html">CIC API</a>、<a href="/CEK/References/CEK_API.html">CEK API</a>の目次、説明を再作成</li>
          <li>[CIC] CIC APIの内容を更新：リクエスト/レスポンスヘッダーのステータスコードを追加、REST APIのリファレンスドキュメント形式を適用</li>
          <li>[その他] 一部のドキュメントの誤りを訂正</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.4.0</td><td>v1.1</td><td>2017/08/28</td>
      <td>
        <ul>
          <li>[CIC] セットトップボックスのためのテレビチャンネル情報の仕様と電源状態情報の仕様を<a href="/CIC/References/Context_Objects.html#DeviceState">Device.DeviceState</a>と<a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl API</a>に追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl API</a>でtargetに使用される値を一部追加および変更：power、energysave、screenbrightness</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl API</a>のSetPointを<a href="/CIC/References/CICInterface/DeviceControl.html#SetValue">SetValue</a>に名前を変更</li>
          <li>[CIC] <a href="/CIC/References/Clova_Auth_API.html">Clova認証API</a>の内容を更新 - リクエスト/レスポンスヘッダーとステータスコードを追加、REST APIのリファレンスドキュメント形式を適用</li>
          <li>[CEK] <a href="/CEK/References/ClovaHomeInterface/Error_Interfaces.html#ValueOutOfRangeError">ValueOutOfRangeError</a>をClova HomeのErrorインターフェースに追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.3.0</td><td>v1.0</td><td>2017/08/21</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/Guides/Interact_with_CIC.html#ManageConnection">アクセストークンを更新する</a>セクションを追加および/token APIの内容を更新</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.2.0</td><td>v0.9</td><td>2017/08/14</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/CIC_Overview.html#DialogModel">対話モデル</a>の説明を追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/DeviceControl.html">DeviceControl</a> APIを追加</li>
          <li>[CIC] <a href="/CIC/References/Context_Objects.html">Device.DeviceState</a>のpayloadフィールドを追加：airplane、battery、bluetooth、brightness、flashLight、gps、powerSavingMode、soundMode、volume、wifi</li>
          <li>[CEK] <a href="/CEK/Guides/Build_Custom_Extension.html#DoMultiturnDialog">マルチターン対話をする</a>セクションを追加およびsessionAttributesフィールドの説明を更新</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.1.0</td><td>v0.8</td><td>2017/08/04</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/Clova.html#Hello">Clova.Hello</a>ディレクティブを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html#Play">AudioPlayer.Play</a>ディレクティブのAudioItemオブジェクトにtypeフィールドを追加</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a>オブジェクトにurlPlayableフィールドを追加</li>
          <li>[CIC] <a href="/CIC/References/CIC_API.html#Error">CICのエラーメッセージ</a>の仕様を追加</li>
          <li>[CIC] <a href="/CIC/References/CIC_API.html#MultipartMessage">マルチパートメッセージ</a>の内容を再作成</li>
          <li>[CEK] Clova Home<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">対応デバイス</a>を追加：空気清浄機、加湿器、セットトップボックス、暖房器具</li>
          <li>[CEK] Clova Home<a href="/CEK/References/ClovaHomeInterface/Shared_Objects.html#ApplianceInfoObject">対応デバイス</a>から除外：ドアロック</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v3.0.0</td><td>v0.7</td><td>2017/07/28</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html">AudioPlayer</a>のPlayNext、Stopを削除(<a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController</a>に併合)</li>
          <li>[CIC] <a href="/CIC/References/CICInterface/PlaybackController.html">PlaybackController</a>のメッセージ名を変更(Mute、Next、Pause、Previous、Resume、Stop、Unmute、VolumeDown、VolumeUp)</li>
          <li>[CIC] ルート検索のテンプレートを追加：CarRoute、TransportationRoute</li>
          <li>[CIC] 天気テンプレートを追加：<a href="/CIC/References/ContentTemplates/Humidity.html">Humidity</a>、<a href="/CIC/References/ContentTemplates/TodayWeather.html">TodayWeather</a>、<a href="/CIC/References/ContentTemplates/TomorrowWeather.html">TomorrowWeather</a>、<a href="/CIC/References/ContentTemplates/WeeklyWeather.html">WeeklyWeather</a>、<a href="/CIC/References/ContentTemplates/WindSpeed.html">WindSpeed</a></li>
          <li>[CEK] <a href="/CEK/Guides/Build_Clova_Home_Extension.html">Clova Home Extensionドキュメント</a>を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.2.1</td><td>v0.6</td><td>2017/07/14</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/References/CICInterface/AudioPlayer.html#AudioStreamInfoObject">AudioStreamInfoObject</a>オブジェクトのbeginAtInMillisecondsフィールドの内容を追加</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.2.0</td><td>v0.5</td><td>2017/07/07</td>
      <td>
        <ul>
          <li>[CEK] <a href="/CEK/References/CEK_API.html#CustomExtResponseMessage">Custom Extensionレスポンスメッセージ</a>の<a href="/CEK/References/CEK_API.html#CustomExtResponseMessage">outputSpeech</a>オブジェクト構成の更新を反映</li>
          <li>[共通] <a href="/Glossary.html">用語集を追加</a></li>
          <li>CEKのメッセージフォーマット部分の目次を更新</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.1.0</td><td>v0.4</td><td>2017/07/03</td>
      <td>
        <ul>
          <li>[CEK] CEKドキュメントの画像を更新</li>
          <li>[共通] ドキュメントの検討結果を反映</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v2.0.0</td><td>v0.3</td><td>2017/06/19</td>
      <td>
        <ul>
          <li>[CEK] CEKのドキュメント部分を作成</li>
          <li>[CIC] <a href="/CIC/Guides/Interact_with_CIC.html#ManageConnection">接続を管理する</a>セクションの内容を更新(HTTP Pingフレームを使用できない場合)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.1.0</td><td>v0.2</td><td>2017/06/08</td>
      <td>
        <ul>
          <li>[CIC] <a href="/CIC/Guides/Interact_with_CIC.html">CICと連携する</a>に<a href="/CIC/Guides/Interact_with_CIC.html#ManageConnection">接続を管理する</a>を追加(HTTP Ping)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>v1.0.0</td><td>v0.1</td><td>2017/05/29</td>
      <td>
        <ul>
          <li>[CIC] CICのドキュメント部分を作成</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
