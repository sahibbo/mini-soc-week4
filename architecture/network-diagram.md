# Alert intake and response paths

```mermaid
flowchart TD
    E["SSH events on ubuntu-web"] --> W["Wazuh manager"]
    W -->|JSON alerts level 10 and above| S["Shuffle webhook"]
    S --> I["IRIS alert queue"]
    I --> H["L1 triage and L2 case handoff"]
    W -->|SSH rule 5763| N["n8n decision"]
    N -->|Qualifies| R["Request block via Wazuh API"]
    N -->|Does not qualify| X["Ignore alert"]
    R --> L["Response log on endpoint"]
    L -->|Decoder and rule 110350| W
```

Returning a block log to Wazuh makes containment visible in IRIS through the same Shuffle intake. The separate synthetic L1-to-L2 case tested the analyst handoff.
