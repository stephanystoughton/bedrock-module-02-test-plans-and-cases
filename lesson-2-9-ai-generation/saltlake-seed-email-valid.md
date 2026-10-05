# Saltlake Seed Test Case - Valid Email

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