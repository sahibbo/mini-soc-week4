# Week 4 lab journal

1. **Bring up the SOAR services.** Shuffle containers started on the SIEM host. IRIS was accessible, and distinct L1, L2 and service identities were configured. [Figures 1–4](evidence/INDEX.md)
2. **Test the analyst handoff.** A synthetic connectivity alert reached L1. L2 opened a case with the escalation reason and a link to that alert. [Figures 5–6](evidence/INDEX.md)
3. **Verify the intake from its trigger.** A successful manual action test was not enough to establish delivery. A webhook-started run carried rule 5763 and the IRIS action returned success; the analyst queue provided independent confirmation. The cache path was not validated for deduplication. [Figures 7–11](evidence/INDEX.md)
4. **Observe the response decision.** A separate n8n workflow validated incoming data, chose between containment and ignore, and requested Active Response through the Wazuh API. [Figure 12](evidence/week4/fig-12-n8n-response-flow.png)
5. **Link the response to an analyst record.** The custom decoder extracted the blocked address and duration; the log test selected rule 110350 at level 10. During the controlled run, IRIS showed the 120-second block for 10.10.10.50 alongside SSH detections. [Figures 13–14](evidence/INDEX.md)

Further work identified in the lab report: verify suppression of duplicate alerts, refine severity mapping and document analyst rollback decisions.
