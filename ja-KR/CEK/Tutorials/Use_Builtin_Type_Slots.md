# ユーザーから入力された情報を活用する
このチュートリアルでは、[簡単なExtensionを作成する](/CEK/Tutorials/Build_Simple_Extension.md)で作成したサンプルサイコロExtensionで、ユーザーのリクエストに応じて1つ以上のサイコロを振る方法について説明します。 

ユーザーの音声には、Extensionが実行するアクションの他にも、そのアクションに必要な追加情報が含まれていることがあります。[チュートリアルの概要](/CEK/Tutorials/Introduction.md)で説明されているExtensionの使い方を確認してください。

{% include "/CEK/Tutorials/BasicInformation/DICE_Sample_Dialog.md" %}

2つ目の発話で、ユーザーは「サイコロを**2つ**振って」とリクエストしています。ここでは、「2つ」が「サイコロを振る」というアクションに必要な追加情報です。

対話モデルでは、そのような追加情報を[スロット](/Design/Design_Guideline_For_Extension.md#Slot)と呼びます。Extensionが追加情報を使用するには、対話モデルを定義するとき、想定される追加の入力値をあらかじめ把握し、適切なスロットを登録する必要があります。Clovaは登録されたスロットに基づいて、ユーザーのリクエストに含まれた追加情報を認識します。

追加情報は、以下のステップを経て、処理できるようになります。
* ステップ1対話モデルを登録する(Clova Developer Centerで行う)
* ステップ2スロットの処理を実装する(Extensionサーバーで行う)
* ステップ3スロットの動作をテストする(Clova Developer Centerで行う)

## ステップ1対話モデルにスロットを登録する {#Step1}
{% include "/CEK/Tutorials/UseBuiltinTypeSlots/Add_Builtin_Slot.md" %}

## ステップ2スロットの処理を実装する {#Step2}
{% include "/CEK/Tutorials/UseBuiltinTypeSlots/Implement_Slot_Handler.md" %}

## ステップ3スロットの動作をテストする {#Step3}
{% include "/CEK/Tutorials/UseBuiltinTypeSlots/Test_Builtin_Type_Slots.md" %}

これで、サンプルサイコロExtensionは、1つ以上のサイコロを振ることができるようになりました。
同じやり方で、サイコロを1度以上振ったり、数字ではない目を持つサイコロを振ることもできます。
