## CLOVA Home extension 응답 반환하기 {#ReturnCLOVAHomeExtensionResponse}

CLOVA Home extension 개발자는 처리 결과를 CLOVA에 전송해야 합니다(HTTP Response). CLOVA Home extension 응답은 다음과 같은 특징이 있습니다.

* 기기의 상태 정보를 요청하면 IoT 서비스에서 기기의 상태 정보를 가져오기 때문에 기기의 실제 현재 상태와 다를 수 있습니다.
* 기기 제어를 요청하면 기기의 최종 상태 변화를 확인한 후 응답을 반환 해야 합니다.
* 요청이 정상적으로 처리되면 다음과 같이 항상 [CLOVA Home extension 요청](#HandleCLOVAHomeExtensionRequest)에 대응되는 [메시지 인터페이스](/Develop/References/Message_Interfaces.md)를 사용하여 응답해야 합니다.

"전등 켜줘"와 같은 제어 요청([`TurnOnRequest`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetTurnOnRequest))을 IoT 서비스에게 전달했고 IoT 서비스가 해당 요청이 정상적으로 처리되었다고 응답했을 때 다음과 같이 [`TurnOnConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetTurnOnConfirmation) 메시지를 이용하여 결과를 CLOVA에 전송해야 합니다.

{% raw %}
```json
{
  "header": {
    "messageId": "4ec35000-88ce-4724-b7e4-7f52050558fd",
    "name": "TurnOnConfirmation",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

만약, 사용자 요청을 수행하는데 오류가 발생하면 [Error API](/Develop/References/ClovaHomeInterface/Error_Interfaces.md)를 이용하여 오류를 CLOVA에 전송해야 합니다. CLOVA는 수신된 API에 따라 그에 상응하는 오류 처리를 수행합니다.

다음은 기기에 접속할 수 없어 `TargetOfflineError` 오류 메시지를 전달한 예제입니다.

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "TargetOfflineError",
    "payloadVersion": "1.0"
  },
  "payload": {
  }
}
```
{% endraw %}


<div class="note">
<p><strong>Note!</strong></p>
<p>오류 메시지를 전달할 때도 응답은 HTTP 200 OK를 사용해야 합니다.</p>
</div>
