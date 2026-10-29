## Security > Vaccine > コンソール使用ガイド > AhnLab(AhnLab CPP)

ここではVaccine Agentの有効化および無効化手の順と、サービス使用方法を説明します。

## セキュリティグループ(Security Groups) 設定

ワクチンサーバーと通信するには、セキュリティグループに以下の内容を追加します。

| 方向 | ポート | リージョン | CIDR |
| --- | --- | --- | ---- |
| Egress | 5465, 5645, 8803, 8804, 8807, 8809, 8810 | 韓国(パンギョ)、韓国(ピョンチョン) | 114.110.145.157/32 or {SG IP} |


## Vaccine サービスゲートウェイ連携
サービスゲートウェイを利用すると、NHN Cloud内部でクライアントとVaccineサーバーが通信する際、外部のインターネットを経由せず、内部ネットワークで通信できます。
Vaccineサービスゲートウェイを連携する方法は次のとおりです。

1. **Network > Service Gateway**で**+ サービスゲートウェイ作成**をクリックします。
2. 作成するサービスゲートウェイの名前、VPC、サブネットを入力し、サービスとして**Vaccine**を選択した後、**確認**をクリックすると、Vaccineサービスゲートウェイが作成されます。


## Vaccine Agent有効化手順

製品名、Instance OS, ネットワーク環境、Service Gateway IPアドレスに応じて、ワクチンインストールスクリプトを呼び出します。

![vaccine_console_01_jp.png](https://static.toastoven.net/prod_vaccine/vaccine_console_01_jp.png)

### Linux系Agent

1\. インストールスクリプトをコピーするには、**クリップボードにコピー**をクリックします。

2\. インストール対象のインスタンスのターミナルに接続します。

3\. 管理者権限でAgentスクリプトを作成し、実行します。

* viエディタなどでスクリプトを作成します。
* 作成したスクリプトファイルの権限を変更します。
* ファイルを実行します。
```
[rocky@vaccine-test ～]$ cd ～
[rocky@vaccine-test ～]$ vi agent.sh
[rocky@vaccine-test ～]$ chmod 744 agent.sh
[rocky@vaccine-test ～]$ ./agent.sh
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

[rocky@vaccine-test ～]$
```

### Windows系Agent

1\. コンソールのスクリプトをコピーします。

2\. インストール対象のインスタンスのターミナルに接続します。

3\. 管理者権限でAgentスクリプトを作成し、実行します。

* メモ帳などのテキストエディタでスクリプトファイルを作成します。
* 管理者権限でコマンドプロンプト(cmd)ウィンドウを有効化します。
* powershell -file "ファイルパス/ファイル名" の形式で実行します。
```
C:\Users\administrator>powershell -file C:\Users\administrator\Desktop\agent.ps1
PowerShell Major Version : 5.1
DownloadType : System.Net.Object.WebClient Download, DownloadUrl : https://114.110.145.157:5645/web/agent/3/test-win-setup.exeFile Install : C:\Users\ADMINI～1\AppData\Local\Temp\2\test-win-setup.exe /F "114.110.145.157" /A "P9tZYRpWDZBBTU3h" /U "da9b75db-269e-48ad-ba93-99949303c256"
File Install Complete!!

C:\Users\administrator>
```
### 使用開始

更新をクリックすると、状況一覧にインストールされたAgent情報が表示されます。
Agentのインストール後、自動的に有効化されます。

## Vaccine Agent無効化手順

![vaccine_console_ahnlabcpp_02_kr.png](https://static.toastoven.net/prod_vaccine/vaccine_console_ahnlabcpp_02_kr.png)

**使用終了**をクリックして、ワクチンの使用を中止します。

## Vaccineサービス使用方法

### マルウェア分析ガイド
* CPPはファイル復元ガイドを提供していません。マルウェアの分析が必要な場合、分析ファイルを収集した後、カスタマーサポートに分析を要請します。
    * Linux
        * マルウェア診断ログファイルの抽出
            * /usr/local/ahnlab/v3net/bin/v3cli と入力してCLIモードに移行
            * show scanlogs export と入力してマルウェア診断ログファイルをexport
            * quit と入力(CLIモード終了)
            * /usr/local/ahnlab/v3net/tmp/ パスに保存された virus.csv ファイルを送付
        * 分析ログの抽出
            * /usr/local/ahnlab/cppagent/bin/ahnrpt -s ahnreport.arc -agreePrivacyPolicy v コマンドを実行
            * コマンド実行パスに保存された ahnreport.arc ファイルを送付
    * Windows
        * マルウェア診断ログファイルの抽出
            * タスクバー右下のV3アイコンをダブルクリック
            * V3メイン画面で**ツール** > **ログ**の順にクリック
            * **診断ログ** > **ファイルとして保存**の順にクリック
            * 保存されたマルウェア診断ログファイル(csv)を送付
        * マルウェア分析ログの抽出
            * C:\Program Files (x86)\AhnLab\CPP Agent\1.0\bin\AhnRpt.exe を実行
            * 上部の**マルウェア申告**をクリック後、ユーザーの同意を進行
            * **詳細内容項目**にマルウェアに関する問い合わせ事項を記入して保存
            * ログ収集ファイルの保存パス及びファイル名を入力して保存
            * ログ収集完了後、保存パス内のファイル(arc圧縮ファイル)を送付

### エージェント状態チェックガイド
* Linux
    * systemctl status cppagent と入力
```
[root@vaccine-test ～]# systemctl status cppagent
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
    * コマンドプロンプト(cmd)ウィンドウを有効化
    * sc query CPPAgentSvc と入力
```
C:\Users\administrator>sc query CPPAgentSvc

SERVICE_NAME: CPPAgentSvc
        種類               : 10  WIN32_OWN_PROCESS
        状態               : 4  RUNNING
                                (NOT_STOPPABLE, NOT_PAUSABLE, ACCEPTS_SHUTDOWN)
        WIN32_EXIT_CODE    : 0  (0x0)
        SERVICE_EXIT_CODE  : 0  (0x0)
        検査点             : 0x0
        WAIT_HINT          : 0x0
```

### 分析ガイド
* エージェントがオフラインまたは無効状態の場合、次のファイルを収集し、カスタマーサポートに分析を要請します。
    * Linux
        * /usr/local/ahnlab/cppagent/bin/ahnrpt -s ahnreport.arc -agreePrivacyPolicy v コマンドを実行
        * コマンド実行パスに保存された ahnreport.arc ファイルを送付
    * Windows
        * C:\Program Files (x86)\AhnLab\CPP Agent\1.0\bin\AhnRpt.exe を実行
        * 上部の**製品エラー申告**をクリック後、ユーザーの同意を進行
        * **詳細内容項目**に問い合わせの症状に関する内容を記入して保存
        * ログ収集ファイルの保存パス及びファイル名を入力して保存
        * ログ収集完了後、保存パス内のファイル(arc圧縮ファイル)を送付

### 削除ガイド
* Linux
    * インスタンスに接続し、CPP Agentを削除します。
    * /usr/local/bin/uninstall-cppagent を実行
* Windows
    * インスタンスに接続し、CPP Agentを削除します。
    * **コントロールパネル > プログラムと機能**で**AhnLab Security Agent(CPP)**を選択して削除
 
## 運営の問い合わせ

### 問い合わせ対象

1\. 特定のファイル及びフォルダの例外処理
2\. Agentのインストール失敗に関する問い合わせ
3\. ワクチンのイベント検知に関する問い合わせ
4\. 正常なファイルの誤検知の申告及び復元に関する問い合わせ
5\. ワクチンによるインスタンスの誤動作の措置及び原因分析に関する問い合わせ

### 問い合わせ方法

1\. 問い合わせ方法：**カスタマーサポート > 問い合わせ**
2\. 対応時間：平日 09:00～18:00
