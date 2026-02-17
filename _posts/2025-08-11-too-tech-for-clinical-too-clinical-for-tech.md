---
title: "Too Tech for Clinical, Too Clinical for Tech"
permalink: /too-tech-for-clinical-too-clinical-for-tech/
excerpt_separator: "<!--more-->"
categories:
  - Modernization in Pharma & Clinical Data
# tags:

layout: single
# classes: wide

header:
  teaser: /assets/images/vennDiagram.png
---

<div class="notice--info">
  This article examines the challenges of working at the intersection of highly regulated clinical research and fast-moving modern technology. It explores why innovation is slow, the realities of vendor lock-in, and why a small group of "bridge builders" is essential for meaningful progress.
</div>

---

<img src="/assets/images/vennDiagram.png" alt="vennDiagram" class="center-image" />

<p align="center">Image created by the author</p>

I work at the intersection of clinical research and modern engineering. One side is governed by regulation and caution, and the other by cloud platforms, automation, and an expectation of rapid iteration.

Somehow, I'm *too tech for clinical* and *too clinical for tech*. And it's… a little like being bilingual in two dialects that don't think they need translators.

## The Clinical Side: "We Could Innovate… But Why Rush?"
The clinical research world isn't opposed to innovation, but it's heavily optimized for stability and compliance. Change is slow because:  
- Every new system must be validated.  
- Every process must meet regulatory expectations.  
- The stakes aren't just uptime and user retention; they're patient safety and data integrity.  

These are valid reasons, but they also mean that a lot of innovation falls into the "maybe someday" pile. If your system still works and still passes audits, the incentive to replace it is very low.

## The Tech Side: "We Can Totally Rebuild This By Friday"
Modern engineers can design platforms in days that would take years to approve in clinical research. They see slow-moving processes and think, *"This just needs better tooling."*

Except… it's not just tooling. It's also regulation, legacy interoperability, domain-specific standards, and workflows designed to satisfy auditors and sponsors — not just end users.

When a tech team looks at clinical systems, they often underestimate:  
- The constraints that are non-negotiable.  
- The rules that can't be "optimized away."  
- The hidden complexity that's invisible until you try to change it.  


## Why the Gray Area Matters
Working in this gray area means understanding two very different sets of priorities and being able to explain them to each other without either side glazing over.

It's about:  
- Translating *"this is how it's always been done"* into *"here's how it could work better — without breaking the rules."*  
- Showing fast-moving engineers that not all obstacles are "technical debt" — some are guardrails that exist for a reason.  
- Finding solutions that feel like progress to both sides, even if they define progress differently.  

> *The bridge does more than connect two sides. It keeps progress alive.* ∞  

The bridge is the only thing that keeps them moving forward.

## The Part No One Talks About

<img src="/assets/images/void.png" alt="void" class="center-image" />

<p align="center">Image created by the author</p>

Here's the point: being in the middle feels like speaking into the void.  

The clinical side has the power to change but not the will — their incentives are tied to compliance, not transformation. The engineering side has the skills to change things but often lacks the incentive, since the complexity is messy, the regulations restrictive, and the work far removed from their usual domain.

That leaves a very small group of people — people like me — who *both* understand the potential and care enough to try.  

It's a strange kind of isolation. You can see the path forward, but most of the audience you're trying to reach is either uninterested, overwhelmed, or incentivized to keep things exactly as they are.  

> *If you don't try to bridge the gap, nothing changes at all.*

## Why We Keep Choosing Pain Over Progress
Here’s the uncomfortable truth: most of the technical problems we struggle with on the clinical side of life sciences are not new. Teams managing clinical data face the same baseline challenges as any modern data organization. They need automated ingestion, data warehousing, metadata management, workflow orchestration, and reliable audit trails. Modern engineering solved these problems years ago.

In many cases, proven solutions already exist. Open-source and cloud-native tools already power industries that operate at far greater scale than clinical research. These systems run securely, handle complex workflows, and support strict audit requirements. They are maintainable. They are battle-tested. The engineering patterns behind them are well understood.

And yet we rarely adopt them.

The constraint isn’t capability. It’s incentives.

The vendor ecosystem around regulated healthcare optimizes first and foremost for passing audits. Compliance is essential, and no one disputes that. But compliance alone is not modern engineering discipline. A system can meet regulatory requirements and still remain architecturally fragile, difficult to integrate, and inefficient for users.

These systems persist because organizations treat them as safe choices inside a risk-averse culture:
- They already satisfy compliance checklists.  
- Leaders view replacement as regulatory risk.  
- Organizations reward stability more than improvement.  

So organizations tolerate clunky interfaces, rigid workflows, and integration barriers that almost any other industry would reject.

> *We pay enormous sums for industry-specific platforms only to discover that meaningful customization costs so much it might as well not exist.*

I’ve written before about how enterprise software can become an operating constraint rather than a tool (see: [When Enterprise Software Becomes an Operating Constraint](https://mlogan914.github.io/when-enterprise-software-becomes-an-operating-constraint/)). Clinical systems follow the same pattern.

Vendor lock-in seals the loop. Once an ecosystem forms around a tool, leaving becomes harder than enduring it. I’ve seen systems violate basic security principles that most industries treat as non-negotiable. One database platform defaulted every new role to maximum privileges and offered no administrative override. The official workaround required users to manually downgrade their own access every time they logged in.

This is not a minor inconvenience. It is a structural weakness.

It creates privilege creep, weakens audit integrity, and shifts access control from system design to human behavior. In most environments, teams would classify this as unacceptable risk. In regulated software, organizations often normalize it because the vendor is entrenched and the perceived cost of switching is too high.

Instead of getting the flexible, industry-specific platform we paid for, organizations end up paying extra for workarounds just to make the system usable.

The safer path forward may not be to reinvent everything from scratch. It may be to adapt proven modern systems that other industries already use at scale, and apply the same validation rigor we expect from any clinical technology.

Until that happens, organizations choose familiarity over improvement.

That choice carries a cost. It may not always appear in revenue or patient safety metrics, but it shows up in the daily friction faced by the people trying to do the work.

## The Real Challenge and Opportunity
This gray area is frustrating, but it is also where meaningful change happens. Progress comes from small, deliberate shifts that teams can adopt without destabilizing their work.

In this space, teams can:
- Simplify systems without stripping away necessary rigor.  
- Introduce improvements that feel safe to adopt.  
- Build trust so larger changes become possible over time.  

The goal is not speed but precision. It is about choosing the right improvements, earning buy-in, and maintaining security and compliance while the system evolves.

If you work in this space, you understand the tension. You also know that people who can bridge clinical operations and modern engineering remain rare and necessary.

> *That is what being too tech for clinical and too clinical for tech means.*

If you want to stay connected, feel free to [connect with me on LinkedIn](https://www.linkedin.com/in/mlogan914/). I enjoy talking with others who think about the future of clinical data and systems design.

---

> **Disclaimer:** This article reflects my personal views only and is for informational purposes. It does not represent professional advice or the positions of any past or current employer. No confidential or proprietary information is shared, and I disclaim all liability for how you use its content. Third-party links or tool mentions are not endorsements.