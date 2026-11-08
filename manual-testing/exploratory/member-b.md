# Self-Designed Testing — Member B

## Testing Idea

After the form blocks age `10`, correct only the age to `18` and submit again without resetting the form.

## Reason

The guided tests showed that age `10` is blocked and age `18` is accepted in separate attempts. This checks whether the form recovers correctly after an invalid attempt.

## Test Basis

The published instructions state that age must be between 18 and 80. This test assumes correcting an invalid age to a valid age should allow submission. The instructions do not explicitly describe recovery after validation feedback.

## Approach

Use the verified baseline: first name `Alexander`, surname `TestingStudent`, country `Singapore`, and notes `Manual testing classroom exercise`. Start with age `10`, attempt submission, then change only age to `18` and submit again on the same form.

## Test Cases

### Test ID: OWN-B-01

| Item | Details |
|---|---|
| Test type | Recovery |
| Tester | member-b |
| Status | Pass |

#### Purpose

Check whether correcting an invalid age allows submission without resetting the form.

#### Preconditions

The Test Pages validation form is open with no data entered. The baseline values above have previously passed validation.

#### Test Data

| Field | Value |
|---|---|
| First name | `Alexander` |
| Surname | `TestingStudent` |
| Age, first attempt | `10` |
| Age, corrected attempt | `18` |
| Country | `Singapore` |
| Notes | `Manual testing classroom exercise` |

#### Steps

1. Enter the baseline values, using age `10`.
2. Select **Submit** and note the feedback.
3. Without resetting the form, change only age to `18`.
4. Select **Submit** again.
5. Note whether the validation report accepts the corrected submission and displays age `18`.

#### Expected Result

The first attempt is blocked because age `10` is below the stated minimum. After changing only age to `18`, the form submits successfully and reports age `18`.

#### Actual Result

The first submission was blocked by browser validation with “Value must be greater than or equal to 18.” The form kept the entered values. I changed only age from `10` to `18` and submitted again without resetting the form. The validation report then stated “Your Input passed validation” and displayed age `18` with the same first name, surname, country, and notes.

#### Evidence

No screenshot saved. Both attempts were observed during the test.

---

## Overall Observations

The form allowed recovery after an invalid age. Browser validation stopped the age `10` attempt; correcting the age to `18` allowed a successful submission without re-entering the other fields.

Member B manually reran this sequence in Google Chrome with country `Singapore` and confirmed the same result: age `10` was blocked, then correcting only age to `18` allowed submission.

## Next Question

Would correction also work after an invalid value in another field, such as a surname shorter than 11 characters?
