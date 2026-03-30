# Zhaopin Scraper

Extract structured data from [zhaopin.com](https://zhaopin.com) — structured job listings from zhaopin.com API.

**[Zhaopin Scraper on Apify →](https://apify.com/blackfalcondata/zhaopin-scraper)**

---

## Key features



**Search with filters** — Search by keyword and location.

**Detail enrichment** — Fetch full job descriptions, salary data, employer profiles for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

---

## Use cases



**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from zhaopin.com on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from zhaopin.com.

---

## Quick start

```json
{
  "query": "python",
  "cityId": "530",
  "maxResults": 10,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Job search keywords (e.g. "python", "销售"). Leave empty to browse all jobs in the selected city. |
| `cityId` | string | `"530"` | City code (e.g. "530" for Beijing, "538" for Shanghai, "765" for Shenzhen). Defaults to Beijing. |
| `maxResults` | integer | `50` | Maximum total results. Zhaopin limits to 100 results per query (5 pages × 20). Set 0 for maximum available. |
| `includeDetails` | boolean | `true` | Fetch full job details (description, company profile, address, geo coordinates, HR contact, skills, benefits). |
| `descriptionMaxLength` | integer | `0` | Truncate description to N characters. 0 = no truncation. |
| `compact` | boolean | `false` | Core fields only — for AI-agent and MCP workflows. |
| `incrementalMode` | boolean | `false` | Only return new or changed listings compared to the previous run. |
| `stateKey` | string | — | Identifier for the tracked universe. Use different keys for different query/city combinations. |

---

## FAQ

<!-- WRITE: 4-6 Q&A pairs relevant to this product -->

**Is it legal to scrape zhaopin.com?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->

---

## Related products by Black Falcon Data



- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 03*
