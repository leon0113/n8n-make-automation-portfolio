# HeyGen AI Avatar Video Auto-Publisher with Slack Approval

**Platform:** n8n **Category:** AI Content / Social Media Automation

## Overview

Talking-head videos perform well on social media, but filming them daily isn't realistic. This workflow writes a short ad script with AI, gets a human to approve it in Slack, renders it as a HeyGen AI-avatar video, and publishes it to Instagram, Facebook, TikTok, and YouTube through Blotato.

## How It Works

1. Trigger — manual run reads the next unprocessed title from Google Sheets.
2. A different HeyGen avatar and voice is picked for each day of the week, and OpenAI writes the video script.
3. **Human-in-the-loop:** the script is sent to Slack with an approve/reject form, and the workflow waits for the response. A rejection sends a notification and ends the run.
4. Approved scripts are sent to HeyGen. The workflow polls the render status every 30 seconds until the video is ready.
5. The MP4 is saved to Google Drive, and OpenAI writes platform captions as JSON.
6. The video is uploaded to Blotato and posted to Instagram, Facebook, TikTok, and YouTube. The sheet status is then updated.

## Tech Stack

n8n, OpenAI, HeyGen API, Slack, Google Sheets, Google Drive, Blotato

## Key Features

- Slack approval gate before any paid video render or public post
- Day-of-week avatar and voice rotation for content variety
- Async polling loop with error-output handling for HeyGen renders
- One video published to 4 platforms with platform-specific payloads

## Setup

1. Import `workflow.json`.
2. Connect credentials: OpenAI, Google Sheets, Google Drive, Slack (OAuth2), Header Auth (HeyGen).
3. Replace placeholders: `{{SHEET_ID}}`, `{{DRIVE_FOLDER_ID}}`, `{{HEYGEN_API_KEY}}`, `{{HEYGEN_AVATAR_ID_1}}`, `{{HEYGEN_AVATAR_ID_2}}`, `{{HEYGEN_VOICE_ID_1}}`, `{{SLACK_USER_ID}}`, `{{BLOTATO_API_KEY}}`, and the social account IDs (`{{INSTAGRAM_ID}}`, `{{FACEBOOK_ID}}`, ...).
4. Sheet columns: `Title`, `Status`.

## Data Privacy

All personal, client, and employer data has been removed and replaced with placeholders. Company names, phone numbers, and email addresses shown here (e.g. "Northwind Digital Solutions") are fictional and do not refer to real businesses or people.

---

Built by **Tahjib Hossain (Leon)**
