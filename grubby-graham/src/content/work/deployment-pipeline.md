---
title: Automate, automate, automate
publishDate: 2019-11-01 00:00:00
img: /assets/deployment-speed.png
img_alt: Illustrative chart of deployment frequency rising over three stretches, manual runbooks, a deployment tool and a pipeline, with the markers stacking into parallel rows in the last stretch
description: |
  From manual runbooks to a deployment pipeline
tags:
  - AWS
  - Platform engineering
  - CI/CD
---

Platform deployments started as manual runbooks, with a deployment queue measured in months.

I wrote a deployment tool in Python covering the most common deployment operations, with a simulation mode and safety checks to catch problems early. It was in use by January 2020.

Working with the pipeline team, I then moved platform deployments onto a CI/CD pipeline. By early 2021 the move was done, and deployments kept getting faster, reaching double-digit production deployments a day.

Work performed for a global financial institution. Illustrative chart, not real data.
