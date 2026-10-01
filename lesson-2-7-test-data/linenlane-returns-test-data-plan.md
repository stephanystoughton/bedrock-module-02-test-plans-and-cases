# LinenLane Returns Test Data Plan

**Date:** October 1, 2026  
**Prepared by:** Stephany Stoughton  
**Workflow:** LinenLane Returns  
**Reviewer:** Priya Subramanian  

## Introduction

This Test Data Plan defines the data required to execute the LinenLane Returns workflow tests reliably and consistently. It supports the state-transition and detailed test cases created in Lessons 2.4 and 2.5, including valid and invalid return transitions. The plan is designed to prevent test-data contamination by giving each data set a predictable starting state, a defined refresh process, and a specific cleanup protocol. All test data is synthetic and must remain isolated from real LinenLane customer information.

---

# LL-DATA-001 — Returns Test Customers

## 1. Data Set Name and ID

**Data Set ID:** LL-DATA-001  
**Data Set Name:** Returns Test Customers

## 2. Purpose

This data set provides synthetic LinenLane customer accounts used by the Returns workflow tests. The customers represent different account and membership states so QA can verify that return behavior works correctly across multiple customer profiles.

At least three customers have existing order history so that they can be used with the Returns workflow test orders.

## 3. Source

The customer records are created by the seed script:

`seed-returns-customers.sql`

The script creates the same predictable customer records whenever the test environment is refreshed.

## 4. Refresh Strategy

The customer seed script runs before the Returns regression suite and whenever the staging environment is reset.

The script is designed to recreate the same customer IDs, membership states, and expected account conditions each time. If a test modifies a customer's membership status, gift-card balance, suspension status, or order history, the seed script restores the original baseline before the next full Returns test run.

## 5. Sensitivity Classification

**Classification: Synthetic**

All names, customer IDs, email addresses, and account details are created specifically for testing.

No real LinenLane customer information or production PII is used.

All email addresses use the Bedrock-controlled testing domain:

`*.linenlane-test@bedrock-staging.com`

## 6. Ownership

The LinenLane QA team owns the test-data requirements and verifies that the records are in the expected state before execution.

The LinenLane engineering team owns and maintains the `seed-returns-customers.sql` implementation.

## 7. Cleanup Protocol

Tests should avoid permanently modifying shared customer records whenever possible.

If a test changes customer state, account credit, membership status, or associated order data, the QA engineer running the test is responsible for ensuring the record is reset after the test completes.

The seed script is rerun after the Returns suite and before the next scheduled suite execution. If a test fails before cleanup completes, the affected customer record must be reset before another test uses it.

This prevents one test from leaving data behind that could cause another test to fail because of contamination.

## Representative Customer Data

| customer_id | name | email | country | membership_status | order_history_flag |
|---|---|---|---|---|---|
| LL-CUST-001 | Test Alice | alice01.linenlane-test@bedrock-staging.com | United States | New | No |
| LL-CUST-002 | Sample Bob | bob02.linenlane-test@bedrock-staging.com | United States | Active | Yes |
| LL-CUST-003 | Demo Carol | carol03.linenlane-test@bedrock-staging.com | Canada | Subscription | Yes |
| LL-CUST-004 | Mock Dana | dana04.linenlane-test@bedrock-staging.com | United Kingdom | Gift Card Credit | Yes |
| LL-CUST-005 | Synthetic Evan | evan05.linenlane-test@bedrock-staging.com | United States | Suspended | Yes |

---

# LL-DATA-002 — Returns-in-Progress Orders

## 1. Data Set Name and ID

**Data Set ID:** LL-DATA-002  
**Data Set Name:** Returns-in-Progress Orders

## 2. Purpose

This data set provides orders positioned in every state of the LinenLane Returns workflow.

It allows QA to test valid and invalid state transitions without depending on another test to create the required starting state.

The data set supports the six Returns states:

- Eligible
- Requested
- Approved
- Rejected
- ItemReceived
- Refunded

It also supports existing Returns cases such as:

- **LL-RETURN-001:** Eligible → InitiateReturn → Requested
- **LL-RETURN-003:** Requested → ApproveReturn → Approved
- **LL-RETURN-007:** Attempt ApproveReturn while Eligible; order must remain Eligible

## 3. Source

The order records are created by:

`seed-returns-orders.sql`

The seed script creates one or more orders in each required Returns workflow state.

## 4. Refresh Strategy

The Returns order seed script runs immediately before the Returns workflow test suite.

Each test begins with an order already placed in the exact state required by its preconditions.

The order data is refreshed again after the suite finishes so that transitions performed during testing do not remain in the shared staging environment.

If multiple QA engineers are testing simultaneously, each tester should use assigned order IDs or freshly seeded records rather than sharing the same mutable order.

## 5. Sensitivity Classification

**Classification: Synthetic**

All orders, customer references, return reasons, timestamps, and workflow states are created exclusively for QA testing.

No production orders or real customer transaction history are used.

## 6. Ownership

The LinenLane QA team defines the required workflow states and verifies state coverage.

The LinenLane engineering team owns the implementation and maintenance of `seed-returns-orders.sql`.

QA is responsible for reporting any state that cannot be reliably recreated by the seed script.

## 7. Cleanup Protocol

Each Returns test is responsible for the state it modifies.

When a test transitions an order from one state to another, the order must not be reused by another test that expects its original state until it has been reset.

At the end of the test suite, `seed-returns-orders.sql` is rerun to restore every order to its documented starting state.

If a test stops unexpectedly, fails during execution, or leaves an order in the wrong state, the QA engineer must reset that order before continuing dependent testing.

Tests must not rely on execution order. For example, LL-RETURN-003 must start with its own Requested order instead of depending on LL-RETURN-001 to run first.

This prevents contamination and test-order dependency.

## Representative Returns Order Data

| order_id | customer_id | current_state | last_updated | return_reason |
|---|---|---|---|---|
| LL-ORDER-1001 | LL-CUST-002 | Eligible | 2026-10-01 08:00 | Not applicable |
| LL-ORDER-1002 | LL-CUST-003 | Requested | 2026-10-01 08:05 | Size did not fit |
| LL-ORDER-1003 | LL-CUST-004 | Approved | 2026-10-01 08:10 | Item not as expected |
| LL-ORDER-1004 | LL-CUST-005 | Rejected | 2026-10-01 08:15 | Return window expired |
| LL-ORDER-1005 | LL-CUST-002 | ItemReceived | 2026-10-01 08:20 | Wrong item received |
| LL-ORDER-1006 | LL-CUST-003 | Refunded | 2026-10-01 08:25 | Damaged item |

### State Coverage

| Returns State | Covered |
|---|---|
| Eligible | Yes |
| Requested | Yes |
| Approved | Yes |
| Rejected | Yes |
| ItemReceived | Yes |
| Refunded | Yes |

---

# LL-DATA-003 — Returns Test Credentials

## 1. Data Set Name and ID

**Data Set ID:** LL-DATA-003  
**Data Set Name:** Returns Test Credentials

## 2. Purpose

This data set provides internal synthetic Returns-agent accounts used by QA to test actions available through the LinenLane internal Returns dashboard.

These accounts allow QA to verify operations that require employee permissions, including approving and rejecting return requests.

They are used for tests such as:

- **LL-RETURN-003:** Approve a return in the Requested state
- **LL-RETURN-007:** Verify that a return cannot be approved while still Eligible
- RejectReturn state-transition tests from the Lesson 2.4 Returns suite
- Internal dashboard authorization and workflow validation

## 3. Source

The agent accounts are created and configured by:

`factory-returns-agents.py`

The factory assigns the required Returns-agent roles and permissions in the staging environment.

Passwords are **not stored in this Test Data Plan**.

Passwords and other authentication secrets are stored in the approved **credentials vault** and retrieved only by authorized QA personnel.

## 4. Refresh Strategy

The test agent accounts remain stable so test cases can reference predictable agent IDs.

Before each Returns test cycle, QA verifies that both accounts:

- are active,
- have the correct Returns permissions,
- are not locked,
- and can access the staging Returns dashboard.

The factory function may be rerun if an account becomes corrupted, deleted, or incorrectly configured.

Passwords are rotated according to Bedrock and LinenLane credential-management policies rather than being manually stored in test documentation.

## 5. Sensitivity Classification

**Classification: Synthetic**

The agent identities are synthetic QA-only accounts.

Authentication secrets are treated as sensitive controlled information even though the accounts are not real employee identities.

Passwords, tokens, API keys, and session credentials must never appear in this document, source code, test-case documentation, or GitHub.

## 6. Ownership

The LinenLane engineering team owns account provisioning and role configuration.

The QA team owns the testing use of the accounts and must report permission or authentication problems.

The credentials vault is the approved source for passwords and authentication secrets.

## 7. Cleanup Protocol

The agent accounts themselves are not deleted after each test because they are reusable staging accounts.

After each Returns test session:

- active test sessions should be ended,
- temporary authentication tokens should expire or be revoked where applicable,
- account permissions must be returned to the documented baseline if a permission test changed them,
- failed-login counters or account locks must be reset before another test uses the account.

QA is responsible for identifying contamination caused by an account being locked, logged in with stale permissions, or left in a modified role.

The account should not be used for another test until the expected baseline has been restored.

## Representative Agent Accounts

| agent_id | role | Used In |
|---|---|---|
| LL-AGENT-001 | Returns Agent | LL-RETURN-003 ApproveReturn; Requested → Approved workflow tests |
| LL-AGENT-002 | Returns Agent | RejectReturn workflow tests; LL-RETURN-007 invalid approval validation |

**Password Handling:** Passwords are stored only in the approved **credentials vault**. No password values are included in this Test Data Plan.

---

# Test Data Contamination Controls

The Returns workflow contains stateful data, so contamination is a major risk. A test that modifies an order from Requested to Approved can cause another test expecting Requested to fail even when the application is functioning correctly.

To prevent this:

1. Every test must begin with explicitly documented preconditions.
2. Tests should use their own assigned data whenever possible.
3. No test should depend on another test running first.
4. Modified data must be reset after execution.
5. Seed scripts must restore the documented baseline before the next test cycle.
6. Failed or interrupted tests must be checked for incomplete cleanup before testing continues.
7. Shared staging data must not be modified outside the documented QA process.

---

# Data Safety Rules

All LinenLane Returns test data follows a synthetic-by-default approach.

The QA team must not use:

- real customer names,
- real customer email addresses,
- real phone numbers,
- real payment information,
- un-anonymized production records,
- passwords or authentication secrets stored directly in test documentation.

Customer email addresses use the controlled:

`*.linenlane-test@bedrock-staging.com`

format.

Production-like information may only be used if it has been properly anonymized and specifically approved for a testing scenario that requires realistic production distributions.

---

# Summary

This Test Data Plan provides three controlled data sets required for the LinenLane Returns workflow:

- **LL-DATA-001:** Returns Test Customers
- **LL-DATA-002:** Returns-in-Progress Orders
- **LL-DATA-003:** Returns Test Credentials

Together, these data sets provide predictable customer profiles, complete coverage of all six Returns workflow states, and controlled internal-agent access for approval and rejection testing. Each data set has an independent refresh and cleanup strategy designed to prevent contamination, state leakage, and test-order dependency.