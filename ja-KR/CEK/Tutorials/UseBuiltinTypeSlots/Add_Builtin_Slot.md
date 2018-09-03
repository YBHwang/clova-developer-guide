ユーザーがサイコロの数を指定できるように、対話モデルを修正する必要があります。

最初に、スロットが受け入れる情報のタイプを決め、対話モデルにスロットタイプを宣言し、そのタイプを使用するスロットをインテントに登録した後、追加情報が含まれたサンプル発話を入力して、Clovaがスロットを認識できるようにします。

### 使用するスロットタイプを宣言する
スロットが受け入れる情報のカテゴリーに応じて、スロットタイプを決めます。例えば、サイコロの数は数字で表されます。

Clovaには、すべてのExtensionで汎用で使用できるように、一般的に使われる情報のカテゴリーがあらかじめ定義されています。それを[ビルトインスロットタイプ](/Design/Design_Guideline_For_Extension.md#BuiltinSlotType)といいます。数字の種類は`CLOVA.NUMBER`というビルトインスロットタイプで定義されているので、サイコロの数を処理するための別のタイプを作成する必要はありません。

<div class="note">
  <p><strong>メモ</strong></p>
  <p>ビルトインスロットタイプとして定義されていない、Extension独自の情報のカテゴリーは、<a href="/Design/Design_Guideline_For_Extension.md#CustomSlotType">カスタムスロットタイプ</a>を定義して処理することができます。</p>
</div>

<a href="{{ book.DeveloperConsoleURL }}/cek/#/list" target="_blank">Clova Developer Center</a>に接続し、次のようにサンプルサイコロExtensionで使用するスロットタイプを宣言します。

1. サンプルサイコロの**{{ book.DevConsole.cek_interaction_model }}**項目の**{{ book.DevConsole.cek_edit }}**ボタンをクリックします。
2. **{{ book.DevConsole.cek_builder_list_title_slottype }}**の右側にある<img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" />ボタンをクリックします。
3. **{{ book.DevConsole.cek_builder_new_slottype_builtin_title }}**の下のテーブルで、`CLOVA.NUMBER`のチェックボックスを選択します。

  <img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slots_Register_Slot_Type.png" style="max-width:800px;"/>

4. **{{ book.DevConsole.cek_builder_new_slottype_builtin_title }}**の右側にある **{{ book.DevConsole.cek_save }}**ボタンをクリックします。

### インテントにスロットを登録する
振るサイコロの数は、サイコロを振るときに必要とされる追加情報です。サイコロを振るアクションは、1番目のチュートリアルで`ThrowDiceIntent`というインテントとして登録しました。次に、そのインテントにサイコロの数に対応するスロットを登録する必要があります。
前にスロットタイプを宣言した画面で、次のようにスロットを登録します。

1. **{{ book.DevConsole.cek_builder_list_title_intent }}**の下にあるカスタムインテントの`ThrowDiceIntent`を選択します。
2. **{{ book.DevConsole.cek_builder_intent_slot_title }}**の下の入力スペースに「diceCount」と入力します。
3. Enterキーを押すか、または右側にある<img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" />ボタンをクリックします。
4. 登録した「diceCount」の右の **{{ book.DevConsole.cek_builder_utterance_select_slot }}**コンボボックスをクリックします。
5. 表示されるリストから、先ほど登録した**{{ book.DevConsole.cek_builder_select_slottype_builtin }}**の`CLOVA.NUMBER`を選択します。

  <img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slots_Add_Slot.png" style="max-width:800px;"/>

6. 画面の右上にある**{{ book.DevConsole.cek_save }}**ボタンをクリックします。

### サンプル発話を入力する
1番目のチュートリアルでは、サンプル発話として、サイコロを振れという単純なフレーズを入力しましたが、ここではスロットを使用して、サイコロの数を指定する新しいフレーズを入力してみます。

先ほどスロットを登録した画面で、次のようにサンプル発話を入力します。

1. **{{ book.DevConsole.cek_builder_intent_expression_title }}**の下の入力スペースに「サイコロを2つ振って」と入力します。

  <img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slots_Sample_Utterance.png" style="max-width:800px;"/>

2. Enterキーを押すか、または<img class="inlineImage" src="/CEK/Resources/Images/DevConsole_Plus_Button.png" />ボタンをクリックします。
3. 登録したフレーズの「2つ」という単語をマウスでドラッグして選択します。
4. **{{ book.DevConsole.cek_builder_slot_layer_select_slot }}**の下にある「diceCount」を選択します。

  <img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Type_Slots_Set_Slot.png" style="max-width:800px;"/>
5. 「1つ振って」「5つのサイコロを振って」というフレーズで1から4までのステップを繰り返し行います。
