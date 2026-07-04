# AI-Orchestrated Data Security Posture Management (DSPM)

## Executive Summary
Designed and deployed an automated, AI-driven Data Security Posture Management (DSPM) pipeline to monitor, baseline, and gamify endpoint data egress. This architecture leverages endpoint telemetry to track unstructured data movement into GenAI/LLM tools, feeding a custom "Security Champions" leaderboard via an external API loop.

## Architecture Stack
* **Telemetry & Detection:** Enterprise EDR / Next-Gen SIEM (Data Protection Module)
* **Agentic Orchestration:** Native AI Security Agents, Scheduled JSON Extraction
* **Frontend UI:** React, Tailwind CSS, Gamified Read-Only Dashboard

## The Engine: Telemetry & Noise Reduction
To avoid the brittleness of cloud API logs, this pipeline captures raw egress events directly at the endpoint. The query intentionally filters out sanctioned Business-As-Usual (BAU) traffic to isolate "Shadow AI" web uploads.

logscale
// 1. Target Data Egress Events
#event_simpleName=DataEgress

// 2. Isolate Web Uploads
| DataEgressDestination =~ /[Ww]eb.*[Uu]pload/i

// 3. Exclude Sanctioned Workspace Traffic (Sanitized for Public Release)
| DataEgressDestination != /<APPROVED_WORKSPACE_DOMAIN_1>/i
| DataEgressDestination != /<APPROVED_WORKSPACE_DOMAIN_2>/i
| DataEgressDestination != /<INTERNAL_IDP_PROVIDER>/i
` ` `

## AI Extraction & Least Privilege
Instead of granting broad SIEM access to external dashboards, a dedicated AI Agent was built using the Principle of Least Privilege. 
* **Execution:** Automatically queries the SIEM via API every 24 hours.
* **Output:** Strictly formatted JSON arrays `[{"Username": "...", "ViolationCount": #}]` to prevent data leakage.

## The Gamified Feedback Loop
The extracted telemetry automatically feeds a decoupled, read-only UI. Engineers are given direct visibility into their baseline telemetry in a gamified environment (XP, Streaks, Letter Grades), fostering a proactive security culture where developers self-correct unapproved LLM data uploads.
