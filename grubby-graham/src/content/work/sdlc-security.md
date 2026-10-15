---
title: SDLC security program
publishDate: 2024-05-01 00:00:00
img: /assets/sdlc.png
img_alt: Flow diagram from policy and vendor evaluation to container and IaC scanning tools, adopted by about ten CI owners, followed by a tollgate, a risk exception process and incident escalation
description: |
  Container and IaC scanning, tollgates and risk exceptions across the company
tags:
  - Security
  - SDLC
  - DevSecOps
---

As lead engineer for SDLC cybersecurity, with no direct reports, I worked across the company's platform teams. The company buys other companies and absorbs them, so the estate was very mixed: Solaris, Kubernetes, Windows and more.

I aligned about ten CI owners across the subsidiaries and got all of them to implement container scanning and IaC scanning in their pipelines. The scanning tool changed once because the vendor changed. Container scanning applied only where containers existed, but the process applied to everyone.

I was also handed the process around the tollgates, which is distinct from enabling the tools: the communications, what threshold counts as a blocker, how findings are explained to teams, how exceptions are documented and implemented, and how incidents are raised. I designed and implemented the risk exception process. It was audit-driven, every development team in the bank used it, and it had to work.

I wrote security policies and guidelines from scratch, and evaluated scanning tools from five vendors with hands-on testing, including sizing the budget. The final purchase was made by another team.

Because the security team was mostly engineers and operators rather than developers, I picked up the hard engineering problems. Two examples: forcing a non-cloud vendor application on EC2 to behave properly in an Auto Scaling Group by automating its bootstrap over SSH with Lambda functions, and a Bash script to hunt for hardcoded credentials across live servers, from decades-old SunOS, RHEL and AIX to modern Ubuntu and AL2023, covering more than 30K machines periodically.

Work performed for a global financial institution. Illustrative diagram does not include any company-specific information or details.
