## GetNoticeRequest {#GetNoticeRequest}

아파트나 오피스텔 관리 사무소의 공지 사항을 확인할 때 사용되며 대상 기기의 현재 상태 정보를 Clova Home extension에게 요청합니다. 이 요청에 대한 응답으로 [`GetNoticeResponse`](#GetNoticeResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token이 전달됩니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 항상 포함됩니다.     | 항상    |

### Remarks

**이 메시지는 아파트나 오피스텔의 스마트 홈 시스템과 같은 서비스를 위해 만들어진 전용 규격입니다.**

### Message example

```json
{
  "header": {
    "messageId": "2d8b8c3b-5905-4355-b4bb-fa359c46c308",
    "name": "GetNoticeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-019"
    }
  }
}
```

### See also
* [`GetNoticeResponse`](#GetNoticeResponse)

## GetNoticeResponse {#GetNoticeResponse}

[`GetNoticeRequest`](#GetNoticeRequest) 메시지에 대한 응답으로 아파트나 오피스텔 관리 사무소의 공지 사항을 CLOVA에 전송합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp`  | string | 기기에서 요청한 정보를 확인한 시간(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `notice[]`       | string array | 공지 사항 제목이나 요약된 텍스트 목록 | 필수    |

### Remarks

**이 메시지는 아파트나 오피스텔의 스마트 홈 시스템과 같은 서비스를 위해 만들어진 전용 규격입니다.**

### Message example

```json
{
  "header": {
    "messageId": "33da6561-0149-4532-a30b-e0de8f75c4cf",
    "name": "GetNoticeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "notice" : [
      "3월 20일 2월분 관리비 고지 안내",
      "3월 15일 재활용 쓰레기 배출요인 변경 안내",
      "3월 12일 단수 안내"
    ],
    "applianceResponseTimestamp": "2017-11-23T20:30:54+09:00"
  }
}
```

### See also
* [GetNoticeRequest](#GetNoticeRequest)
