<div align="center">
  <h1>Himanshu Singh</h1>
  <p><strong>Senior Software Engineer — Agentic AI Architectures & Multi-Tenant Cloud Platforms</strong></p>
  <p>Berlin, Germany · B.Tech, IIT Guwahati · <a href="https://www.linkedin.com/in/himanshu-s">LinkedIn</a> · <a href="https://www.credly.com/users/himanshu2408/">Verified Credentials (Credly)</a> · <a href="mailto:singhhimanshu2408@gmail.com">singhhimanshu2408@gmail.com</a></p>
</div>

---

### Engineering Profile

Senior Software Engineer with **9 years of production experience** designing and operating cloud-native, multi-tenant distributed systems on **Google Cloud Platform (GCP)** and architecting production-grade **AI agent systems** (**Google ADK 2.x**, **Model Context Protocol (MCP)**, deterministic pre-flight guardrails, and automated CI/CD evaluation gates).

- **Enterprise Platform Architecture (dunnhumby, 2020–Present):** Lead technical discovery, system architecture, and end-to-end delivery for **DH Sphere**, a multi-tenant retail media platform across in-store digital signage, point-of-sale, and offsite advertising integrations (**Google Ad Manager**, **Meta Marketing API**, and third-party signage CMS providers). Build and evaluate internal agentic workflows on Google Cloud (ADK 2.x, Python, MCP servers, automated evaluation pipelines) and serve on the production on-call rotation.
- **Enterprise Client Delivery (Nagarro, 2017–2020):** Promoted from Trainee to Senior Engineer; architected a global enterprise workflow platform and led the **2-week on-site production launch in Hong Kong**, owning stakeholder discovery, user onboarding, knowledge transfer, and live cutover support.

---

### 1. Featured System Architecture: [Enterprise Context Scout](https://github.com/himanshu2408/enterprise-context-scout)

Local-first context discovery for coding agents (`Gemma 4` open-weights local exploration, `Google ADK`, `MCP`, `PostgreSQL 17` with `pgvector`, `pg_trgm`, and `FORCE ROW LEVEL SECURITY`, FastAPI SSE, and strict TypeScript/React). A small open-weights model explores the repository at \$0 API cost; a 4-check deterministic pre-flight gate verifies the result; only then does one paid Gemini call run on a compact `ContextPack`.

| Architectural Pillar | Production Implementation | Measured Result *(Small Golden Set — See Repo Limitations)* |
| :--- | :--- | :--- |
| **Tiered Token Economics** | Decouples **\$0 local discovery** (`Gemma 4` MoE + in-memory rank-16 QLoRA adapter hot-swap in `0.018 ms`) from **1-shot paid execution** on a compact `2k–4k` token `ContextPack` | **~80% fewer paid input tokens** vs. raw-repo context *(estimated counterfactual; unseen-repo A/B baseline in progress)* |
| **Code Intelligence Engine (Primary Domain)** | Git Blob-SHA Merkle incremental indexing + `tree-sitter` Python/TypeScript AST graph + bounded 1-hop dependency closure ($\le 3$ callers, $\le 1,500$ tokens) + byte-exact `DeterministicSlicer` | **`< 40 ms` incremental Merkle sync** · **10 of 10 (100%) File & Symbol Recall@5** *(own-repo golden set)* |
| **Research Retrieval Engine (Second Domain)** | Demonstrates declarative `DomainPack` extensibility over 300 arXiv/OpenAlex papers (`IN_NSE`, `DE_XETRA`, `US_EQUITY` — 14,331 chunks) + Anthropic Contextual Retrieval + 3-way Normalized RRF (`BM25` + `pgvector` + `pg_trgm`) | **10 of 10 (100%) Zero-Touch Sufficiency & NFKC Verbatim Citation Overlap** ($\ge 0.98$, deterministic check) |
| **Kernel-Level Multi-Tenant Security** | Out-of-band `PrincipalContext` binding via `contextvars` in MCP servers (zero identity parameters in LLM prompts) + PostgreSQL 17 `FORCE ROW LEVEL SECURITY` (`non-superuser` app role) + `ShieldGemma 2` guardrails | **0 of 22 cross-role RBAC leaks** (live PostgreSQL 17 `FORCE RLS`) · **21 of 22 prompt-injection payloads blocked** (`95.45%`, 1 miss documented) |
| **Verification & CI/CD Gates** | 6-gate automated evaluation harness on every PR, OpenTelemetry GenAI semantic traces, isolated `GitWorktreeSandbox` with `require_confirmation=True` human-in-the-loop write approval | **537/537 Python tests + 43/43 strict-TS Vitest tests passing** (`0` `mypy --strict` / `ruff` / `eslint` errors) |

---

### 2. Engineering Post-Mortem & Champion/Challenger Case Study: [NIFTY 200 EOD Quantitative Engine & AI Research Gate (`nifty-eod-dashboard`)](https://github.com/himanshu2408/nifty-eod-dashboard)

Encrypted live telemetry repository ([`index.html` Champion](https://himanshu2408.github.io/nifty-eod-dashboard/) vs. [`challenger.html` Challenger](https://himanshu2408.github.io/nifty-eod-dashboard/challenger.html)) and full systems engineering post-mortem documenting how our initial `v2.1.0` quantitative engine failed in point-in-time evaluation—and how we re-engineered both the causal execution engine and the bitemporal **`gemini-3.8-flash`** pre-market risk gate:

| Engineering Stage | Root Causes & Architectural Intervention | Verified Point-in-Time Result (`2021–2026` Nifty 200) |
| :--- | :--- | :--- |
| **1. Forensic Audit of `v2.1.0` Failure** | Uncovered **5 compounding defects**: (a) a weekend unauthorized fill anomaly caused by cache timestamp misattribution + a permissive same-day fill fallback without an exchange trading-hours gate; (b) pre-ranking alphabetical universe truncation (causing single-conglomerate concentration while dropping 85% of index constituents); (c) unnormalized concentration-cap clipping that left **68.4% of capital in `0.0%` dead cash**; (d) a missing rank cutoff in the live execution path; and (e) naive $P_T^{\text{close}}$ lookahead and survivorship bias. | **`3.06%` CAGR** (`2.48%` post-tax) · **`-1.66%` Net Alpha** · **Sharpe `-0.461`** ($R_f=6.0\%$) · **`31.6%` Avg Capital Deployed** across 482 trades |
| **2. Causal Walk-Forward OOS Multi-Pod Rebuild** | Rebuilt around a **zero-survivorship 240-stock Point-in-Time Nifty 200 registry** (including all 40 exited/delisted constituents, listing-maturity & liquidity filters), strict **$T \to T+1$ next-day open execution ($P_{T+1}^{\text{open}}$)** in SQLite WAL, **~51.5 bps round-trip statutory Indian delivery friction** (`0.10%` STT buy/sell, stamp duty, SEBI/NSE fees, GST, DP charges), and water-filling inverse-volatility sizing across uncorrelated **Momentum**, **Stage-2 Breakout**, and **Defensive Reserve** pods. | **`14.19%` CAGR** (`11.87%` post-tax, **`+91.58%`** net vs. `+25.40%` Nifty 50) · **`+9.47%` Annualized Net Alpha** · **Sharpe `0.615`** · **Max DD `10.92%`** · **Calmar `1.299`** across 429 trades |
| **3. Bitemporal `gemini-3.8-flash` AI Research Gate** | Pre-open agentic risk gate over a **bitemporal SQLite evidence store** (`published_at_utc <= as_of_utc AND ingested_at_utc <= as_of_utc`, enforced via static AST regression gate in CI). Combines deterministic **0-LLM pre-gates** (scheduled board earnings blackout window & exchange surveillance filters) with a **Neutral Prosecutor + Heuer ACH ($H_1/H_2/H_3$) Critic**, verbatim quote substring verification, and **Champion (`SHADOW`) vs. Challenger (`FULL`)** live telemetry. | Eliminates LLM temporal lookahead; enforces **pre-open vetoes**, **defensive haircuts**, and **Two-Key overnight surveillance** without overriding sovereign trailing stops |
| **4. Architectural Transfer $\to$ `enterprise-context-scout`** | Directly motivated the deterministic **Market-Regime Quant Scepticism Gate** in [`enterprise-context-scout`](https://github.com/himanshu2408/enterprise-context-scout), which automatically audits retrieved quantitative papers for $\ge 15\text{ bps}$ `IN_NSE` statutory delivery friction, point-in-time survivorship controls, and overnight gap/circuit constraints. | Prevents frictionless same-bar close backtests from passing research verification gates |

---

### Google Cloud Certifications

<div align="center">
  <a href="https://www.credly.com/badges/5b825ca6-927b-4c08-8c9d-77945be6600c/public_url" target="_blank">
    <img src="professional-agentic-architect-certification.png" alt="Google Cloud Certified Professional Agentic Architect" width="150" />
  </a>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://www.credly.com/badges/6e869054-b3cf-4f6a-9fef-46c2806263b3/public_url" target="_blank">
    <img src="associate-cloud-engineer-certification.png" alt="Google Cloud Certified Associate Cloud Engineer" width="150" />
  </a>
  <p>
    <a href="https://www.credly.com/badges/5b825ca6-927b-4c08-8c9d-77945be6600c/public_url"><strong>Google Cloud Certified — Professional Agentic Architect</strong></a> <em>(Proctored Exam + Hands-On Performance Labs, Nov 2026)</em><br/>
    <a href="https://www.credly.com/badges/6e869054-b3cf-4f6a-9fef-46c2806263b3/public_url"><strong>Google Cloud Certified — Associate Cloud Engineer</strong></a> <em>(May 2026)</em>
  </p>
</div>

---

### Core Technical Stack

- **Agentic AI & Retrieval:** Google ADK 2.x (`Workflow` DAGs), Model Context Protocol (`MCP` 2.3 `stdio` & Streamable HTTP), Hybrid RAG (Anthropic Contextual Retrieval, BM25 + `pgvector` HNSW Reciprocal Rank Fusion), `tree-sitter` AST Code Graphs, QLoRA Fine-Tuning (`MLX` / Vertex AI PEFT), OpenTelemetry GenAI Tracing, Automated LLM Evaluation Harnesses.
- **Languages & Backend:** Python 3.11+ (`FastAPI`, `Pydantic v2`, `psycopg 3`, `pytest`, `mypy --strict`, `ruff`, `uv`), TypeScript (`strict` mode), C# / ASP.NET Core Web API, PostgreSQL 17 (`pgvector`, `pg_trgm`, `FORCE ROW LEVEL SECURITY`), GraphQL.
- **Cloud, Security & Frontend:** Google Cloud Platform (Cloud Run, Vertex AI / Gemini Enterprise Agent Platform, GKE, BigQuery, Workload Identity Federation, Model Armor), Docker, Kubernetes, Terraform, GitLab CI/CD, GitHub Actions, React 18, Angular (Module Federation).
