# Less Than Whataburger: What $5/Month Gets You in 2026

I pay $5.41 a month for a cloud server in Helsinki. After tax.

That server runs a full security operations center. It monitors honeypots that real attackers hit thousands of times a day. It enriches threat intelligence across multiple feeds. It runs web application scans, tracks blocklists, pushes custom metrics to a live dashboard, and emails me formatted briefs every morning and every Sunday. An AI agent handles all of it — the data collection, the correlation, the formatting, the delivery.

The model that runs that agent? A trillion-parameter MiMo-V2.5-Pro, served through Xiaomi's API at fractions of a penny per million tokens.

Let me say that again. A trillion-parameter model, running autonomously on a $5 server, costing less in compute than a Whataburger combo.

---

## The Stack That Shouldn't Work

The server is a Hetzner CX23. Two vCPUs, 4GB RAM, 40GB of storage. It's the cheapest tier Hetzner sells that isn't arm64. By any traditional measure, this machine should not be able to do anything interesting.

But the hardware doesn't need to be interesting. The cloud does the heavy lifting. The server just orchestrates.

Here's what runs on it:

- **Six Docker containers** — honeypots for SSH, FTP, Telnet, SMB, databases, and web applications. Each one isolated, each one generating real traffic from real internet scanners and attackers.
- **A threat intelligence pipeline** — pulls from multiple feed sources, enriches suspicious indicators against public databases, fingerprints TLS clients, scans downloaded payloads against YARA rules. Runs every six hours automatically.
- **Automated blocklists** — thousands of known malicious CIDRs loaded into kernel-level sets. Drops traffic at line rate before it reaches a single application.
- **A metrics pipeline** — pushes custom security counters to a live dashboard every 30 seconds. Honeypot connections, unique attackers, firewall blocks, intel hits, pipeline health. All visible on one page.
- **An email pipeline** — the agent writes and sends a formatted daily security brief, a comprehensive weekly SOC report, and forwards inbound messages to personal email. All HTML, all readable, all automated.
- **Encrypted offsite backups** — because losing a $5 server's worth of data would be embarrassing more than catastrophic, but still not fun.

The agent doesn't just monitor. It acts. When confirmed malicious infrastructure is identified, firewall rules update. When blocklists refresh, traffic drops. When the system detects drift — a new open port, a missing security control — it flags it in the next report.

---

## The Model That Costs Nothing

MiMo-V2.5-Pro is a 1.02 trillion parameter mixture-of-experts model with 42 billion active parameters per token. To run this locally, you'd need a cluster of H100s. At US electricity rates, the power bill alone would be $30-80 per day — more than the entire monthly cost of this setup.

Through Xiaomi's API, on the Lite plan that costs effectively nothing with the current promotional credits, I'm running inference at what amounts to free-tier volumes. The credits they give you — 4.1 billion on the base plan — represent more tokens than a single person would plausibly consume in months of daily agent use.

The model is genuinely capable. It handles tool calling, long context, structured output, and multi-step reasoning without complaint. The only quirks are occasional infinite loops on very complex chains and some aggressive content moderation false positives — both manageable with prompt structure and fallback logic.

---

## The Agent That Makes It Work Without a Salary

Hermes Agent is the operational core. It's an open-source AI agent framework by Nous Research that runs in the terminal, connects to messaging platforms, schedules tasks, remembers context across sessions, and learns from experience by saving reusable procedures.

In this setup, it does the work that would take a junior security analyst several hours a day:

- **07:00** — Wake up, run threat correlation. Parse honeypot logs from the last 24 hours. Count connections, unique IPs, top credentials, command sequences. Compare against yesterday. Save for trend tracking.
- **08:00** — Collect OSINT findings. Check certificates, exposed infrastructure, pipeline outputs.
- **08:30** — Format and email the daily brief. System health, honeypot stats, top attackers, blocklist status, web scan results, intel pipeline health, pending updates. Readable in under two minutes.
- **Throughout the day** — Threat intel enrichment. Web scans. Honeypot harvesting. Backup monitoring. All on independent schedules.
- **Sunday 09:00** — Compile the weekly report. Executive summary with KPIs. Honeypot deep-dive with tables. Threat intel status. Trend comparison against the previous week.

The agent doesn't need sleep, doesn't take weekends, doesn't get bored. It reads the data, synthesizes it, and tells me what matters. All for the cost of the API calls.

---

## The Comparison That Sounds Fake

Let me put this in concrete terms.

| Item | Cost |
|---|---|
| Whataburger #1 combo (double meat, large) | ~$9.50 |
| One month of this entire security stack | ~$5.41 |
| Difference | I save $4 and get a SOC instead of lunch |

One trip to Whataburger funds 1.75 months of a production-adjacent security operations center that runs 24/7, never calls in sick, and gets smarter every week.

The model alone — MiMo-V2.5-Pro at the promotional rate — would take something like 30,000+ Whataburger combos to match the upfront hardware cost of the GPU cluster needed to run it locally. And that's before the electricity.

---

## What This Actually Means

There are two narratives about AI and cloud infrastructure in 2026.

**Narrative A:** Everything is too expensive. GPUs cost too much. Cloud bills are out of control. AI is only for well-funded companies.

**Narrative B:** The cost of inference has collapsed. A trillion-parameter model costs fractions of a penny per million tokens. A $5 server runs software stacks that would have required a small team and a large budget five years ago. The barrier to entry for serious technical work is approaching zero.

Both narratives are true for different people. But for a student, a hobbyist, or anyone who wants to learn by building — Narrative B is the one that matters.

The infrastructure that used to cost thousands now costs pocket change. The models that used to require cluster access now run through a web API. The operational work that used to consume hours now happens autonomously.

The only thing that hasn't changed is the need to understand what you're building. And that's exactly the thing a setup like this forces you to learn — not by reading, but by operating a real system that real attackers are hitting right now.

That's the whole thesis of the $5 SOC. Not that you can build a production SOC for pocket change — though technically you can. But that the best way to learn security and AI operations is to build something real and watch it work. Or break. Then fix it.

The server costs less than lunch. The model runs on what amounts to promotional air. The agent handles the grunt work.

The only expensive part is paying attention.

---

*The full repository, including architecture docs, setup guidance, sanitized examples, and a visual diagram, is at [github.com/hellasleeper108/5-dollar-soc](https://github.com/hellasleeper108/5-dollar-soc). The write-up describing the stack in more detail is at [docs/the-5-dollar-soc.md](docs/the-5-dollar-soc.md).*

*Server: Hetzner CX23 · Agent: Hermes Agent · Model: MiMo-V2.5-Pro via Xiaomi API · Honeypots: Cowrie + Dionaea · Dashboard: Netdata · Backup: Restic*