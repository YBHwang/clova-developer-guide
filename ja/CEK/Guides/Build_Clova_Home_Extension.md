# Clova Home Extensionを作成する

Clova Home Extensionは、外部のIoTサービスを利用して、家庭内のIoTデバイスに遠隔操作機能を提供するExtensionです。Clova Home Extensionは、ユーザーが操作できるIoTデバイスの情報をCEKに提供する必要があります。また、CEKからIoTデバイス操作のリクエストを受け取り、それを処理して結果を返す必要があります。以下の図は、Clova Home Extensionの仕組みを示しています。

![](/CEK/Resources/Images/CEK_Clova_Home_Extension_Operation_Structure.png)

{% if book.EnableClovaHome == false %}

<div class="note">
<p><strong>メモ</strong></p>
<p>Clova Developer Centerでは Clova Home Extension の情報登録を受け付けておりません。Clova Home Extension を利用した連携に興味のある企業様は、<a href="https://partner.line.me/ja" target="_blank"> LINE Partner </a> よりお問い合わせください。　
</p>
</div>

{% else %}

Clova Home Extensionを作成する際の事前準備と、Custom ExtensionがCEKとどのようなメッセージをやり取りし、どのように動作するかについて説明します。

Clova Home Extensionの開発者は、次の内容を知っておく必要があります。

1. [準備事項](#Preparation)
2. [Discovery機能を提供する](#ProvideDeviceDiscovery)
3. [Clova Home Extensionリクエストを処理する](#HandleClovaHomeExtensionRequest)
4. [Clova Home Extensionレスポンスを返す](#ReturnClovaHomeExtensionResponse)

{% endif %}

{% set targetFile = 'Preparation.md' if book.EnableClovaHome else 'Dummy.md' %}
{% include "/CEK/Guides/BuildClovaHomeExtension/" + targetFile %}

{% set targetFile = 'Provide_Device_Discovery.md' if book.EnableClovaHome else 'Dummy.md' %}
{% include "/CEK/Guides/BuildClovaHomeExtension/" + targetFile  %}

{% set targetFile = 'Handle_Clova_Home_Extension_Request.md' if book.EnableClovaHome else 'Dummy.md' %}
{% include "/CEK/Guides/BuildClovaHomeExtension/" + targetFile  %}

{% set targetFile = 'Return_Clova_Home_Extension_Response.md' if book.EnableClovaHome else 'Dummy.md' %}
{% include "/CEK/Guides/BuildClovaHomeExtension/" + targetFile  %}
