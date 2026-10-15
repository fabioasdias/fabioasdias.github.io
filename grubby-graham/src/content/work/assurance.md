---
title: Secrets, backup and compliance automation
publishDate: 2019-09-01 00:00:00
img: /assets/assurance.png
img_alt: "Three lanes, a custom layer over AWS Secrets Manager with a rotation module, a backup layer over AWS Backup feeding a locked vault and a backup region, and compliance reporting producing weekly audit packages and tenant follow-up reports"
description: |
  Secrets management, backups and audit evidence that run themselves
tags:
  - AWS
  - Platform engineering
  - Security and compliance
---

**Secrets management.** I built a custom layer over AWS Secrets Manager with additional security checks and audit logging beyond what AWS provides natively. A separate module automated credential rotation for all the supported services, including many that AWS did not natively rotate, such as Oracle, OpenSearch and Redis. The layer provided production credentials (database credentials, API tokens and so on) to tenant production teams, handling thousands of calls per second because most tenants never cached results. Production services depended on it to authenticate, so it had to always work, and there were no outages while I owned it.

**Backup.** AWS Backup alone was not enough for the requirements of a regulated financial institution, so the team built a layer over it to automate and extend it. Everything was backed up automatically into a locked AWS vault, application teams had a self-service interface, and the layer added support for services AWS Backup did not natively support, such as Redshift. A backup region followed the data residency requirements that applied globally.

**Compliance reporting.** The framework was custom, driven by requirements specific to the institution rather than SOC 2 or PCI DSS. Using GuardDuty, Config, Security Hub and Audit Manager, the automation produced two kinds of output. Tenant follow-up reports pushed teams to fix findings, such as a service without TLS enabled. Audit packages were generated weekly from AWS Audit Manager with the required evidence, so they were always ready for the audit teams and nobody had to scramble when an audit started.

Work performed for a global financial institution. Illustrative diagram does not include any company-specific information or details.
