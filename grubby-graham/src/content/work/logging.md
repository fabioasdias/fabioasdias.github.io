---
title: Logging enrichment and storage
publishDate: 2019-09-01 00:00:00
img: /assets/logging.png
img_alt: Architecture diagram using AWS logos with S3 buckets, lambda functions, kinesis streams and OpenSearch
description: |
  Ensuring secure logging accessibility, retrieval, and storage at scale
tags:
  - AWS
  - Platform engineering
  - Distributed systems
---

As part of the platform team for an AWS landing zone, I was the owner for the system responsible for gathering, enriching, transporting, and storing logs from all applications. I modernized the traditional ELK stack by replacing the Logstash instances with Lambda functions, reducing monitoring and maintenance efforts.

While the storage relies on Managed OpenSearch, the rest of the system is serverless and scalable. It covers 13 global regions, and it scaled without architectural changes from ~500Gb/day to 5Tb/day in 3 years.

Since the system was architected for robustness, with multiple redundancies and automated recovery, it didn't require intervention even during some AWS Kinesis outages ([July 2024](https://aws.amazon.com/message/073024/), [November 2020](https://aws.amazon.com/message/11201/)). As soon as the underlying services became operational, the system automatically processed the backlog and <i>just worked</i>.

Work performed for a global financial instituition under guidance of [Nauman Noor](https://www.pcas.ai/). Illustrative diagram does not include any company specific information or details.
