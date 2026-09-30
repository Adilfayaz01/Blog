+++
title = "Part 3: Segmentation and Network Hardening"
description = "Micro-segmentation, security groups, firewalls, and why a flat network is a breach waiting to happen."
date = '2026-09-15T09:00:00+05:30'
weight = 3
draft = false
tags = ["zero trust", "network", "segmentation", "cloud security"]
+++

Identity decides *who* can act. The network decides *where* a compromise can go. If you handle part two but leave the network flat, you've built a very secure front door and no walls between the rooms.

**A flat network turns one bad role into a lateral-movement playground.** The attacker doesn't need to break into your crown jewels  they just need to land *near* them. In a flat network, "near" is everywhere.

### The Rules of Micro-Segmentation

1. **Deny by default**  only allow the traffic you can justify. Justification is a feature, not a chore.
2. **East-west matters more than north-south**  the interesting movement is between workloads, not to the internet. That's where attackers roam.
3. **Document every rule**  an allow rule with no owner is a liability. If nobody knows why it exists, it's a door you forgot to close.

### AWS

Security groups are stateful  use them for fine-grained instance-level control. Put application tiers in separate subnets with NACLs as a coarse backstop. Remember that SG rules are evaluated per-instance, not per-subnet. Scope tightly, and your database tier won't accept traffic from your web tier  because there's no rule saying it can.

### Azure

NSGs bind to subnets or NICs and are the primary segmentation tool. Use **application security groups** to group by role ("web", "db") and reference them in rules instead of IPs, so rules survive IP churn. That way, "web" can talk to "db" without you ever hardcoding an address that will change next quarter.

### GCP

Firewall rules apply at the VPC level with **network tags** as the target mechanism. Tag your instances by role and write deny-by-default rules, then layer on Cloud Armor for edge protections. Clean tags mean clear rules  and clear rules mean you can actually read your own network.

A compromise will spread until a boundary stops it. **Boundaries are policies  write them intentionally.** The time you spend documenting one rule now is a breach you don't contain at 2 a.m. later.

Next and final: continuous validation  audit, monitoring, and making zero trust a habit rather than a one-time project.