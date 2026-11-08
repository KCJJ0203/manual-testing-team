# Manual Testing Results — Member C

## Environment

| Item | Details |
|---|---|
| Tester identifier | member-c |
| Date and time | 8 Nov 2026, 8:22 PM (SGT) |
| Browser and version | FireFox Version 159.0.1 |
| Operating system | Windows 11 |

## Login Tests

### Test ID: LOGIN-N02

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-c |
| Website | SauceDemo |
| Status | Pass |

#### Purpose

Check that login is rejected when the password is missing.

#### Preconditions

The login page is open, no user is logged in, and both fields are empty.

#### Test Data

| Field | Value |
|---|---|
| Username | standard_user |
| Password | (empty) |

#### Steps

1. Follow the shared starting procedure.
2. Enter the username.
3. Leave the password empty.
4. Select Login.
5. Observe the feedback.

#### Expected Result

The attempt is rejected with validation feedback. The inventory is not reached.

#### Actual Result

After selecting Login with the password left empty, the page stayed on the
login screen and the error message "Epic sadface: Password is required"
appeared. The inventory page was not reached.

#### Evidence

[View screenshot](../evidence/member-c/login-n02.png)

---

## Equivalence Partitioning

## 2-Point Boundary Tests

## 3-Point Boundary Tests