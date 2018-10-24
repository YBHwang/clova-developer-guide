# Creating a Clova Home extension

Clova Home extensions provide remote control features for home IoT devices through third-party IoT services. Clova Home extensions must provide CEK with the information of IoT devices which can be controlled by the user. Also, when Clova Home extensions receive a control request for an IoT device from CEK, it must perform an appropriate action and return the results. The diagram below shows the operation of the Clova Home extension.

![](/CEK/Resources/Images/CEK_Clova_Home_Extension_Operation_Structure.png)

{% if book.EnableClovaHome == false %}

<div class="note">
<p><strong>Note!</strong></p>
<p>You cannot register a Clova Home extension on the Clova developer console. Should you be interested in linking your service with a Clova Home extension, contact us via <a href="https://partner.line.me/ja" target="_blank">LINE Partner</a>.
</p>
</div>

{% else %}

This section explains the prerequisites for creating a Clova Home extension, the types of messages exchanged with CEK, and the method of operation.

The information is provided for the Clova Home extension developers in the following order:

1. [Prerequisites](#Preparation)
2. [Providing device discovery](#ProvideDeviceDiscovery)
3. [Handling a Clova Home extension request](#HandleClovaHomeExtensionRequest)
4. [Returning a Clova Home extension response](#ReturnClovaHomeExtensionResponse)

{% endif %}

{% set targetFile = 'Preparation.md' if book.EnableClovaHome else book.DummyFile %}
{% include "/CEK/Guides/BuildClovaHomeExtension/" + targetFile %}

{% set targetFile = 'Provide_Device_Discovery.md' if book.EnableClovaHome else book.DummyFile %}
{% include "/CEK/Guides/BuildClovaHomeExtension/" + targetFile  %}

{% set targetFile = 'Handle_Clova_Home_Extension_Request.md' if book.EnableClovaHome else book.DummyFile %}
{% include "/CEK/Guides/BuildClovaHomeExtension/" + targetFile  %}

{% set targetFile = 'Return_Clova_Home_Extension_Response.md' if book.EnableClovaHome else book.DummyFile %}
{% include "/CEK/Guides/BuildClovaHomeExtension/" + targetFile  %}
