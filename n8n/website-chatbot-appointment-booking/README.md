# AI Website Chatbot with Appointment Booking

**Platform:** n8n **Category:** AI Chatbot / Appointment Booking

## Overview

Website visitors leave when nobody answers their questions, and many are ready to book a consultation right away. This multi-agent chatbot answers FAQs about a real estate brokerage, collects lead details, and books appointments, while keeping context across visits.

## How It Works

1. Trigger — the website chat widget sends each message and session ID to a webhook.
2. Prior chat history is loaded from the site's API and formatted as a transcript.
3. A **Router Agent** classifies the user's intent as `BOOK` or `CONVERSATION`.
4. **Conversation Agent** (Gemini) answers questions about the brokerage, listings, and site features, and nudges the visitor toward booking.
5. **Booking Agent** (GPT-4o-mini) collects name, then email, then phone, validates each one, and shares the booking link. Cal.com tools can fetch free slots and create bookings.
6. Both agents return structured lead data (name, email, phone, address), which is sent back to the website through Respond to Webhook.

## Tech Stack

n8n, OpenAI (GPT-4o-mini), Google Gemini, Cal.com API, Custom REST API (chat history)

## Key Features

- Multi-agent design: an intent router plus specialized conversation and booking agents
- Persistent memory across sessions: returning visitors are never re-greeted or re-asked
- Step-by-step lead capture with email and phone validation
- Structured data extraction on every turn, so no lead details are lost
- Cal.com availability and booking tools available to the agent

## Setup

1. Import `workflow.json`.
2. Connect credentials: OpenAI, Google Gemini.
3. Replace placeholders: `{{CAL_API_KEY}}`, `{{CAL_EVENT_TYPE_ID}}`, `{{CALENDLY_SLUG}}`, and the `contoso-realty.example.com` chat-history API URL.
4. Edit the business details in the Conversation Agent prompt to match your company.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, addresses, phone numbers, and email addresses shown here (e.g. "Contoso Realty") are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
