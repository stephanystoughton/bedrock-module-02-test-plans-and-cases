# LinenLane Display Name Test Cases

This document contains the test case design for the LinenLane signup form's Display Name field. The test cases apply equivalence partitioning and boundary value analysis to verify the field's validation rules. The goal is to cover valid and invalid input classes while focusing on the minimum and maximum length boundaries. The combined test cases ensure that every identified partition and every required boundary value is tested.

## 1. Equivalence Partition Table

| Partition Name | Type | Rule / Description | Example Input |
|---|---|---|---|
| Valid display name | Valid | 3–20 characters, allowed characters only, contains at least one letter, no leading or trailing spaces, no consecutive spaces, and is unique case-insensitively | Alice123 |
| Too short | Invalid | Fewer than 3 characters | Ab |
| Too long | Invalid | More than 20 characters | ABCDEFGHIJKLMNOPQRSTU |
| Contains invalid character | Invalid | Contains a character other than letters, numbers, or spaces | Alice! |
| All numbers | Invalid | Contains only numbers and no letters | 12345 |
| Starts with a space | Invalid | First character is a space |  Alice |
| Ends with a space | Invalid | Last character is a space | Alice  |
| Contains consecutive spaces | Invalid | Contains two or more spaces in a row | Alice  Smith |
| Case-insensitive duplicate | Invalid | Matches an existing display name when case is ignored | alice |

> Assumption for the case-insensitive uniqueness test: a display name of `Alice` already exists in the system.

---

## 2. Boundary Value Table

| Input | Position Relative to Boundary | Should the System Accept It? |
|---|---|---|
| Ab | Just below the minimum length of 3 characters | No |
| Ab1 | On the minimum length of 3 characters | Yes |
| Ab12 | Just above the minimum length | Yes |
| ABCDEFGHIJKLMNOPQRS | Just below the maximum length of 20 characters (19 characters) | Yes |
| ABCDEFGHIJKLMNOPQRST | On the maximum length of 20 characters | Yes |
| ABCDEFGHIJKLMNOPQRSTU | Just above the maximum length (21 characters) | No |

---

## 3. Combined Test Case Table

| Test ID | Test Description | Input | Expected Result | Partition Type | Boundary Status |
|---|---|---|---|---|---|
| LL-SIGNUP-001 | Verify display name below minimum length is rejected | Ab | Validation error: display name must be 3 to 20 characters | Invalid – Too short | Just below minimum |
| LL-SIGNUP-002 | Verify display name at minimum length is accepted | Ab1 | Display name is accepted and signup can continue | Valid | On minimum |
| LL-SIGNUP-003 | Verify display name just above minimum length is accepted | Ab12 | Display name is accepted and signup can continue | Valid | Just above minimum |
| LL-SIGNUP-004 | Verify 19-character display name is accepted | ABCDEFGHIJKLMNOPQRS | Display name is accepted and signup can continue | Valid | Just below maximum |
| LL-SIGNUP-005 | Verify display name at maximum length is accepted | ABCDEFGHIJKLMNOPQRST | Display name is accepted and signup can continue | Valid | On maximum |
| LL-SIGNUP-006 | Verify display name above maximum length is rejected | ABCDEFGHIJKLMNOPQRSTU | Validation error: display name must be 3 to 20 characters | Invalid – Too long | Just above maximum |
| LL-SIGNUP-007 | Verify display name containing an invalid special character is rejected | Alice! | Validation error: display name may contain only letters, numbers, and spaces | Invalid – Invalid character | Not a boundary test |
| LL-SIGNUP-008 | Verify display name containing only numbers is rejected | 12345 | Validation error: display name must contain at least one letter | Invalid – All numbers | Not a boundary test |
| LL-SIGNUP-009 | Verify display name starting with a space is rejected |  Alice | Validation error: display name cannot start with a space | Invalid – Starts with space | Not a boundary test |
| LL-SIGNUP-010 | Verify display name ending with a space is rejected | Alice  | Validation error: display name cannot end with a space | Invalid – Ends with space | Not a boundary test |
| LL-SIGNUP-011 | Verify display name containing consecutive spaces is rejected | Alice  Smith | Validation error: display name cannot contain consecutive spaces | Invalid – Consecutive spaces | Not a boundary test |
| LL-SIGNUP-012 | Verify display name uniqueness check is case-insensitive | alice | Validation error: display name is already in use because `Alice` already exists and uniqueness checking is case-insensitive | Invalid – Case-insensitive duplicate | Not a boundary test |

---

## Self-Check

- At least 8 partitions total: Yes. There are 9 total partitions: 1 valid and 8 invalid.
- No redundant partitions: Yes.
- Both length boundaries covered with three values each: Yes.
  - Minimum boundary: 2, 3, and 4 characters.
  - Maximum boundary: 19, 20, and 21 characters.
- Every combined test case has a specific Expected Result: Yes.
- Test IDs use the LL-SIGNUP-NNN format: Yes.
- Every equivalence partition appears in the combined test case table: Yes.
- Every boundary value appears in the combined test case table: Yes.