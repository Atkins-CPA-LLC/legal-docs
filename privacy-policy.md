# Privacy Policy

**Atkins CPA Firm — AI Financial Analyst**

*Last updated: April 2, 2026*

Atkins CPA, LLC ("Company," "we," "us," or "our") operates the Atkins AI Financial Analyst application ("Application"). This Privacy Policy describes how we collect, use, store, and protect your information when you use our Application.

## 1. Information We Collect

### Account Information
- Email address (used for authentication via magic link login)
- Name and business association (managed by your administrator)

### Financial Data
- QuickBooks Online financial data synced to our secure database, including:
  - Profit and loss reports
  - Balance sheet data
  - Cash flow statements
  - Transaction records (invoices, payments, purchases, bills)
  - Accounts receivable and payable aging
  - Chart of accounts and account balances
- This data is synced from your authorized QuickBooks Online account with your consent via OAuth 2.0 authorization.

### Usage Data
- Chat conversation history (questions you ask and AI responses)
- Business context notes you provide through the Application ("client memory")

### Technical Data
- We do not collect browser fingerprints, IP addresses, or device identifiers beyond what is necessary for authentication and session management.

## 2. How We Use Your Information

We use your information to:

- Authenticate your identity and manage your account
- Sync and store your QuickBooks Online data for querying
- Process your natural-language questions using AI models
- Maintain conversation history for context in ongoing chats
- Store business preferences and context you provide to personalize responses
- Monitor system health and troubleshoot errors

## 3. Third-Party AI Processing

When you ask a question in the Application, your query and relevant financial data excerpts are sent to third-party AI providers for processing. These providers include:

- **Anthropic** (Claude models)
- **OpenAI** (GPT models)
- **Google** (Gemini models)

These providers are accessed through **OpenRouter**, an AI API routing service.

**Important:** All of these providers have API terms of service that **prohibit training on data sent through their APIs.** Your financial data is used only to generate a response to your specific query and is not retained by these providers for model training purposes.

## 4. Data Storage and Security

- Financial data is stored in **Supabase** (PostgreSQL database hosted on AWS).
- All sensitive data (QuickBooks OAuth tokens) is encrypted at rest using **pgcrypto** (AES-256 symmetric encryption).
- **Row-Level Security (RLS)** is enforced at the database level, ensuring you can only access data associated with your authorized client account.
- Authentication is handled by **Supabase Auth** using secure, httpOnly session cookies.
- Data is transmitted over HTTPS (TLS 1.2+) at all times.

## 5. Data Retention

- Your financial data is retained as long as your account is active and your QuickBooks Online connection is authorized.
- Chat conversation history is retained indefinitely for your reference unless you request deletion.
- If your account is terminated, your data will be deleted within 30 days.

## 6. Data Sharing

We do not sell, rent, or trade your personal or financial information. We share data only in the following circumstances:

- **AI Processing:** Query data is sent to third-party AI providers as described in Section 3.
- **QuickBooks Online:** We access your QBO data through Intuit's official API with your OAuth authorization.
- **Legal Requirements:** We may disclose information if required by law, legal process, or government request.

## 7. Your Rights

You have the right to:

- **Access** your stored financial data and conversation history through the Application
- **Request deletion** of your account and associated data by contacting us
- **Revoke QuickBooks access** at any time through your QuickBooks Online account settings or by contacting us
- **Request export** of your data in a machine-readable format

## 8. QuickBooks Online Integration

- We access your QuickBooks Online data through **Intuit's official OAuth 2.0 API**.
- You authorize this access when you connect your QuickBooks account through our admin dashboard.
- You can revoke this access at any time by disconnecting the Application from your QuickBooks Online account (Settings → Apps → Manage apps in QuickBooks Online).
- We access only the data scopes authorized during the OAuth consent flow (`com.intuit.quickbooks.accounting`).

## 9. Children's Privacy

The Application is not intended for use by individuals under the age of 18. We do not knowingly collect information from children.

## 10. Changes to This Policy

We may update this Privacy Policy from time to time. Changes will be posted to this page with an updated "Last updated" date. We encourage you to review this policy periodically.

## 11. Contact Us

If you have questions about this Privacy Policy or wish to exercise your data rights, contact us at:

**Atkins CPA, LLC**
337 Regency Dr
Allen, TX 75002
Email: hunter.atkins@atkinscpafirm.com
