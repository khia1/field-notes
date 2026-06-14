---
title: "Cloud Security's Hidden Contract: What 'Shared Responsibility' Actually Means"
date: 2026-06-14
categories: [Cloud Security]
tags: [cloud security, shared responsibility model, AWS, Azure, IaaS, SaaS, zero trust, defense in depth, identity and access management]
description: "Most cloud breaches don't come from the provider's infrastructure — they come from customers misunderstanding which parts of the security stack are still theirs. A look at how the shared responsibility model actually divides the line, and why the dividing line moves depending on the service tier."
---

# Cloud Security's Hidden Contract: What "Shared Responsibility" Actually Means

One of the most persistent misconceptions in cloud security is the idea that moving to the cloud means handing security off to someone else. Sign with AWS, Azure, or Google, and the provider's security team takes it from there — or so the thinking goes. In practice, this assumption is responsible for a large share of cloud breaches, and almost all of them trace back to the same root cause: a misconfigured storage bucket, an overly permissive identity policy, or an unpatched application layer that the customer — not the provider — was responsible for.

## Security doesn't transfer, it splits

When an organization moves a workload to the cloud, security isn't outsourced — it's divided along a line that depends entirely on the service model being used. The provider secures the parts of the stack it controls (physical data centers, hypervisors, network backbone), and the customer secures the parts they control (data, identity, configuration, and sometimes the operating system and applications themselves). The dividing line moves depending on whether you're consuming Infrastructure as a Service, Platform as a Service, or Software as a Service.

This is worth sitting with for a moment, because the practical difference is enormous:

- **IaaS** (e.g., a virtual machine in EC2 or Azure VMs) puts almost everything above the hypervisor in the customer's hands — OS patching, network configuration, firewall rules, application security, and data protection are all the customer's responsibility.
- **SaaS** (e.g., Salesforce, Microsoft 365) shifts nearly all of that to the provider. The customer's responsibility narrows dramatically — but it doesn't disappear. Identity and access management, data classification, and how the application is configured remain squarely on the customer's side of the line.

The danger isn't in either extreme — it's in the assumption that "cloud" means "less responsibility" across the board, when in reality it means "different responsibility," and the specifics change with every service tier.

## Why this keeps causing incidents

Most high-profile cloud breaches aren't the result of a provider's infrastructure being compromised. They're the result of the customer-side responsibilities being misunderstood or simply not staffed for. A team that moves from on-prem servers to IaaS often carries over the assumption that "the cloud team handles security now" — without realizing that patching, access control, and network segmentation are still entirely on them. The provider secured the building; nobody secured the door.

This is also where foundational security thinking earns its keep. Defense in depth — layering controls so that no single failure is catastrophic — and zero trust — verifying every request regardless of where it originates — aren't abstract principles. They're the practical answer to "given that I'm responsible for this layer, how do I make sure one mistake doesn't become a breach?"

## What this means in practice

For teams evaluating or operating in the cloud, a few questions are worth asking for every service in use:

1. **Where does the provider's responsibility end, and ours begin?** This should be explicit, not assumed — most providers publish a shared responsibility breakdown per service.
2. **Who owns identity and access management?** Across almost every service model, this stays with the customer — and it's one of the most common sources of breaches.
3. **What's our visibility into the layers we don't control?** Even when a provider manages a layer, understanding
