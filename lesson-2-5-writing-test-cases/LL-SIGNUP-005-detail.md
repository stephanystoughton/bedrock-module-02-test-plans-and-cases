# LL-SIGNUP-005 Detail View

## Test ID
LL-SIGNUP-005

## Test Title
Verify display name at maximum length is accepted

## Preconditions
1. The LinenLane signup page is open and available to the tester.
2. The Display Name field is visible and ready for input.
3. The display name `ABCDEFGHIJKLMNOPQRST` is not already registered in the system.

## Test Data
- Display Name: `ABCDEFGHIJKLMNOPQRST`
- Display Name Length: 20 characters

## Steps to Execute
1. Navigate to the LinenLane signup page.
2. Locate the Display Name field.
3. Enter `ABCDEFGHIJKLMNOPQRST` in the Display Name field.
4. Move focus away from the Display Name field to trigger validation.
5. Attempt to continue the signup process.

## Expected Results
1. The system accepts `ABCDEFGHIJKLMNOPQRST` as a valid Display Name.
2. No validation error is displayed for the Display Name field.
3. The Display Name remains entered without being modified or truncated.
4. The user is allowed to continue the signup process.

## Postconditions
The signup process may remain incomplete after the test. No cleanup is required because the test validates the Display Name field without requiring creation of a completed user account.