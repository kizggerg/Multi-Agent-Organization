# Stage 1 PRD: Opportunity and Discovery

## Initiative
- **Working name:** LeadReply
- **Stage:** 1 - Opportunity and Discovery
- **Status:** Draft complete, awaiting Gate 1 VP sign-off before Stage 2
- **Date:** 2026-02-22

## Problem Statement
Small local service businesses (plumbers, HVAC, electricians, med spas, legal offices) lose inbound website leads when they cannot respond immediately, especially evenings and weekends. Existing chat/support tools are often too expensive or too complex for owners with no technical staff.

### Why this matters now
- Small businesses increasingly expect "instant response" behavior from consumers.
- AI tooling has reduced build cost enough for a focused micro-SaaS.
- Early revenue can be generated with a narrow vertical solution and simple onboarding.

## Target Persona / Segment
- **Primary persona:** Owner-operator of a local service business (1-25 employees)
- **Secondary persona:** Office manager handling inbound inquiries
- **Customer profile:** Has a website, receives lead forms/messages, misses off-hours leads, willing to pay $29-$79/month for measurable lead conversion lift

## Opportunity Options Considered (Prioritization Snapshot)
Scoring: 1 (low) to 5 (high), effort is inverse (lower effort = higher score).

1. **AI lead-reply widget for local services (chosen)**  
   - Impact 4, Urgency 4, Effort 4, Risk 3, Strategic fit 4 -> **19**
2. Generic AI customer support chatbot (broad SMB)  
   - Impact 4, Urgency 3, Effort 2, Risk 2, Strategic fit 3 -> **14**
3. Internal engineering SDLC copilot tool  
   - Impact 3, Urgency 2, Effort 3, Risk 3, Strategic fit 4 -> **15**

**Rationale:** Option 1 offers the best near-term value per cost and is easier to position around a clear ROI ("fewer missed leads").

## Value Hypothesis
If we provide a simple AI lead-reply widget that captures and qualifies inbound website leads within 60 seconds, then local businesses will convert more inquiries into booked calls/jobs and will pay a monthly subscription because the product can pay for itself with even one additional closed job per month.

## Success Metrics and Measurement Window
Measurement window: **first 90 days after MVP launch**

### North-star metric
- **Activated paying accounts** (connected website + at least 20 conversations in first 30 days)

### Primary success metrics
- Time-to-first-response median <= 60 seconds
- Visitor-to-lead conversion uplift >= 15% versus pre-install baseline (or matched control period)
- Trial-to-paid conversion >= 20%
- Month-2 logo retention >= 75%
- At least 20 paying customers by day 90 (initial modest-income target)

### Guardrail metrics
- False/incorrect response rate < 5% of conversations
- Escalation to human when confidence low >= 95%
- Gross margin >= 60% at 20-customer scale

## Smallest Testable Scope (MVP)
Deliver one focused workflow:
1. Install script on customer website.
2. Widget answers FAQs from a customer-provided knowledge source (URL or text).
3. Captures visitor contact info and intent.
4. Sends lead summary to business email/SMS.
5. Simple owner dashboard with conversation log and lead count.

No CRM integrations, no multichannel, no complex automation in MVP.

## PRD - Functional Requirements
- **FR-01:** Business owner can create an account and start a trial with email + password.
- **FR-02:** Owner can install a JavaScript widget snippet on their website.
- **FR-03:** Owner can provide knowledge source via website URL crawl or pasted FAQ text.
- **FR-04:** System answers visitor questions using only configured knowledge source and safe defaults.
- **FR-05:** Widget asks for name, phone/email, and service need before conversation end.
- **FR-06:** System creates a lead record with transcript, source page, timestamp, and contact details.
- **FR-07:** System notifies owner via email immediately when a new lead is captured.
- **FR-08:** Optional SMS alert can be enabled for new leads.
- **FR-09:** Owner can review leads and conversation transcripts in a basic dashboard.
- **FR-10:** Owner can set business hours and auto-message behavior for after-hours vs in-hours.
- **FR-11:** Owner can mark responses as helpful/unhelpful for future quality tuning.
- **FR-12:** Owner can upgrade from trial to paid plan with card checkout.

## PRD - Non-Functional Requirements
- **NFR-01 (Performance):** P95 widget response latency <= 2.5 seconds under expected MVP load.
- **NFR-02 (Availability):** 99.5% monthly uptime target for customer-facing widget service.
- **NFR-03 (Security):** Encrypt data in transit (TLS 1.2+) and at rest; role-based account access.
- **NFR-04 (Privacy):** Minimize PII capture, provide deletion request path, and configurable data retention.
- **NFR-05 (Reliability):** No lead-loss on transient failures; retry and durable queue for notifications.
- **NFR-06 (Observability):** Track response latency, answer confidence, lead-capture funnel, and failure events.
- **NFR-07 (Maintainability):** Deployable as modular services with clear API boundaries for future integrations.
- **NFR-08 (Usability):** Owner onboarding to first live widget in <= 15 minutes without engineering support.

## Initiative Scope Boundaries
### In scope (Stage 1 vision for first release)
- Single-language English support
- Website widget only
- Email + optional SMS alerts
- Single-seat owner account

### Out of scope (deferred)
- Full CRM integrations (HubSpot/Salesforce)
- Voice channel and call routing
- Multi-location enterprise account hierarchy
- White-label reseller controls

## Initial Budget Envelope (Stage 1)
All figures are early estimates for initial delivery and first 3 months.

### Cost summary
- **Delivery cost:** $18k-$32k (engineering/design/qa effort equivalent)
- **Runtime cost:** $250-$1,000 per month (hosting, LLM inference, SMS/email variable usage)
- **Agent usage cost:** $150-$500 during build phase for discovery/planning/implementation support

### Assumptions
- 1-2 engineers equivalent pace, 4-6 week MVP build in Stage 4
- 20-50 pilot customers in first 90 days
- Average 300-1,000 monthly conversations per customer
- Lean infrastructure and managed services preferred

### Confidence and variance
- **Confidence:** Medium-low (0.58) due to greenfield execution and customer acquisition uncertainty
- No prior baseline exists yet (new initiative); variance tracking begins once Stage 3 estimate baseline is approved

### Top cost drivers
- LLM usage per conversation
- SMS notifications volume
- Customer acquisition cost if paid channels are used

### Cost controls
- Limit free-trial conversation volume
- Cache frequent FAQ responses
- Start email-only notifications by default; SMS as paid add-on

## Assumptions, Risks, and Confidence
1. Customers will trust an AI widget for first response in their domain.  
   - Confidence: Medium
2. Businesses can self-onboard without high-touch support.  
   - Confidence: Medium-low
3. One additional closed job/month is enough ROI to sustain subscription.  
   - Confidence: Medium
4. We can acquire early users through founder-led outbound and local networks at low CAC.  
   - Confidence: Medium-low

### Key risks
- Crowded chatbot market may compress pricing.
- Hallucinated answers can damage trust if guardrails are weak.
- Onboarding friction could reduce trial activation.

## Recommended Next Step (if approved)
Proceed to **Stage 2 - Initiative Shaping** with required outputs:
- UX/UI design spec
- Architecture document
- Threat model
- Scope boundaries (refined)
- Initial epic map

Do not begin Stage 2 until Gate 1 decision is recorded.

---

## Gate 1 VP Sign-Off Brief (Stage 1 -> Stage 2)

### Trigger type
- **Mandatory stage gate** between Stage 1 and Stage 2
- No escalation threshold currently triggered (no approved baseline yet, no high/critical unresolved risk accepted)

### Decision options
1. **Approve Stage 2 now**  
   - Continue with shaping artifacts for LeadReply as scoped
2. **Approve with constraints**  
   - Limit MVP to one vertical and email-only notifications for stricter runtime cost control
3. **Defer / rework Stage 1**  
   - Request deeper customer validation before shaping

### Recommendation
**Option 2: Approve with constraints.**  
Reason: preserves speed to first revenue while reducing early cost and complexity.

### Reversible vs irreversible impact
- **Reversible now:** problem framing, scope boundaries, pricing assumptions
- **Potentially harder to reverse later:** architecture choices that overfit broad multichannel support too early
- No irreversible production-release actions are proposed at this stage

### Required VP Engineering (human) decision
Please choose one:
- `APPROVE_STAGE_2`
- `APPROVE_STAGE_2_WITH_CONSTRAINTS`
- `DEFER_FOR_REWORK`

### Post-decision conditions
- If approved: begin Stage 2 only, produce shaping artifacts, and run shaping-phase security validation.
- If deferred: revise PRD based on VP feedback and resubmit Gate 1 brief.

## Current Halt Status
Per SDLC policy, execution is **halted at Gate 1** pending explicit VP sign-off.
