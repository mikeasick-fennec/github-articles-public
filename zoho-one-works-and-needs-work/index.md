# What Works and What Needs Work in the Zoho One Product Suite

I've been running Zoho One at Fen X Custom for over a year now. Not as a demo or a pilot — as the actual backbone of a smart manufacturing startup. I've been mentally drafting this article in one form or another for 9 months now. Sometimes I've been drafting because of product satisfaction, other times it's been because of frustration. But today, I'm finishing this up to help organizations considering Zoho One make an informed decision. I wrote this as the guide I wish that I had when we evaluated Zoho One.

## Fen X Custom's Motivations for Selecting Zoho One

[Fen X Custom Inc](https://fenxcustom.com) officially started in late 2024 with a 3D printer, a client only iOS application, and nothing in the way of IT infrastructure. We knew we had to focus on building a system for selling and delivering completely custom ear buds.

![Zoho One — Category Overview](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/zoho-categories.png)
*Figure 1: Zoho One — Category Overview*

### Fen X Custom's - How Custom is Custom?

While we support basic customization by purpose (swimming, hearing protection, acoustic, ...), and type (full shell, half shell, 3/4 shell, ...) and color, we hyper personalize by fit. We do this by taking a scan of your outer ear and making a highly accurate prediction about your inner ear, to produce an ear bud that is custom to your ear. The [Acoustic ](https://fenxcustom.com/collections/music/products/acoustic)earbuds featured below are custom to the user based on their scan. With fit confirmed, they fit the users ears specifically and with a level of comfort that universal tips can't match.

![Fen X Custom Acoustic Earbuds](https://fenxcustom.com/cdn/shop/files/acoustic-both-halfshell-black-alt_CIHFBK1WO41B-03.jpg?v=1772903182&width=360)

*Figure 2: Fen X Custom — Acoustic Earbuds*

Fen X delivers this level of customization using a customized E-Commerce experience, an Ear Scanning App (iOS only, Android this summer!), and a set of integrated Backend and ERP level functions shown below.

![Fen X Custom — System Context](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/fenx-system.png)
*Figure 3: Fen X Custom — System Context*

### What Did This Mean for Our Systems?

Fen X knew that we would have to focus on three key areas:

1.  **Custom Buying**: Our buy process combines the typical order process with the need to take a custom ear scan and connect it with the initial and all subsequent orders. We knew we would have to focus on a custom purchase process that allows us to gather information about the user of our scanning process and our custom Ear Scanning App (currently iOS only).
2.  **Custom Manufacturing**: We knew our inventory and manufacturing systems needed to be deeply aware of the custom nature of our products.
3.  **Custom Service**: Both direct sales to a consumer (B2C) and resales through a third party partner (B2B2C), require us to support the end consumer to have success in custom buying, ear scanning, confirmation of fit, and correction when needed.

### So How Did We Get to Zoho? The Core!

Based on the above, we knew there was no single system that would provide us with all of our requirements. Based on that, we decided that we would have a rich set of custom services shaped around our business needs (implemented in Python-Django, but that's another article). Since we did not want to write everything custom, we knew we wanted to pull in some big components that we could customize to our processes, including: E-Commerce, Inventory & Manufacturing, and Help Desk (Customer Facing).

Enter Zoho, who offers:

*  **Zoho Commerce**: An e-commerce package with a catalog, ordering, payment, and fulfillment services.
*  **Zoho Inventory**: An inventory and light manufacturing system that manages products, sales orders, work orders, packaging, shipping, purchasing, invoicing, and returns.
*  **Zoho CRM & Desk**: An integrated Customer Relationship Management (CRM) system and a help desk and ticketing system.

The ability to integrate natively across modules is at the core of Zoho's value proposition. This requires the integration to be both configurable and Application Programming Interface (API) forward.

### So How Did We Get to Zoho? The Rest!

As big of a deal as it was to satisfy our core needs, we also did not want to spend a large amount of resources focusing on the basic systems that every company needs to operate but which are non-differentiating. These would include Directory Services, Email, Office Suite, Scheduling, Chat, Agile Project Management, Email Lists / Shared Inboxes, Cloud Drive, Accounting, Expenses, Human Resource Information System, Reporting / Analytics, Contracts & Signatures, Mobile Device Management, and Multi-Factor Authentication.

For Fen X, we require all of these systems to work, but none of them are differentiating for our business. For a consultancy, Zoho Show is unlikely to replace PowerPoint where slide decks are an end deliverable. For Fen X, we just need to put together a slide deck to get some ideas across (unless we're fundraising, then we use PowerPoint).

![Zoho One — Application Map](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/zoho-apps.png)
*Figure 4: Zoho One — Application Map (✓ = modules Fen X runs)*

### So How Did We Get to Zoho? The Price ($$)

I would be lying if I said that this was decision independent of cost. The pricing plan for Zoho One, which bundles all of these applications, is $37/employee/month for the annualized price. Other Fen X team members initially had trouble understanding just how much was covered under the flat per-employee pricing. In the beginning, I'd constantly get questions / pushback like "Well QuickBooks only costs X, isn't that cheaper?". Where QuickBooks might cost some non-trivial portion of the Zoho One pricing, and only cover Zoho Books and parts of Inventory. When we compared side to side, nothing was really price competitive with Zoho. Certainly not a best of breed approach, even before we considered integration costs. In summary, we found that Zoho was affordable when we had a fairly long runway to selling product.

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

**The Conclusion for Core?** Zoho is meeting / exceeding on the core applications. They work well and, despite some gaps, we've been able to do what we need when we need to. We might have additional input here as we expand our use cases and address more exception workflows.

**The Conclusion for "The Rest"?** We find the rest of the Zoho stack to be a mixed bag. Products range from solid to almost there to ones with fundamental issues. For example, Zoho Calendar-Meeting has issues where events cannot be reliably updated and/or deleted. This creates confusion. A few problems with the core productivity applications does not sound so bad, but these are the types of issues that start you down the path of putting in other products and reducing the core value proposition of Zoho One.

Would I take us down the Zoho One path again, knowing what I know now? Yes, but likely with some adjustment. I'm hoping that Zoho gets to the fixes before we get the chance to make changes. Details below. With adjustments, our top level architecture is:

![Fen X Custom — Technology Architecture](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/fenx-tech.png)
*Figure 5: Fen X Custom — Technology Architecture*

## The Scoring System

Four categories, each scored 1-5:

![The Scoring System](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-system.png)
*Figure 6: The Scoring System*

**Categories:**

*  **Functionality** — Does it do what it's supposed to?
*  **API Completeness** — How complete is the API? *(N/A if we don't use it for that module)*
*  **Support** — How responsive and helpful is Zoho when something goes wrong?
*  **Performance** — How fast and responsive is the module in daily use?

---

## Zoho Inventory & Books — 16/20

Inventory and Books are tightly integrated. It makes sense to score them together.

![Zoho Inventory & Books Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-inventory.png)
*Figure 7: Zoho Inventory & Books Score*

**Functionality** is solid — we've been able to customize everything we need for selling highly customized product. Immutable custom fields creates a significant gap because you cannot change their API level name or their data type. Zoho does not even support non-breaking data type changes (i.e. from string menu item to general string). This has produced a set of "dead" custom fields that we need to relabel and document. Over time, this "cruft" will need a solution.

**Support** for Inventory and Books has been exceptional within the Zoho ecosystem. The team is knowledgeable, responsive, genuinely helpful.

**API** is where Inventory falls down. It's solid for functional actions but breaks on administrative ones. We had to find a hidden API just to view custom fields so we could compare staging to production. There is no API for creating custom fields, instead a human (or maybe an agent) needs to create custom fields through the Inventory-Books UI. People are less consistent than an API or IaC (Infrastructure as Code) tool and they make mistakes. This creates inconsistencies across environments. The combined the inability to programmatically validate and create custom fields and the issue of effectively immutable custom fields, and has left us with custom fields we do not use and cannot delete.

**Performance** of Inventory and Books is normally fast, but we get intermittent lag days when even simple page loads slow down. Concerning because we're still a small install with only six months of transaction history.

The custom field limitations deserve their own post — and they're getting one. The short version: you can't rename them, you can't delete them without losing data, and you can't change data types. Plan your field design carefully on day one, because you're living with it.

## Zoho Commerce — 12/20

Zoho Commerce is a newer product, just on its 2.0 version. Commerce is not mature and we quickly found we could not customize the cart add / checkout experience for our needs. I hope to do a specific article on how we created a custom shopping experience in Shopify and better show the gaps we found in Zoho Commerce at that time.

![Zoho Commerce Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-commerce.png)
*Figure 8: Zoho Commerce Score*

**Functionality** is basic. Fen X couldn't customize the product add or checkout process in the way we needed to support a custom checkout. We could have sent customers to a second site post checkout, but with already needing to do a scan this seemed overly complex. Commerce's integration to Inventory would fail at times, which reduced a big part of the attraction. Zoho Commerce-Books did not allow us to change a business' tax treatment in Commerce without also changing it generally in Books. This was not the desired effect.

**Support** — The support team was responsive; they just did not have the answers we were looking for, we did not hold that against them.

**API** — The API seemed relatively complete, again the core issue was the functionality that they projected.

**Performance** — Performance seemed fine in our tests, though we did not put it through any scaling stresses.

## Zoho Sprints — 13/20

![Zoho Sprints Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-sprints.png)
*Figure 9: Zoho Sprints Score*

**Functionality** Sprints has most of what you'd need. If you're used to Jira, it'll be a step back — but that's scale and needs, not a defect. For a small dev team it works well. We haven't hit anything we can't do via API. Our integration runs through standard GitHub-Sprints connections, which work reliably.

**Support** is variable — some questions go unanswered. Not terrible, but you can't count on getting a knowledgeable response every time.

**Performance** is generally fine but seems to have "bad weeks" where even simple UI operations drag. Mostly in the UI, not the API.

I wouldn't recommend Sprints for a fifty-person engineering org. For a startup with three to five developers, it does the job without getting in the way.

## Zoho Office Suite (Writer, Sheet, Show) — 12/20

![Zoho Office Suite Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-office.png)
*Figure 10: Zoho Office Suite Score*

**Functionality** There are serious gaps versus Google and Microsoft equivalents. Sheets lacks a strong tabular interface and SQL mode. Less technical users find them hard to navigate. Zoho Show — the PowerPoint equivalent — is primitive. I can't see a management consultancy using it successfully. We're a manufacturing company — our presentations are internal or fundraising, and we do those in PowerPoint.

**API Completeness** Fen X has found the API adequate but we haven't driven it far.

**Support** for the Office products hasn't been great — we've had to self-support to get answers in a timely fashion. Often tickets are not responded to or are not responded to in a timely fashion. 

**Performance** is fine overall, though Sheet formula performance gets sluggish on larger workbooks.

If we had sophisticated needs for these tools, we'd need to switch. We don't, so we stay. The value is suite simplicity, not tool excellence.

## Zoho CRM + Desk — 16/20

![Zoho CRM + Desk Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-crm.png)
*Figure 11: Zoho CRM + Desk Score*

**Functionality** CRM is probably Zoho's most mature product, and it shows. It's done everything we've asked it to. There's more complexity than we'd like, but we know there are lower-complexity configurations available. As we scale, we'll be driving more complex B2B support scenarios.

**API** **Completeness** for CRM is mature, though there's some confusing overlap with other modules. The Desk API has been adequate. We haven't had to engage support for CRM or Desk in any depth — which is its own kind of endorsement.

For a small manufacturing company, we're using maybe a quarter of CRM's capabilities. That means there's room to grow into it.

**Support** of CRM/Desk has been adequate but we have not really put it through its paces.

**Performance** of the CRM/Desk has been adequate, no issues but we are not operating at scale.

## Zoho Flow — 9/20

This is the only module we're actively removing from our solution.

![Zoho Flow Score](https://raw.githubusercontent.com/mikeasick-fennec/github-articles-public/main/zoho-one-works-and-needs-work/score-flow.png)
*Figure 12: Zoho Flow Score*

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
*Figure 13: The Scorecard*

## Additional Notes

Avoid Deluge if you have the capability to develop in another language. It has little advantage over using an external language which can leverage the core APIs. Poor observability and features made it a non-starter for us.