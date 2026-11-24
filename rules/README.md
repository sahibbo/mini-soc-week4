# Week 4 Wazuh configuration

- [labshop_soar_decoder.xml](labshop_soar_decoder.xml) parses `LabShop SOAR: BLOCKED:` records. It maps the source to `srcip` and the duration in seconds to `extra_data`.
- [labshop_soar_rules.xml](labshop_soar_rules.xml) matches that decoder and emits rule **110350** at level **10**. The wording contains the source and the duration.
- [shuffle-integration.example.xml](shuffle-integration.example.xml) illustrates the manager’s JSON integration at minimum level 10. The URL is a placeholder. The lab used separate header authentication; no credentials or live workflow export are part of this example.

The decoder and rule are transcribed from [Figure 13](../evidence/week4/fig-13-wazuh-containment-rule.png). The integration is illustrated in [Figure 7](../evidence/week4/fig-07-wazuh-shuffle-integration.png). Rule **5763** is the SSH detection; **110350** records the resulting containment action.
