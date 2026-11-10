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
- **Filename Standard:** `[TestID]_[Module]_[Result]_[YYYY-MM-DD].[ext]` (e.g., `LOGIN-N03_MissingUsername_Pass_2026-11-10.png`).
- **Privacy Standard:** Screen capture checked to ensure no PII, real passwords, or private keys are exposed.
- **Relative Pathing:** Evidence links strictly use relative repository paths (`../evidence/filename.png`).

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

[View Evidence](../evidence/LOGIN-N03_MissingUsername_Pass_2026-11-10.png)

---

## Equivalence Partitioning

### Test ID: AGE-EP-10-B

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-d |
| Website | Test Pages Validation Form |
| Status | Pass |

#### Purpose

Verify that an age input below the minimum value (e.g., 10) is rejected.

#### Preconditions

Validation form is open with valid baseline data entered.

#### Test Data

| Field | Value |
|---|---|
| Age | `10` |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed valid baseline data.
3. Change only the age field to `10`.
4. Submit the form.

#### Expected Result

Age 10 is rejected because it is below the minimum age requirement of 18.

#### Actual Result

Form submission was rejected with a validation message indicating age must be between 18 and 80.

#### Evidence

[View Evidence](../evidence/AGE-EP-10-B_Equivalence_Pass_2026-11-10.png)

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
| Age | `81` |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline data.
3. Replace age with `81`.
4. Submit the form.
5. Observe the response.

#### Expected Result

Age 81 is rejected because it exceeds the maximum allowed age of 80.

#### Actual Result

Form submission was rejected because age 81 is outside the valid range.

#### Evidence

[View Evidence](../evidence/AGE-2P-81-D_Boundary2P_Pass_2026-11-10.png)

---

## 3-Point Boundary Tests

### Test ID: AGE-3P-79-C

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-d |
| Website | Test Pages Validation Form |
| Status | Pass |

#### Purpose

Check 3-point boundary value analysis for age immediately below the upper limit (`79`).

#### Preconditions

Validation form is open with valid baseline data.

#### Test Data

| Field | Value |
|---|---|
| Age | `79` |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline data.
3. Replace age with `79`.
4. Submit the form.
5. Observe the response.

#### Expected Result

Age 79 is accepted because it falls within the valid range (18 to 80).

#### Actual Result

Form was submitted successfully and the confirmation page displayed age 79.

#### Evidence

[View Evidence](../evidence/AGE-3P-79-C_Boundary3P_Pass_2026-11-10.png)