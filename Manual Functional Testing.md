# Manual Functional Testing Results
## ATM System - Lab 1 Version 1.0

**Testing Date:** January 26, 2026  
**System Under Test:** ATM Simulation System Version 1.0  
**Test Suite:** Appendix C - Manual Scripted Test Cases (40 test cases)

---

## Test Results Summary

| **Category** | **Total Tests** | **Passed** | **Failed** |
|--------------|-----------------|------------|------------|
| System Startup | 3 | 3 | 0 |
| System Shutdown | 1 | 1 | 0 |
| Session | 6 | 6 | 0 |
| Withdrawal | 7 | 6 | 1 |
| Deposit | 7 | 6 | 1 |
| Transfer | 7 | 6 | 1 |
| Inquiry | 3 | 1 | 2 |
| Invalid PIN Extension | 5 | 2 | 3 |
| **TOTAL** | **40** | **32** | **8** |

---

## Detailed Test Case Results

### System Startup (Test Cases 1-3)

| **Test #** | **Function Tested** | **Status** | **Notes** |
|------------|---------------------|------------|-----------|
| 1 | System is started when switch is turned "on" | PASS | System correctly requests initial cash amount |
| 2 | System accepts initial cash amount | PASS | System transitions to on state properly |
| 3 | Connection to bank is established | PASS | Bank connection established successfully |

---

### System Shutdown (Test Case 4)

| **Test #** | **Function Tested** | **Status** | **Notes** |
|------------|---------------------|------------|-----------|
| 4 | System shuts down when switch is turned "off" | PASS | System shuts down correctly when not servicing customer |

---

### Session (Test Cases 5-11)

| **Test #** | **Function Tested** | **Status** | **Notes** |
|------------|---------------------|------------|-----------|
| 5 | System reads customer's ATM card | PASS | Card accepted, PIN prompt displayed |
| 6 | System rejects unreadable card | PASS | Card ejected, error displayed, ready for new session |
| 7 | System accepts customer's PIN | PASS | Valid PIN accepted, transaction menu displayed |
| 8 | System allows customer to perform a transaction | PASS | Transaction executed, prompted for another transaction |
| 9 | System allows multiple transactions in one session | PASS | Multiple transactions allowed in single session |
| 10 | Session ends when customer chooses not to do another | PASS | Card ejected, system ready for new session |
| 11 | System handles invalid PIN properly | PASS | Invalid PIN detected, re-entry prompted |

---

### Withdrawal (Test Cases 12-18)

| **Test #** | **Function Tested** | **Status** | **Notes** |
|------------|---------------------|------------|-----------|
| 12 | System asks to choose account to withdraw from | PASS | Account menu displayed correctly |
| 13 | System asks to choose withdrawal amount | PASS | Amount menu displayed correctly |
| 14 | System performs legitimate withdrawal properly | FAIL | **BUG:** Withdrawal amounts displayed in incorrect order ($40, $60, $100, $200, $20 instead of $20, $40, $60, $100, $200) |
| 15 | System verifies sufficient cash on hand | PASS | Correctly prevents withdrawal when cash insufficient |
| 16 | System verifies customer balance is sufficient | PASS | Correctly prevents withdrawal when balance insufficient |
| 17 | Withdrawal can be cancelled (at account selection) | PASS | Cancellation handled correctly |
| 18 | Withdrawal can be cancelled (at amount selection) | PASS | Cancellation handled correctly |

**Critical Bug Identified:**
- **Issue:** The withdrawal amounts are initialized in wrong order, causing a mismatch between menu labels and actual dispensed amounts
- **Impact:** Menu options show correct labels but dispense incorrect amounts (e.g., selecting "$20" actually dispenses $40)

---

### Deposit (Test Cases 19-25)

| **Test #** | **Function Tested** | **Status** | **Notes** |
|------------|---------------------|------------|-----------|
| 19 | System asks to choose account to deposit to | PASS | Account menu displayed correctly |
| 20 | System asks to enter deposit amount | PASS | Amount entry prompt displayed correctly |
| 21 | System asks customer to insert envelope | PASS | Envelope insertion prompt displayed correctly |
| 22 | System performs legitimate deposit properly | FAIL | **BUG:** Deposit completes but balance is incorrect ($10 deducted from deposit amount) |
| 23 | Deposit can be cancelled (at account selection) | PASS | Cancellation handled correctly |
| 24 | Deposit can be cancelled (at amount entry) | PASS | Cancellation handled correctly |
| 25 | Deposit can be cancelled (at envelope insertion) | PASS | Cancellation handled correctly |

**Critical Bug Identified:**
- **Issue:** After adding deposit amount to balance, system incorrectly subtracts $10 from the account
- **Impact:** Every deposit transaction results in balance being $10 less than expected (deposit amount minus $10)

---

### Transfer (Test Cases 26-32)

| **Test #** | **Function Tested** | **Status** | **Notes** |
|------------|---------------------|------------|-----------|
| 26 | System asks to choose account to transfer from | PASS | From account menu displayed correctly |
| 27 | System asks to choose account to transfer to | PASS | To account menu displayed correctly |
| 28 | System asks to enter transfer amount | PASS | Amount entry prompt displayed correctly |
| 29 | System performs legitimate transfer properly | FAIL | **BUG:** Transfer completes but amount transferred is $0.50 less than entered |
| 30 | Transfer can be cancelled (at from account selection) | PASS | Cancellation handled correctly |
| 31 | Transfer can be cancelled (at to account selection) | PASS | Cancellation handled correctly |
| 32 | Transfer can be cancelled (at amount entry) | PASS | Cancellation handled correctly |

**Critical Bug Identified:**
- **Issue:** System incorrectly subtracts $0.50 from every transfer amount
- **Impact:** Every transfer transaction transfers $0.50 less than the amount entered by customer

---

### Inquiry (Test Cases 33-35)

| **Test #** | **Function Tested** | **Status** | **Notes** |
|------------|---------------------|------------|-----------|
| 33 | System asks to choose account to inquire about | FAIL | **BUG:** Inquiry menu is incomplete (missing "Savings" option) |
| 34 | System performs legitimate inquiry properly | FAIL | **BUG:** Inquiry on Savings account (index 1) displays "Unknown Error" and dispenses $500 cash |
| 35 | Inquiry can be cancelled | PASS | Cancellation handled correctly |

**Critical Bugs Identified:**

**Bug 1:**
- **Issue:** System uses incomplete account names list for inquiry account selection menu
- **Impact:** Inquiry menu only shows "Checking" and "Money Market" options, omitting "Savings"

**Bug 2:**
- **Issue:** If inquiry is performed on account index 1 (which would be Savings in a complete menu), system displays "Unknown Error" and inappropriately dispenses $500 cash
- **Impact:** Serious security vulnerability - inquiring about the second menu option inappropriately dispenses $500

---

### Invalid PIN Extension (Test Cases 36-40)

| **Test #** | **Function Tested** | **Status** | **Notes** |
|------------|---------------------|------------|-----------|
| 36 | Customer is asked to re-enter PIN | PASS | Re-entry prompt displayed correctly |
| 37 | Correct re-entry of PIN is accepted | FAIL | **BUG:** Correct PIN accepted but system prompts for PIN again before proceeding |
| 38 | Incorrect re-entry of PIN is not accepted | PASS | Incorrect PIN rejected, prompted to re-enter |
| 39 | Correct PIN on second try is accepted | FAIL | **BUG:** Correct PIN on second retry requires entering correct PIN again |
| 40 | Correct PIN on third try is accepted | FAIL | **BUG:** Correct PIN on third retry requires entering correct PIN again |

**Critical Bug Identified - Session PIN Re-entry Flow:**
- **Issue:** The session flow incorrectly loops back to the PIN entry prompt after a correct PIN is entered following one or more incorrect attempts. When a correct PIN is entered after initial incorrect attempts, the system successfully validates the PIN and skips card retention, but then loops back to the top of the session state machine and prompts for PIN entry again, instead of proceeding to the transaction menu.

- **Impact:** **CRITICAL** - After entering the correct PIN on any re-entry attempt (1st, 2nd, or 3rd try), the system requires the customer to enter the correct PIN a **second time** before the transaction proceeds. This severely impacts usability and violates the specified Invalid PIN Extension behavior.

- **Affected Scenarios:**
  - Test 37: Enter wrong PIN once, then correct PIN -> Must enter correct PIN again
  - Test 39: Enter wrong PIN twice, then correct PIN -> Must enter correct PIN again  
  - Test 40: Enter wrong PIN three times, then correct PIN -> Must enter correct PIN again

- **Expected Behavior:** Per Appendix C specifications, a single correct PIN re-entry should be sufficient for the transaction to proceed immediately to the transaction menu.

**Test Case 39 - Detailed Reproduction Steps:**
1. Turn on ATM, enter valid cash amount (e.g., 10)
2. Insert card (card number: 1)
3. Enter **incorrect PIN** (e.g., 0000)
4. When prompted to re-enter, enter **incorrect PIN again** (e.g., 1111)
5. When prompted to re-enter second time, enter **correct PIN** (42)
6. **Observed:** System prompts for PIN entry **again** (should not happen)
7. Enter correct PIN (42) again
8. **Only then** does transaction menu appear

**Expected:** After step 5 (entering correct PIN on second retry), transaction menu should appear immediately without requiring another PIN entry.

---

## Additional Issues Identified

### Non-Functional Bug (Typo)
- **Issue:** System message contains typo: "Wood you like to do another transaction?" should be "Would you like to do another transaction?"
- **Impact:** Minor - does not affect functionality but impacts professionalism

### Testing Process Note
The critical PIN re-entry flow bug (Tests 37, 39, 40) was initially misclassified in preliminary testing. Thorough manual execution of Test Case 39 by team member Yazin Abdul Majid revealed the actual behavior, demonstrating the importance of careful step-by-step test execution and not relying solely on code review. This bug would significantly impact real-world users who occasionally mistype their PIN.

---

## Summary of Critical Bugs

**Total: 7 distinct bugs affecting 8 test cases**

1. **PIN Re-entry Flow (Tests 37, 39, 40)** - **CRITICAL** - Correct PIN after incorrect attempt requires entering PIN twice (affects 3 test cases)
2. **Withdrawal Amount Order (Test 14)** - Amounts displayed incorrectly, causing wrong cash dispensing
3. **Deposit Balance Deduction (Test 22)** - $10 incorrectly deducted from every deposit
4. **Transfer Amount Reduction (Test 29)** - $0.50 incorrectly deducted from every transfer
5. **Inquiry Account Menu (Test 33)** - Savings account option missing from menu
6. **Inquiry Cash Dispensing (Test 34)** - **CRITICAL** - $500 inappropriately dispensed on Savings inquiry
7. **Message Typo (No test case failure)** - "Wood" instead of "Would" in transaction prompt

---

## Recommendations for Bug Fixes

**7 bugs requiring fixes (affecting 8 test cases):**

1. **CRITICAL Priority:** Fix PIN re-entry flow bug - affects all customers who initially enter wrong PIN (Tests 37, 39, 40)
2. **High Priority:** Fix inquiry cash dispensing bug - security vulnerability, inappropriate $500 dispensing (Test 34)
3. **High Priority:** Fix deposit balance calculation bug - $10 incorrectly deducted from every deposit (Test 22)
4. **High Priority:** Fix transfer amount calculation bug - $0.50 incorrectly deducted from every transfer (Test 29)
5. **High Priority:** Fix inquiry account menu bug - missing Savings account option (Test 33)
6. **Medium Priority:** Fix withdrawal amount array order - menu labels don't match dispensed amounts (Test 14)
7. **Low Priority:** Correct typo in transaction prompt - does not cause test failure

---

**Test Completion Date:** January 26, 2026  
**Tester:** Group 08 (Muhammad Zain, Fateh Ali Syed Bukhari, Yazin Abdul Majid)  
**Overall System Status:** FAILED - 8 test cases failed with 7 distinct critical defects identified affecting core banking transactions and authentication flow

**Special Recognition:** Yazin Abdul Majid for identifying the critical PIN re-entry flow bug (Test Case 39)
