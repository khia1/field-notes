---
title: "'Secure by Design' Needs a Definition — ISO/IEC 19249 Provides One"
date: 2026-06-14
categories: [Security Architecture & Design]
tags: [secure by design, ISO/IEC 19249, security architecture, least privilege, attack surface, common criteria, threat modeling, domain separation]
description: "'Secure by design' is a phrase that shows up everywhere and gets defined almost nowhere. ISO/IEC 19249 turns it into an actual checklist — splitting security into how a system is structured and how each component behaves, with principles like least privilege, domain separation, and attack surface minimization."
---

# "Secure by Design" Needs a Definition — ISO/IEC 19249 Provides One

"Secure by design" is one of those phrases that shows up in every security pitch deck and almost never gets defined. It sounds like a principle, but on its own it's closer to a slogan — a goal without a method. ISO/IEC 19249 is one of the more practical attempts to close that gap. Rather than telling teams *what* to secure, it gives a structured vocabulary for *how* security gets built into a system's architecture and the behavior of its individual components.

## Two layers of thinking, not one

The standard splits its guidance into two categories that map onto two different design questions:

**Architectural principles** answer "how is the system structured?" They're about how components relate to each other — what's grouped together, what's isolated, what depends on what.

**Design principles** answer "how does each component behave?" They're about the internal logic of individual parts — how they validate input, what permissions they assume, how they fail.

The distinction matters because these failures show up at different stages. A flawed architecture is expensive to fix after the fact — it usually means redrawing system boundaries. A flawed component behavior is often fixable in isolation. Knowing which category a given weakness falls into changes how urgently — and how disruptively — it needs to be addressed.

## On the architecture side

A few of the architectural principles are worth calling out because they show up constantly in real incident postmortems, even when nobody names them explicitly:

**Domain separation** — grouping components that share the same trust level and access requirements, and forcing any communication between domains through well-defined, mediated channels. This is the underlying logic behind network segmentation, but it applies just as well to how a single application separates its admin functions from its user-facing functions.

**Layering** — structuring a system so that lower layers don't depend on the security of higher layers. A database shouldn't assume the application layer has already filtered malicious input; it should be able to defend itself independently.

**Redundancy** — not just for availability, but for security controls themselves. If a single control (say, input validation) fails, is there a second control behind it, or does failure cascade straight through?

## On the design side

The component-level principles tend to read as common sense individually, but the value is in treating them as a checklist rather than isolated good habits:

**Least privilege** — components, processes, and users should operate with the minimum access needed, nothing more. This is the principle most often violated not through bad intent, but through convenience during initial setup that never gets revisited.

**Attack surface minimization** — every exposed interface, open port, or enabled feature is something that has to be defended. Reducing what's exposed is often more effective than adding controls around what's already exposed.

**Centralized validation and centralized security services** — input validation and security functions (authentication, logging, cryptography) implemented once, centrally, and reused — rather than reimplemented inconsistently across every component that needs them.

**Preparing for error and exception handling** — designing for what happens when something *does* go wrong, rather than assuming it won't. Many real-world vulnerabilities live in exception paths precisely because they're the least-tested part of a system.

## Why this is more than academic

ISO/IEC 19249 was written with security evaluation in mind — it connects to Common Criteria (ISO/IEC 15408), which is used for formal product certification. But its real value for most teams isn't certification; it's vocabulary. "We need to be more secure" is not an actionable design review comment. "Does this component assume the layer below it is trustworthy?" or "What's the blast radius if this domain is compromised?" are.

Used this way, the standard isn't a compliance artifact to file away — it's a set of questions that turn a vague architecture review into a structured one.
