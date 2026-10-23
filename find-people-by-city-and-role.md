---
title: "Finding professionals by city and role: how to read a people directory honestly"
description: "Using Data Galactica's 95.6M-person directory by city, function and seniority, and why record grades matter more than raw counts."
---

# Finding professionals by city and role

Recruiters, researchers and sales teams often start with the same question: how many people doing X are there in city Y, and who are they? Data Galactica's people directory answers it with **95,635,820 people across 252 countries and territories**, each with a permanent **DGP-** Galactica ID. Used carelessly, any directory that size gives you a big number and a bad list. Used well, it gives you a sized pool and a short list you can trust.

## Step 1: size the pool by city

The directory's largest Indian cities by people count (October 2026):

| City | People |
|---|---|
| Delhi | 2,187,374 |
| Mumbai | 1,504,547 |
| Chennai | 1,199,072 |
| Bangalore | 941,177 |
| Pune | 881,155 |
| Kolkata | 748,193 |
| Hyderabad | 639,153 |
| New Delhi | 532,508 |
| Gurgaon | 454,389 |

India alone accounts for 26 million records. Note that Delhi and New Delhi are listed separately, as are Gurgaon and nearby cities. Add them if your market is the NCR.

## Step 2: narrow by function

Each person is grouped by the function of their current or latest role: Engineering (1.32M), Media, Public service, Finance, Operations, Administration, Education, Sales, Marketing, Healthcare, Human resources, Design, Research, Customer service, Legal, Leadership and Product.

## Step 3: narrow by seniority

Seniority buckets include professional (4.98M), manager, student, entry and senior. A "senior engineer in Pune" list should filter on both.

## Step 4: read the grade before you act

This is the step most people skip. Every record carries a grade:

- **Verified**: the person claimed the record
- **Gold**: Data Galactica holds an e-mail and a phone, both checked
- **Silver**: an e-mail and a phone
- **Bronze**: less than that

There are about 19 million silver records and 11.6 million bronze. A list of 500 bronze records is a research starting point, not an outreach list. Weight your plan by grade.

## Step 5: confirm a specific person

To check whether there is a public record of a named person at an employer in a city, use the person check rather than a broad search. It answers the narrow question directly.

## Doing it in code

The same steps are available as API endpoints: `/people/search` for talent by city and `/person/check` for a single person in a role, plus `/watch` to be told when a record you rely on changes.

Start from the [Data Galactica people directory](https://datagalactica.com/people), and see the [API reference](https://datagalactica.com/api) for the endpoints.

---
[Back to the Data Galactica guide](./) · [Market sizing with lists](market-sizing-with-lists.html)
