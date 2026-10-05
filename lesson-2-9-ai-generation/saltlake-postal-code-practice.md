# Saltlake Postal Code Practice

## Seed Test Case

Test Case ID: SL-SIGNUP-PC-001

Test Title: Valid 5-digit US ZIP code accepted on Saltlake signup form

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded.
- The Country field is available and has not yet triggered postal code validation.
- Browser is ready for manual test execution.

Test Data:
- Email: postal.qa.signup-test@bedrock-staging.com
- Country: United States
- Postal Code: 80202

Steps:
1. Select "United States" in the Country field.
2. Click into the Postal Code field.
3. Enter `80202`.
4. Click outside the Postal Code field to trigger field-blur validation.
5. Observe the Postal Code field and the inline error message area below it.

Expected Results:
- The Postal Code value is accepted as a valid US 5-digit ZIP code.
- No inline validation error appears below the Postal Code field.
- The Postal Code field is not flagged as invalid.

Postconditions:
- Country remains set to United States.
- Postal Code remains `80202`.
- The form is ready for continued input.

---

## Variations

### SL-SIGNUP-PC-002

Technique: Equivalence Partition — valid Canadian postal code

Test Case ID: SL-SIGNUP-PC-002

Test Title: Valid Canadian postal code accepted on Saltlake signup form

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded.
- The Country field is available.
- Browser is ready for manual test execution.

Test Data:
- Email: postal.qa.signup-test@bedrock-staging.com
- Country: Canada
- Postal Code: K1A 0B1

Steps:
1. Select "Canada" in the Country field.
2. Click into the Postal Code field.
3. Enter `K1A 0B1`.
4. Click outside the Postal Code field to trigger field-blur validation.
5. Observe the Postal Code field and the inline error message area below it.

Expected Results:
- The Postal Code value is accepted as a valid Canadian postal code.
- No inline validation error appears below the Postal Code field.
- The Postal Code field is not flagged as invalid.

Postconditions:
- Country remains set to Canada.
- Postal Code remains `K1A 0B1`.
- The form is ready for continued input.

---

### SL-SIGNUP-PC-003

Technique: Equivalence Partition — valid UK postal code

Test Case ID: SL-SIGNUP-PC-003

Test Title: Valid UK postal code accepted on Saltlake signup form

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded.
- The Country field is available.
- Browser is ready for manual test execution.

Test Data:
- Email: postal.qa.signup-test@bedrock-staging.com
- Country: United Kingdom
- Postal Code: SW1A 1AA

Steps:
1. Select "United Kingdom" in the Country field.
2. Click into the Postal Code field.
3. Enter `SW1A 1AA`.
4. Click outside the Postal Code field to trigger field-blur validation.
5. Observe the Postal Code field and the inline error message area below it.

Expected Results:
- The Postal Code value is accepted as a valid UK postal code.
- No inline validation error appears below the Postal Code field.
- The Postal Code field is not flagged as invalid.

Postconditions:
- Country remains set to United Kingdom.
- Postal Code remains `SW1A 1AA`.
- The form is ready for continued input.

---

### SL-SIGNUP-PC-004

Technique: Boundary Value Analysis — one digit below the valid US 5-digit ZIP length

Test Case ID: SL-SIGNUP-PC-004

Test Title: Four-digit US ZIP code rejected on Saltlake signup form

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded.
- The Country field is available.
- Browser is ready for manual test execution.

Test Data:
- Email: postal.qa.signup-test@bedrock-staging.com
- Country: United States
- Postal Code: 8020

Steps:
1. Select "United States" in the Country field.
2. Click into the Postal Code field.
3. Enter `8020`.
4. Click outside the Postal Code field to trigger field-blur validation.
5. Observe the Postal Code field and the inline error message area below it.

Expected Results:
- The four-digit value is rejected because it does not meet the required 5-digit US ZIP format.
- An inline validation error appears below the Postal Code field.
- The Postal Code field is flagged as invalid.

Postconditions:
- Country remains set to United States.
- The invalid Postal Code value remains available for correction.
- The postal code validation error remains visible until the value is corrected.

---

### SL-SIGNUP-PC-005

Technique: Boundary Value Analysis — maximum field length of 10 characters

Test Case ID: SL-SIGNUP-PC-005

Test Title: Valid 10-character US ZIP+4 accepted at maximum field length

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded.
- The Country field is available.
- Browser is ready for manual test execution.

Test Data:
- Email: postal.qa.signup-test@bedrock-staging.com
- Country: United States
- Postal Code: 80202-1234
- Postal Code Length: 10 characters including the hyphen

Steps:
1. Select "United States" in the Country field.
2. Click into the Postal Code field.
3. Enter `80202-1234`.
4. Click outside the Postal Code field to trigger field-blur validation.
5. Observe the Postal Code field and the inline error message area below it.

Expected Results:
- The 10-character ZIP+4 value is accepted as a valid US postal code.
- The value is accepted at the field's stated maximum length.
- No inline validation error appears below the Postal Code field.
- The Postal Code field is not flagged as invalid.

Postconditions:
- Country remains set to United States.
- Postal Code remains `80202-1234`.
- The form is ready for continued input.

---

### SL-SIGNUP-PC-006

Technique: Decision-Table Row — selected country and postal code format do not match

Test Case ID: SL-SIGNUP-PC-006

Test Title: US ZIP code rejected when Canada is selected as the country

Preconditions:
- User is on https://staging.saltlake-test.bedrock-staging.com/signup
- The signup form is loaded.
- The Country field is available.
- Browser is ready for manual test execution.

Test Data:
- Email: postal.qa.signup-test@bedrock-staging.com
- Country: Canada
- Postal Code: 80202

Steps:
1. Select "Canada" in the Country field.
2. Click into the Postal Code field.
3. Enter `80202`.
4. Click outside the Postal Code field to trigger field-blur validation.
5. Observe the Postal Code field and the inline error message area below it.

Expected Results:
- Postal code validation runs after the Country field has been selected.
- The US ZIP value is rejected because it does not match the required Canadian `A1A 1A1` format.
- An inline validation error appears below the Postal Code field.
- The Postal Code field is flagged as invalid.

Postconditions:
- Country remains set to Canada.
- The invalid Postal Code value remains available for correction.
- The postal code validation error remains visible until the value is corrected.

---

## AI Test Case Verification Checklist

### Check 1: UI Element Existence

Verify that every UI element referenced by the generated test case actually exists on the Saltlake signup form. For postal code testing, expected elements are the Postal Code field, the Country field or dropdown, and the inline validation error area below the Postal Code field.

Example: If an AI-generated test case instructs the tester to click a "Validate Postal Code" button, reject or edit that step because the specification does not identify such a button.

Why it matters: AI can invent realistic-sounding UI elements. A test case referencing an element that does not exist cannot be executed reliably.

### Check 2: Specification Traceability

Verify that every expected result can be traced directly to the postal code specification. Confirm the correct country-specific formats: US `12345` or `12345-6789`, Canada `A1A 1A1`, and the specified UK alphanumeric formats. Also verify that validation occurs on field-blur, the Country field is selected first, and the maximum field length is 10 characters.

Example: If AI claims that a US ZIP must contain six digits, the variation fails this check because the specification defines 5-digit ZIP and ZIP+4 formats.

Why it matters: Expected results must come from the documented requirements rather than from assumptions made by the AI.

### Check 3: Meaningful Variation

Verify that the generated variation tests a genuinely different partition, boundary, or decision-table condition from the seed and from the other variations.

Example: Changing `80202` to another ordinary 5-digit ZIP such as `33647` without testing a different condition would be a cosmetic duplicate. Testing Canada `K1A 0B1`, a four-digit US value, or a country-format mismatch provides meaningful additional coverage.

Why it matters: Variations should increase test coverage rather than create multiple test cases for essentially the same behavior.

### Check 4: Test Data Compliance

Verify that all test data is realistic, synthetic, and consistent with the test data plan. If an email is required, it must use the `*.signup-test@bedrock-staging.com` convention. Confirm that postal codes match the selected country unless the mismatch is deliberate and documented as the condition being tested.

Example: A Canadian validation test using a real customer's address or an unrelated personal email would fail this check.

Why it matters: Controlled synthetic test data makes tests repeatable and prevents inappropriate use of real personal information.

### Check 5: Stranger Test

Verify that a tester who did not design the test case could execute it without asking questions. The test must clearly state which country to select, the exact Postal Code value to enter, when to trigger field-blur validation, and what result to observe.

Example: A step that says "Enter an invalid ZIP and verify the error" fails the Stranger Test because it does not define the country, exact value, or validation action. A clear version specifies: select United States, enter `8020`, click outside the field, and verify that an inline validation error appears.

Why it matters: A test case must remain understandable and executable by another tester without relying on undocumented knowledge from the original author.