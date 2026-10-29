<!-- machine_translated: true -->

<!-- pre-align:aligned sig=de8ccb25881e -->

<a id="security-ddos-guard-l7-ddos-security-configuration-guide"></a>
## Security > DDoS Guard > L7 DDoS Security Configuration Guide { #security-ddos-guard-l7-ddos-security-configuration-guide }

This document explains how to configure security settings to effectively respond to L7 DDoS attacks.

<a id="background"></a>
## 1. Background { #background }

* Increasing L7 Slow DDoS attacks
    * Attacks such as Slowloris and Slow Read, which occupy application-layer sessions for extended periods rather than consuming network bandwidth, occur frequently.
    * Even with relatively low overall traffic volume, these attacks rapidly exhaust the Connection/Session resources of web servers, blocking access for legitimate users.
* Increasing detection difficulty
    * Because these attacks are disguised as normal HTTP requests within HTTPS-encrypted traffic, simple L3/L4 threshold-based Anti-DDoS devices alone have limited effectiveness.

<a id="purpose"></a>
## 2. Purpose { #purpose }

* Establish a comprehensive defense system
    * Establish multi-layer security policies covering the server, network, and application layers.
* Mitigate web server resource exhaustion
    * Protect server resources during session-based attacks by configuring connection counts and wait time settings.
* Ensure service availability
    * Maintain normal service by managing appropriate session maintenance times and maximum connection counts.

<a id="security-measures"></a>
## 3. Security Measures { #security-measures }

* Web server hardening
    * Minimize resource occupancy caused by abnormal connections by optimizing session settings such as KeepAliveTimeout, RequestReadTimeout, and client_body_timeout.
* Country-based pre-blocking configuration for Anti-DDoS solutions
    * Blocking criteria: Apply when web service delays or failures (inaccessibility) occur due to L7 DDoS attacks.
    * Country criteria: In the event of an emergency, block all overseas source IP ranges except for domestic and major service countries (e.g., Korea, Japan).
    * Recovery procedure: After confirming a reduction in attack traffic and the end of the incident, lift the country-based blocking policy to restore normal service.

<a id="security-checklist"></a>
## 4. Security Checklist { #security-checklist }

<a id="nginx"></a>
### Nginx { #nginx }

| Number | Category | Item | Checked | Notes |
| --- | --- | --- | ---- | ---- |
| 1 | Security solution | Is a WEB Firewall deployed and operational? |  |  |
| 2 | System | Is the request rate limit (Rate Limit) configured? |  |  |
| 3 | System | Is the connection limit (Connection Limit) configured? |  |  |
| 4 | System | Is the request body size limit configured? |  |  |
| 5 | System | Is the buffer size limit configured? |  |  |
| 6 | System | Is the Keep-Alive limit configured? |  |  |
| 7 | System | Is the request wait time limit configured? |  |  |
| 8 | System | Is the HTTP Method restriction configured? |  |  |
| 9 | System | Is the block abnormal user agents setting configured? |  |  |
| 10 | System | Is the status monitoring configured? |  |  |
| 11 | System | Is the caching settings configured? |  |  |

<a id="apache"></a>
### Apache { #apache }

| Number | Category | Item | Checked | Notes |
| --- | --- | --- | ---- | ---- |
| 1 | Security solution | Is a WEB Firewall deployed and operational? |  |  |
| 2 | System | Is mod_evasive configured? |  |  |
| 3 | System | Is mod_qos configured? |  |  |
| 4 | System | Is the KeepAlive limit configured? |  |  |
| 5 | System | Is the request body size limit configured? |  |  |
| 6 | System | Is the Timeout adjustment configured? |  |  |
| 7 | System | Is the HTTP Method restriction configured? |  |  |
| 8 | System | Is the User-Agent filtering configured? |  |  |
| 9 | System | Is the request rate limit (mod_ratelimit) configured? |  |  |
| 10 | System | Is the enhanced log format configured? |  |  |

<a id="netty"></a>
### Netty { #netty }

| Number | Category | Item | Checked | Notes |
| --- | --- | --- | ---- | ---- |
| 1 | Security solution | Is a WEB Firewall deployed and operational? |  |  |
| 2 | System | Is the request rate limit (Rate Limit) applied? |  |  |
| 3 | System | Is the connection limit (Connection Limit) applied? |  |  |
| 4 | System | Is the request body size limit configured? |  |  |
| 5 | System | Is the header/buffer size limit configured? |  |  |
| 6 | System | Is the Keep-Alive / Idle Timeout configured? |  |  |
| 7 | System | Is the request processing time limit configured? |  |  |
| 8 | System | Is the HTTP Method restriction configured? |  |  |
| 9 | System | Is there logic to block abnormal user agents? |  |  |
| 10 | System | Is status monitoring and metrics collection enabled? |  |  |
| 11 | System | Is cache or response optimization applied? |  |  |

<a id="security-configuration-guide"></a>
## 5. Security Configuration Guide { #security-configuration-guide }

When configuring security settings, you must consider your environment to minimize web service disruptions.

<a id="security-configuration-guide-nginx"></a>
### Nginx { #security-configuration-guide-nginx }

| Number | Item | How to configure | Content | Priority | Example |
| --- | --- | --- | ---- | ---- | ---- |
| 1 | Request rate limit | Set limit_req_zone / limit_req | Prevent excessive HTTP requests by limiting the number of requests per second by IP | Required | http {<BR>   limit_req_zone $binary_remote_addr zone=req_limit_per_ip:10m rate=5r/s; <BR>} server {<BR>   limit_req zone=req_limit_per_ip burst=10 nodelay; <BR>} |
| 2 | Connection limit | Set limit_conn_zone / limit_conn | Limit the number of simultaneous connections from a single IP | Required | http {<BR>   limit_conn_zone $binary_remote_addr zone=conn_limit_per_ip:10m; <BR>} server {<BR>   limit_conn conn_limit_per_ip 10; <BR>} |
| 3 | Request body size limit | Set client_max_body_size | Prevent resource exhaustion due to large POST requests | Required | client_max_body_size 1m; |
| 4 | Buffer size limit | Set client_body_buffer_size and client_header_buffer_size | Limit request header and body buffer usage (Slowloris attack defense) | Required | client_body_buffer_size 16k; <BR>client_header_buffer_size 1k; |
| 5 | Keep-Alive limit | Set keepalive_timeout | Limit client session occupancy time | Required | keepalive_timeout 10s; |
| 6 | Request wait time limit | Set client_header_timeout and send_timeout | Prevent slow request (Slow HTTP) attacks | Required | client_header_timeout 10s; <BR>send_timeout 10s; |
| 7 | Restrict HTTP methods | Restrict only allowed methods with if statements | Block requests for unnecessary methods (TRACE, PUT, etc.) | Recommended | if ($request_method !~ ^(GET\|POST\|HEAD)$) { return 444; } |
| 8 | Block abnormal user agents | Filter user agents with regular expressions | Block access from automated tools such as scanners, bots, and curl | Recommended | if ($http_user_agent ~* (masscan\|curl\|python\|nmap)) { return 403; } |
| 9 | Status monitoring | Set stub_status | Check the number of requests/sessions in real time (for operational maintenance) | Recommended | location /nginx_status {<BR>   stub_status;<BR>   allow 127.0.0.1;<BR>   deny all; <BR>} |
| 10 | Caching settings | Proxy cache settings | Reducing backend load by caching identical requests | Recommended | proxy_cache_path /tmp/nginx_cache levels=1:2 keys_zone=my_cache:10m; <BR>location / {<BR>   proxy_cache my_cache;<BR>   proxy_cache_use_stale error timeout updating; <BR>} |

<a id="security-configuration-guide-apache"></a>
### Apache { #security-configuration-guide-apache }

| Number | Item | How to configure | Content | Priority | Example |
| --- | --- | --- | ---- | ---- | ---- |
| 1 | Configuring mod_evasive | After installing mod_evasive with yum, configure /etc/httpd/conf.d/mod_evasive.conf | Automatically block IP addresses that make multiple requests within a short period of time | Required | DOSPageCount 2 <BR>DOSSiteCount 50 <BR>DOSBlockingPeriod 10 |
| 2 | mod_qos settings | yum install mod_qos and then /etc/httpd/conf.d/mod_qos.conf | Maximum connections and requests per IP | Required | QS_SrvMaxConnPerIP 10 <BR>QS_SrvMaxConnClose 20 <BR>QS_SrvRequestRate 5 |
| 3 | KeepAlive limit | Set KeepAliveTimeout | Prevent long-duration connection maintenance | Required | KeepAlive On <BR>MaxKeepAliveRequests 100 <BR>KeepAliveTimeout 5 |
| 4 | Request body size limit | Set LimitRequestBody | Limit large POST requests | Required | LimitRequestBody 1048576 |
| 5 | Timeout adjustment | Set Timeout and RequestReadTimeout | Block slow requests/responses | Required | Timeout 10 <BR>RequestReadTimeout header=10-20,MinRate=500 |
| 6 | Restrict HTTP methods | Use \<LimitExcept\> block | Allow only permitted methods | Required | \<LimitExcept GET POST HEAD\><BR>   Deny from all <BR>\</LimitExcept\> |
| 7 | User-Agent filtering | SetEnvIfNoCase + Deny | Block abnormal user agents | Recommended | SetEnvIfNoCase User-Agent "curl" bad_bot <BR>Order Allow,Deny <BR>Allow from all <BR>Deny from env=bad_bot |
| 8 | Request rate limit (mod_ratelimit) | Using mod_ratelimit | Limiting response rates to prevent excessive requests | Recommended | SetOutputFilter RATE_LIMIT <BR>SetEnv rate-limit 400 |
| 9 | Enhanced log format | Modified LogFormat | Enhanced traceability, including request and response sizes and User-Agent | Recommended | LogFormat "%h %l %u %t \\"%r\\" %>s %b \\"%{Referer}i\\" \\"%{User-Agent}i\\"" combined |

<a id="security-configuration-guide-netty"></a>
### Netty { #security-configuration-guide-netty }

| Number | Item | How to configure | Content | Priority | Example | Notes |
| --- | --- | --- | ---- | ---- | ---- | ---- |
| 1 | Request rate limit | ChannelHandler / Redis / Guava RateLimiter | Limit requests by IP | Required | `SimpleRateTracker(5, 10)` | Allow from 5 to 15 requests per second |
| 2 | Connection limit | ChannelGroup / Atomic Counter | Limit simultaneous connections per IP | Required | `MAX_CONN_PER_IP = 10` | Limit of 10 simultaneous connections per IP |
| 3 | Request body size limit | HttpObjectAggregator | Prevent large POST attacks | Required | `new HttpObjectAggregator(1024 * 1024)` | Limit POST body requests to 1 MB |
| 4 | Buffer size limit | HttpServerCodec settings | Limit header/line length | Required | `new HttpServerCodec(4096, 1024, 8192)` | Limit abnormally large Header/URI requests (line 4096 / header 1024 / chunk 8192) |
| 5 | Keep-Alive limit | IdleStateHandler | Trigger events for idle sessions | Required | `new IdleStateHandler(10, 10, 10)` | Triggers an event if no event occurs for 10 seconds (read/write/read&write) |
| 6 | Request time limit | ReadTimeoutHandler / WriteTimeoutHandler | Defend against Slowloris | Required | `new ReadTimeoutHandler(10)`<BR>`new WriteTimeoutHandler(10)` |  |
| 7 | Restrict HTTP methods | ChannelInboundHandler | Process only allowed methods | Recommended | `if (!(request.method().equals(HttpMethod.GET)`<BR>`  \|\| request.method().equals(HttpMethod.POST)`<BR>`  \|\| request.method().equals(HttpMethod.HEAD))) {`<BR>`  ctx.close();`<BR>`  return;`<BR>`}` | Allow only GET, POST, and HEAD methods |
| 8 | Block user agents | Inspect headers in handler | Block scanners/bots | Recommended | `String ua = request.headers().get("User-Agent");`<BR> `if(ua != null && ua.matches(".(masscan\|curl\|python\|nmap).")) {`<BR>`  ctx.close();`<BR>`  return;`<BR>`}` | Detect masscan/curl/python/nmap patterns |
| 9 | Status monitoring | Micrometer / Prometheus | Monitor TPS and connection count | Recommended |  |  |
| 10 | Cache settings | Caffeine / Redis | Reduce backend load | Recommended |  |  |

<a id="load-balancer"></a>
### Load Balancer { #load-balancer }

| Number | Item | How to configure | Content | Example | Notes |
| --- | --- | --- | ---- | ---- | ---- |
| 1 | Session connection limit | Connection limit settings | Specify the number of TCP sessions that the listener maintains simultaneously | `Default: 60,000` <BR>`Step-by-step adjustments are required depending on the service characteristics` |  |
| 2 | Keep-Alive limit | Keep-Alive timeout setting | Specify the session maintenance time between the client and server in seconds | `Default: 300 seconds` |  |
| 3 | Automatically block abnormal requests | Invalid request blocking settings | Block HTTP requests that contain invalid characters in the request header | `Default: Enabled` |  |
