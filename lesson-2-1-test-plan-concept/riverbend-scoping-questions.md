# RiverBend Credit Union – Scoping Questions

This document contains the scoping questions for the upcoming RiverBend Credit Union kickoff call. The goal is to gather the information needed to create a clear and realistic test plan for the redesigned member-facing online banking portal. These questions will help define what will be tested, how testing will be performed, the timeline, responsibilities, risks, and expected deliverables. They will also help identify banking-specific security and compliance requirements before testing begins.

## Scope

1. Which features of the redesigned member portal are included in this QA engagement: login, account balances, transaction history, transfers, bill pay, statements, profile management, and secure messaging?
2. Are we testing only the redesigned member-facing portal, or are any internal banking or administrative systems also included?
3. Will mobile browsers and/or a mobile banking app be included, or is this engagement limited to the desktop web portal?

## Test Methodology

1. Do you expect the engagement to include manual functional testing, automated testing, or both?
2. Which member workflows are considered highest priority and should receive the deepest testing?
3. Do you expect security, accessibility, performance, and cross-browser testing to be part of our QA work?

## Test Environment

1. Will RiverBend provide a dedicated staging or QA environment that mirrors the production member portal?
2. Which browsers, operating systems, and mobile devices must the redesigned portal support at launch?
3. Will the test environment connect to sandbox versions of services such as authentication, transfers, bill pay, and other banking integrations?

## Test Data

1. Will RiverBend provide test member accounts with different account types, such as checking, savings, loans, and credit cards?
2. Will all testing use synthetic or masked data, and are there specific rules we must follow to prevent exposure of real member information?
3. Will we have test accounts representing different scenarios, such as locked accounts, insufficient funds, pending transactions, and multiple linked accounts?

## Schedule and Milestones

1. Is the end-of-next-quarter launch date firm, and does that timeline include test planning, execution, bug fixes, regression testing, and final approval?
2. When will the staging environment and a testable build be available to the QA team?
3. Are there scheduled dates for feature completion, code freeze, regression testing, user acceptance testing, and production launch?

## Resources

1. Who will be our main RiverBend contact for questions about requirements and expected portal behavior?
2. Which RiverBend developers, product owners, security specialists, or compliance representatives will be available during testing?
3. What tools will we use for test case management, defect tracking, documentation, and communication?

## Risks and Mitigations

1. Are there known dependencies or third-party banking services that could delay testing or become unavailable during the engagement?
2. If requirements change during testing, who approves scope changes and how should those changes affect the launch timeline?
3. What is the escalation process if we discover a critical security or transaction-related defect close to launch?

## Entry and Exit Criteria

1. What must be completed before formal QA begins—for example, approved requirements, a stable staging build, integrations, and test data?
2. Which severity levels of defects must be resolved before RiverBend considers the portal ready for launch?
3. Who has final authority to approve the portal for release after QA is completed?

## Deliverables

1. Does RiverBend expect documented test cases, defect reports, execution results, and a final test summary?
2. What format or platform should we use to deliver test documentation and reports?
3. Do you need evidence such as screenshots or execution records for audit or compliance purposes?

## Regulatory and Compliance

1. Which banking regulations, internal policies, or compliance standards must the redesigned member portal satisfy?
2. Are there specific audit requirements that require us to preserve test results, screenshots, defect history, or approval records?
3. Are there security or privacy requirements governing how the QA team can access, store, or handle member-related test data?
