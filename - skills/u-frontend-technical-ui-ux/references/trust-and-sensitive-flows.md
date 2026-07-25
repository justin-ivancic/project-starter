# Trust And Sensitive Flows

Use this reference when the interface affects money, consent, personal data, permissions, public visibility, destructive actions, regulated access, AI-mediated decisions, ads, user-generated content, minors, or another high-consequence choice.

## Contents

- Operating Rule
- Cross-Cutting Trust Contract
- Permissions, Privacy, Consent, And Tracking
- Manipulative Choice Architecture
- Pricing, Payment, Subscription, And Cancellation
- Destructive, Public, Export, And Permission Changes
- Advertising, Marketplaces, And User-Generated Content
- AI Features
- Children, Minors, And Vulnerable Users
- Authentication And Account Recovery
- Current-Guidance Lookup
- Verification

## Operating Rule

Treat this as a risk-trigger and safer-default guide, not legal advice or a compliance checklist.

When a jurisdiction, regulation, standard version, enforcement date, threshold, exemption, storefront rule, or distribution policy affects the decision:

1. identify the product, actor, audience, market, platform, and transaction involved;
2. verify current official primary sources for that exact context;
3. separate a legal requirement, contractual requirement, platform policy, security dependency, and voluntary safer default;
4. implement what is within the authorized task;
5. flag unresolved or broader work and request direction before expanding scope;
6. report the target and evidence without claiming full compliance.

Do not preserve a static legal link catalog as if it were authority. Rules and platform programs change faster than this skill. Prefer current regulator, legislature, standards body, or platform-owner material over summaries and memory.

## Cross-Cutting Trust Contract

- Tell users what will happen before a consequential action, in plain language and close to the decision.
- Make required, optional, recommended, and unavailable choices distinguishable without coercion.
- Keep material terms visible and proximate. Use progressive disclosure only for supplementary detail, not the price, renewal, data use, cancellation consequence, or irreversible result that determines consent.
- Use affirmative action for purchase, publication, permission, recurring charge, or destructive commitment.
- Keep safe refusal, cancellation, withdrawal, undo, and recovery paths findable and proportionate.
- Do not use visual treatment, extra steps, emotional language, defaults, timing, or obstruction to punish a privacy-protective or money-saving choice.
- Preserve confirmations and receipts for consequential changes.
- Show current status, effective time, pending work, and entitlement or access consequences.
- Treat warning and confirmation UI as communication. Verify authorization, idempotency, audit, retention, and enforcement separately.

## Permissions, Privacy, Consent, And Tracking

Trigger this section for personal data, analytics, advertising, session replay, heatmaps, pixels, fingerprinting, cross-context tracking, contacts, files, photos, camera, microphone, location, health, finance, biometrics, or other sensitive data.

Use safer defaults:

- Collect and retain only what the stated task needs.
- Ask for sensitive device or account permission in context, after the benefit is understandable, unless the core product cannot function without it.
- Explain purpose, scope, recipient, persistence, and meaningful consequence at the decision point.
- Separate materially different purposes and distinguish required processing from optional consent.
- Do not preselect optional consent or bundle it into unrelated acceptance.
- In contexts where prior consent is required, do not load nonessential trackers before that choice.
- Give Accept and Reject or Decline comparable clarity and prominence for optional choices. Treat this as a conservative baseline, not a universal one-line legal test.
- Make withdrawal or changed choice as easy to find and perform as the original choice. Explain what withdrawal changes; do not imply it retroactively erases lawful prior processing.
- Provide settings to revoke or modify permissions later and explain when the operating system or administrator controls the final state.
- Align in-product disclosure, permission prompts, privacy settings, analytics configuration, and storefront declarations.
- Avoid vague claims such as “improve your experience” when different data uses have different consequences.
- Do not send sensitive content into analytics, logs, URLs, screenshots, previews, or third-party AI services without an authorized and disclosed purpose.

Verify current official privacy, ePrivacy or cookie, national authority, Apple tracking/privacy, Google User Data/Data Safety, and sector-specific requirements for the actual market and platform.

## Manipulative Choice Architecture

Reject interfaces that obtain action through confusion, exhaustion, concealment, or emotional punishment.

- No confirmshaming, trick questions, forced continuity, disguised ads, fake scarcity, fake countdowns, hidden costs, surprise renewals, or misleading defaults.
- Do not make refusal slower, grayer, smaller, more repetitive, or less understandable than acceptance when the choice is optional.
- Do not block core functionality behind optional consent unless the processing is genuinely required for that function and the distinction is explained.
- Do not move users into public sharing, contact invitation, recurring payment, or broad permission through an unrelated primary action.
- Do not use retention offers to obscure or repeatedly intercept cancellation. A relevant alternative may be offered once without changing the user's chosen path.
- Distinguish organic, sponsored, recommended, required, and administrator-controlled content or actions.

When a pattern is commercially useful but ethically or legally questionable, do not quietly implement it. State the concern, propose the non-manipulative path, and escalate any business decision outside the authorized task.

## Pricing, Payment, Subscription, And Cancellation

Trigger this section for pricing, trials, checkout, subscriptions, renewal, cancellation, refund, paid add-ons, in-app purchases, shipping, tax, fees, discounts, coupons, credits, or currency conversion.

Before commitment, show the material terms that apply:

- total amount and currency;
- billing cadence and whether the charge recurs;
- trial duration and first charge timing;
- taxes, fees, shipping, conversion, and conditions that can change the total;
- renewal and price-change treatment;
- refund or cancellation path and material consequence;
- account, entitlement, delivery, or access created by the purchase.

Use explicit purchase language that makes payment obligation clear for the applicable jurisdiction. Require affirmative agreement for recurring charges. Do not rely on a preselected box, buried terms, or a generic “Continue” button to establish informed intent.

For payment entry:

- Prefer PCI-validated provider-hosted fields or controls and the repository's approved payment integration.
- Never store or repopulate CVV, raw card credentials, or other prohibited authentication data.
- Preserve cart and non-sensitive billing or shipping entries after recoverable failure when safe.
- Keep validation and processor errors specific enough to recover without exposing sensitive details.
- Prevent accidental duplicate payment in the UI and verify server-side idempotency separately.
- Do not claim payment completion until authoritative confirmation exists. Handle delayed, failed, challenged, canceled, and duplicate outcomes.

For subscriptions and cancellation:

- Keep subscription status, next charge, plan, renewal, trial end, and management path findable.
- Make cancellation available through a simple, proportionate mechanism; do not hide it behind chat, phone, email-only handling, or a retention maze when a direct path is expected or required.
- Explain effective date, remaining entitlement, saved data, scheduled deletion, refunds, credits, and reversibility before confirmation.
- Allow the user to complete the chosen cancellation without repeated diversion.
- Confirm the request and resulting state. Distinguish requested, processing, scheduled, completed, and failed cancellation.
- Verify current federal, state, national, and storefront rules. Do not treat a remembered “click-to-cancel” rule or a universal platform-billing rule as current fact.

For native distribution, verify the current storefront, region, product type, purchase channel, external-purchase treatment, entitlement requirements, and subscription-management path. Apple and Google policies are not interchangeable or static.

## Destructive, Public, Export, And Permission Changes

For deletion, publication, invitations, export of sensitive data, permission changes, security settings, or irreversible bulk actions:

- Name the affected object, count or scope, consequence, effective timing, and whether recovery exists.
- Separate routine changes from genuinely destructive actions. Do not ask for confirmation on every harmless edit.
- Use step-up authentication when the product's threat model warrants it; treat that as an authentication and backend dependency.
- Make public, organization-visible, link-accessible, and private states explicit.
- Show who will gain or lose access and whether inherited permissions or external sharing apply.
- Keep exports authorization-checked, scoped, redacted where necessary, and protected during creation and download. Explain format, included data, expiry, delivery, and failure.
- Keep audit trails access-controlled and redact sensitive values. A visible “audit log” is not proof that the backend captures trustworthy events.
- Require server authorization for every consequential operation regardless of what the UI hides or disables.

## Advertising, Marketplaces, And User-Generated Content

- Label advertising, sponsorship, affiliate relationships, boosted placement, and paid recommendations clearly.
- Keep paid and organic ranking distinguishable and explain important ranking or filtering factors when user decisions depend on them.
- Do not camouflage ads as navigation, system messages, user posts, or primary content.
- Make seller or trader identity, price, fees, shipping, returns, dispute, and support routes clear where applicable.
- Provide reporting, blocking, muting, moderation, appeal, and safety controls appropriate to the product's content and risk.
- Preserve context and evidence for moderation decisions without exposing reporters or sensitive material unnecessarily.
- Verify current marketplace, advertising, endorsement, platform, and online-service obligations for the market and business model.

## AI Features

Trigger this section for chatbots, generated media, recommendations, ranking, scoring, classification, summarization, extraction, automated decisions, copilots, agents, or AI actions applied to user data.

- Make AI involvement clear when a user could reasonably mistake it for a person, authoritative source, verified fact, or deterministic system.
- Explain material limitations at the point of reliance, especially for consequential domains or irreversible actions.
- Distinguish generated content, retrieved evidence, user-provided material, system inference, and verified source.
- Show sources or provenance when available and useful. Do not invent confidence percentages or imply calibration the system does not possess.
- Provide edit, retry, undo, stop, report, and feedback paths appropriate to the action.
- Require explicit review or confirmation before sending, publishing, billing, deleting, changing permissions, or applying other high-impact actions unless the user has deliberately authorized bounded automation and recovery is established.
- Do not anthropomorphize the system into false authority or imply certification, expertise, consciousness, or human review that does not exist.
- Protect user data sent to model providers and align disclosure, retention, subprocessors, permissions, and storefront declarations.
- Verify current AI transparency, synthetic-content marking, sector-specific, and platform rules for the exact provider, deployer, system, content, and audience. Effective dates and scoped exceptions matter.

## Children, Minors, And Vulnerable Users

Trigger this section for products likely to reach children or teens, education, games, social features, creator tools, messaging, location, ads, sensitive content, streaks, loot-like rewards, or compulsive loops.

- Use privacy-protective and non-public defaults appropriate to the age and product.
- Avoid manipulative retention, spending pressure, social pressure, sensitive ad targeting, and location disclosure.
- Use age-appropriate language without disguising consequence.
- Keep blocking, reporting, privacy, safety, and trusted-adult support reachable.
- Do not expose precise location, contact details, school, routine, or public profile information by default.
- Verify current age-assurance, parental-consent, advertising, data, platform, and regional requirements. Do not infer one universal age threshold or parental-gate design.
- Escalate safeguarding, moderation, crisis, or mandatory-reporting questions to qualified product, policy, and legal owners.

## Authentication And Account Recovery

- Support password managers, autofill, paste, one-time-code retrieval, and passkeys where the platform, threat model, and audience support them.
- Use current autocomplete and platform semantics. Do not split credentials into hostile input patterns.
- Give recovery paths that explain timing, delivery channel, expiry, and what to do when access to the original factor is lost.
- Avoid account-enumeration disclosure where the product threat model requires it, while keeping messages usable. Treat response behavior and rate limiting as backend/security dependencies.
- Protect sessions through reauthentication and expiry without silently losing entered non-sensitive work.
- Apply step-up authentication according to risk, not as theater before every settings change.
- Never expose secrets, recovery codes, tokens, or authentication factors in analytics, logs, URLs, screenshots, or support transcripts.
- Verify the current identity standard and platform guidance when authentication assurance materially matters.

## Current-Guidance Lookup

Browse current official sources when the task depends on any of these areas:

- accessibility law, procurement, the European Accessibility Act or national implementation, EN 301 549 harmonization, ADA Title II, or Section 508;
- GDPR, ePrivacy or cookie rules, national data-protection authority guidance, tracking, consent, or withdrawal;
- consumer rights, negative-option or recurring billing rules, cancellation, pricing disclosure, refunds, or state-specific requirements;
- PCI requirements and the chosen payment provider's current integration contract;
- Apple or Google privacy, tracking, billing, subscriptions, external purchase, data safety, permissions, or review policy;
- online-platform, advertising, marketplace, trader, or user-generated-content duties;
- AI transparency, synthetic-content marking, high-impact systems, or sector-specific AI rules;
- children, minors, age assurance, parental consent, advertising, education, health, finance, or other vulnerable-user regimes.

Use official enacted text, regulator guidance, standards bodies, and platform-owner documentation. Note effective dates, pending changes, exemptions, and jurisdiction. Do not promote a proposal, vacated rule, draft standard, consultation paper, or outdated help page into a current requirement.

## Verification

Add the applicable sensitive-flow proof to the core contract: material information before action; refusal, withdrawal, cancellation, and safe escape; delayed, duplicate, challenged, partial, failed, and reversed outcomes; expired authentication and changed permission or entitlement; authoritative server result; confirmation, receipt, audit, export, or deletion evidence; analytics and logs checked for unintended sensitive data; and the current official source behind any requirement claim.

Record what was verified in the interface, what depends on backend or policy work, and what remains legally or operationally unresolved.
