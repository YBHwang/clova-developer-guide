# CEK API reference
The CEK API contains message specifications for exchanging information between CEK and extensions. For more information on CEK API, see:
* [HTTP messages](#HTTPMessage)
* [Custom extension messages](#CustomExtMessage)
{% if EnableClovaHome == true %}* [Clova Home extension messages](#ClovaHomeExtMessage){% endif %}

{% include "/CEK/References/HTTP_Message.md" %}

{% include "/CEK/References/Custom_Extension_Message.md" %}

{% if EnableClovaHome == true %}{% include "/CEK/References/Clova_Home_Extension_Message.md" %}{% endif %} 
