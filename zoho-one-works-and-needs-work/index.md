# What Works and What Needs Work in the Zoho One Product Suite

I've been running Zoho One at Fen X Custom for over a year now. Not as a demo or a pilot — as the actual backbone of a hardware startup. I've been mentally drafting this article in one form or another for 9 months now. Sometimes I've been drafting because of product satisfaction, other times it's been because of frustration. But today, I'm finishing this up to help organizations considering Zoho One make an informed decision. Below is the start of the guide I wish that I had when we evaluated Zoho One. 

## Fen X Custom's Motivations for Selecting Zoho One

[Fen X Custom Inc](https://fenxcustom.com) was officially started in late 2024 with a 3D printer, a client only iOS application, and nothing in the way of IT infrastructure. We knew we had to focus on building a system for selling and delivering completely custom ear buds.

![Zoho One — Category Overview](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/zoho-categories.png) *Figure 1: Zoho One — Category Overview*

### Fen X Custom's - How Custom is Custom?

While we support basic customization by purpose (swimming, hearing protection, acoustic, ...), and type (full shell, half shell, 3/4 shell, ...) and color, we hyper personalize by fit. We do this by taking a scan of your outer ear and making a highly accurate prediction about your inner ear, to produce an ear bud that is custom to your ear.

![Fen X Custom — System Context](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/fenx-system.png) *Figure 2: Fen X Custom — System Context*

### What Did This Mean for Our Systems?

Fen X knew that we would have to focus on three key areas:

1.  **Custom Buying**: Our buy process combines the typical order process with the need to take a custom ear scan and connect it with the initial and all subsequent orders. We knew we would have to focus on a custom purchase process that allows us to gather information about the user of our scanning process and our custom Ear Scanning App (currently iOS only).
2.  **Custom Manufacturing**: We knew our inventory and manufacturing systems needed to be deeply aware of the custom nature of our products.
3.  **Custom Service**: Both direct sales to a consumer (B2C) and resales through a third party partner (B2B2C), require us to support the end consumer to have success in custom buying, ear scanning, confirmation of fit, and correction when needed.

### So How Did We Get to Zoho? The Core!

Based on the above, we knew there was no single system that would provide us with all of our requirements. Based on that, we decided that we would have a rich set of custom services shaped around our business needs (implemented in Python-Django, but that's another story). Since we did not want to write everything custom, we knew we wanted to pull in some big components that we could customize to our processes, including: E-Commerce, Inventory & Manufacturing, and Help Desk (Customer Facing).

Enter Zoho, who offers:

*  **Zoho Commerce**: An e-commerce package with a catalog, ordering, payment, and fulfillment services.
*  **Zoho Inventory**: An inventory and light manufacturing system that manages products, sales orders, work orders, packaging, shipping, purchasing, invoicing, and returns.
*  **Zoho CRM & Desk**: An integrated Customer Relationship Management (CRM) system and a help desk and ticketing system.

Zoho's promise across modules is that they were integrated and Application Programming Interface (API) forward.

### So How Did We Get to Zoho? The Rest!

As big of a deal as it was to satisfy our core needs, we also did not want to spend a large amount of resources focusing on the basic systems that every company needs to operate but which are non-differentiating. These would include Directory Services, Email, Office Suite, Scheduling, Chat, Agile Project Management, Email Lists / Shared Inboxes, Cloud Drive, Accounting, Expenses, Human Resource Information System, Reporting / Analytics, Contracts & Signatures, Mobile Device Management, and Multi-Factor Authentication. All of these systems are important, but none of them are differentiating as long as they basically work.

![Zoho One — Application Map](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/zoho-apps.png) *Figure 3: Zoho One — Application Map (✓ = modules Fen X runs)*

### So How Did We Get to Zoho? The Price ($$)

I would be lying if I said that this was decision independent of cost. The pricing plan for Zoho One, which bundles all of these applications, is $37/employee/month for the annualized price. This number was difficult for some of the team to get their head around. In the beginning, I'd constantly get questions / pushback like "Well Quickbooks only costs X, isn't that cheaper?". But when we compared side to side, nothing was really price competitive with Zoho. Certainly not a best of breed approach, even before the cost of integration was considered. So, long-short, Zoho was a product we could afford when we had a fairly long time between when we were starting and when we were selling product.

## The Modules We Run

We don't use all forty-plus apps in the Zoho One bundle. Nobody does. Here's what we actually deploy and depend on daily:

*  **~~Zoho Commerce~~** — ~~E-commerce storefront with catalog, ordering, payment, and fulfillment~~ (We ended up finding Zoho Commerce was not flexible enough for our needs and went with Shopify instead)
*  **Zoho Inventory & Books** — Order management, stock tracking, manufacturing workflows, invoicing, accounting
*  **Zoho CRM & Desk** — Customer pipeline and support tickets
*  **Zoho Sprints** — Agile project management
*  **Zoho Office Suite** — Writer, Sheet, Show for internal docs
*  **Zoho Flow** — Integration automation (being phased out)
*  **Everything else** — Mail, Cliq, TeamInbox, Campaigns, Forms, Bookings, WorkDrive, Meeting, Vani, Analytics, People, Expense, Contracts, Sign, OneAuth

## The Conclusion

While I'm going to score some of our experiences with Zoho, I figured it would be helpful to put the conclusion up front instead of making anyone who made it this far through more reading. To succeed with Zoho, we really needed two things:

1. A Strong performance from the core Modules (Inventory, Desk, CRM, Books), with a focus on functionality, API completeness, support, and performance.
2. "Good Enough" performance from everything else. We don't need all of Outlook's features, but we do need Mail and Calendar to work and be reliable.

The Conclusion for Core? Zoho is meeting / exceeding on the core applications. They work well and, despite some gaps, we've been able to do what we need when we need to. We might have additional input here as we expand our use cases and address more exception workflows.

The Conclusion for "The Rest"? Zoho is a mixed bag. There are some very solid products in the mix. There are some that are "almost there" and there are some products with some fundamental issues that Zoho needs to address to be competitive. Maybe just a few problems with the Office Suite does not sound so bad, but these are the types of issues that start you down the path of putting in other products and reducing the core value proposition of Zoho One.

Would I take us down the Zoho One path again, knowing what I know now? Yes, but likely with some adjustment. I'm hoping that Zoho gets to the fixes before we get the chance to make changes. Details below. With adjustments, our top level architecture is:

![Fen X Custom — Technology Architecture](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/fenx-tech.png) *Figure 4: Fen X Custom — Technology Architecture*

## The Scoring System

Four categories, each scored 1-5:

![The Scoring System](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-system.png)

**Categories:**

*  **Functionality** — Does it do what it's supposed to?
*  **API Completeness** — How complete is the API? *(N/A if we don't use it for that module)*
*  **Support** — How responsive and helpful is Zoho when something goes wrong?
*  **Performance** — How fast and responsive is the module in daily use?

---

## Zoho Inventory & Books — 16/20

Inventory and Books are tightly integrated. It makes sense to score them together.

![Zoho Inventory & Books Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-inventory.png)

**Functionality** is solid — we've been able to customize everything we need for selling highly customized products.

**Support** is the standout here. While Zoho support is variable across the suite, the Inventory and Books team is excellent. Knowledgeable, responsive, genuinely helpful.

**API** is where it falls down. It's solid for functional actions but breaks on administrative ones. We had to find a hidden API just to view custom fields so we could compare staging to production. Custom fields can only be created through the UI — which means arbitrary differences between environments with no way to automate governance.

**Performance** is normally fast, but we get intermittent lag days where even simple page loads slow down. Concerning because we're still a small install with only six months of transaction history.

The custom field limitations deserve their own post — and they're getting one. The short version: you can't rename them, you can't delete them without losing data, and you can't change data types. Plan your field design carefully on day one, because you're living with it.

## Zoho Commerce — 12/20

Zoho Commerce is a newer product, just on its 2.0 version. It is not a mature product and we quickly went past our ability to customize it for our purposes.

![Zoho Commerce Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-commerce.png)

**Functionality** is basic. We were not able to customize the product add or checkout process in the way we needed to support a custom checkout. We could have sent customers to a second site post checkout, but with already needing to do a scan this seemed overly complex. We had integration to Inventory fail at times, which is a big part of the attraction. Changing tax treatment was awkward, making changes in Books when none was desired.

**Support** is the standout here. While Zoho support is variable across the suite, the Inventory and Books team is excellent. Knowledgeable, responsive, genuinely helpful.

**API** is where it falls down. It's solid for functional actions but breaks on administrative ones. We had to find a hidden API just to view custom fields so we could compare staging to production. Custom fields can only be created through the UI — which means arbitrary differences between environments with no way to automate governance.

**Performance** is normally fast, but we get intermittent lag days where even simple page loads slow down. Concerning because we're still a small install with only six months of transaction history.

The custom field limitations deserve their own post — and they're getting one. The short version: you can't rename them, you can't delete them without losing data, and you can't change data types. Plan your field design carefully on day one, because you're living with it.

## Zoho Sprints — 13/20

![Zoho Sprints Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-sprints.png)

**Functionality** Sprints has most of what you'd need. If you're used to Jira, it'll be a step back — but that's scale and needs, not a defect. For a small dev team it works well. We haven't hit anything we can't do via API. Our integration runs through standard GitHub-Sprints connections, which work reliably.

**Support** is variable — some questions go unanswered. Not terrible, but you can't count on getting a knowledgeable response every time.

**Performance** is generally fine but seems to have "bad weeks" where even simple UI operations drag. Mostly in the UI, not the API.

I wouldn't recommend Sprints for a fifty-person engineering org. For a startup with three to five developers, it does the job without getting in the way.

## Zoho Office Suite (Writer, Sheet, Show) — 12/20

![Zoho Office Suite Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-office.png)

**Functionality** There are serious gaps versus Google and Microsoft equivalents. Sheets lacks a strong tabular interface and SQL mode. Less technical users find them hard to navigate. Zoho Show — the PowerPoint equivalent — is primitive. I can't see a management consultancy using it successfully. We're a manufacturing company — our presentations are internal or fundraising, and we do those in PowerPoint.

**API Completeness** is adequate but we haven't driven it far.

**Support** hasn't been great — we've had to self-support to get answers in a timely fashion.

**Performance** is fine overall, though Sheet formula performance gets sluggish on larger workbooks.

If we had sophisticated needs for these tools, we'd need to switch. We don't, so we stay. The value is suite simplicity, not tool excellence.

## Zoho CRM + Desk — 16/20

![Zoho CRM + Desk Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-crm.png)

**Functionality** CRM is probably Zoho's most mature product, and it shows. It's done everything we've asked it to. There's more complexity than we'd like, but we know there are lower-complexity configurations available. As we scale, we'll be driving more complex B2B support scenarios.

**API** **Completeness** for CRM is the most complete in the suite, though there's some confusing overlap with other modules. The Desk API has been adequate. We haven't had to engage support for CRM or Desk in any depth — which is its own kind of endorsement.

For a small hardware company, we're using maybe a quarter of CRM's capabilities. That means there's room to grow into it.

**Support** has been adequate but we have not really put it through its paces.

**Performance** has been adequate, no issues but we are not operating at scale.

## Zoho Flow — 9/20

This is the only module we're actively removing from our solution.

![Zoho Flow Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-flow.png)

Functionality for Flow is rich by features, it has many connections and basic transformation capabilities. It could work for organizations that live primarily within the Zoho suite. We don't — we have a significant component of our solution in Python-Django, and Flow was a poor fit for hybrid architectures.

**API Completeness:** We did not test it extensively, but the API functions we did look for like monitoring were non-existent.

**Support** was spotty. We got accurate answers, but they confirmed that the limitations we were hitting were by design, not bugs.

**Performance** was unreliable — webhook integrations got delayed and we couldn't diagnose why.

The real issues are deeper than the scores suggest:

**Deluge.** Zoho's scripting language was a poor fit for us. We couldn't find a written language specification, and support couldn't provide one. Debugging was frustrating — poor error messaging, limited logging, and no integration with external observability tools. If you're a team that expects to debug with CloudWatch, Datadog, or any external stack, Deluge will feel like going back in time.

**Error handling and logging.** Flow's local logging and debugging history can get reset, preventing the accumulation of history you need for troubleshooting. There's no Flow-level integration with AWS CloudWatch, which we use extensively. For a team that runs on observable systems, this was a dealbreaker.

Flow may work for organizations with simple use cases or that are fully committed to the Zoho suite. If you've got external services, custom code, and an expectation of production-grade observability, look elsewhere.

---

## The Scorecard

![The Scorecard](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-summary.png)

## Additional Notes

Avoid Deluge if you have the capability to develop in another language. It has little advantage over using an external language which can leverage the core APIs. Poor observability and features made it a non-starter for us.