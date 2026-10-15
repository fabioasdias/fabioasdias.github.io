---
title: Deployment tool
publishDate: 2019-11-01 00:00:00
img: /assets/autodeploy.png
img_alt: Flow diagram of a deployment tool that reads one configuration file, runs a simulation mode with several checks, applies sanity checks, deploys with CloudFormation, then runs smoke tests and cleanup
description: |
  From ~15-step runbooks to a single command
tags:
  - AWS
  - Platform engineering
  - Developer experience
---

When I joined the platform team, deployments followed runbooks. Each one was different, they averaged about 15 steps, some included hand-edited files, and the deployment queue ran to months.

By November 2019 I had written a Python tool, end to end, that takes one configuration file and runs the operations, turning a runbook into "run the tool". Its YAML parser uses a custom syntax that declares the dev, UAT and prod values in a single file and selects them per environment. The interface is `git checkout <branch> && autodeploy`.

A simulation mode, much like a Terraform plan, shows the resolved runtime values, including mocked custom-resource calls, AWS resource evaluation and CloudFormation syntax checks. It caught many problems before they became problems.

Sanity checks block deployments likely to cause trouble. For example, a configuration tool owned by the team tied IAM roles to resources, and creating a resource without a role failed. The deployment tool refused deployments where that association was missing, so the gap was caught up front instead of through an outage.

After a deployment, the tool runs smoke tests and cleanup specific to each application type. For an RDS offering, it creates a real instance, exercises the feature, then deletes the instance and its test resources. Time to deploy was the time AWS took to run plus a few minutes.

The tool was adopted in January 2020 and was a bridge: by the end of 2020 or early 2021, deployments moved onto the proper pipeline, a custom Jenkins setup owned by another team. I drove the standardization and onboarding of the platform's own infrastructure onto it. From early 2021, platform changes reached production with double-digit deployments on Mondays and about ten a day from Tuesday to Thursday, and none on Fridays to protect the weekend.

Work performed for a global financial institution. Illustrative diagram does not include any company-specific information or details.
