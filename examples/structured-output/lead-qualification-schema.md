# Example: Lead Qualification Structured Output

This example defines a JSON output contract for lead research and qualification workflows.

## Purpose

This output represents a qualified or partially qualified sales lead extracted from public business information and user-provided criteria.

## Consumer

The output may be consumed by:

- CRM;
- spreadsheet;
- lead research dashboard;
- follow-up workflow;
- another LLM generating outreach.

## Schema

```json
{
  "type": "object",
  "required": [
    "status",
    "business_name",
    "website",
    "lead_score",
    "fit_reason",
    "automation_angle",
    "missing_information",
    "requires_human_review"
  ],
  "properties": {
    "status": {
      "type": "string",
      "enum": ["qualified", "partial", "not_fit", "insufficient_context"]
    },
    "business_name": {
      "type": "string"
    },
    "website": {
      "type": "string"
    },
    "niche": {
      "type": "string"
    },
    "location": {
      "type": "string"
    },
    "public_contacts": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "type": { "type": "string", "enum": ["email", "phone", "telegram", "instagram", "contact_form", "other"] },
          "value": { "type": "string" },
          "source_note": { "type": "string" }
        }
      }
    },
    "lead_score": {
      "type": "integer",
      "minimum": 1,
      "maximum": 5
    },
    "fit_reason": {
      "type": "string"
    },
    "automation_angle": {
      "type": "string"
    },
    "outreach_hook": {
      "type": "string"
    },
    "missing_information": {
      "type": "array",
      "items": { "type": "string" }
    },
    "confidence": {
      "type": "number",
      "minimum": 0,
      "maximum": 1
    },
    "requires_human_review": {
      "type": "boolean"
    }
  }
}
```

## Field Definitions

| Field | Type | Required | Description | Fallback |
|---|---|---:|---|---|
| `status` | string enum | Yes | Qualification status | `insufficient_context` |
| `business_name` | string | Yes | Name of the business | `unknown` |
| `website` | string | Yes | Website URL | `unknown` |
| `niche` | string | No | Business category | `unknown` |
| `location` | string | No | City/country/region | `unknown` |
| `public_contacts` | array | No | Publicly visible contact channels | `[]` |
| `lead_score` | integer | Yes | Fit score from 1 to 5 | `1` |
| `fit_reason` | string | Yes | Why this lead fits or does not fit | `Not enough information` |
| `automation_angle` | string | Yes | Specific automation opportunity | `unknown` |
| `outreach_hook` | string | No | Personalization angle for first message | `unknown` |
| `missing_information` | string[] | Yes | Missing details needed for better qualification | `[]` |
| `confidence` | number | No | Confidence from 0 to 1 | `0` |
| `requires_human_review` | boolean | Yes | Whether a human should check the result | `true` |

## Prompt Instructions

```text
Return only a JSON object that matches the schema.
Do not include Markdown, prose, explanations, or extra keys.
Do not invent contact details, prices, team names, customer volume, or private business information.
If a field is not available from the input, use `unknown`, an empty array, or mark it in `missing_information`.
```

## Valid Example

```json
{
  "status": "partial",
  "business_name": "Example Dental Clinic",
  "website": "https://example.com",
  "niche": "dental clinic",
  "location": "Kyiv, Ukraine",
  "public_contacts": [
    {
      "type": "contact_form",
      "value": "website contact form",
      "source_note": "Contact form visible on the website"
    }
  ],
  "lead_score": 4,
  "fit_reason": "The clinic likely receives repetitive appointment and service questions, and the website has a public contact form.",
  "automation_angle": "AI assistant could answer common service questions and collect appointment requests before manager follow-up.",
  "outreach_hook": "Mention the clinic's visible services and website contact flow.",
  "missing_information": ["monthly inquiry volume", "current CRM or booking system"],
  "confidence": 0.72,
  "requires_human_review": true
}
```

## Insufficient Context Example

```json
{
  "status": "insufficient_context",
  "business_name": "unknown",
  "website": "unknown",
  "niche": "unknown",
  "location": "unknown",
  "public_contacts": [],
  "lead_score": 1,
  "fit_reason": "Not enough information to qualify the lead.",
  "automation_angle": "unknown",
  "outreach_hook": "unknown",
  "missing_information": ["business website", "target niche", "service offer"],
  "confidence": 0,
  "requires_human_review": true
}
```
