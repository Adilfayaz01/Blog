+++
title = "Part 1: What Zero Trust Actually Means"
description = "The mental model: trust nothing, verify everything. Why the castle-and-moat era is over."
date = '2026-09-01T09:00:00+05:30'
weight = 1
draft = false
tags = ["zero trust", "security", "cloud security"]
+++

Stop me if you've heard this one: *"We're secure  the firewall is up, the VPN works, we're fine."* It's the same story every breached company tells right before they're not fine.

That confidence rests on a myth. The castle-and-moat model assumes that once you're inside the wall, you can be trusted. But the modern cloud doesn't have walls. Your data, your workloads, and your users live everywhere  on laptops, in containers, across three continents. There is no moat.

**Zero trust is not a product you can buy.** It's a threat model: an operating assumption that no device, user, or network is trusted by default  no matter where it sits. Every request, to every resource, gets authenticated, authorized, and encrypted, as if it originates from an open network.

Here's the uncomfortable part: that's exactly how attackers treat your network. They assume *they* can get in. The question isn't *if* someone breaches you  it's how far they can move once they do.

### The Core Pillars

Think of these as the four rules that decide how far a compromise travels.

1. **Identity is the new perimeter**  the user or workload identity, not the network segment, is what grants access.
2. **Least privilege by default**  grant the minimum access required, and nothing more.
3. **Micro-segmentation**  break the network into small zones so a compromise can't pivot freely.
4. **Continuous validation**  access decisions are re-evaluated on every request, not just at login.

That last point is where zero trust parts ways with the old VPN mindset. A session isn't a blanket pass you earn once and keep forever. **Each action is a fresh decision.** Think of it like a bouncer at a club  but one who checks your ID at every single table you walk past, not just at the door.

In the next part, we'll map these principles onto IAM and service accounts in AWS, Azure, and GCP  because in the cloud, identity *is* the control plane. If you're not sure your identities are scoped tightly enough, you'll want to read closely.