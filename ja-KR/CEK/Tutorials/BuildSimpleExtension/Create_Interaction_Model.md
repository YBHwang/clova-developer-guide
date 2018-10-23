<a href="{{ book.ServiceEnv.DeveloperConsoleURL }}/cek/#/list" target="_blank">Clova Developer Center</a>で対話モデルを登録します。

このチュートリアルでサンプルサイコロは、ユーザーから数の指定なしにサイコロを振るようにリクエストされると、デフォルトで1つのサイコロを振ります。ここでは、このように1つのサイコロを振るという指示を処理する、簡単な対話モデルを使用することにします。サイコロの数を収集しないため、スロットを持たないインテントを1つ登録することになります。

### 新規のカスタムインテントを作成する
ここでは、サイコロを振れというリクエストに対し、1つのサイコロを振る、簡単なインテントを作成します。

1. サンプルサイコロの**{{ book.DevConsoleUIString.cek_interaction_model }}**項目の**{{ book.DevConsoleUIString.cek_edit }}**ボタンをクリックします。
2. **{{ book.DevConsoleUIString.cek_builder_list_title_intent }}**の右側にある<img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" />ボタンをクリックします。
3. **{{ book.DevConsoleUIString.cek_builder_new_intent }}**の下の入力ウィンドウに「ThrowDiceIntent」と名前を入力します。
4. Enterキーを押すか、または入力ウィンドウの右側にある**{{ book.DevConsoleUIString.cek_builder_new_intent_create }}**ボタンをクリックします。

	<img src="/CEK/Resources/Images/CEK_Tutorial_NewIntent.png" style=" max-width:800px;" />

	<div class="danger">
	  <p><strong>注意</strong></p>
		<p>インテント名の大文字・小文字の区別に注意します。</p>
	</div>

### サンプル発話のリストに文章を入力する
ここでは、ユーザーが発する文章のうち、どんなものをインテントとして処理するか指定します。サンプル発話の数は多ければ多いほど良いですが、このチュートリアルでは1つだけ入力します。
1. **{{ book.DevConsoleUIString.cek_builder_intent_expression_title }}**に「サイコロを振って」と入力します。
2. Enterキーを押すか、または<img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" />ボタンをクリックします。
3. すべてのサンプル発話を入力して、**{{ book.DevConsoleUIString.cek_save }}**ボタンをクリックします。

	<img src="/CEK/Resources/Images/CEK_Tutorial_SpeechExample.png" style=" max-width:800px; margin-top:10px; margin-bottom:10px;" />

### ビルドおよびテストする
対話モデルが入力された通りに動作するか確認するために、対話モデルをビルドしてテストします。

1. **Custom Extension**の画面の左上にある**{{ book.DevConsoleUIString.cek_builder_menu_build }}**ボタンをクリックします。

	<div class="note">
	  <p><strong>メモ</strong></p>
		<p>ビルドは3~5分ほどかかります。ビルドが開始されると、ボタンが<strong>{{ book.DevConsoleUIString.cek_builder_menu_build_in_progress }}</strong>に変わり、ビルドが完了すると<strong>{{ book.DevConsoleUIString.cek_builder_menu_build }}</strong>に戻ります。</p>
	</div>

2. ビルドが完了すると、**{{ book.DevConsoleUIString.cek_builder_menu_build }}**ボタンの下にある**{{ book.DevConsoleUIString.cek_test }}**メニューをクリックします。

3. **{{ book.DevConsoleUIString.cek_builder_test_expression_title }}**にテストするフレーズを入力します。例えば、「サイコロを振って」と入力します。
4. Enterキーを押すか、または{{ book.DevConsoleUIString.cek_builder_test_request_test }}ボタンをクリックします。
5. **{{ book.DevConsoleUIString.cek_builder_test_result_title }}**の**{{ book.DevConsoleUIString.cek_builder_test_intent_result }}**項目に「ThrowDiceIntent」と表示されるか確認します。

	<img src="/CEK/Resources/Images/CEK_Tutorial_Test.png" style="max-width:800px;"/>

	<div class="note">
	<p><strong>メモ</strong></p>
	<p>ステップ2で、外部からアクセスできるExtensionサーバーのURLを登録していない場合、<strong>{{ book.DevConsoleUIString.cek_builder_test_service_response }}</strong>は「{{ book.DevConsoleUIString.cek_builder_test_no_response }}」と表示されます。</p>
	</div>
