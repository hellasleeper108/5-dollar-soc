# Honeypots

Honeypots are one of the most valuable learning tools in a security lab.

## Why use them

Honeypots help you:
- observe attacker behavior
- collect real-world logs
- understand credential stuffing and brute-force patterns
- see what commands attackers actually run
- study malware staging and download behavior

## What this project uses honeypots for

This project is not focused on deception for production defense.  
It is focused on **learning from real traffic**.

Common services to emulate:
- SSH
- FTP
- Telnet
- SMB
- database services
- HTTP admin panels

## Important safety rules

### 1. Keep honeypots isolated
Do not allow a compromised honeypot to pivot into your real systems.

### 2. Do not store real credentials near honeypots
Treat honeypot infrastructure as hostile territory.

### 3. Do not blindly trust captured payloads
Handle captured files carefully.

### 4. Monitor the host, not just the honeypot
Honeypot value increases when paired with system-level telemetry.

## Learning outcomes

After a few weeks of honeypot operation, you should be able to answer:

- Which ports attract the most traffic?
- Which credentials attackers try most
- What commands follow initial access
- Which IPs return repeatedly
- What files attackers attempt to stage

That is real defensive intuition.
