# Lesson 2.5 - Writing Test Cases Other People Can Execute

This folder contains three detailed LinenLane test cases expanded from the summary-view test cases created in Lessons 2.3 and 2.4.

## Test Cases

### LL-SIGNUP-005
Original Test ID: `LL-SIGNUP-005`

This test verifies that a Display Name containing exactly 20 characters, the maximum allowed length, is accepted by the system. The summary view identified the input, boundary, and expected result, while the detail view adds specific preconditions, test data, atomic execution steps, verifiable expected results, and a postcondition so another tester can execute the test without referring to the previous exercise.

### LL-RETURN-001
Original Test ID: `LL-RETURN-001`

This test verifies the valid state transition from `Eligible` to `Requested` when the customer initiates a return using the `InitiateReturn` event. The detail view expands the original summary row by defining the required starting conditions, specific test data, individual execution steps, observable expected results, and the resulting postcondition.

### LL-RETURN-007
Original Test ID: `LL-RETURN-007`

This test verifies that the system rejects an invalid `ApproveReturn` event when a return is still in the `Eligible` state. The detail view makes the original summary case independently executable by documenting the starting state, test data, atomic actions, expected rejection behavior, unchanged state, and postcondition.

## Stranger Test Reflection

Each detail-view test case includes enough information for a tester who has not reviewed the previous LinenLane exercises to understand the required starting conditions, data, actions, and expected behavior. The steps use one action per step, and the expected results describe specific observable outcomes rather than vague statements such as "verify it works."