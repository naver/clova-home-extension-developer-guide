## GetDetectionCountRequest {#GetDetectionCountRequest}

센서나 움직임을 인식하는 카메라가 있는 기기에서 센서나 카메라가 움직임과 같은 것을 감지한 횟수를 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`GetDetectionCountResponse`](#GetDetectionCountResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. CEK는 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token을 전달합니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |

### Message example

```json
{
  "header": {
    "messageId": "6c04fc2d-64dd-41a0-9162-7cb0d4cf7c08",
    "name": "GetDetectionCountRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-011"
    }
  }
}
```

### See also
* [`GetDetectionCountResponse`](#GetDetectionCountResponse)

## GetDetectionCountResponse {#GetDetectionCountResponse}
[`GetDetectionCountRequest`](#GetDetectionCountRequest) 메시지에 대한 응답으로 대상 기기가 센서나 움직임을 인식하는 카메라를 통해 움직임 같은 것을 감지한 횟수를 CEK에 전달합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `detectionCount`             | [DetectionCountInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#DetectionCountInfoObject) | 기기가 센서나 움직임을 감지하는 카메라를 통해 대상을 감지한 횟수 정보를 담고 있는 객체     | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetDetectionCountResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "detectionCount": {
      "value": "어제 2건, 오늘 1건"
    },
    "applianceResponseTimestamp": "2019-08-16T15:18:27+09:00"
  }
}
```

### See also
* [`GetDetectionCountRequest`](#GetDetectionCountRequest)
