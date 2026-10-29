<!-- machine_translated: true -->

<!-- pre-align:aligned sig=470d545def88 -->

<a id="security-ddos-guard-console-user-guide"></a>
## Security > DDoS Guard > コンソール使用ガイド { #security-ddos-guard-console-user-guide }

ここでは、DDoS Guardコンソール使い方を説明します。

DDoS Guardサービスを使用するには、**NHN Cloudコンソール**にログインし、サービス選択で**Security > DDoS Guard**をクリックして有効にします。


<a id="how-to-apply-and-release-managed"></a>
## Managedの申請および解除方法 { #how-to-apply-and-release-managed }
<a id="apply"></a>
### 申請 { #apply }
1. DDoS Guardコンソールでサービス申請現況タブをクリックし、Managedタブで**Zone申請**ボタンをクリックします。
2. Zone情報と保護対象(IP、ドメイン)を入力し、対応モードを選択します。
3. 伝播担当者を入力し、個人情報の収集及び利用に同意した後、**保存**ボタンをクリックします。
4. 申請が完了すると、運営担当者が内容を確認して処理します。Managedサービスが開始されると、現況が**運営中**に変更されます。

<a id="release"></a>
### 解除 { #release }
1. Managed申請現況リストの中から解除を希望する対象を選択し、**解除**ボタンをクリックします。
2. Zone解除約款内容に同意した後、**確認**ボタンをクリックします。
3. 解除がリクエストされると、運営担当者が内容を確認して処理します。

<a id="managed-report-settings"></a>
## Managedレポート設定 { #managed-report-settings }
<a id="managed-report-settings-apply"></a>
### 申請 { #managed-report-settings-apply }
1. Managedタブで**レポート設定**ボタンをクリックします。
2. **利用及びメール受信申請**ボタンをクリックして**申請**に変更します。
3. レポートタイプを選択し、**確認**ボタンをクリックします。

<a id="managed-report-settings-release"></a>
### 解除 { #managed-report-settings-release }
1. Managedタブで**レポート設定**ボタンをクリックします。
2. **利用及びメール受信申請**ボタンをクリックして**申請しない**に変更します。
3. **確認**ボタンをクリックします。


<a id="apply-and-release-simulation-training-support"></a>
## 模擬訓練サポート申請及び解除 { #apply-and-release-simulation-training-support }
<a id="apply-and-release-simulation-training-support-apply"></a>
### 申請 { #apply-and-release-simulation-training-support-apply }
1. DDoS Guardコンソールでサービス申請現況タブをクリックし、模擬訓練サポートタブで**申請**ボタンをクリックします。
2. 模擬訓練サポート利用規約を確認し、同意した後、**確認**ボタンをクリックします。
3. 基本情報、訓練情報、攻撃者IP帯域、訓練対象、実行担当者情報、訓練シナリオ情報を入力します。
4. 負荷テストはオプションで、必要に応じて情報を入力し、**保存**ボタンをクリックします。
5. 申請が完了すると、運営担当者が内容を確認して処理します。

<a id="delete"></a>
### 削除 { #delete }
1. 模擬訓練サポート申請現況リストのうち、削除を希望する対象を選択し、**削除**ボタンをクリックします。
2. 模擬訓練サポート削除約款内容に同意した後、 **確認**ボタンをクリックします。

<a id="check-traffic-status"></a>
## トラフィック現況確認 { #check-traffic-status }
- トラフィック現況タブで、DDoS装置を通じて保護対象に流入する全てのトラフィックと遮断トラフィックの統計情報を確認できます。
  - トラフィック統計: DDoS装置に流入するトラフィックの統計情報を表示します。
  - 遮断トラフィック統計: DDoS装置で遮断されるトラフィックの統計情報を表示します。
  - トラフィックログは、最近1か月のデータを保管します。

![%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_ddosguard/%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png)

![%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%8E%E1%85%A1%E1%84%83%E1%85%A1%E1%86%AB%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_ddosguard/%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%8E%E1%85%A1%E1%84%83%E1%85%A1%E1%86%AB%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png)

<a id="check-event-status"></a>
## イベント現況確認 { #check-event-status }
- イベント現況タブでイベント統計情報と詳細イベント現況を確認できます。
- イベントログは最近1年間のデータを保存し、最大1か月単位で照会できます。

![%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_ddosguard/%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png)

![%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%8C%E1%85%A9%E1%84%92%E1%85%AC.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_ddosguard/%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%8C%E1%85%A9%E1%84%92%E1%85%AC.png)
