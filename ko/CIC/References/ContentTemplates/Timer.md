# Timer Template
CIC는 사용자가 타이머를 생성하면 생성한 타이머의 정보를 Timer 템플릿 형태로 클라이언트에게 전달합니다. 클라이언트는 이 템플릿을 사용하여 사용자가 생성한 타이머 정보를 화면에 표시해야 합니다.

<div class="note">
<p><strong>Note!</strong></p>
<p>Timer 템플릿은 현재 다음과 같은 제약 사항이 있습니다.</p>
<ul>
  <li>사용자는 음성으로 타이머 등록과 타이머 목록 조회만 요청할 수 있습니다.</li>
  <li>사용자가 타이머를 수정하거나 삭제하려면 Clova 앱을 이용해야 합니다.</li>
</ul>
</div>

## Template field

| 필드 이름       | 자료형    | 필드 설명                     |
|---------------|---------|-----------------------------|
| `scheduledTime` | [DateTimeObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateTimeObject) | 타이머가 울릴 날짜와 시간 정보를 가지는 객체      |
| `type`          | string                                                                              | Content template 구분자. `"Timer"` 값을 가집니다.  |

## Template Example

{% raw %}

```json
{
  "type": "Timer",
  "scheduledTime": {
    "type": "datetime",
    "value": "2017-12-24T00:00:00Z"
  }
}
```

{% endraw %}

## Screen UI example {#UIExample}

<div class="note">
<p><strong>Note!</strong></p>
<p>Timer 템플릿이 사용된 화면 예제를 준비하고 있습니다.</p>
</div>

## See also
* [Alerts](/CIC/References/CICInterface/Alerts.md) 인터페이스
* [TimerList](/CIC/References/ContentTemplates/TimerList.md)