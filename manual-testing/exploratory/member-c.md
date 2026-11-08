# Self-Designed Testing - Member C

## Testing Idea

Test the boundaries of the surname length rule on the validation form.

## Reason

The guided activities only tested age. Surname has its own length rule,
and the wording "between 11 and 79" does not say clearly whether 11 and 79
themselves are allowed.

## Test Basis

The instructions page says surname should be between 11 and 79 characters.

Assumption: "between" is inclusive, so 11 and 79 should be accepted.
This is not stated clearly, so results at 11 and 79 may answer a
requirement question rather than confirm a defect.

## Approach

Use 2-point boundary testing on surname length: 10, 11, 79, and 80
characters. Keep all other fields at the agreed baseline and change only
the surname.

## Test Cases

### Test ID: OWN-C-01

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-c |
| Status | Pass |

#### Purpose

Check that a surname just below the minimum length is rejected.

#### Preconditions

The validation form is open. All other fields use the agreed baseline.

#### Test Data

| Field | Value |
|---|---|
| Surname | `Abcdefghij` (10 characters) |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline.
3. Replace surname with the test value.
4. Submit.
5. Observe the response.

#### Expected Result

The surname is rejected because it is shorter than 11 characters.

#### Actual Result

After selecting Submit, the form stayed on the same page and red text
appeared under the surname field saying "Surname provided is too short".
The form was not submitted. Unlike the age field, no browser validation
bubble appeared.

#### Evidence

[View screenshot](../evidence/member-c/own-c-01.png)

---

### Test ID: OWN-C-02

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-c |
| Status | Pass |

#### Purpose

Check that a surname of exactly the minimum length is accepted.

#### Preconditions

The validation form is open. All other fields use the agreed baseline.

#### Test Data

| Field | Value |
|---|---|
| Surname | `Abcdefghijk` (11 characters) |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline.
3. Replace surname with the test value.
4. Submit.
5. Observe the response.

#### Expected Result

The surname is accepted, assuming "between 11 and 79" includes 11.

#### Actual Result

After selecting Submit, the form submitted successfully and the results
page showed the surname as Abcdefghijk. No validation errors appeared.
This suggests the minimum of 11 is inclusive.

#### Evidence

[View screenshot](../evidence/member-c/own-c-02.png)

---

### Test ID: OWN-C-03

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-c |
| Status | Pass |

#### Purpose

Check that a surname of exactly the maximum length is accepted.

#### Preconditions

The validation form is open. All other fields use the agreed baseline.

#### Test Data

| Field | Value |
|---|---|
| Surname | `abcdefghij` x7 + `abcdefghi` (79 characters) |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline.
3. Replace surname with the test value.
4. Submit.
5. Observe the response.

#### Expected Result

The surname is accepted, assuming "between 11 and 79" includes 79.

#### Actual Result

After selecting Submit, the form submitted successfully and the results
page showed the 79-character surname. No validation errors appeared.
This suggests the maximum of 79 is inclusive.

#### Evidence

[View screenshot](../evidence/member-c/own-c-03.png)

---

### Test ID: OWN-C-04

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-c |
| Status | Pass |

#### Purpose

Check that a surname just above the maximum length is rejected.

#### Preconditions

The validation form is open. All other fields use the agreed baseline.

#### Test Data

| Field | Value |
|---|---|
| Surname | `abcdefghij` x8 (80 characters) |
| Other fields | Agreed valid baseline |

#### Steps

1. Restore the validation form.
2. Enter the agreed baseline.
3. Replace surname with the test value.
4. Submit.
5. Observe the response.

#### Expected Result

The surname is rejected because it is longer than 79 characters.

#### Actual Result

After selecting Submit, the form stayed on the same page and red text
appeared under the surname field saying "Surname provided is too long".
The form was not submitted. No browser validation bubble appeared.

#### Evidence

[View screenshot](../evidence/member-c/own-c-04.png)

---

## Overall Observations

All four surname boundary tests matched the expected results. Surnames of
10 and 80 characters were rejected with red text under the field, while
11 and 79 characters were accepted. This answers the requirement question:
"between 11 and 79" is inclusive.

The surname field showed feedback differently from the age field. Age used
a browser validation bubble, while surname used red text on the page. This
suggests the two fields are checked in different ways.

## Next Question

Does the server also reject surnames that are too short or too long, or
only the page? If the page check were skipped, would the server still
catch it?