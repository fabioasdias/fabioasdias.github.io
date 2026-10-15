---
title: Service enablement and multi-region IaC
publishDate: 2019-09-01 00:00:00
img: /assets/enablement.png
img_alt: Diagram showing an AWS service request going through study and guardrails, an enablement checklist, reusable CloudFormation templates and StackSets to 13 regions, with regional values coming from a configuration database
description: |
  Golden paths, guardrails and one set of templates for 13 regions
tags:
  - AWS
  - Platform engineering
  - Infrastructure as code
---

For each AWS service a team wanted, the platform team studied the service and its use cases, established a golden path and set guardrails before enabling it. A checklist governed enablement: the service itself, authentication and authorization, logging, monitoring, chargeback, compliance and integration with other resources.

Reusable CloudFormation templates covered RDS, EC2 with Auto Scaling Groups and unusual services such as Neptune. One fully featured template ran ECS over EC2, and a second ran services and jobs on top of it. Templates shipped with IAM role and resource-policy templates, and with secret rotation hooked up automatically.

In the multi-tenant environment, every application had "environments", and the application itself was multi-tenant and needed isolation. Resources were tagged and named by convention, and policies used those conventions to allow only the minimum set of actions over the right resources. No AWS-managed policies were used because they were too broad. Whether a policy matched on tags or names depended on the resource, since AWS is not uniform: some services support tags, others require names, and Neptune used a custom managed policy kept up to date by a custom resource. Deployment roles followed the same logic, and everything was templated.

The same CloudFormation files brought up resources in 13 regions. Everything that varied by region came from a request to a configuration database, delivered into the templates through custom resources, so the template code stayed clean. The same service discovery layer also let services find other services.

Deployment ran through StackSets and an automated pipeline. When I joined, everything was manual and the pipeline existed only for customer workloads; I drove the standardization and onboarding of the platform's own infrastructure onto it.

Work performed for a global financial institution. Illustrative diagram does not include any company-specific information or details.
