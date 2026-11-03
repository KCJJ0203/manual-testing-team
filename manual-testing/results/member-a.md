# Manual Testing Results — Member A

## Environment

| Item | Details |
|---|---|
| Tester identifier | member-a |
| Date and time | 3 Nov 2026, 10:25 |
| Browser and version | Google Chrome 156.0.8078.80 |
| Operating system | Windows 11 Pro 25H2 |

## Login Tests

### Test ID: LOGIN-P01

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-a |
| Website | SauceDemo |
| Status | Not run |

#### Purpose

Check that valid credentials allow access to the product inventory.

#### Preconditions

On the SauceDemo login page, logged out, both input fields empty.

#### Test Data

| Field | Value |
|---|---|
| Username | `standard_user` |
| Password | `secret_sauce` |

#### Steps

1. Open the login page, log out if logged in, and clear both fields.
2. Enter the username.
3. Enter the password.
4. Select `Login`.
5. Observe the page reached.
6. Check that products are visible.

#### Expected Result

The inventory page appears and products are visible.

#### Actual Result

Not recorded — test has not been executed.

#### Evidence

Not captured.

---

### Test ID: LOGIN-R01

| Item | Details |
|---|---|
| Test type | Recovery |
| Tester | member-a |
| Website | SauceDemo |
| Status | Not run |

#### Purpose

Check that correcting an invalid login attempt allows a subsequent valid login.

#### Preconditions

On the SauceDemo login page, logged out, both input fields empty.

#### Test Data

| Field | Value |
|---|---|
| Username | `standard_user` |
| Password (attempt 1) | `wrong_password` |
| Password (attempt 2) | `secret_sauce` |

#### Steps

1. Open the login page, log out if logged in, and clear both fields.
2. Enter `standard_user` and `wrong_password`.
3. Select `Login`.
4. Confirm rejection.
5. Replace the password with `secret_sauce`, keeping the username unchanged.
6. Select `Login` again.
7. Check whether the inventory appears.

#### Expected Result

The invalid attempt is rejected. After correcting the password, login succeeds and the inventory appears.

#### Actual Result

Not recorded — test has not been executed.

#### Evidence

Not captured.

---


## Equivalence Partitioning

## 2-Point Boundary Tests

## 3-Point Boundary Tests
