# CLOVA Push API

안전이나 재산 피해와 같이 치명적인 이유로 CLOVA Home extension 사용자에게 긴급하게 상황을 알려야 하는 경우 CLOVA Push API를 이용해 사용자에게 메시지를 전송할 수 있습니다. 이 API를 사용하려면 [CLOVA Home extension 푸시 알림 설정](/DevConsole/Guides/Configure_Push_Settings.md)이 되어 있어야 합니다.

## Endpoint

<pre><code>GET|POST {{ book.ServiceEnv.PushAPIBaseURI }}/clovahome/clova-platform/sendNotification</code></pre>

## Request header

| Request header            | 설명                                                                         |
|---------------------------|------------------------------------------------------------------------------|
| X-Clova-Extension-Id      | 푸시 알림 메시지를 전송하는 CLOVA Home extension의 ID                  |
| X-Clova-Extension-Secret  | 푸시 알림 API 키. API 키는 [CLOVA Home extension 푸시 알림 설정 메뉴](/DevConsole/Guides/Configure_Push_Settings.md)에서 획득할 수 있습니다.  |

## Query parameter

없음

## Request JSON object fields

| 필드 이름       | 자료형  | 필드 설명                   | 필수 여부 |
|-----------------|---------|-----------------------------|:---------:|
| `applianceId`   | string  | 푸시 알림 메시지 전송과 관련된 IoT 기기의 ID. 푸시 알림 메시지를 전송하게 된 것의 발단이 되는 IoT 기기의 식별자입니다. | 필수 |
| `messageId`     | string  | 푸시 알림 메시지의 ID. [CLOVA Home extension 푸시 알림 설정](/DevConsole/Guides/Configure_Push_Settings.md)에 미리 정의해둔 메시지의 식별자입니다. 메시지 ID는 심사 완료 전 상태에 `"test-msg-"`와 같은 형태의 prefix를 가지며, 심사 완료 후에는 `"msg-"`와 같은 형태의 prefix를 가집니다.  | 필수  |

## Request example

<pre><code>curl -X POST '{{ book.ServiceEnv.PushAPIBaseURI }}/clovahome/clova-platform/sendNotification' \
      -H 'X-Clova-Extension-Id: com.example.extension.homeremote' \
      -H 'X-Clova-Extension-Secret: 32bddccd1a644021a4b48bc67240d887' \
      -d  '{"applianceId":"device-012", "messageId":"msg-99b1598904d34bb69773a27c1b9ff285"}'</code></pre>

## Response header

| Response header | 설명                                                                |
|-----------------|--------------------------------------------------------------------|
| Content-Type    | <p>다음 값을 포함하고 있습니다.</p><p><pre><code>application/json</code></pre></p>                   |

## Response JSON object fields

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|-----------------|-----------|-------------------------------|:---------:|
| meta            | object    | 푸시 알림 API 호출 결과에 대한 정보를 담고 있는 객체  | 항상  |
| meta.error      | string    | 푸시 알림 API 호출 실패 시 발생한 오류에 대한 설명. 이 필드는 `meta.success` 필드 값이 `true`일 때 `null` 값을 가집니다.  | 항상  |
| meta.errorCode  | number    | 푸시 알림 API 호출 실패 시 발생한 오류의 코드. 이 필드는 `meta.success` 필드 값이 `true`일 때 `null` 값을 가집니다.  | 항상  |
| meta.success    | boolean   | 푸시 알림 API 호출 성공 여부<ul><li><code>true</code>: 성공</li><li><code>false</code>: 실패</li></ul>  | 항상  |

## Status codes

| 상태 코드        | 설명                                  |
|------------------|---------------------------------------|
| 200 OK           | 요청 처리 성공 시 받는 응답                                                 |
| 400 Bad Request  | HTTP 헤더 값이나 요청 메시지에 유효하지 않은 데이터를 입력했을 때 받는 응답 |

## Error code reference

| `meta.success` | `meta.errorCode` | `meta.error`                      | 설명                                              |
|:--------------:|:----------------:|-----------------------------------|---------------------------------------------------|
| `true`         | `null`           | `null`                            | 호출 성공                                         |
| `false`        | `4201`           | `"not found home extension"`      | `X-Clova-Extension-Id` 헤더에 입력한 CLOVA Home extension의 ID 값이 유효하지 않을 때 발생하는 오류      |
| `false`        | `4202`           | `"invalid notification api key"`  | `X-Clova-Extension-Secret` 헤더에 입력한 푸시 알림 API 키 값이 유효하지 않을 때 발생하는 오류           |
| `false`        | `4203`           | `"empty applianceId"`             | 요청 메시지 본문 `applianceId` 필드에 입력한 스마트 기기의 ID 값이 유효하지 않을 때 발생하는 오류       |
| `false`        | `4204`           | `"invalid messageId"`             | 요청 메시지 본문 `messageId` 필드에 입력한 푸시 알림 메시지의 ID 값이 유효하지 않을 때 발생하는 오류    |
| `false`        | `4205`           | `"invalid request body"`          | 요청 메시지 본문의 포맷이 유효하지 않을 때 발생하는 오류                                                |
| `false`        | `4206`           | `"given home extension not support notification"`  | 지정된 CLOVA Home extension이 푸시 알림을 사용하도록 설정되지 않았을 때 발생하는 오류  |
| `false`        | `4207`           | `"appliance-message limit exceeded"`  | 하나의 기기(applianceId)에 같은 메시지(messageId)를 24시간 내 두 번 이상 보내려 할 때 발생하는 오류. 이때, "test-"로 시작되는 테스트 메시지는 횟수에 포함되지 않습니다.  |
| `false`        | `4208`           | `"extension-message limit exceeded"`  | Extension이 요청한 알림 발송 건수가 24시간 내에 발송 가능한 최대 건수(50,000건)를 초과할 때 발생하는 오류. 이때, "test-"로 시작되는 테스트 메시지도 횟수에 포함됩니다.  |



## Response example

```json
// 예제 1: HTTP 응답 메시지가 200 OK 상태 코드를 가지는 예
{
  "meta":{
    "success":true,
    "error":null,
    "errorCode":null
  }
}

// 예제 2: 잘못된 푸시 알림 API 키 입력으로 호출 실패, 상태 코드 400 Bad Request
{
  "meta":{
    "success":true,
    "error":"invalid notification api key",
    "errorCode": 4202
  }
}
```

## See also
* [CLOVA Home extension 푸시 알림 설정하기](/DevConsole/Guides/Configure_Push_Settings.md)
