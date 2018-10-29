# Creating a Clova Home Extension

Clova Home Extensions provide remote control features for home IoT devices through third-party IoT services. Clova Home Extensions must provide CEK with the information of IoT devices which can be controlled by the user. Also, when Clova Home Extensions receive a control request for an IoT device from CEK, it must perform an appropriate action and return the results. The diagram below shows the operation of the Clova Home Extension.

![](/CEK/Resources/Images/CEK_Clova_Home_Extension_Operation_Structure.png)

{% if book.EnableClovaHome == false %}

<div class="note">
<p><strong>Note!</strong></p>
<p>You cannot register a Clova Home Extension on the Clova Developer Center. Should you be interested in linking your service with a Clova Home Extension, contact us via <a href="https://partner.line.me/ja" target="_blank">LINE Partner</a>.
</p>
</div>

{% else %}

This section explains the prerequisites for creating a Clova Home Extension, the types of messages exchanged with CEK, and the method of operation.

The information is provided for the Clova Home Extension developers in the following order:

* [Prerequisites](#Preparation)
* [Providing device discovery](#ProvideDeviceDiscovery)
* [Handling a Clova Home Extension request](#HandleClovaHomeExtensionRequest)
* [Returning a Clova Home Extension response](#ReturnClovaHomeExtensionResponse)

{% endif %}

{% set targetFile = '/CEK/Guides/BuildClovaHomeExtension/Preparation.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile %}

{% set targetFile = '/CEK/Guides/BuildClovaHomeExtension/Provide_Device_Discovery.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile  %}

{% set targetFile = '/CEK/Guides/BuildClovaHomeExtension/Handle_Clova_Home_Extension_Request.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile  %}

{% set targetFile = '/CEK/Guides/BuildClovaHomeExtension/Return_Clova_Home_Extension_Response.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile  %}
