# Building a Clova Home extension

The Clova Home extension provides remote control features for home IoT devices through third-party IoT services. The Clova Home extension must provide CEK with the information of IoT devices which can be controlled by the user. Also, when it receives a control request for an IoT device from CEK, it must perform an appropriate action and return results. The diagram below shows the operation of the Clova Home extension.

![](/CEK/Resources/Images/CEK_Clova_Home_Extension_Operation_Structure.png)

{% if book.EnableClovaHome == false %}

<div class="note">
<p><strong>メモ</strong></p>
<p>Clova Developer Centerでは Clova Home Extension の情報登録を受け付けておりません。Clova Home Extension を利用した連携に興味のある企業様は、<a href="https://partner.line.me/ja" target="_blank"> LINE Partner </a> よりお問い合わせください。　
</p>
</div>

{% else %}

This section explains the prerequisites for creating a Clova Home extension, the types of messages exchanged with CEK, and the method of operation.

The information is provided for the Clova Home extension developers in the following order:

* [Prerequisites](#Preparation)
* [Device discovery](#ProvideDeviceDiscovery)
* [Handling a Clova Home extension request](#HandleClovaHomeExtensionRequest)
  * [Validating a request message](#RequestMessageValidation)
* [Returning a Clova Home extension response](#ReturnClovaHomeExtensionResponse)

{% endif %}

{% set targetFile = '/CEK/Guides/BuildClovaHomeExtension/Preparation.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile %}

{% set targetFile = '/CEK/Guides/BuildClovaHomeExtension/Provide_Device_Discovery.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile  %}

{% set targetFile = '/CEK/Guides/BuildClovaHomeExtension/Handle_Clova_Home_Extension_Request.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile  %}

{% set targetFile = '/CEK/Guides/BuildClovaHomeExtension/Return_Clova_Home_Extension_Response.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile  %}
