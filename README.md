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

### 1. Featured System Architecture: [Enterprise Context Scout (`v1.0.0`)](https://github.com/himanshu2408/enterprise-context-scout)

Self-hosted, cloud- and model-agnostic **Enterprise Context Control Plane** for private VPCs and air-gapped Kubernetes clusters (`Google ADK 2.x` 3-graph orchestrator, Stateless Streamable HTTP `MCP 2026-07-28`, `PostgreSQL 17` with `23/23` `FORCE ROW LEVEL SECURITY` tables + `halfvec(D)` blue/green HNSW, `Zoekt RE2`, 12-language `tree-sitter` & `SCIP`, `vLLM`/`SGLang`/`mlx-lm`, and air-gapped strict TypeScript/React). Sits in front of IDE MCP clients and internal engineering assistants to resolve multi-repo codebases and enterprise wikis locally at `$0` API cost—verifying every symbol and citation deterministically before synthesis and abstaining at `$0.00` paid tokens when indexed evidence is insufficient ([`L1`–`L12` GA Release Scorecard](https://github.com/himanshu2408/enterprise-context-scout/blob/main/reports/v1_ga_release_scorecard.md)).

| Architectural Pillar | Production Implementation (`v1.0.0` GA) | Measured Result *(Explicit $N$, Method & Caveats)* |
| :--- | :--- | :--- |
| **Tiered Token Economics & Governed BYO Model Plane** | Decouples **`$0` self-hosted discovery** (`Gemma 4 26B-A4B` MoE default + governed BYO `Qwen3`/`Devstral`/`DeepSeek`/`Llama 4`/`Granite` via `vLLM`/`mlx-lm` + `OWASP ASI06` `rsLoRA` cartridges & Cosign `AdapterSyncSidecar`) from 5-format IDE handoff or opt-in keyless Vertex AI execution | **`81.96%` fewer median input tokens** (`4,898` vs. `26,509`) & **`30/30` vs. `6/30` Symbol `Recall@5`** on `N=30` unseen `httpx`/`click` PRs · **`91.35%` fewer median input tokens** (`1,949` vs. `17,473`; `0` vs. `96` search turns) on `N=30` live `Gemini 3.8 Flash` A/B *(`27/30` initial strict audit, `30/30` post-fix re-run — caveats in repo)* |
| **5-Pillar Code & Document Retrieval (`3-Graph ADK`)** | `Zoekt RE2` $O(n)$ trigram search + Copy-on-Write MR/PR overlays (`ref_snapshots`), 12-language `tree-sitter` & `SCIP` call graphs + cross-boundary contracts, `PG17 halfvec(D)` blue/green HNSW, `BM25` + disjunctive `glossary.yaml` + self-hosted `Docling` tables, and Pillar-5 AST `side_effects` + `ConflictDetector` | **`10,000`-page Confluence wiki (`N=71`):** `12/12` noise rejection, `27/27` v3 freshness, `10/10` 2026-vs-2023 conflicts, `10/10` `Docling` tables, `0/51` wrongful refusals (`p50 = 541 ms`) · **`59/60` (`98.33%`)** `Recall@5` across 50 polyglot repos *(`anyio` train-overlap disclosed in repo)* |
| **Headless Stateless HTTP MCP (`2026-07-28`) & `$0` Gate** | Stateless Streamable HTTP MCP (`/mcp/code/mcp` 14 tools, `/mcp/docs/mcp` 3 tools, `/.well-known/mcp`), `SessionCompactor` commit-drift detection, deterministic `PreFlightValidator` + exact NFKC `ClaimVerifier` (`$0` bounce-back & `paid_tokens_spent = 0` abstention), and air-gapped 3-persona React Workbench | **`60 of 60` (`100%`) live-MLX `verify-backend` middleware cases** (`24` grounded across 4 domains, `14` `$0` out-of-domain/decoy abstentions, `6` MCP/MR/handoff flows, `4` RBAC/WORM audit, `12` foundational/federated) · **`63 of 63` local browser requests (`0` external egress)** |
| **Kernel `FORCE RLS`, `<60s` ACLs/Purge & `OWASP ASI01`–`ASI10`** | `23 of 23` PG17 tables under `FORCE ROW LEVEL SECURITY` (`NOBYPASSRLS`, `squawk`-clean Alembic `0001`–`0023`), Cloud IAP (`ES256`)/OIDC/SCIM 2.0, WORM hash-chained SIEM audit + EU `BetrVG §87` pseudonymization, `<60s` GitLab/GitHub/Confluence/Jira ACL sync & purge, 128-bit XML nonces + `<=31 ms` HTML5 guardrails, and **zero host RCE (`ASI05`)** | **`0 of 22` red-team RBAC leaks** · **`0 of 50` concurrent mixed-tenant (`25` SSE + `25` MCP) leaks** · **`22 of 22` injection/secret payloads blocked** · **`21 of 21` `OWASP ASI01`–`ASI10` matrix** (`0` `shell=True`, `custom_patch` & host `pytest` blocked) |
| **Zero-Skip Release Engineering, Fuzzing & Keyless GKE IaC** | Distroless non-root (`uid=65532`) containers, keyless GKE Workload Identity Terraform/Helm (`0` SA keys, Cloud SQL PSC IAM auth, AWS/Azure/On-Prem overlays), 4-plane PITR `StateReconciler`, Sigstore-verified CycloneDX `1.6` AI-BOM (`97` components), Schemathesis OpenAPI fuzzing, and AST/`mutmut` mutation gates | **`1,045/1,045` Python `pytest` (`84` modules, `0` skips)** + **`75/75` strict-TS `vitest` (`10` suites, `0` skips)** · **`62/62` Schemathesis OpenAPI subtests (`0` 5xx)** · **`406/456` (`89.04%`) AST & `529/529` (`100%`) `mutmut` mutation kill rates** |

---

### 2. Engineering Post-Mortem & Champion/Challenger Case Study: [NIFTY 200 EOD Quantitative Engine & AI Research Gate (`nifty-eod-dashboard`)](https://github.com/himanshu2408/nifty-eod-dashboard)

Encrypted live telemetry repository ([`index.html` Champion](https://himanshu2408.github.io/nifty-eod-dashboard/) vs. [`challenger.html` Challenger](https://himanshu2408.github.io/nifty-eod-dashboard/challenger.html)) and full systems engineering post-mortem documenting how our initial `v2.1.0` quantitative engine failed in point-in-time evaluation—and how we re-engineered both the causal execution engine and the bitemporal **`gemini-3.8-flash`** pre-market risk gate:

| Engineering Stage | Root Causes & Architectural Intervention | Verified Point-in-Time Result (`2021–2026` Nifty 200) |
| :--- | :--- | :--- |
| **1. Forensic Audit of `v2.1.0` Failure** | Uncovered **5 compounding defects**: (a) a weekend unauthorized fill anomaly caused by cache timestamp misattribution + a permissive same-day fill fallback without an exchange trading-hours gate; (b) pre-ranking alphabetical universe truncation (causing single-conglomerate concentration while dropping 85% of index constituents); (c) unnormalized concentration-cap clipping that left **68.4% of capital in `0.0%` dead cash**; (d) a missing rank cutoff in the live execution path; and (e) naive $P_T^{\text{close}}$ lookahead and survivorship bias. | **`3.06%` CAGR** (`2.48%` post-tax) · **`-1.66%` Net Alpha** · **Sharpe `-0.461`** ($R_f=6.0\%$) · **`31.6%` Avg Capital Deployed** across 482 trades |
| **2. Causal Walk-Forward OOS Multi-Pod Rebuild** | Rebuilt around a **zero-survivorship 240-stock Point-in-Time Nifty 200 registry** (including all 40 exited/delisted constituents, listing-maturity & liquidity filters), strict **$T \to T+1$ next-day open execution ($P_{T+1}^{\text{open}}$)** in SQLite WAL, **~51.5 bps round-trip statutory Indian delivery friction** (`0.10%` STT buy/sell, stamp duty, SEBI/NSE fees, GST, DP charges), and water-filling inverse-volatility sizing across uncorrelated **Momentum**, **Stage-2 Breakout**, and **Defensive Reserve** pods. | **`14.19%` CAGR** (`11.87%` post-tax, **`+91.58%`** net vs. `+25.40%` Nifty 50) · **`+9.47%` Annualized Net Alpha** · **Sharpe `0.615`** · **Max DD `10.92%`** · **Calmar `1.299`** across 429 trades |
| **3. Bitemporal `gemini-3.8-flash` AI Research Gate** | Pre-open agentic risk gate over a **bitemporal SQLite evidence store** (`published_at_utc <= as_of_utc AND ingested_at_utc <= as_of_utc`, enforced via static AST regression gate in CI). Combines deterministic **0-LLM pre-gates** (scheduled board earnings blackout window & exchange surveillance filters) with a **Neutral Prosecutor + Heuer ACH ($H_1/H_2/H_3$) Critic**, verbatim quote substring verification, and **Champion (`SHADOW`) vs. Challenger (`FULL`)** live telemetry. | Eliminates LLM temporal lookahead; enforces **pre-open vetoes**, **defensive haircuts**, and **Two-Key overnight surveillance** without overriding sovereign trailing stops |
| **4. Architectural Transfer $\to$ `enterprise-context-scout`** | Directly motivated the deterministic **Market-Regime Quant Scepticism Gate** packaged as an isolated reference `DomainPlugin` ([`examples/quant_dogfood/`](https://github.com/himanshu2408/enterprise-context-scout/tree/main/examples/quant_dogfood), zero core engine coupling) in [`enterprise-context-scout`](https://github.com/himanshu2408/enterprise-context-scout), auditing retrieved quantitative papers for $\ge 15\text{ bps}$ `IN_NSE` statutory delivery friction, point-in-time survivorship controls, and overnight gap/circuit constraints. | Proves custom domain-contract extensibility while blocking frictionless same-bar close backtests |

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

- **Agentic AI & Retrieval:** Google ADK 2.x (`Workflow` DAGs), Model Context Protocol (`MCP` Stateless Streamable HTTP `2026-07-28` & `stdio`), 5-Pillar Hybrid RAG (Anthropic Contextual Retrieval, `Zoekt RE2`, BM25 + `halfvec` HNSW RRF, Cross-Encoder Reranking, `Docling`), 12-Language `tree-sitter` & `SCIP` Code Graphs, `vLLM` Multi-LoRA & `rsLoRA` Specialization (`PEFT` / `MLX`), OpenTelemetry GenAI Tracing, Automated LLM Evaluation & Mutation Gates.
- **Languages & Backend:** Python 3.12 (`FastAPI`, `Pydantic v2`, `psycopg 3`, `Alembic`, `pytest`, `mypy --strict`, `ruff`, `uv`), TypeScript (`strict` mode), C# / ASP.NET Core Web API, PostgreSQL 17 (`pgvector` `halfvec`, `pg_trgm`, `FORCE ROW LEVEL SECURITY`), GraphQL.
- **Cloud, Security & Frontend:** Google Cloud Platform (GKE, Cloud SQL PSC, Vertex AI / Gemini Enterprise Agent Platform, Cloud IAP, Cloud Armor, Workload Identity Federation, Model Armor), SCIM 2.0, Docker, Kubernetes, Terraform, Helm, GitLab CI/CD, GitHub Actions, React 19, Angular (Module Federation).
