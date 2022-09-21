## GetUsageTimeRequest {#GetUsageTimeRequest}
사용자가 대상 기기를 얼마나 사용했는지 확인할 때 사용하며, 대상 기기가 특정 기간이나 현재까지 누적 사용된 시간 정보를 CLOVA Home extension에 요청합니다. 이 요청에 대한 응답으로 [`GetUsageTimeResponse`](#GetUsageTimeResponse) 메시지를 사용해야 합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 포함 여부 |
|---------------|---------|-----------------------------|:---------:|
| `accessToken`      | string                                  | IoT 서비스의 사용자 계정의 access token. 외부 서비스의 인증 서버로부터 획득한 사용자 계정의 access token이 전달됩니다. 자세한 설명은 [사용자 계정 연결하기](/Develop/Guides/Link_User_Account.md)를 참조합니다.                          | 항상    |
| `appliance`        | [ApplianceInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#ApplianceInfoObject)     | 대상 기기 정보를 담고 있는 객체. `applianceId` 필드는 필수입니다.     | 항상    |
| `period`           | [PeriodInfoObject](/Develop/References/ClovaHomeInterface/Shared_Objects.md#PeriodInfoObject)           | 기간 정보를 담고 있는 객체                                     | 항상   |

### Message example

```json
{
  "header": {
    "messageId": "59a3f5bc-4c38-4d4c-9b71-3a037bf9f9b0",
    "name": "GetUsageTimeRequest",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "accessToken": "92ebcb67fe33",
    "appliance": {
      "applianceId": "device-028"
    },
    "period": {
      "start": "2018-03-28T00:00:00+09:00",
      "end": "2018-03-28T23:59:59+09:00"
    }
  }
}
```

### See also
* [`GetUsageTimeResponse`](#GetUsageTimeResponse)

## GetUsageTimeResponse {#GetUsageTimeResponse}

[`GetUsageTimeRequest`](#GetUsageTimeRequest) 메시지에 대한 응답으로 대상 기기가 사용된 시간 정보를 CLOVA에 전송합니다.

| 필드 이름       | 자료형    | 필드 설명                     | 필수 여부 |
|---------------|---------|-----------------------------|:---------:|
| `applianceResponseTimestamp` | string | 기기에서 요청한 정보를 확인한 시간(`"YYYY-MM-DDThh:mm:ss±hh:mm"`, <a href="https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations" target="_blank">ISO 8601 Combined date and time representations</a> )     | 선택    |
| `usageTime`                  | string | 사용 시간(<a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601 Durations</a>)               | 필수    |

### Message example

```json
{
  "header": {
    "messageId": "b502dd42-b698-4d3b-9ddb-bbdda70f254f",
    "name": "GetUsageTimeResponse",
    "namespace": "ClovaHome",
    "payloadVersion": "1.0"
  },
  "payload": {
    "usageTime": "P12DT8H40M",
    "applianceResponseTimestamp": "2017-11-23T20:30:19+09:00"
  }
}
```

### See also
* [`GetUsageTimeRequest`](#GetUsageTimeRequest)
