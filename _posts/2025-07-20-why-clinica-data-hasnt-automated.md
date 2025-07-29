---
title: "Post: Standard"
excerpt_separator: "<!--more-->"
categories:
  - Blog
tags:
  - Post Formats
  - readability
  - standard
---

## We Had the Blueprint the Whole Time: Why Clinical Data Hasn’t Automated (Yet)

> In clinical data workflows, the technical potential has always outpaced organizational readiness.

<!--more-->

For over two decades, CDISC has provided us with deeply thoughtful metadata standards. The Operational Data Model (ODM) wasn’t just created to document what we did — it was designed to enable automation, consistency, and reuse. It gave us a structured, machine-readable way to describe the forms, fields, controlled terminology, and relationships that make up a clinical trial.

And yet, here we are: still copying SDTM specs into Excel, writing thousands of lines of SAS code by hand, and maintaining hardcoded mappings across multiple studies that look nearly identical.

It’s not because we’re lazy. It’s because the people doing the work are under-resourced, overburdened, and deeply siloed — and the systems that support them were never designed for modern workflows.

But now, I think we have an opportubity to change that.

## The ODM: More Than Metadata, It's Infrastructure

Let’s start with the basics.

The CDISC Operational Data Model (ODM-XML) is a standardized format for representing:

- Study design
- Case report forms
- Item definitions (with datatypes, labels, units, etc.)
- Codelists and value-level metadata
- Audit trails, versioning, and relationships

It’s verbose, yes. But it’s also deeply rich — and if we treat it like the source of truth, it can do more than describe a study. It can become the foundation for:

- Automated SDTM scaffolding
- Study-agnostic data transformations
- Real-time metadata traceability
- Spec-to-code pipelines with overrides
- AI-assisted mapping and validation

Most teams don’t realize how much information is already embedded in an ODM file — simply because we’ve never been encouraged to use it that way.

##  Example: What’s Actually in an ODM File?
Here’s a simplified snippet of what you might find in a real-world ODM file:

```xml
<ItemDef OID="IT.QS.QSSTRESC" Name="Severity" DataType="text">
  <Question>Severity of Pain</Question>
  <CodeListRef CodeListOID="CL.SEVERITY_SCALE"/>
</ItemDef>

<CodeList OID="CL.SEVERITY_SCALE" Name="Severity Scale">
  <CodeListItem CodedValue="MILD"><Decode><TranslatedText>Mild</TranslatedText></Decode></CodeListItem>
  <CodeListItem CodedValue="MOD"><Decode><TranslatedText>Moderate</TranslatedText></Decode></CodeListItem>
  <CodeListItem CodedValue="SEV"><Decode><TranslatedText>Severe</TranslatedText></Decode></CodeListItem>
</CodeList>
```
From just this, a system could:
- Infer the appropriate STRESC and STRESN logic
- Scaffold the QS domain’s QSSTRESC variable with appropriate mapping
- Validate data values against the codelist

But instead of using this directly, we often retype this same information into a spec spreadsheet… and then again into SAS code.

## Why Haven’t We Used the Specs CDISC Gave Us?

This is the real question, and it deserves reflection.

Here are a few reasons I’ve observed:

### 1. EDC Vendors Own the Output
Most sponsors don’t generate ODM — they receive it from EDC platforms like Medidata or Oracle. That means:
- The structure is often proprietary or inconsistent
- There’s little transparency into how the ODM is generated
- There’s no incentive (yet) to clean or standardize it

### 2. Specs Are Still Handwritten
Even with ODM in place, many orgs still create and pass around Excel/Word-based specs for SDTM mapping. Why?
- It feels familiar
- Programmers are used to SAS, not metadata parsing
- Clinical teams often work in silos from engineers

### 3. ODM Is Treated as an Archive, Not a Tool
The industry sees ODM as a recordkeeping format — something to store, not something to build with. But it was always meant to be both.

## What If We Used ODM as Intended?

| Current State           | Future State (ODM-Driven)          |
| ----------------------- | ---------------------------------- |
| Manual SDTM programming | Auto-scaffolded SDTM SQL           |
| Excel-based specs       | Machine-readable mappings          |
| Per-study derivations   | Modular overrides                  |
| No lineage              | Full traceability from CRF to SDTM |
| Rework across studies   | Reuse with metadata versioning     |


By parsing ODM and pairing it with a reference model (e.g., SDTMIG or CDISC Library), we can:
- Automatically match ItemOIDs to SDTM targets
- Generate compliant scaffolding for standard domains
- Allow for lightweight custom overrides where needed

## What I’m Building

I’ve been working on a Blueprint-as-a-Service (BaaS) framework that:
- Parses ODM-JSON or ODM-XML
- Matches metadata to SDTM targets
- Generates scaffolding SQL using DBT
- Supports overrides for custom derivations
- Outputs traceable, auditable pipeline templates

My goal is to make SDTM programming modular, inspectable, and automatable — while still honoring the deep expertise of clinical teams and the nuances of individual studies.

I’ll be sharing more about the project later. But for now, I want to invite others to reflect with me:

This isn’t about replacing people. It’s about respecting their time and expertise enough to remove the busywork and empower smarter workflows.

We don’t need to wait for vendors to catch up.
We can start small. Build modularly. Use the standards we already have.

If we’re thoughtful, we can finally bridge the gap between what’s possible and what’s actually happening.

If you're enjoying the ideas here and want to stay connected, feel free to [connect with me on LinkedIn](https://www.linkedin.com/in/mlogan914/). I’d love to stay in touch with others thinking about the future of clinical data and systems design.