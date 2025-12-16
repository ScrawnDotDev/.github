# Welcome to Scrawn

Scrawn is a **billing infrastructure** that lets you integrate usage-based billing into your application with a single function call.


> Track billable events, calculate usage, and handle payments - all with one line of code.


## What is Scrawn?

Scrawn tracks user events, calculates usage, and handles payments - all behind a simple SDK. Instead of building billing logic yourself, you call `event consumers` and we handle the rest.

```typescript
import { Scrawn } from '@scrawn/sdk';

const scrawn = new Scrawn({
  apiKey: process.env.SCRAWN_KEY!,
  baseUrl: process.env.SCRAWN_BASE_URL!
});

// That's it - track usage with one line
await scrawn.sdkCallEventConsumer({ 
  userId: 'uuid', 
  debitAmount: 69.69,
});
```


> **One line of code**  -  That's all you need to start tracking billable events in your application.


## Why Scrawn?

<Cards>
  <Card icon={} title="Single Line Integration">
    No complex billing logic. One function call tracks events, calculates usage, and triggers payments.
  </Card>
  <Card icon={} title="Usage-Based Billing">
    Charge users based on actual consumption. Track API calls and function invocations per user.
  </Card>
  <Card icon={} title="Built-in Admin Dashboard">
    Monitor events, manage API keys, and view analytics out of the box.
  </Card>
</Cards>

## How It Works

1. **Deploy Backend**  -  Self-host the gRPC server with PostgreSQL
2. **Install SDK**  -  Add `@scrawn/sdk` to your application
3. **Track Events**  -  Call `scrawn.sdkCallEventConsumer()` whenever billable actions occur
4. **Collect Payment**  -  Call `scrawn.collectPayment()` when usage exceeds threshold

## Getting Started

<Cards>
  <Card href="/docs/quick-start" title="Quick Start">
    Get running in under 2 minutes with our quick start guide.
  </Card>
  <Card href="/docs/scrawn-js" title="Scrawn.js SDK Guide">
    Learn how to integrate Scrawn into your application
  </Card>
</Cards>

## Use Cases

- **API Platforms**  -  Charge per API request
- **AI Services**  -  Bill based on compute/tokens used
- **Data Processing**  -  Track storage, bandwidth, or processing time
- **SaaS Products**  -  Usage-based pricing for any metric

## Features

- **Self-Hosted**  -  Full control over your billing infrastructure
- **gRPC Backend**  -  High-performance server with PostgreSQL
- **Type-Safe SDK**  -  TypeScript SDK with full type safety
- **Framework Agnostic**  -  Works with Express, Next.js, Fastify, tRPC, NestJS
- **Production Ready**  -  LRU caching, retry logic, error handling


> Scrawn is open source and available on [GitHub](https://github.com/ScrawnDotDev/Scrawn).
