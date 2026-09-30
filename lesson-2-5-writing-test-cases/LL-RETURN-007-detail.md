# LL-RETURN-007 Detail View

## Test ID
LL-RETURN-007

## Test Title
Verify a return cannot be approved before the customer initiates the return

## Preconditions
1. A delivered LinenLane order exists and its return is currently in the `Eligible` state.
2. No `InitiateReturn` event has been submitted for the order.
3. A LinenLane returns agent has access to the returns workflow.

## Test Data
- Order ID: `LL-ORDER-1002`
- Current Return State: `Eligible`
- Invalid Event: `ApproveReturn`
- Expected State After Attempt: `Eligible`

## Steps to Execute
1. Sign in as a LinenLane returns agent.
2. Locate order `LL-ORDER-1002` in the returns system.
3. Confirm that the return is currently in the `Eligible` state.
4. Attempt to apply the `ApproveReturn` event to the return.
5. View the return state after the approval attempt.

## Expected Results
1. The system rejects the `ApproveReturn` event because approval is not valid from the `Eligible` state.
2. The return does not transition to the `Approved` state.
3. The return remains in the `Eligible` state.
4. No approval is recorded for order `LL-ORDER-1002`.

## Postconditions
The return remains in the `Eligible` state because the invalid transition was rejected. No cleanup is required because the return state was not changed.