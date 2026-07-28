# AI Lead Qualification Pipeline

An AI-powered lead qualification workflow built with **n8n** that automatically validates incoming leads, scores their sales potential using **Google Gemini AI**, classifies them into Hot, Warm, or Cold tiers, stores qualified leads in Google Sheets, and logs workflow errors for monitoring and debugging.

---

## Overview

Qualifying leads manually is time-consuming and inconsistent. This workflow automates the entire qualification process by using AI to analyze every incoming lead and determine its potential value.

Once a lead is submitted, the workflow automatically:

- Validates incoming lead data
- Normalizes fields for consistency
- Scores the lead using Google Gemini AI
- Assigns a qualification tier (Hot, Warm, Cold)
- Generates AI insights
- Stores qualified leads in Google Sheets
- Logs workflow errors automatically
- Returns a structured API response

This workflow is designed for businesses, agencies, sales teams, and CRM automation.

---

## Features

- AI-powered lead scoring
- Automatic lead validation
- Data normalization
- Hot / Warm / Cold lead classification
- AI-generated qualification reasoning
- Estimated budget prediction
- Suggested next sales action
- Google Sheets integration
- Slack notification support
- Automatic error logging
- Production-ready workflow
- REST API compatible

---

## Workflow Architecture

```
Lead Submission (Webhook)
          │
          ▼
Normalize & Validate Lead
          │
          ▼
Required Field Validation
          │
          ▼
Google Gemini AI Analysis
          │
          ▼
Generate AI Score & Insights
          │
          ▼
Assign Lead Tier
   ├── Hot
   ├── Warm
   └── Cold
          │
          ▼
Store in Google Sheets
          │
          ▼
Return API Response

If Error Occurs

Error Trigger
      │
      ▼
Capture Error Details
      │
      ▼
Log Error to Google Sheets
      │
      ▼
(Optional) Slack Notification
```

---

## Workflow Nodes

### Main Workflow

| Node | Purpose |
|------|---------|
| Lead Intake Webhook | Receives incoming lead data |
| Normalize & Validate Lead | Cleans and standardizes lead information |
| Valid Lead? | Checks required fields |
| Google Gemini Chat Model | AI model for lead analysis |
| AI Score Lead | Generates score and business insights |
| Parse & Validate AI JSON | Parses AI response safely |
| Route by Tier | Separates Hot, Warm, and Cold leads |
| Google Sheets | Stores qualified leads |
| Respond | Returns API response |

### Error Handling Workflow

| Node | Purpose |
|------|---------|
| Error Trigger | Captures workflow failures |
| Build Error Record | Formats execution details |
| Google Sheets | Logs errors |
| Slack Alert | Optional real-time notification |

---

## Technologies Used

- n8n
- Google Gemini AI
- Google Sheets
- Webhooks
- JavaScript
- JSON
- Slack
- REST API

---

## Input Example

```json
{
  "name": "Sarah Chen",
  "email": "sarah@example.com",
  "company": "Acme Logistics",
  "job_title": "VP Operations",
  "source": "LinkedIn"
}
```

---

## AI Output Example

```json
{
  "score": 95,
  "tier": "Hot",
  "intent_summary": "Seeking an AI solution for business automation.",
  "reason": "Senior decision-maker with high buying intent.",
  "suggested_next_step": "Schedule a discovery call.",
  "budget": "$8,000 - $12,000"
}
```

---

## Google Sheets Output

Each processed lead is stored with the following information:

| Field |
|--------|
| Timestamp |
| Name |
| Email |
| Company |
| Job Title |
| Source |
| AI Score |
| Lead Tier |
| Intent Summary |
| Qualification Reason |
| Suggested Next Step |
| Estimated Budget |
| AI Fallback Used |

---

## Error Logging

If any node fails, the workflow automatically records:

- Timestamp
- Workflow Name
- Error Message
- Failed Node
- Execution URL
- Input Snapshot

This makes troubleshooting much easier without manually reviewing workflow executions.

---

## Use Cases

- AI Lead Qualification
- Sales Automation
- CRM Enrichment
- Marketing Agencies
- SaaS Companies
- B2B Lead Management
- Customer Acquisition
- AI Sales Assistant
- Business Automation

---

## Integrations

- Google Gemini AI
- Google Sheets
- Slack
- HTTP Requests
- Webhooks

---

## Environment Variables

Create the following credentials before importing the workflow.

```env
GOOGLE_GEMINI_API_KEY=

GOOGLE_SHEET_ID=

GOOGLE_SERVICE_ACCOUNT=

SLACK_WEBHOOK_URL=
```

---

## Project Structure

```
ai-lead-qualification-pipeline/
│
├── README.md
├── workflow.json
├── architecture.png
├── .env.example
├── assets/
│   ├── workflow-overview.png
│   ├── qualified-leads-sheet.png
│   └── error-log-sheet.png
└── sample-data/
    ├── sample-input.json
    └── sample-output.json
```

---

## Screenshots

### Workflow Overview

Complete AI-powered lead qualification workflow built in n8n.

![Workflow Overview](assets/workflow-overview.png)

---

### Qualified Leads

All processed leads are automatically analyzed, scored, and stored in Google Sheets.

![Qualified Leads](assets/qualified-leads-sheet.png)

---

### Error Monitoring

Workflow failures are automatically logged with execution details for easier debugging and monitoring.

![Error Log](assets/error-log-sheet.png)

---

## Future Improvements

- HubSpot Integration
- Salesforce Integration
- Airtable Support
- Automatic Email Follow-up
- WhatsApp Notifications
- Meeting Scheduler Integration
- Duplicate Lead Detection
- Dashboard Analytics
- Multi-Model AI Support
- CRM Synchronization

---

## License

This project is licensed under the MIT License.
