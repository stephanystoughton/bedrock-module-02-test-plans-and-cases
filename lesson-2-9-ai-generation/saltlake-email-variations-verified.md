# AI Use Disclosure for SL-SIGNUP-002 through SL-SIGNUP-006

Source seed: SL-SIGNUP-001 (hand-written, see saltlake-seed-email-valid.md)

AI tool: ChatGPT by OpenAI

Prompt:

Role: You are a senior QA Analyst at a software quality assurance firm. You have 10 years of experience designing test case variations using equivalence partitioning and boundary value analysis. You write in the same seven-element test case format used throughout the engagement.

Task: Generate 5 variations of the seed test case below. Each variation tests the same email validation behavior using a different equivalence partition representative or a different boundary value. The variations should cover: a plus-addressed email (e.g., user+tag@domain.com), a country-TLD email (e.g., .co.uk), a subdomain email (e.g., user@mail.domain.com), an email at the maximum length boundary (per HTML5 spec, 254 characters), and an email with a numeric local-part (e.g., 12345@domain.com).

Context: I'm a junior QA at Bedrock Quality Labs testing the Saltlake Outfitters signup form. The form has 6 fields (email, password, postal code, country, age, marketing-opt-in). The form validates client-side on field-blur (clicking outside the field). There is no "Verify Email" button, no "Confirm Email" field, no email-confirmation modal. Validation is inline only. Email format follows RFC 5322 with HTML5's relaxed rules. The form's "Create Account" submit button is at the bottom of the form. The seed test case below is for the email field's valid-input partition.

Constraints: Don't reference any UI element that isn't in the Context. Don't invent buttons, links, modals, or fields. Use the same seven-element format as the seed. Use the same test data domain convention (*.signup-test@bedrock-staging.com). Use the same staging URL. Use realistic but synthetic test data.

Output format: 5 variations, each in the same seven-element format as the seed (Test Case ID, Test Title, Preconditions, Test Data, Steps, Expected Results, Postconditions). Assign Test Case IDs SL-SIGNUP-002 through SL-SIGNUP-006.

Seed:

Test Case ID: SL-SIGNUP-001

Test Title: Valid email accepted on Saltlake signup form

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded with all 6 fields visible
- Browser console is open to observe network requests

Test Data:
- Email: customer.alice.signup-test@bedrock-staging.com
- Password: PassW0rd!23 (valid per spec)
- Postal Code: 80202
- Country: United States
- Age: 35
- Marketing opt-in: unchecked

Steps:
1. Click into the Email field.
2. Type the test email exactly as specified.
3. Click outside the field (Tab key or click on Password field).
4. Observe the field's validation state.

Expected Results:
- Email field shows no error message.
- Email field border is the default (not red, not flagged).
- Browser console shows no validation error logged.

Postconditions:
- No backend request fired (validation is client-side until submit).
- Form is ready for next field input.

Verification: Five-Point Verification Checklist applied to each variation.

Edits made:
- SL-SIGNUP-002: Step 3 corrected. A hallucinated "Verify Email" button was removed and replaced with field-blur validation.
- SL-SIGNUP-004: An invented confirmation tooltip was removed from Expected Results.
- SL-SIGNUP-006: Test data domain was corrected to comply with the staging test-data convention while preserving a numeric local-part.
- SL-SIGNUP-003 and SL-SIGNUP-005 required no functional edits.

Net result: 5 variations generated, 3 edited, 2 kept as-is, 0 rejected.

## Verification Notes

### SL-SIGNUP-002
1. UI element existence: PASS after edit. The nonexistent "Verify Email" button was removed.
2. Spec traceability: PASS. Plus-addressing is evaluated as valid email input under the stated email-format rules.
3. Meaningful variation: PASS. The plus-addressed email is different from the plain seed email.
4. Test data compliance: PASS. Synthetic staging test data is used.
5. Stranger Test: PASS after edit. The field-blur step is explicit and executable.

### SL-SIGNUP-003
1. UI element existence: PASS.
2. Spec traceability: PASS.
3. Meaningful variation: PASS. The test exercises a country-TLD email.
4. Test data compliance: PASS for the guided exercise's country-TLD variation using synthetic staging data.
5. Stranger Test: PASS.

### SL-SIGNUP-004
1. UI element existence: PASS.
2. Spec traceability: PASS after edit. The invented confirmation tooltip was removed.
3. Meaningful variation: PASS. The email uses a subdomain.
4. Test data compliance: PASS. Synthetic staging test data is used.
5. Stranger Test: PASS.

### SL-SIGNUP-005
1. UI element existence: PASS.
2. Spec traceability: PASS against the exercise's stated 254-character HTML5 boundary.
3. Meaningful variation: PASS. It tests the maximum-length boundary.
4. Test data compliance: PASS. Synthetic staging test data is used.
5. Stranger Test: PASS.

### SL-SIGNUP-006
1. UI element existence: PASS.
2. Spec traceability: PASS.
3. Meaningful variation: PASS. The local-part begins with numeric characters.
4. Test data compliance: PASS after edit. The incorrect external domain was replaced with the staging test-data domain.
5. Stranger Test: PASS.

# Verified Test Case Variations

## SL-SIGNUP-002

Test Case ID: SL-SIGNUP-002

Test Title: Plus-addressed email accepted on Saltlake signup form

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded with all 6 fields visible
- Browser console is open to observe network requests

Test Data:
- Email: customer.alice+marketing.signup-test@bedrock-staging.com
- Password: PassW0rd!23
- Postal Code: 80202
- Country: United States
- Age: 35
- Marketing opt-in: unchecked

Steps:
1. Click into the Email field.
2. Type the test email exactly as specified.
3. Click outside the field (Tab key or click on Password field).
4. Observe the field's validation state.

Expected Results:
- Email field shows no error message.
- Email field border is the default (not red, not flagged).
- Browser console shows no validation error logged.
- Plus-addressed email is accepted as valid input.

Postconditions:
- No backend request fired.
- Form is ready for next field input.

## SL-SIGNUP-003

Test Case ID: SL-SIGNUP-003

Test Title: Country-TLD email accepted on Saltlake signup form

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded with all 6 fields visible
- Browser console is open to observe network requests

Test Data:
- Email: customer.uk.signup-test@bedrock-staging.co.uk
- Password: PassW0rd!23
- Postal Code: 80202
- Country: United States
- Age: 35
- Marketing opt-in: unchecked

Steps:
1. Click into the Email field.
2. Type the test email exactly as specified.
3. Click outside the field (Tab key or click on Password field).
4. Observe the field's validation state.

Expected Results:
- Email field shows no error message.
- Email field border is the default (not red, not flagged).
- Browser console shows no validation error logged.
- Country-TLD email is accepted as valid input.

Postconditions:
- No backend request fired.
- Form is ready for next field input.

## SL-SIGNUP-004

Test Case ID: SL-SIGNUP-004

Test Title: Subdomain email accepted on Saltlake signup form

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded with all 6 fields visible
- Browser console is open to observe network requests

Test Data:
- Email: customer.alice.signup-test@mail.bedrock-staging.com
- Password: PassW0rd!23
- Postal Code: 80202
- Country: United States
- Age: 35
- Marketing opt-in: unchecked

Steps:
1. Click into the Email field.
2. Type the test email exactly as specified.
3. Click outside the field (Tab key or click on Password field).
4. Observe the field's validation state.

Expected Results:
- Email field shows no error message.
- Email field border is the default (not red, not flagged).
- Browser console shows no validation error logged.
- Email containing a subdomain is accepted as valid input.

Postconditions:
- No backend request fired.
- Form is ready for next field input.

## SL-SIGNUP-005

Test Case ID: SL-SIGNUP-005

Test Title: Maximum-length email accepted at the 254-character boundary

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded with all 6 fields visible
- Browser console is open to observe network requests

Test Data:
- Email: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa.signup-test@bedrock-staging.com
- Email length: 254 characters total
- Password: PassW0rd!23
- Postal Code: 80202
- Country: United States
- Age: 35
- Marketing opt-in: unchecked

Steps:
1. Click into the Email field.
2. Type the 254-character test email exactly as specified.
3. Click outside the field (Tab key or click on Password field).
4. Observe the field's validation state.

Expected Results:
- Email field shows no error message.
- Email field border is the default (not red, not flagged).
- Browser console shows no validation error logged.
- The email is accepted at the stated 254-character maximum boundary.

Postconditions:
- No backend request fired.
- Form is ready for next field input.

## SL-SIGNUP-006

Test Case ID: SL-SIGNUP-006

Test Title: Numeric local-part email accepted on Saltlake signup form

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded with all 6 fields visible
- Browser console is open to observe network requests

Test Data:
- Email: 12345.signup-test@bedrock-staging.com
- Password: PassW0rd!23
- Postal Code: 80202
- Country: United States
- Age: 35
- Marketing opt-in: unchecked

Steps:
1. Click into the Email field.
2. Type the test email exactly as specified.
3. Click outside the field (Tab key or click on Password field).
4. Observe the field's validation state.

Expected Results:
- Email field shows no error message.
- Email field border is the default (not red, not flagged).
- Browser console shows no validation error logged.
- Email with a numeric local-part is accepted as valid input.

Postconditions:
- No backend request fired.
- Form is ready for next field input.