* **Extension 서버**

	Extension이 실행되는 웹 서버로서 Clova developer console에 등록됩니다. Clova가 사용자의 발화를 분석한 결과나 기본적으로 제공하는 의도를 전달했을 때 extension 서버는 이를 처리하여 알맞은 응답을 반환해야 합니다. Extensio 서버는 요청을 처리할 때 **HTTPS 프로토콜**을 사용해야 합니다.

	<div class="danger">
		<p><strong>Caution!</strong></p>
		<p>테스트 단계에서는 HTTP도 가능하나 정식 서비스를 위해서는 HTTPS여야 합니다. Extension 서버는 HTTP일 때 80번 포트를 HTTPS일 때 443번 포트를 사용해야 합니다.</p>
	</div>
