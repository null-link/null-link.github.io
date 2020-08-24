---
layout: article 
title: GCP VPC Security Concepts
tags: gcp cloudsec vpc iam network netsec dns
aside:
  toc: true
license: false
show_subscribe: false
show_author_profile: true
---

GCP VPC Key Concepts explained here:

Private Google Access is a feature that allows VM's, that only have private network access, to access Google Services/APIs via Private Google Access (instead of egressing to public Internet).

## VPC Service Controls

[How to Setup Private Connectivity](https://cloud.google.com/vpc-service-controls/docs/set-up-private-connectivity) and [VPC - Private Access Options](https://cloud.google.com/vpc/docs/private-access-options) documentation will help you understand the difference between the private.googleapis.com and restricted.googleapis.com DNS names that are used for Private Access.  The restricted.googleapis.com should be used for services that need to be restricted to VPC Service Controls perimeter too.


//TODO: elaborate on network topology for when using private access w/o VPC Service Controls

//TODO: elaborate on data leak challenges and prevention measures when using the private access options

//TODO: elaborate on network topology for when using VPC Service Controls and Private Access to address the Data Leak concerns of egress access.

Access Control Manager (ACM) is used to define access context that is applied to VPC Service Perimeter which are defined for the VPC Service Controls.

//TODO: elaborate on ACM.

## Google Docs Refrences

* [VPC - Setting up Private Connectivity](https://cloud.google.com/vpc-service-controls/docs/set-up-private-connectivity)
* [VPC - Private Access Options](https://cloud.google.com/vpc/docs/private-access-options)
* [VPC - Private Google Access with VPC Service Controls Perimeter](https://cloud.google.com/vpc-service-controls/docs/private-connectivity)
* [VPC - Service Controls](https://cloud.google.com/vpc-service-controls/docs)

## Other References

* [ScaleSec article on Protecting GCP Services with VPC Service Controls and Terraform](https://blog.scalesec.com/protecting-gcp-services-with-vpc-service-controls-and-terraform-858019d8b4ff)
* [BeyondCorp Approach to Perimeter Security](https://www.beyondcorp.com/)
