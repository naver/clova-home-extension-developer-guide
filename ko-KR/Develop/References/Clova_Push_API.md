# CLOVA Push API

이 문서는 CLOVA Home extension의 푸시 알림용 REST API 레퍼런스입니다.

## Base URI

이 API의 base URI는 다음과 같습니다.

* https://apis.naver.com

    * **protocol** -  https

<!--

<h1 id="-clova-push">CLOVA Push</h1> 

CLOVA Home extension 사용자에게 메시지를 전송합니다.

-->

## 알림 메시지 전송 {#sendNotification}

<a id="opIdsendNotification"></a>

안전이나 재산 피해와 같이 치명적인 이유로 CLOVA Home extension 사용자에게 긴급하게 상황을 알려야 하는 경우 CLOVA Push API를 이용해 사용자에게 메시지를 전송할 수 있습니다. 이 API를 사용하려면 [CLOVA Home extension 푸시 알림 설정](/DevConsole/Guides/Configure_Push_Settings.md)이 되어 있어야 합니다.

### Endpoint

```
POST /clovahome/clova-platform/sendNotification
```

### Parameter

| 입력 타입 | 필드 이름     | 자료형  | 필드 설명                   | 필수 여부 |
|-----------|---------------|---------|-----------------------------|:---------:|
| Header    | `X-Clova-Extension-Id` | string | 푸시 알림 메시지를 전송하는 CLOVA Home extension의 ID | 필수 |
| Header    | `X-Clova-Extension-Secret` | string | 푸시 알림 API 키. API 키는 [CLOVA Home extension 푸시 알림 설정 메뉴](/DevConsole/Guides/Configure_Push_Settings.md)에서 획득할 수 있습니다. | 필수 |
| Body    | `applianceId` | string | 푸시 알림 메시지 전송과 관련된 IoT 기기의 ID. 푸시 알림 메시지를 전송하게 된 것의 발단이 되는 IoT 기기의 식별자입니다. | 필수 |
| Body    | `messageId` | string | 푸시 알림 메시지의 ID. [CLOVA Home extension 푸시 알림 설정](/DevConsole/Guides/Configure_Push_Settings.md)에 미리 정의해둔 메시지의 식별자입니다. 메시지 ID는 심사 완료 전 상태에 `"test-msg-"`와 같은 형태의 prefix를 가지며, 심사 완료 후에는 `"msg-"`와 같은 형태의 prefix를 가집니다. | 필수 |

### Body parameter

```json
{
  "applianceId": "device-012",
  "messageId": "msg-99b1598904d34bb69773a27c1b9ff285"
}
```

### Request example

```http
POST https://apis.naver.com/clovahome/clova-platform/sendNotification HTTP/1.1
Host: apis.naver.com
Content-Type: application/json
Accept: application/json
X-Clova-Extension-Id: com.example.extension.homeremote
X-Clova-Extension-Secret: com.example.extension.homeremote

```

```shell
# You can also use wget
curl -X POST https://apis.naver.com/clovahome/clova-platform/sendNotification \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'X-Clova-Extension-Id: com.example.extension.homeremote' \
  -H 'X-Clova-Extension-Secret: com.example.extension.homeremote'
```

### Response

| 상태 코드 | 설명                                          | 응답 객체            |
|-----------|-----------------------------------------------|----------------------|
| 200       | 요청 처리 성공 시 받는 응답 | [sendNotificationResult](#schemasendnotificationresult) |
| 400       | HTTP 헤더 값이나 요청 메시지에 유효하지 않은 데이터를 입력했을 때 받는 응답 | [sendNotificationResult](#schemasendnotificationresult) |

### Response example

> 200 Response

```json
{
  "summary": "호출 성공",
  "value": {
    "success": true,
    "error": null,
    "errorCode": null
  }
}
```

> HTTP 헤더 값이나 요청 메시지에 유효하지 않은 데이터를 입력했을 때 받는 응답

```json
{
  "success": false,
  "error": "not found home extension",
  "errorCode": 4201
}
```

```json
{
  "success": false,
  "error": "invalid notification api key",
  "errorCode": 4202
}
```

```json
{
  "success": false,
  "error": "empty applianceId",
  "errorCode": 4203
}
```

```json
{
  "success": false,
  "error": "invalid messageId",
  "errorCode": 4204
}
```

```json
{
  "success": false,
  "error": "invalid request body",
  "errorCode": 4205
}
```

```json
{
  "success": false,
  "error": "given home extension not support notification",
  "errorCode": 4206
}
```

```json
{
  "success": false,
  "error": "appliance-message limit exceeded",
  "errorCode": 4207
}
```

```json
{
  "success": false,
  "error": "extension-message limit exceeded",
  "errorCode": 4208
}
```

## 공유 객체 {#SharedObjects}

여기서는 요청이나 응답 시 사용되는 공유 객체에 대해 설명합니다.

### sendNotificationResult {#sendNotificationResult}
<!-- backwards compatibility -->
<a id="schemasendnotificationresult" /><a id="schema_sendNotificationResult" /><a id="tocSsendnotificationresult" /><a id="tocssendnotificationresult" />

[`/clovahome/clova-platform/sendNotification`](#sendNotification)에 대한 결과를 가지는 응답 객체

```json
{
  "meta": {
    "error": "string",
    "errorCode": 0,
    "success": true
  }
}
```

#### Properties

| 필드 이름     | 자료형  | 필드 설명                   | 필수/포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `meta` | [metaObject](#schemametaobject) | 푸시 알림 API 호출 결과에 대한 정보를 담고 있는 객체 | 필수/항상 |

### metaObject {#metaObject}
<!-- backwards compatibility -->
<a id="schemametaobject" /><a id="schema_metaObject" /><a id="tocSmetaobject" /><a id="tocsmetaobject" />

푸시 알림 API 호출 결과에 대한 정보를 담고 있는 객체

```json
{
  "error": "string",
  "errorCode": 0,
  "success": true
}
```

#### Properties

| 필드 이름     | 자료형  | 필드 설명                   | 필수/포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `error` | string | 푸시 알림 API 호출 실패 시 발생한 오류에 대한 설명. 이 필드는 `meta.success` 필드 값이 `true`일 때 `null` 값을 가집니다. | 필수/항상 |
| `errorCode` | number | 푸시 알림 API 호출 실패 시 발생한 오류의 코드. 이 필드는 `meta.success` 필드 값이 `true`일 때 `null` 값을 가집니다. | 필수/항상 |
| `success` | boolean | 푸시 알림 API 호출 성공 여부. `true`이면 성공을 `false`이면 실패를 의미합니다. | 필수/항상 |

