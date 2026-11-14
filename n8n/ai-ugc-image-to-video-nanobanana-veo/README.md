# AI UGC Product Ad Generator (Nano Banana + Veo 3.1)

**Platform:** n8n **Category:** AI Content / Video Ads

## Overview

UGC-style ads (a real-looking person using the product) convert well but are expensive to shoot. This workflow takes a plain product photo from a Google Sheet and produces a lifestyle UGC image with Nano Banana (Gemini 2.5 Flash Image), then animates it into a short video ad with Veo 3.1.

## How It Works

1. Trigger — manual run reads product rows (image URL, name, offer) from Google Sheets and loops through them one at a time.
2. The product image is downloaded and padded onto a 16:9 canvas to fit video framing.
3. GPT-4o-mini Vision analyzes the product and writes a detailed UGC image prompt, which is saved to the sheet.
4. Nano Banana generates a lifestyle image of a person using the product, based on the original photo.
5. GPT-4o-mini turns that image plus the product name and offer into a Veo 3.1 video prompt.
6. Veo 3.1 renders the video from the reference image. The workflow polls until it's done, then uploads to Drive and writes the video URL back to the sheet.

## Tech Stack

n8n, OpenAI (GPT-4o-mini Vision), Google Vertex AI (Gemini 2.5 Flash Image "Nano Banana", Veo 3.1), Google Sheets, Google Drive

## Key Features

- Two-stage generation: product photo to UGC image to video, using a reference image for consistency
- Image preprocessing (resolution check and 16:9 canvas) done with n8n's built-in Edit Image node
- Prompts and output URLs stored per row for review and reuse
- Async polling loop for Veo's long-running jobs
- Includes disabled alternative nodes (DALL-E 3 path, direct URL download) for experimentation

## Setup

1. Import `workflow.json`.
2. Connect credentials: OpenAI, Google (OAuth2 with Vertex AI access), Google Sheets, Google Drive.
3. Replace placeholders: `{{GCP_PROJECT_ID}}`, `{{SHEET_ID}}`, `{{DRIVE_IMAGE_FOLDER_ID}}`, `{{DRIVE_VIDEO_FOLDER_ID}}`.
4. Sheet columns: `productImgUrl`, `productName`, `productOffer`, `nanobananaPrompt`, `veo31Prompt`, `finalVideoUrl`.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, phone numbers, and email addresses that appear in this workflow are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
