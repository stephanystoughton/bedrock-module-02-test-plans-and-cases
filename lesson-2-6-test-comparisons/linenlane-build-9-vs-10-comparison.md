# LinenLane Build 9 vs Build 10 Comparison Report

**Builds Compared:** Build 9 vs Build 10  
**Date:** October 1, 2026  
**Prepared by:** Stephany Stoughton  
**Reviewer:** Priya Subramanian  

---

## Executive Summary

Build 10 shows an overall improvement compared with Build 9, with a 68.0% pass rate across 25 tests versus a 60.9% pass rate across 23 executed tests in Build 9. The net improvement is **+1 defect**, with 4 defects fixed while 3 new failures appeared: 2 regressions and 1 ordinary new defect. Build 10 currently has 8 failing tests, including 5 carried-over defects from Build 9. The highest immediate risk is the two regressions in Login and Cart, followed by the new Checkout failure and the defects that remain unresolved from Build 9.

---

## Headline Metrics

| Metric | Build 9 | Build 10 | Change |
|---|---:|---:|---:|
| Tests Run | 23 | 25 | +2 |
| Pass Rate | 60.9% | 68.0% | +7.1 percentage points |
| Net Improvement | Baseline | +1 defect | +1 |

**Build 9 calculation:** 14 passed / 23 tests run = 60.9%  
**Build 10 calculation:** 17 passed / 25 tests run = 68.0%

The two "(not run)" tests in Build 9 were excluded from the Build 9 baseline.

---

## The Four Numbers

- **Fixed:** 4
- **New:** 1
- **Regressions:** 2
- **Carried-over:** 5

### Fixed Defects

The following tests failed in Build 9 and passed in Build 10:

- LL-CATALOG-003
- LL-CART-001
- LL-CHECKOUT-003
- LL-MIGRATE-002

### New Defect

The following test was not run in Build 9 and failed in Build 10, so it is categorized as an ordinary new defect rather than a regression:

- LL-CHECKOUT-005

### Regressions

The following tests passed in Build 9 and failed in Build 10:

- LL-LOGIN-002
- LL-CART-003

### Carried-Over Defects

The following tests failed in both Build 9 and Build 10:

- LL-CATALOG-004
- LL-CART-002
- LL-CHECKOUT-004
- LL-MIGRATE-001
- LL-PAYMENT-003

---

## Recommendation

For Build 11, prioritize the **LL-CART-003** and **LL-LOGIN-002** regressions first because these tests were passing in Build 9 and now fail in Build 10, indicating that previously working functionality has been broken. Next, investigate **LL-CHECKOUT-005**, which is an ordinary new defect because it was not run in Build 9, and confirm why the test was excluded from the previous build. After addressing the new failures, prioritize the still-open carried-over defects, particularly **LL-MIGRATE-001**, **LL-PAYMENT-003**, **LL-CHECKOUT-004**, **LL-CART-002**, and **LL-CATALOG-004**, based on their severity and customer impact. After fixes are implemented, rerun the affected feature areas and regression suite before approving Build 11.

---

# Appendix A: Per-Feature-Area Defect Density — Build 10

| Feature Area | Tests Run | Failing Tests | Defect Density |
|---|---:|---:|---:|
| Login | 5 | 1 | 20.0% |
| Catalog | 4 | 1 | 25.0% |
| Cart | 5 | 2 | 40.0% |
| Checkout | 5 | 2 | 40.0% |
| Account Migration | 3 | 1 | 33.3% |
| Payment | 3 | 1 | 33.3% |
| **Total** | **25** | **8** | **32.0%** |

Defect density is calculated as:

**Failing Tests / Tests Run × 100**

Cart and Checkout currently have the highest defect density at 40.0%.

---

# Appendix B: Full Defect List — Build 10

| Test ID | Feature Area | Build 9 Status | Build 10 Status | Classification |
|---|---|---|---|---|
| LL-LOGIN-002 | Login | PASS | FAIL | Regression |
| LL-CATALOG-004 | Catalog | FAIL | FAIL | Carried-over |
| LL-CART-002 | Cart | FAIL | FAIL | Carried-over |
| LL-CART-003 | Cart | PASS | FAIL | Regression |
| LL-CHECKOUT-004 | Checkout | FAIL | FAIL | Carried-over |
| LL-CHECKOUT-005 | Checkout | Not Run | FAIL | New Defect |
| LL-MIGRATE-001 | Account Migration | FAIL | FAIL | Carried-over |
| LL-PAYMENT-003 | Payment | FAIL | FAIL | Carried-over |

**Total Build 10 defects: 8**

---

# Appendix C: Regressions

The following tests were passing in Build 9 and are failing in Build 10:

| Test ID | Feature Area | Build 9 | Build 10 |
|---|---|---|---|
| LL-LOGIN-002 | Login | PASS | FAIL |
| LL-CART-003 | Cart | PASS | FAIL |

**Total regressions: 2**

These regressions should receive high priority because they represent functionality that worked successfully in Build 9 but no longer works in Build 10.

---

# Appendix D: Clarifying Questions

1. Why were **LL-LOGIN-005** and **LL-CHECKOUT-005** not run in Build 9? Were they newly added tests, blocked tests, or excluded because of an environment or test-data issue?

2. Was **LL-CHECKOUT-005** newly introduced for Build 10, or did the test already exist but was skipped in Build 9?

3. What are the severity and priority levels of the eight defects currently failing in Build 10?

4. Are any of the carried-over defects known release blockers for Build 11?

5. Were there code changes in the Login or Cart areas between Build 9 and Build 10 that could explain the regressions in **LL-LOGIN-002** and **LL-CART-003**?

6. Should the two tests that were not run in Build 9 be included in future baseline comparisons once they have established execution history?