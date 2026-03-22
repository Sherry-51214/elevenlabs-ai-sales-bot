# ElevenLabs AI Sales Bot — Lithuanian Outbound Calls

An AI-powered outbound sales calling bot that receives leads via Telegram, automatically places calls in Lithuanian using ElevenLabs voice AI, tracks results in Google Sheets, and books calendar meetings — all without manual intervention.

## What It Does

1. **Receives leads** via a Telegram bot (name, phone number, context)
2. **Stores the lead** in Google Sheets and sends an alert
3. **ElevenLabs places the call** — AI voice speaks Lithuanian to the prospect
4. **Captures the result** via webhook when the call completes
5. **Summarises the call** in English using OpenAI
6. **Updates Google Sheets** with full call outcome
7. **Books a calendar event** automatically if a meeting was agreed
8. **Sends Telegram alerts** for every outcome — meeting booked or call completed

## Architecture

```
Telegram Lead Intake → Parse Lead → Store in Google Sheets → Alert: New Lead
                                         ↓
                              ElevenLabs Places Call (Lithuanian)
                                         ↓
                         ElevenLabs Call Result Webhook
                                         ↓
                    Generate English Summary (OpenAI) → Update Sheets
                                         ↓
                              Meeting Booked?
                              ├── Yes → Create Calendar Event → Alert: Meeting Booked
                              └── No  → Alert: Call Completed
```

## Tech Stack

- **n8n** — workflow orchestration
- **ElevenLabs** — AI voice calling in Lithuanian
- **OpenAI** — call result summarisation in English
- **Telegram Bot** — lead intake and real-time alerts
- **Google Sheets** — lead tracking and call result storage
- **Google Calendar** — automatic meeting booking

## Key Features

- **Multilingual AI calling** — speaks Lithuanian natively using ElevenLabs voice synthesis
- **Fully automated pipeline** — from lead received to meeting booked with zero manual steps
- **Real-time Telegram alerts** — instant notification for every call outcome
- **Google Sheets CRM** — lightweight lead and result tracking without complex CRM setup
- **Auto calendar booking** — meetings created instantly when prospect agrees

## Setup

1. Import the workflow JSON into your n8n instance
2. Connect credentials:
   - Telegram Bot token
   - ElevenLabs API key (with Lithuanian voice configured)
   - OpenAI API key
   - Google Sheets OAuth2
   - Google Calendar OAuth2
3. Configure your ElevenLabs agent with the Lithuanian outbound call script
4. Set the webhook URL in ElevenLabs to point to your n8n webhook
5. Activate the workflow and send a test lead via Telegram

## Usage

Send a lead to the Telegram bot in this format:
```
/lead John Smith +37060000000 Interested in pricing
```

The bot handles everything from there automatically.

---

Built by [Shehroz Khan](https://www.linkedin.com/in/shehroz-khan-b91716197/) · Fullstack Automation Engineer
