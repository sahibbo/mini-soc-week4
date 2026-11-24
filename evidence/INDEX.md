# Evidence index — Week 4

Open a figure to view the full-size screenshot. Lettered entries are panels of the same numbered figure.

| Figure | Screenshot | What it shows |
|---|---|---|
| 1 | [Shuffle services on the SIEM host](week4/fig-01-shuffle-services.png) | Docker Compose reports the frontend, backend, security service, Orborus and OpenSearch running. |
| 2 | [Initial Shuffle workflow](week4/fig-02-shuffle-workflow-setup.png) | The Shuffle interface shows the setup form for the lab workflow. |
| 3a | [DFIR IRIS sign-in](week4/fig-03a-iris-sign-in.png) | The sign-in page identifies the analyst platform used in the lab. |
| 3b | [DFIR IRIS dashboard](week4/fig-03b-iris-dashboard.png) | The authenticated dashboard shows that IRIS is accessible after sign-in. |
| 4a | [IRIS users and integration identity](week4/fig-04a-iris-identities.png) | The user list distinguishes the L1 and L2 analysts and the Shuffle service account. |
| 4b | [IRIS groups and permissions](week4/fig-04b-iris-groups.png) | The permissions list shows separate SOC-L1, SOC-L2 and SOAR-Integration roles. |
| 5 | [Synthetic alert in the L1 queue](week4/fig-05-synthetic-alert.png) | SOC L1 can see the API connectivity test alert that will be handed to L2. |
| 6 | [L2 case linked to the synthetic alert](week4/fig-06-l2-case-handoff.png) | The L2-owned case records the handoff and links back to the original alert. |
| 7 | [Wazuh integration configuration](week4/fig-07-wazuh-shuffle-integration.png) | The manager sends JSON alerts at level 10 and above to the authenticated Shuffle integration. The webhook address is redacted. |
| 8 | [Wazuh event in a Shuffle execution](week4/fig-08-shuffle-webhook-run.png) | A completed webhook execution contains Wazuh rule 5763 at level 10. |
| 9 | [IRIS Add Alert result](week4/fig-09-iris-action-fields.png) | The IRIS action output carries rule 5763, the Wazuh source and a source reference derived from the Wazuh event ID. |
| 10a | [Wazuh detections in the IRIS L1 queue](week4/fig-10a-l1-queue.png) | The analyst queue shows Wazuh-sourced alerts following the Shuffle run. |
| 10b | [Shuffle workflow branches](week4/fig-10b-shuffle-repeater.png) | The Repeater connects to IRIS and a cache branch. Duplicate suppression was explored but was not verified. |
| 11 | [IRIS statistics after handoff testing](week4/fig-11-iris-statistics.png) | The statistics view shows eight alerts and one linked to a case at the time of capture. |
| 12 | [n8n response workflow](week4/fig-12-n8n-response-flow.png) | Qualifying events follow the preparation and Wazuh API branch. Other events follow Ignore Alert. |
| 13 | [Wazuh decoder and rule for block events](week4/fig-13-wazuh-containment-rule.png) | The decoder extracts a source IP and duration from a block log; rule 110350 records the response at level 10. |
| 14 | [IRIS containment alert and n8n execution](week4/fig-14-iris-and-n8n-validation.png) | IRIS shows the block event for 10.10.10.50 for 120 seconds. The n8n execution below shows the response path. |

The lab IPs, timestamps, rule IDs and results are retained. Figure 7 has an opaque redaction over the webhook address. Figure 10a focuses on the analyst queue; Figure 14 focuses on the IRIS and n8n panels of the original capture.
