<!-- machine_translated: true -->

<!-- pre-align:aligned sig=470d545def88 -->

<a id="security-ddos-guard-console-user-guide"></a>
## Security > DDoS Guard > Console User Guide { #security-ddos-guard-console-user-guide }

It describes how to use the DDoS Guard console.

To use the DDoS Guard service, log in to the NHN Cloud console and activate it by clicking Security > DDoS Guard in the Select Service.

<a id="how-to-apply-and-release-managed"></a>
## How to Apply and Release Managed { #how-to-apply-and-release-managed }

<a id="apply"></a>
### Apply { #apply }

1. In the DDoS Guard console, click the Service Application Status tab and then click the Apply for Zone button in the Managed tab.
2. Enter the zone information and protection target (IP, domain), and select the response mode.
3. Enter the propagation manager, agree to the collection and use of personal information, and click the Save button.
4. Once your application is complete, the operations manager will review and process the information. Once the Managed service begins, the status will change to "Operating."

<a id="release"></a>
### Release { #release }

1. Select the target you wish to release from the list of Managed applications and click the **Release** button.
2. Agree to the Zone release terms and conditions and click the **Confirm** button.
3. Once the release is requested, the operations manager will review and process the information.

<a id="managed-report-settings"></a>
## Managed Report Settings { #managed-report-settings }

<a id="managed-report-settings-apply"></a>
### Apply { #managed-report-settings-apply }

1. Click the Report Settings button on the Managed tab.
2. Click the **Apply for Use and Email Reception** button to change it to **Apply**.
3. Select the report type and click the Confirm button.

<a id="managed-report-settings-release"></a>
### Release { #managed-report-settings-release }

1. Click the Report Settings button on the Managed tab.
2. Click the **Apply for Use and Email Reception** button to change it to **Not Apply**.
3. Click the Confirm button.

<a id="apply-and-release-simulation-training-support"></a>
## Apply and Release Simulation Training Support { #apply-and-release-simulation-training-support }

<a id="apply-and-release-simulation-training-support-apply"></a>
### Apply { #apply-and-release-simulation-training-support-apply }

1. In the DDoS Guard console, click the Service Application Status tab and then click the Apply button in the Simulation Training Support tab.
2. Agree to the simulation training support terms and conditions and click the **Confirm** button.
3. Enter the basic information, training information, attacker IP range, training target, executor and training scenario information.
4. Load testing is optional. Enter information and click the Save button, if needed.
5. Once your application is complete, the operations manager will review and process the information.

<a id="delete"></a>
### Delete { #delete }

1. Select the target you wish to delete from the list of simulation training support applications and click the **Delete** button.
2. Agree to the simulation training support deletion terms and conditions and click the **Confirm** button.

<a id="check-traffic-status"></a>
## Check Traffic Status { #check-traffic-status }

- From the traffic status tab, you can view the statistics information about all traffic flowing into the protected target through DDoS devices and blocked traffic.
  - Traffic statistics: display statistics on traffic flowing into DDoS devices.
  - Blocked traffic statistics: display statistics on traffic blocked by DDoS devices.
  - Traffic logs store data for the past month.

![%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_ddosguard/%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png)

![%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%8E%E1%85%A1%E1%84%83%E1%85%A1%E1%86%AB%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_ddosguard/%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%8E%E1%85%A1%E1%84%83%E1%85%A1%E1%86%AB%E1%84%90%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B5%E1%86%A8%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png)

<a id="check-event-status"></a>
## Check Event Status { #check-event-status }

- You can view the event statistics information and detailed event status from the event status tab.
- Event log data for the past year is stored and can be viewed in units of up to one month.

![%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_ddosguard/%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%90%E1%85%A9%E1%86%BC%E1%84%80%E1%85%A8.png)

![%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%8C%E1%85%A9%E1%84%92%E1%85%AC.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_ddosguard/%E1%84%8B%E1%85%B5%E1%84%87%E1%85%A6%E1%86%AB%E1%84%90%E1%85%B3%E1%84%92%E1%85%A7%E1%86%AB%E1%84%92%E1%85%AA%E1%86%BC_%E1%84%8C%E1%85%A9%E1%84%92%E1%85%AC.png)
