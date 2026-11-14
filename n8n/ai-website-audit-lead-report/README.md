# AI Website Audit & Lead Outreach Report

**Platform:** n8n **Category:** Lead Generation / AI Sales Outreach

## Overview

Cold outreach converts better when it opens with real value. This workflow audits each lead's website with AI, finds missing automation opportunities (chat, online booking, lead capture), and produces a branded HTML/PDF report plus a personalized 3-email follow-up sequence.

## How It Works

1. Trigger — every 15 minutes, reads leads with status `pending` from Google Sheets and processes them one at a time with a polite delay.
2. Creates (or reuses) a Google Drive folder for each lead.
3. Scrapes the homepage and contact page, detects signals (chat widget, booking, forms), and falls back to Jina Reader plus a screenshot with GPT-4o Vision for JavaScript-heavy SPA sites.
4. GPT-4o-mini runs the audit using the detected signals as confirmed facts, and the output is parsed and validated.
5. Builds an HTML report with an ROI section, converts it to PDF (PDFShift), and uploads the report, raw data, and scraped content to Drive.
6. Generates a 3-step personalized email sequence and updates the sheet (`audited` or `low_signal`).

## Tech Stack

n8n, OpenAI (GPT-4o-mini, GPT-4o Vision), Google Sheets, Google Drive, Jina Reader, thum.io, PDFShift

## Key Features

- Signal detection before the AI step, so the model can't contradict facts found on the page
- SPA fallback using rendered markdown and a screenshot for vision analysis
- Low-signal guard that skips sites with too little content to audit
- Per-lead Drive folder with the report (HTML + PDF), audit JSON, and email copy
- Batch processing with throttling to stay polite to target sites

## Setup

1. Import `workflow.json`.
2. Connect credentials: OpenAI, Google Sheets, Google Drive.
3. Replace placeholders: `{{SHEET_ID}}`, `{{DRIVE_PARENT_FOLDER_ID}}`, `{{PDFSHIFT_API_KEY}}`, `{{BOOKING_SLUG}}`.
4. Sheet tab `Leads` needs at least: `website`, `company_name`, `contact_name`, `status`.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, phone numbers, and email addresses shown here (e.g. "Northwind Digital Solutions", "Alex Morgan") are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
