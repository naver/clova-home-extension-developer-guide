# CLOVA Home extension 푸시 알림 설정하기

안전이나 재산 피해와 같은 치명적인 이유로 CLOVA Home extension 사용자에게 긴급하게 상황을 알려야 하는 경우 [CLOVA Push API(REST API)](/Develop/References/Clova_Push_API.md)를 이용해 사용자에게 메시지를 전송할 수 있습니다. 이를 위해 CLOVA developer console에서 CLOVA Home extension에 대한 푸시 알림 설정을 수행해야 합니다.

푸시 알림을 사용하려면 다음 절차에 따라 푸시 알림 설정을 수행합니다.

![DevConsole-Clova_Home_Extension_Push_Settings](/DevConsole/Assets/Images/DevConsole-Clova_Home_Extension_Push_Settings.png)

<ol>
  <li>Extension 정보 입력 UI에서 위쪽에 있는 <strong>{{ book.DevConsole.cek_home_push }}</strong> 탭을 누르십시오.</li>
  <li><strong>{{ book.DevConsole.cek_home_push_use }}</strong> 항목에서 <strong>{{ book.DevConsole.cek_home_push_use_yes }}</strong>을 선택하십시오.</li>
  <li><strong>{{ book.DevConsole.cek_home_push_api_key }}</strong> 항목에서 <strong>{{ book.DevConsole.cek_home_push_api_key_button}}</strong> 버튼을 눌러 API 키를 발급하십시오.
    <div class="note">
      <p><strong>Note!</strong></p>
      <p><a href="/Develop/References/Clova_Push_API.md">CLOVA Push API</a>를 호출할 때 발급한 API 키를 사용해야 합니다.</p>
    </div>
  </li>
  <li><strong>{{ book.DevConsole.cek_home_push_add_message }}</strong> 항목에서 보내려는 메시지를 <strong>{{ book.DevConsole.cek_home_push_add_message_guide_btn }}</strong>에 맞게 입력하십시오.</li>
  <li>메시지를 입력한 후 <strong>{{ book.DevConsole.cek_home_push_add_message_button }}</strong> 버튼을 누르십시오. 그러면 <strong>{{ book.DevConsole.cek_home_push_messages }}</strong> 항목에 입력한 메시지가 추가됩니다.</li>
  <li>마지막으로 <strong>{{ book.DevConsole.cek_save }}</strong> 버튼을 누르십시오.</li>
</ol>

<div class="note">
  <p><strong>Note!</strong></p>
  <p><strong>{{ book.DevConsole.cek_save }}</strong> 버튼까지 눌러야 각 메시지에 메시지 ID가 부여됩니다. <a href="/Develop/References/Clova_Push_API.md">CLOVA Push API</a>를 호출할 때 이 메시지 ID를 사용해야 합니다.</p>
</div>

<div class="note">
  <p><strong>Note!</strong></p>
  <p>메시지 ID는 심사 완료 전 상태에 <code>"test-msg-"</code>와 같은 형태의 prefix를 가지며, 심사 완료 후에는 <code>"msg-"</code>와 같은 형태의 prefix를 가집니다. 심사 완료 전 메시지는 테스트 계정으로 <a href="/DevConsole/Guides/Test_Clova_Home_Extension.md#TestOnCLOVAApp">CLOVA Home extension을 CLOVA 앱으로 테스트</a>할 때 보내볼 수 있습니다.</p>
</div>
