# Changelog

All notable changes to this demo are tracked here.

## [0.1.1] — 2026-04-21

### Fixed
- Microsoft 365 product-logo icons were missing on the deployed site. The HTML references eight external PNGs (`copilot-logo.png`, `logo-outlook.png`, `logo-teams.png`, `logo-word.png`, `logo-excel.png`, `logo-powerpoint.png`, `logo-onedrive.png`, `logo-m365.png`) via inline SVG `<image>` tags, but the assets were not included in the initial commit or SWA deploy. Added all eight PNGs alongside `index.html` so app logos now render across the sign-in screen, home surface, waffle menu, Teams/Outlook topbars, and Copilot panels.

## [0.1.0] — 2026-04-21

### Added
- Initial public release of the Meridian State University M365 HR Copilot demo.
- Single-file HTML (`index.html`, ~592 KB, ~10.5K lines) — self-contained CSS + JS, no build step.
- Sign-in flow, desktop/home, 10 M365 app surfaces (Outlook, Teams, Word, Excel, PowerPoint, OneDrive, SharePoint, Purview, Copilot Studio, Agent 365), admin center, and guided 8-step tour.
- Four personas: Sarah Chen (HRBP, default), Marcus Johnson (HR Director), Maria Gutierrez (Benefits), Dan Kowalski (IT Director).
- Phase 0–3 roadmap aligned to a 24-week, ~$350K HR Copilot rollout: Enablement + Guardrails, Employee File Validation, Teams PTO, HR Front Door + RAG, Onboarding Nudge.
- Agent fleet: File Validator, PTO Assistant, HR Front Door, Policy RAG, Onboarding Nudge, with ADP (Aquera) + Workday HCM connectors referenced throughout.
- Governance surfaces: Purview HR PII / Confidential / Internal / Public labels with FERPA boundary for student workers, Agent 365 audit log, admin-center governance posture.
- FMLA intake scene (HR Intake ambient capture), employment-verification letter scaffold (Word), Q2 HR Town Hall deck (PowerPoint), Q2 HR Operations Review (Pages), HR Service Delivery FY26 dashboard (Power BI).

### Deployed
- Azure Static Web Apps (Free SKU) at <https://kind-mushroom-0b2b3da0f.7.azurestaticapps.net/>.
- Subscription: Centrix Labs Demo. Resource group: `rg-meridian-demo` (East US 2). Resource: `swa-meridian-hr-demo`.
