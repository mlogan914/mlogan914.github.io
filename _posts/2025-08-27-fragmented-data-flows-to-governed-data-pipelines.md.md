---
title: "From Fragmented Data Flows to a Governed Data Pipelines"
excerpt_separator: "<!--more-->"
categories:
  - Data & Platform Engineering
tags:
  - data engineering
  - data-architecture
  - data-pipelines
  - operating-model
  - life-sciences
classes: wide
---

<div class="notice--info">
    Many organizations focus on fixing individual data issues but overlook the bigger picture: how data enters, moves, and is governed across the entire environment. This article shows a practical before-and-after example of moving from fragmented data flows to governed, versioned pipelines — an approach that supports scalability, trust, and repeatability without relying on tool-first thinking.
</div>

<img src="/assets/images/governed_data_pipelines.png" alt="governed data pipelines" class="center-image" />

<p align="center">Image created by the author</p>

In my previous article, [Data Platform Engineering for Regulated Teams](/data%20&%20platform%20engineering/data-platform-engineering-for-regulated-data-teams/), I outlined why modernizing data in regulated industries requires more than just swapping out tools.

This follow-up shows what that shift can look like in practice — moving from fragmented, ad-hoc flows to a governed, repeatable data pipelines.<!--more-->

---

## The core idea

Many organizations have data flowing in from multiple systems and vendors, each using their own methods to send it over. Without consistent entry points, quality checks, or structure, the result is hard to scale, hard to trust, and expensive to maintain.

A modern engineering approach changes that by:
- Defining **one “front door”** for all incoming data.
- Running **quality checks early**.
- Using **layered storage** to clearly separate raw, refined, and curated data.
- Governing **how definitions and rules are applied** so they’re consistent everywhere.

---

## Example: Current vs. Future State

Here’s a fictional example to make it concrete.

---

### Current state: fragmented and inconsistent

```mermaid
flowchart LR
  %% Sources
  subgraph SRC[Sources]
    CRM[(CRM System)]
    EHR[(Clinical App)]
    LIMS[(Lab System)]
    Sheets[(Spreadsheets – uncontrolled)]
  end

  %% Ingestion & Landing
  subgraph ING[Ingestion & Landing]
    SFTP[(SFTP Drop)]
    API[[API Pull]]
    NAS[(Shared Drive – uncontrolled)]:::problem
    Intake[(Cloud Landing Area)]
  end

  %% Processing
  subgraph PROC[Processing]
    Legacy[[Legacy Jobs]]:::problem
    Scripts[[Ad-hoc Scripts]]:::problem
  end

  %% Storage
  subgraph STORE[Storage]
    OnDW[(On-Prem DW)]:::problem
    Cloud[(Cloud DW)]
  end

  %% Flows
  CRM --> SFTP --> Intake
  EHR --> API --> Intake
  LIMS --> SFTP --> NAS
  Sheets -. ad-hoc .-> NAS

  Intake --> Scripts --> Cloud
  NAS --> Legacy --> OnDW

  %% Styling
  classDef problem stroke-dasharray:5 3,stroke:#e5484d,stroke-width:2px;
```

**Key characteristics**:
- Multiple uncontrolled entry points (SFTP, shared drives, ad-hoc files).
- Different storage environments holding overlapping data.
- Custom logic scattered across scripts that aren’t centrally managed.

---

### Future state: governed and repeatable
```mermaid
flowchart LR
  %% Sources
  subgraph SRC[Sources]
    CRM[(CRM System)]
    EHR[(Clinical App)]
    LIMS[(Lab System)]
    Sheets[(Spreadsheets – controlled intake)]
  end

  %% Ingestion
  subgraph ING[Ingestion]
    CDC[[Managed Connectors]]
    Batch[[Scheduled Batch]]
    Bronze[(Landing / Bronze – Raw)]
  end

  %% Core Environment
  subgraph CORE[Core Environment]
    DQ{{Automated Quality Checks}}
    Transforms[[Versioned Processing]]
    Silver[(Refined / Silver – Cleaned)]
    Gold[(Curated / Gold – Ready for Use)]
  end

  %% Flows
  CRM --> CDC --> Bronze
  EHR --> CDC --> Bronze
  LIMS --> Batch --> Bronze
  Sheets -. template/validation .-> Bronze

  Bronze --> DQ --> Transforms --> Silver --> Transforms --> Gold

```

**Key characteristics**:
- One governed front door for all sources.
- Automated checks ensure issues are caught before they spread.
- Layered structure (Raw → Refined → Curated) for clarity and trust.
- Repeatable processing patterns replace scattered, one-off scripts.

---

### What Changed: A Delta View
- Red (dashed) = remove/retire
- Green = add
- Blue = standardize or migrate into the governed flow

```mermaid
flowchart LR
  %% DELTA MAP: Red=retire, Green=add, Blue=standardize/migrate

  %% Sources (unchanged)
  subgraph SRC[Sources]
    CRM[(CRM)]
    EHR[(Clinical App)]
    LIMS[(Lab System)]
    Sheets[(Spreadsheets)]
  end

  %% Retire / Remove (RED)
  subgraph RET[Remove]
    NAS[(Shared Drive Intake)]:::retire
    Legacy[[Legacy Jobs / One-off Scripts]]:::retire
    OnDW[(On-Prem Warehouse as “truth”)]:::retire
  end

  %% Add (GREEN)
  subgraph ADD[Add]
    Bronze[(Landing / Bronze)]:::add
    DQ{{Early Automated Quality Checks}}:::add
    Silver[(Refined / Silver)]:::add
    Gold[(Curated / Gold)]:::add
    Semantic[[Shared Definitions]]:::add
  end

  %% Standardize / Migrate (BLUE)
  subgraph STD[Standardize / Migrate]
    CDC[[Managed Connectors / Change Feeds]]:::migrate
    Batch[[Scheduled Batch Intake]]:::migrate
    Cloud[(Primary Analytical Store)]:::migrate
  end

  %% Flows into the governed entry points
  CRM --> CDC --> Bronze
  EHR --> CDC --> Bronze
  LIMS --> Batch --> Bronze
  Sheets -. controlled templates/validation .-> Bronze

  %% Old/retiring paths (fading)
  Sheets -. ad-hoc .-> NAS
  NAS --> Legacy --> OnDW

  %% New governed flow
  Bronze --> DQ --> Silver --> Gold
  Gold --> Semantic

  %% Styling
  classDef retire fill:#ffeceb,stroke:#e5484d,stroke-dasharray:5 3,stroke-width:2px,color:#5a1a1d;
  classDef add fill:#e9f8ef,stroke:#2bb673,stroke-width:2px,color:#0f3d2c;
  classDef migrate fill:#e8f1ff,stroke:#3a7afe,stroke-width:2px,color:#0e2a64;
```
> *Delta Map highlighting the removal of shared-drive intake, legacy jobs, and on-prem as the primary source of truth. It also shows the addition of Bronze/Silver/Gold layers, early automated quality checks, and shared definitions, along with the standardization of data entry through managed connectors, scheduled batch intake, and a single analytical store.*.

---

## Why this matters

This isn’t about chasing the latest software. It’s about setting up an engineering approach that:

- Handles growth without adding chaos.  
- Makes processes repeatable across teams and projects.  
- Gives you a single, trusted foundation for all downstream work.  

When your data environment is designed this way, technology choices become easier, because they’re guided by a clear operating model instead of being the starting point.

---

## Next steps

If your current-state looks more like the first diagram than the second, the first move isn’t to buy new software. It’s to map your flows, identify the uncontrolled entry points, and decide what your “front door” should be.

From there, governance, automation, and layered structure follow naturally — and the result is an environment that supports the work you’re doing today and the scale you’ll need tomorrow.