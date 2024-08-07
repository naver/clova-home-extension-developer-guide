# 기기 제어 인터페이스

기기 제어와 관련된 요청 및 응답을 수행할 때 사용되는 메시지 인터페이스입니다. 요청 메시지는 `XxxxRequest`, 응답 메시지는  `XxxxConfirmation`와 같은 형태의 이름을 가지며, 기기 제어 인터페이스는 다시 아래와 같은 분류로 나뉩니다.

* [값 설정형 인터페이스](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md): 기기의 특정 속성 값이나 운전 모드를 지정한 값으로 설정하는 인터페이스
* [값 증감형 인터페이스](/Develop/References/ClovaHomeInterface/Incremental_Type_Interfaces.md): 수치나 단계로 표현되는 기기의 특정 속성 값이나 설정 값을 올리거나 내리는 인터페이스
* [전환형 인터페이스](/Develop/References/ClovaHomeInterface/Switching_Type_Interfaces.md): 기기의 운전 모드나 설정을 특정하지 않고 다른 모드나 값으로 전환되도록 만드는 인터페이스
* [액션형 인터페이스](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md): 기기가 특정 동작을 수행하도록 만드는 인터페이스

<div class="note">
  <p><strong>Note!</strong></p>
  <p>기기 제어 인터페이스의 분류는 추가 또는 삭제되거나 이름이 변경될 수 있습니다.</p>
</div>