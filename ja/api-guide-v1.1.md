## Security > Security Monitoring > APIガイド

[APIドメイン]

| リージョン | ドメイン |
| --- | --- |
| 韓国(パンギョ)リージョン | https://kr1-secmon.api.nhncloudservice.com |
| 韓国(ピョンチョン)リージョン | https://kr2-secmon.api.nhncloudservice.com |

## 監視登録API

### 監視 未申請リスト照会

#### リクエスト

[URI]

| メソッド | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/not-applied-vms |

[例]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/not-applied-vms" \
 -H "Content-Type: application/json"
```

#### レスポンス

[レスポンス本文]

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

[フィールド]

| フィールド | タイプ | 説明 |
| --- | --- | --- |
| header | Object | ヘッダ領域 |
| header.isSuccessful | Boolean | 成否 |
| header.resultCode | Integer | 結果コード |
| header.resultMessage | String | 結果メッセージ |
| results | List | 監視未申請状態のvmリスト |
| results[0].lbIp | String | Load BalancerのFloating IP |
| results[0].vm | List | Load Balancerに接続されたVMリスト |
| results[0].vm[0].vmId | String | VMの識別子ID |
| results[0].vm[0].fixedIp | String | VMのFixed IP |
| results[0].vm[0].vmOs | String | VMのOS情報 |
| results[0].vm[0].vmIp | String | VMのFloating IP |
| results[0].vm[0].serviceStatus | String | VMのセキュリティ監視申請状態 |
| results[0].vm[0].vmName | String | VMの名前 |
| results[0].fixedIp | String | Load BalancerのFixed IP |
| results[0].lbId | String | Load Balancerの識別子ID |
| results[0].lbName | String | Load Balancerの名前 |
| results[0].serviceStatus | String | Load Balancerのセキュリティ監視申請状態 |
| results[1].vmId | String | VMの識別子ID |
| results[1].fixedIp | String | VMのFixed IP |
| results[1].vmOs | String | VMのOS情報 |
| results[1].vmIp | String | VMのFloating IP |
| results[1].serviceStatus | String | VMのセキュリティ監視申請状態 |
| results[1].vmName | String | VMの名前 |

### 監視申請リスト照会

#### リクエスト

[URI]

| メソッド | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/applied-vms |

[例]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/applied-vms" \
 -H "Content-Type: application/json"
```

#### レスポンス

[レスポンス本文]

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

[フィールド]

| フィールド | タイプ | 説明 |
| --- | --- | --- |
| header | Object | ヘッダ領域 |
| header.isSuccessful | Boolean | 成否 |
| header.resultCode | Integer | 結果コード |
| header.resultMessage | String | 結果メッセージ |
| results | List | 監視申請された状態のvmリスト |
| results[0].lbIp | String | Load BalancerのFloating IP |
| results[0].vm | List | Load Balancerに接続されたVMリスト |
| results[0].vm[0].vmId | String | VMの識別子ID |
| results[0].vm[0].fixedIp | String | VMのFixed IP |
| results[0].vm[0].vmOs | String | VMのOS情報 |
| results[0].vm[0].vmIp | String | VMのFloating IP |
| results[0].vm[0].serviceStatus | String | VMのセキュリティ監視申請状態 |
| results[0].vm[0].vmName | String | VMの名前 |
| results[0].fixedIp | String | Load BalancerのFixed IP |
| results[0].lbId | String | Load Balancerの識別子ID |
| results[0].lbName | String | Load Balancerの名前 |
| results[0].serviceStatus | String | Load Balancerのセキュリティ監視申請状態 |
| results[1].vmId | String | VMの識別子ID |
| results[1].fixedIp | String | VMのFixed IP |
| results[1].vmOs | String | VMのOS情報 |
| results[1].vmIp | String | VMのFloating IP |
| results[1].serviceStatus | String | VMのセキュリティ監視申請状態 |
| results[1].vmName | String | VMの名前 |

### 監視追加

#### リクエスト

[URI]

| メソッド | URI |
| --- | --- |
| POST | /v1.0/appkeys/{appKey}/vm |


[リクエスト本文]

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

[フィールド]

| 名前 | タイプ | 必須かどうか | デフォルト値 | 有効範囲 | 説明 |
| --- | --- | --- | --- | --- | --- |
| vmList | List | 必須 |  |  | 監視申請vmリスト |
| vmList[0].lbIp | String | 必須 |  |  | Load BalancerのFloating IP |
| vmList[0].vm | List | 必須 |  |  | Load Balancerに接続されたVMリスト |
| vmList[0].vm[0].vmId | String | 必須 |  |  | VMの識別子ID |
| vmList[0].vm[0].fixedIp | String | 必須 |  |  | VMのFixed IP |
| vmList[0].vm[0].vmOs | String | 必須 |  |  | VMのOS情報 |
| vmList[0].vm[0].vmIp | String | 必須 |  |  | VMのFloating IP |
| vmList[0].vm[0].vmName | String | 必須 |  |  | VMの名前 |
| vmList[0].fixedIp | String | 必須 |  |  | Load BalancerのFixed IP |
| vmList[0].lbId | String | 必須 |  |  | Load Balancerの識別子ID |
| vmList[0].lbName | String | 必須 |  |  | Load Balancerの名前 |
| vmList[1].vmId | String | 必須 |  |  | VMの識別子ID |
| vmList[1].fixedIp | String | 必須 |  |  | VMのFixed IP |
| vmList[1].vmOs | String | 必須 |  |  | VMのOS情報 |
| vmList[1].vmIp | String | 必須 |  |  | VMのFloating IP |
| vmList[1].vmName | String | 必須 |  |  | VMの名前 |

* Load Balancerに接続された形態のVMの監視申請を行うには、vmList[0]のデータを必ず入力しなければならず、Load Balancerに接続されていないVMを監視申請するにはvmList[1]のデータを必ず入力する必要があります。

#### レスポンス

[レスポンス本文]

``` json
{
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    }
}
```

### 監視解除

#### リクエスト

[URI]

| メソッド | URI |
| --- | --- |
| DELETE | /v1.0/appkeys/{appKey}/vm |

[例]

```
curl -X DELETE "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/vm?vmId=8b031032-e0a0-4b36-8a98-642b6d3ca07b,1dc707a8-a5be-431e-aca1-77c60af1fe9a" \
 -H "Content-Type: application/json"
```
* Load Balancerに接続された形態のVMを監視解除するにはvmIdパラメータにLoad Balancer IDだけを入力する必要があります。

#### レスポンス

[レスポンス本文]

``` json
{
    "header": {
        "resultCode": 1,
        "resultMessage": "Request success",
        "isSuccessful": true
    }
}
```

### 監視状態変更履歴照会

#### リクエスト

[URI]

| メソッド | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/history |

[パラメータ]

| 名前 | タイプ | 必須かどうか | デフォルト値 | 有効範囲 | 説明 |
| --- | --- | --- | --- | --- | --- |
| page | Integer | 任意 | 1 |  | 照会するページ |

[例]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/history?page=1" \
 -H "Content-Type: application/json"
```

#### レスポンス

[レスポンス本文]

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

[フィールド]

| フィールド | タイプ | 説明 |
| --- | --- | --- |
| header | Object | ヘッダ領域 |
| header.isSuccessful | Boolean | 成否 |
| header.resultCode | Integer | 結果コード |
| header.resultMessage | String | 結果メッセージ |
| results | List | 監視状態変更履歴リスト |
| results[0].status | String | 監視状態 |
| results[0].reason | String | 監視変更理由 |
| results[0].contents | String | 変更内容 |
| results[0].vmId | String | 変更対象 |
| results[0].meter | String | 課金進行 |
| results[0].type | String | 変更タイプ |
| results[0].regDate | Datetime | 履歴登録日時 |
| results[0].historyId | Integer | 履歴識別子 |
| count | Integer | 履歴総数 |
| previous | String | 以前ページリンクURL |
| next | String | 次のページリンクURL |


## セキュリティ監視対応状況

### 対応状況リスト照会

#### リクエスト

[URI]

| メソッド | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/tickets |

[例]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/tickets?page=1" \
 -H "Content-Type: application/json"
```

[パラメータ]

| 名前 | タイプ | 必須かどうか | デフォルト値 | 有効範囲 | 説明 |
| --- | --- | --- | --- | --- | --- |
| page | Integer | 任意 | 1 |  | 照会するページ |

#### レスポンス

[レスポンス本文]

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

[フィールド]

| フィールド | タイプ | 説明 |
| --- | --- | --- |
| header | Object | ヘッダ領域 |
| header.isSuccessful | Boolean | 成否 |
| header.resultCode | Integer | 結果コード |
| header.resultMessage | String | 結果メッセージ |
| results | List | 対応状況リスト |
| results[0].detectDate | DateTime | 検知日時 |
| results[0].isAttack | String | true alerm/false alerm |
| results[0].ticketStatus | String | 処理状態 |
| results[0].attackType | String | 攻撃タイプ |
| results[0].srcIp | String | 送信元IP |
| results[0].ticketId | String | 対応チケット識別子 |
| results[0].dstIp | String | 到着地IP |
| results[0].ticketType | String | チケットタイプ |
| results[0].tickentName | String | チケット |
| count | Integer | 対応リスト総数 |
| previous | String | 以前ページリンクURL |
| next | String | 次のページリンクURL |

### 対応状況詳細情報

#### リクエスト

[URI]

| メソッド | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/tickets/{ticketId} |

[例]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/tickets/{ticketId}" \
 -H "Content-Type: application/json"
```

#### レスポンス

[レスポンス本文]


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

[フィールド]

| フィールド | タイプ | 説明 |
| --- | --- | --- |
| header | Object | ヘッダ領域 |
| header.isSuccessful | Boolean | 成否 |
| header.resultCode | Integer | 結果コード |
| header.resultMessage | String | 結果メッセージ |
| results | List | 対応状況詳細情報リスト |
| results[0] | String | 攻撃要約 |
| results[1] | String | 分析結果HTMLデータ |
| results[2] | String | 深化分析 |
| desc | List | チケット 詳細情報リスト |
| desc[0] | String | チケット名 |
| desc[1] | String | チケットの説明 |

### 詳細イベント状況

#### リクエスト

[URI]

| メソッド | URI |
| --- | --- |
| GET | /v1.0/appkeys/{appKey}/events |

[例]

```
curl -X GET "https://kr1-secmon.api.nhncloudservice.com/v1.0/appkeys/{appKey}/events?page=1&startDate=2021-07-01T20:00:00&endDate=2021-07-13T20:23:59" \
 -H "Content-Type: application/json"
```

[パラメータ]

| 名前 | タイプ | 必須かどうか | デフォルト値 | 有効範囲 | 説明 |
| --- | --- | --- | --- | --- | --- |
| page | Integer | 任意 | 1 |  | 照会するページ |
| startDate | Datetime | 任意 | 1日前のDatetime |  | 照会開始時間 |
| endDate | Datetime | 任意 | 現在Datetime |  | 照会終了時間 |

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

[フィールド]

| フィールド | タイプ | 説明 |
| --- | --- | --- |
| header | Object | ヘッダ領域 |
| header.isSuccessful | Boolean | 成否 |
| header.resultCode | Integer | 結果コード |
| header.resultMessage | String | 結果メッセージ |
| results | List | 詳細イベント状況リスト |
| results[0].detectDate | DateTime | 検知日時 |
| results[0].severityLevel | String | イベントの危険度 |
| results[0].dstIp | String | 宛先IP |
| results[0].dstCountryCode | String | 宛先国コード |
| results[0].attackName | String | イベント名 |
| results[0].srcIp | String | 送信元IP |
| results[0].dstPort | Integer | 宛先ポート |
| results[0].srcPort | Integer | 送信元ポート |
| results[0].inOut | String | 通信方向 |
| count | Integer | 対応リスト総数 |
| previous | String | 以前ページリンクURL |
| next | String | 次のページリンクURL |
