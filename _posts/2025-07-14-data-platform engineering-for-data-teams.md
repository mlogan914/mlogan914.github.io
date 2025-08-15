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


💡 **Example** 
Imagine your organization uses **Snowflake** as its central data warehouse.  

<img src="/assets/diagrams/pipeline_example.png" alt="pipeline example" class="center-image" />
 <p align="center">Example ETL pipeline using Snowflake and dbt (data build tool) </p>

**STEP 1**. A data manager exports cleaned EDC data and loads it into the **RAW** schema in Snowflake - This can be manual or batch automated.

**STEP 2**. That load event **automatically** triggers a dbt (data build tool) pipeline that applies SDTM and ADaM transformations.  

**STEP 3**. Once the transformations pass **automated** compliance checks, the outputs are written to a **PROD** schema in Snowflake.  

From there, authorized teams can connect directly to the PROD datasets:  
- **Statisticians** run analyses without waiting for manual dataset deliveries.  
- **Medical monitors** can view custom dashboards showing patient progress, safety metrics, and study KPIs.  
- **Other stakeholders** can access the same trusted, validated data for their own tools and reporting needs.  

In this model:  
- **Data engineering** builds the automated flow from RAW → dbt → PROD, plus the connections to analytics tools + dashboards.

---

## What is platform engineering?
<img src="/assets/images/platform_engineering.png" alt="platform engineering" class="center-image" />

<p align="center">Image created by the author</p>

> *"In a platform engineering approach, one or more teams—often referred to as the platform engineering team or the platform team—build a comprehensive set of shared tools and services (aka “the platform”) to help development teams develop, deploy, and operate cloud infrastructure on a self-service basis. This includes cloud infrastructure, container orchestration platforms, databases, networking, monitoring, code repositories, and deployment pipelines."* — Pulumi

Instead of building a study-specific ETL flow from scratch every time, platform engineering provides the **foundation**:  
- Standardized, compliant environments for development and execution  
- Orchestrated workflows that connect ingestion, transformation, and delivery  
- Automated testing so changes are safe and repeatable  
- Centralized logging, monitoring, and audit trails for transparency  

💡 **Example**: The platform team manages the infrastructure that makes the work possible — IaC templates to provision RAW, DEV, and PROD schemas in Snowflake, standardized access controls, logging, monitoring, and compliance settings.

### How this changes the statistical programmer’s role

In a traditional setup, statistical programmers often write study-specific SAS programs to transform raw EDC data into SDTM, building much of the process from scratch each time.  

In a platform-enabled pipeline, SDTM creation is no longer a one-off SAS exercise. Instead, the domain-specific transformation logic lives in **maintainable, version-controlled models** (e.g., dbt models) that programmers refine and reuse across studies.  

The shift looks like this:  
- **Before**: Procedural programming in SAS to generate SDTM datasets for each study.  
- **Now**: Maintaining and improving standardized transformation models that automatically produce SDTM datasets when new data lands — while still applying deep clinical data expertise to ensure accuracy and compliance.  

SAS may still be used, especially for regulatory deliverables or when required by sponsors, but the focus moves upstream. Programmers spend more time ensuring the transformation layer is correct and less time reinventing the wheel for each study.  

TFL (Tables, Figures, Listings) creation remains a core deliverable, so statistical programmers continue to work closely with biostatistics — now with more reliable, reusable SDTM inputs feeding their analysis work.  

Think of it like this:  
- **Data engineering** defines *what* to move and transform.  
- **Platform engineering** defines *how* it gets done — providing the operating model and **blueprints** to make it consistent, compliant, and scalable across studies.  

> **Note:** A “platform” here isn’t a single system to buy or install. It’s a deliberate way of working — an internal, self-service workflow.  
>
> For example, when starting a new study, a statistical programmer might request a Snowflake pipeline environment setup (RAW, DEV, PROD) so the data manager can begin loading data from the EDC into RAW. This would be deployed using the IaC managed by the platform team.

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

## Why now?

Platform engineering is still taking shape — even in mainstream software.  

For data teams in regulated industries, it’s almost uncharted territory.

That’s exactly why the timing matters.  

If we keep designing systems to match how things were done yesterday, we’ll never be ready for tomorrow — whether that’s real-time submissions, AI-assisted compliance, or simply giving teams tools that remove the busywork and let them focus on higher-value work.

---

## Closing thought  

While platform engineering varies by industry, platform thinking shifts the focus from delivering a single project to building the capability to deliver any project well.  

If you’ve ever thought, “There has to be a better way” — you’re probably right. The first step might be to start thinking like a platform engineer.

---

💬 If you're enjoying the ideas here and want to stay connected, feel free to [connect with me on LinkedIn](https://www.linkedin.com/in/mlogan914/). I’d love to stay in touch with others thinking about the future of clinical data and systems design.

> **Disclaimer:** This article reflects my personal views only and is for informational purposes. It does not represent professional advice or the positions of any past or current employer. No confidential or proprietary information is shared, and I disclaim all liability for how you use its content. Third-party links or tool mentions are not endorsements.

## Glossary of Acronyms
<script src="https://gist.github.com/mlogan914/f81e616779a5cde4d46644dce24393ae.js"></script>