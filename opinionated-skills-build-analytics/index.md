---
title: "Opinionated Skills to Build Analytics"
channel: data-engineering-with-claude
status: draft
publish_date: null
tags: [data-management, claude-code, skills, analytics, data-modeling]
skills_refs: [data-architecture, data-engineering, analytics, ai-automation, data-strategy]
---

# Opinionated Skills to Build Analytics

This is the first in a series where I take core data management principles and turn them into Claude Code skills — reusable, opinionated prompts that encode decades of practice into something you can actually run.

I'm starting with data modeling because it's where most analytics projects go wrong. Not the tools. Not the infrastructure. The model. Get the model wrong and everything downstream — reports, dashboards, ML features — inherits that mistake.

## Why Skills?

If you've used Claude Code, you know the pattern: you describe what you want, Claude builds it, you iterate. That works for one-off tasks. But data management isn't one-off. It's the application of principles, consistently, across every table, every pipeline, every query.

A skill encodes those principles. Instead of explaining dimensional modeling theory every time I ask Claude to help me design a fact table, I load a skill that already knows the rules. The skill is opinionated — it reflects how I think about data modeling after twenty-five years of building warehouses and pipelines. You might disagree with some of my opinions. Good. Fork the skill and encode your own.

## Core Principles

The Data Modeler skill I'm sharing below is built on a few principles I've found to be non-negotiable:

**1. Model the business process, not the source system.**

Source systems change. Business processes change slower. If your fact table mirrors the structure of your ERP, you've built a dependency that will break every time someone changes a field in Zoho or Salesforce. Model the business event — the order, the shipment, the payment — and let the ETL handle the mapping.

**2. Dimensions are shared. Facts are specific.**

A customer dimension should be the same customer dimension whether you're looking at sales, support tickets, or invoicing. The moment you build a "sales customer" and a "support customer" with slightly different attributes, you've created a reconciliation problem that will haunt you forever.

**3. Grain is sacred.**

Every fact table has one and only one grain. If you can't state the grain in one sentence — "one row per order line per day" — the table is doing too much. Mixed-grain tables are the single most common analytics mistake I see in production.

**4. Conformed dimensions enable cross-process analytics.**

This is Kimball's biggest insight and the one most teams skip. If your date dimension, customer dimension, and product dimension are conformed across all your fact tables, you can answer questions that span business processes without building custom joins. If they're not, every cross-process question requires a data engineering project.

**5. Slowly changing dimensions are a business decision, not a technical one.**

Type 1 (overwrite) vs Type 2 (versioned) vs Type 3 (previous value) is not a data engineering question. It's a question about what the business needs to know. "Do we need to see what region a customer was in when they placed the order, or just what region they're in now?" That's a business question. Make the business answer it before you pick the SCD type.

## The Data Modeler Skill

Here's the skill. Drop it into your Claude Code skills directory and load it when you're doing dimensional modeling work.

```markdown
# Data Modeler

You are a dimensional modeling specialist. Apply Kimball methodology with the
following opinionated constraints:

## Principles
- Model business processes, not source systems
- Every fact table has exactly one grain, stated explicitly
- Dimensions are conformed across fact tables by default
- SCD type is a business decision — ask before assuming

## When designing a fact table:
1. State the grain in one sentence
2. Identify the business process it measures
3. List the dimensions (who, what, when, where, how)
4. List the measures (additive, semi-additive, non-additive)
5. Confirm no mixed grain — if two events at different granularity,
   use two fact tables

## When designing a dimension:
1. Check if a conformed version already exists
2. If yes, extend it — do not create a parallel dimension
3. Identify natural key vs surrogate key
4. Determine SCD type for each attribute (ask the user)
5. Include a "current" flag and effective date range for Type 2

## Naming conventions:
- Fact tables: fact_{business_process} (e.g., fact_order_lines)
- Dimensions: dim_{entity} (e.g., dim_customer)
- Surrogate keys: {table}_sk
- Natural keys: {table}_nk
- Measures: descriptive, no abbreviations (total_amount, not tot_amt)

## Anti-patterns to flag:
- Mixed grain in a single fact table
- Dimension attributes in the fact table
- Non-conformed dimensions across fact tables
- "One big table" approaches that skip dimensional modeling
- Star schema with no date dimension
```

## How I Use It

When I'm designing a new analytics model — say, for the manufacturing workflow at Fen X Custom — I load this skill and start describing the business process. Claude asks the right questions because the skill tells it to. "What's the grain?" "Is there an existing customer dimension we should conform to?" "What SCD type does the business need for product attributes?"

The conversation is faster and the output is better than if I started from scratch every time. And when I hand the model to someone else on the team, the skill documents the reasoning.

## What's Next

This is the first skill in the series. Coming up:

- **Data Quality Checker** — encoding data quality rules as a reusable Claude skill
- **Pipeline Reviewer** — a skill that reviews ETL/ELT pipeline designs against common anti-patterns
- **Schema Evolution Advisor** — handling schema changes without breaking downstream consumers

Each one encodes a set of principles I've applied across EY, ThoughtWorks, Clorox, and now Fen X Custom. The principles don't change much. The tools change constantly. Skills bridge the gap.

If you want to build your own, start with the question: "What do I explain to every new team member?" That's your first skill.
