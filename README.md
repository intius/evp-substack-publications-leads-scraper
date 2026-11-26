# Substack publications Scraper & Unofficial API (Python, Node.js, MCP)

[Run Substack Publications, Authors & Sponsorship Leads on Apify](https://apify.com/evpp/substack-publications-leads) to export Substack publications data as clean JSON, CSV, Excel, or an API feed. This repository is a developer quick-start kit with working Python and Node.js clients, an MCP configuration, a real sample dataset, and an n8n automation template.

[![Run on Apify](https://img.shields.io/badge/Run%20on-Apify-orange)](https://apify.com/evpp/substack-publications-leads)

[Open the documentation and crawlable sample explorer](https://intius.github.io/evp-labs-data-extractors/actors/substack-publications-leads/) for quick inputs, integration links, real sample rows, and ready-made task examples.

## Why use this Substack publications scraper?

- Export Substack publications data without building or maintaining a custom scraper
- Get flat, schema documented JSON ready for analytics, lead generation, market research, and AI agents
- Run manually, on a schedule, through the Apify API, or through MCP compatible AI tools
- Use the included 25+ row sample dataset to prototype before running the live Actor

Built for B2B lead generation teams, market researchers, growth operators, AI workflow builders.

## Quick start on Apify

Open [https://apify.com/evpp/substack-publications-leads](https://apify.com/evpp/substack-publications-leads) and use this input:

```json
{
  "categoryId": "4",
  "paidOnly": false,
  "bestsellerOnly": false,
  "maxItems": 12
}
```

## Python

```bash
pip install -r requirements.txt
export APIFY_TOKEN=your_apify_token
python python/run.py
```

On Windows PowerShell, use `$env:APIFY_TOKEN="your_apify_token"` instead of `export`.

## Node.js

```bash
npm install
export APIFY_TOKEN=your_apify_token
node node/run.mjs
```

## MCP and AI agents

Add the hosted Apify MCP server from `mcp-config.json` to your MCP client:

```json
{
  "mcpServers": {
    "apify": {
      "type": "http",
      "url": "https://mcp.apify.com/?tools=evpp/substack-publications-leads"
    }
  }
}
```

Then ask your agent to run `evpp/substack-publications-leads`, inspect the output schema, or export the latest dataset. The direct MCP URL is `https://mcp.apify.com/?tools=evpp/substack-publications-leads`.

For multi-source public data agents, use the [EVP Public Data MCP server](https://github.com/intius/evp-public-data-mcp). It is published in the Official MCP Registry as `io.github.intius/evp-public-data-mcp` and is also available as a one-click Claude Desktop MCPB release.

## n8n automation

Import `n8n-workflow.json` into n8n, select your Apify credential, replace the webhook placeholder, and activate the schedule. The workflow runs the Actor every morning and posts fresh dataset items to your webhook.

## Output schema

| Field | Type | Description |
|---|---|---|
| `publicationId` | string | Substack publication ID |
| `rank` | integer | Leaderboard rank |
| `name` | string | Publication name |
| `subdomain` | string | Substack subdomain |
| `url` | string | Publication home URL |
| `customDomain` | string | Custom domain when configured |
| `description` | string | Publication description |
| `authorName` | string | Primary author display name |
| `authorId` | string | Primary author ID |
| `subscriberCount` | integer | Displayed or estimated subscriber count |
| `subscriberCountLabel` | string | Subscriber count badge |
| `paidSubscriberBand` | string | Paid subscriber band |
| `bestsellerTier` | integer | Bestseller badge tier floor |
| `isBestseller` | boolean | True when bestseller badge present |
| `paidEnabled` | boolean | True when paid subscriptions enabled |
| `monthlyPriceUsd` | number | Monthly price when available |
| `yearlyPriceUsd` | number | Yearly price when available |
| `logoUrl` | string | Publication logo URL |
| `createdAt` | string | Publication creation timestamp |
| `categoryId` | string | Category used |

## Real sample output

The first sanitized row from the included sample dataset:

```json
{
  "publicationId": "817132",
  "rank": 1,
  "name": "ByteByteGo Newsletter",
  "subdomain": "bytebytego",
  "url": "https://blog.bytebytego.com",
  "customDomain": "blog.bytebytego.com",
  "description": "Explain complex systems with simple terms, from the authors of the best-selling system design book series. Join over 1,000,000 friendly readers.",
  "authorName": "Alex Xu",
  "authorId": "22329494",
  "authorHandle": "bytebytego",
  "bestsellerTier": 0,
  "isBestseller": false,
  "paidEnabled": true,
  "monthlyPriceUsd": 15,
  "yearlyPriceUsd": 150,
  "logoUrl": "https://substackcdn.com/image/fetch/$s_!1eXV!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2F8a5609ae-1239-4400-9491-6010a15c4d60_504x504.png",
  "createdAt": "2022-03-27T03:36:45.845Z",
  "categoryId": "4"
}
```

## Files in this kit

| File | Purpose |
|---|---|
| `python/run.py` | Working Python Apify API example |
| `node/run.mjs` | Working Node.js Apify API example |
| `mcp-config.json` | MCP server configuration for AI agents |
| `sample-output.json` | First five sanitized sample rows |
| `dataset-snapshot.csv` | 25+ row evaluation snapshot |
| `DATASET_CARD.md` | Dataset documentation and provenance |
| `n8n-workflow.json` | Scheduled n8n automation template |

## Fresh data

This repository contains a static evaluation sample. For current data, run the live Actor: https://apify.com/evpp/substack-publications-leads

## Responsible use

The Actor reads public data from `substack.com`. Review the source site's terms and applicable privacy rules before production use.
