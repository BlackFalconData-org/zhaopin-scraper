# Zhaopin Scraper

Extract structured data from [zhaopin.com](https://zhaopin.com) — structured job listings from zhaopin.com API.

**[Zhaopin Scraper - China Job Listings on Apify →](https://apify.com/blackfalcondata/zhaopin-scraper?fpr=1h3gvi)**

---

## Key features






**Search with filters** — Search by keyword and location.

**Detail enrichment** — Fetch full job descriptions, salary data, employer profiles for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Description truncation** — Cap description length per listing to control output size and cost.

**Result cap** — Stop after N listings (up to 100). Set to 0 for the full catalog.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Every listing returns the same schema with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases






**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from zhaopin.com on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from zhaopin.com.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**Compensation benchmarking**
Aggregate salary ranges across roles, industries, and locations on zhaopin.com to inform pricing decisions, hiring plans, or candidate negotiations.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

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


## Output fields

Every listing returns the same 34-field schema. Missing values are `null` — never omitted.

- `jobId`
- `title`
- `company`
- `companyId`
- `companyLogo`
- `companySize`
- `companyUrl`
- `companyDescription`
- `industry`
- `financingStage`
- `location`
- `district`
- `address`
- `latitude`
- `longitude`
- `salary`
- `salaryMin`
- `salaryMax`
- `education`
- `experience`
- `employmentType`
- `jobCategory`
- `recruitCount`
- `skills`
- `benefits`
- `description`
- `summary`
- `hrName`
- `hrTitle`
- `portalUrl`
- `postedDate`
- `firstPostedDate`
- `scrapedAt`
- `source`


## Sample output

One object per listing. Here is a real example from a production run:

```json
{
  "jobId": "4a9d0bda98b5aefe3b6b7faa1bf532c944bde53c6da104a161efcff0d1b332fa",
  "title": "python后端开发工程师",
  "company": "北京阿提拉科技有限公司",
  "companyId": 14764600,
  "companyLogo": "https://storage-public.zhaopin.cn/CompanyLogo/20150804/150542FB272A44B1A7477DC659096ACE.jpg",
  "companySize": "300-499人",
  "companyUrl": "http://company.zhaopin.com/CZ147646000.htm",
  "companyDescription": "阿提拉基本介绍 由来：阿提拉(ATTILA)是一位雄心壮志，才智超群，高超外交手腕，傲居全人类，持战神之剑，纵横无敌，握\"上帝之鞭\"的东方人，阿提拉建立的匈奴帝国是欧亚大草原上最辉煌的帝国。从勒内格鲁塞的不朽著作『草原帝国』中第一次接触到阿提拉，便被阿提拉深深吸引。2006年，开创以阿提拉为名字的科技公司，公司将借阿提拉之神剑，望最辉煌的成绩写入历史。 北京…",
  "industry": "计算机软件",
  "financingStage": "未融资",
  "location": "北京",
  "district": "西城"
}
```

*Truncated — full records contain 34 fields. See Output fields for the complete schema.*


**[Try Zhaopin Scraper - China Job Listings now — $5 free credit, no credit card →](https://apify.com/blackfalcondata/zhaopin-scraper?fpr=1h3gvi)**


## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.002 |

See the [actor on Apify](https://apify.com/blackfalcondata/zhaopin-scraper?fpr=1h3gvi) for current pricing.

---

## Related products by Black Falcon Data






- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Naukri Scraper](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) — India's largest job portal

---


## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---

## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. [Sign up free](https://console.apify.com/sign-up?fpr=1h3gvi) — $5 credit included
2. Open the actor and paste your input
3. Click Start — results download as JSON, CSV, or Excel

Need more volume? [See pricing](https://apify.com/pricing?fpr=1h3gvi).

---

---

*Last updated: 2026 03*
