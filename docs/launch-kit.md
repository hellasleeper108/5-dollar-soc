# Launch Kit

Use this as starter copy for social posts or a launch blog.

## Short hook

I turned a cheap VPS into an AI-managed security lab.

Honeypots, threat intel, dashboards, automated email reports, and a trillion-parameter AI agent — all for less than a Whataburger combo.

## 10-post thread starter

1/ I pay $5.41/month for a cloud server that runs a full security operations center.

A trillion-parameter AI model administers it. Real attackers hit it thousands of times a day. It emails me reports.

All for less than lunch.

2/ The core idea is simple:
- attract attacker traffic
- capture telemetry
- enrich it
- report it
- improve the system every week

That loop teaches more than most courses.

3/ The model behind the agent is MiMo-V2.5-Pro. 1.02 trillion parameters. Cost per token: fractions of a penny.

To run that locally I'd need a GPU cluster pulling 20kW at the wall. The electricity alone would be $30-80/day.

Through the API: basically free.

4/ Hermes Agent acts as the automation and operator layer.

It runs scripts, checks findings, summarizes activity, and delivers reports like a junior analyst that never sleeps — but doesn't need a salary.

4/ The stack includes:
- honeypots
- threat intel enrichment
- Netdata dashboards
- automated email reports
- forwarding and observability
- a trillion-parameter AI agent

Total cost: $5.41/month. Less than a Whataburger combo.

5/ The math that breaks my brain:

A trillion-parameter model. On a $5 server. Running 24/7. Costing less in inference than a quick-service sandwich.

The electricity alone to run the GPU cluster for that model locally would cost 10x the entire monthly bill.

6/ The biggest lesson: small systems teach big lessons.

You learn detection engineering fastest when you have to triage your own noisy data.

7/ Threat intel is not useful until it becomes triage.

The point is not feeds. The point is asking:
- what changed?
- what matters?
- what do I investigate next?

8/ I also learned that operator-facing output matters.

If the system is hard to read, you stop learning from it.

That is why I built daily and weekly reports.

9/ The project is not about being production-grade.
It is about being real enough to force decision-making.

That is the fastest way to grow in security and AI ops.

10/ If you are a student or builder, try this pattern:
- one VPS
- one agent
- one honeypot
- one dashboard
- one report

Then expand only when you understand what is missing.

11/ Repo and writeup:
https://github.com/hellasleeper108/5-dollar-soc

The full read: docs/less-than-whataburger.md
