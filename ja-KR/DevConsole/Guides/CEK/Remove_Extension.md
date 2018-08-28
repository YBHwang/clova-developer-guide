# Extensionを中止および削除する

審査をリクエストする前のExtensionは、[Extensionの基本情報を入力](/DevConsole/Guides/CEK/Register_Extension.md#InputExtensionInfo)するページでそのExtensionを削除できます。

![](/DevConsole/Resources/Images/DevConsole-Remove_Extension.png)

ただし、下記の状態にあるExtensionは削除できません。

* 審査中のExtension
* サービス中のExtension

審査中のExtensionは、いつでも審査をキャンセルし、削除できます。

![](/DevConsole/Resources/Images/DevConsole-Cancel_Submission.png)

もし、Extensionが審査を通過し、サービスが開始されている場合には、サービスを一度中止の状態にすることで削除できるようになります。サービスを中止すると、Extensionは**{{ book.DevConsole.cek_status_dev }}**ステータスに戻ります。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>サービスを中止する際には、Clova運営チームの確認が必要です。Extensionを中止するには、<a href="mailto://{{ book.ExtensionAdminEmail }}">{{ book.ExtensionAdminEmail }}</a>まで連絡してください。</p>
</div>
