# Memo Template
CIC는 사용자가 메모를 생성하면 생성한 메모의 정보를 Memo 템플릿 형태로 클라이언트에게 전달합니다. 클라이언트는 이 템플릿을 사용하여 사용자가 생성한 메모를 화면에 표시해야 합니다.

<div class="note">
<p><strong>Note!</strong></p>
<p>Memo 템플릿은 현재 다음과 같은 제약 사항이 있습니다.</p>
<ul>
  <li>사용자는 음성으로 메모 등록과 메모 목록 조회만 요청할 수 있습니다.</li>
  <li>사용자가 메모를 수정하거나 삭제하려면 Clova 앱을 이용해야 합니다.</li>
</ul>
</div>

## Template fields

| 필드 이름       | 자료형    | 필드 설명                     |
|---------------|---------|-----------------------------|
| `content`     | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)     | 메모의 내용이 담긴 객체  |
| `timestamp`   | [DateTimeObject](/CIC/References/ContentTemplates/Shared_Objects.md#DateTimeObject) | 메모 생성 시간 정보가 담긴 객체 |
| `token`       | [StringObject](/CIC/References/ContentTemplates/Shared_Objects.md#StringObject)     | 추가한 메모의 식별자 정보가 담긴 객체  |
| `type`        | string                                                                              | Content template 구분자. `"Memo"` 값을 가집니다.             |

## Template example

{% raw %}

```json
{
  "type": "Memo",
  "token": {
    "type": "string",
    "value": "072c72b9-cfc5-4127-b4fe-557a10457232"
  },
  "content": {
    "type": "string",
    "value": "내 와이파이 비밀번호: 12345678"
  },
  "timestamp": {
    "type": "datetime",
    "value": "2017-12-24T00:00:00Z"
  }
}
```

{% endraw %}

## UI example {#UIExample}

다음은 {{ book.ServiceEnv.OrientedService }}가 배포한 모바일용 Clova 앱에서 Memo 템플릿의 내용을 표현한 UI 예제입니다.

![](/CIC/Assets/Images/Content_Template-Memo.png)

## See also
* [MemoList](/CIC/References/ContentTemplates/MemoList.md)
