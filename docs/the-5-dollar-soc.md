# The $5 SOC: What I Actually Use a Cheap Cloud Server For

I'm an AI engineering student with a cybersecurity problem: I learn best by doing, but most security labs are either theoretical slides or expensive enterprise toys. So I built one on a cloud server that costs less than coffee.

The idea was simple. What if an AI agent could run my security stack — monitor honeypots, collect threat intel, scan for vulnerabilities, and email me a daily report — while I focused on learning from the output?

It turns out that works. And it taught me more than any course has.

---

## The Architecture

The stack runs on a single cheap Ubuntu VPS. No Kubernetes. No cloud-native buzzwords. Just a server, Docker containers, and an AI agent gluing everything together.

The core loop is:

**Attract → Capture → Enrich → Report → Improve**

### Attract

Multiple honeypots run in isolated Docker containers, exposing services like SSH, FTP, Telnet, SMB, database ports, and web application panels to the open internet. These aren't defended — they're baited. Every connection is a data point.

### Capture

Incoming traffic is logged, parsed, and stored. The honeypots capture credentials tried, commands executed, files downloaded, and protocols probed. A real-time metrics pipeline pushes custom counters to a dashboard for at-a-glance visibility: connection rates, unique attackers, command volume, download attempts.

### Enrich

Suspicious IPs get piped through a multi-stage enrichment pipeline. Blocklists from threat intelligence providers check against known malicious infrastructure. Geolocation data maps attacker origins. Public threat databases return reputation scores, associated malware families, and known attack campaigns. Fingerprinting systems identify TLS client behaviors and malware signatures in downloaded files.

### Report

Every morning, the AI agent gathers the last 24 hours of data — honeypot stats, enrichment results, blocklist changes, system health, pending updates — and emails a formatted security brief. Every Sunday, a comprehensive weekly report goes out with trends, top attackers, command analysis, and operational metrics. Both are dark-themed, readable, and actionable.

### Improve

The agent doesn't just report. It acts. When threat intelligence identifies confirmed malicious infrastructure, firewall rules get updated automatically. Blocklists refresh daily. New indicators get checked against historical data. The stack gets smarter while I sleep.

---

## What Runs on the Box

The system is a collection of focused components, each doing one thing well.

**Honeypots** run in Docker, isolated from the host and from each other. They emulate real services convincingly enough that automated scanners treat them as genuine targets.

**A threat intelligence pipeline** runs on a schedule, pulling from multiple public and API-based sources. It correlates indicators across sources, scores them by confidence, and feeds results into both the reporting system and the automated blocking layer.

**Automated blocklists** use efficient set-based lookups rather than individual firewall rules. Thousands of known malicious network ranges get dropped at the kernel level in seconds, not minutes.

**A web application scanner** tests the honeypot web interfaces for common vulnerabilities — injection, template injection, WordPress misconfigurations — on a recurring schedule. Results feed into the same reporting pipeline.

**A real-time dashboard** provides instant visibility into system health, custom security metrics, and operational status. No Grafana setup required — it just works.

**An email pipeline** delivers reports directly to an inbox. New messages that arrive in the monitoring inbox get automatically forwarded to a personal email. The AI agent writes, formats, and sends every report.

**An encrypted backup system** runs nightly, with offsite storage and integrity verification.

**A hardening audit** checks for configuration drift weekly — open ports, unauthorized changes, missing security controls.

---

## The AI Agent's Role

The agent isn't a chatbot bolted onto the side. It's the operational core.

It wakes up on a schedule, reads the data the pipeline has collected, synthesizes it into something useful, and delivers it. When it finds something interesting — a new attack pattern, a spike in traffic from a particular region, a novel command sequence — it flags it prominently.

The agent also handles the tedious parts that make security operations exhausting: correlating data across sources, formatting reports, maintaining blocklists, and checking whether yesterday's top attackers are still active today.

But the real value isn't automation. It's interpretation. Raw logs are noise. An agent that can read the logs, understand what matters, and present the story — that's where cheap cloud servers start punching above their weight.

---

## What a Typical Day Looks Like

**07:00** — The threat correlation pipeline runs. Honeypot logs from the last 24 hours get parsed: connections, unique IPs, top credentials, command sequences, file downloads. Data gets saved for trend comparison.

**08:00** — The OSINT pipeline checks for new certificates, exposed credentials, and suspicious infrastructure activity.

**08:30** — The daily security brief gets emailed. It includes system health, honeypot stats, top attackers, blocklist status, web scan findings, threat intel pipeline results, and pending updates. Green, yellow, red indicators make it scannable in under two minutes.

**Every 6 hours** — The threat intel pipeline enriches new indicators, checks reputation databases, and auto-blocks confirmed malicious infrastructure.

**Every 6 hours** — The web scanner tests honeypot web apps.

**Every 6 hours** — The honeypot harvester collects and summarizes new telemetry.

**Sunday 09:00** — The weekly SOC report goes out. Executive summary with KPIs, honeypot deep-dive with tables, threat intel pipeline status, blocklist metrics, and a trend comparison against the previous week.

The total time I spend reading these reports: maybe 10 minutes a day. The total time the system saves me from manually parsing logs: hours.

---

## What I Learned

### 1. Attackers are boring until they're not

Most honeypot traffic is automated brute-forcing. Same usernames, same passwords, same commands. But occasionally something novel shows up — a new command sequence, a previously unseen malware sample, an attacker probing multiple services in a coordinated pattern. Those moments are where the real learning happens.

### 2. Threat intel is only useful if you act on it

Feeds and databases are easy to collect. The hard part is building the pipeline that turns indicators into action: blocking infrastructure, enriching reports, correlating across sources. A list of malicious IPs is data. A system that automatically blocks them and tells you why is intelligence.

### 3. Reports need to be readable

If a security report isn't formatted well, you won't read it. If you won't read it, you won't learn from it. Investing in clean, dark-themed, scannable HTML emails was one of the highest-ROI decisions in the entire project.

### 4. An AI agent is a multiplier, not a replacement

The agent doesn't replace security knowledge. It multiplies it. It handles the data collection, correlation, and formatting so you can focus on the interesting questions: Why did this pattern emerge? What's this attacker doing differently? What should I investigate next?

### 5. A $5 server is enough

You don't need expensive infrastructure to learn security operations. You need traffic, telemetry, and a system that helps you make sense of it. A cheap cloud server with a public IP gets more attacker attention than most people realize.

---

## What You'd Need to Build This

- A cloud server with a public IP (Ubuntu recommended)
- Docker for honeypot isolation
- An AI agent framework with cron scheduling and email capability
- Public threat intelligence APIs and feeds
- A metrics dashboard
- A few weekends of setup and iteration

The total cost is dominated by the server. Everything else has free tiers or open-source alternatives.

---

## Why This Matters

Security education has a gap. You can study theory, pass certifications, and complete capture-the-flag challenges — but until you've operated a system that real attackers are actively probing, you're missing the intuition that makes a good security engineer.

This project builds that intuition. Not through simulated environments, but through real traffic, real telemetry, and real operational decisions.

It's cheap. It's practical. And it runs while you're doing something else.

That's the whole point.

---

*The repository is at [github.com/hellasleeper108/5-dollar-soc](https://github.com/hellasleeper108/5-dollar-soc). It includes architecture docs, setup guides, sanitized examples, and a launch-ready diagram.*
