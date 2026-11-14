# AI Voice Call Handler: GoHighLevel Booking & CRM Sync (Retell AI)

**Platform:** n8n **Category:** AI Voice / CRM Sync / Appointment Booking

## Overview

An AI phone agent is only useful if it can check real availability, book real appointments, and log every call in the CRM. This webhook is the backend of a Retell AI voice agent. It answers live function calls during the conversation and syncs results to GoHighLevel after the call ends. It's part 2 of the system that starts with [AI Voice Outbound Lead Dispatcher](../ai-voice-outbound-lead-dispatcher/).

## How It Works

1. Trigger — a single webhook receives Retell events and live tool calls, and a switch routes them by type.
2. **`Get_Availability`** — fetches GoHighLevel calendar free slots for the requested day and returns them as speakable text ("Available times are 10:00 AM, 11:30 AM … Eastern Time").
3. **`schedule_appointment`** — finds the contact by phone (or creates it), matches the spoken time to a real free slot, books the appointment, then creates an opportunity in the "New Lead" pipeline stage. The result is returned to the agent mid-call.
4. **`call_analyzed`** — marks the lead's row in Google Sheets as `Call ended`, then finds the contact in GoHighLevel by phone.
5. Adds the AI call summary as a contact note, updates email and address from Retell's post-call analysis, and checks for an existing opportunity. (`call_started` has a route reserved for future use.)

## Tech Stack

n8n, Retell AI, GoHighLevel API (Calendars, Contacts, Opportunities, Notes), Google Sheets

## Key Features

- Real-time function calling: the voice agent checks availability and books during the live call
- Upsert logic: search the contact by phone, create it if missing, then book
- Every appointment is automatically linked to a pipeline opportunity
- Post-call enrichment: AI summary note plus extracted email and address
- Structured success and error responses so the agent can recover gracefully

## Setup

1. Import `workflow.json`.
2. Connect credentials: Google Sheets.
3. Replace placeholders: `{{GHL_API_KEY}}`, `{{LOCATION_ID}}`, `{{CALENDAR_ID}}`, `{{FREE_SLOTS_CALENDAR_ID}}`, `{{PIPELINE_ID}}`, `{{SHEET_ID}}`. (`{{TEST_CONTACT_ID}}` is only used by disabled test nodes.)
4. In Retell, point the agent webhook and the custom functions (`Get_Availability`, `schedule_appointment`) to the `voice-call-events` path, and add post-call analysis fields `Email`, `StreetAddress`, `City`, `State`, `Postal Code`.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, phone numbers, and email addresses that appear in this workflow are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
