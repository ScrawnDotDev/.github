# Scrawn... Usage-based billing in one-ish line

[**Wrap your API. Track usage. Collect cash.**](https://www.scrawn.dev) Scrawn is the open-source billing
infrastructure for builders who'd rather ship features than build a payment
pipeline. Drop in our SDK, define your pricing with our expression DSL, and
let the backend handle the math, the webhooks, and the DodoPayments plumbing.

```typescript
import { scrawn, mul } from "@scrawn/core";

const biller = scrawn({
  apiKey: process.env.SCRAWN_KEY,
  baseURL: process.env.SCRAWN_BASE_URL,
  httpUrl: process.env.SCRAWN_HTTP_URL,
});

// One line. That's it.
await biller.basicUsageEventConsumer({
  userId: "u_abc123",
  debit: biller.expr(mul(biller.tag("API_CALL"), 3)),
});
```

## What's inside

| Repo | What it does |
|---|---|
| [`Scrawn`](https://github.com/ScrawnDotDev/Scrawn) | gRPC + HTTP backend - event ingestion, billing engine, DodoPayments integration, webhook forwarding |
| [`Scrawn.js`](https://github.com/ScrawnDotDev/Scrawn.js) | TypeScript SDK - `scrawn()`, pricing DSL, AI token tracking, webhook verification |
| [`CLI`](https://github.com/ScrawnDotDev/CLI) | Go CLI - `scrawn init`, `scrawn start`, `scrawn tag sync` |
| [`dash`](https://github.com/ScrawnDotDev/dash) | Admin dashboard - analytics, API keys, webhook logs, tag/expression management |

## Use cases

- **API platforms** - Charge per request, per endpoint, or per user. Define tiers with expressions like `mul(tag("RATE"), inputTokens())`.
- **AI / LLM services** - Track token consumption per model per user. Wrap any AI SDK and bill with per-model rates.
- **SaaS products** - Usage-based pricing for any metric: storage, bandwidth, compute time, active users.
- **Developer tools** - CLI tools, SDKs, and platform APIs that need metered billing without building it in-house.

## How it works

**Deploy** → `scrawn init` + `scrawn start` spins up the stack.

**Configure** → Set DodoPayments keys and product ID via the onboarding wizard.

**Track** → Call `biller.basicUsageEventConsumer({ userId, debit })` from your app.

**Bill** → DodoPayments handles checkout; Scrawn forwards signed webhooks and manages state.

## Features

- **Pricing expression DSL** - `mul(tag("RATE"), inputTokens())`, persisted expressions, nested references, compile-time checked tags
- **AI token tracking** - Wrap any AI SDK, bill per-token with granular per-model rates
- **Self-hosted** - Your data, your Postgres, your infrastructure, your control
- **Type-safe SDK** - Tags and expressions checked at compile time
- **Webhook forwarding** - Ed25519-signed Standard Webhooks delivered to your endpoints
- **Admin dashboard** - Analytics, event logs, API key management, webhook delivery history
- **DodoPayments integration** - Checkout links, payment collection, webhook processing
- **CLI** - One-command deploy, tag sync, stack management
