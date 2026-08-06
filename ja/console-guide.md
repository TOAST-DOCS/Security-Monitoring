<!-- pre-align:aligned sig=371929834704 -->

<a id="security-security-monitoring-console-guide"></a>
## Security > Security Monitoring > コンソール使用ガイド { #security-security-monitoring-console-guide }

ここではSecurity Monitoringコンソールの使用方法を説明します。

Security Monitoringサービスを使用するには、**NHN Cloud Console**にログインし、サービスリストから**Security > Security Monitoring**をクリックします。

<a id="service-application-and-release"></a>
## セキュリティー監視サービスの申請および解除 { #service-application-and-release }
<a id="add-security-monitoring-targets"></a>
### セキュリティー監視対象を追加 { #add-security-monitoring-targets }
1. Security Monitoringコンソールで**申請状況**タブをクリックし、**セキュリティー監視サービス未利用状況**から監視サービスを利用するインスタンスを選択します。
2. 選択されたリストを確認した後、**監視対象追加**ボタンをクリックし、監視サービスを申請します。
3. 申請後、<span style="color:#ab4642">**最長1時間以内に**</span>該当インスタンスに対する監視サービスが始まります。監視サービスが始まると、**セキュリティー監視サービス利用状況**の下にある**監視状況**列の'受付待機'状態が'進行中'に変更されます。

<a id="release-from-security-monitoring"></a>
### セキュリティー監視対象の解除 { #release-from-security-monitoring }
1. **セキュリティー監視サービス利用状況**リストから、セキュリティー監視を解除するインスタンスを選択し、**監視対象解除**ボタンをクリックします。
解除要請後、<span style="color:#ab4642">**最長1時間以内**</span>に該当インスタンスに対する監視が解除されます。

<a id="receiving-information-for-security-monitoring-events"></a>
## セキュリティー監視業務の受信設定 { #receiving-information-for-security-monitoring-events }
セキュリティー監視サービス中に発生するイベントに対して受信設定ができます。

![securitymonitoring_console_guide_jp_210625.png](http://static.toastoven.net/prod_mss/securitymonitoring_console_guide_jp_220719.png)

<a id="enable-phone-communication-for-urgency"></a>
### 緊急電話連絡の許可 { #enable-phone-communication-for-urgency }

緊急を要するセキュリティーイベントが発生した場合、電話で連絡を受けることができます。利用するには申請が必要です。

**緊急電話連絡の許可**で、**はい**をクリックします。

- 申請者と電話連絡受信者が同じ場合
  - **申請者と電話連絡受信者が同じかどうか**で**はい**をクリックすると、登録されている電話連絡先情報で申請されます。
- 申請者と電話連絡受信者が異なる場合
 1. **申請者と電話連絡受信者が同じかどうか**で**いいえ**をクリックします。
 2. **受信担当者**と**連絡先**に情報を入力します。

**上記の個人情報収集および利用に同意します**を選択します。

<a id="apply-for-mail-notification-on-progress"></a>
### 業務処理内容メール受信申請 { #apply-for-mail-notification-on-progress }

セキュリティー監視対応および処理内容をメールで受け取ることができます。メールアドレスは、セミコロン(;)で区切って複数入力できます。

3. **業務処理内容メール受信申請**で**はい**をクリックします。
4. **メールアドレス**に情報を入力し、**上記個人情報収集および利用に同意します**を選択します。

<a id="check-security-monitoring-status"></a>
## セキュリティー監視状況確認 { #check-security-monitoring-status }
- **監視状況**</span>タブでセキュリティ監視サービスを申請したインスタンスのセキュリティ監視対応状況を確認できます。 
  - セキュリティ監視対応リストは過去1年のデータのみ検索できます。

![securitymonitoring_console_guide_jp_210629_1.png](http://static.toastoven.net/prod_mss/securitymonitoring_console_guide_jp_220719_1.png)

<a id="check-detailed-event-status"></a>
## 詳細イベント状況確認 { #check-detailed-event-status }
- **詳細イベント状況** </span> タブでセキュリティ監視サービスを申請したインスタンスの詳細イベント状況を確認できます。 
  - 詳細イベントリストは過去3ヶ月のデータのみ検索できます。

![securitymonitoring_console_guide_jp_210625_2.png](http://static.toastoven.net/prod_mss/securitymonitoring_console_guide_jp_220719_2.png)
