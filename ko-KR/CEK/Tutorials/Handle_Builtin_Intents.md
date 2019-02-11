# 기본적인 의사 표현 처리하기
이 튜토리얼에서는 [기초적인 extension 만들기](/CEK/Tutorials/Build_Simple_Extension.md)에서 만든 샘플 주사위 extension을 통해 예, 아니오 등의 기본적인 의사 표현을 처리하는 법을 알아봅니다.

Clova는 빈번하게 발생하는 사용자의 기본적인 의사 표현을 모든 extension에서 공통으로 사용할 수 있도록 [built-in intent](/Design/Design_Guideline_For_Extension.md#BuiltinIntent)로 미리 정의해 놓았습니다. 다음은 Clova가 제공하는 built-in intent입니다.

| Built-in intent 이름       | 의도               | 대응하는 사용자 발화 예시                                      |
|---------------------------|-------------------|----------------------------------------------------------|
| Clova.GuideIntent         | 도움말 요청          | "너 뭐 할 줄 알아?", "사용법 알려줘" |
| Clova.CancelIntent        | 실행 취소 요청        | "취소", "취소해줘"                                          |
| Clova.YesIntent           | 긍정 응답(예, Yes)   | "응", "그래", "알겠어", "알겠습니다", "오케이"                   |
| Clova.NoIntent            | 부정 응답(아니오, No) | "아니", "아니요", "싫어"                                     |

사용자가 도움말을 요청하거나 실행 취소를 요청할 때 이를 처리하기 위해 첫 번째 튜토리얼에서 했던 것처럼 intent와 예시 문장을 등록할 필요 없이 위 표에 있는 built-in intent를 사용하면 됩니다.

Built-in intent를 처리하는 과정은 다음과 같습니다.
* 1단계. Built-in intent 처리 구현(Extension 서버에서 작업)
* 2단계. Built-in intent 동작 테스트(Clova developer console에서 작업)

## 1단계. Built-in intent 처리 구현 {#Step1}

샘플 주사위 extension이 built-in intent를 처리할 수 있도록 코드를 변경해야 합니다.

여기서는 기본적인 처리 방법을 알아보기 위해 도움말 요청 built-in intent만 처리하도록 합니다.
도움말 요청 built-in intent는 사용자가 "어떻게 사용해", "도움말 알려줘" 같은 말을 할 때 전송되며, `Clova.GuideIntent`라는 이름을 사용합니다.

이 built-in intent를 처리하기 위해 다음과 같이 [첫 번째 튜토리얼](/CEK/Tutorials/Build_Simple_Extension.md)의 저장소를 재사용합니다.
다음과 같이 로컬 저장소로 이동하여 `tutorial2` 브랜치로 전환합니다.

```bash
cd /path/to/your_sample_dice_directory
git fetch
git checkout tutorial2
```

샘플 주사위 extension은 `clova/index.js` 파일의 `intentRequest()`에서 도움말 요청을 처리합니다.

```javascript
intentRequest(cekResponse) {
  const intent = this.request.intent.name

  switch (intent) {
    ...
    case "Clova.GuideIntent":
    default:
      cekResponse.setSimpleSpeechText("주사위 한 개 던져줘, 라고 시도해보세요.")
  }
  ...
}
```

위 코드에서 보는 것처럼, Clova로부터 받은 요청 메시지에서 intent를 추출하여 그 이름이 `Clova.GuideIntent`일 때 "주사위 한 개 던져줘"라고 시도하도록 알려줍니다.

변경된 코드를 extension 서버에서 실행합니다.

## 2단계. Built-in intent 동작 테스트 {#Step2}
샘플 주사위 extension이 도움말 요청을 하는 built-in intent를 잘 처리하는지 테스트해야 합니다.

[첫 번째 튜토리얼](/CEK/Tutorials/Build_Simple_Extension.md)에서처럼 두 가지 테스트 방법이 있습니다. 하나는 Clova developer console에서 interaction 모델 동작을 확인하는 것이고, 다른 하나는 테스터 ID를 등록하여 Clova 앱에서 실제 동작을 확인하는 것입니다.
이 튜토리얼에서는 interaction 모델 동작만 확인합니다.

<div class="note">
  <p><strong>Note!</strong></p>
  <p>Built-in intent는 interaction 모델에 명시적으로 등록하지 않아도 기본적으로 동작합니다.
  추후 각 extension에서 built-in intent를 선택하여 등록할 수 있도록 할 예정입니다.</p>
</div>

다음 순서대로 샘플 주사위 extension의 도움말 요청이 잘 동작하는지 확인합니다.

<ol>
  <li><p><a href="{{ book.ServiceEnv.DeveloperConsoleURL }}/cek/#/list" target="_blank">Clova developer console</a>에 접속합니다.</p></li>
  <li><p>샘플 주사위의 <strong>{{ book.DevConsole.cek_interaction_model }}</strong> 항목 내 <strong>{{ book.DevConsole.cek_edit}}</strong> 버튼을 누릅니다.</p></li>
  <li><p>화면 좌측 상단의 <strong>{{ book.DevConsole.cek_builder_menu_build }}</strong> 버튼을 눌러 interaction 모델을 빌드합니다.</p></li>
  <li><p>빌드가 끝난 후, 왼쪽의 메뉴 목록에서 <strong>{{ book.DevConsole.cek_test }}</strong> 메뉴를 누릅니다.</p></li>
  <li><p><strong>{{ book.DevConsole.cek_builder_test_expression_title }}</strong>에 도움말을 요청하는 문장을 입력합니다. 예를 들어, "사용법 알려줘"라고 입력합니다.</p></li>
  <li><p>엔터키 또는 <strong>{{ book.DevConsole.cek_builder_test_request_test }}</strong> 버튼을 누릅니다.</p></li>
  <li>
    <p><strong>{{ book.DevConsole.cek_builder_test_result_title }}</strong>의 <strong>{{ book.DevConsole.cek_builder_test_intent_result }}</strong> 항목에 "Clova.GuideIntent"라고 나타나는지 확인합니다.</p>

  	<img src="/CEK/Resources/Images/CEK_Tutorial_Builtin_Intent_Test.png" />

    <div class="note">
    	<p><strong>Note!</strong></p>
    	<p>외부에서 접근할 수 있는 extension 서버 URL을 등록하지 않았다면, <strong>{{ book.DevConsole.cek_builder_test_service_response }}</strong>은 "{{ book.DevConsole.cek_builder_test_no_response }}"라고 나타납니다.</p>
  	</div>
  </li>
</ol>

이렇게 하면 샘플 주사위 extension이 도움말 요청에 응답할 수 있게 됩니다.
이와 같은 방법으로 extension 서버가 `Clova.CancelIntent`, `Clova.YesIntent`, `Clova.NoIntent`을 처리하도록 구현하면, 실행 취소나 긍정 혹은 부정을 의미하는 요청에도 응답할 수 있습니다.
