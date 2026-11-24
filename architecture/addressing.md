# Week 4 services and roles

| Component | Location in the lab | Responsibility |
|---|---|---|
| Wazuh manager | siem-host · 10.10.10.10 | Detect SSH failures, publish alerts, accept response requests and record containment |
| Shuffle | SIEM host, Docker Compose | Receive qualifying Wazuh alerts and create IRIS alerts |
| DFIR IRIS | Lab case-management service | Keep the alert queue, analyst assignments and linked cases |
| n8n | Lab automation service | Validate an SSH alert, decide whether to request a block and call the Wazuh API |
| ubuntu-web | 10.10.10.30 | Protected SSH endpoint |
| Kali | 10.10.10.50 | Controlled source used to validate containment |

The integrations used private lab networking. The repository includes the configuration shape and observed result; the webhook address and authentication material are environment-specific.

[Event paths](network-diagram.md)
