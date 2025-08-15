---
title: Multi-tenant observability
publishDate: 2024-01-01 00:00:00
img: /assets/monitoring.png
img_alt: AWS architecture diagram with monitored accounts feeding data to a centra account running AMP and grafana
description: |
  Multi-tenant monitoring across accounts and regions using Amazon Managed Service for Prometheus
tags:
  - AWS
  - Platform engineering
  - Observability
---

Observability is crucial in modern applications. That was included as provided service in our platform. I architected and modernized the approach by using Open Telemetry instances acting as middleware/forwarders to allow for cross-account aggregation at scale. It also provided an entrypoint for On-Premises ingestion.


This approach was documented in an [AWS blog post](https://aws.amazon.com/blogs/mt/multi-tenant-monitoring-across-accounts-and-regions-using-amazon-managed-for-prometheus/).


Work performed for a global financial instituition under guidance of [Nauman Noor](https://www.pcas.ai/), in collaboration with [Dylan Alibay](https://www.linkedin.com/in/dylan-alibay/). Illustrative diagram does not include any company-specific information or details.