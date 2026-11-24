# How the two workflows use a Wazuh alert

## Shuffle: deliver Wazuh detections to analysts

The `custom-shuffle-auth` integration posts JSON alerts at level 10 and above to a private authenticated webhook. The IRIS Add Alert action supplies a title using the Wazuh rule ID, a description from the event, the source `Wazuh` and a source reference based on the Wazuh event ID. It also supplies customer, severity and status fields. The test run started at the webhook and the IRIS action returned HTTP 200; SOC L1 independently saw Wazuh records in the queue.

The workflow diagram also shows a Repeater and a cache action. The tested intake path reached IRIS. The cache branch was skipped in the observed execution, so duplicate suppression remains unverified.

[Webhook execution](../evidence/week4/fig-08-shuffle-webhook-run.png) · [Field mapping](../evidence/week4/fig-09-iris-action-fields.png) · [Workflow graph](../evidence/week4/fig-10b-shuffle-repeater.png)

## n8n: request containment and record it

The separate SSH response workflow validates the incoming alert and evaluates the source. If the blocking condition matches, n8n prepares the source address, authenticates to the Wazuh API and requests Active Response. Otherwise the workflow ends at Ignore Alert.

In the test, the endpoint logged a 120-second block for 10.10.10.50. The Wazuh decoder extracted the address and duration; rule 110350 made the action visible in IRIS. This is a different record from the initiating 5763 detection.

[n8n decision path](../evidence/week4/fig-12-n8n-response-flow.png) · [Wazuh decoder and rule](../rules/README.md) · [IRIS result](../evidence/week4/fig-14-iris-and-n8n-validation.png)
