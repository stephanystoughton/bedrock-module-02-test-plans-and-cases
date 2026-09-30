# # LinenLane Returns State Transitions

This document defines the state transition design for the LinenLane returns workflow. The workflow contains six states and six events that determine how a return can move from one state to another. The state transition table identifies every valid and invalid state-event combination, while the diagram shows all valid transitions visually. The test cases verify both successful transitions and invalid events that the system should reject.

## State Transition Table

| Current State | InitiateReturn | ApproveReturn | RejectReturn | ConfirmReceipt | ProcessRefund | ExpireWindow |
|---|---|---|---|---|---|---|
| Eligible | Requested | - | - | - | - | Rejected (window expired) |
| Requested | - | Approved | Rejected | - | - | - |
| Approved | - | - | - | ItemReceived | - | - |
| Rejected | - | - | - | - | - | - |
| ItemReceived | - | - | - | - | Refunded | - |
| Refunded | - | - | - | - | - | - |

A dash (-) means that the event is invalid for the current state and should be rejected by the system.

## State Transition Diagram

```text
                         InitiateReturn
                +---------------------------->
                |                             |
                |                             v
          +------------+               +-------------+
          |  Eligible  |               |  Requested  |
          +------------+               +-------------+
                |                         |         |
                |                         |         |
                | ExpireWindow            |         |
                v                         |         |
          +------------+          ApproveReturn   RejectReturn
          |  Rejected  |                |            |
          +------------+                v            v
            TERMINAL              +------------+  +------------+
                                  |  Approved  |  |  Rejected  |
                                  +------------+  +------------+
                                        |           TERMINAL
                                        |
                                  ConfirmReceipt
                                        |
                                        v
                                 +--------------+
                                 | ItemReceived |
                                 +--------------+
                                        |
                                        |
                                  ProcessRefund
                                        |
                                        v
                                  +------------+
                                  |  Refunded  |
                                  +------------+
                                     TERMINAL
 Valid transitions shown in the diagram:

Eligible –InitiateReturn–> Requested
Eligible –ExpireWindow–> Rejected
Requested –ApproveReturn–> Approved
Requested –RejectReturn–> Rejected
Approved –ConfirmReceipt–> ItemReceived
ItemReceived –ProcessRefund–> Refunded

Rejected and Refunded are terminal states, so no events can move a return out of either state.

Test Case Table          
Test ID
Test Description
Starting State
Event
Expected End State
Valid?
LL-RETURN-001
Verify an eligible return can be initiated by the customer
Eligible
InitiateReturn
Requested
Yes
LL-RETURN-002
Verify an eligible return becomes rejected when the 30-day return window expires
Eligible
ExpireWindow
Rejected (window expired)
Yes
LL-RETURN-003
Verify a requested return can be approved by a returns agent
Requested
ApproveReturn
Approved
Yes
LL-RETURN-004
Verify a requested return can be rejected by a returns agent
Requested
RejectReturn
Rejected
Yes
LL-RETURN-005
Verify receipt of an approved returned item can be confirmed by the warehouse
Approved
ConfirmReceipt
ItemReceived
Yes
LL-RETURN-006
Verify a refund can be processed after the returned item has been received
ItemReceived
ProcessRefund
Refunded
Yes
LL-RETURN-007
Verify a return cannot be approved before the customer initiates the return
Eligible
ApproveReturn
Eligible (no change)
No
LL-RETURN-008
Verify a refund cannot be processed before the returned item has been received
Approved
ProcessRefund
Approved (no change)
No
LL-RETURN-009
Verify receipt cannot be confirmed while the return is only in Requested state
Requested
ConfirmReceipt
Requested (no change)
No
LL-RETURN-010
Verify a new return cannot be initiated after the return has been rejected
Rejected
InitiateReturn
Rejected (no change)
No
LL-RETURN-011
Verify an approved return cannot be rejected because rejection is only valid from Requested state
Approved
RejectReturn
Approved (no change)
No
LL-RETURN-012
Verify no additional refund event can be processed after the return has already been refunded
Refunded
ProcessRefund
Refunded (no change)
No
