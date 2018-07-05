# CEK APIのリファレンス
CEK APIは、CEKとExtensionの間で情報を交換するために使用されるメッセージ仕様です。CEK APIについては以下をご確認ください。
* [HTTPメッセージ](#HTTPMessage)
* [Custom Extensionメッセージ](#CustomExtMessage)
{% if isClovaHome == "true" %}* [Clova Home Extensionメッセージ](#ClovaHomeExtMessage){% endif %}

{% include "/CEK/References/HTTP_Message.md" %}

{% include "/CEK/References/Custom_Extension_Message.md" %}

{% if isClovaHome == "true" %}{% include "/CEK/References/Clova_Home_Extension_Message.md" %}{% endif %} 
