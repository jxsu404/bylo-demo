# Bylo

> WhatsApp AI agent for small businesses — bookings, CRM, and customer retention on autopilot.

**Status:** In development · Private beta · Costa Rica 🇨🇷

---

## The problem

Small service businesses (barbershops, nail salons, vets, clinics) lose clients because they can't respond to WhatsApp fast enough. A single owner can't manage appointments, answer FAQs, and do the actual work at the same time.

## What Bylo does

Bylo connects to a business's WhatsApp number and handles customer conversations automatically using AI. When a client writes, Bylo responds instantly — with the right info, in natural Spanish.

```
Client writes on WhatsApp
        ↓
   Bylo AI agent
  (powered by Claude)
        ↓
 Responds instantly with:
  - Availability & bookings
  - Service info & pricing
  - FAQs
  - Loyalty rewards
        ↓
  Business sees everything
  live on their dashboard
```

When a conversation needs a human, Bylo escalates automatically and the owner takes over from the dashboard.

---

## Core features

| Feature | Description |
|---------|-------------|
| **AI Agent** | Responds to customers 24/7 in natural Spanish using the business's own info |
| **Booking management** | Handles availability and appointment confirmations via chat |
| **Live dashboard** | Real-time view of all conversations, with ability to take over manually |
| **Customer CRM** | Auto-tags customers based on conversation content (Claude Haiku) |
| **Loyalty system** | Tracks visits, rewards loyal customers, reactivates inactive ones |
| **Multi-tenant** | Each business connects their own WhatsApp number independently |

---

## Tech stack

| Layer | Technology |
|-------|-----------|
| Frontend + Backend | Next.js 14 (App Router) + TypeScript |
| Styling | Tailwind CSS |
| Database + Auth | Supabase (PostgreSQL + Row Level Security) |
| Realtime | Supabase Realtime (live conversation updates) |
| AI | Claude Sonnet (conversations) + Claude Haiku (async tagging) |
| WhatsApp | Kapso Platform (Meta Cloud API wrapper) |
| Deploy | Vercel |

---

## Architecture overview

```
WhatsApp Client
      ↓
Kapso Platform (Meta Cloud API)
      ↓ webhook POST (HMAC signed)
Next.js /api/webhook/whatsapp
  1. Verify HMAC signature
  2. Identify business (multi-tenant)
  3. Upsert customer record
  4. Get/create conversation
  5. Build system prompt + history
  6. Call Claude API
  7. Send reply via Kapso
  8. Save outbound message
      ↓
Supabase (businesses · customers · conversations · messages)
      ↓ Realtime subscription
Dashboard (business owner sees live conversations)
```

**Multi-tenancy:** Row Level Security ensures each business only sees its own data. Every business connects its own WhatsApp number.

---

---

## Roadmap

- [x] Project structure + schema design
- [x] Next.js + Supabase + Claude integrations scaffolded
- [ ] Full auth + onboarding flow
- [ ] WhatsApp webhook end-to-end
- [ ] Live dashboard (Supabase Realtime)
- [ ] Auto-tagging with Claude Haiku
- [ ] Loyalty & reactivation system
- [ ] 5 pilot businesses (target: end of 2026)

---

## Demo

> Live demo coming soon. Reach out if you want early access.

---

*The production codebase is private. This repo contains public-facing documentation.*
