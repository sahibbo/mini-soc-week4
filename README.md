# Mini-SOC in a Box — Week 4

**Blue Team Capstone | LabShop Security Operations Center**

Two workflows were validated in the LabShop Mini-SOC. Shuffle delivered Wazuh detections to the DFIR IRIS analyst queue; n8n handled the decision to request a temporary IP block. A synthetic handoff also showed that an L1 analyst could escalate an alert into an L2-owned case.

**Previous phase:** [Week 3 — network detection and native Wazuh response](https://github.com/sahibbo/mini-soc-week3)

**Technical report:** [View PDF](docs/Week4-Technical-Report.pdf) · [Download Word](docs/Week4-Technical-Report.docx) · [Browse all 14 figures](evidence/INDEX.md)

## Workflows and results

| Path | What was verified | Evidence |
|---|---|---|
| Wazuh → Shuffle → DFIR IRIS | The integration accepted JSON alerts at Wazuh level 10 or above. A webhook run carried SSH rule 5763 into the IRIS Add Alert action; Wazuh detections were visible to SOC L1. | [Webhook run](evidence/week4/fig-08-shuffle-webhook-run.png) · [IRIS fields](evidence/week4/fig-09-iris-action-fields.png) · [L1 queue](evidence/week4/fig-10a-l1-queue.png) |
| SOC L1 → SOC L2 | L1 assigned a synthetic connectivity alert to L2. The L2 case linked to the original alert and documented the reason for escalation. | [Test alert](evidence/week4/fig-05-synthetic-alert.png) · [L2 case](evidence/week4/fig-06-l2-case-handoff.png) |
| Wazuh → n8n → Wazuh Active Response | The n8n decision branch requested a temporary block. The test recorded a 120-second block for 10.10.10.50. | [Workflow](evidence/week4/fig-12-n8n-response-flow.png) · [Run and IRIS record](evidence/week4/fig-14-iris-and-n8n-validation.png) |
| Response log → Wazuh → IRIS | Rule 110350 at level 10 produced a separate analyst-visible record containing the blocked source and duration. | [Decoder and rule](evidence/week4/fig-13-wazuh-containment-rule.png) · [Containment record](evidence/week4/fig-14-iris-and-n8n-validation.png) |

Week 3 documents the **native 180-second** Wazuh action and its block/unblock events. Week 4 documents the **n8n-driven 120-second** response. The Shuffle cache branch was investigated; duplicate suppression was not verified.

## Repository guide

- [Architecture and addressing](architecture/addressing.md) · [Alert and response paths](architecture/network-diagram.md)
- [Workflow notes and field mapping](workflows/README.md)
- [Wazuh decoder, response rule and integration example](rules/README.md)
- [Lab journal](journal.md) · [Evidence index](evidence/INDEX.md)
