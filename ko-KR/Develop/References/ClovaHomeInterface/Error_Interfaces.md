# 오류 응답 인터페이스
CLOVA Home extension이 CEK에 오류를 반환할 때 사용되는 메시지 인터페이스이며, `XxxxError`와 같은 이름을 가집니다. 다음과 같은 오류 메시지를 사용할 수 있습니다.


| 메시지 이름         | 메시지 타입  | 메시지 설명                                   |
|------------------|-----------|---------------------------------------------|
| [`ActionFailedError`](#ActionFailedError)                 | Error Response | 요청된 동작을 수행할 때 준비 단계나 수행 단계에서 기기에 오류가 발생하면 이 메시지를 응답으로 보내야 합니다. |
| [`ActionTemporarilyBlockedError`](#ActionTemporarilyBlockedError)  | Error Response | 짧은 시간동안 대상 기기에 수용할 수 없을 만큼 많은 동작이 요청이 되었거나 사용자 및 기기의 안전 문제로 요청을 쥐소한 경우 CEK에 이 메시지를 응답으로 보내야 합니다. |
| [`ConditionsNotMetError`](#ConditionsNotMetError)          | Error Response | 대상 기기가 동작하기 위해 특정 조건(상태)이 충족되지 않으면 CEK에 이 메시지를 응답으로 보내야 합니다. |
| [`DeviceFailureError`](#DeviceFailureError)                | Error Response | 대상 기기에 결함이 발생했다면 CEK에 이 메시지를 응답으로 보내야 합니다.              |
| [`DriverInternalError`](#DriverInternalError)              | Error Response | 내부적인 오류가 발생했다면 CEK에 이 메시지를 응답으로 보내야 합니다.                |
| [`ExpiredAccessTokenError`](#ExpiredAccessTokenError)      | Error Response | [사용자 계정 연결](/Develop/Guides/Link_User_Account.md) 시 [인증 서버](/Develop/Guides/Link_User_Account.md#BuildAuthServer)로부터 발급 받은 access token이 만료되었으면 CEK에 이 메시지를 응답으로 보내야 합니다.  |
| [`InvalidAccessTokenError`](#InvalidAccessTokenError)      | Error Response | 사용자가 사용 중인 access token에 대한 권한이 해제되었다면 CEK에 이 메시지를 응답으로 보내야 합니다.         |
| [`NoSuchTargetError`](#NoSuchTargetError)                  | Error Response | 대상 기기를 찾을 수 없을 때 CEK에 이 메시지를 응답으로 보내야 합니다.                            |
| [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError) | Error Response | 대상 기기의 현재 모드에서 수행할 수 없는 동작이 요청되었다면 CEK에 이 메시지를 응답으로 보내야 합니다.  |
| [`TargetOfflineError`](#TargetOfflineError)                | Error Response | 대상 기기에 접속할 수 없으면(offline) CEK에 이 메시지를 응답으로 보내야 합니다. |
| [`UnsupportedOperationError`](#UnsupportedOperationError)  | Error Response | 대상 기기가 지원하지 않는 동작이 요청되었다면 CEK에 이 메시지를 응답으로 보내야 합니다.   |
| [`ValueNotFoundError`](#ValueNotFoundError)                | Error Response | 대상 기기가 측정 값이나 상태 값을 측정하거나 저장하지 못해 요청된 값을 제공할 수 없을 때 CEK에 이 메시지를 응답으로 보내야 합니다.  |
| [`ValueNotSupportedError`](#ValueNotSupportedError)        | Error Response | 대상 기기가 지원하지 않는 값으로 동작이 요청되었다면 CEK에 이 메시지를 응답으로 보내야 합니다.  |
| [`ValueOutOfRangeError`](#ValueOutOfRangeError)            | Error Resposne | 사용자가 대상 기기가 처리할 수 없는 범위의 값으로 동작이 요청되었다면 CEK에 이 메시지를 응답으로 보내야 합니다. |

<div class="tip">
<p><strong>Tip!</strong></p>
<p>오류 메시지 종류가 계속 추가될 것입니다.</p>
</div>

## ActionFailedError {#ActionFailedError}
요청된 동작을 수행할 때 준비 단계나 수행 단계에서 기기에 오류가 발생하면 이 메시지를 응답으로 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "9f230873-217d-49d7-81df-74fed623eacd",
    "namespace": "ClovaHome",
    "name": "ActionFailedError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also

* [`StartRecordingConfirmation`](/Develop/References/ClovaHomeInterface/Action_Type_Interfaces.md#SetStartRecordingConfirmation)

## ActionTemporarilyBlockedError {#ActionTemporarilyBlockedError}
짧은 시간동안 대상 기기에 수용할 수 없을 만큼 많은 동작이 요청이 되었거나 사용자 및 기기의 안전 문제로 요청을 취소한 경우 CEK에 이 메시지를 응답으로 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "63788c00-5b27-4ce7-b1f4-4f56bc12d3f4",
    "namespace": "ClovaHome",
    "name": "ActionTemporarilyBlockedError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also

없음

## ConditionsNotMetError {#ConditionsNotMetError}
대상 기기가 동작하기 위해 특정 조건(상태)이 충족되지 않으면 CEK에 이 메시지를 응답으로 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `state`       | string  | 충족되지 않은 조건이나 상태를 설명한 값. 이 필드는 사용자에게 TTS로 전달되므로 사용자가 이해할 수 있는 말로 작성되어야 합니다. 다음과 같은 형태로 사용자에게 현재 상황을 전달합니다.<pre><code>{대상 기기}의 {state} 상태에서는 지원하지 않는 기능입니다. 확인 후 다시 시도해 주세요.</code></pre>  | 필수    |

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "4ea1e527-7be3-4b54-b531-93d245b97303",
    "namespace": "ClovaHome",
    "name": "ConditionsNotMetError",
    "payloadVersion": "1.0"
  },
  "payload": {
    "state": "절전 모드"
  }
}
```
{% endraw %}

### See also
* [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError)

## DeviceFailureError {#DeviceFailureError}
대상 기기에 결함이 발생했다면 CEK에 이 메시지를 응답으로 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "4ea1e527-7be3-4b54-b531-93d245b97303",
    "namespace": "ClovaHome",
    "name": "DeviceFailureError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`DriverInternalError`](#DriverInternalError)
* [`TargetOfflineError`](#TargetOfflineError)

## DriverInternalError {#DriverInternalError}
내부적인 오류가 발생했다면 CEK에 이 메시지를 응답으로 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "DriverInternalError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`DeviceFailureError`](#DeviceFailureError)
* [`TargetOfflineError`](#TargetOfflineError)

## ExpiredAccessTokenError {#ExpiredAccessTokenError}
[사용자 계정 연결](/Develop/Guides/Link_User_Account.md) 시 [인증 서버](/Develop/Guides/Link_User_Account.md#BuildAuthServer)로부터 발급 받은 access token이 만료되었다면 CEK에 이 메시지를 응답으로 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "1abd6113-4a36-47c3-851e-bee3254fe183",
    "namespace": "ClovaHome",
    "name": "ExpiredAccessTokenError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`InvalidAccessTokenError`](#InvalidAccessTokenError)

## InvalidAccessTokenError {#InvalidAccessTokenError}
사용자가 사용 중인 access token에 대한 권한이 해제되었다면 CEK에 이 메시지를 응답으로 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "b8ac8b45-9fb9-4dc4-97ca-d55e9fc1ff8f",
    "namespace": "ClovaHome",
    "name": "InvalidAccessTokenError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`ExpiredAccessTokenError`](#ExpiredAccessTokenError)

## NoSuchTargetError {#NoSuchTargetError}
대상 기기를 찾을 수 없을 때 CEK에 이 메시지를 응답으로 보내야 합니다. 예를 들면, 사용자가 IoT 서비스에서 특정 기기를 제거했지만 해당 내용이 아직 CLOVA 앱에 반영되지 않은 상태에서 해당 기기에 대한 제어를 요청했다면 이 메시지를 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "d458e46c-6827-4940-9340-a7a9d427d7ab",
    "namespace": "ClovaHome",
    "name": "NoSuchTargetError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`ConditionsNotMetError`](#ConditionsNotMetError)
* [`TargetOfflineError`](#TargetOfflineError)

## NotSupportedInCurrentModeError {#NotSupportedInCurrentModeError}
대상 기기의 현재 모드에서 수행할 수 없는 동작이 요청되었다면 CEK에 이 메시지를 응답으로 보내야 합니다. 예를 들면, 에어컨 중에서도 특정 제품은 제습 모드로 동작하고 있을 때 온도 조절 관련 동작이 제한될 수 있습니다. 이런 제품을 사용하는 사용자가 제습 모드에서 온도를 조절하는 요청을 할 수 없을 때와 같은 상화에 이 메시지를 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "f321b946-b593-4279-a840-8e5af5a00146",
    "namespace": "ClovaHome",
    "name": "NotSupportedInCurrentModeError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`UnsupportedOperationError`](#UnsupportedOperationError)

## TargetOfflineError {#TargetOfflineError}
대상 기기에 접속할 수 없으면(offline) CEK에 이 메시지를 응답으로 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "TargetOfflineError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`DeviceFailureError`](#DeviceFailureError)
* [`DriverInternalError`](#DriverInternalError)

## UnsupportedOperationError {#UnsupportedOperationError}

대상 기기가 지원하지 않는 동작이 요청되었다면 CEK에 이 메시지를 응답으로 보내야 합니다. 기본적으로 대상 기기가 지원하지 않는 동작(action)을 사용자가 요청했다면 CEK가 바로 사용자에게 허용되지 않는 범위의 요청임을 알려줍니다. 다만, `SetMode`와 같은 동작은 CLOVA Home extension이 [SetModeRequest](/Develop/References/ClovaHomeInterface/Value-Setting_Type_Interfaces.md#SetModeRequest) 메시지를 수신하여 `mode` 필드 값을 확인하기 전까지 허용 범위의 동작인지 알 수 없습니다. 만약, CLOVA Home extension이 메시지를 했는데 지원하지 않는 모드라면 오류 응답을 보내야 합니다. 이때, `UnsupportedOperationError` 메시지를 CEK로 보내면 됩니다.

예를 들어, 사용자의 온도조절기(`"THERMOSTAT"` 타입)가 `SetMode` 동작을 수행할 수 있고 해당 기기가 취침 모드(`"sleep"`), 외출 모드(`"away"`)를 지원한다고 가정해 봅니다. 이 상태에서 사용자가 해당 기기에 냉방 모드(`"cool"`)를 설정하도록 요청하면 CLOVA Home extension에서 `UnsupportedOperationError` 메시지를 CEK로 보내야 합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "e9a77ef6-748b-4f9b-aa3e-c14ece3fa726",
    "namespace": "ClovaHome",
    "name": "UnsupportedOperationError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also
* [`NotSupportedInCurrentModeError`](#NotSupportedInCurrentModeError)

## ValueNotFoundError {#ValueNotFoundError}
대상 기기가 측정 값이나 상태 값을 측정하거나 저장하지 못해 요청된 값을 제공할 수 없을 때 CEK에 이 메시지를 응답으로 보내야 합니다. 예를 들면, 에어컨은 현재 온도와 같은 값을 기본적으로 제공해야 하지만 결함이나 일시적인 고장으로 온도를 측정하지 못해 값을 제공하지 못할 수도 있습니다. 이런 상황에 이 메시지가 사용될 수 있습니다.

### Payload fields
없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "57109b11-ee04-45df-9dd2-c979bc8608ea",
    "namespace": "ClovaHome",
    "name": "ValueNotFoundError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also

* [`ValueNotSupportedError`](#ValueNotSupportedError)
* [`ValueOutOfRangeError`](#ValueOutOfRangeError)

## ValueNotSupportedError {#ValueNotSupportedError}
대상 기기가 지원하지 않는 값으로 동작이 요청되었다면 CEK에 이 메시지를 응답으로 보내야 합니다. CEK가 이 메시지를 전달받으면 미리 준비된 오류 메시지를 클라이언트에 전달합니다.

### Payload fields

없음

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* 오류 메시지의 이름으로 상황을 판단하기 때문에 별도의 `payload`가 필요하지 않습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "9bfd7a41-2a4a-428a-b429-823cc6ae4813",
    "namespace": "ClovaHome",
    "name": "ValueNotSupportedError",
    "payloadVersion": "1.0"
  },
  "payload": {}
}
```
{% endraw %}

### See also

* [`ValueNotFoundError`](#ValueNotFoundError)
* [`ValueOutOfRangeError`](#ValueOutOfRangeError)

## ValueOutOfRangeError {#ValueOutOfRangeError}
사용자가 대상 기기가 처리할 수 없는 범위의 값으로 동작이 요청되었다면 CEK에 이 메시지를 응답으로 보내야 합니다. 예를 들면, 에어컨에 설정할 수 있는 희망 온도 값이 18에서 28 사이인데 사용자가 16이나 30과 같은 값을 설정하도록 요청한 상황에 이 메시지가 사용될 수 있습니다. `payload`에 대상 기기가 처리할 수 있는 최대치와 최소치를 전달해야 합니다.

### Payload fields

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `maximumValue` | number | 대상 기기가 허용하는 설정값의 최대치 | 필수    |
| `minimumValue` | number | 대상 기기가 허용하는 설정값의 최소치 | 필수    |

### Remarks
* 오류 메시지도 정상적인 HTTP 응답(200 OK)으로 CEK에 메시지를 전달해야 합니다.
* `payload`에 입력한 값은 사용자 안내에 사용될 수 있습니다.

### Message example

{% raw %}
```json
{
  "header": {
    "messageId": "fef949b7-eb94-4bda-a417-2cfb604194c3",
    "namespace": "ClovaHome",
    "name": "ValueOutOfRangeError",
    "payloadVersion": "1.0"
  },
  "payload": {
    "minimumValue":18.0,
    "maximumValue":30.0
  }
}
```
{% endraw %}

### See also

* [`ValueNotFoundError`](#ValueNotFoundError)
* [`ValueNotSupportedError`](#ValueNotSupportedError)
