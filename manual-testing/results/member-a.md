# Manual Testing Results — Member A

## Environment

| Item | Details |
|---|---|
| Tester identifier | member-a |
| Date and time | 3 Nov 2026, 10:25 |
| Browser and version | Microsoft Edge 156.0.4314.58 |
| Operating system | Windows 11 Pro 25H2 |

## Login Tests

### Test ID: LOGIN-P01

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-a |
| Website | SauceDemo |
| Status | Pass |

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

After selecting Login with `standard_user` and `secret_sauce`, the Products page (`/inventory.html`) appeared and the product list was visible.

#### Evidence

Not captured (passing test, written result recorded).

---

### Test ID: LOGIN-R01

| Item | Details |
|---|---|
| Test type | Recovery |
| Tester | member-a |
| Website | SauceDemo |
| Status | Pass |

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

Attempt 1: After selecting Login with `wrong_password`, the login was rejected. The page stayed on the login screen, both fields were marked with red ✕ icons, and the error "Epic sadface: Username and password do not match any user in this service" was shown.

Attempt 2: Without refreshing, the password was replaced with `secret_sauce` and Login was selected again. The Products page (`/inventory.html`) appeared and the product list was visible.

#### Evidence

- [Rejected attempt](../evidence/member-a/login-r01-rejected.png)
- [Successful login after correction](../evidence/member-a/login-r01-success.png)

---


## Equivalence Partitioning

### Test ID: AGE-EP-30-A

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-a |
| Website | Test Pages — Client Server Form Validation |
| Partition | EP-02 (18–80 inclusive) |
| Status | Pass |

#### Purpose

Check that an age inside the valid partition (18–80 inclusive) is accepted.

#### Preconditions

Form restored to its starting state. All other fields hold the team's valid baseline.

#### Test Data

| Field | Value |
|---|---|
| First name | `Alexander` (see baseline note) |
| Surname | `TestingStudent` |
| Age | `30` |
| Country | Singapore |
| Notes | `Manual testing classroom exercise` |

#### Steps

1. Restore the form.
2. Enter the valid baseline.
3. Keep age as `30` (only age is varied in this activity).
4. Submit the form.
5. Observe acceptance or rejection.
6. Where displayed, verify the submitted age.

#### Expected Result

Accept: the form submits successfully and the submitted age shows as 30.

#### Actual Result

The form submitted successfully. The Validation Report showed "Valid Input — Your Input passed validation", and the submitted values listed Age as 30 with all other baseline fields unchanged.

**Baseline note:** the first submission used the README baseline first name `Alex` (4 characters). The server rejected it with "Firstname Error — Firstname too short", even though the published requirement only says the first name "must be filled" and be under 90 characters, and the page's client-side check accepts more than 2 characters. The baseline first name was changed to `Alexander`, which was accepted. Requirement question: what is the server's minimum first-name length? The server rule does not match the published requirement or the client-side check.

#### Evidence

- [Age 30 accepted](../evidence/member-a/age-ep-30-a.png)
- [Baseline with `Alex` rejected](../evidence/member-a/baseline-alex-rejected.png)

---

## 2-Point Boundary Tests

## 3-Point Boundary Tests
