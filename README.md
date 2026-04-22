# Meridian State University — Microsoft 365 HR Copilot Demo

A single-file, interactive demo of a **Microsoft 365 Copilot rollout for HR** at a fictional state university (Meridian State University, ~18,000 employees). Built to walk clients through a phased, governed path from Copilot enablement to proactive HR automation.

**Live demo:** <https://kind-mushroom-0b2b3da0f.7.azurestaticapps.net/>

Sign in as `sarah.chen@meridianstate.edu` — any password is accepted. A guided 8-step tour narrates the key scenes.

---

## What the demo shows

A 24-week, **~$350K** HR Copilot journey mapped across M365 surfaces (Outlook, Teams, Word, Excel, PowerPoint, OneDrive, SharePoint, Purview, Copilot Studio, Agent 365):

| Phase | Weeks | Investment | Scope |
|---|---|---|---|
| **Phase 0 — Enablement + Guardrails** | 1–2 | bundled with Phase 1 | HR×IT AI operating model, governance baseline, Teams entry point, doc repos + retention owners |
| **Phase 1A — Employee File Validation & Retention** | 3–8 | bundled | Scan repos, validate required docs (I-9, W-4, offer, handbook ack), retention, exception reports |
| **Phase 1B — Teams PTO Transaction Pattern** | 3–10 | $135K combined (Phase 0+1, $75K partner funding possible) | PTO balance + request + manager approval loop in Teams, ADP via Aquera |
| **Phase 2 — Scale Self-Service + Reduce HR Inbox** | 10–18 | $110K (funding TBD) | HR Front Door (structured intake), HR RAG with confidence gating + escalation, address-change + employment-verification transactions |
| **Phase 3 — Proactive / Predictive HR** | 18–24 | $125K (funding TBD) | Onboarding Nudge (30/60/90 manager checklist reminders), event triggers, monitoring cadence |

## Personas

| Name | Role |
|---|---|
| Sarah Chen | HR Business Partner, People Operations (default sign-in) |
| Marcus Johnson | HR Director |
| Maria Gutierrez | Benefits Analyst |
| Dan Kowalski | IT Director |

Each persona has their own home feed, agent access, and recent activity. Switch via the avatar menu.

## Agents shown in the fleet

- **File Validator** (Phase 1A, prod) — scans SharePoint/Workday/ADP for missing or expired employee documents
- **PTO Assistant** (Phase 1B, prod) — PTO balance, request, manager approval in Teams; ADP (Aquera) connector
- **HR Front Door** (Phase 2, prod) — structured intake and routing for address change + employment verification
- **Policy RAG** (Phase 2, staging) — handbook/policy Q&A with citations + confidence gating
- **Onboarding Nudge** (Phase 3, pilot in College of Engineering) — 30/60/90-day checklist monitoring

## Governance surfaces

- **Purview** — sensitivity labels (HR PII, Confidential, Internal, Public), FERPA boundary for student workers, retention policies
- **Agent 365** — agent fleet inventory, identity + permissions, incidents, cost attribution, audit log
- **Admin Center** — adoption metrics, data loss prevention posture, governance cadence

## Run locally

It's a single self-contained HTML file with embedded CSS + JS. No build step.

```bash
# Python 3
python -m http.server 8000
# then visit http://127.0.0.1:8000/
```

Or just open `index.html` in a browser directly.

## Deploy to Azure Static Web Apps

```bash
# Create infra
az group create -n rg-meridian-demo -l eastus2
az staticwebapp create -n swa-meridian-hr-demo -g rg-meridian-demo -l eastus2 --sku Free

# Deploy (run from the parent directory — SWA CLI refuses to deploy when CWD is inside the artifact folder)
TOKEN=$(az staticwebapp secrets list -n swa-meridian-hr-demo -g rg-meridian-demo --query properties.apiKey -o tsv)
swa deploy ./meridian-m365-hr-demo --deployment-token "$TOKEN" --env production
```

## Notes

- All organization names, employee names, case details, dollar figures, and ticket volumes are fictional.
- The demo is client-facing positioning material; it is not a functional HR system.
- Derived from an earlier healthcare-themed version of the same framework.
