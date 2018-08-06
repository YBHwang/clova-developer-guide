## HTTP messages {#HTTPMessage}
CEK and the extensions communicate via the HTTP/1.1 protocol and exchange basic HTTP requests and HTTP responses. During this communication, a JSON format message is contained in the HTTP message body. This section explains the configuration of HTTP messages exchanged between CEK and the extension.

* [HTTP header](#HTTPHeader)
* [HTTP body](#HTTPBody)
* [Validating request messages](#RequestMessageValidation)

### HTTP header {#HTTPHeader}
An HTTP request is used when CEK sends the analyzed information of a user utterance to the extension. The HTTP request header is configured as follows:

{% if book.TargetCountryCode == "KR" %}
{% raw %}

```
POST /APIpath HTTP/1.1
Host: your.extension.endpoint
Content-Type: application/json;charset-UTF-8
Accept: application/json
Accept-Charset: utf-8
SignatureCEK: {{ SignatureCEK }}
SignatureCEKCertChainUrl: {{ SignatureCEKCertChainUrl }}
```
{% endraw %}

* HTTPS communication is performed with HTTP/1.1 and uses the POST method.
* The values for the host and request target path are filled with the URI defined by you.
* The data type of the body is in JSON format and is UTF-8 encoded.
* You can [validate whether or not a request is sent from CEK](#RequestMessageValidation) using the `SignatureCEK` and `SignatureCEKCertChainUrl` fields.
{% elif book.TargetCountryCode == "JP" %}
{% raw %}

```
POST /APIpath HTTP/1.1
Host: your.extension.endpoint
Content-Type: application/json;charset-UTF-8
Accept: application/json
Accept-Charset: utf-8
SignatureCEK: {{ SignatureCEK }}
```
{% endraw %}

* HTTPS communication is performed with HTTP/1.1 and uses the POST method.
* The values for the host and request target path are filled with the URI defined by you.
* The data type of the body is in JSON format and is UTF-8 encoded.
* You can [validate whether or not a request is sent from CEK](#RequestMessageValidation) using the `SignatureCEK` field and the public key.
{% endif %}

However, an HTTP response is used when the extension sends the processed results to CEK. The HTTP response header only needs to configure basic information as follows:
{% raw %}
```
HTTP/1.1 200 OK
Content-Type: application/json;charset-UTF-8
```
{% endraw %}
* The processed results are returned as a response to the HTTP request from CEK.
* The data type of the body is in JSON format and uses UTF-8 encoding.

### HTTP body {#HTTPBody}
Both the body of the HTTP request message and response message are in JSON format, and it contains the information about the user utterance analysis or the processed results of the extension. The configuration of each message varies depending on the extension type. For more information on message configurations, see [Custom extension messages](#CustomExtMessage) and [Clova Home extension messages](#ClovaHomeExtMessage).

### Validating request messages {#RequestMessageValidation}
{% if book.TargetCountryCode == "KR" %}
When the extension receives an HTTP request from CEK, you need to validate the integrity of the request to check that the request was sent from Clova and not from a third party. Using the `SignatureCEK` and `SignatureCEKCertChainUrl` fields in the [HTTP header](#HTTPHeader), you can validate the request message as follows:

**Obtain the certificate from `SignatureCEKCertChainUrl` for validation**
1. Check that `SignatureCEKCertChainUrl` is an HTTPS URL and includes a `{{ book.SignatureSubPath }}`.
2. Download the X.509 certificate (PEM) from the URL of `SignatureCEKCertChainUrl`.
3. Check that the value of the Subject Alternative Name (SAN) field in the downloaded certificate is `{{ book.SignatureSANDomain }}`.
4. Check that all chains have been created using a trusted root certificate.
5. Check that the downloaded certificate is valid.

**Generate a hash value and validate the message**
1. Decode the value of `SignatureCEK` in Base64.
2. Generate an SHA-1 hash value using the body of HTTP request message.
3. <a href="https://en.wikipedia.org/wiki/Digital_Signature_Algorithm#Verifying" target="_blank">Verify</a> using the public key of the certificate downloaded earlier, the decoded value of `SignatureCEK` obtained in step 1, and the hash value generated in step 3.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>If the certificate cannot be trusted or if the two values compared in the <strong>generate a hash value and validate the message</strong> process are different, we recommend that you discard the corresponding request.</p>
</div>
{% elif book.TargetCountryCode == "JP" %}
When the extension receives an HTTP request from CEK, you need to validate the integrity of the request to check that the request was sent from Clova and not from a third party. Using the `SignatureCEK` and [HTTP header](#HTTPHeader) and the public key, you can validate the request message as follows:

**Generate a hash value and validate the message**
1. Download the public key (`https://clova-cek-requests.line.me/.well-known/signature-public-key.pem`).
2. Decode the value of `SignatureCEK` in Base64.
3. Generate an SHA-256 hash value using the body of HTTP request message.
4. <a href="https://en.wikipedia.org/wiki/Digital_Signature_Algorithm#Verifying" target="_blank">Verify</a> using the public key downloaded in step 1, the decoded value of `SignatureCEK` obtained in step 2, and the hash value generated in step 3.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>If the two values compared in the <strong>generate a hash value and validate the message</strong> process are different, we recommend that you discard the corresponding request.</p>
</div>
{% endif %}
