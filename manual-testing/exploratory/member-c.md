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
| Status | Not run |

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

Not recorded - test has not been executed.

#### Evidence

Not captured.

---

### Test ID: OWN-C-02

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-c |
| Status | Not run |

#### Purpose

Check that a surname just below the minimum length is rejected.

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

Accepted, if “between” is inclusive

#### Actual Result

Not recorded - test has not been executed.

#### Evidence

Not captured.

---

### Test ID: OWN-C-03

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-c |
| Status | Not run |

#### Purpose

Check that a surname just below the minimum length is rejected.

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

Accepted, if “between” is inclusive

#### Actual Result

Not recorded - test has not been executed.

#### Evidence

Not captured.

---

### Test ID: OWN-C-04

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-c |
| Status | Not run |

#### Purpose

Check that a surname just below the minimum length is rejected.

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

Rejected, longer than 79

#### Actual Result

Not recorded - test has not been executed.

#### Evidence

Not captured.

---

## Overall Observations

## Next Question