---
title: Cloud cost chargeback
publishDate: 2021-10-01 00:00:00
img: /assets/billing.png
img_alt: Data flow diagram with several steps where the cost and usage report data is processed to generate a final bill
description: |
  Efficient chargeback of platform services
tags:
  - AWS
  - Platform engineering
  - FinOps
---

As part of the platform team, I was the owner of the billing system, responsible for chargeback of the costs incurred by the use of the platform, including company-provided shared services. Each AWS Cost and Usage Report contains ~100 GB of zipped CSV files.

I inherited a PySpark/Glue-based system that took hours and cost thousands of dollars per month to process 20 GB of data. By adopting streaming processing and a serverless architecture, I reduced that processing time to a few minutes. The cost was well within the serverless free tier.

That improvement allowed us to add more features to the system, including custom allocation rules, removing administrative blockers for platform adoption.

I was invited to present this approach in an [AWS Cloud Financial Management Peer Connect](https://pages.awscloud.com/aws-cfm-peer-connect-11102021.html) on Nov 10th, 2021.

Work performed for a global financial instituition under guidance of [Nauman Noor](https://www.pcas.ai/). Illustrative diagram does not include any company-specific information or details.