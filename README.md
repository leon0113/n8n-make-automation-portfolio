# n8n & Make.com Automation Portfolio

Hi, I'm **Tahjib Hossain (Leon)**, an automation developer who builds AI agents, lead-capture flows, CRM integrations, and content pipelines.
This repository collects production-style workflows I've built in **n8n** and **Make.com**. Every workflow can be imported and comes with a short README.

## n8n Workflows

| Workflow | What it does | Tools |
| --- | --- | --- |
| [Facebook & Instagram DM + Comment AI Auto-Reply](n8n/facebook-dm-comment-ai-auto-reply/) | Replies to comments and DMs with AI, qualifies leads, and logs them to a CRM | OpenAI, Gemini, Meta Graph API, Supabase, Google Docs |
| [AI Long-Form Video Generator (Veo 3.1)](n8n/ai-long-form-video-veo/) | Turns a topic into a 30-second, 4-scene AI video ad with script, SEO metadata and subtitles | OpenAI, Vertex AI (Veo 3.1, Gemini), Google Sheets, Google Drive |
| [AI Carousel Content Generator & Auto-Publisher](n8n/ai-carousel-content-autopublish/) | Writes a carousel with GPT, generates an AI image per slide and publishes it to Instagram, LinkedIn and Facebook | OpenAI, Vertex AI (Gemini), Google Sheets, Google Drive, Blotato |
| [AI SEO Blog Writer & Auto-Publisher](n8n/ai-seo-blog-autopublish/) | Writes weekly SEO articles from a keyword queue, adds meta and images, and saves them as drafts for review | OpenAI, Pexels, REST API, Slack |
| [AI Website Audit & Lead Outreach Report](n8n/ai-website-audit-lead-report/) | Audits lead websites with AI, builds an HTML/PDF report and writes a personalized email sequence | OpenAI, Google Sheets, Google Drive, Jina Reader, PDFShift |
| [HeyGen AI Avatar Video Auto-Publisher](n8n/heygen-avatar-video-autopublish-with-approval/) | Writes a script, gets Slack approval, renders a HeyGen avatar video and posts it to 4 platforms | OpenAI, HeyGen, Slack, Google Sheets, Google Drive, Blotato |
| [Apify Lead Scraper with Email & Phone Validation](n8n/apify-lead-scraper-email-phone-validation/) | Scrapes Google Maps leads, finds emails, validates phone line types, scores leads and saves them to Sheets | Apify, NumLookup, Google Sheets |
| [Gmail to GoHighLevel AI Contact Sync](n8n/gmail-to-gohighlevel-contact-sync/) | Extracts lead details from incoming emails with AI and creates or updates GoHighLevel contacts | Gmail, OpenAI, GoHighLevel |
| [AI Website Chatbot with Appointment Booking](n8n/website-chatbot-appointment-booking/) | Multi-agent website chatbot that answers FAQs, captures leads and books appointments with memory | OpenAI, Gemini, Cal.com, REST API |
| [Facebook Page AI Sales & Order Chatbot](n8n/facebook-page-order-chatbot/) | Bilingual Messenger bot that answers from a live product sheet and saves confirmed orders | Gemini, Google Sheets, Meta Graph API |
| [AI UGC Product Ad Generator (Nano Banana + Veo 3.1)](n8n/ai-ugc-image-to-video-nanobanana-veo/) | Turns a product photo into a UGC-style lifestyle image and a short AI video ad | OpenAI, Vertex AI (Nano Banana, Veo 3.1), Google Sheets, Google Drive |
| [WhatsApp Client Task Intake to ClickUp & Slack](n8n/whatsapp-task-intake-clickup/) | AI agent turns client WhatsApp messages (text, voice, images, docs) into assigned ClickUp tasks | WhatsApp Cloud API, OpenAI, ClickUp, Slack, Google Sheets |
| [AI Voice Outbound Lead Dispatcher (Retell AI)](n8n/ai-voice-outbound-lead-dispatcher/) | Calls queued leads from a sheet with a Retell AI voice agent (part 1 of an AI calling system) | Retell AI, Google Sheets |
| [AI Voice Call Handler: GHL Booking & CRM Sync](n8n/ai-voice-call-handler-ghl-booking/) | Backend for the voice agent: checks live availability, books GoHighLevel appointments, logs call summaries (part 2) | Retell AI, GoHighLevel, Google Sheets |
| [Instagram AI Sales Agent (Multi-Agent)](n8n/instagram-ai-sales-agent-multimodal/) | Multi-agent DM sales bot handling text, voice and images, with catalog search, orders and Mercado Pago checkout | OpenAI, Redis, Google Sheets, Mercado Pago |

## Make.com Workflows

| Workflow | What it does | Tools |
| --- | --- | --- |
| [HouseCall Pro to GoHighLevel Sync](make/housecall-pro-to-gohighlevel-sync/) | Syncs 11 HouseCall Pro lifecycle events into GoHighLevel contacts and pipeline opportunities | HouseCall Pro, GoHighLevel |
| [Vapi AI Outbound Calls from Google Drive CSV](make/vapi-outbound-calls-from-drive-csv/) | Drop a lead CSV into Drive and a Vapi AI agent calls every lead (part 1) | Google Drive, Vapi |
| [Vapi Call Result AI Qualification](make/vapi-call-result-ai-qualification/) | Summarizes call transcripts with OpenAI and classifies leads as qualified or not (part 2) | Vapi, OpenAI, HTTP |
| [Voice Agent Calendar Availability Check](make/voice-agent-calendar-availability-check/) | Live tool for a voice agent that checks Google Calendar availability mid-call | Bland AI, Google Calendar |
| [Bland AI Bilingual Lead Callback](make/bland-ai-bilingual-lead-callback/) | Instantly calls new leads with a French or English AI voice pathway | Bland AI |
| [ClickUp Task to Zoom Meeting Link](make/clickup-task-zoom-meeting-link/) | Creates a Zoom meeting from a ClickUp checkbox and writes the link back to the task | ClickUp, Zoom |
| [Google Sheet to CSV Download Webhook](make/google-sheet-csv-export-webhook/) | Serves a live Google Sheet as a downloadable CSV through a webhook URL | Google Sheets, CSV |
| [Real Estate Lead Round-Robin Assignment](make/real-estate-lead-round-robin-assignment/) | Assigns new leads to the longest-idle agent and syncs them to Notion, Follow Up Boss and JustCall | Airtable, Notion, Follow Up Boss, JustCall |

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, phone numbers, and email addresses that appear in these workflows are fictional and do not refer to real businesses or people.
