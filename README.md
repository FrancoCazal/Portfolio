# Franco Cazal

**Backend & AI Engineer. I design and ship scalable, production-grade systems on AWS — with a custom agent harness I built for AI-augmented dev.**

Python · Django · FastAPI · PostgreSQL · AWS · Terraform · LangGraph · RAG

Lambaré, Paraguay · Remote-friendly · [francocazal.com](https://francocazal.com) · [LinkedIn](https://www.linkedin.com/in/franco-cazal) · [GitHub](https://github.com/FrancoCazal) · contact@francocazal.com

---

## About

Multi-tenant SaaS, agentic AI workflows, ecommerce — owned end-to-end from data model to deploy. I work AI-augmented, with a customized agent harness as daily-driver tooling.

I'm backend-first, but ship the full stack when needed: React + TypeScript frontends for [UrbanAttic](#urbanattic--ecommerce-platform) and [WhisperDocs](#whisperdocs--agentic-rag-over-your-documents), Django Channels for real-time, and Next.js for marketing surfaces.

I care about the boring parts: tenant isolation, observability from day one, cost-aware AI, deploys that don't surprise you on a Friday.

---

## Featured projects

### Focal Point — multi-tenant ERP SaaS with WhatsApp AI agents

*Founding Engineer.* Production multi-tenant ERP SaaS. Schema-per-tenant architecture with inventory, sales, CRM, HR, finance, SIFEN-compliant electronic invoicing, and a LangGraph-based agent that answers customers and creates quotes over WhatsApp. I co-founded Focal Point with my partners and led engineering end-to-end.

**Stack** · Django 5.2 · DRF · Channels · PostgreSQL 17 (`django-tenants`) · Valkey/Redis · LangGraph + OpenAI · Meta WhatsApp Cloud API · AWS (EC2, RDS, ElastiCache, S3, CloudFront, SES) · Terraform · Sentry + Prometheus + Grafana

**Why it's interesting** · Real multi-tenant isolation (PostgreSQL schemas, not `tenant_id` columns). SIFEN integration as a bounded context. Per-tenant AI cost tracking. EC2 + Terraform sized to the actual problem.

[Read the case study →](https://github.com/FrancoCazal/focalpoint-case-study)

---

### AgroBuy — AI procurement copilot for agricultural cooperatives

*🏆 1st place — AI Tinkerers San Lorenzo x FIUNA Deep Dive Hackathon 2026.* Backend, AI orchestration, and the ML/scoring layer. AgroBuy turns manual supplier-quotation comparison into an AI-assisted workflow: four specialized LangGraph agents (extraction, comparison, recommendation, negotiation), a supplier-reliability classifier, and explainable composite scoring grounded in live weather and exchange-rate data.

**Stack** · Python · FastAPI · LangGraph (4 LLM agents) · scikit-learn (`GradientBoostingClassifier`) · PostgreSQL · Redis · ARQ workers · React 19 · Oracle APEX · Docker

**Why it's interesting** · Honest, verifiable ML (supplier on-time classifier at AUC 0.748, with a rules-based baseline) — not decorative. Every agent has a deterministic fallback, so it produces valid outputs with no LLM available. Dual urgency/offer scoring exposes its full breakdown — auditable, not a black box. One API, two interchangeable clients (React + Oracle APEX) with zero schema duplication.

[Read the case study →](https://github.com/FrancoCazal/agrobuy-case-study)

---

### UrbanAttic — ecommerce platform

Full-stack ecommerce with Django REST Framework + React. JWT via HttpOnly cookies, Redis-backed cart, Stripe Checkout, async order processing with Celery, transactional email via SendGrid, S3 media, brutalist design system.

**Stack** · Django 5 · DRF · PostgreSQL · Redis · Celery · Stripe · SendGrid · AWS S3 · React 18 + TypeScript · Vite · TanStack Query · Tailwind · Radix UI · Railway · Vercel

**Why it's interesting** · 93 tests, 84% coverage, CI on every PR. Atomic order creation with `select_for_update()` prevents overselling. `TimestampSigner`-based email verification and password reset — no token table, no cleanup job.

[Live demo](https://urbanattic.vercel.app) · [Repo →](https://github.com/FrancoCazal/UrbanAttic)

---

### WhisperDocs — agentic RAG over your documents

Document Q&A with an explicit LangGraph state machine, hybrid retrieval, multi-provider LLM routing, token-level SSE streaming, and a real eval suite.

**Stack** · FastAPI · PostgreSQL + pgvector · LangGraph · Gemini (Vertex AI) + AWS Bedrock (Claude) · OpenAI embeddings · Twilio (WhatsApp) · React + TanStack Router · structlog · Prometheus

**Why it's interesting** · Hybrid retrieval (vector + BM25 + RRF + optional cross-encoder rerank + MMR). Gemini for cheap hot-path nodes, Bedrock for grounded generation. 50-query golden eval set with LLM-as-judge, retrieval precision/recall@k, latency, USD cost. Per-call cost is persisted, not estimated.

[Repo →](https://github.com/FrancoCazal/WhisperDocs)

---

## Skills

**Backend** · Python · Django · DRF · Django Channels · FastAPI · Celery · LangGraph · LangChain

**Databases** · PostgreSQL · pgvector · Redis · Valkey · multi-tenancy (schema-per-tenant)

**Cloud / DevOps** · AWS (EC2, RDS, ElastiCache, S3, CloudFront, SES, Bedrock) · Terraform · Docker · GitHub Actions · Nginx · Gunicorn · Vector · CloudWatch

**AI / ML** · OpenAI · Anthropic Claude (Bedrock) · Gemini (Vertex AI) · RAG · agentic workflows · hybrid retrieval · LLM evaluation · cost-aware routing

**Frontend** · React · TypeScript · Vite · TanStack Query · Tailwind · Radix UI · Next.js

**Observability** · Sentry · Prometheus · Grafana · structlog · Silk

---

## Education

**Industrial Engineering** · FIUNA · in progress (since 2022)

**Diploma in Machine Learning & Deep Learning** · FIUNA · in progress · 2026 · 4 months

**Foundations** · CoderHouse · 2024
- Python · Cloud Computing (AWS)

**Current depth**
- Anthropic Academy — 13 courses (Claude API, Claude Code, MCP, agent design)

**Self-taught**
- Django REST Framework · FastAPI · LangGraph / LangChain · GraphQL
- AI-augmented dev workflow (sub-agents, hooks, MCP, skills, statusline)

---

## AWS ecosystem

- AWS Solutions Architect Associate · in progress · 2026
- AWS for Startups · credit on Focal Point
- AWS UG Paraguay · volunteer
- Cloud Computing (AWS) · CoderHouse · 2024
- Next: AWS ML/GenAI Specialty

---

## Contact

- Email · [contact@francocazal.com](mailto:contact@francocazal.com)
- LinkedIn · [linkedin.com/in/franco-cazal](https://www.linkedin.com/in/franco-cazal)
- GitHub · [@FrancoCazal](https://github.com/FrancoCazal)
- Portfolio site · [francocazal.com](https://francocazal.com)

---

<sub>This is my portfolio repo — depth on featured work. For the quick view see <a href="https://github.com/FrancoCazal">my profile</a>. For the full experience see <a href="https://francocazal.com">francocazal.com</a>. The featured projects each link to their own repo (or, for Focal Point and AgroBuy, a public case study — the source code is private).</sub>
