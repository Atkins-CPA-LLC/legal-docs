<!--
DRAFT — 2026-06-14. Item A5 of the client-rollout plan (vendor / subprocessor register).
NOT legal advice; attorney review recommended alongside A1–A3 before the first client signature.
Satisfies AICPA ET 1.700.040(a) + ET 1.700.005.02 (must be able to DEMONSTRATE safeguards) and is the
"belt" under the Texas §501.75 written-consent "suspenders." Maps 1:1 to the A1 consent-clause categories.
Cite trail for the reviewer is in HTML comments throughout. Update review dates as DPAs are executed.
-->

# Vendor / Subprocessor Register — Ask Your Books

**Ask Your Books, a service of Atkins CPA, LLC** · **Maintained by:** Atkins CPA, LLC (Allen, TX)
**Register version:** DRAFT 2026-06-14 · **Default annual review:** each June (next full review: 2027-06)

This register lists every third party that touches Client accounting or financial information through the
Ask Your Books ("AYB") platform, the category of data it touches, its confidentiality / DPA posture, the
controls evidence on file, and the date of next annual review. It is the Firm's record that it can
*demonstrate* the safeguards it relies on, and it pairs with the written-consent clause in the
engagement-letter Addendum (item A1), which obtains Client consent by **provider category** rather than by
naming individual vendors — so the categories below mirror that clause exactly.

<!-- ET 1.700.040(a) (vendor confidentiality contract + reasonable assurance path); ET 1.700.005.02
     (demonstrate safeguards); FTC 314.4(f) vendor oversight (retained for snap-back). ET 1.300.040
     supervision duty applies REGARDLESS of consent — this register is that supervision evidence. -->

## Provider categories (cross-reference to A1 consent clause)

| A1 consent category | Vendors in this register |
|---|---|
| Cloud hosting & infrastructure | Supabase (on AWS), Vercel, Cloudflare, E2B |
| AI / LLM processing | OpenRouter, Anthropic + downstream models (OpenAI, Google) |
| Bank-data aggregation | Plaid |
| Practice-management / workflow tools | Intuit (QuickBooks Online), n8n / Hostinger VPS, Microsoft (Outlook), Telegram |
| IT / managed-security service providers | Managed Security Provider (MSP) |

## Register

| Vendor | Data touched | Confidentiality / DPA terms | SOC 2 / controls evidence | Annual review |
|---|---|---|---|---|
| **Supabase** (hosted on AWS) | Everything — Postgres database, auth, and file storage (the full Client books, uploads, chat history, memory) | DPA + confidentiality terms to **confirm and file**; confirm paid plan tier; backup/PITR posture tracked under A8 | SOC 2 Type II (Supabase) + AWS SOC 2 / ISO 27001 underneath — **obtain and file reports** | 2027-06 |
| **Vercel** | Application hosting, edge network, environment variables (no Client books stored at rest; serves the app + holds secrets) | Standard Vercel DPA — **execute / confirm on file** | SOC 2 Type II — **obtain and file** | 2027-06 |
| **OpenRouter** | AI chat queries + financial excerpts passed through the router to model providers | Account-level **no-logging / no-training** routing to be verified in dashboard (Workstream C5); ZDR routing (`zdr: true`) pinned in application code | Vendor attestation + dashboard screenshot of privacy/routing settings (C5) on file | 2027-06 |
| **Anthropic** + downstream models (**OpenAI, Google**) | AI chat queries + financial excerpts (model inference) | **Execute Anthropic's self-serve DPA — REQUIRED. Status: NOT YET EXECUTED (target 2026-06; record execution date here on completion).** Document no-training default + up-to-30-day retention; newest models excluded from full ZDR | Anthropic Commercial Terms + retention docs; provider SOC 2 / trust reports as available — file with the executed DPA | 2027-06 |
| **Intuit** (QuickBooks Online) | QBO OAuth tokens + the full Client books (source of synced data) | Covered by Intuit Developer / API terms; Intuit App Assessment under C2 (verify whether existing production keys ever passed the assessment) | Intuit platform SOC reports / trust posture; App Assessment outcome on file | 2027-06 |
| **Plaid** | Bank-credential-adjacent tokens + bank transactions (**sandbox-only today**; production gated on Decision Gate 1 — currently NO-GO) | Plaid MSA executed at production approval (C1); privacy policy must disclose Plaid + link `plaid.com/legal` (A2) | Plaid SOC 2 — obtain at production onboarding | 2027-06 |
| **E2B** (FoundryLabs, Inc., DE) | **Raw transaction rows (up to 25,000) sent to ephemeral sandboxes for report-generation code** — the *most granular* Client data of any vendor here | **PATH A (DPA) — viable + self-serve.** DPA, SOC 2 Type II, pentest + insurance COI are all available via E2B's Vanta Trust Center (request access at trust.e2b.dev; security@e2b.dev). **DPA ON FILE** — `legal-docs/vendor-contracts/E2B-FoundryLabs-DPA.pdf` (executed 2026-06-18 — confirmed). GDPR/CCPA/UK DPA — E2B = Processor / Atkins = Controller (§2.1); purpose-limited, no-sale of data (§2.2); Personnel + subprocessors under confidentiality (§2.5); **delete/return all Personal Data on termination** (§2.6); **breach notice without undue delay** (§6.1); EU+UK SCCs incorporated for restricted transfers (§8); annual audit right, 30-day notice (§3); US processing. Compensating controls already LIVE in code: `allowInternetAccess:false` (no egress) **and** an explicit `sandbox.kill()` in a `finally` block after every task (runs even on error — data is not left to idle into a persisted "paused" microVM). | **DPA Annex C TOMs:** TLS 1.2 in transit + AES-256 at rest (AWS); **SOC 2 Type II (annual) + ISO 27001-compliant ISMS** contractually committed; MFA/SSO for prod access; daily/weekly/monthly backups. **SOC 2 Type II ON FILE** (`legal-docs/vendor-contracts/E2B-FoundryLabs-SOC2-Type-II.pdf`) — Johanson Group LLP, period **Jun 11–Sep 10 2025**, **clean/unqualified opinion**, Security (Common Criteria); **scope = the E2B sandbox platform that runs AI-generated code — i.e., it covers our processing runtime ✅**; GCP cloud hosting carved out (its own SOC 2); complementary user-entity controls (CUECs) apply. | **DPA + SOC 2 Type II on file ✅. Re-review 2027-06 (next SOC 2)** |
| **n8n / Hostinger VPS** | QBO sync payloads + Client financial data in flight (sync orchestration); Outlook/Telegram alert routing | Self-hosted n8n on a Hostinger VPS — **paper the VPS host** (Hostinger DPA/terms on file); credentials held in n8n, not Vercel | Hostinger DPA/terms; self-hosted control narrative (who can access the VPS) on file | 2027-06 |
| **Microsoft** (Outlook) | Email contents (Firm/Client correspondence sent via n8n + native Outlook credential) | Standard Microsoft 365 / Online Services terms + DPA — confirm on file | Microsoft SOC 2 / ISO 27001 (publicly available) — file reference | 2027-06 |
| **Telegram** | **Alert text currently includes Client names** (per Decision Gate 5: names **kept**, so Telegram is papered as a data-touching vendor — not stripped to IDs) | Standard Telegram terms — **papered here as a data-touching vendor per Gate 5**; added to the A1 consent-clause categories. Re-evaluate if alert content scope expands | Limited vendor assurance; documented decision (Gate 5, 2026-06-12) is the compensating control + rationale (Ops push is counts-only; Telegram alerts preserve which-client traceability) | 2027-06 |
| **Cloudflare** | Traffic metadata (in front of the app; no Client books at rest) | Standard Cloudflare DPA — confirm on file | SOC 2 Type II / ISO 27001 (publicly available) — file reference | 2027-06 |
| **Managed Security Provider (MSP)** | Whatever the MSP's monitoring/agents touch — likely office endpoints + email; **possibly Client data at rest** (scope to be confirmed) | Confidentiality terms in the MSP's MSA; **confirm scope incl./excl. the AYB cloud stack (Supabase/Vercel) vs office endpoints only** (A4 scope check — get the answer in writing); added to the A1 consent-clause categories | MSP attestation / scope statement in writing (also supports the C4 insurer call) | 2027-06 |

<!-- Telegram row reflects Gate 5 = KEEP names + paper as vendor (decided 2026-06-12). E2B row carries an
     explicit, mandatory resolution. Anthropic self-serve DPA execution is flagged NOT-YET-EXECUTED with a
     date placeholder. All 11 vendor rows present (Supabase, Vercel, OpenRouter, Anthropic+downstream,
     Intuit, Plaid, E2B, n8n/Hostinger, Microsoft/Outlook, Telegram, Cloudflare, MSP). -->

## Open items (must close before the first friendly client)

1. **E2B:** ✅ **CLOSED** — DPA **executed 2026-06-18** + **SOC 2 Type II on file** (Johanson Group LLP, period Jun 11–Sep 10 2025, clean opinion, **scope covers the E2B sandbox runtime** where our data is processed). Both filed in `legal-docs/vendor-contracts/`. E2B subprocessors (DPA Annex B): Google, Vercel, Supabase, Cloudflare, PostHog, Stripe — the hosting ones sit inside our already-consented "cloud hosting & infrastructure" category, no new consent gap. Data-minimization (Path B) NOT needed — controls (no egress + kill-on-completion) + DPA + SOC 2 suffice. Minor non-blocking follow-ups: initial SOC 2 window is short (~3 mo) → expect a longer next report; review the report's CUECs (our egress-off + kill-on-completion + AES-256-GCM token encryption align with the user-entity responsibilities).
2. **Anthropic self-serve DPA:** execute and record the execution date in the register row.
3. **OpenRouter (C5):** verify account-level no-logging / no-training routing; file the dashboard screenshot.
4. **MSP scope (A4):** confirm in writing whether the MSP covers the AYB cloud stack or only office endpoints/email.
5. **Plaid:** no action while Gate 1 = NO-GO (sandbox only); execute the MSA only if/when bank-feed goes to production.
6. **Confirm & file DPAs / SOC 2 reports** for Supabase, Vercel, Cloudflare, Microsoft, Hostinger.

<!--
ACCEPTANCE CRITERIA (from 2026-06-10 plan A5):
  - All 11 rows present ✓ (Supabase, Vercel, OpenRouter, Anthropic+downstream, Intuit, Plaid, E2B,
    n8n/Hostinger, Microsoft/Outlook, Telegram, Cloudflare, MSP)
  - E2B row carries an explicit resolution (DPA/retention review OR data minimization; MANDATORY before clients) ✓
  - Anthropic DPA execution noted with a date placeholder (flagged NOT-YET-EXECUTED, target 2026-06) ✓
  - Telegram row reflects Gate 5 outcome (KEEP names + paper as vendor) ✓
Columns per spec: vendor → data touched → confidentiality/DPA terms → SOC 2 evidence → annual review date ✓
-->
