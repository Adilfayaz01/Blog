+++
title = "Part 4: Continuous Validation"
description = "Audit logs, monitoring, and making zero trust a habit  detection, response, and review."
date = '2026-09-22T09:00:00+05:30'
weight = 4
draft = false
tags = ["zero trust", "monitoring", "audit", "cloud security"]
+++

By now you've hardened your identities and your network. Good. Here's the part most teams skip: **zero trust is not a one-time hardening project.** It's a continuous loop  **detect, respond, review.** The moment you stop watching is the moment a trusted identity gets quietly abused.

Think of it like a fire alarm. Installing the alarm isn't the end of the safety work  someone has to check the batteries, test it, and actually listen when it goes off. Zero trust is the same. Setup is the beginning, not the finish line.

### Build the Detection Layer

- **AWS:** CloudTrail for API activity, GuardDuty for anomaly detection, and a baseline of normal `AssumeRole` patterns. Know what "normal" looks like so you can spot the deviation.
- **Azure:** Microsoft Defender for Cloud with activity log streaming into a SIEM. Centralize it  a log nobody reads is just storage.
- **GCP:** Cloud Audit Logs  especially *data access* logs for storage, plus Security Command Center for posture.

### What to Watch

These three are the classic smoke signals of an in-progress breach:

1. **Privilege escalation**  new admin roles, role grants to unexpected principals. Someone quietly giving themselves more keys.
2. **New regions / new providers**  attacker infrastructure often shows up as unfamiliar geography. "Why is my Singapore workload pinging us?"
3. **Mass exfiltration**  unusual download volume from storage or databases. The whole point of the attack, happening now.

### The Review Loop

Every month, re-run your IAM and network reviews. **Access rots:** people leave, projects retire, but grants persist. That contractor who quit last year? Their role is probably still alive, quietly waiting. Least privilege is a verb, not a checkbox  it's something you do over and over, not a one-time configuration.

That closes this playlist. The throughline: **identity** decides who can act, **segmentation** decides where they can go, and **continuous validation** keeps both honest. If you're going to act on only one thing from this series, start with the identity audit  it delivers the fastest reduction in blast radius. Do that first, then come back and take it from the top. You'll see the whole system differently.