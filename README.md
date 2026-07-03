# whoami
*by Rashard · IT Security Analyst & AI Risk Practitioner*

IT Security Analyst bridging the gap between AI experimentation and 
enterprise security. My work focuses on AI Risk Architecture, 
enforcing secure-by-design principles in LLMOps deployments, and 
building out AI Data Loss Prevention (AI-DLP) guardrails.

## Focus Areas

- **AI Governance & LLMOps:** Managing the lifecycle, RBAC, and secure deployment of enterprise AI agents.
- **AI Data Loss Prevention (AI-DLP):** Configuring classification modules to track and block PII (SSN, DL, PDFs) egress in generative AI prompt flows.
- **Security Automation:** Designing human-in-the-loop SOAR workflows.
- **DevSecOps (In Progress):** Transitioning toward infrastructure-as-code via Terraform and pursuing the Anthropic Claude Architect Certification.

## Repo Layout

- [`now.md`](./now.md) — what I'm working on this month
- [`/writeups`](./writeups) — generalized technical writeups
- [`/decisions`](./decisions) — architectural decision records

## Working Principles

- Smallest thing that solves the real problem
- Threat model before automation
- Documentation is a deliverable, not an afterthought
- One percent better daily

## Builds

### RRA Automation Pipeline — Human-in-the-Loop SOAR Pattern

A repeatable 5-step pipeline for Rapid Risk Assessment workflows built on Google Sheets + Zapier + Slack.

**Core Philosophy:** Automation stays dormant while a human works. A single status cell change (`Automation Status = Ready to Send`) is the only trigger that moves data into production.

**The 5 Steps:**
1. **Ingest** — Request ticket arrives on the intake board
2. **Document** — Analyst fills a strict flat-row schema on the review sheet
3. **Gate** — Zapier filters for `Ready to Send` rows only
4. **Alert** — Zapier sends a YAML block to Slack
5. **Lock** — Zapier writes `Sent` back to the row, preventing duplicate triggers

**Teaching Model (Three Terms):**
- **The Sandbox** — Tab 1: freeform human thinking and notes
- **The Flight Deck** — Tab 2: structured flat row for automation
- **The Key** — `Automation Status`: the explicit switch that moves data from sandbox to production

**In Progress:** Parallel variant using Zapier MCP so an LLM agent can natively trigger this workflow via Model Context Protocol instead of spreadsheet polling.

## Stack

CrowdStrike NG-SIEM · SOAR · Google Workspace · Python · YAML · 
Markdown · Git
