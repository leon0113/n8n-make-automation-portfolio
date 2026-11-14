# AI Voice Outbound Lead Dispatcher (Retell AI)

**Platform:** n8n **Category:** AI Voice / Lead Management

## Overview

New leads go cold fast if nobody calls them. This workflow reads queued leads from Google Sheets and has a Retell AI voice agent call each one automatically, passing the lead's name into the conversation. It's part 1 of a two-workflow AI calling system. Call results and bookings are handled by [AI Voice Call Handler](../ai-voice-call-handler-ghl-booking/).

## How It Works

1. Trigger — manual run (or the included schedule trigger) reads the lead list from Google Sheets.
2. Leads that are not yet queued or called are filtered, and one lead is picked per run.
3. The lead's row is marked `In_progress` to prevent double-dialing.
4. After a short wait, the Retell API places the outbound call from your agent's number, with the customer's name as a dynamic variable.
5. Call events (started, analyzed) are sent by Retell to the companion Call Handler workflow, which updates the sheet and the CRM.

## Tech Stack

n8n, Retell AI, Google Sheets (an alternative Vapi call node is included)

## Key Features

- Sheet-driven call queue with status locking to avoid duplicate calls
- One lead per run, so it's safe to put on a schedule
- Personalized calls through Retell dynamic variables
- Provider-agnostic: a ready-made Vapi request node is included as an alternative

## Setup

1. Import `workflow.json`.
2. Connect credentials: Google Sheets.
3. Replace placeholders: `{{SHEET_ID}}`, `{{RETELL_API_KEY}}`, `{{RETELL_AGENT_ID}}`, `{{RETELL_FROM_NUMBER}}` (and `{{VAPI_*}}` if you use Vapi).
4. Sheet columns: `lead_id`, `first_name`, `last_name`, `email`, `phone_e164`, `city`, `service_type`, `timezone`, `status`.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, phone numbers, and email addresses that appear in this workflow are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
