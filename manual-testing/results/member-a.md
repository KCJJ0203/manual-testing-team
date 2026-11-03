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

### Test ID: AGE-2P-17-A

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-a |
| Website | Test Pages — Client Server Form Validation |
| Technique | 2-point boundary testing |
| Status | Pass |

#### Purpose

Check that an age immediately below the minimum (18) is rejected.

#### Preconditions

The validation form is open and restored. All other fields use the agreed valid baseline.

#### Test Data

| Field | Value |
|---|---|
| First name | `Alexander` |
| Surname | `TestingStudent` |
| Age | `17` |
| Country | Singapore |
| Notes | `Manual testing classroom exercise` |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline.
3. Replace age with `17`.
4. Submit.
5. Observe the response.

#### Expected Result

Age 17 is rejected because it is below the minimum age of 18.

#### Actual Result

After selecting Submit, the form was not submitted. The browser (Microsoft Edge) showed its built-in validation message on the Age field: "Value must be greater than or equal to 18." The page stayed on the input form and no Validation Report appeared.

This rejection came from client-side (browser) validation, from the Age field's minimum of 18. The request never reached the server, so this result does not show whether the server would also reject age 17.

#### Evidence

[Browser validation message for age 17](../evidence/member-a/age-2p-17-a.png)

---

## 3-Point Boundary Tests

Convention: ISTQB CTFL v4.0 three-value boundary analysis (eight-value set 16, 17, 18, 19, 79, 80, 81, 82).

### Test ID: AGE-3P-16-A

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-a |
| Website | Test Pages — Client Server Form Validation |
| Technique | 3-point boundary testing |
| Status | Pass |

#### Purpose

Check that age 16 (one below the invalid-partition boundary value 17) is rejected.

#### Preconditions

The validation form is open and restored. All other fields use the agreed valid baseline.

#### Test Data

| Field | Value |
|---|---|
| First name | `Alexander` |
| Surname | `TestingStudent` |
| Age | `16` |
| Country | Singapore |
| Notes | `Manual testing classroom exercise` |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline.
3. Replace age with `16`.
4. Submit.
5. Observe the response.

#### Expected Result

Age 16 is rejected because it is below the minimum age of 18.

#### Actual Result

After selecting Submit, the form was not submitted. The browser (Microsoft Edge) showed its built-in validation message on the Age field: "Value must be greater than or equal to 18." The page stayed on the input form and no Validation Report appeared.

As with AGE-2P-17-A, this rejection came from client-side (browser) validation. The request never reached the server.

#### Evidence

[Browser validation message for age 16](../evidence/member-a/age-3p-16-a.png)

---

### Age 17 — Reused Execution

- Original test: `AGE-2P-17-A`
- Tester: `member-a`
- Record: see AGE-2P-17-A above in this file
- Reason for reuse: The baseline, environment, and procedure remain applicable.
