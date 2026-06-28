# Vedant Bhavsar

Full-stack engineer who ships production-shaped systems, not tutorial demos. I write the "why," not just the "what" — every project below has an architecture decision behind it that I can defend in detail.

**Currently:** Frontend engineer at Sparrowhost, working on [likelife.ai](https://likelife.ai) (AI voice agent SaaS) and [simuphish.com](https://simuphish.com) (phishing-awareness training platform).

**Building in public:** SaaS side-projects that solve real infra problems — webhook reliability, RAG search, video pipelines, link management — each one written up with the trade-offs spelled out, not just the feature list.

📫 [vedantbhavsar.10@gmail.com](mailto:vedantbhavsar.10@gmail.com) · [LinkedIn](https://linkedin.com/in/vedantbhawsar) · [X/Twitter](https://x.com/vedantbhawsar) · [vedxnt.com](https://vedxnt.com)

---

## What I'm building

| Project | What it does | Stack |
|---|---|---|
| **[HookScope](https://github.com/VedantBhawsar/HookScope)** | Multi-tenant webhook observability platform — verifies, archives, forwards, and audits webhooks with replay and live alerts | Fastify, Express, Next.js, BullMQ, Redis, S3, Prisma, Turborepo |
| **[DocSense](https://github.com/VedantBhawsar/DocSense)** | RAG platform — upload PDFs, get semantic search + streamed LLM answers over your own documents | Next.js, Express, BullMQ, pgvector, Drizzle, SSE |
| **[ClipFlow](https://github.com/VedantBhawsar/ClipFlow)** | SaaS for YouTube creators — automates scheduling, thumbnails, and chapter timestamps from a single upload | Next.js, Express, BullMQ worker, Prisma, S3/R2, YouTube Data API |
| **[Sniplink](https://github.com/VedantBhawsar/Sniplink)** | URL shortener with click analytics, geo-tracking, and Stripe billing, built for sub-millisecond redirects | Bun, Express, React 19, Redis, PostgreSQL (Neon), Prisma |

Each repo's README documents the actual architecture — sequence diagrams, state machines, and a "why this and not that" section comparing the alternative I didn't pick. I'd rather you read those than a list of badges.

---

## How I think about systems

- **Decouple the hot path from the slow path.** Sniplink's redirect endpoint never blocks on a DB write; HookScope's webhook intake never waits on auth/CRUD traffic. Same idea, different repo.
- **Durability has a cost — name it.** I use Redis as a queue when the infra is already there and the failure mode (a flushed cache before ack) is acceptable; I reach for Postgres-backed queues when it isn't.
- **State machines over status flags.** ClipFlow's video pipeline is `UPLOADED → READY/SCHEDULED → PUBLISHING → PUBLISHED/PUBLISH_FAILED`, with every transition's failure path written down before I wrote the happy path.
- **Auth that survives a real attacker.** httpOnly cookies over localStorage, JWT refresh rotation with theft detection, raw-body capture for HMAC verification before the body parser can mangle it.

---

## Stack

**Core:** TypeScript · Next.js · NestJS · Node.js · Express

**Data:** PostgreSQL · Drizzle · Prisma · pgvector · Redis

**Infra:** Docker · AWS S3 · BullMQ · Turborepo · GitHub Actions

**Frontend:** React 19 · Tailwind · shadcn/ui · TanStack Query · Zustand

---

## Outside of code

Tracking crypto markets with technical analysis, deep in body-recomposition training (vegetarian, gym 5–6x/week), and posting build logs on [X](https://x.com/vedantbhawsar) as these projects ship.

---

<sub>Open to remote full-stack roles at early-stage product startups. Reach out if any of the above is relevant to what you're building.</sub>
