サンプルサイコロExtensionが、登録したスロットをうまく処理するかをテストする必要があります。

[1番目のチュートリアル](/CEK/Tutorials/Build_Simple_Extension.md)のように、2つのテスト方法があります。1つは、Clova Developer Centerで対話モデルの動作を確認する方法です。もう1つは、テスターIDを登録して、Clovaデバイスで実際の動作を確認する方法です。
このチュートリアルでは、対話モデルの動作のみ確認します。

<a href="{{ book.DeveloperConsoleURL }}/cek/#/list" target="_blank">Clova Developer Center</a>に接続し、次のようにサンプルサイコロExtensionがサイコロの数をうまく認識することを確認します。
1. サンプルサイコロの**{{ book.DevConsole.cek_interaction_model }}**項目の**{{ book.DevConsole.cek_edit}}**ボタンをクリックします。
2. 画面左上の**{{ book.DevConsole.cek_builder_menu_build }}**ボタンをクリックして、対話モデルをビルドします。
3. ビルドが終わったら、左側のメニューリストで**{{ book.DevConsole.cek_test }}**メニューを選択します。
4. **{{ book.DevConsole.cek_builder_test_expression_title }}**に、複数のサイコロを振れというフレーズを入力します。例えば、「サイコロを2つ振ってみて」と入力します。
5. Enterキーを押すか、または{{ book.DevConsole.cek_builder_test_request_test }}ボタンをクリックします。
6. **{{ book.DevConsole.cek_builder_test_result_title }}**の**{{ book.DevConsole.cek_builder_test_intent_result }}**項目に`ThrowDiceIntent`、**{{ book.DevConsole.cek_builder_test_slot_result }}**項目に`diceCount`が表示され、**{{ book.DevConsole.cek_builder_test_slot_data}}**に入力したサイコロの数が表示されることを確認します。

	<img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slot_Test.png" style="max-width:800px;"/>

  <div class="note">
	<p><strong>メモ</strong></p>
	<p>外部からアクセスできるExtensionサーバーのURLを登録していない場合、<strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong>は「{{ book.DevConsole.cek_builder_test_no_response }}」と表示されます。</p>
	</div>

7. 「サイコロを10個振って」「4つのサイコロを振れ」などのフレーズで4から6までのステップを繰り返し行います。

うまく認識されない場合、さまざまなサンプル発話を追加して、認識率を向上させることができます。
