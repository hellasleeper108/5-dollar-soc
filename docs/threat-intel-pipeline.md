# Threat Intel Pipeline

This document describes the conceptual threat intel workflow used in the project.

## Pipeline stages

### 1. Ingest
Collect raw security telemetry:
- honeypot logs
- firewall blocks
- failed authentication attempts
- suspicious network activity

### 2. Normalize
Convert raw logs into consistent fields:
- source IP
- timestamp
- service / port
- action
- command / payload (if available)

### 3. Enrich
Add external context:
- ASN / org
- country / region
- reputation
- threat feed matches
- malware / proxy / bot indicators

### 4. Score
Prioritize indicators based on:
- repeated hits
- service breadth
- known malicious reputation
- command sophistication
- file download / payload behavior

### 5. Report
Produce human-readable outputs:
- daily briefs
- weekly summaries
- notable escalations
- operational lessons

## Good enrichment sources (non-exhaustive)

- Spamhaus DROP / EDROP
- Tor exit lists
- AbuseIPDB
- VirusTotal
- IPinfo
- OTX
- CISA / KEV
- public OSINT feeds

## Operational goals

A strong threat-intel workflow is not just about blocking.  
It should help you answer:

1. What is hitting me?
2. How noisy is it?
3. Is it opportunistic or targeted?
4. What changed since yesterday?
5. What should I investigate next?

## Lesson for students

Threat intel becomes useful only when it is connected to action, triage, or learning.

Raw feeds are cheap. Judgment is expensive.
