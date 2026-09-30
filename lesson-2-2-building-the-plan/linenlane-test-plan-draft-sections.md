# LinenLane Test Plan – Draft Sections

This document is my first-draft contribution to the LinenLane test plan, based on the kickoff notes from October 13. It covers three foundational sections of the plan: Scope, Assumptions, and Risks and Mitigations. The information below reflects the current understanding of the engagement and identifies areas that may still require client confirmation. The remaining sections of the test plan will be added throughout the following lessons.

## Scope

### In-Scope

- Customer-facing storefront testing on the React/Node application for desktop web
- Customer-facing storefront testing on mobile web using Chrome and Safari
- Launch-region validation for the US, UK, and Canada
- Existing Stripe payment integration testing
- New Apple Pay payment flow testing on mobile web
- New Google Pay payment flow testing on mobile web
- Account migration validation for existing customer accounts
- Migrated customer login, order-history, and new-order flow validation
- Manual functional testing across storefront, checkout, and account flows
- Exploratory testing in support of functional coverage
- Daily bug report deliverables during test execution
- Final test summary report at engagement close

### Out-of-Scope

- Admin dashboard testing, owned by LinenLane internal QA
- Native iOS application testing, planned by LinenLane for post-launch
- Native Android application testing, planned by LinenLane for post-launch
- PayPal payment integration testing, planned by LinenLane for a future roadmap release
- Accessibility audit, excluded from launch-blocking scope by LinenLane
- Performance and load testing, owned by LinenLane and a separate vendor
- Security and penetration testing, owned by LinenLane and a separate vendor
- Post-launch hot-fix testing window, pending Beatrix's confirmation and currently treated as out of scope

## Assumptions

- The staging environment will be stable and accessible to the Bedrock QA team from Friday, October 17 through November 22.
- The staging environment will contain 200 anonymized customer accounts and a realistic product catalog by Friday, October 17.
- Bedrock will have at least one shared test account with sufficient customer-level permissions to validate subscription customers, gift card holders, and other relevant edge cases.
- The customer-facing storefront will support the latest two stable versions of Chrome, Safari, Firefox, and Edge on desktop, and the latest two stable versions of Chrome and Safari on mobile.
- Tax and shipping rules for the US, UK, and Canada will be correctly configured by LinenLane engineering before testing begins.
- The Stripe API version used in staging will match the version documented by LinenLane, and any version changes will be communicated to Bedrock before deployment.
- Account migration testing will use migrated test accounts in staging that mirror the production migration logic without exposing real customer data.

## Risks and Mitigations

### Risk 1: Staging Environment Availability

The staging environment may not be stable or available by Friday, October 17, reducing the available testing window before the November 21 code freeze.

**Mitigation:** Confirm staging readiness with LinenLane before testing begins and escalate access or stability issues immediately so testing priorities can be adjusted.

### Risk 2: Account Migration Defects

Migrated customer accounts may fail to log in, display order history, or place new orders after the migration.

**Mitigation:** Test representative migrated accounts in staging before launch and prioritize login, order-history, and checkout validation for migrated users.

### Risk 3: Payment Integration Issues

Stripe, Apple Pay, or Google Pay flows may fail or behave differently across supported desktop and mobile browsers.

**Mitigation:** Test each in-scope payment method across the supported browser and device combinations and report payment-blocking defects as high priority.

### Risk 4: Regional Configuration Issues

Incorrect tax, shipping, currency, or other regional configurations may affect customers in the US, UK, or Canada.

**Mitigation:** Validate representative purchase flows for all three launch regions and escalate configuration discrepancies to LinenLane engineering.

### Risk 5: Limited Time Before Code Freeze

Late fixes or environment delays may reduce the time available for regression testing before the November 21 code freeze and November 25 launch.

**Mitigation:** Prioritize critical storefront, checkout, payment, and account flows first and perform targeted regression testing after high-impact fixes.

### Risk 6: Unconfirmed Post-Launch Testing

The post-launch hot-fix testing window has not yet been confirmed, which may leave defects discovered after launch without agreed Bedrock QA coverage.

**Mitigation:** Request confirmation from Beatrix before finalizing the test plan and document post-launch testing as out of scope until approval is received.
