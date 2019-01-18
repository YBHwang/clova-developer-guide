## ダイアログIDを管理し、作業を処理する {#ManageDialogueIDAndHandleTasks}

[間接対話](/CIC/CIC_Overview.md#IndirectDialogue)の問題を解決するために、**ダイアログID**という概念を使用します。クライアントは、ダイアログIDに関連して、以下の内容を実行する必要があります。

* [ダイアログIDを作成する](#CreatingDialogueID)
* [ダイアログIDによってディレクティブを処理する](#HandleDirectivesByDialogueID)

### ダイアログIDを作成する {#CreatingDialogueID}

**ダイアログID**とは、ユーザーのリクエストを識別するために、ユーザーが発話を開始する度に作成される識別子です。クライアントは、ユーザーのリクエストをCICに送信する度に、最終リクエストのダイアログIDを保管し、それと同時に、最終ダイアログIDを更新する必要があります。

**最終ダイアログID**とは、クライアントがCICに最終的に送信した [SpeechRecognizer.Recognize](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize)イベント、または[TextRecognizer.Recognize](/CIC/References/CICInterface/TextRecognizer.md#Recognize)イベントに含まれたダイアログIDのことです。クライアントは、この最終ダイアログIDを保管している必要があります。

クライアントは、次のように動作する必要があります。

![](/CIC/Resources/Images/CIC_Dialogue_ID_Creation.svg)

1. ユーザーが新しい対話を開始する度に、**新しいダイアログIDを作成**します(UUID形式をお勧めします）。
2. [SpeechRecognizer.Recognize](/CIC/References/CICInterface/SpeechRecognizer.md#Recognize)イベントでユーザーのリクエストをCICに送信します。テキストのリクエストは、[TextRecognizer.Recognize](/CIC/References/CICInterface/TextRecognizer.md#Recognize)イベントを使用します。
  * そのとき、[イベントのヘッダー](/CIC/References/CIC_API.md#Event)の`dialogRequestId`に新しく作成したダイアログIDを含めます。
3. イベントを送信すると、作成したダイアログIDを**最終ダイアログID**として保管します。

<div class="danger">
<p><strong>注意</strong></p>
<p>最終ダイアログIDは、<strong><a href="/CIC/References/CICInterface/SpeechRecognizer.md#Recognize">SpeechRecognizer.Recognize</a>イベント、または<a href="/CIC/References/CICInterface/TextRecognizer.md#Recognize">TextRecognizer.Recognize</a>イベントの送信を完了した後、必ず更新</strong>される必要があります。</p>
</div>

最終ダイアログIDを更新した後、クライアントは、新しい[ダイアログIDを持つディレクティブを処理する](#HandleDirectivesByDialogueID)ために、以下を実行する必要があります。

* 前のダイアログIDを持つディレクティブの内容をユーザーに提供している場合、[オーディオ再生の基本ルール](/Design/Design_Guideline_For_Client_Hardware.md#AudioInterruptionRule)または[ユーザー発話時のオーディオ再生ルール](/Design/Design_Guideline_For_Client_Hardware.md#AudioInterruptionRuleForUserUtterance)を参照して、それを中止する必要があります。
* [メッセージキュー](/CIC/Guides/Interact_with_CIC.md#ManageMessageQ)から以前のダイアログIDを持つディレクティブをすべて破棄する必要があります。

### ダイアログIDによってディレクティブを処理する {#HandleDirectivesByDialogueID}

通常、CICは、リクエストに対する応答としてクライアントにディレクティブを送信します。そのディレクティブに、[クライアントが作成したダイアログID](#CreatingDialogueID)が含まれます。クライアントはダイアログIDから、CICから受信した結果が現在のリクエストに適切な応答かどうかを確認できます。クライアントは、ダイアログIDによって、以下のようにディレクティブを処理する必要があります。

![](/CIC/Resources/Images/CIC_Handle_Directives_By_Dialogue_ID.svg)

最初に、クライアントはCICから受信した[ディレクティブのヘッダー」(/CIC/References/CIC_API.md#Directive)にダイアログIDが含まれているかを確認します。受信したディレクティブにダイアログIDが含まれている場合、**最終ダイアログID**と比較し、その結果によって以下のように処理します。

* **2つのダイアログIDが一致する場合**、受信したメッセージを[メッセージキュー](/CIC/Guides/Interact_with_CIC.md#ManageMessageQ)に追加し、順番になると、その内容をユーザーに提供します。
* **ダイアログIDが一致しない場合**、受信したディレクティブを破棄します。

**ディレクティブにダイアログIDが含まれていない場合**、クライアントは**即座に**受信したディレクティブを処理します。ダイアログIDを持たないディレクティブは、主に[ダウンチャネル](/CIC/References/CIC_API.md#EstablishDownchannel)で送信され、対話に割り込まないバックグラウンドのサービスを指示するものです。
