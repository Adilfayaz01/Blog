+++
title = "Part 2: Identity Is the Control Plane"
description = "Mapping zero trust onto IAM: service accounts, workload identity, and conditional access in the big three clouds."
date = '2026-09-08T09:00:00+05:30'
weight = 2
draft = false
tags = ["zero trust", "iam", "identity", "cloud security"]
+++

Here's a mental experiment: take every identity in your cloud account, add up everything each one *could* do, and imagine a single stolen key handing that all to an attacker. How far could they get in five minutes?

That's the real security question in the cloud  because in the cloud, the network is software-defined and the boundaries are policies. **Identity is the single most important control you own.**

If you take one idea from this playlist, take this: **an overprivileged identity is a backdoor that ships with your architecture.** The blast radius of any compromise is defined by how much that stolen identity could do. Want smaller breaches? Give identities less to do.

### AWS

- Use **IAM roles** for workloads, never long-lived access keys. Keys that last forever are secrets waiting to leak.
- Scope policies to the smallest action set (`Action`, `Resource`, `Condition`). If a role doesn't need it, don't grant it.
- Enable **CloudTrail** and alert on `AssumeRole` from unexpected principals  that's the fingerprint of a hijacked session.

### Azure

- Prefer **managed identities** over client secrets for Azure resources. No secret to rotate, no secret to leak.
- Use **Conditional Access** to gate access by device compliance, location, and risk  so a laptop that's "you" in the office isn't "you" from a foreign coffee shop.
- Scope role assignments at the resource group level, not the subscription. Least privilege, one level at a time.

### GCP

- Bind service accounts to specific resources and use **workload identity federation** for on-prem workloads.
- Apply the **principle of least privilege** with custom roles instead of blanket `roles/editor`. A role named "just what this service needs" beats "everything."
- Remember: a `roles/owner` on a single service account is an org-wide key. Treat it like a master key  because it is.

The pattern is identical everywhere: machines get short-lived, scoped identities; humans get risk-aware access; **nothing is permanently trusted.** If that sounds like extra work, remember the alternative  one leaked key, one flat blast radius.

Next, we take this into the network layer  segmentation, and why a flat cloud network is a breach waiting to happen.