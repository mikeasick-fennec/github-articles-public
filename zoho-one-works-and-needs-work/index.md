---
title: "What Works and What Needs Work in the Zoho One Product Suite"
channel: the-zoho-cto
status: draft
publish_date: null
tags: [zoho-one, erp, product-review, inventory, sprints, crm, desk, flow]
skills_refs: [zoho-administration, erp-implementation, vendor-evaluation]
---

# What Works and What Needs Work in the Zoho One Product Suite

I've been running Zoho One at Fen X Custom for over a year now. Not as a demo or a pilot — as the actual backbone of a hardware startup. CRM, inventory, manufacturing workflows, invoicing, project management, internal docs. The whole stack.

Here's my honest take on what works, what needs work, and where Zoho sits relative to the enterprise platforms I spent twenty years consulting on.

## The Modules We Run

We're not using all forty-plus apps in the Zoho One bundle. Nobody is. Here's what we actually deploy and depend on daily:

- **Zoho Inventory & Books** — Order management, stock tracking, manufacturing workflows, invoicing, accounting
- **Zoho CRM + Desk** — Customer pipeline and support
- **Zoho Sprints** — Development project management
- **Zoho Office Suite** — Writer, Sheet, Show for internal docs
- **Zoho Flow** — Integration automation between modules (being phased out)

## The Scoring System

Four categories, each scored 1-5:

| Score | Meaning |
|-------|---------|
| 5 | **Excellent** — Nothing to complain about |
| 4 | **Good** — Works well, minor gaps |
| 3 | **Adequate** — Gets the job done, but you feel the friction |
| 2 | **Frustrating** — Works, but you're fighting it regularly |
| 1 | **Broken** — Unusable or so limited it might as well not exist |

**Categories:**

- **Functionality** — Does it do what it's supposed to?
- **API Completeness** — How complete is the API? _(N/A if we don't use it for that module)_
- **Support** — How responsive and helpful is Zoho when something goes wrong?
- **Performance** — How fast and responsive is the module in daily use?

---

## Zoho Inventory & Books — 14/20

Inventory and Books are tightly integrated. The experience is uniform enough that it makes sense to score them together.

| Category | Score | |
|----------|-------|-|
| Functionality | 4 | Our team has been able to do all of the needed customizations to enable the selling of highly customized products. |
| API Completeness | 2 | Solid for functional actions but falls down on administrative actions. We had to find a hidden API just to view custom fields so we could compare our staging environment to production. Custom fields can only be created through the UI, which introduces a human element that causes arbitrary differences between environments. |
| Support | 5 | While Zoho support is highly variable across the suite, the Inventory and Books team has been standout excellent. Knowledgeable, responsive, and genuinely helpful. |
| Performance | 3 | Normally fast, but we get intermittent lag days where even simple page loads slow down. Concerning because we're still a small install with only six months of transaction history. |

The custom field limitations deserve their own post — and they're getting one. The short version: you can't rename them, you can't delete them without losing data, and you can't change data types. Plan your field design carefully on day one, because you're living with it.

## Zoho Sprints — 14/20

| Category | Score | |
|----------|-------|-|
| Functionality | 4 | Sprints has most of what's needed. If you're used to Jira or another advanced package, it will be a step back — but that's a matter of scale and needs, not a defect. For a small dev team it works well. |
| API Completeness | 4 | We haven't hit anything we can't do via API that we want to. Our integration is mostly handled through standard GitHub-Sprints connections, which work reliably. |
| Support | 3 | Variable expertise. Some questions go unanswered. Not terrible, but you can't count on getting a knowledgeable response every time. |
| Performance | 3 | Generally performant but seems to have "bad weeks" where even simple UI operations take a long time. Mostly observed in the UI, not the API. |

Sprints is a solid tool for a team our size. I wouldn't recommend it for a fifty-person engineering organization that needs advanced workflow customization, but for a startup with three to five developers it does the job without getting in the way.

## Zoho Office Suite (Writer, Sheet, Show) — 13/20

| Category | Score | |
|----------|-------|-|
| Functionality | 3 | Serious gaps versus both Google and Microsoft equivalents. Sheets lacks a strong tabular interface and SQL mode that competitors offer. Less technical users find them difficult to navigate. There are subtle, annoying compatibility issues between Zoho Meeting and Zoho Calendar. Zoho Show — the PowerPoint equivalent — is primitive compared to competitors. I cannot see a management consultancy using it successfully. We're a manufacturing company — our only presentations have been internal or fundraising, which we do in PowerPoint. That said, we manage with them and still prefer the simplicity of staying in-suite over adding more tools. |
| API Completeness | 3 | Adequate, but we haven't driven it far. |
| Support | 3 | End user support has not been great. We've had to self-support to get questions answered in a timely fashion. |
| Performance | 4 | Adequate overall. Sheet formula performance can be sluggish on larger workbooks. |

If we had sophisticated needs for these tools, we would need to switch. We don't, so we stay. The value is suite simplicity, not tool excellence.

## Zoho CRM + Desk — 12/15

| Category | Score | |
|----------|-------|-|
| Functionality | 4 | The tool has done everything we want. There is more complexity to CRM than we'd like, but we know there are lower-complexity configurations available. As our company scales up, we'll be driving more complex support scenarios — with a focus on B2B support. |
| API Completeness | 4 | The CRM API appears to be the most complete in the suite, though there's some confusing overlapping functionality with other modules. The Desk API has been adequate. |
| Support | N/A | We haven't engaged Zoho support for CRM or Desk in any depth. |
| Performance | 4 | Adequate to date. |

CRM is probably Zoho's most mature product, and it shows. The depth is there when you need it. For a small hardware company, we're using maybe a quarter of its capabilities — which means there's room to grow into it.

## Zoho Flow — 6/10

This is the only module we're actively removing from our solution.

| Category | Score | |
|----------|-------|-|
| Functionality | 3 | Flow has many connections and basic transformation capabilities. It could work for organizations that are primarily within the Zoho suite. We are not — we have a significant component of our solution written in Python-Django, and Flow was a poor fit for hybrid architectures. |
| API Completeness | N/A | Did not engage Flow at the API level. |
| Support | 3 | Spotty. We got accurate answers to our questions, but the answers confirmed that the limitations we were hitting were by design, not bugs. |
| Performance | N/A | Insufficient data for a fair score. We did feel that webhook integrations were getting delayed at times. |

The real issues are deeper than the scores suggest:

**Deluge.** Zoho's scripting language was a poor fit for us. We were unable to find a written language specification, and support was unable to provide one. Debugging was frustrating — poor error messaging, limited logging, and no integration with external logging or observability tools. If you're a team that expects to debug with CloudWatch, Datadog, or any external observability stack, Deluge will feel like going back in time.

**Error handling and logging.** Flow's local logging and debugging history can get reset, preventing the accumulation of history you need for troubleshooting. There's no Flow-level integration with AWS CloudWatch, which we use extensively. For a team that runs on observable systems, this was a dealbreaker.

Flow may work for organizations with simple use cases or that are fully committed to the Zoho suite. If you have external services, custom code, and an expectation of production-grade observability, look elsewhere.

---

## The Scorecard

| Module | Functionality | API | Support | Performance | Total |
|--------|:---:|:---:|:---:|:---:|:---:|
| Inventory & Books | 4 | 2 | 5 | 3 | **14/20** |
| Sprints | 4 | 4 | 3 | 3 | **14/20** |
| Office Suite | 3 | 3 | 3 | 4 | **13/20** |
| CRM + Desk | 4 | 4 | N/A | 4 | **12/15** |
| Flow | 3 | N/A | 3 | N/A | **6/10** |

## The Big Picture

Zoho One's value proposition is real: one subscription, all the modules, data flows between them without third-party integration tax. For a startup that needs CRM, inventory, accounting, project management, and internal docs, there's nothing else at this price point that covers this much ground.

But "covers ground" and "does it well" aren't the same thing. The individual modules range from genuinely good (CRM, Inventory & Books support) to genuinely frustrating (Flow for hybrid architectures, Office Suite vs competitors). The integration between modules works until it doesn't — and when it breaks, debugging across Zoho's suite is harder than it should be, especially if your observability tools live outside of Zoho.

My advice if you're evaluating Zoho One: deploy it for the bundle economics and the native integrations. Plan to write Deluge scripts for anything beyond the defaults — and accept that Deluge is a limited language with limited tooling. Budget time for the governance gaps, especially around custom fields. And if you have significant external integrations, think twice before betting on Flow.

_Coming up next: "Zoho Inventory & Books — Custom Fields: Limits, Tips, and Tricks"_
