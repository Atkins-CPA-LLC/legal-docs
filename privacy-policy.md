<!--
DRAFT — 2026-06-14. Item A2 of the client-rollout readiness plan (privacy policy refresh).
NOT legal advice; have a Texas attorney review A1–A3 together before the first client signature.
Every statement here must remain non-falsifiable against the current product (Next.js + Supabase
project hcxgwgxowuayqfuqrmac + Vercel at app.atkinscpafirm.com). Citations / reviewer notes are in
HTML comments. Mirrors the A1 addendum's provider categories, AI-disclaimer framing, and branding.
-->

# Privacy Policy

**Ask Your Books, a service of Atkins CPA, LLC**

*Last updated: June 14, 2026 (DRAFT — pending attorney review)*

<!-- 22 TAC §501.83(a)(2): the product must be presented under the licensed firm name. Branding line above mirrors the A1 addendum and is mandatory. -->

Atkins CPA, LLC ("Company," "Firm," "we," "us," or "our") operates **Ask Your Books** ("AYB" or the "Application") — a software application that synchronizes your accounting data and provides AI-assisted analysis as part of the Firm's bookkeeping and advisory services. This Privacy Policy describes how we collect, use, store, and protect your information when you use the Application.

## 1. Information We Collect

### Account Information
- Email address and password, used to authenticate your identity and manage your account.
- Name and business association (managed by your administrator).

<!-- A2 change #4: auth is email + password (Supabase Auth password sign-in). The prior "magic link only" claim was false and is removed. -->

### Financial Data
- **QuickBooks Online (QBO) data** synced to our secure database, including:
  - Profit and loss reports
  - Balance sheet data
  - Cash flow statements
  - Transaction records (invoices, payments, purchases, bills)
  - Accounts receivable and payable aging
  - Chart of accounts and account balances
- This data is synced from your authorized QuickBooks Online account with your consent via OAuth 2.0 authorization.

### Bank Data (Plaid)
- Where bank-feed features are enabled for your account, we use **Plaid Inc.** ("Plaid") to connect to your financial institutions and retrieve bank-account and transaction information.
- When you link an account through Plaid, you provide your credentials directly to Plaid; we do not see or store your online-banking username or password. We receive Plaid-issued access tokens and the account, balance, and transaction data you authorize.
- Plaid's handling of your information is governed by Plaid's own end-user privacy policy. Please review it at **[https://plaid.com/legal](https://plaid.com/legal)**.

<!-- A2 change #1 (Plaid production requirement): the verbatim conspicuous link to plaid.com/legal MUST stay present. Plaid is sandbox-only today; this disclosure is gated to "where bank-feed features are enabled." -->

### File Uploads
- The Application allows you to attach files (such as documents or images) to your chat conversations. Any files you upload are stored in our secure file storage and associated with your account so they remain available within your conversation history.

<!-- A2 change #2: chat attachments exist in schema/storage even though the AI model does not currently read them. Statement is scoped to storage + availability, not AI processing, so it stays non-falsifiable. -->

### Usage and Memory Data
- **Chat conversation history** — the questions you ask and the AI responses you receive.
- **Persistent memory** — business context, preferences, and facts that you or the Firm provide, or that the Application derives from your conversations, which we store so the Application can personalize and improve the relevance of future responses.

<!-- A2 change #3: persistent memory covers client_memory (v1) + memory_entries (v2). -->

### Technical Data
- We collect limited technical information necessary to operate the service, including session and authentication data and basic system logs used for security, troubleshooting, and monitoring system health.

## 2. How We Use Your Information

We use your information to:

- Authenticate your identity and manage your account;
- Sync and store your QuickBooks Online and (where enabled) Plaid bank data for querying;
- Process your natural-language questions using AI models;
- Maintain conversation history and uploaded files for context in ongoing chats;
- Store business context, preferences, and memory you or the Firm provide to personalize responses;
- Deliver the Firm's bookkeeping and advisory services; and
- Monitor system health, secure the service, and troubleshoot errors.

## 3. Third-Party AI Processing

When you ask a question in the Application, your query and relevant financial-data excerpts are sent to third-party AI providers for processing. These providers are accessed through **OpenRouter**, an AI API routing service, which directs requests to underlying model providers including:

- **Anthropic** (Claude models)
- **OpenAI** (GPT models)
- **Google** (Gemini models)

**Training and retention.** Our agreements and the API terms governing these AI providers **contractually bar them from using your data to train their models.** Your data is sent only to generate a response to your specific request. These providers may, however, **retain submitted data for a limited period (generally up to 30 days)** for purposes such as abuse monitoring, security, and legal compliance before deletion. We do **not** represent that these providers retain none of your data.

<!-- A2 change #5 (MANDATORY accuracy fix): no zero-retention claim. Anthropic Commercial Terms = no-training default + up to 30-day retention; newest models excluded from full ZDR. OpenRouter is ZDR-pinned in code but the honest provider-level statement is "no training + up to 30 days." -->

## 4. Data Storage and Security

- Financial data is stored in **Supabase** (a PostgreSQL database hosted on Amazon Web Services). Uploaded files are stored in our secure object storage.
- To generate certain reports, the Application runs code in **isolated, ephemeral cloud compute sandboxes** (provided by **E2B**). Raw transaction rows are processed transiently inside a sandbox to produce the report; the sandbox has **no outbound internet access**.
- Sensitive credentials, including QuickBooks Online and Plaid access tokens, are encrypted at the application tier using **AES-256-GCM** authenticated encryption with key versioning before they are stored.
- **Row-Level Security (RLS)** is enforced at the database level, ensuring you can only access data associated with your authorized client account.
- Authentication is handled by **Supabase Auth** using secure, httpOnly session cookies.
- Data is transmitted over **HTTPS (TLS)** at all times.

<!-- A2 change #6: encryption corrected from "pgcrypto (AES-256 symmetric)" to app-tier AES-256-GCM with key versioning (current prod). Storage now includes uploaded files. -->

## 5. Data Retention

- Your financial and bank data is retained as long as your account is active and your QuickBooks Online and/or Plaid connections are authorized.
- Chat conversation history, uploaded files, and stored memory are retained for your reference unless you request deletion.
- The third-party AI providers described in Section 3 may retain submitted data for a limited period (generally up to 30 days) as described above.
- If your account is terminated, your data stored by the Application will be deleted within **30 days**, except where retention is required by law or by the Firm's professional record-retention obligations.

## 6. Data Sharing

We do not sell, rent, or trade your personal or financial information. We share data only in the following circumstances:

- **Cloud hosting & infrastructure:** database, authentication, and file-storage providers and the application-hosting platform store your data so the service can operate (Section 4).
- **AI/LLM processing:** query data and financial excerpts are sent to the AI routing and model providers described in Section 3.
- **Bank-data aggregation:** where enabled, account and transaction data is exchanged with Plaid as described in Section 1.
- **QuickBooks Online:** we access your QBO data through Intuit's official API under your OAuth authorization.
- **Firm operations and security:** practice-management/workflow tools and information-technology and managed-security providers that support the Firm's systems.
- **Legal requirements:** we may disclose information if required by law, legal process, or government request.

Each such provider is required, by contract, to keep your information confidential and to use it only as necessary to provide its services.

<!-- Provider categories mirror A1 addendum §1 (cloud hosting; AI/LLM; bank-data aggregation; practice-management/workflow; IT/managed-security). Texas governing rule is 22 TAC §501.75 (written client consent; no service-provider exception) — consent is obtained via the A1 engagement-letter addendum, not this policy. -->

## 7. AI-Assistance Disclaimer

AI-generated chat answers and analysis are **informational only**, may be inaccurate or incomplete, and **do not constitute professional, accounting, tax, legal, or investment advice** unless and until reviewed and validated by the Firm. You should not act on Application output without confirming it with the Firm.

<!-- Mirrors A1 addendum §2 and the in-app disclaimer (Workstream B5). Decision Gate 2 software-tool classification. -->

## 8. Your Rights

You have the right to:

- **Access** your stored financial data, conversation history, and uploaded files through the Application;
- **Request deletion** of your account and associated data by contacting us;
- **Revoke QuickBooks access** at any time (Section 9) and **disconnect Plaid bank connections** at any time through the Application or by contacting us; and
- **Request export** of your data in a machine-readable format.

## 9. QuickBooks Online Integration

- We access your QuickBooks Online data through **Intuit's official OAuth 2.0 API**.
- You authorize this access when you connect your QuickBooks account through our admin dashboard.
- We access only the data scopes authorized during the OAuth consent flow (`com.intuit.quickbooks.accounting`).
- You can revoke this access at any time by disconnecting the Application from your QuickBooks Online account (Settings → Apps → Manage apps in QuickBooks Online) or by contacting us.

## 10. Children's Privacy

The Application is not intended for use by individuals under the age of 18. We do not knowingly collect information from children.

## 11. Changes to This Policy

We may update this Privacy Policy from time to time. Changes will be posted to this page with an updated "Last updated" date. We encourage you to review this policy periodically.

## 12. Contact Us

If you have questions about this Privacy Policy or wish to exercise your data rights, contact us at:

**Atkins CPA, LLC**
337 Regency Dr
Allen, TX 75002
Email: hunter.atkins@atkinscpafirm.com

<!--
ACCEPTANCE CRITERIA (2026-06-10 plan A2): no statement falsifiable against the current product.
Checklist: Plaid disclosed ✓ + conspicuous link to https://plaid.com/legal present ✓ (§1, verbatim);
file uploads ✓ (§1, scoped to storage/availability — model can't read them yet); persistent memory ✓
(§1, client_memory + memory_entries); password authentication ✓ (§1, false magic-link claim removed);
ZDR overstatement fixed ✓ (§3 — no-training + up to 30-day retention, NO zero-retention claim);
Supabase/AWS + uploaded-file storage ✓, AES-256-GCM app-tier token encryption w/ key versioning ✓
(NOT pgcrypto), RLS ✓, HTTPS ✓, 30-day post-termination deletion ✓, QBO OAuth + revocation ✓,
contact block ✓. Provider categories + AI disclaimer + branding line consistent with A1 addendum.
-->
