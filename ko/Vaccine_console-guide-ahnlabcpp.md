<!-- pre-align:aligned sig=f05aff1b6142 -->

<a id="security-vaccine-console-user-guide-ahnlabahnlab-cpp"></a>
## Security > Vaccine > 콘솔 사용 가이드 > AhnLab(AhnLab CPP) { #security-vaccine-console-user-guide-ahnlabahnlab-cpp }

여기에서는 Vaccine Agent 활성화 및 비활성화 절차와 서비스 사용법을 설명합니다.

<a id="set-up-security-groups"></a>
## 보안 그룹(Security Groups) 설정 { #set-up-security-groups }

백신 서버와 통신하려면 보안 그룹에 아래 내용을 추가합니다.

| 방향 | 포트 | 리전 | CIDR |
| --- | --- | --- | ---- |
| Egress | 5465, 5645, 8803, 8804, 8807, 8809, 8810 | 한국(판교), 한국(평촌) | 114.110.144.193/32 or {SG IP}|


<a id="integrate-vaccine-service-gateway"></a>
## Vaccine 서비스 게이트웨이 연동 { #integrate-vaccine-service-gateway }
서비스 게이트웨이를 이용하면 NHN Cloud 내부에서 클라이언트와 Vaccine 서버가 통신할 때 외부 인터넷을 경유하지 않고, 내부 네트워크로 통신할 수 있습니다.
Vaccine 서비스 게이트웨이를 연동하는 방법은 아래와 같습니다.

1. **Network > Service Gateway**에서 **+ 서비스 게이트웨이 생성**을 클릭합니다.
2. 생성할 서비스 게이트웨이의 이름, VPC, 서브넷을 입력하고 서비스를 **Vaccine**으로 선택한 뒤 **확인**을 클릭하면 Vaccine 서비스 게이트웨이가 생성됩니다.


<a id="vaccine-agent-activation-process"></a>
## Vaccine Agent 활성화 절차 { #vaccine-agent-activation-process }

제품명, Instance OS, Network 환경, Service Gateway IP 주소에 따라 백신 설치 스크립트를 불러옵니다.

![vaccine_console_01_kr.png](https://static.toastoven.net/prod_vaccine/vaccine_console_01_kr.png)

<a id="linux-based-agent"></a>
### Linux 계열 Agent { #linux-based-agent }

1\. 설치 스크립트를 복사하려면 **클립보드로 복사**를 클릭합니다.

2\. 설치 대상 인스턴스 터미널에 접속합니다.

3\. 관리자 권한으로 Agent 스크립트를 생성하고 실행합니다.

* vi 편집기 등으로 스크립트를 생성합니다.
* 생성한 스크립트 파일의 권한을 변경합니다.
* 파일을 실행합니다.
```
[rocky@vaccine-test ~]$ cd ~
[rocky@vaccine-test ~]$ vi agent.sh
[rocky@vaccine-test ~]$ chmod 744 agent.sh
[rocky@vaccine-test ~]$ ./agent.sh
####### DownloadUrl :https://114.110.145.157:5645/web/agent/4/test-lin-setup.tar.gz #######
####### filePath : /root/test-lin-setup.tar.gz #######
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 34.0M  100 34.0M    0     0  2041k      0  0:00:17  0:00:17 --:--:-- 2037k
File Download Complete
ahnagent-install.sh
ahnagent-install.sh.ahc
eal.tar
ahnagent-install.conf
Valid IP 114.110.145.157

Start the installation for ahnagent

Succeed to extract "eal.tar" archive
Check Linux ID and version ...
-> OS ID and version : ROCKY_9
   OS Description : Rocky Linux 9.5 (Blue Onyx)
"ROCKY_9" is supported
[INFO] get to install path: /usr/local/ahnlab/cppagent
The installed agent will be removed when installing a new agent

    "Before uninstall ahnagent, Start the uninstallation for mgmt products"

[INFO] get to install path: /usr/local/ahnlab/cppagent
skip uninstallation of mgmt products

    "Start to uninstall agent from SystemD"


    "Complete to uninstall agent from SystemD"


    "Complete the uninstallation for ahnagent package"

[INFO] get to install path: /usr/local/ahnlab/cppagent
Install ahnagent package ...
Succeed to install ahnagent package to /usr/local/ahnlab/cppagent
force server ip: 114.110.145.157
appkey: P9tZYRpWDZBBTU3h
user name: 9b273bb9-edb4-42f1-b11b-4d1befcde97b
Created symlink /etc/systemd/system/multi-user.target.wants/cppagent.service → /usr/lib/systemd/system/cppagent.service.
Succeed to enable ahnagent
Succeed to start ahnagent

    "Complete the installation for ahnagent package"

[rocky@vaccine-test ~]$
```

<a id="windows-based-agent"></a>
### Windows 계열 Agent { #windows-based-agent }

1\. 콘솔 스크립트를 복사합니다.

2\. 설치 대상 인스턴스 터미널에 접속합니다.

3\. 관리자 권한으로 Agent 스크립트를 생성하고 실행합니다.

* 메모장과 같은 텍스트 에디터로 스크립트 파일을 생성합니다.
* 관리자 권한으로 명령 프롬프트(cmd) 창을 활성화합니다.
* powershell -file "파일 경로/파일명" 형태로 실행합니다.
```
C:\Users\administrator>powershell -file C:\Users\administrator\Desktop\agent.ps1
PowerShell Major Version : 5.1
DownloadType : System.Net.Object.WebClient Download, DownloadUrl : https://114.110.145.157:5645/web/agent/3/test-win-setup.exeFile Install : C:\Users\ADMINI~1\AppData\Local\Temp\2\test-win-setup.exe /F "114.110.145.157" /A "P9tZYRpWDZBBTU3h" /U "da9b75db-269e-48ad-ba93-99949303c256"
File Install Complete!!

C:\Users\administrator>
```
<a id="getting-started"></a>
### 사용 시작 { #getting-started }

새로고침을 클릭하면 현황 목록에 설치된 Agent 정보가 표시됩니다.
Agent 설치 후 자동으로 활성화됩니다.

<a id="vaccine-agent-deactivation-process"></a>
## Vaccine Agent 비활성화 절차 { #vaccine-agent-deactivation-process }

![vaccine_console_ahnlabcpp_02_kr.png](https://static.toastoven.net/prod_vaccine/vaccine_console_ahnlabcpp_02_kr.png)

**사용 종료**를 클릭하여 백신 사용을 중지합니다.

<a id="how-to-use-vaccine-service"></a>
## Vaccine 서비스 사용법 { #how-to-use-vaccine-service }

<a id="malware-analysis-guide"></a>
### 악성코드 분석 가이드 { #malware-analysis-guide }
* CPP는 파일 복원 가이드를 제공하지 않습니다. 악성코드 분석이 필요할 경우 분석 파일 수집 후 고객지원으로 분석을 요청합니다.
    * Linux
        * 악성코드 진단 로그 파일 추출
            * /usr/local/ahnlab/v3net/bin/v3cli 입력하여 CLI 모드 진입
            * show scanlogs export 입력하여 악성코드 진단 로그 파일 export
            * quit 입력(CLI 모드 종료)
            * /usr/local/ahnlab/v3net/tmp/ 경로에 저장된 virus.csv 파일 전달
        * 분석 로그 추출
            * /usr/local/ahnlab/cppagent/bin/ahnrpt -s ahnreport.arc -agreePrivacyPolicy v 명령어 실행
            * 명령어 실행 경로에 저장된 ahnreport.arc 파일 전달
    * Windows
        * 악성코드 진단 로그 파일 추출
            * 작업 표시줄 우측 하단에 V3 아이콘 더블 클릭
            * V3 메인 화면에서 **도구** > **로그**순으로 클릭
            * **진단 로그** > **파일로 저장**순으로 클릭
            * 저장된 악성코드 진단 로그 파일(csv) 전달
        * 악성코드 분석 로그 추출
            * C:\Program Files (x86)\AhnLab\CPP Agent\1.0\bin\AhnRpt.exe 실행
            * 상단 **악성코드 신고** 클릭 후 사용자 동의 진행
            * **상세 내용 항목**에 악성코드 관련 문의 사항 기입 후 저장
            * 로그 수집 파일의 저장 경로 및 파일명 입력 후 저장
            * 로그 수집 완료 후 저장 경로 내 파일(arc 압축 파일) 전달

<a id="agent-health-check-guide"></a>
### 에이전트 상태 체크 가이드 { #agent-health-check-guide }
* Linux
    * systemctl status cppagent 입력
```
[root@vaccine-test ~]# systemctl status cppagent
● cppagent.service - "AhnLab Security Agent Linux Service"
   Loaded: loaded (/usr/lib/systemd/system/cppagent.service; enabled; vendor preset: di>
   Active: active (running) since Thu 2026-02-05 14:53:03 KST; 17min ago
 Main PID: 19486 (ahnagent)
    Tasks: 9 (limit: 48701)
   Memory: 6.2M
   CGroup: /system.slice/cppagent.service
           └─19486 /usr/local/ahnlab/cppagent/bin/ahnagent
```
* Windows
    * 명령 프롬프트(cmd) 창 활성화
    * sc query CPPAgentSvc 입력
```
C:\Users\administrator>sc query CPPAgentSvc

SERVICE_NAME: CPPAgentSvc
        종류               : 10  WIN32_OWN_PROCESS
        상태               : 4  RUNNING
                                (NOT_STOPPABLE, NOT_PAUSABLE, ACCEPTS_SHUTDOWN)
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        검사점             : 0x0
        WAIT_HINT          : 0x0
```

<a id="analysis-guide"></a>
### 분석 가이드 { #analysis-guide }
* 에이전트 오프라인 또는 비활성 상태 시 다음 파일을 수집하여 고객지원으로 분석을 요청합니다.
    * Linux
        * /usr/local/ahnlab/cppagent/bin/ahnrpt -s ahnreport.arc -agreePrivacyPolicy v 명령어 실행
        * 명령어 실행 경로에 저장된 ahnreport.arc 파일 전달
    * Windows
        * C:\Program Files (x86)\AhnLab\CPP Agent\1.0\bin\AhnRpt.exe 실행
        * 상단 **제품 오류 신고** 클릭 후 사용자 동의 진행
        * **상세 내용 항목**에 문의 증상에 대한 내용 기입 후 저장
        * 로그 수집 파일의 저장 경로 및 파일명 입력 후 저장
        * 로그 수집 완료 후 저장 경로 내 파일(arc 압축 파일) 전달

<a id="uninstall-guide"></a>
### 삭제 가이드 { #uninstall-guide }
* Linux
    * 인스턴스에 접속하여 CPP Agent를 삭제합니다.
    * /usr/local/bin/uninstall-cppagent 실행
* Windows
    * 인스턴스에 접속하여 CPP Agent를 삭제합니다.
    * **제어판 > 프로그램 및 기능**에서 **AhnLab Security Agent(CPP)** 선택하여 제거
 
<a id="operation-inquiry"></a>
## 운영 문의 { #operation-inquiry }

<a id="inquiry-item"></a>
### 문의 대상 { #inquiry-item }

1\. 특정 파일 및 폴더 예외 처리
2\. Agent 설치 실패 문의
3\. 백신 이벤트 탐지 관련 문의
4\. 정상 파일 오진 신고 및 복원 관련 문의
5\. 백신으로 인한 인스턴스 오동작 조치 및 원인 분석 관련 문의

<a id="how-to-inquire"></a>
### 문의 방법 { #how-to-inquire }

1\. 문의 방법: **고객지원 > 문의하기**
2\. 대응 시간: 평일 09:00~18:00
