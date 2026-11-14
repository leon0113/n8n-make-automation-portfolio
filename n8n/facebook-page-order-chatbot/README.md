# Facebook Page AI Sales & Order Chatbot

**Platform:** n8n **Category:** AI Chatbot / E-commerce

## Overview

Small wholesale businesses get dozens of Messenger questions a day about prices, stock, and orders. This bilingual (Bangla/English) AI page admin answers from a live product sheet and records confirmed orders directly into Google Sheets.

## How It Works

1. Trigger — the Messenger webhook receives incoming page messages and responds immediately so Meta doesn't retry.
2. A filter keeps only real user text messages and drops echoes and delivery events.
3. A Gemini-powered agent with per-sender memory handles the conversation, using business rules defined in the prompt.
4. The `Get_Products` tool reads name, description, price, features, and stock from the Products sheet.
5. Once the customer confirms, the `Save_Order` tool appends the order (ID, name, phone, address, product, amount) to the Orders sheet.
6. The reply is sent back to the customer through the Graph API.

## Tech Stack

n8n, Google Gemini, Google Sheets, Meta Graph API (Messenger)

## Key Features

- Bilingual: replies fully in Bangla or English to match the customer
- Product answers come only from the sheet data, so prices and stock are never made up
- Order capture with confirmation and auto-generated order IDs
- Per-customer conversation memory keyed by Messenger sender ID

## Setup

1. Import `workflow.json`.
2. Connect credentials: Google Gemini, Google Sheets.
3. Replace placeholders: `{{FACEBOOK_PAGE_ACCESS_TOKEN}}`, `{{SHEET_ID}}`.
4. Create two sheet tabs: `Products` (Product Name, Product Description, Product Price, Key Features, Product Stock) and `Orders` (Order Id, Customer Name, Customer Phone, Customer Address, Order Date, Order Product, Order Amount).
5. Point your Meta app's Messenger webhook to the `facebook-bot` path.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, addresses, phone numbers, and email addresses shown here (e.g. "Tailspin Apparel") are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
