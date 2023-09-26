## Security > Security Monitoring > API Guide

[API domain]

| Region | domain |
| --- | --- |
| Korea (Pangyo) region | https://kr1-secmon.api.nhncloudservice.com |
| Korea (Pyeongchon) region | https://kr2-secmon.api.nhncloudservice.com |

## Control registration API

### Search the list of non-registered control

#### Request

[URI]

| Method | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/not-applied-vms |

[예]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/not-applied-vms" \
 -H "Content-Type: application/json"
```

#### Response

[Response body]

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

[Field]

| Field | Type | Description |
| --- | --- | --- |
| header | Object | Header area |
| header.isSuccessful | Boolean | Success |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Result message |
| results | List | List of vms in non-registered control |
| results[0].lbIp | String | Floating IP of Loadbalancer |
| results[0].vm | List | List of vms connected to Loadbalancer |
| results[0].vm[0].vmId | String | Identifier ID of VM |
| results[0].vm[0].fixedIp | String | Fixed IP of VM |
| results[0].vm[0].vmOs | String | OS information of VM |
| results[0].vm[0].vmIp | String | Floating IP of VM |
| results[0].vm[0].serviceStatus | String | Security control application status of VM |
| results[0].vm[0].vmName | String | VM name |
| results[0].fixedIp | String | Fixed IP of Loadbalancer |
| results[0].lbId | String | Identifier ID of Loadbalancer |
| results[0].lbName | String | Name of Loadbalancer |
| results[0].serviceStatus | String | Security control application status of Loadbalancer |
| results[1].vmId | String | Identifier ID of VM |
| results[1].fixedIp | String | Fixed IP of VM |
| results[1].vmOs | String | OS information of VM |
| results[1].vmIp | String | Floating IP of VM |
| results[1].serviceStatus | String | Security control application status of VM |
| results[1].vmName | String | VM name |

### Search the list of control application

#### Request

[URI]

| Method | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/applied-vms |

[Example]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/applied-vms" \
 -H "Content-Type: application/json"
```

#### Response

[Response body]

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

[Field]

| Field | Type | Description |
| --- | --- | --- |
| header | Object | Header area |
| header.isSuccessful | Boolean | Success |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Result message |
| results | List | List of vms in non-registered control |
| results[0].lbIp | String | Floating IP of Loadbalancer |
| results[0].vm | List | List of vms connected to Loadbalancer |
| results[0].vm[0].vmId | String | Identifier ID of VM |
| results[0].vm[0].fixedIp | String | Fixed IP of VM |
| results[0].vm[0].vmOs | String | OS information of VM |
| results[0].vm[0].vmIp | String | Floating IP of VM |
| results[0].vm[0].serviceStatus | String | Security control application status of VM |
| results[0].vm[0].vmName | String | VM name |
| results[0].fixedIp | String | Fixed IP of Loadbalancer |
| results[0].lbId | String | Identifier ID of Loadbalancer |
| results[0].lbName | String | Name of Loadbalancer |
| results[0].serviceStatus | String | Security control application status of Loadbalancer |
| results[1].vmId | String | Identifier ID of VM |
| results[1].fixedIp | String | Fixed IP of VM |
| results[1].vmOs | String | OS information of VM |
| results[1].vmIp | String | Floating IP of VM |
| results[1].serviceStatus | String | Security control application status of VM |
| results[1].vmName | String | VM name |

### Add control

#### Request

[URI]

| Method | URI |
| --- | --- |
| POST | /v1.0/appkeys/{appKey}/vm |

[Request body]

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

[Field]

| Name | Type | Necessity | Default | Valid range | Description |
| --- | --- | --- | --- | --- | --- |
| vmList | List | Required |  |  | List of vms of control registeration |
| vmList[0].lbIp | String | Required |  |  | Floating IP of Loadbalancer |
| vmList[0].vm | List | Required |  |  | List of vms connected to Loadbalancer |
| vmList[0].vm[0].vmId | String | Required |  |  | Identifier ID of VM |
| vmList[0].vm[0].fixedIp | String | Required |  |  | Fixed IP of VM |
| vmList[0].vm[0].vmOs | String | Required |  |  | OS information of VM |
| vmList[0].vm[0].vmIp | String | Required |  |  | Floating IP of VM |
| vmList[0].vm[0].vmName | String | Required |  |  | VM name |
| vmList[0].fixedIp | String | Required |  |  | Fixed IP of Loadbalancer |
| vmList[0].lbId | String | Required |  |  | Identifier ID of Loadbalancer |
| vmList[0].lbName | String | Required |  |  | Name of Loadbalancer |
| vmList[1].vmId | String | Required |  |  | Identifier ID of VM |
| vmList[1].fixedIp | String | Required |  |  | Fixed IP of VM |
| vmList[1].vmOs | String | Required |  |  | OS information of VM |
| vmList[1].vmIp | String | Required |  |  | Floating IP of VM |
| vmList[1].vmName | String | Required |  |  | VM name |

* The data of vmList[0] must be entered to apply for control of the VM connected to the Loadbalancer and the data of vmList[1] must be entered to apply for control of the VM not connected to the Loadbalancer.

#### Response

[Response body]

``` json
{
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    }
}
```

### Release control

#### Request

[URI]

| Method | URI |
| --- | --- |
| DELETE | /v1.0/appkeys/{appKey}/vm |

[Example]

```
curl -X DELETE "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/vm?vmId=8b031032-e0a0-4b36-8a98-642b6d3ca07b,1dc707a8-a5be-431e-aca1-77c60af1fe9a" \
 -H "Content-Type: application/json"
```
* To remove the control of VM which is connected to the Load Balancer, only Load Balancer ID must be entered in the vmId parameter.

#### Response

[Response body]

``` json
{
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    }
}
```

### Viewing change history of control status

#### Request

[URI]

| Method | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/history |

[Parameter]

| Name | Type | Necessity | Default | Valid range | Description |
| --- | --- | --- | --- | --- | --- |
| page | Integer | Optional | 1 |  | Page to search |

[Example]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/history?page=1" \
 -H "Content-Type: application/json"
```

#### Response

[Response body]

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

[Field]

| Field | Type | Description |
| --- | --- | --- |
| header | Object | Header area |
| header.isSuccessful | Boolean | Success |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Result message |
| results | List | List of change history of control status |
| results[0].status | String | Control status |
| results[0].reason | String | Reason to change control |
| results[0].contents | String | Change detail |
| results[0].vmId | String | Changing subject |
| results[0].meter | String | Billing status |
| results[0].type | String | Change type |
| results[0].regDate | Datetime | History registration date |
| results[0].historyId | Integer | History identifier |
| count | Integer | Total number of history |
| previous | String | URL link to previous page |
| next | String | URL link to next page |


## Security control response status

### Search response status list

#### Request

[URI]

| Method | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/tickets |

[Example]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/tickets?page=1" \
 -H "Content-Type: application/json"
```

[Parameter]

| Name | Type | Necessity | Default | Valid range | Description |
| --- | --- | --- | --- | --- | --- |
| page | Integer | Optional | 1 |  | Page to search |

#### Response

[Response body]

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

[Field]

| Field | Type | Description |
| --- | --- | --- |
| header | Object | Header area |
| header.isSuccessful | Boolean | Success |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Result message |
| results | List | Response status list |
| results[0].detectDate | DateTime | Detection date |
| results[0].isAttack | String | True/False Positive |
| results[0].ticketStatus | String | Processing status |
| results[0].attackType | String | Attack type |
| results[0].srcIp | String | Departure IP |
| results[0].ticketId | String | Response ticket identifier |
| results[0].dstIp | String | Destination IP |
| results[0].ticketType | String | Ticket type |
| results[0].tickentName | String | Ticket name |
| count | Integer | Total number of response list |
| previous | String | URL link to previous page |
| next | String | URL link to next page |

### Detailed information on response status

#### Request

[URI]

| Method | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/tickets/{ticketId} |

[Example]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/tickets/{ticketId}" \
 -H "Content-Type: application/json"
```

#### Response

[Response body]

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

[Field]

| Field | Type | Description |
| --- | --- | --- |
| header | Object | Header area |
| header.isSuccessful | Boolean | Success |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Result message |
| results | List | List of detailed information on response status |
| results[0] | String | Attack summary |
| results[1] | String | HTML data of analysis result |
| results[2] | String | Deep analysis |
| desc | List | List of detailed information on ticket |
| desc[0] | String | Ticket name |
| desc[1] | String | Ticket description |

### Detailed event status

#### Request

[URI]

| Method | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/events |

[Example]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/events?page=1&startDate=2021-07-01T20:00:00&endDate=2021-07-13T20:23:59" \
 -H "Content-Type: application/json"
```

[Parameter]

| Name | Type | Necessity | Default | Valid range | Description |
| --- | --- | --- | --- | --- | --- |
| page | Integer | Optional | 1 |  | Page to search |
| startDate | Datetime | Optional | Datetime before a day |  | Search Start time |
| endDate | Datetime | Optional | Current Datetime |  | End time |

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

[Field]

| Field | Type | Description |
| --- | --- | --- |
| header | Object | Header area |
| header.isSuccessful | Boolean | Success |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Result message |
| results | List | List of detailed event status |
| results[0].detectDate | DateTime | Detection date |
| results[0].severityLevel | String | Event risk level |
| results[0].dstIp | String | Destination IP |
| results[0].dstCountryCode | String | Destination country code |
| results[0].attackName | String | Event name |
| results[0].srcIp | String | Departure IP |
| results[0].dstPort | Integer | Destination port |
| results[0].srcPort | Integer | Departure port |
| results[0].inOut | String | Communication direction |
| count | Integer | Total number of response list |
| previous | String | URL link to previous page |
| next | String | URL link to next page |
