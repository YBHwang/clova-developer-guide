# CEK API reference
The CEK API contains message specifications for exchanging information between CEK and extensions. The following covers topics related to the CEK API.
* [HTTP messages](#HTTPMessage)
* [Custom extension messages](#CustomExtMessage)
{% if book.EnableClovaHome == true %}* [Clova Home extension messages](#ClovaHomeExtMessage){% endif %}

{% include "/CEK/References/HTTP_Message.md" %}

{% include "/CEK/References/Custom_Extension_Message.md" %}

{% set targetFile = '/CEK/References/Clova_Home_Extension_Message.md' if book.EnableClovaHome else book.DummyFile %}
{% include targetFile %}
