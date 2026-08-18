+++
date = '2026-08-18T10:00:00+05:30'
draft = false
title = 'Using AI for Day-to-Day Security Tasks: The Good, The Bad, and The Risky'
tags = ["AI", "security", "automation", "SOC", "detection", "cloud security"]
+++

Everyone is shouting about AI in security. Vendors promise "AI-powered threat detection" on every slide deck. LinkedIn gurus claim AI will replace the entire SOC. And then there's the other extreme: the purists who insist AI has no place in security at all.

I use AI every single day for security work, and the truth sits somewhere boring: it's a great tool for some things, a dangerous crutch for others, and knowing the difference is the whole game. Here's the honest take from someone who actually runs it daily.

## Where AI Actually Earns Its Keep

Let's start with what genuinely works. Not the marketing, not the demos, the real daily wins.

**Log triage.** Dump 5,000 lines of GCP Cloud Audit logs into a prompt and ask what matters. The AI flags the 12 entries worth your time, like a service account suddenly calling `storage.objects.setIamPolicy` at 2 AM. Would grep have found it? Eventually. But the AI found it in 30 seconds and summarized why it's suspicious.

**Writing detection rules.** KQL, SPL, YARA, regex. The syntax is fiddly and the AI is genuinely good at it. Ask for "a KQL query that finds VMs with public IPs and no NSG attached" and you get correct syntax first try, in 2 minutes instead of 30. It's not writing novel detection logic, but it removes all the syntax fighting.

**Automation scripts.** Repetitive Python is the sweet spot. I asked for a script that pulls every IAM binding from a GCP project, cross-references it against a least-privilege baseline, and outputs a CSV of over-privileged service accounts. One shot, working code, 10 minutes instead of an afternoon.

**CVE digestion.** Drop a vendor advisory plus your asset inventory into a prompt and get back: which resources are affected, what the patch priority should be, and a suggested rollout order. It won't be perfect, but it turns a 20-page advisory into a 10-line action list.

**IaC review before deploy.** Paste `main.tf` and ask for security issues. The AI catches `0.0.0.0/0` in a security group rule before it ever reaches production. This is genuinely better than a manual review, because the AI doesn't skim when it's tired.

**Report writing.** You found a critical vulnerability. Now the writeup. The AI turns raw technical findings into a readable summary for management in five minutes. This used to eat half my day.

**It's always awake.** 3 AM incident? The AI doesn't have a timezone. It doesn't need coffee. It's there, ready to correlate logs, right now.

## Where It Goes Wrong

Now the part nobody puts in the marketing.

**Hallucinations in critical contexts.** The AI confidently invents a `gcloud iam fix-everything` command that doesn't exist. Worse: in a detection rule, it invents a KQL operator that looks plausible but silently returns nothing. The rule ships, the alerts never fire, and you feel safe while being blind. That's the dangerous one.

**Data leakage.** Pasting a real `.env` file or customer PII into a third-party chat tool means you just exfiltrated data to a company with no contract with yours. This happens constantly because it's so easy. Copy, paste, done. You just leaked credentials to a training dataset.

**Automation bias.** An AI-generated Terraform "fix" that widens a firewall rule looks professional, so you merge it. It breaks compliance silently, and nobody notices for three months. The scariest AI mistake is the one that looks competent.

**Zero accountability.** The AI recommends an IAM change. You apply it. It locks everyone out of prod at 11 PM. Guess whose name goes on the postmortem? The AI won't be in the incident review call.

**No context about your environment.** The AI suggests deleting a service account it thinks is unused. It doesn't know that account runs your payment processing cron at 3 AM. It can't know. Your environment's undocumented quirks live only in your head and your runbooks.

**Noisy detections.** Ask the AI to write a SIEM rule for "suspicious HTTP activity" and it matches the word "HTTP" in every log line. 9,000 false positives overnight, and the SOC tunes it out forever, including the real alerts.

**The AI itself is an attack surface.** Prompt injection in a phishing email that your AI triage agent "reads" and acts on. A security agent given admin credentials "to help" that a threat actor now has. The more access we give AI agents, the more attractive they become as targets.

## The Rules I Live By

After enough bruises, these are non-negotiable:

- **Never paste secrets or real customer data.** Sanitize. Use placeholders. If it's real, it doesn't go in.
- **AI proposes, human disposes.** Every diff gets reviewed. Every rule gets read. Every recommendation gets checked. Always.
- **No destructive actions, ever.** The AI drafts the `gcloud` commands. You run them. It never touches prod directly.
- **AI writes the rule, you test it against real data** before it goes anywhere near a live detection pipeline.
- **AI is great for drafts, banned from final sign-off.** The accountability stays human. That's the deal.

## A Day in the Life

Here's what this actually looks like for me on a normal day:

- **Morning.** The AI digests overnight SIEM alerts into a one-page triage summary. I read the summary, not the raw queue.
- **Midday.** The AI drafts a least-privilege IAM review script. I review the code, run it against a test project, then production.
- **Before deploy.** The AI reviews the IaC diff for misconfigurations. I read every finding and confirm each one before anything deploys.
- **During an incident.** The AI helps correlate logs across services and suggests what to check next. I confirm root cause and decide the fix.
- **After.** The AI drafts the writeup. I edit, sign, and own it.

Notice the pattern: the AI does the volume work, I do the judgment work. If you want to structure this into a repeatable system, that's exactly what [custom skills and pipelines](/posts/building-custom-ai-skills-and-pipelines/) are for.

## The Bottom Line

AI in security is a force multiplier, not a replacement. Think of it as an always-available junior analyst that is fast, tireless, and occasionally hallucinates with total confidence. You would never let a junior analyst make production changes without review, and the same applies here.

Delegate the volume: log triage, rule syntax, boilerplate scripts, report drafts, advisory summaries. Keep the judgment: what's actually suspicious, what gets blocked, what touches prod, and who's accountable when it breaks.

The future of security work isn't humans versus AI. It's humans who use AI well versus humans who don't.
