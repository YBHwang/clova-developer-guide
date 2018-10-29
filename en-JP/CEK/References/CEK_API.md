# CEK API reference
The CEK API contains message specifications for exchanging information between CEK and extensions. For more information on CEK API, see:
* [HTTP messages](#HTTPMessage)
* [Custom extension messages](#CustomExtMessage)
{% if book.EnableClovaHome == true %}* [Clova Home Extension messages](#ClovaHomeExtMessage){% endif %}

{% include "/CEK/References/HTTP_Message.md" %}

{% include "/CEK/References/Custom_Extension_Message.md" %}

{% set targetFile = '/CEK/References/Clova_Home_Extension_Message.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile  %}
