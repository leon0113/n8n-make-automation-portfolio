# Apify Lead Scraper with Email & Phone Validation

**Platform:** n8n **Category:** Lead Generation / Data Enrichment

## Overview

Scraped lead lists are often full of dead numbers and missing emails. This workflow scrapes local businesses from Google Maps through Apify, finds an email on each business's website, validates the phone line type, scores every lead, and saves a call-ready list to Google Sheets.

## How It Works

1. Trigger — a webhook receives the search terms, location, lead count, and API config (with safe defaults).
2. Apify's Google Maps extractor returns business listings, which are cleaned and normalized.
3. If a lead has a website, the HTML is fetched and an email is extracted (mailto first, then text patterns) and classified as direct or generic.
4. Phone numbers are normalized to E.164 and validated through NumLookup (mobile, landline, or VoIP).
5. Each lead is scored by rating, review count, website, email, and mobile line, then tagged with SMS eligibility and priority.
6. Results are merged, appended to Google Sheets, and returned in the webhook response.

## Tech Stack

n8n, Apify (Google Maps Extractor), NumLookup API, Google Sheets

## Key Features

- One webhook call runs the whole pipeline: scrape, enrich, validate, score, save
- Email extraction filters out junk matches such as asset filenames and framework emails
- Line-type detection flags SMS-capable mobile numbers for outreach
- Lead scoring and priority tagging for call-list ordering
- Config-driven: actor, tokens, and limits can be passed per request

## Setup

1. Import `workflow.json`.
2. Connect credentials: Google Sheets.
3. Replace placeholders: `{{SHEET_ID}}`, `{{NUMLOOKUP_API_KEY}}` (or pass it in the request body). Send your Apify token in `workflowConfig.apify.token`.
4. Example request body: `{ "searchStringsArray": ["HVAC contractor"], "locationQuery": "Austin, Texas", "maxLeads": 10 }`.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, phone numbers, and email addresses that appear in this workflow are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
