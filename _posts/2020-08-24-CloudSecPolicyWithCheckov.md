---
layout: article 
title: Checkov - A Cloud Resource Security Scanner
tags: aws azure arm gcp cloudsec
aside:
  toc: true
license: false
show_subscribe: false
show_author_profile: true
---

The opensource project called [Checkov](https://www.checkov.io) developed and released by [Bridgecrew](https://bridgecrew.io/about/) has interesting approach to auditing and fixing common cloud misconfigurations. Checkov is a component of the [Bridgecrew.io platform](https://docs.bridgecrew.io/docs).

Interesting aspects of checkov:

- Checkov policies are expressed as Python files
- Checkov runs static code analysis on Terraform files

## Policies Expressed as Python files

Since we can express policies as python files, that makes it easier for us to implement more complicated logic checks. Scenarios such as IP Rule checks might become possible.

### Advanced Network Configuration Checks

One possible advanced configuration check that Checkov could allow us to do would be to query Firewall/Network ACLs applied on PaaS/SaaS resources to validate the networks are approved allow-listed IP's, etc. How do we update network firewall rules though without making the rules in Checkov out-to-date? We'd need the new allowed source-ips to be published so we could put those into a location our policies could query against.

Performance considerations: Since checkov is designed to run as a SAST agains the cloud infra provisioning files, the policies should be designed with low-latency and minimal to no external dependencies if possible. However, we might explore REST API calls or fetching new network rules from a cache manager to make its checks fast and up-to-date.

## Run Static Analysis on Terraform files

Since checkov works by running static analysis on codified infra files, we can write one policy that can be used to check for miscofigurations in the deployment pipeline if using a gitops ci/cd model for infrastructure.

- [Integrate Checkov with Github Actions](https://www.checkov.io/4.Integrations/github-actions.html)
- [Integrate with pre-commit hook on local git repo](https://www.checkov.io/4.Integrations/pre-commit.html)

## Run Scans on Cloud Platform Resources

In the case that a user goes around the pipeline deployment, we will need to scrape the resource details from the cloud resource manager and import the details into a template static format that we can analyze using the same checkov policy. If we can do this, we achieve consistent policy checks against the Infra-as-Code files and the Cloud Platform's Runtime. Checkov project itself doesn't support this, but the checkov project does have policies that work against ARM templates and it seems that Bridgecrew platform could support doing the API calls to the Azure Resource Manager (ARM) APIs to run the scans against the ARM templates it pulls for a resource.

- https://www.checkov.io/3.Scans/resource-scans.html#resource-scans-auto-generated

NOTE: ARM templates do not always support all of the properties of some Azure Resources, so I don't know how reliable this will be.  It may be similar to the challenge of using Azure Policy which is limited to only the policy aliases that are provided to Azure Policy by the individual Azure resource providers.

## Checkov Docs References

- [Checkov Documentation](https://www.checkov.io/documentation.html)
