# AI SEO Blog Writer & Auto-Publisher

**Platform:** n8n **Category:** AI Content / SEO

## Overview

Publishing SEO content every week needs a writer, an editor, and someone to source images. This workflow pulls the next target keyword from a website's API, writes a long-form SEO article with GPT-4o, adds meta tags and a stock image, and saves it as a draft blog post for human review.

## How It Works

1. Trigger — weekly cron (Mondays 9 AM) or an on-demand "Run Now" webhook from an admin dashboard.
2. Fetches the next pending keyword (with LSI keywords, intent, and target word count) from the site's API and stops if there's nothing to do.
3. GPT-4o writes an E-E-A-T-focused HTML article, and GPT-4o-mini generates the SEO title, meta description, slug, and image search query.
4. Pexels returns a matching landscape image, and the highest-resolution URL is picked as the thumbnail.
5. The payload is cleaned (markdown fences stripped) and posted as a **draft** blog through the site's API.
6. The keyword is marked as completed and Slack receives a review notification.

## Tech Stack

n8n, OpenAI (GPT-4o, GPT-4o-mini), Pexels API, Custom REST API, Slack

## Key Features

- Keyword queue driven by an API, with a "no work" guard
- Two-model setup: a stronger model writes the article, a cheaper model handles metadata
- Defensive output cleanup (markdown fences, BOM, stray quotes) before publishing
- Human-in-the-loop: posts land as drafts and a Slack alert links to the review dashboard

## Setup

1. Import `workflow.json`.
2. Connect credentials: OpenAI, Slack.
3. Replace placeholders: `{{BLOG_API_KEY}}`, `{{PEXELS_API_KEY}}`, `{{SLACK_TEAM_ID}}`, `{{CHANNEL_ID}}`, and the `contoso-realty.example.com` base URL with your own blog API.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, phone numbers, and email addresses shown here (e.g. "Contoso Realty") are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
