# Instagram AI Sales Agent (Multi-Agent, Voice & Image, Mercado Pago)

**Platform:** n8n **Category:** AI Sales Agent / E-commerce

## Overview

Clothing stores that sell through Instagram DMs lose sales when replies are slow. This multi-agent sales assistant answers in Spanish or English, understands text, voice notes, and photos, recommends products from a live catalog, builds the order, and sends a Mercado Pago payment link. Payment status is then synced back to the order sheet automatically.

## How It Works

1. Trigger — a messaging webhook receives the DM. A switch routes it by type: text, voice (Whisper transcription), or image (GPT-4o Vision description).
2. Messages are buffered in Redis for a few seconds, so a burst of short messages is answered as one.
3. An **Orchestration Agent** classifies the intent and routes it to the matching specialist: **Catalog**, **Payment/Order**, **General Info**, or **Conversational**. Each has its own memory.
4. The Catalog Agent searches the Google Sheets product catalog and returns structured JSON. Product cards (with images) are sent back one by one.
5. When the order is ready, a Format Agent converts it to JSON. A Mercado Pago checkout link is created and sent, and the order is saved to Sheets.
6. A second webhook receives Mercado Pago payment notifications, checks the status, updates the order as approved or rejected, and messages the customer.

## Tech Stack

n8n, OpenAI (GPT-4o-mini, GPT-4.1-mini, GPT-4o Vision, Whisper), Redis, Google Sheets, Mercado Pago API

## Key Features

- Multi-agent architecture: an orchestrator plus 4 specialist agents with separate memories
- Multi-modal input: text, voice notes, and product photos
- Redis message buffering to handle rapid multi-message DMs naturally
- End-to-end checkout: cart, payment link, and payment-status webhook that updates the order sheet
- Bilingual replies (Spanish/English) that match the customer's language

## Setup

1. Import `workflow.json`.
2. Connect credentials: OpenAI, Google Sheets, Redis, Header Auth (for your messaging API).
3. Replace placeholders: `{{SHEET_ID}}`, `{{MERCADOPAGO_ACCESS_TOKEN}}`, `{{MERCADOPAGO_PUBLIC_KEY}}`, `{{MERCADOPAGO_TEST_ACCESS_TOKEN}}`, `{{WEBHOOK_PATH}}`. Map `{{PAYMENT_ID}}` to the ID from the Mercado Pago notification.
4. Set the URL of the **Send Message** nodes to your Instagram messaging endpoint (Meta Graph API or your DM platform), and point that platform's webhook to this workflow.
5. Sheet tabs: a product catalog tab and an `Orders` tab (including `Phone` and `Payment Status` columns).

> Built on a marketplace sales-agent template and customized.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, store locations, phone numbers, and email addresses shown here (e.g. "Fabrikam Apparel") are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
