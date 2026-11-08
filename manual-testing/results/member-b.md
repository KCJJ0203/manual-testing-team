# Manual Testing Results — Member B

## Environment

| Item | Details |
|---|---|
| Tester identifier | member-b |
| Date and time | 8 November 2026, approximately 7:16 PM Singapore time |
| Browser and version | Google Chrome 157.0.8103.38 (rerun by member-b) |
| Operating system | macOS |

Member B reran the recorded tests in Google Chrome and confirmed the same results. The form tests were then repeated with country `Singapore` with Codex browser assistance; the baseline and age results matched the records below.

## Login Tests

### Test ID: LOGIN-N01

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-b |
| Website | SauceDemo |
| Status | Pass |

#### Purpose

Check that an incorrect password does not allow login.

#### Preconditions

The SauceDemo login page is open and the user is logged out.

#### Test Data

| Field | Value |
|---|---|
| Username | `standard_user` |
| Password | `wrong_password` |

#### Steps

1. Open the SauceDemo login page while logged out.
2. Enter `standard_user` and `wrong_password`.
3. Select **Login**.
4. Observe the page and feedback.

#### Expected Result

Login is rejected, error feedback appears, and the inventory is not reached.

#### Actual Result

After the login attempt, the login form remained visible. A red error banner stated, “Epic sadface: Username and password do not match any user in this service.” The inventory page was not visible.

#### Evidence

[Screenshot of rejected login](../evidence/member-b/login-n01-rejected.png)

---

## Equivalence Partitioning

### Test ID: AGE-EP-10-B

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-b |
| Website | Test Pages validation form |
| Technique | Equivalence partitioning, below the valid age range |
| Status | Pass |

#### Purpose

Check that an age below 18 is rejected while all other inputs are valid.

#### Preconditions

A baseline submission with first name `Alexander`, surname `TestingStudent`, age `30`, country `Singapore`, and notes `Manual testing classroom exercise` returned “Your Input passed validation”.

#### Test Data

| Field | Value |
|---|---|
| First name | `Alexander` |
| Surname | `TestingStudent` |
| Age | `10` |
| Country | `Singapore` |
| Notes | `Manual testing classroom exercise` |

#### Steps

1. Enter the same successful baseline values in the form.
2. Change only age from `30` to `10`.
3. Select **Submit**.
4. Observe whether submission completes and what feedback appears.

#### Expected Result

Age 10 is rejected because the valid classroom range is 18–80 inclusive.

#### Actual Result

The browser prevented submission and displayed “Value must be greater than or equal to 18.” The form remained visible with age `10`. This was browser validation; no server rejection was observed for this attempt.

#### Evidence

The validation message was observed during the test; no screenshot has been saved to the repository for this test.

---

## 2-Point Boundary Tests

### Test ID: AGE-2P-18-B

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-b |
| Website | Test Pages validation form |
| Technique | 2-point boundary testing |
| Status | Pass |

#### Purpose

Check that the minimum permitted age, 18, is accepted.

#### Preconditions

The other fields use the verified valid baseline: `Alexander`, `TestingStudent`, `Singapore`, and `Manual testing classroom exercise`.

#### Test Data

| Field | Value |
|---|---|
| Age | `18` |
| Other fields | Verified valid baseline |

#### Steps

1. Enter the verified valid baseline in the form.
2. Set age to `18`.
3. Select **Submit** and observe the validation report.

#### Expected Result

The form accepts age 18 because it is the minimum valid age.

#### Actual Result

The form submitted successfully. The validation report stated “Your Input passed validation” and listed age `18` with the baseline values.

#### Evidence

No screenshot saved; the result was observed during the test.

---

## 3-Point Boundary Tests

### Test ID: AGE-3P-19-B

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-b |
| Website | Test Pages validation form |
| Technique | 3-point boundary testing |
| Status | Pass |

#### Purpose

Check the value immediately above the minimum permitted age.

#### Preconditions

The other fields use the verified valid baseline: `Alexander`, `TestingStudent`, `Singapore`, and `Manual testing classroom exercise`.

#### Test Data

| Field | Value |
|---|---|
| Age | `19` |
| Other fields | Verified valid baseline |

#### Steps

1. Enter the verified valid baseline in the form.
2. Set age to `19`.
3. Select **Submit** and observe the validation report.

#### Expected Result

The form accepts age 19 because it is within the valid range.

#### Actual Result

The form submitted successfully. The validation report stated “Your Input passed validation” and listed age `19` with the baseline values.

#### Evidence

No screenshot saved; the result was observed during the test.

---
