---
layout: article 
title: Notes on k8s Network Security
tags: k8s kubernetes calico netsec aks gke cloudsec
aside:
  toc: true
license: false
show_subscribe: false
show_author_profile: true
---

Article Outline:

- TODO: Draft notes on how k8s network policy does help handle multi-tenancy in clusters
- TODO: Draft notes and diagram on how there may still be network security challenges when isolated workloads on a cluster need to have layer3/4 ip rules when egressing large clusters.
-- Diagram of k8s network ingress/egress with a traditional Network FW/IDS/IPS like device providing ingress/egress rules.

## References

- [Kevin Sookocheff's article on Understanding Kubernetes Network Model](https://sookocheff.com/post/kubernetes/understanding-kubernetes-networking-model/)
- [GKE Network Policy Docs](https://cloud.google.com/kubernetes-engine/docs/how-to/network-policy)
