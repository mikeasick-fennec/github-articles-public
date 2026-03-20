---
title: "Zoho Inventory & Books — Custom Fields: Limits, Tips, and Tricks"
channel: the-zoho-cto
status: draft
publish_date: null
tags: [zoho-inventory, zoho-books, custom-fields, governance, erp]
skills_refs: [zoho-administration, erp-implementation, data-governance]
---

# Zoho Inventory & Books — Custom Fields: Limits, Tips, and Tricks

Custom fields are where Zoho's "customizable platform" promise meets reality. They're essential — every business has data that doesn't fit the default fields. But in Zoho Inventory and Books, custom fields come with a set of limitations that can quietly paint you into a corner if you don't plan for them from day one.

I've spent the last year building custom fields across Inventory and Books at Fen X Custom. Here's what I wish I'd known at the start.

## What Are Custom Fields?

Custom fields let you add your own data fields to Zoho modules — items, sales orders, invoices, contacts, purchase orders, and more. You pick a data type, give it a label, and it shows up on the form alongside the built-in fields.

Zoho Books supports about twenty data types: single-line text (255 char limit), multi-line text (36,000 chars), number, decimal, amount, percent, date, date-time, checkbox, dropdown, multi-select (up to 30 options), auto-generate number, email, URL, phone, lookup, attachment (7MB max), image (5MB max), formula, and external lookup.

The variety is good. The limits around managing them are not.

## The Key Limits

### You Can't Rename a Custom Field

This is the one that bites first. You create a field called "Mfg Batch ID" and three months later realize it should be "Manufacturing Batch Number" because that's what everyone actually calls it. Too bad. The internal API name is locked at creation and the label name — while editable in some contexts — doesn't change the API name.

The workaround: plan your naming convention before you create your first field. I know that sounds obvious. I did not do it. You probably won't either.

### You Can't Change the Data Type

Created a text field that should have been a dropdown? You can't convert it. Created a number field that needs to be a decimal? Start over. There is no data type migration path — not even for non-breaking changes like widening a number to a decimal, or converting a single-line text to a multi-line text.

This is frustrating because some of these changes are clearly non-breaking. Going from text to multi-line text doesn't lose data. Going from number to decimal doesn't lose data. But Zoho treats all data type changes the same: impossible.

### You Can't Delete a Field with Data

Technically, you can. But only through "force delete," which permanently destroys all data in that field across every record. There's no "delete the field definition but archive the data" option. No export-then-delete workflow built in.

If you have a field with data in a hundred records and you want to restructure, your options are:

1. Export the data manually, delete the field, create the new field, re-import
2. Force delete and accept the data loss
3. Mark the field as inactive and create a new one alongside it

Option 3 is what most people end up doing, which leads to field sprawl — inactive fields accumulating like sediment layers in your module configuration.

### The Module Limit

You can have a maximum of 44 custom fields per module (varying by subscription plan). That sounds like plenty until you account for the inactive fields you can't clean up. If you've gone through a few iterations of your data model, you can burn through that limit faster than you'd expect.

## Governance Tips

After learning these limits the hard way, here's what I do now:

### 1. Name It Right the First Time

Use a consistent naming convention. I use: `{Category}_{Description}_{Type hint}`

Examples:
- `Mfg_BatchNumber_Text`
- `Order_ShipMethod_Dropdown`
- `Product_Weight_Decimal`

The type hint in the name feels redundant, but it saves you when you're staring at a list of forty fields and trying to remember which one is the dropdown and which one is the text.

### 2. Document Every Field Before Creation

Keep a spreadsheet (or a YAML file, if you're me) that tracks:
- Field name
- Module
- Data type
- Purpose
- Created date
- Active/Inactive status

This is your field registry. Zoho doesn't provide a good overview of your custom fields across modules. Build your own.

### 3. Use Inactive Before Delete

When a field is no longer needed, mark it inactive first. Leave it for at least one reporting cycle. If nobody misses it and no integrations break, then consider whether the data needs to be archived before force-deleting.

### 4. Plan for Dropdowns

Dropdown and multi-select fields have a 30-option limit. If your list might grow beyond that, consider whether a lookup field or a text field with validation in your workflow (Deluge) is a better choice.

### 5. Test in Sandbox

If your plan includes sandbox environments, prototype your custom field design there first. The inability to change data types makes production experimentation expensive.

## What Zoho Needs to Fix

I don't usually do feature requests in blog posts, but these are fundamental governance gaps:

**Allow non-breaking data type changes.** Text to multi-line text. Number to decimal. Single-select to multi-select. These conversions don't lose data. Let us make them.

**Allow field renaming.** At minimum, let us rename the display label without affecting the API name. Ideally, provide a migration path for API names with a deprecation period.

**Provide a field export before delete.** Before force-deleting a field, offer to export the data from that field across all records to CSV. This is a five-minute feature that would save hours of manual work.

**Show custom field usage analytics.** Which fields have data in them? What percentage of records use each field? Which fields haven't been populated in six months? This exists in Zoho CRM. Bring it to Inventory and Books.

**Raise or remove the 44-field limit for higher-tier plans.** When inactive fields count against the limit, the effective limit is much lower than 44.

## The Bottom Line

Custom fields in Zoho Inventory and Books work fine as long as you get them right the first time. The problem is that nobody gets them right the first time. Data models evolve. Business requirements change. The fields you created in month one won't all be the fields you need in month twelve.

Plan for it. Document everything. Name carefully. And keep a registry, because Zoho won't do it for you.
