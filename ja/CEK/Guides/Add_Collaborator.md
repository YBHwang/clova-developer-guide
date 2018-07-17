# 共同開発者を登録する

Custom Extensionを開発しているアカウント

開発しているアカウントで初期化しているClovaデバイスからは、以下で説明するテスターIDの追加作業を実施しなくてもテストをすることができます。
別のアカウントで初期化したClovaデバイスからスキルをテストしたい場合に以下のドキュメントを参照してください。



複数のユーザーが共同で1つのスキルを開発するには、共同開発者を登録する必要があります。具体的には、[LINE Developers](https://developers.line.me/)に開発者として登録が完了しているユーザーを、Admin権限者もしくはテスターとして登録することができます。

Admin権限者として登録すると、以下のことを実行できます。
* [LINE Developersコンソール](https://developers.line.me/console/)でチャネルを参照する
* [Clova Developer Center β](https://clova-developers.line.me/)でスキルを開発する
* Clovaデバイスで動作テストを行う

テスターとして登録すると、以下のことを実行できます。
* Clovaデバイスで動作テストを行う


1. [Admin権限者を追加する](#AssignAdminRight)
2. [テスターを追加する](#RegisterTester)
3. [Admin権限者を削除する](#RemoveAdminRight)
4. [テスターを削除する](RemoveTester)


<div class="note">
  <p><strong>メモ</strong></p>
  <p>Admin権限者およびテスターを登録した後、Extensionをテストできるようになるまでに少し時間がかかる場合があります。追加されない場合、時間をあけてから、再度確認してください。</p>
</div>

## Admin権限者を追加する {#AssignAdminRight}

Admin権限は、次の手順で付与します。

1. [LINE Developersコンソール](https://developers.line.me/console/)に接続し、**プロバイダーリスト** を表示します。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Provider_List.png)

2. 共同で開発したいスキルが含まれるプロバイダーを選択し、当該の **Clovaスキル** をクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Channel_List.png)

4. **権限管理** タブをクリックし、**追加** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Admin_LineDev_Admin_Tab.png)

5. **プロバイダーの権限者の一覧から登録**、**メールアドレス一括登録**、**メールアドレスで個別登録** のいずれかを選択し、Admin権限を付与するユーザーのアカウントを入力します。  
  ここでは **メールアドレスで個別登録** を例に説明します。追加したいユーザーのアカウント（LINE Developersへのログインに使用しているメールアドレス）を入力フォームに入力し、 **確認** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Admin_LineDev_Add_Address.png)

6. **登録** ボタンをクリックすると、当該のメールアドレス宛に招待メールが送信されます。  
![](/CEK/Resources/Images/CEK_Admin_LineDev_Add_Confirm.png)

7. 招待されたユーザーがメールに含まれる **招待を承諾する** リンクをクリックすると、Admin権限者としての登録が完了します。  
![](/CEK/Resources/Images/CEK_Admin_Invitation_Email.png)

8. **権限管理** タブを再度クリックすると、テスターが追加されたことを確認できます。  
![](/CEK/Resources/Images/CEK_Admin_LineDev_Admin_List.png)


## テスターを登録する {#RegisterTester}

テスターは、次の手順で登録します。

1. [LINE Developersコンソール](https://developers.line.me/console/)に接続し、**プロバイダーリスト** を表示します。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Provider_List.png)

2. テストするスキルが含まれるプロバイダーを選択し、当該の **Clovaスキル** をクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Channel_List.png)

4. **テスター管理** タブをクリックし、**追加** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_Tab.png)

5. **プロバイダーの権限者の一覧から登録**、**メールアドレス一括登録**、**メールアドレス個別登録** のいずれかを選択し、テスターのアカウントを入力します。  
  ここでは **メールアドレス個別登録** を例に説明します。テスターのアカウント（LINE Developersへのログインに使用しているメールアドレス）を入力フォームに入力し、 **確認** ボタンをクリックします。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_Add_Address.png)

6. **登録** ボタンをクリックすると、当該のメールアドレス宛に招待メールが送信されます。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_Add_Confirm.png)

7. 招待されたユーザーが、メールに含まれる **招待を承諾する** リンクをクリックすると、テスター登録が完了します。  
![](/CEK/Resources/Images/CEK_Test_Invitation_Email.png)

8. **テスター管理** タブを再度クリックすると、テスターが追加されたことを確認できます。  
![](/CEK/Resources/Images/CEK_Test_LineDev_Tester_List.png)

## Admin権限者を削除する {#RemoveAdminRight}

現在、この機能はご利用いただけません。

## テスターを削除する {#RemoveTester}

テスターは、次の手順で削除します。
