## Security > Vaccine > コンソール使用ガイド > Trend Micro(Deep Security)

ここではVaccine Agentの有効化および無効化手の順と、サービス使用方法を説明します。

## セキュリティグループ(Security Group)設定

ワクチンサーバーと通信するには、セキュリティグループに以下の内容を追加します。

| 方向 | ポート | リージョン | CIDR |
| --- | --- | --- | ---- |
| Egress | 4119, 4120, 4122 | 韓国(パンギョ)、韓国(ピョンチョン) | 114.110.144.39/32 |

## Vaccine Agentの有効化手順

製品名、Instance OS, ネットワーク環境、Service Gateway IPアドレスに応じて、ワクチンインストールスクリプトを呼び出します。

![vaccine_console_01_jp.png](https://static.toastoven.net/prod_vaccine/vaccine_console_01_jp.png)

### Linux系列のAgent

1\. インストールスクリプトをコピーするには、**クリップボードにコピー**をクリックします。

2\. インストール対象のインスタンスターミナルに接続します。

3\. 管理者権限でAgentスクリプトを作成し、実行します。

* viエディタなどでスクリプトを作成します。
* 作成したスクリプトファイルの権限を変更します。
* ファイルを実行します。
```
[root@vaccine-test ~]# cd ~
[root@vaccine-test ~]# vi agent.sh
[root@vaccine-test ~]# chmod 744 agent.sh
[root@vaccine-test ~]# ./agent.sh
/tmp/DownloadInstallAgentPackage: OK
Downloading agent package ...
curl https://114.110.144.39:4119/software/agent/RedHat_EL7/x86_64/ -o /tmp/agent.rpm --insecure --silent
Installing agent package ...
Preparing...                          ################################# [100%]
Updating / installing...
   1:ds_agent-10.0.0-2775.el7         ################################# [100%]
Starting ds_agent (via systemctl):  [  OK  ]
HTTP Status: 200 - OK
Activation will be re-attempted 30 time(s) in case of failure
dsa_control
HTTP Status: 200 - OK
Response:
Attempting to connect to https://114.110.144.39:4120/
SSL handshake completed successfully - initiating command session.
Connected with (NONE) to peer at 114.110.144.39
Received a 'GetHostInfo' command from the manager.
Received a 'GetHostInfo' command from the manager.
Received a 'SetDSMCert' command from the manager.
Received a 'SetAgentCredentials' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetInterfaces' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetAgentStatus' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetHostMetaData' command from the manager.
Received a 'SetSecurityConfiguration' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetAgentStatus' command from the manager.
Command session completed.
[root@vaccine-test ~]#
```

### Windows系列のAgent

1\. コンソールスクリプトをコピーします。

2\. インストール対象のインスタンスターミナルに接続します。

3\. 管理者権限でAgentスクリプトを作成し、実行します。

* メモ帳などのテキストエディタでスクリプトファイルを作成します。
* 管理者権限で**コマンドプロンプト**(cmd)ウィンドウを有効にします。
* powershell -file "ファイルパス/ファイル名"の形式で実行します。
```
Microsoft Windows [Version 6.3.9600]
(c) 2013 Microsoft Corporation. All rights reserved.

C:\Users\Administrator>powershell -file "agent.ps1"


  ディレクトリ： C:\Users\Administrator\AppData\Roaming\Trend Micro\Deep Security Agent


Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----      2018-06-05 午後2：37            installer
記録が始まりました。出力ファイルはC:\Users\Administrator\AppData\Roaming\Trend Micro\Deep Security Agent\installer\dsa_deploy.logです。
午後2：37：23 - DSA download started
午後2：37：23 - Download Deep Security Agent Package
https://114.110.144.39:4119/software/agent/Windows/x86_64/
午後2：37：24 - Downloaded File Size：
13897728
午後2：37：24 - DSA install started
午後2：37：24 - Installer Exit Code：
0
午後2：37：32 - DSA activation started
HTTP Status: 200 - OK
Activation will be re-attempted 30 time(s) in case of failure
dsa_control
HTTP Status: 200 - OK
Response:
Attempting to connect to https://114.110.144.39:4120/
SSL handshake completed successfully - initiating command session.
Connected with AES256-SHA256 to peer at 114.110.144.39
Received a 'GetHostInfo' command from the manager.
Received a 'GetHostInfo' command from the manager.
Received a 'SetDSMCert' command from the manager.
Received a 'SetAgentCredentials' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetInterfaces' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetAgentStatus' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetHostMetaData' command from the manager.
Received a 'SetSecurityConfiguration' command from the manager.
Received a 'GetAgentEvents' command from the manager.
Received a 'GetAgentStatus' command from the manager.
Command session completed.
記録が中止されました。出力ファイルはC:\Users\Administrator\AppData\Roaming\Trend Micro\Deep Security Agent\installer\dsa_deploy.logです。
午後2：38：29 - DSA Deployment Finished

C:\Users\Administrator>
```
### 使用開始

![vaccine_console_deepsecurity_02_jp.png](https://static.toastoven.net/prod_vaccine/vaccine_console_deepsecurity_02_jp.png)

更新をクリックすると、状況リストにインストールされたAgent情報が表示されます。
**使用開始**ボタンをクリックすると、サービスの使用を開始します。

## Vaccine Agentの無効化手順

![vaccine_console_deepsecurity_03_jp.png](https://static.toastoven.net/prod_vaccine/vaccine_console_deepsecurity_03_jp.png)

1\. Webコンソール使用中止

* **使用終了**ボタンをクリックして、ワクチンの使用を中止します。
### Linux系列のAgent
* インスタンスに接続し、Vaccine Agentを削除します。
    * CentOS：rpm -e ds_agentの実行
    * Debian/Ubuntu： apt-get remove ds-agent実行

### Windows系列のAgent
* インスタンスに接続し、Vaccine Agentを削除します。
    *プログラムおよび機能メニューで**Trend Micro Deep Security Agent**を削除します。

## Vaccineサービスの使用方法

### ファイル復元ガイド
1\. ファイル復元

* 復元ツールを[ダウンロード](http://static.toastoven.net/prod_vaccine/QFAdminUtil_win32.zip)します。
* ダウンロードしたQFAdminUtil_win32.zipファイルをWindows OS環境で解凍します。
* QDecrypt.exeを実行し、隔離されたファイルを開いてファイルを復元します。

2\. 隔離ファイルの位置

* Linux ： /var/opt/ds_agent/guest/0000-0000-0000/quarantined
* Windows ： C:\ProgramData\Trend Micro\AMSP\quarantine
    *隔離ファイルが見えない場合は、**コンピュータ**または**ファイルエクスプローラ**のメニューで**フォルダーオプション**をクリックして<br>
    **表示**タブで**保護されたオペレーションシステムファイルを表示しない**の選択を解除して**隠しファイル、隠しフォルダー、および隠しドライブを表示する**を選択します。

### エージェント状態チェックガイド
* Linux
    * sudo /opt/ds_agent/dsa_query -c GetAgentStatus | grep AgentStatus.agentState

```
[root@vaccine-test ~]# cd /opt/ds_agent/
[root@vaccine-test ds_agent]# ./dsa_query -c GetAgentStatus | grep AgentStatus.agentState
AgentStatus.agentState: green
[root@vaccine-test ds_agent]#
```

* Windows
    * WindowsトレイでAgentを右クリックしてコンソールを開く > 「実行中(Running)」確認  
    * ![windows_agent_status.png](https://static.toastoven.net/prod_vaccine/windows_agent_status.png)

### 分析ガイド
* ***エージェントがオフラインまたは非アクティブ状態の場合、次のファイルを収集してサポートに分析をリクエストします。**
    * Linux
        * /opt/ds_agent/dsa_control -d実行
        * /var/opt/ds_agent/diag/ランダム10桁数字.zipファイル分析要請
        * カーネル情報確認: sudo uname -a, OS情報確認: sudo cat /etc/\*release結果の伝達
    * Windows
        * C:\Program Files\Trend Micro\Deep Security Agent\dsa_control -d実行
        * C:\Program Data\Trend Micro\Deep Security Agent\diag\ランダム10桁数字.zipファイル分析リクエスト
    * 詳細な分析のために、問題発生状況でデバッグ実行後に作成されたファイルを追加で要請できます。

### 削除ガイド
* Linux系列Agent
    * インスタンスに接続してVaccine Agentを削除します。
       * CentOS: rpm -e ds_agent実行
       * Debian/Ubuntu: apt-get remove ds-agent実行
* Windows系列Agent
    * インスタンスに接続してVaccine Agentを削除します。
       * プログラム及び機能メニューで**Trend Micro Deep Security Agent**を削除します。

### イメージ複製時の使用ガイド

Vaccine Agentが含まれているPrivate Image基盤インスタンス作成時のワクチン使用ガイドです。

* インスタンスに接続して、それぞれ該当するスクリプトを作成および実行してインストールします。
* Vaccine Agent有効化ガイドに従って、サービス画面で更新および**使用開始**ボタンをクリックすると使用できます。

※注意事項

* スクリプト内容中、"group：アプリケーションキー"のアプリケーションキーは、サービス画面の**URL & Appkey**メニュー内のAppkey値に変更する必要があります。
* 使用を望まない複製インスタンスは、不要なリソースを浪費しないように、インストールされたAgentの削除を推奨します。
* '使用開始'後、サービス使用状態はすぐに'商品終了'状態が有効になりますが、ワクチンは最初のインストール同様に最長で約10分後から正常に動作します。

1\. Linux系列のAgentスクリプト

```
touch /etc/use_dsa_with_iptables

IP=`ifconfig eth0 | grep -w -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}' | head -1`
uuidInfo=`curl -s 169.254.169.254/openstack/latest/meta_data.json | python -c 'import json,sys;obj=json.load(sys.stdin);print (str(obj["uuid"])+":"+str("user_metadata.server_group" in obj["meta"]))'`
/opt/ds_agent/dsa_control -r
/opt/ds_agent/dsa_control -a dsm://114.110.144.39:4120/ "group:앱키" "displayname:$IP" "description:$uuidInfo"
```

2\. Windows系列のAgentスクリプト

```
$idx=(Get-WmiObject -Class Win32_IP4RouteTable | where { $_.destination -eq '0.0.0.0' -and $_.mask -eq '0.0.0.0'} | Sort-Object metric1).interfaceindex[0]

$IP=((Get-WmiObject win32_networkadapterconfiguration | where { $_.interfaceindex -eq $idx} | select ipaddress)| findstr .*[0-9].\.).Split(",")[0].Split("{")[-1].Split("}")[0]
$uuid=((invoke-webrequest -uri 169.254.169.254/openstack/latest/meta_data.json -UseBasicParsing).content | convertfrom-json).uuid
$as="user_metadata.server_group" -in ((invoke-webrequest -uri 169.254.169.254/openstack/latest/meta_data.json -UseBasicParsing).content | convertfrom-json).meta.psobject.properties.name
$uuidInfo=$uuid+":"+$as`

& $Env:ProgramFiles"\Trend Micro\Deep Security Agent\dsa_control" -r
& $Env:ProgramFiles"\Trend Micro\Deep Security Agent\dsa_control" -a dsm://114.110.144.39:4120/ "group:앱키" "displayname:$IP" "description:$uuidInfo"
```
※パッチファイル(.bat)で作成し、スクリプトを実行する必要があります。

### Auto Scale使用ガイド
Auto Scaleを利用したワクチン機能の使用案内は、サポートへお問い合わせください。詳細を説明いたします。

## 運営お問い合わせ

### お問い合わせ対象

1\. 特定ファイルおよびフォルダ例外処理
2\. Agentインストール失敗のお問い合わせ
3\. ワクチンイベント探知関連のお問い合わせ
4\. 正常ファイル誤診申告および復元関連のお問い合わせ
5\. ワクチンによるインスタンス誤作動の対処および原因分析関連のお問い合わせ

### 問い合わせ方法

1\. 問い合わせ方法：**カスタマーサポート > 問い合わせ**
2\. 対応時間：平日 09:00～18:00
