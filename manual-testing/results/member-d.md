# Manual Testing Results — Member D

## Environment

| Item | Details |
|---|---|
| Tester identifier | member-d |
| Date and time | 2026-11-10 04:41 AM |
| Browser and version | Google Chrome 131.0 |
| Operating system | Windows 11 |

---

## Evidence Organisation Guidelines (Member D Role)

As **Member D — Evidence Organisation**, all evidence collected for these test records adheres to the following team standards:
- **Filename Standard:** `[TestID]_[Module]_[Result].[ext]` (e.g., `LOGIN-N03_MissingUsername_Pass.png`).
- **Privacy Standard:** Screen capture checked to ensure no PII, real passwords, or private keys are exposed.
- **Relative Pathing:** Evidence links strictly use relative repository paths (`../evidence/member-d/filename.png`).

---

## Login Tests

### Test ID: LOGIN-N03

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-d |
| Website | SauceDemo |
| Status | Pass |

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
Login was rejected. An error banner reading "Epic sadface: Username is required" appeared, and the inventory page was not reached.

#### Evidence
[View Evidence](../evidence/member-d/LOGIN-N03_MissingUsername_Pass.png)

---

## Equivalence Partitioning

### Test ID: AGE-EP-BLANK

| Item | Details |
|---|---|
| Test type | Negative / Format |
| Tester | member-d |
| Website | Test Pages Validation Form |
| Status | Pass |

#### Purpose
Verify that leaving the age input blank during form submission is properly rejected.

#### Preconditions
Validation form is open with valid baseline data entered.

#### Test Data
| Field | Value |
|---|---|
| First name | `Alexander` |
| Surname | `TestingStudent` |
| Age | *Empty* |
| Country | `Singapore` |

#### Steps
1. Restore the validation form.
2. Enter valid baseline first name (`Alexander`) and surname (`TestingStudent`).
3. Leave the age field completely blank.
4. Submit the form.

#### Expected Result
Form submission is blocked because age is a required numeric input field.

#### Actual Result
Form validation blocked submission with a validation error indicating age must be provided.

#### Evidence
[View Evidence](../evidence/member-d/AGE-EP-BLANK_Equivalence_Pass.png)

---

### Test ID: AGE-EP-ABC

| Item | Details |
|---|---|
| Test type | Negative / Invalid Format |
| Tester | member-d |
| Website | Test Pages Validation Form |
| Status | Pass |

#### Purpose
Verify that entering non-numeric string data (`abc`) into the age input field is properly rejected.

#### Preconditions
Validation form is open with valid baseline data entered.

#### Test Data
| Field | Value |
|---|---|
| First name | `Alexander` |
| Surname | `TestingStudent` |
| Age | `abc` |
| Country | `Singapore` |

#### Steps
1. Restore the validation form.
2. Enter valid baseline first name (`Alexander`) and surname (`TestingStudent`).
3. Enter `abc` into the Age field.
4. Submit the form.

#### Expected Result
Form submission is blocked because age requires a numeric value.

#### Actual Result
Form validation blocked submission with an error indicating age cannot contain letters or non-numeric input.

#### Evidence
[View Evidence](../evidence/member-d/AGE-EP-ABC_Equivalence_Pass.png)

---

## 2-Point Boundary Tests

### Test ID: AGE-2P-81-D

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-d |
| Website | Test Pages Validation Form |
| Status | Pass |

#### Purpose
Check that an age immediately above the maximum boundary limit (81) is rejected.

#### Preconditions
Validation form is open with valid baseline data.

#### Test Data
| Field | Value |
|---|---|
| First name | `Alexander` |
| Surname | `TestingStudent` |
| Age | `81` |
| Country | `Singapore` |

#### Steps
1. Restore the validation form.
2. Enter baseline data with `Alexander` as First name.
3. Set age to `81`.
4. Submit the form.
5. Observe the response.

#### Expected Result
Age 81 is rejected because it exceeds the maximum allowed age of 80.

#### Actual Result
Form submission was rejected because age 81 is outside the valid range.

#### Evidence
[View Evidence](../evidence/member-d/AGE-2P-81-D_Boundary2P_Pass.png)

---

## 3-Point Boundary Tests

### Test ID: AGE-3P-82-D

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-d |
| Website | Test Pages Validation Form |
| Status | Pass |

#### Purpose
Check 3-point boundary value analysis for age above the upper boundary limit (`82`).

#### Preconditions
Validation form is open with valid baseline data.

#### Test Data
| Field | Value |
|---|---|
| First name | `Alexander` |
| Surname | `TestingStudent` |
| Age | `82` |
| Country | `Singapore` |

#### Steps
1. Restore the validation form.
2. Enter baseline data with `Alexander` as First name.
3. Set age to `82`.
4. Submit the form.
5. Observe the response.

#### Expected Result
Age 82 is rejected because it exceeds the valid boundary limit (18 to 80).

#### Actual Result
Form submission was rejected with an error banner indicating age must be less than or equal to 80.

#### Evidence
[View Evidence](../evidence/member-d/AGE-3P-82-D_Boundary3P_Pass.png)