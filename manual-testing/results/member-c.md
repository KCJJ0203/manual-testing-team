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

### Test ID: AGE-EP-90-C

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-c |
| Website | Test Pages validation form |
| Technique | Equivalence partitioning |
| Status | Pass |

#### Purpose

Check that an age from the above-80 partition is rejected.

#### Preconditions

The validation form is open.
All other fields will use the agreed valid baseline.

#### Test Data

| Field | Value |
|---|---|
| Age | `90` |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline.
3. Replace age with `90`.
4. Submit.
5. Observe the response.

#### Expected Result

Age 90 is rejected because it is above the maximum age of 80.

#### Actual Result

After entering the baseline with age 90 and selecting Submit, the browser
prevented submission. A validation bubble appeared next to the age field
saying "Please select a value that is no more than 80". The form was not
sent to the server.

#### Evidence

[View screenshot](../evidence/member-c/age-ep-90.png)

---

## 2-Point Boundary Tests

### Test ID: AGE-2P-80-C

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-c |
| Website | Test Pages validation form |
| Technique | 2-point boundary testing |
| Status | Pass |

#### Purpose

Check that the maximum valid age is accepted.

#### Preconditions

The validation form is open.
All other fields will use the agreed valid baseline.

#### Test Data

| Field | Value |
|---|---|
| Age | `80` |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline.
3. Replace age with `80`.
4. Submit.
5. Observe the response.

#### Expected Result

Age 80 is accepted because it is the maximum valid age.

#### Actual Result

After entering the baseline with age 80 and selecting Submit, the form
submitted successfully and the results page showed the age as 80. No
validation errors appeared.

#### Evidence

[View screenshot](../evidence/member-c/age-2p-80.png)

---

## 3-Point Boundary Tests

### Test ID: AGE-3P-79-C

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-c |
| Website | Test Pages validation form |
| Technique | 3-point boundary testing |
| Status | Pass |

#### Purpose

Check that the value just inside the maximum boundary is accepted.

#### Preconditions

The validation form is open.
All other fields will use the agreed valid baseline.

#### Test Data

| Field | Value |
|---|---|
| Age | `79` |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline.
3. Replace age with `79`.
4. Submit.
5. Observe the response.

#### Expected Result

Age 79 is accepted because it is within the valid range of 18 to 80.

#### Actual Result

After entering the baseline with age 79 and selecting Submit, the form
submitted successfully and the results page showed the age as 79. No
validation errors appeared.

#### Evidence

[View screenshot](../evidence/member-c/age-3p-79.png)

---