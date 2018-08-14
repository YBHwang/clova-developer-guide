# Building a Clova Home extension

Clova Home extensions provide remote control features for home IoT devices through 3rd party IoT services. Clova Home extensions must provide CEK with the information of IoT devices which can be controlled by the user. Also, when it receives a control request for an IoT device from CEK, it must perform an appropriate action and return the results. The diagram below shows the operation of a Clova Home extension.

![](/CEK/Resources/Images/CEK_Clova_Home_Extension_Operation_Structure.png)

This section explains the prerequisites for creating a Clova Home extension, the types of messages exchanged with CEK, and the method of operation.

This guide provides the information Clova Home extension developers need to know in the following order:

1. [Prerequisites](#Preparation)
2. [Device discovery](#ProvideDeviceDiscovery)
3. [Handling a Clova Home extension request](#HandleClovaHomeExtensionRequest)
4. [Returning Clova Home extension responses](#ReturnClovaHomeExtensionResponse)

{% include "/CEK/Guides/BuildClovaHomeExtension/Preparation.md" %}

{% include "/CEK/Guides/BuildClovaHomeExtension/Provide_Device_Discovery.md" %}

{% include "/CEK/Guides/BuildClovaHomeExtension/Handle_Clova_Home_Extension_Request.md" %}

{% include "/CEK/Guides/BuildClovaHomeExtension/Return_Clova_Home_Extension_Response.md" %}