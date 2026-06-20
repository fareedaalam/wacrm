# Afisofftech CRM — WhatsApp CRM

> A self-hostable WhatsApp CRM by **Afisofftech** — shared inbox,
> contacts, sales pipelines, broadcasts, and no-code automations.
> Deploy it, brand it, sell it.

[![License: MIT](https://img.shields.io/badge/License-MIT-violet.svg)](./LICENSE)
[![Next.js 16](https://img.shields.io/badge/Next.js-16-black?logo=nextdotjs)](https://nextjs.org)
[![Supabase](https://img.shields.io/badge/Supabase-Postgres%20%2B%20Auth-3ecf8e?logo=supabase)](https://supabase.com)

Afisofftech CRM is a complete, working WhatsApp CRM you can stand up in
an afternoon — clone or fork it to run your own branded instance.

## What you get out of the box

- **Shared inbox** on the official WhatsApp Business API — multiple
  agents working one number, per-conversation assignment, status, and
  notes.
- **Contacts + tags + custom fields**, CSV import, deduplication.
- **Sales pipelines** (Kanban) with deals linked to conversations.
- **Broadcasts** with Meta-approved templates, delivery + read
  tracking, per-recipient variable substitution.
- **No-code automations** — triggers on inbound messages, new
  contacts, keywords, or schedule; conditional branches, waits,
  tags, webhooks. Visual builder.
- **Real-time dashboard** — response times, daily volume, pipeline
  value, cross-module activity feed.
- **Team accounts** — invite teammates by link, role-based access
  (owner / admin / agent / viewer), ownership transfer. Every install
  is account-scoped, so one shared inbox can be staffed by a whole
  team. Solo use stays single-user with zero setup.
- **Account management** — email, password, avatar, global sign-out.

## Why run Afisofftech CRM?

- **Full ownership** — your code, your Supabase project, your domain,
  your data. No SaaS lock-in, no seat pricing.
- **Full customisation** — add the fields your team needs, remove the
  modules you don't, redesign anything. The stack is boring on
  purpose (Next.js + Supabase + Tailwind) so the learning curve is
  short.
- **Zero ops to start** — Managed Node.js hosts deploy it in a few
  clicks. No Docker, no Kubernetes, no infra team needed.
- **Real security primitives** — token encryption (AES-256-GCM), RLS
  on every table, HMAC-verified webhooks, CSP, rate limiting, CI
  typecheck/build on every PR.

## Quick start

```bash
git clone https://github.com/fareedaalam/wacrm.git
cd wacrm
npm install
cp .env.local.example .env.local   # fill in Supabase + Meta creds
npm run dev
```

Open <http://localhost:3000>. You'll be redirected to `/login` (or
`/dashboard` if already signed in).

## Deploy

Afisofftech CRM is a standard Next.js 16 app and runs anywhere Node.js
does (managed Node.js hosts, Vercel, Railway, or your own VPS).

The 60-second version:

1. Provision a Node.js host and connect this repository.
2. Set your Supabase + Meta environment variables (see
   `.env.local.example`) — including `NEXT_PUBLIC_SITE_URL` so invite
   links resolve to your domain.
3. Push to your deploy branch. The host builds and serves it.

> HTTPS is required for the WhatsApp Business webhook, so make sure
> your host issues an SSL certificate for your domain.

## Stack

- **App** — Next.js 16 (App Router), React 19, TypeScript, Tailwind v4.
- **Data** — Supabase (Postgres + Auth + Storage + RLS).
- **WhatsApp** — Meta Cloud API (official WhatsApp Business API).

## Configuration

All configuration is via environment variables — see
[`.env.local.example`](./.env.local.example) for the full list,
including Supabase keys, Meta WhatsApp credentials, the encryption
key, and `NEXT_PUBLIC_SITE_URL`.

## License

[MIT](./LICENSE). © Afisofftech.
