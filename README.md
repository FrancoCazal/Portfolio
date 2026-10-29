# Franco Cazal

**AI & ML Engineer · applied AI: agentic systems & RAG in production**

I take applied AI from prototype to production: agents and RAG measured with evals, ML models measured against baselines, and the Python backends and AWS infrastructure they run on.

Lambaré, Paraguay · GMT-3 · remote · [francocazal.com](https://francocazal.com) · [LinkedIn](https://www.linkedin.com/in/francocazal) · [GitHub](https://github.com/FrancoCazal) · contact@francocazal.com

---

## Stack by domain

| | What | Proof |
|---|---|---|
| **ai** | LangGraph agents, hybrid RAG (pgvector + BM25), golden-set evals, cost-aware model routing (Bedrock and Vertex AI in WhisperDocs) | [Focal Point](https://github.com/FrancoCazal/focalpoint-case-study) · [WhisperDocs](https://github.com/FrancoCazal/WhisperDocs) · [SilentOps](https://github.com/FrancoCazal/SilentOps) |
| **ml** | scikit-learn, gradient boosting (LightGBM), conformal prediction, rolling-origin backtests with leakage tests | [Blindside](https://github.com/FrancoCazal/Blindside) · [AgroBuy](https://github.com/FrancoCazal/AgroBuy) |
| **backend** | Python (FastAPI, Django, Celery), PostgreSQL, Redis, schema-per-tenant isolation | [Focal Point](https://github.com/FrancoCazal/focalpoint-case-study) · [WhisperDocs](https://github.com/FrancoCazal/WhisperDocs) · [Urban Attic](https://github.com/FrancoCazal/UrbanAttic) |
| **cloud** | AWS (EC2, RDS, S3, SES) provisioned with Terraform, Docker, GitHub Actions | [Focal Point](https://github.com/FrancoCazal/focalpoint-case-study) · [WhisperDocs](https://github.com/FrancoCazal/WhisperDocs) · [Urban Attic](https://github.com/FrancoCazal/UrbanAttic) |
| **front** | React + TypeScript, when the product needs a front | [Focal Point](https://github.com/FrancoCazal/focalpoint-case-study) · [Blindside](https://github.com/FrancoCazal/Blindside) · [Urban Attic](https://github.com/FrancoCazal/UrbanAttic) |

---

## Experience

**Co-founder & Founding Engineer · Focal Point** · Dec 2023 – Mar 2026
Multi-tenant ERP SaaS with production-grade agentic AI workflows. The company continues; my full-time tenure ended in March 2026.

**Freelance · Custom Platforms & Web** · Dec 2023 – now
Custom software platforms for public and private institutions, built end to end: data model, backend, working frontends, data integration and ETL pipelines, deploys. Plus web development: websites and landing pages for businesses.

---

## Featured projects

### Focal Point · multi-tenant ERP SaaS with WhatsApp AI agents

*Co-founder & Founding Engineer · Dec 2023 – Mar 2026 · production.* Schema-per-tenant ERP with inventory, sales, CRM, HR, finance, SIFEN-compliant electronic invoicing, and a LangGraph agent that answers customers and places real orders over WhatsApp. I co-founded Focal Point with my partners and led engineering end to end.

**Stack** · Django 5 · DRF · Channels · Next.js · PostgreSQL 17 (`django-tenants`) · Valkey/Redis · LangGraph + OpenAI · Meta WhatsApp Cloud API · PagoPar · AWS (EC2, RDS, ElastiCache, S3, CloudFront, SES) · Terraform · GitHub Actions · Sentry + Prometheus + Grafana

**Result** · Live in production with real businesses. Five subscriptions replaced by one product, and a customer-facing agent available 24/7.

**Why it's interesting** · Real multi-tenant isolation (PostgreSQL schemas instead of `tenant_id` columns). SIFEN integration as a bounded context. Per-tenant AI cost tracking. EC2 + Terraform sized to the actual problem.

[Read the case study →](https://github.com/FrancoCazal/focalpoint-case-study) (the source code is private)

---

### Blindside · perishable demand forecasting that recovers censored demand

*Capstone · FIUNA Applied Machine Learning & Deep Learning Diploma · 2026 · solo.* Forecasts demand per store and product for perishables. It first recovers the demand hidden by stockouts (sales read zero, demand was not), then turns the forecast into an order quantity at the critical fractile `q* = Cu / (Cu + Co)`, inside a calibrated conformal band.

**Stack** · Python · LightGBM (one global quantile model over 3,066 series) · conformalized quantile regression · FastAPI · Streamlit · React · Docker

**Result** · MASE 0.8217 over 8 rolling origins and 3,066 series: 25.3% better than seasonal naive against a declared 20% goal, worst origin 0.8790. The 90% CQR interval covers 88.0% with a band 53% narrower than residual conformal. Training on recovered demand cuts the re-censored bias from −18.19% to −6.61%.

**Why it's interesting** · 320 tests, including leakage tests that caught real bugs in this code. Negative results (a hyperparameter search that changed nothing, clustering) are published, not hidden.

[Repo →](https://github.com/FrancoCazal/Blindside)

---

### SilentOps · shift-handover agent for cold-chain operations

*AI Tinkerers Agents, Everywhere global hackathon · Sep 2026 · team of four. My part (R1): the detector, the agent loop, prompts, read tools, provider fallback and the eval harness, plus the spec and the frozen contracts.* Lives in the operations Slack of a refrigerated logistics hub. A deterministic detector finds the shift handover that was never written and records the evidence of that absence; an agent proposes a sourced handover document, work-order reassignments and the Slack notice. Nothing is written until a supervisor approves.

**Stack** · TypeScript · Node.js · CopilotKit (Channels, BuiltInAgent) · Slack · MCP (Ambiguous workspace) · Auth0 M2M · Gemini 2.5 Flash with Pro fallback · Next.js

**Result** · The full loop ran end to end against the live workspace with Gemini 2.5 Flash, and replaying an approval executed nothing twice. The 15-case golden set passes 15/15 against a scripted model and 5/15 against Gemini 2.5 Flash, reported separately.

**Why it's interesting** · The model cannot write: its only action tool is `propose_action`, and every write crosses one boundary with an Auth0 scope per action and an idempotency key. 310 offline tests, CI on every push.

[Repo →](https://github.com/FrancoCazal/SilentOps)

---

### WhisperDocs · agentic RAG over your documents

*Solo · built April–May 2026 · published as a snapshot · runs locally with Docker Compose.* Document Q&A from a chat UI or WhatsApp, with an explicit LangGraph state machine, hybrid retrieval, per-node model routing and token-level SSE streaming. It cites every claim to a retrieved chunk and refuses when the documents do not hold the answer.

**Stack** · FastAPI · PostgreSQL + pgvector · LangGraph · Gemini (Vertex AI) + AWS Bedrock (Claude) · OpenAI embeddings · Twilio (WhatsApp) · React + TanStack Router · structlog · Prometheus

**Result** · On eval run `b2b0899a` (50 golden questions), an LLM judge scored 96% answer accuracy and a 6% hallucination rate, with retrieval precision and recall of 91.5% and 92.1%, 9.1 s p95 latency and $0.63 for the whole set. It is one run of a stochastic pipeline: the seven full runs that day ranged from 80% to 96% accuracy, and the run predates the published snapshot. 58 offline tests run in CI on every push.

**Why it's interesting** · Hybrid retrieval (vector + BM25 + RRF + optional cross-encoder rerank + MMR). Gemini for cheap hot-path nodes, Bedrock for grounded generation. Per-call cost is persisted at request time. The design decisions are recorded in four ADRs.

[Repo →](https://github.com/FrancoCazal/WhisperDocs)

---

### AgroBuy · AI procurement copilot for agricultural cooperatives

*🏆 1st place · AI Tinkerers San Lorenzo x FIUNA Deep Dive 2026 · team of five. My part: backend, AI orchestration and the ML and scoring layer.* AgroBuy reads supplier quotations, scores each one against weather, exchange-rate and supplier-reliability signals, recommends one with its full breakdown, and drafts the negotiation email. It runs on AgroPredict AI, a multi-agent platform by Cristian Paniagua; I built the procurement backend on top of it, including the four LLM agents and the plain Python orchestrator that runs them.

**Stack** · Python · FastAPI · 4 LLM agents with deterministic fallbacks · scikit-learn (`GradientBoostingClassifier`) · PostgreSQL · React 19 · Oracle APEX (build guide) · Docker

**Result** · 1st place. 67 tests run without a database. The supplier on-time classifier scores AUC 0.748 on a held-out split of a synthetic delivery history (the demo has no real supplier records), so it shows the pipeline works end to end and says nothing about real suppliers; a rules-based fallback takes over when no model is loaded.

**Why it's interesting** · Every agent has a deterministic fallback, so it produces valid outputs with no LLM available. The urgency and offer scores expose their full breakdown. One API designed for two clients: the React app and Oracle APEX, whose build guide is in the repo.

[Repo →](https://github.com/FrancoCazal/AgroBuy)

---

### Urban Attic · ecommerce platform

*Solo · April 2026.* Full-stack store on Django REST Framework and React: JWT in HttpOnly cookies, a Redis cart, stock locked when the order is created, Stripe's hosted Checkout confirmed by a signed webhook, and transactional email sent from Celery.

**Stack** · Django 5 · DRF · PostgreSQL · Redis · Celery · Stripe · SendGrid · AWS S3 · React 18 + TypeScript · Vite · TanStack Query · Tailwind · Radix UI · Docker · Vercel

**Result** · 93 tests. CI runs them against Postgres 16 on every push and pull request and fails under 80% coverage (84% in a local run); a second job type-checks and builds the storefront.

**Why it's interesting** · Atomic order creation with `select_for_update()` prevents overselling. `TimestampSigner`-based email verification and password reset: no token table, no cleanup job.

[Repo →](https://github.com/FrancoCazal/UrbanAttic) · live demo offline while the backend moves to a new host

---

## Now

- AWS Certified Solutions Architect – Associate (October 2026), after Cloud Practitioner and AI Practitioner earlier in the year.
- Finished the FIUNA Machine Learning & Deep Learning diploma. Capstone: [Blindside](https://github.com/FrancoCazal/Blindside).
- Two AI Tinkerers hackathons in 2026: [AgroBuy](https://github.com/FrancoCazal/AgroBuy), 1st place at San Lorenzo x FIUNA Deep Dive (April), and [SilentOps](https://github.com/FrancoCazal/SilentOps) at the Agents, Everywhere global hackathon (September).
- Community: member of AI Tinkerers San Lorenzo and the FIUNA computing club, volunteer at AWS UG Paraguay, attendee at AI Tinkerers Asunción and GDG Asunción.

---

## Education & certifications

**Certifications** · AWS Certified Solutions Architect – Associate (2026) · AWS Certified AI Practitioner (2026) · AWS Certified Cloud Practitioner (2026)

**Degrees & diplomas**
- Diploma in Machine Learning & Deep Learning · FIUNA · completed 2026 · capstone: [Blindside](https://github.com/FrancoCazal/Blindside)
- Industrial Engineering · FIUNA · since 2022 · expected 2027

**Courses**
- Anthropic Academy · Claude API, Claude Code, MCP, agent design · 2025
- Python and Cloud Computing (AWS) · CoderHouse · 2024

**Self-taught** · Django REST Framework · FastAPI · LangGraph · GraphQL, from the docs and shipped projects

---

## Contact

- Email · [contact@francocazal.com](mailto:contact@francocazal.com)
- LinkedIn · [linkedin.com/in/francocazal](https://www.linkedin.com/in/francocazal)
- GitHub · [@FrancoCazal](https://github.com/FrancoCazal)
- Portfolio site · [francocazal.com](https://francocazal.com) (English, with every page in Spanish under `/es`)
- Languages · English (C2) · Spanish (native)

---

<sub>This is my portfolio repo: depth on featured work. For the quick view see <a href="https://github.com/FrancoCazal">my profile</a>. For the full experience see <a href="https://francocazal.com">francocazal.com</a>. Every featured project links to its public repo, except Focal Point: its code is private and it has a public case study.</sub>
