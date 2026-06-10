# Architecture

The repository documents an **AI-managed SOC lab** built around:

- a cheap public VPS
- Hermes Agent as the automation layer
- honeypots for attacker telemetry
- threat-intel enrichment
- Netdata for observability
- AgentMail for structured email reports

## High-level design

```text
Attackers / Internet traffic
        |
        v
  [ Public VPS / hermes-home ]
  |  honeypots
  |  firewall / blocklists
  |  threat-intel pipeline
  |  Netdata dashboard
  |  email pipeline
        |
        v
  Hermes Agent
  - runs scripts
  - enriches findings
  - sends reports
  - updates automation
        |
        v
  Operator (Telegram / Email / Gmail forwarding)
```

## Main components

### Hermes Agent
The agent is the automation and operations brain. It:
- runs scheduled security tasks
- interprets telemetry
- formats reports
- manages cron jobs
- decides what is interesting enough to surface

### Honeypots
Honeypots expose attractive services for attackers, such as:
- SSH
- FTP
- Telnet
- SMB
- database ports
- other service emulation

The purpose is **observation**, not protection.

### Threat intel pipeline
Suspicious activity is enriched with sources like:
- Spamhaus / Tor exit data
- Abuse/threat feeds
- VirusTotal
- IPinfo
- OTX
- local YARA / JA3 / GeoIP data

### Reporting
Operator-facing outputs include:
- daily security brief
- weekly SOC report
- email forwarding
- threat summaries

### Observability
Netdata provides near-realtime system visibility for:
- CPU
- memory
- disk
- custom metrics
- operational health

## Why this architecture works for learning

This stack is valuable because it touches several real-world areas at once:
- blue team operations
- detection engineering
- incident triage
- threat intelligence enrichment
- automation design
- data storytelling

It is intentionally small enough to understand end to end.
