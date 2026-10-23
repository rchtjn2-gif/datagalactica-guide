---
title: "De-duplicating company records in a CRM: why names fail and IDs work"
description: "A practical way to merge duplicate accounts using registry identifiers instead of fuzzy name matching."
---

# De-duplicating company records in a CRM: why names fail and IDs work

Every CRM older than a year has duplicates: "Tata Consultancy Services", "TCS Ltd" and "Tata Consultancy Services Limited" as three accounts with three owners. Fuzzy name matching helps, but it also merges different companies that happen to share a name, which is worse than leaving duplicates alone.

## Why names fail

- **Many companies share a name.** A common name can belong to dozens of unrelated small businesses across cities.
- **Companies rename.** The registered name changes, the old name lives on in your CRM.
- **Brands are not legal entities.** One brand can sit across several legal companies, and one company can trade under several brands.

## Use identifiers instead

Registry identifiers are assigned once and don't change with branding: the CIN for Indian companies, the LLPIN for LLPs, the LEI for entities active in financial markets, and national company numbers elsewhere. Each covers only part of the world, which is why a permanent ID that crosswalks them is useful. Data Galactica explains its approach on the [Galactica ID page](https://datagalactica.com/galactica-id).

## A practical process

1. **Export accounts** with name, website domain, city and any registry number you already hold.
2. **Resolve each row to an ID.** Use the registry number where you have it; otherwise match on name plus city plus website, and keep the confidence.
3. **Group by ID**, not by name. Rows that share an ID are true duplicates.
4. **Review low-confidence matches by hand** before merging.
5. **Store the ID on the account** so new records are matched on entry.

The [Data Galactica API](https://datagalactica.com/api) can match CRM rows in batches and return the permanent ID with a confidence grade, and [About the data](https://datagalactica.com/about-data) explains what the grades mean.

---
Written by Sunny Mittal, marketing lead at [Data Galactica](https://datagalactica.com/).
