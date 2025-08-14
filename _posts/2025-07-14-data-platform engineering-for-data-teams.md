---
title: "From Pipelines to Platforms: Modern Engineering for Regulated Data Teams"
excerpt_separator: "<!--more-->"
categories:
  - Data Engineering
  - Platform Engineering
tags:
  - data-engineering
  - platform-engineering
  - systems-thinking

---

<div class="notice--info">
    Many regulated data teams still work without true pipelines, relying on manual, study-by-study transformations. Learn how combining data engineering with platform engineering can create scalable, compliant, and reusable workflows across studies and indications.
</div>

<img src="/assets/images/data_platform.png" alt="data platform" class="center-image" />

<p align="center">Image created by the author</p>

---
If you work in a regulated data environment — pharma, med devices, clinical research — chances are you’ve heard a version of this sentence:

> “That’s just how it’s always been done.”

In practice, that often means:  
- Data ingestion, transformation, and delivery handled separately by different teams using different tools — with no central data warehouse or shared infrastructure  
- Manual handoffs between roles that slow delivery and increase risk  
- Compliance checks treated as a separate, end-of-process chore instead of something built into the workflow  

Automation has helped in some areas, but the underlying patterns haven’t changed. Teams are still solving the same problems repeatedly, often in isolation and with little code reuse or standardization. When code is reused, it’s often copied manually from one study to the next.

The real challenge isn’t just outdated tools — it’s the lack of shared systems, orchestration, and standardized processes that can make data ingestion, transformation, and delivery scalable, compliant, and repeatable across studies and therapeutic areas.

That’s where **data engineering** meets **platform engineering**.

---

## What is data engineering?

<img src="/assets/images/data_engineering.png" alt="data engineering" class="center-image" />

<p align="center">Image created by the author</p>

In most industries, **data engineering** is about building orchestrated, automated pipelines that handle the full flow of data — **Extract, Transform, Load (ETL)**. These pipelines ingest data from source systems, transform it into the required structure and format, and deliver it to its end users. Those end users might be data analysts, business stakeholders, or, in pharma, biostatisticians, medical monitors, and other study team members.  

Well-designed pipelines are **reusable, testable, and maintainable** — not manual, study-specific processes.  

In regulated pharma, most statistical programmers — at least for SDTM and ADaM — work only on the **Transform** step of ETL, writing highly manual, study-by-study code that’s rarely reused. The **Extract** (ingestion) and **Load** (delivery) steps are typically handled by data management teams through ad-hoc methods like sFTP transfers or study-specific scripts, with delivery treated as a manual handoff to downstream consumers or regulators, without an automated process to move data through consistent environments.  

In a true data engineering model, all three ETL steps — ingestion, transformation, and delivery — are connected through an orchestrated, automated pipeline. For example, an organization could maintain central data warehouses for **RAW** and **PROD** data, organized by indication, with transformation jobs producing SDTM and ADaM outputs as part of that flow.  

In most pharma organizations today, this kind of end-to-end pipeline doesn’t exist. Instead, we rebuild the transform logic for every study and rely on manual, disconnected processes for ingestion and delivery.

---

## What is platform engineering?
<img src="/assets/images/platform_engineering.png" alt="platform engineering" class="center-image" />

<p align="center">Image created by the author</p>

Platform engineering is the practice of designing and maintaining shared tools, services, and infrastructure so that teams can deliver value **reliably, securely, and at scale**. In the context of data teams, that means creating the **systems and automation** that turn one-off pipelines into **reusable, self-service workflows**.  

Instead of building a study-specific ETL flow from scratch every time, platform engineering provides the **foundation**:  
- Standardized, compliant environments for development and execution  
- Orchestrated workflows that connect ingestion, transformation, and delivery  
- Automated testing so changes are safe and repeatable  
- Centralized logging, monitoring, and audit trails for transparency  

💡 Example: If Snowflake were your data warehouse, Infrastructure as Code could provision RAW, DEV, and PROD environments from the same template — each with consistent security, access controls, and monitoring.

Think of it like this: data engineering defines *what* to move and transform; platform engineering provides the operating model and tooling to make it consistent, compliant, and scalable across studies.  

It’s not the end product — it’s the framework for how the work gets done. In regulated industries, that framework enables both governance and agility.  

> Platform engineering isn’t a single system to buy or install — it’s a deliberate way of working.

---

## How data engineering and platform engineering intersect

Data engineering and platform engineering are complementary disciplines.  
- **Data engineering** focuses on building the pipelines that ingest, transform, and deliver data so it’s ready for use.  
- **Platform engineering** focuses on creating the shared systems, automation, and infrastructure that make those pipelines scalable, compliant, and reusable across projects.  

In regulated industries, this intersection is where the real transformation happens:  
- Data engineering brings the technical capability to build end-to-end ETL flows.  
- Platform engineering ensures those flows are consistent, governed, and repeatable across studies and therapeutic areas.  

When combined, the result is an **orchestrated, self-service data platform** where ingestion, transformation, and delivery are connected into a single, automated process.  
Instead of manually rebuilding the same logic for each study, teams can focus on solving new problems — confident that the platform handles compliance, quality, and delivery.

---

## Why this matters in regulated industries

Regulated data teams are a perfect candidate for platform thinking because:  
- **Patterns repeat** — SDTM, ADaM, CDASH aren’t changing every week.  
- **Compliance is non-negotiable** — so why not bake it into the system?  
- **Audit trails** are a requirement, not a nice-to-have.  
- **Multiple teams** touch the same workflows, often with handoffs that could be automated.  

A platform approach can:
- Reduce duplicate work across studies  
- Ensure compliance checks run automatically, not just at the end  
- Let statisticians, programmers, and data managers work without waiting for engineering support every time  
- Make it easier to adapt to new standards or tech without starting from scratch  

---

## A practical example

It’s one thing to talk about data and platform engineering in theory — but what does it actually look like in practice?  

Here’s a simplified end-to-end flow using a pharma-friendly example inspired by my own **Blueprint-as-a-Service (BaaS)** project.

---

### Before vs. After

<script src="https://gist.github.com/mlogan914/23076832dcbf5cf1b4923a6749c52c3c.js"></script>

---

### Future-State Example: EDC → Warehouse → Submission-Ready Data

1. **Ingestion (Extract)**  
   - Clinical trial data is automatically pulled from the EDC at scheduled intervals.  
   - Data lands in a **central RAW data warehouse**, organized by indication and study.  

2. **Metadata-Driven Transformation (Transform)**  
   - A **metadata scaffolding service** (like the BaaS project) reads trial metadata from the RAW warehouse.  
   - It auto-generates standardized SDTM transformation templates based on controlled terminology and mapping rules.  
   - Any custom derivations or study-specific rules are injected automatically from a central library.  

3. **Continuous Compliance**  
   - As data flows through transformation jobs, automated checks run to validate SDTM compliance and internal data quality rules.  
   - Errors are flagged immediately, not weeks later.  

4. **Delivery (Load)**  
   - Finalized SDTM and ADaM datasets are written to a secure **PROD warehouse**.  
   - Access controls ensure that only authorized users (e.g., statisticians, regulators, study teams) can retrieve them.  
   - Downstream consumers — from analysis tools to submission systems — can connect directly to this trusted PROD source.  

---

### Why it works

This model replaces fragmented, study-specific processes with a **reusable, orchestrated, and governed pipeline**. 

Instead of re-coding transformations for every study and moving files manually, teams get:  

- **Faster delivery** through automation  
- **Higher quality** thanks to built-in compliance checks  
- **Better reuse** by centralizing transformation logic and metadata  
- **Greater transparency** with shared, version-controlled workflows  

---

Here’s how that future-state model could look in practice.

*Diagram placeholder:*  
```
DETAILED FLOW (EDC → RAW → BaaS → SDTM/ADaM → PROD → Consumers)

            ┌──────────────────────┐
            │  EDC (source system) │
            └──────────┬───────────┘
                       │ 1) Scheduled extract (API/flat files)
                       │
               ┌───────▼────────────────────────────────────────────┐
               │           RAW DATA WAREHOUSE (secure)              │
               │  • Organized by therapeutic area / study           │
               │  • Immutable, auditable landing zone               │
               └───────┬────────────────────────────────────────────┘
                       │ 2) Ingestion complete → event/cron triggers pipeline
                       │
        ┌──────────────▼────────────────┐
        │   METADATA SCAFFOLDING (BaaS) │
        │   • Read ODM/CDISC metadata   │
        │   • Generate dbt/Jinja models │
        │   • Inject standard derivs    │
        └──────────────┬────────────────┘
                       │ 3) Orchestrated transform jobs (ETL-T)
                       │
     ┌─────────────────▼───────────────────┐
     │ TRANSFORMATION & VALIDATION LAYER   │
     │ • Run SDTM mappings (dbt/SQL)       │
     │ • Apply custom overrides            │
     │ • Continuous compliance checks:     │
     │   - SDTM IG rules                   │
     │   - Terminology checks              │
     │   - Data quality tests              │
     └─────────────────┬───────────────────┘
                       │ 4) Publish validated outputs
                       │
            ┌──────────▼───────────┐
            │   PROD DATA WAREHOUSE│
            │   • SDTM / ADaM      │
            │   • Versioned, ACLs  │
            └──────────┬───────────┘
                       │ 5) Role-based access (RBAC)
                       │
  ┌──────────────┬─────▼────────┬───────────────┬───────────────┐
  │ Statisticians│ Med Monitors │ Submissions   │ BI/Analytics  │
  │ (analysis)   │ (review)     │ (regulatory)  │ (dashboards)  │
  └──────────────┴──────────────┴───────────────┴───────────────┘
```

Notes:
- Orchestration (Airflow, Dagster, etc.) coordinates steps 2–4.
- Logging/monitoring trace each run for auditability.
- Same framework reused across studies; only metadata/configs change.

---

## Why now?

Platform engineering is still taking shape — even in mainstream software.  
For data teams in regulated industries, it’s almost uncharted territory.

That’s exactly why the timing matters.  
If we keep designing systems to match how things were done yesterday, we’ll never be ready for tomorrow — whether that’s real-time submissions, AI-assisted compliance, or simply giving teams tools that remove the busywork and let them focus on higher-value work.

---

## Closing thought  

Platform engineering shifts your focus from delivering a single project to building the capability to deliver any project well. If you’ve ever thought, “There has to be a better way,” you’re probably right — and the first step might be thinking like a platform engineer.

---

💬 If you're enjoying the ideas here and want to stay connected, feel free to [connect with me on LinkedIn](https://www.linkedin.com/in/mlogan914/). I’d love to stay in touch with others thinking about the future of clinical data and systems design.

> **Disclaimer:** This article reflects my personal views only and is for informational purposes. It does not represent professional advice or the positions of any past or current employer. No confidential or proprietary information is shared, and I disclaim all liability for how you use its content. Third-party links or tool mentions are not endorsements.

## Glossary of Acronyms
<script src="https://gist.github.com/mlogan914/f81e616779a5cde4d46644dce24393ae.js"></script>