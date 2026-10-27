<!-- pre-align:aligned sig=de8ccb25881e -->

<a id="security-ddos-guard-l7-ddos-security-configuration-guide"></a>
## Security > DDoS Guard > L7 DDoS 보안 설정 가이드 { #security-ddos-guard-l7-ddos-security-configuration-guide }

여기에서는 L7 DDoS 공격을 효과적으로 대응하기 위한 보안 설정 방법을 설명합니다.

<a id="background"></a>
## 1. 배경 { #background }

* L7 Slow DDoS 공격 지속 증가
    * Slowloris, Slow Read 등 네트워크 대역폭이 아닌 애플리케이션 계층의 세션을 장시간 점유하는 공격이 빈번히 발생합니다.
    * 전체 트래픽량은 적더라도 웹 서버의 Connection/Session 자원을 빠르게 고갈시켜 정상 사용자의 접근을 차단합니다.
* 탐지 난이도 상향
    * HTTPS 암호화 트래픽 내에 정상적인 HTTP 요청처럼 위장하여 유입되므로, 단순 L3/L4 임계치(Threshold) 기반 Anti-DDoS 장비만으로는 대응에 한계가 있습니다.

<a id="purpose"></a>
## 2. 목적 { #purpose }

* 종합적 방어 체계 수립
    * 서버, 네트워크, 애플리케이션 등 다중 계층 보안 정책을 수립합니다.
* 웹 서버 자원 고갈 완화
    * 세션 기반 공격 유입 시 연결 수 및 대기 시간 설정을 통해 서버 리소스를 보호합니다.
* 서비스 가용성(Availability) 확보
    * 적절한 세션 유지 시간 및 최대 연결 수 관리를 통해 정상 서비스 유지를 도모합니다. 

<a id="security-measures"></a>
## 3. 보안 대책 { #security-measures }

* 웹 서버 하드닝(Web Server Hardening)
    * KeepAliveTimeout, RequestReadTimeout, client_body_timeout 등 세션 설정을 최적화하여 비정상 연결로 인한 리소스 점유를 최소화합니다.
* Anti-DDoS 솔루션 국가 기반 선 차단 설정
    * 차단 기준: L7 DDoS 공격으로 인해 웹 서비스 지연 또는 장애(접근 불가)가 발생할 경우 적용합니다.
    * 국가 기준: 긴급 상황 발생 시 국내 및 주요 서비스 국가(예: 한국, 일본 등)를 제외한 해외 출발지 IP 대역 전체를 차단합니다.
    * 복구 절차: 공격 트래픽 감소 및 상황 종료를 확인한 후, 국가 차단 정책을 해제하여 정상 서비스 상태로 원복합니다.

<a id="security-checklist"></a>
## 4. 보안 점검 리스트 { #security-checklist }

<a id="nginx"></a>
### Nginx { #nginx }

| 번호 | 구분 | 항목 | 확인 여부 | 비고 |
| --- | --- | --- | ---- | ---- |
| 1 | 보안 솔루션 | WEB Firewall 구축 및 운영하고 있는지? |  |  |
| 2 | 시스템 | 요청 속도 제한(Rate Limit) 설정이 되었는지? |  |  |
| 3 | 시스템 | 동시 연결 제한(Connection Limit) 설정이 되었는지? |  |  |
| 4 | 시스템 | 요청 본문 크기 제한 설정이 되었는지? |  |  |
| 5 | 시스템 | 버퍼 크기 제한 설정이 되었는지? |  |  |
| 6 | 시스템 | Keep-Alive 제한 설정이 되었는지? |  |  |
| 7 | 시스템 | 요청 대기 시간 제한 설정이 되었는지? |  |  |
| 8 | 시스템 | HTTP Method 제한 설정이 되었는지? |  |  |
| 9 | 시스템 | 비정상 User-Agent 차단 설정이 되었는지? |  |  |
| 10 | 시스템 | 상태 모니터링 설정이 되었는지? |  |  |
| 11 | 시스템 | 캐싱 설정이 되었는지? |  |  |

<a id="apache"></a>
### Apache { #apache }

| 번호 | 구분 | 항목 | 확인 여부 | 비고 |
| --- | --- | --- | ---- | ---- |
| 1 | 보안 솔루션 | WEB Firewall 구축 및 운영하고 있는지? |  |  |
| 2 | 시스템 | mod_evasive 설정이 되었는지? |  |  |
| 3 | 시스템 | mod_qos 설정이 되었는지? |  |  |
| 4 | 시스템 | KeepAlive 제한 설정이 되었는지? |  |  |
| 5 | 시스템 | 요청 본문 크기 제한 설정이 되었는지? |  |  |
| 6 | 시스템 | Timeout 조정 설정이 되었는지? |  |  |
| 7 | 시스템 | HTTP Method 제한 설정이 되었는지? |  |  |
| 8 | 시스템 | User-Agent 필터링 설정이 되었는지? |  |  |
| 9 | 시스템 | 요청 속도 제한(mod_ratelimit) 설정이 되었는지? |  |  |
| 10 | 시스템 | 로그 포맷 강화 설정이 되었는지? |  |  |

<a id="netty"></a>
### Netty { #netty }

| 번호 | 구분 | 항목 | 확인 여부 | 비고 |
| --- | --- | --- | ---- | ---- |
| 1 | 보안 솔루션 | WEB Firewall 구축 및 운영하고 있는지? |  |  |
| 2 | 시스템 | 요청 속도 제한(Rate Limit) 적용되어 있는가? |  |  |
| 3 | 시스템 | 동시 연결 수 제한(Connection Limit) 적용되어 있는가? |  |  |
| 4 | 시스템 | 요청 본문 크기 제한 설정이 있는가? |  |  |
| 5 | 시스템 | 헤더/버퍼 크기 제한 설정이 있는가? |  |  |
| 6 | 시스템 | Keep-Alive / Idle Timeout 설정이 있는가? |  |  |
| 7 | 시스템 | 요청 처리 시간 제한 설정이 있는가? |  |  |
| 8 | 시스템 | HTTP Method 제한 설정이 있는가? |  |  |
| 9 | 시스템 | 비정상 User-Agent 차단 로직이 있는가? |  |  |
| 10 | 시스템 | 상태 모니터링 및 Metrics 수집이 되는가? |  |  |
| 11 | 시스템 | 캐시 또는 응답 최적화 적용 여부 |  |  |

<a id="security-configuration-guide"></a>
## 5. 보안 설정 가이드 { #security-configuration-guide }

보안 설정 시 웹 서비스 장애를 최소화하려면 환경을 고려해야 합니다.

<a id="security-configuration-guide-nginx"></a>
### Nginx { #security-configuration-guide-nginx }

| 번호 | 항목 | 설정 방법 | 내용 | 우선순위 | 예시 |
| --- | --- | --- | ---- | ---- | ---- |
| 1 | 요청 속도 제한(Rate Limit) | limit_req_zone / limit_req 설정 | IP별 초당 요청 수 제한으로 과도한 HTTP 요청 방어 | 필수 | http {<BR>   limit_req_zone $binary_remote_addr zone=req_limit_per_ip:10m rate=5r/s; <BR>} server {<BR>   limit_req zone=req_limit_per_ip burst=10 nodelay; <BR>} |
| 2 | 동시 연결 제한(Connection Limit) | limit_conn_zone / limit_conn 설정 | 하나의 IP에서 동시에 맺을 수 있는 연결 수 제한 | 필수 | http {<BR>   limit_conn_zone $binary_remote_addr zone=conn_limit_per_ip:10m; <BR>} server {<BR>   limit_conn conn_limit_per_ip 10; <BR>} |
| 3 | 요청 본문 크기 제한 | client_max_body_size 설정 | 대용량 POST 요청으로 인한 리소스 고갈 방지 | 필수 | client_max_body_size 1m; |
| 4 | 버퍼 크기 제한 | client_body_buffer_size, client_header_buffer_size 설정 | 요청 헤더·본문 버퍼 사용량 제한(Slowloris 공격 방어) | 필수 | client_body_buffer_size 16k; <BR>client_header_buffer_size 1k; |
| 5 | Keep-Alive 제한 | keepalive_timeout 설정 | 클라이언트의 세션 점유 시간 제한 | 필수 | keepalive_timeout 10s; |
| 6 | 요청 대기 시간 제한 | client_header_timeout, send_timeout 설정 | 느린 요청(Slow HTTP) 공격 방어 | 필수 | client_header_timeout 10s; <BR>send_timeout 10s; |
| 7 | HTTP Method 제한 | if문으로 허용된 메서드만 제한 | 불필요한 메서드(TRACE, PUT 등) 요청 차단 | 권고 | if ($request_method !~ ^(GET\|POST\|HEAD)$) { return 444; } |
| 8 | 비정상 User-Agent 차단 | 정규식으로 User-Agent 필터링 | 스캐너, 봇, curl 등 자동화 툴 접근 차단 | 권고 | if ($http_user_agent ~* (masscan\|curl\|python\|nmap)) { return 403; } |
| 9 | 상태 모니터링 | stub_status 설정 | 실시간 요청/세션 수 확인(운영 점검용) | 권고 | location /nginx_status {<BR>   stub_status;<BR>   allow 127.0.0.1;<BR>   deny all; <BR>} |
| 10 | 캐싱 설정 | proxy_cache 설정 | 동일 요청 캐싱으로 백엔드 부하 감소 | 권고 | proxy_cache_path /tmp/nginx_cache levels=1:2 keys_zone=my_cache:10m; <BR>location / {<BR>   proxy_cache my_cache;<BR>   proxy_cache_use_stale error timeout updating; <BR>} |

<a id="security-configuration-guide-apache"></a>
### Apache { #security-configuration-guide-apache }

| 번호 | 항목 | 설정 방법 | 내용 | 우선순위 | 예시 |
| --- | --- | --- | ---- | ---- | ---- |
| 1 | mod_evasive 설정 | yum install mod_evasive 후 /etc/httpd/conf.d/mod_evasive.conf 설정 | 짧은 시간 내 다수 요청 IP 자동 차단 | 필수 | DOSPageCount 2 <BR>DOSSiteCount 50 <BR>DOSBlockingPeriod 10 |
| 2 | mod_qos 설정 | yum install mod_qos 후 /etc/httpd/conf.d/mod_qos.conf | IP별 최대 연결 수 및 요청 수 제한 | 필수 | QS_SrvMaxConnPerIP 10 <BR>QS_SrvMaxConnClose 20 <BR>QS_SrvRequestRate 5 |
| 3 | KeepAlive 제한 | KeepAliveTimeout 설정 | 장시간 연결 유지 방지 | 필수 | KeepAlive On <BR>MaxKeepAliveRequests 100 <BR>KeepAliveTimeout 5 |
| 4 | 요청 본문 크기 제한 | LimitRequestBody 설정 | 대용량 POST 요청 제한 | 필수 | LimitRequestBody 1048576 |
| 5 | Timeout 조정 | Timeout, RequestReadTimeout 설정 | 느린 요청/응답 차단 | 필수 | Timeout 10 <BR>RequestReadTimeout header=10-20,MinRate=500 |
| 6 | HTTP Method 제한 | <LimitExcept\> 블록 사용 | 허용된 메서드만 허용 | 필수 | <LimitExcept GET POST HEAD\><BR>   Deny from all <BR></LimitExcept\> |
| 7 | User-Agent 필터링 | SetEnvIfNoCase + Deny | 비정상 User-Agent 차단 | 권고 | SetEnvIfNoCase User-Agent "curl" bad_bot <BR>Order Allow,Deny <BR>Allow from all <BR>Deny from env=bad_bot |
| 8 | 요청 속도 제한(mod_ratelimit) | mod_ratelimit 사용 | 응답 전송 속도 제한으로 과도한 요청 억제 | 권고 | SetOutputFilter RATE_LIMIT <BR>SetEnv rate-limit 400 |
| 9 | 로그 포맷 강화 | LogFormat 수정 | 요청, 응답 크기, User-Agent 포함해 추적성 강화 | 권고 | LogFormat "%h %l %u %t \\"%r\\" %>s %b \\"%{Referer}i\\" \\"%{User-Agent}i\\"" combined |

<a id="security-configuration-guide-netty"></a>
### Netty { #security-configuration-guide-netty }

| 번호 | 항목 | 설정 방법 | 내용 | 우선순위 | 예시 | 비고 |
| --- | --- | --- | ---- | ---- | ---- | ---- |
| 1 | 요청 속도 제한(Rate Limit) | ChannelHandler / Redis / Guava RateLimiter | IP 기반 요청 수 제한 | 필수 | `SimpleRateTracker(5, 10)` | 초당 5개 ~ 15개까지 허용 |
| 2 | 동시 연결 제한(Connection Limit) | ChannelGroup / Atomic Counter | IP별 동시 연결 제한 | 필수 | `MAX_CONN_PER_IP = 10` | IP당 동시 연결 수 10개 제한 |
| 3 | 요청 본문 크기 제한 | HttpObjectAggregator | 대용량 POST 공격 방지 | 필수 | `new HttpObjectAggregator(1024 * 1024)` | POST Body 요청 1MB로 제한 |
| 4 | 버퍼 크기 제한 | HttpServerCodec 설정 | 헤더/라인 길이 제한 | 필수 | `new HttpServerCodec(4096, 1024, 8192)` | 비정상적으로 큰 Header/URI 요청 제한(line 4096 / header 1024 / chunk 8192) |
| 5 | Keep-Alive 제한 | IdleStateHandler | 유휴 세션 이벤트 발생 | 필수 | `new IdleStateHandler(10, 10, 10)` | 10초 동안 이벤트 발생하지 않으면 이벤트 발생(읽기/쓰기/읽기&쓰기) |
| 6 | 요청 시간 제한 | ReadTimeoutHandler / WriteTimeoutHandler | Slowloris 대응 | 필수 | `new ReadTimeoutHandler(10)`<BR>`new WriteTimeoutHandler(10)` |  |
| 7 | HTTP Method 제한 | ChannelInboundHandler | 허용 메서드만 처리 | 권고 | `if (!(request.method().equals(HttpMethod.GET)`<BR>`  \|\| request.method().equals(HttpMethod.POST)`<BR>`  \|\| request.method().equals(HttpMethod.HEAD))) {`<BR>`  ctx.close();`<BR>`  return;`<BR>`}` | GET,POST,HEAD Method만 허용 |
| 8 | User-Agent 차단 | Handler에서 Header 검사 | 스캐너/봇 차단 | 권고 | `String ua = request.headers().get("User-Agent");`<BR> `if(ua != null && ua.matches(".(masscan\|curl\|python\|nmap).")) {`<BR>`  ctx.close();`<BR>`  return;`<BR>`}` | masscan/curl/python/nmap 패턴 탐지 |
| 9 | 상태 모니터링 | Micrometer / Prometheus | TPS, 연결수 모니터링 | 권고 |  |  |
| 10 | 캐시 설정 | Caffeine / Redis | 백엔드 부하 감소 | 권고 |  |  |

<a id="load-balancer"></a>
### Load Balancer { #load-balancer }

| 번호 | 항목 | 설정 방법 | 내용 | 예시 | 비고 |
| --- | --- | --- | ---- | ---- | ---- |
| 1 | 세션 연결 제한 | 연결 제한 설정 | 리스너가 동시에 유지할 TCP 세션의 수를 지정 | `기본값 : 60,000` <BR>`서비스 특성에 따라 단계적 조정 필요` |  |
| 2 | Keep-Alive 제한 | Keep-Alive 타임아웃 설정 | 클라이언트 및 서버와의 세션 유지 시간을 초 단위로 지정 | `기본값 : 300초` |  |
| 3 | 비정상 요청 자동 차단 | 유효하지 않은 요청 차단 설정 | HTTP 요청 헤더에 유효하지 않은 문자가 포함된 경우 차단 | `기본값 : 사용` |  |
