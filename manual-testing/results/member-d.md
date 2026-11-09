# Manual Testing Results — Member D

## Environment

| Item | Details |
|---|---|
| Tester identifier | member-d |
| Date and time | 2026-11-10 04:40 AM |
| Browser and version | Google Chrome 131.0 |
| Operating system | Windows 11 |

---

## Login Tests

### Test ID: LOGIN-N03

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-d |
| Website | SauceDemo |
| Status | Not run |

#### Purpose
Check that leaving the username empty when attempting to log in is properly rejected.

#### Preconditions
The SauceDemo login page is open and fields are cleared.

#### Test Data

| Field | Value |
|---|---|
| Username | *Empty* |
| Password | `secret_sauce` |

#### Steps
1. Open the SauceDemo login page.
2. Leave the username field completely empty.
3. Enter `secret_sauce` into the Password field.
4. Click Login.

#### Expected Result
The attempt is rejected with validation feedback (e.g., username required error). The inventory is not reached.

#### Actual Result
Not recorded — test has not been executed.

#### Evidence
Not captured.