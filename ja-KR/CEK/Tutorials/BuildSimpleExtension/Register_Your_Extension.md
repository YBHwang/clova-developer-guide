<a href="{{ book.ServiceEnv.DeveloperConsoleURL }}/cek/#/list" target="_blank">Clova Developer Center</a>に接続して、Extensionの基本情報を登録します。
主な項目は次のとおりです。

* Extensionの情報
	* **{{ book.DevConsole.cek_id }}**: Extensionの一意のIDです。通常、パッケージの名前とExtensionの名前を組み合わせて作成します。サンプルサイコロExtensionのIDは、「my.clova.extension.sampledice」を入力します。
	* **{{ book.DevConsole.cek_invocation_name }}**：Extensionを実行する際に呼び出す名前です。Clovaアプリやスピーカー機器で正しく音声認識される言葉に設定します。サンプルサイコロExtensionの呼び出し名は、「サンプルサイコロ」です。

* サーバーとの連携を設定する
	* **{{ book.DevConsole.cek_service_endpoint_url }}**：Clovaと通信するExtensionのREST APIサーバーです。外部からアクセスできるURLにする必要があります。
		ステップ1でサンプルサイコロのソースコードを実行したサーバーのURLを入力します。

		<div class="danger">
			<p><strong>注意</strong></p>
			<p>テスト段階ではHTTPも使用できますが、正式なサービスのためにはHTTPSを使用する必要があります。Extensionのサーバーは、HTTPで80ポート、HTTPSで443ポートに設定してください。</p>
		</div>

	* **{{ book.DevConsole.cek_account_linking }}**：認可サーバー(OAuth 2.0)を介して、サードパーティサービスの会員情報と連携する場合にのみ使用されます。
		サンプルサイコロExtensionは、**{{ book.DevConsole.cek_no }}**に設定します。
* 配布情報、プライバシーポリシーおよびコンプライアンス情報

	Extensionの配布と審査に必要な情報です。このチュートリアルを進める際には、必ずしも入力する必要はありません。
