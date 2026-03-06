# Nonprofit ERP Gap Analysis for `ofbiz-framework`

Generated: 2026-03-06  
Scope: Full repository parse and targeted capability checks for adapting this codebase into a modern, user-friendly ERP for nonprofit organizations.

## Assessment Method

This gap inventory was built from:

- Architecture and module review across `applications`, `framework`, `themes`, `docs`, and runtime/build config.
- Entity/service/controller/theme scans for nonprofit and modern UX/API indicators.
- Evidence checks for presence/absence of API contracts, modern frontend stack artifacts, accessibility tooling, and nonprofit domain artifacts.

## Baseline Strengths to Keep

These are meaningful assets you can build on:

1. Mature ERP backbone: accounting, party, order, product, content, work efforts, manufacturing, HR.
2. Flexible metadata-driven platform: entity engine + service engine + widget/screen rendering model.
3. Multi-tenant capability exists (but is not turnkey out-of-the-box).
4. Strong permission model and configurable security controls.
5. Build/runtime tooling exists (Gradle tasks, Docker support, plugin model).

## Comprehensive Gap Inventory

### A) Nonprofit Domain Model and Workflows (Critical)

1. No first-class donor CRM model.
- Missing: donor householding, donor lifecycle, donor segments, communication preferences, relationship graph.
- Impact: cannot operate as a donor-centric CRM.

2. No complete donation lifecycle.
- Missing: gift entry, soft credits, tribute gifts, in-kind gifts, split gifts, refunds/reversals specific to fundraising.
- Impact: core fundraising operations remain manual/custom.

3. No nonprofit recurring giving model.
- Note: generic subscription capability exists, but not donation-focused recurring gift governance.
- Impact: major recurring revenue workflows require custom implementation.

4. No pledge and major-gift management.
- Missing: pledge schedules, installments, moves management, officer portfolios, ask pipeline.
- Impact: development teams cannot manage major gifts natively.

5. No grant management lifecycle.
- Missing: prospecting, application, award, restriction terms, budget lines, deliverables, reporting deadlines.
- Impact: grant-funded nonprofits cannot manage compliance workflows in-system.

6. No fund accounting model aligned to nonprofit restrictions.
- Missing: unrestricted/temporarily restricted/permanently restricted or equivalent net asset controls, release logic, donor restriction governance.
- Impact: financial statements and controls for nonprofits are incomplete.

7. No program and outcome measurement model.
- Missing: program outputs/outcomes, beneficiary metrics, impact KPIs, logic model tracking.
- Impact: mission impact reporting cannot be produced reliably.

8. No volunteer management domain.
- Missing: volunteer recruitment, onboarding, certifications, schedules, attendance, background checks, hours reporting.
- Impact: volunteer-heavy nonprofits need parallel systems.

9. No membership nonprofit lifecycle model.
- Missing: member tiers, benefits, renewals, lapses, chapter-specific member governance.
- Impact: membership organizations need heavy customization.

10. No nonprofit-specific campaign/fund structure.
- Note: marketing campaign entities exist, but not fundraising campaign constructs with gift attribution and fundraising KPIs.
- Impact: fundraising teams cannot run campaigns in a nonprofit-native model.

11. No planned giving/endowment workflow support.
- Missing: planned gift vehicles, expectancies, endowment policy constraints.
- Impact: long-horizon development operations are unsupported.

12. Minimal nonprofit traces are only generic accounting enums/adjustments.
- Example data exists (donation adjustment, payroll charity deduction, tax-form enums), but no end-to-end nonprofit capability.
- Impact: indicates primitives, not a nonprofit ERP solution.

### B) Finance, Compliance, and Regulatory Gaps (Critical)

13. No full nonprofit financial statement pack out-of-the-box.
- Missing: nonprofit-specific presentation templates and automation for board/reporting cycles.

14. No operational IRS 990 workflow automation.
- Current state includes enum values only, not filing workflow, mapping, validation, or exports.

15. No Gift Aid or equivalent jurisdictional donation tax workflows.
- Missing donor declarations, claim batches, and compliance logs.

16. No functional expense allocation framework for nonprofit reporting.
- Missing robust allocation mechanisms by program/admin/fundraising dimensions.

17. No grant compliance reporting engine.
- Missing award-level restrictions, burn tracking, and compliance package outputs.

18. No donation receipting and acknowledgment framework at nonprofit depth.
- Missing tax-compliant receipts, annual statements, acknowledgment SLA tooling.

19. No nonprofit-specific audit trail views for restricted funds and grant constraints.
- Existing audit/logging is generic, not purpose-built for nonprofit audits.

### C) UX and Product Experience Gaps (Critical for user-friendly goal)

20. Legacy UI architecture dominates.
- Widget/screen XML + FTL + jQuery is powerful but hard to make intuitive for non-technical staff at modern UX expectations.

21. No modern role-based product UX layer.
- Missing dedicated, simplified experiences for Development, Programs, Finance, Executive, and Volunteer coordinators.

22. Limited guided workflows and onboarding.
- Missing step-based wizards, context-aware help, and setup assistants for common nonprofit tasks.

23. Information density and navigation complexity are high.
- Existing screen patterns are ERP-heavy and not optimized for nonprofit staff usability.

24. Mobile-first field workflows are not a first-class product layer.
- Missing modern mobile UX for events, canvassing, volunteer check-in, and donor meeting notes.

25. No evidence of PWA/offline-first architecture.
- Limits modern field operations for nonprofits.

26. Accessibility governance/tooling is not evident.
- No repo-level automated WCAG/a11y toolchain found.

### D) API, Integration, and Ecosystem Gaps (High)

27. Not API-first for modern integration programs.
- No OpenAPI/Swagger/GraphQL contract artifacts found in the repo scan.

28. Existing REST-labeled entity routes are admin/webtools-oriented.
- They map to generic entity operations and views, not a stable nonprofit public API domain model.

29. Legacy SOAP/Axis2 integration surface still present.
- Useful for backward compatibility, but not sufficient as primary modern integration strategy.

30. No webhook/event product layer for integration orchestration.
- Missing reliable event publication for donation, pledge, grant, and program lifecycle events.

31. No packaged nonprofit connector suite.
- Missing first-class integrations for common nonprofit tooling (donation platforms, email automation, accounting sync, grant portals, BI pipelines).

32. Identity modernization is partial, not productized.
- JWT/OIDC-related configuration hooks exist, but there is no clear turnkey nonprofit-grade identity package (MFA policy packs, SCIM, zero-trust defaults, rollout guides).

### E) Data, Analytics, and Decision Support Gaps (High)

33. No nonprofit semantic layer.
- Missing canonical metric model for fundraising health, donor retention, grant utilization, and mission outcomes.

34. No executive nonprofit KPI dashboard framework out-of-the-box.
- Missing board-ready and leadership-ready dashboards tied to mission + finance + fundraising.

35. No built-in data quality management for constituent and gift integrity.
- Missing dedupe/match governance, survivorship rules, and stewardship workflows.

36. Limited mission impact analytics support.
- Missing integrated model for beneficiaries, services delivered, and outcomes over time.

### F) Delivery, Productization, and Adoption Gaps (High)

37. Multi-tenant capability is present but not enabled by default.
- Deployment hardening and tenant onboarding automation are needed for a productized SaaS-like rollout.

38. No nonprofit migration accelerators.
- Missing import templates/mapping tools for typical legacy nonprofit CRMs/ERPs and spreadsheet-heavy data.

39. No explicit nonprofit implementation playbooks.
- Missing packaged configurations by nonprofit subtype (membership org, grant-funded NGO, community services, faith-based, etc.).

40. No modern E2E quality gate evidence for UX-critical flows.
- No Playwright/Cypress/Puppeteer/Selenium project artifacts found in repository file scan.

41. No nonprofit-tailored training and change management artifacts in-repo.
- Missing role-based enablement kits that are essential to adoption in mission-driven teams.

## Priority Bands

### P0 - Must Build Before Nonprofit Go-Live

1. Donor and donation domain model/services.
2. Fund accounting and restriction controls.
3. Grant lifecycle and compliance reporting.
4. Nonprofit financial reporting and 990 workflow automation.
5. Role-based modern UX shell (Development, Programs, Finance).
6. API contract layer for integrations (OpenAPI-first).

### P1 - Should Build for Competitive Product-Market Fit

1. Volunteer and membership management.
2. Recurring giving, pledge, and major gifts.
3. Donation receipting and acknowledgment automation.
4. Accessibility program (WCAG compliance targets + CI checks).
5. Event/webhook integration framework.

### P2 - Strategic Differentiators

1. Outcome/impact analytics and board dashboards.
2. Data quality stewardship tooling.
3. Vertical implementation templates for nonprofit sub-sectors.
4. Advanced identity/tenant governance and policy automation.

## Suggested Phased Modernization Plan

### Phase 1 (0-3 months)

1. Create nonprofit core data model extension modules (donor, gift, fund, grant).
2. Introduce API contract layer and stable domain endpoints.
3. Build modern UX shell for top 5 nonprofit jobs-to-be-done.
4. Add initial compliance outputs (receipts, restricted fund reports, 990 data prep).

### Phase 2 (3-6 months)

1. Add recurring giving, pledges, volunteer, and membership packages.
2. Build integration connectors and webhook/event pipeline.
3. Add accessibility CI tooling and E2E automation for critical flows.
4. Add migration toolkit and nonprofit implementation playbooks.

### Phase 3 (6-12 months)

1. Expand advanced reporting/analytics and impact measurement.
2. Add board dashboard packs and benchmarking.
3. Harden multi-tenant operations, SSO/MFA policies, and enterprise controls.
4. Build repeatable deployment templates for managed/SaaS offerings.

## Key Evidence References (Repository)

- Legacy theme model and jQuery-centered rendering:
  - `themes/docs/themes.adoc:26`
  - `themes/docs/themes.adoc:155`
  - `themes/common-theme/widget/Theme.xml:60`
  - `themes/common-theme/widget/Theme.xml:61`
  - `themes/common-theme/widget/Theme.xml:63`

- Widget/screen-driven UI composition pattern:
  - `applications/workeffort/widget/WorkEffortScreens.xml:23`
  - `applications/workeffort/widget/WorkEffortScreens.xml:37`
  - `applications/workeffort/widget/WorkEffortScreens.xml:47`

- REST-labeled webtools entity mapping (admin/generic):
  - `framework/webtools/webapp/webtools/WEB-INF/controller.xml:45`
  - `framework/webtools/webapp/webtools/WEB-INF/controller.xml:60`
  - `framework/webtools/webapp/webtools/WEB-INF/controller.xml:71`

- Axis2 SOAP/REST legacy config surface:
  - `framework/service/config/axis2/conf/axis2.xml:90`
  - `framework/service/config/axis2/conf/axis2.xml:97`

- Minimal nonprofit-related primitives in seed data (not full workflows):
  - `applications/datamodel/data/seed/OrderSeedData.xml:41`
  - `applications/datamodel/data/seed/AccountingSeedData.xml:673`
  - `applications/datamodel/data/seed/AccountingSeedData.xml:965`
  - `applications/datamodel/data/seed/AccountingSeedData.xml:966`
  - `applications/datamodel/data/seed/AccountingSeedData.xml:967`

- Multi-tenant capability exists but defaults need productization:
  - `framework/common/config/general.properties:138`
  - `README.adoc:543`
  - `README.adoc:564`

- Security/identity baseline configuration points:
  - `framework/security/config/security.properties:24`
  - `framework/security/config/security.properties:157`
  - `framework/security/config/security.properties:169`

- API spec and PWA artifact absence checks:
  - `NO_API_SPEC_OR_PWA_FILES_FOUND` from repository file scan command.

- Nonprofit domain entity/service absence checks:
  - `NO_DONOR_DONATION_VOLUNTEER_PLEDGE_SERVICES_OR_ENTITIES` from entity/service scan.

- Accessibility and modern E2E test tooling absence checks:
  - `NO_ACCESSIBILITY_TOOLING_FILES_FOUND`
  - `NO_MODERN_E2E_TEST_FRAMEWORK_FILES_FOUND`

## Conclusion

`ofbiz-framework` is a strong ERP platform foundation, but it is not yet a nonprofit-native, modern, user-friendly ERP product. Reaching that goal requires both domain expansion (fundraising/grants/funds/outcomes) and product modernization (UX/API/integration/accessibility), not only UI theming changes.
