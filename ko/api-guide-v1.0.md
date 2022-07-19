## Security > Security Monitoring > API 가이드

[API 도메인]

| 리전 | 도메인 |
| --- | --- |
| 한국(판교, 평촌) 리전 | https://kr1-secmon.api.nhncloudservice.com |

## 관제 등록 API

### 관제 미신청 목록 조회

#### 요청

[URI]

| 메서드 | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/not-applied-vms |

[파라미터]

| 이름 | 타입 | 필수 여부 | 기본값 | 유효 범위 | 설명 |
| --- | --- | --- | --- | --- | --- |
| regionCode | String | 선택 | KR1 | KR1/KR2 | 인스턴스를 조회할 리전 정보<br>(KR1 : 판교 리전, KR2 : 평촌 리전) |

[예]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/not-applied-vms?regionCode=KR1" \
 -H "Content-Type: application/json"
```

#### 응답

[응답 본문]

``` json
{
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    },
    "results": [
        {
            "lbIp": "133.186.111.22",
            "vm": [
                {
                    "vmId": "9d5cbf7b-4826-4e83-b13a-ef608bacf0e9",
                    "fixedIp": "192.168.0.9",
                    "vmOs": "CentOS 7.8",
                    "vmIp": "",
                    "serviceStatus": "미신청",
                    "vmName": "vm1"
                }
            ],
            "fixedIp": "192.168.0.18",
            "lbId": "8b031032-e0a0-4b36-8a98-642b6d3ca07b",
            "lbName": "lb1",
            "serviceStatus": "미신청"
        },
        {
            "vmId": "2300727f-3771-4bdc-bba1-35ca12cb8635",
            "fixedIp": "192.168.0.4",
            "vmOs": "CentOS 7.8",
            "vmIp": "133.186.112.33",
            "serviceStatus": "미신청",
            "vmName": "vm2"
        }
    ]
}
```

[필드]

| 필드 | 타입 | 설명 |
| --- | --- | --- |
| header | Object | 헤더 영역 |
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 결과 코드 |
| header.resultMessage | String | 결과 메시지 |
| results | List | 관제 미신청 상태의 vm 목록 |
| results[0].lbIp | String | Load Balancer의 Floating IP |
| results[0].vm | List | Load Balancer에 연결된 VM 목록 |
| results[0].vm[0].vmId | String | VM의 식별자 ID |
| results[0].vm[0].fixedIp | String | VM의 Fixed IP |
| results[0].vm[0].vmOs | String | VM의 운영체제 정보 |
| results[0].vm[0].vmIp | String | VM의 Floating IP |
| results[0].vm[0].serviceStatus | String | VM의 보안관제 신청 상태 |
| results[0].vm[0].vmName | String | VM의 이름 |
| results[0].fixedIp | String | Load Balancer의 Fixed IP |
| results[0].lbId | String | Load Balancer의 식별자 ID |
| results[0].lbName | String | Load Balancer의 이름 |
| results[0].serviceStatus | String | Load Balancer의 보안관제 신청 상태 |
| results[1].vmId | String | VM의 식별자 ID |
| results[1].fixedIp | String | VM의 Fixed IP |
| results[1].vmOs | String | VM의 운영체제 정보 |
| results[1].vmIp | String | VM의 Floating IP |
| results[1].serviceStatus | String | VM의 보안관제 신청 상태 |
| results[1].vmName | String | VM의 이름 |

### 관제 신청 목록 조회

#### 요청

[URI]

| 메서드 | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/applied-vms |

[파라미터]

| 이름 | 타입 | 필수 여부 | 기본값 | 유효 범위 | 설명 |
| --- | --- | --- | --- | --- | --- |
| regionCode | String | 선택 | KR1 | KR1/KR2 | 인스턴스를 조회할 리전 정보<br>(KR1 : 판교 리전, KR2 : 평촌 리전) |

[예]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/applied-vms?regionCode=KR1" \
 -H "Content-Type: application/json"
```

#### 응답

[응답 본문]

``` json
{
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    },
    "results": [
        {
            "lbIp": "133.186.111.22",
            "vm": [
                {
                    "vmId": "9d5cbf7b-4826-4e83-b13a-ef608bacf0e9",
                    "fixedIp": "192.168.0.9",
                    "vmOs": "CentOS 7.8",
                    "vmIp": "",
                    "serviceStatus": "접수대기",
                    "vmName": "vm1"
                }
            ],
            "fixedIp": "192.168.0.18",
            "lbId": "8b031032-e0a0-4b36-8a98-642b6d3ca07b",
            "lbName": "lb1",
            "serviceStatus": "접수대기"
        },
        {
            "vmId": "2300727f-3771-4bdc-bba1-35ca12cb8635",
            "fixedIp": "192.168.0.4",
            "vmOs": "CentOS 7.8",
            "vmIp": "133.186.112.33",
            "serviceStatus": "진행중",
            "vmName": "vm2"
        }
    ]
}
```

[필드]

| 필드 | 타입 | 설명 |
| --- | --- | --- |
| header | Object | 헤더 영역 |
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 결과 코드 |
| header.resultMessage | String | 결과 메시지 |
| results | List | 관제 신청된 상태의 vm 목록 |
| results[0].lbIp | String | Load Balancer의 Floating IP |
| results[0].vm | List | Load Balancer에 연결된 VM 목록 |
| results[0].vm[0].vmId | String | VM의 식별자 ID |
| results[0].vm[0].fixedIp | String | VM의 Fixed IP |
| results[0].vm[0].vmOs | String | VM의 운영체제 정보 |
| results[0].vm[0].vmIp | String | VM의 Floating IP |
| results[0].vm[0].serviceStatus | String | VM의 보안관제 신청 상태 |
| results[0].vm[0].vmName | String | VM의 이름 |
| results[0].fixedIp | String | Load Balancer의 Fixed IP |
| results[0].lbId | String | Load Balancer의 식별자 ID |
| results[0].lbName | String | Load Balancer의 이름 |
| results[0].serviceStatus | String | Load Balancer의 보안관제 신청 상태 |
| results[1].vmId | String | VM의 식별자 ID |
| results[1].fixedIp | String | VM의 Fixed IP |
| results[1].vmOs | String | VM의 운영체제 정보 |
| results[1].vmIp | String | VM의 Floating IP |
| results[1].serviceStatus | String | VM의 보안관제 신청 상태 |
| results[1].vmName | String | VM의 이름 |

### 관제 추가

#### 요청

[URI]

| 메서드 | URI |
| --- | --- |
| POST | /v1.0/appkeys/{appKey}/vm |

[파라미터]

| 이름 | 타입 | 필수 여부 | 기본값 | 유효 범위 | 설명 |
| --- | --- | --- | --- | --- | --- |
| regionCode | String | 선택 | KR1 | KR1/KR2 | 인스턴스를 조회할 리전 정보<br>(KR1 : 판교 리전, KR2 : 평촌 리전) |

[요청 본문]

``` json
{
  "vmList": [
    {
      "lbIp": "133.186.154.14",
      "vm": [
        {
          "vmId": "9d5cbf7b-4826-4e83-b13a-ef608bacf0e9",
          "fixedIp": "192.168.0.9",
          "vmOs": "CentOS 7.8",
          "vmIp": "",
          "vmName": "mss-test"
        }
      ],
      "fixedIp": "192.168.0.18",
      "lbId": "8b031032-e0a0-4b36-8a98-642b6d3ca07b",
      "lbName": "lb3"
    },
    {
      "vmId": "1dc707a8-a5be-431e-aca1-77c60af1fe9a",
      "fixedIp": "192.168.0.2",
      "vmOs": "CentOS 6.10",
      "vmIp": "133.186.154.126",
      "vmName": "booting-test"
    }
  ]
}
```

[필드]

| 이름 | 타입 | 필수 여부 | 기본값 | 유효 범위 | 설명 |
| --- | --- | --- | --- | --- | --- |
| vmList | List | 필수 |  |  | 관제 신청 vm 목록 |
| vmList[0].lbIp | String | 필수 |  |  | Load Balancer의 Floating IP |
| vmList[0].vm | List | 필수 |  |  | Load Balancer에 연결된 VM 목록 |
| vmList[0].vm[0].vmId | String | 필수 |  |  | VM의 식별자 ID |
| vmList[0].vm[0].fixedIp | String | 필수 |  |  | VM의 Fixed IP |
| vmList[0].vm[0].vmOs | String | 필수 |  |  | VM의 운영체제 정보 |
| vmList[0].vm[0].vmIp | String | 필수 |  |  | VM의 Floating IP |
| vmList[0].vm[0].vmName | String | 필수 |  |  | VM의 이름 |
| vmList[0].fixedIp | String | 필수 |  |  | Load Balancer의 Fixed IP |
| vmList[0].lbId | String | 필수 |  |  | Load Balancer의 식별자 ID |
| vmList[0].lbName | String | 필수 |  |  | Load Balancer의 이름 |
| vmList[1].vmId | String | 필수 |  |  | VM의 식별자 ID |
| vmList[1].fixedIp | String | 필수 |  |  | VM의 Fixed IP |
| vmList[1].vmOs | String | 필수 |  |  | VM의 운영체제 정보 |
| vmList[1].vmIp | String | 필수 |  |  | VM의 Floating IP |
| vmList[1].vmName | String | 필수 |  |  | VM의 이름 |

* Load Balancer에 연결된 형태의 VM을 관제 신청하기 위해서는 vmList[0]의 데이터를 필수로 입력해야하며, Load Balancer에 연결되지 않은 VM을 관제 신청하기 위해서는 vmList[1]의 데이터를 필수로 입력하여야 합니다.

#### 응답

[응답 본문]

``` json
{
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    }
}
```

### 관제 해제

#### 요청

[URI]

| 메서드 | URI |
| --- | --- |
| DELETE | /v1.0/appkeys/{appKey}/vm |

[파라미터]

| 이름 | 타입 | 필수 여부 | 기본값 | 유효 범위 | 설명 |
| --- | --- | --- | --- | --- | --- |
| vmId | String | 필수 |  |  | 관제 해제할 vm들의 ID를 `,`로 연결한 값 |
| regionCode | String | 선택 | KR1 | KR1/KR2 | 인스턴스의 리전 정보<br>(KR1 : 판교 리전, KR2 : 평촌 리전) |

[예]

```
curl -X DELETE "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/vm?regionCode=KR1&vmId=8b031032-e0a0-4b36-8a98-642b6d3ca07b,1dc707a8-a5be-431e-aca1-77c60af1fe9a" \
 -H "Content-Type: application/json"
```
* Load Balancer에 연결된 형태의 VM을 관제 해제하기 위해서는 vmId 파라미터에 Load Balancer ID만을 입력하여야 합니다.

#### 응답

[응답 본문]

``` json
{
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    }
}
```

### 관제 상태 변경 이력 조회

#### 요청

[URI]

| 메서드 | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/history |

[파라미터]

| 이름 | 타입 | 필수 여부 | 기본값 | 유효 범위 | 설명 |
| --- | --- | --- | --- | --- | --- |
| page | Integer | 선택 | 1 |  | 조회할 페이지 |

[예]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/history?page=1" \
 -H "Content-Type: application/json"
```

#### 응답

[응답 본문]

``` json
{
    "count": 20,
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    },
    "previous": null,
    "results": [
        {
            "status": "접수",
            "reason": "사용자신청",
            "contents": "보안관제 추가 진행 중 입니다.",
            "vmId": "vm1 | vm2",
            "meter": "NO",
            "type": "신규",
            "regDate": "2021-07-09T15:34:29+09:00",
            "historyId": 4539
        },
        ...
        ,
        {
            "status": "접수",
            "reason": "사용자신청",
            "contents": "보안관제 추가 진행 중 입니다.",
            "vmId": "vm3",
            "meter": "NO",
            "type": "신규",
            "regDate": "2021-07-09T15:00:38+09:00",
            "historyId": 4530
        }
    ],
    "next": "https://kr1-secmon.api.nhncloudservice.com/appkeys/{appKey}/history?page=2"
}
```

[필드]

| 필드 | 타입 | 설명 |
| --- | --- | --- |
| header | Object | 헤더 영역 |
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 결과 코드 |
| header.resultMessage | String | 결과 메시지 |
| results | List | 관제 상태 변경 이력 목록 |
| results[0].status | String | 관제 상태 |
| results[0].reason | String | 관제 변경 사유 |
| results[0].contents | String | 변경 내용 |
| results[0].vmId | String | 변경 대상 |
| results[0].meter | String | 과금 진행 여부 |
| results[0].type | String | 변경 타입 |
| results[0].regDate | Datetime | 이력 등록 일시 |
| results[0].historyId | Integer | 이력 식별자 |
| count | Integer | 이력 총 개수 |
| previous | String | 이전 페이지 링크 URL |
| next | String | 다음 페이지 링크 URL |


## 보안관제 대응 현황

### 대응 현황 목록 조회

#### 요청

[URI]

| 메서드 | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/tickets |

[예]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/tickets?page=1" \
 -H "Content-Type: application/json"
```

[파라미터]

| 이름 | 타입 | 필수 여부 | 기본값 | 유효 범위 | 설명 |
| --- | --- | --- | --- | --- | --- |
| page | Integer | 선택 | 1 |  | 조회할 페이지 |

#### 응답

[응답 본문]

``` json
{
    "count": 2,
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    },
    "previous": null,
    "results": [
        {
            "detectDate": "2020-02-03T16:49:00+09:00",
            "isAttack": "정탐",
            "ticketStatus": "처리완료",
            "attackType": "Network 침해",
            "srcIp": "120.24.86.122",
            "ticketId": "98425190186514912",
            "dstIp": "103.243.201.11",
            "ticketType": "침해사고",
            "ticketName": "K047_NHN_WebShell_Alert"
        },
        {
            "detectDate": "2016-04-21T01:09:00+09:00",
            "isAttack": "정탐",
            "ticketStatus": "처리완료",
            "attackType": "Brute Force",
            "srcIp": "209.126.122.16",
            "ticketId": "96147997888715867",
            "dstIp": "103.194.108.15",
            "ticketType": "침입탐지",
            "ticketName": "판교IDC 미등록(103.194.108.15) Bruteforce_Inbound"
        }
    ],
    "next": null
}
```

[필드]

| 필드 | 타입 | 설명 |
| --- | --- | --- |
| header | Object | 헤더 영역 |
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 결과 코드 |
| header.resultMessage | String | 결과 메시지 |
| results | List | 대응 현황 목록 |
| results[0].detectDate | DateTime | 탐지 일시 |
| results[0].isAttack | String | 정오탐 |
| results[0].ticketStatus | String | 처리 상태 |
| results[0].attackType | String | 공격 유형 |
| results[0].srcIp | String | 출발지 IP |
| results[0].ticketId | String | 대응 티켓 식별자 |
| results[0].dstIp | String | 도착지 IP |
| results[0].ticketType | String | 티켓 유형 |
| results[0].tickentName | String | 티켓명 |
| count | Integer | 대응 목록 총 개수 |
| previous | String | 이전 페이지 링크 URL |
| next | String | 다음 페이지 링크 URL |

### 대응 현황 상세 정보

#### 요청

[URI]

| 메서드 | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/tickets/{ticketId} |

[예]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/tickets/{ticketId}" \
 -H "Content-Type: application/json"
```

#### 응답

[응답 본문]

``` json
{
    "header": {
        "resultCode": 1,
        "resultMessage": "Service Result",
        "isSuccessful": true
    },
    "data": {
        "result": [
            "TEST 티켓 처리 완료",
            "<table border=\"1\" cellpadding=\"0\" cellspacing=\"0\" class=\"__se_tbl\" style=\"width:1400px\">\r\n\t<tbody>\r\n\t\t<tr>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">이름</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">종료시간</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">위험도</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">공격자 주소</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">공격자 포트</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">공격자 국가</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">목적지 주소</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">목적지 포트</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">목적지 국가</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">탐지방향</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">탐지패턴</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#eaeaea; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">공격횟수</p>\r\n\t\t\t</td>\r\n\t\t</tr>\r\n\t\t<tr>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">UDS_Appkey_PIOLINK</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">2018-08-21 12:07:59</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">Low</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">211.58.124.208</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">50741</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">Korea, Republic of</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">133.186.242.15</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">80</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">Japan</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">Inbound</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">&nbsp;</p>\r\n\t\t\t</td>\r\n\t\t\t<td style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">1</p>\r\n\t\t\t</td>\r\n\t\t</tr>\r\n\t\t<tr>\r\n\t\t\t<td colspan=\"12\" style=\"background-color:#ffffff; height:18px\">\r\n\t\t\t<p style=\"text-align:center\">Total : 1</p>\r\n\t\t\t</td>\r\n\t\t</tr>\r\n\t</tbody>\r\n</table>\r\n",
            "<p>정탐 심화분석 TEST</p>\r\n"
        ],
        "desc": [
            "",
            ""
        ]
    }
}
```

[필드]

| 필드 | 타입 | 설명 |
| --- | --- | --- |
| header | Object | 헤더 영역 |
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 결과 코드 |
| header.resultMessage | String | 결과 메시지 |
| results | List | 대응 현황 상세 정보 목록 |
| results[0] | String | 공격 요약 |
| results[1] | String | 분석 결과 HTML 데이터 |
| results[2] | String | 심화 분석 |
| desc | List | 티켓 상세 정보 목록 |
| desc[0] | String | 티켓명 |
| desc[1] | String | 티켓 설명 |

### 상세 이벤트 현황

#### 요청

[URI]

| 메서드 | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/events |

[예]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/events?page=1&startDate=2021-07-01T20:00:00&endDate=2021-07-13T20:23:59" \
 -H "Content-Type: application/json"
```

[파라미터]

| 이름 | 타입 | 필수 여부 | 기본값 | 유효 범위 | 설명 |
| --- | --- | --- | --- | --- | --- |
| page | Integer | 선택 | 1 |  | 조회할 페이지 |
| startDate | Datetime | 선택 | 하루 전 Datetime |  | 조회 시작 시간 |
| endDate | Datetime | 선택 | 현재 Datetime |  | 조회 종료 시간 |

``` json
{
    "count": 1,
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    },
    "previous": null,
    "results": [
        {
            "detectTime": "2021-07-11T23:36:13+09:00",
            "severityLevel": "Low",
            "dstIp": "133.186.143.56",
            "dstCountryCode": "JP",
            "attackName": "UDS_439_phpmyadmin_access",
            "srcIp": "89.248.168.171",
            "dstPort": 80,
            "srcPort": 33420,
            "inOut": "Inbound"
        }
    ],
    "next": null
}
```

[필드]

| 필드 | 타입 | 설명 |
| --- | --- | --- |
| header | Object | 헤더 영역 |
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 결과 코드 |
| header.resultMessage | String | 결과 메시지 |
| results | List | 상세 이벤트 현황 목록 |
| results[0].detectDate | DateTime | 탐지 일시 |
| results[0].severityLevel | String | 이벤트 위험도 |
| results[0].dstIp | String | 목적지 IP |
| results[0].dstCountryCode | String | 목적지 국가 코드 |
| results[0].attackName | String | 이벤트명 |
| results[0].srcIp | String | 출발지 IP |
| results[0].dstPort | Integer | 목적지 포트 |
| results[0].srcPort | Integer | 출발지 포트 |
| results[0].inOut | String | 통신 방향 |
| count | Integer | 대응 목록 총 개수 |
| previous | String | 이전 페이지 링크 URL |
| next | String | 다음 페이지 링크 URL |
