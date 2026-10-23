---
title: "Sizing a B2B market before you build a list: using Data Galactica's enums and ranked lists"
description: "How to estimate how many companies or people match your target before buying data, then page through ranked lists with the Data Galactica API."
---

# Sizing a B2B market before you build a list

A common mistake in B2B sales and research is to start by buying or scraping a list, then discover the segment is ten times bigger (or smaller) than assumed. A better order is: **size first, then page through**. The [Data Galactica API](https://datagalactica.com/api) is built to support exactly that.

## What the dataset covers

Data Galactica gives every person and company a permanent ID. The API page lists **28.6 million organisations**, **95.6 million people**, **252 countries** and **762 ranked lists** (October 2026). Every record carries a quality grade and its sources.

## Step 1: Get the counts with /enums

`GET /api/v1/enums` returns every industry, function and country with **live counts**. A trimmed example from the API page:

```json
{ "industry": { "values": [
  { "code": "J", "name": "Information and communication",
    "organisations": 1018079 }, ... ] },
  "function": [ { "code": "engineering", "people": 1319543 }, ... ] }
```

Use it to answer questions such as:

- How many organisations are in industry section J (information and communication)?
- How many people work in engineering functions?
- How do two countries compare in a given industry?

This is enough to decide whether a segment is worth pursuing, and how to split territories, before you spend anything on contact data.

## Step 2: Page through a ranked list with /lists

Once the segment looks right, `/lists` gives you ranked lists you can page through **100 records at a time**, filtered by industry, country, city or function. Records with contact details come first. The pattern on the API page looks like:

```
GET /lists/c/cc/in/sec/J?page=2
```

That is companies in India in section J, page 2.

## Step 3: Ask in plain words with /find

If you do not know the industry code, `/find` reads a question into filters and tells you how it understood it:

```bash
curl -H "Authorization: Bearer YOUR_KEY" \
  "https://api.datagalactica.com/api/v1/find?q=software+companies+in+pune"
```

The response includes how the query was understood (for example, type company, city Pune, industry 62 software) and the matching records with their Galactica IDs.

## Step 4: Clean and join

- **Verify** candidate companies with `/verify/company` to check they are real and operating.
- **Resolve** your existing register numbers (CIN, LEI, Wikidata IDs and others) to Galactica IDs with `/resolve` so new and old data share one key.
- **Match** CRM rows in batches of 25 with `/match`.

## A worked example

Suppose you sell HR software to mid-sized IT companies in Pune.

1. Use `/enums` to see how many organisations sit in information and communication in India.
2. Use `/find` with "software companies in pune" to see how the API narrows it and roughly how many match.
3. Page through the relevant list 100 at a time, starting with records that have contact details.
4. Verify the shortlist and resolve it into your CRM using Galactica IDs, so re-imports never create duplicates.

## Getting started

Accounts start with **Rs 50 free credit**. Some MCP tools, such as market research and dataset descriptions, are free; lookups and lists are billed. Full endpoint details are in the [API docs](https://datagalactica.com/api/docs).

---
[Back to the Data Galactica guide](./) · [CRM deduplication with company IDs](crm-deduplication-company-ids.html)
