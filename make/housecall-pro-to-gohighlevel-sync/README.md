# HouseCall Pro to GoHighLevel Sync

**Platform:** Make.com **Category:** CRM Sync / Field Service

## Overview

Field-service companies often run jobs in HouseCall Pro and do marketing and sales in GoHighLevel, which leaves customer and pipeline data out of sync. This scenario listens to HouseCall Pro webhooks and keeps GoHighLevel contacts and opportunities updated in real time across the whole customer lifecycle.

## How It Works

1. Trigger — a custom webhook receives HouseCall Pro events.
2. A router splits the events into 11 routes: lead created/converted, customer created/updated, estimate sent/approved, job created/scheduled/completed/canceled, and invoice paid.
3. Each route searches GoHighLevel for the contact by phone, name, and email (HouseCall Pro job details are fetched for invoices).
4. A second router decides whether the contact exists. If not, it creates the contact; if it does, it updates it.
5. Opportunities are then listed and created or moved to the right pipeline stage, with status (open, won, or lost) matching the event.
6. Error handlers on the CRM modules keep the scenario running when a single record fails.

## Tech Stack

Make.com, HouseCall Pro, GoHighLevel

## Key Features

- One webhook covers 11 lifecycle events
- Upsert logic (search, then create or update) for both contacts and opportunities
- Automatic pipeline-stage mapping from job and estimate status
- Error-handler routes so a single bad record doesn't stop the sync

## Setup

1. Import `blueprint.json` into a new Make scenario.
2. Connect: GoHighLevel (OAuth) and HouseCall Pro. Then create the webhook and add its URL in HouseCall Pro.
3. Replace placeholders: `{{GHL_CONNECTION_ID}}`, `{{HCP_CONNECTION_ID}}`, `{{HOOK_ID}}`, `{{PIPELINE_ID_n}}`, `{{STAGE_ID_n}}`. `{{CONTACT_ID_n}}` and `{{OPPORTUNITY_ID_n}}` were test records, so map them to the search results instead.
4. **Note:** the follow-up branch for each event (contact and opportunity upsert) is stored as a separate module group in the blueprint. After import, drag each group onto the end of its matching router route. The filter labels show which event each one belongs to.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, phone numbers, and email addresses that appear in this scenario are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
