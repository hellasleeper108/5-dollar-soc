# 5 Dollar SOC — Full Setup Guide

This guide explains how the repository is meant to be used.

## 1. Understand the goal

This is not a hardened production SOC.  
It is a **learning system** built around a cheap VPS and an AI-automated operator workflow.

Use it to study:
- security monitoring
- honeypot telemetry
- threat enrichment
- reporting
- automation design

## 2. Create your base server

Recommended starting point:
- Ubuntu VPS
- public IP
- SSH access
- ability to run Docker
- enough disk for logs and backups

## 3. Install Hermes Agent

Follow the Hermes Agent install docs:
- install Hermes
- connect a model provider
- connect Telegram or another gateway
- verify the agent can run commands, create files, and schedule cron jobs

## 4. Decide your operating model

You need three layers:

### Collect
- honeypots
- firewall logs
- auth logs
- web app observations

### Enrich
- threat feeds
- reputation sources
- IP metadata
- optional YARA / JA3 / GeoIP data

### Report
- daily email brief
- weekly report
- optional Telegram alerts

## 5. Sanitize before publishing

Do not publish:
- API keys
- real IPs
- internal hostnames
- personal email addresses
- inbox IDs
- tokens
- tailscale addresses
- router information

Use `.env.example` and placeholder docs instead of real config.

## 6. Use the repo as documentation, not just code

This project works best when you document:
- what you built
- what surprised you
- what broke
- what you automated next
- what you learned from attacker behavior

That story is the real product.

## 7. Suggested repo flow

- keep `docs/` narrative-heavy
- keep `examples/` sanitized
- keep `cron/` readable
- keep diagrams visible
- avoid turning the repo into a private config dump

## 8. Recommended launch assets

A good public repo should include:
- strong README
- architecture diagram
- component explanation
- sanitized examples
- learning outcomes
- cost framing
- optional screenshots

That is what makes other people care.
