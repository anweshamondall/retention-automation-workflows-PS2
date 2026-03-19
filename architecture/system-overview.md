# Campaign Architecture

## System Overview

The retention marketing campaigns executed during this internship followed a **modular, layered architecture** — where creative assets, automation logic, communication APIs, and tracking systems were integrated into a unified campaign execution framework.

---

## Architectural Layers

### Layer 1 — Creative Layer (Presentation)

User-facing communication assets developed and refined at this layer:

- **Email Creatives** — Responsive HTML layouts with embedded links, UTM parameters, and preview-compatible formatting
- **WhatsApp Templates** — Structured messaging templates with header media, body text, dynamic variable placeholders, and CTA buttons
- **Social Media Visuals** — Ad creatives and carousel assets in platform-specific aspect ratios
- **Video Creatives** — Short-form promotional videos with text overlays, optimised dimensions, and platform-compatible exports

---

### Layer 2 — Configuration Layer

Technical setup that connects creative assets to campaign systems:

- **Meta Business Suite** — WhatsApp template registration, compliance validation, approval monitoring
- **HTML Template Editing** — Updating template identifiers, campaign content blocks, embedded links, and formatting tags
- **ImgBB Media Hosting** — Hosting visual assets externally, embedding publicly accessible URLs into templates
- **UTM Link Generation** — Appending structured tracking parameters (source, medium, campaign) to all campaign URLs
- **JSON Payload Structuring** — Defining sender, recipient, template reference, and media elements for WhatsApp API calls

**Sample WhatsApp API Endpoint:**
```
POST https://api.in.freshchat.com/v2/outbound-messages/whatsapp
```

**Sample JSON Payload Structure:**
```json
{
  "from": {
    "channel": "whatsapp",
    "phone_number": "<business_number>"
  },
  "to": {
    "phone_number": "<recipient_number>"
  },
  "message": {
    "template": {
      "name": "<approved_template_name>",
      "language": {
        "code": "en"
      },
      "components": [
        {
          "type": "header",
          "parameters": [
            {
              "type": "image",
              "image": {
                "link": "<imgbb_hosted_image_url>"
              }
            }
          ]
        },
        {
          "type": "body",
          "parameters": [
            {
              "type": "text",
              "text": "{{customer_name}}"
            }
          ]
        }
      ]
    }
  }
}
```

---

### Layer 3 — Automation & Logic Layer

Workflow intelligence and behavioural targeting configured at this layer:

- **User Segmentation** — Audience segments built on behavioural attributes: product views, engagement history, purchase activity
- **Trigger-Based Workflows** — Campaign flows activated by predefined events (cart abandonment, inactivity, product interaction)
- **Time-Based Scheduling** — Campaign dispatch scheduled for optimal time slots (morning/evening deployment)
- **Conditional Branching** — If-else logic structures within automation platforms to send differentiated communication based on user behaviour
- **Behaviour-Driven Retention** — Campaigns targeting users based on incomplete purchases, product-view patterns, or engagement drop-offs

---

### Layer 4 — Delivery Layer

Actual campaign transmission and deployment validation:

- **Interakt** — WhatsApp campaign configuration, template linking, test runs, delivery log monitoring
- **Customer.io** — Trigger-based email and WhatsApp workflows, HTML template uploads, conditional logic branching
- **Mailchimp** — Email campaign drafting, scheduling, subject line and preview text configuration
- **Mailjet** — HTML email file uploads, audience segment configuration, rendering compatibility validation

---

### Layer 5 — Tracking & Analytics Layer

Performance monitoring and data-driven optimisation:

- **UTM Tracking** — Structured parameters embedded in all campaign URLs for traffic and engagement attribution
- **Excel Tracking Sheets** — Campaign performance figures, sales data, asset links, segmentation details, and scheduling metadata
- **Meta Analytics Dashboard** — Delivery rates, click-through metrics, engagement performance, template approval status
- **Delivery Status Logs** — Error investigation, template mismatch resolution, controlled re-testing

---

## End-to-End Tech Stack Flow

```
Creative Design Tools (Adobe CC / Canva / AI Tools)
                    ↓
     HTML & WhatsApp Template Configuration
                    ↓
      Meta Business Suite — Template Registration
                    ↓
   Automation Platforms (Customer.io / Interakt)
                    ↓
  Delivery APIs (WhatsApp Business API / Email Engines)
                    ↓
        UTM Tracking & Analytics Systems
                    ↓
     Performance Review & Iterative Optimisation
```

---

## Platform Integration Map

```
ClickUp (Task Management)
    │
    ├── Creative Assets ──────────────────── ImgBB (Media Hosting)
    │        │
    │        ▼
    │   Meta Business Suite ── WhatsApp Template Approval
    │        │
    │        ▼
    ├── Interakt ──────────────────────────── WhatsApp Delivery
    │
    ├── Customer.io ───────────────────────── Email + WhatsApp
    │
    ├── Mailchimp ─────────────────────────── Email Delivery
    │
    ├── Mailjet ───────────────────────────── Email Delivery
    │
    └── Excel + UTM Builder ───────────────── Tracking & Reporting
```
