# Wellfound Startup Jobs & Tech Talent Scraper (AngelList)

[![Apify Actor](https://img.shields.io/badge/Apify-Actor%20Store-orange?logo=apify)](https://apify.com/moneygain/wellfound-jobs-scraper)
[![Python Version](https://img.shields.io/badge/Python-3.10%20%7C%203.11%20%7C%203.12-blue?logo=python)](https://github.com/Archibald322/wellfound-jobs-scraper)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Live Apify Store Actor:** [https://apify.com/moneygain/wellfound-jobs-scraper](https://apify.com/moneygain/wellfound-jobs-scraper)

This repository provides an open-source Python runner and documentation for **[Wellfound Startup Jobs & Tech Talent Scraper (AngelList)](https://apify.com/moneygain/wellfound-jobs-scraper)**.

---

## ⚡ Quickstart

### Option 1: Run in Cloud (No Code)
Launch directly from your browser via the Apify Store console:
👉 **[Open Wellfound Startup Jobs & Tech Talent Scraper (AngelList) on Apify Store](https://apify.com/moneygain/wellfound-jobs-scraper)**

### Option 2: Run via Python SDK
```bash
git clone https://github.com/Archibald322/wellfound-jobs-scraper.git
cd wellfound-jobs-scraper
pip install -r requirements.txt
export APIFY_TOKEN="your_apify_token_here"
python run.py
```

---

# 🦄 Wellfound (AngelList Talent) Startup Jobs Scraper

**Scrape Wellfound startup jobs data to JSON, CSV, or Excel in seconds without browser overhead.** Extract high-growth startup vacancies, engineering roles, founder/executive hiring, verified compensation salary brackets, equity percentages, tech stacks, and direct candidate application URLs from **Wellfound.com** (formerly AngelList Talent) — the world's leading startup recruiting platform.

Designed for AI recruiting platforms, HR tech innovators, technical headhunters, candidate sourcing agencies, venture funds, and autonomous AI agents. Built with ultra-fast direct Apollo cache / Next.js SSR extraction, **zero browser overhead**, and **100% Pay-Per-Event (PPE) pricing** — you only pay for verified job postings delivered.

---

## ⚡ Speed & Value Comparison

| Feature | Our Lightweight Wellfound Scraper | Heavy Browser Scrapers (Playwright / Puppeteer) |
|---|---|---|
| **Memory Usage** | **128 MB – 256 MB** | 2 GB – 4 GB |
| **Startup Fee** | **$0.00 (Zero Start Fee)** | $0.05 – $0.10 per run |
| **Extraction Speed** | **0.3s – 0.8s per page** | 12s – 25s per page |
| **Pricing Model** | **Pay-Per-Event ($0.006 / job)** | Expensive Monthly Flat Fee ($40–$60/mo) |
| **Data Enrichment** | **Clean salary bounds, equity ranges & tech tags** | Broken unstructured card text |
| **Anti-Bot Reliability** | **High-speed Chrome TLS fingerprinting** | Frequent bot challenge blocks |

---

## 📦 Sample JSON Output

```json
{
  "id": "2984120",
  "title": "Staff Full Stack Engineer (AI Products)",
  "company": "Perplexity AI",
  "companySlug": "perplexity-ai",
  "companyWebsite": "https://perplexity.ai",
  "companyLogo": "https://photos.wellfound.com/startups/i/perplexity.png",
  "location": "San Francisco, CA",
  "isRemote": true,
  "salaryRange": "$190k - $250k",
  "salaryMin": 190000,
  "salaryMax": 250000,
  "currency": "USD",
  "equity": "0.1% - 0.25%",
  "experience": "5+ years",
  "skills": ["Python", "TypeScript", "React", "PyTorch", "FastAPI"],
  "applyUrl": "https://wellfound.com/jobs/2984120-staff-full-stack-engineer",
  "scrapedAt": "2026-11-17T11:00:00.000000+00:00"
}
```

---

## 🎯 Use Cases & Business Value

- **Tech Talent Sourcing & Recruiting**: Source top-tier candidates by monitoring new engineering, product, and AI leadership roles as soon as venture-backed startups post them.
- **Compensation & Equity Benchmarking**: Benchmark cash salaries and equity compensation packages across Seed, Series A, Series B, and late-stage tech startups.
- **Automated AI Job Boards**: Power specialized niche job boards (e.g. AI Engineers, Remote Startups, YC Alumni Hiring) with daily automated feeds.
- **Venture Capital Deal Sourcing**: Identify early stealth startups aggressively ramping up hiring before formal funding announcements.

---

## ⚙️ Input Parameters

| Parameter | Type | Default | Description |
|---|---|---|---|
| `startUrls` | Array | `["https://wellfound.com/jobs"]` | Direct Wellfound directory, role, or location URLs to scrape. |
| `role` | String | `"all"` | Role filter shortcut (`software-engineer`, `product-manager`, `data-scientist`, `sales`, `marketing`, `designer`). |
| `location` | String | `""` | Optional location slug (e.g. `san-francisco`, `new-york-city`, `london`). Leave empty for all. |
| `onlyRemote` | Boolean | `false` | When `true`, filters strictly for 100% remote positions. |
| `maxItems` | Integer | `10` | Maximum number of verified startup job records to scrape (Prefilled for instant 5-second test runs). |

---

## 🤖 Integrate with AI Agents & No-Code Platforms

### 1. Claude Desktop & Cursor via Apify MCP Server
Connect this actor directly to Cursor, Claude Desktop, Windsurf, or LangChain agents using the official Apify MCP Server:

```json
{
  "mcpServers": {
    "apify": {
      "command": "npx",
      "args": ["-y", "@apify/mcp-server"],
      "env": {
        "APIFY_TOKEN": "YOUR_APIFY_API_TOKEN"
      }
    }
  }
}
```
*Prompt example:*
> *"Find 10 remote AI engineer jobs on Wellfound offering at least $180k salary and equity using wellfound-jobs-scraper."*

### 2. n8n Automation Workflows
1. Add an **Apify Node** or **HTTP Request Node** in your n8n workflow.
2. Select `Run an Actor` with Actor ID: `moneygain/wellfound-jobs-scraper`.
3. Route new startup roles into Airtable, Notion, or your recruiting CRM.

### 3. Make.com (Integromat)
1. Add the **Apify Module** ➔ `Run Actor and get dataset items`.
2. Automatically email qualified startup vacancies to registered job seekers.

### 4. Clay.com Enrichment
1. Use the **Apify Integration** inside Clay.
2. Enrich target venture companies with their active open engineering roles and hiring velocity.

### 5. Python SDK Integration
```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_API_TOKEN")
run_input = {
    "role": "software-engineer",
    "onlyRemote": True,
    "maxItems": 20
}
run = client.actor("moneygain/wellfound-jobs-scraper").call(run_input=run_input)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"{item['company']} | {item['title']} | {item['salaryRange']} -> {item['applyUrl']}")
```

---

## ❓ Frequently Asked Questions (SEO FAQ)

### Q1: Is it legal to scrape data from Wellfound?
**Yes.** All job postings and company overviews extracted by this actor are publicly indexable career advertisements published by startups to recruit applicants. The actor accesses only public directory pages without bypassing private candidate applications or employer logins.

### Q2: How much does it cost to scrape 1,000 startup jobs?
Under our **Pay-Per-Event (PPE)** pricing model, you only pay **$0.006 per verified job posting**, so 1,000 jobs cost **$6.00**. There are zero startup fees, zero compute charges, and subscribers on Apify Bronze/Silver/Gold tiers receive automatic volume discounts up to 20% ($4.80 per 1,000).

### Q3: Can I export Wellfound data to Excel, CSV, or Google Sheets?
**Yes.** Apify provides 1-click export options in JSON, CSV, XML, Excel (.xlsx), and HTML table formats. You can also sync datasets automatically to Google Sheets via webhooks or Make/n8n.

### Q4: Do I need proxies to scrape Wellfound?
**No.** Our optimized HTTP engine uses Chrome TLS session impersonation, allowing seamless extraction without heavy residential proxy costs.

### Q5: Does this scraper extract equity and salary numbers?
**Yes.** Where disclosed by the hiring startup, our actor extracts the exact minimum and maximum salary figures (`salaryMin`, `salaryMax`), the currency code, and the equity ownership range (`equity`).

---

## 🔗 Explore More High-Speed B2B Scrapers & Enrichers by Our Team

Supercharge your data pipelines, sales outreach, and AI agents with our suite of lightweight, Pay-Per-Event scrapers:

| Scraper | Segment / Target | Key Value | Store Link |
|---|---|---|---|
| **TrustMRR SaaS Startups Scraper** | SaaS Revenue & M&A Data | Stripe-verified MRR, 30d revenue, active subscriptions & founder contacts | [Open on Apify Store](https://apify.com/moneygain/trustmrr-startups-scraper) |
| **Ashby ATS Tech Jobs Scraper** | Next-Gen ATS Career Feeds | Direct ATS API extraction, salaries, departments & remote flags | [Open on Apify Store](https://apify.com/moneygain/ashby-jobs-scraper) |
| **Clutch B2B Agencies Scraper** | B2B Agencies & IT Services | Decoded direct websites, review ratings, hourly rates & service focus | [Open on Apify Store](https://apify.com/moneygain/clutch-agencies-scraper) |
| **Wellfound Startup Talent Scraper** | AI & Tech Startup Jobs | Startup jobs, compensation ranges, equity & tech stack tags | [Open on Apify Store](https://apify.com/moneygain/wellfound-jobs-scraper) |
| **TheProtocol.it IT Careers Scraper** | IT Salaries & Vacancies | Verified salary brackets, tech requirements & seniority levels | [Open on Apify Store](https://apify.com/moneygain/theprotocol-scraper) |
| **Bulldogjob Tech Recruitment Scraper** | Tech Recruitment Feeds | B2B/Employment rates, tech tags & recruiter contacts | [Open on Apify Store](https://apify.com/moneygain/bulldogjob-scraper) |
