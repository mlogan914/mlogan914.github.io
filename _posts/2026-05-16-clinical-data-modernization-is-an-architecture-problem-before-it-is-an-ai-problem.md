---
title: "Clinical Data Modernization Is an Architecture Problem Before It Is an AI Problem"
permalink: /clinical-data-modernization-is-an-architecture-problem-before-it-is-an-ai-problem/
excerpt_separator: "<!--more-->"
categories:
  - Modernization in Pharma & Clinical Data
# tags:
#   - 

layout: single
# classes: wide

header:
  teaser: /assets/images/clinical-data-modernization-is-an-architecture-problem2.png
  og_image: /assets/images/clinical-data-modernization-is-an-architecture-problem2.png
image: /assets/images/clinical-data-modernization-is-an-architecture-problem2.png
---

<div class="notice--info">
This article explains why I believe clinical data modernization is currently more constrained by workflow architecture, reuse, and operational design than by a lack of AI capability, and how that thinking influenced the direction of my metadata-driven SDTM Blueprint-as-a-Service project.
</div>

<img src="/assets/images/clinical-data-modernization-is-an-architecture-problem2.png" alt="clinical data modernization is an architecture problem"/>

<p align="center">Image created by the author</p>

"Move fast and break things" was a common philosophy during earlier eras of software development. Over time, many engineering organizations moved away from that mindset because repeatedly rebuilding large systems quickly without strong architectural foundations created significant maintenance burden, operational overhead, and technical debt.

In many ways, parts of clinical data workflows still resemble earlier software engineering eras.

Clinical programming workflows often remain highly repetitive, heavily manual, and rebuilt repeatedly in slightly different ways across studies. Even when studies share similar structural concepts, large portions of the implementation are frequently recreated from scratch. Over time, this creates operational inconsistency, validation burden, and technical debt that becomes increasingly difficult to scale.

This becomes especially important in regulated environments where traceability, repeatability, and reviewability are critical.

For that reason, I do not think the primary bottleneck in clinical data modernization is currently a lack of AI capability.

Adding additional layers of automation or AI on top of inefficient workflow architecture risks increasing long-term technical debt.

To me, the larger challenge is *operational design*.

This thought process has heavily influenced the direction of my [SDTM Blueprint-as-a-Service project](https://github.com/mlogan914/sdtm-blueprint-as-a-service). The project explores how metadata-driven architecture and reusable workflow structures can reduce repetitive structural work while preserving the study-specific logic and interpretation required for clinical programming.

In this architecture, derivations and transformation logic are contributed into standardized workflow structures instead of repeatedly rebuilding large study-specific programs from scratch for every study.

Conceptually, the architecture separates:
- Structural workflow generation
- Metadata interpretation and normalization
- Derivation injection points
- Workflow validation checkpoints
- Study-specific transformation logic

The goal is to reduce the amount of repetitive infrastructure work surrounding the programming itself.

In many software domains, abstraction layers evolved because repeatedly rebuilding the same structural patterns became operationally inefficient. Frameworks, reusable modules, infrastructure-as-code, CI/CD pipelines, and platform engineering practices emerged to standardize workflow structure while allowing teams to focus on the logic unique to their problem space.

I believe clinical data workflows are beginning to face many of the same pressures.

AI may eventually assist many parts of clinical programming in meaningful ways. However, sustainable automation becomes significantly more realistic when the surrounding workflow is structured, standardized, and easier to validate.

For me, that is currently the more interesting engineering problem.