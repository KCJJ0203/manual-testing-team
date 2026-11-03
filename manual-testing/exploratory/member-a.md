# Self-Designed Testing — Member A

## Testing Idea

Find the shortest and longest first names the server actually accepts on the Test Pages validation form.

## Reason

During the Activity 2 baseline, the README's first name `Alex` (4 characters) was rejected by the server with "Firstname too short". The published requirement does not mention a minimum length, so the server may be enforcing a hidden rule. Users with short real names (for example `Amy` or `Tan`) could be blocked.

## Test Basis

Published requirements (instructions page):

- firstname must be filled
- firstname must be less than 90 chars

The page's client-side check accepts first names longer than 2 characters and rejects 90 or more.

Unclear requirement: no minimum length is published, but the server rejected 4 characters. The expected results below follow the published requirement. Where the server differs, it is recorded as a mismatch and a requirement question, not a confirmed defect.

## Approach

- Keep every other field at the team baseline so only the first-name length changes.
- Part 1, minimum: test lengths 3, 5 and 7 to find roughly where the server starts accepting, then add follow-up tests on each side of that point (2-point boundary) once it is found.
- Part 2, maximum: 2-point boundary on the published limit (89 accept, 90 reject).

## Test Cases

### Test ID: OWN-A-01

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-a |
| Status | Fail |

#### Purpose

Check whether a 3-character first name (the shortest the client-side check allows) is accepted.

#### Preconditions

Validation form open and restored. All other fields hold the team baseline (Surname `TestingStudent`, Age `30`, Country Singapore, Notes `Manual testing classroom exercise`).

#### Test Data

| Field | Value |
|---|---|
| First name | `Amy` (3 characters) |

#### Steps

1. Restore the form and enter the baseline.
2. Replace the first name with the test value.
3. Submit.
4. Record whether the browser blocks it or the server returns a Validation Report, and the exact message.

#### Expected Result

Per the published requirement, accepted. Basis: it is filled and under 90 characters.

#### Actual Result

The browser allowed the submission (3 characters passes the client-side check), but the server's Validation Report showed "Firstname Error — Firstname too short". `Amy` was listed under "You submitted".

This differs from the published requirement, which only says the first name must be filled and be under 90 characters. Status is Fail against the published requirement. Whether the requirement or the server is wrong is an open requirement question.

#### Evidence

[`Amy` rejected by the server](../evidence/member-a/own-a-01.png)

---

### Test ID: OWN-A-02

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-a |
| Status | Pass |

#### Purpose

Check whether a 5-character first name is accepted.

#### Preconditions

Validation form open and restored. All other fields hold the team baseline (Surname `TestingStudent`, Age `30`, Country Singapore, Notes `Manual testing classroom exercise`).

#### Test Data

| Field | Value |
|---|---|
| First name | `Alexa` (5 characters) |

#### Steps

1. Restore the form and enter the baseline.
2. Replace the first name with the test value.
3. Submit.
4. Record whether the browser blocks it or the server returns a Validation Report, and the exact message.

#### Expected Result

Per the published requirement, accepted.

#### Actual Result

The server's Validation Report showed "Valid Input — Your Input passed validation", with `Alexa` listed under "You submitted".

#### Evidence

[`Alexa` accepted](../evidence/member-a/own-a-02.png)

---

### Test ID: OWN-A-03

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-a |
| Status | Pass |

#### Purpose

Check whether a 7-character first name is accepted.

#### Preconditions

Validation form open and restored. All other fields hold the team baseline (Surname `TestingStudent`, Age `30`, Country Singapore, Notes `Manual testing classroom exercise`).

#### Test Data

| Field | Value |
|---|---|
| First name | `Michael` (7 characters) |

#### Steps

1. Restore the form and enter the baseline.
2. Replace the first name with the test value.
3. Submit.
4. Record whether the browser blocks it or the server returns a Validation Report, and the exact message.

#### Expected Result

Per the published requirement, accepted.

#### Actual Result

The server's Validation Report showed "Valid Input — Your Input passed validation", with `Michael` listed under "You submitted".

#### Evidence

[`Michael` accepted](../evidence/member-a/own-a-03.png)

---

### Test ID: OWN-A-04

| Item | Details |
|---|---|
| Test type | Positive |
| Tester | member-a |
| Status | Pass |

#### Purpose

Check that an 89-character first name (one below the published maximum) is accepted.

#### Preconditions

Validation form open and restored. All other fields hold the team baseline (Surname `TestingStudent`, Age `30`, Country Singapore, Notes `Manual testing classroom exercise`).

#### Test Data

| Field | Value |
|---|---|
| First name | 89 characters (copy below) |

```text
AbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghi
```

#### Steps

1. Restore the form and enter the baseline.
2. Replace the first name with the test value.
3. Submit.
4. Record whether the browser blocks it or the server returns a Validation Report, and the exact message.

#### Expected Result

Accepted. Basis: "must be less than 90 chars".

#### Actual Result

The form submitted and the server's Validation Report showed "Valid Input — Your Input passed validation". The full 89-character first name was listed unchanged under "You submitted" (not truncated).

#### Evidence

[89-character first name accepted](../evidence/member-a/own-a-04.png)

---

### Test ID: OWN-A-05

| Item | Details |
|---|---|
| Test type | Negative |
| Tester | member-a |
| Status | Pass |

#### Purpose

Check that a 90-character first name (at the published limit) is rejected.

#### Preconditions

Validation form open and restored. All other fields hold the team baseline (Surname `TestingStudent`, Age `30`, Country Singapore, Notes `Manual testing classroom exercise`).

#### Test Data

| Field | Value |
|---|---|
| First name | 90 characters (copy below) |

```text
AbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghijAbcdefghij
```

#### Steps

1. Restore the form and enter the baseline.
2. Replace the first name with the test value.
3. Submit.
4. Record whether the browser blocks it or the server returns a Validation Report, and the exact message.

#### Expected Result

Rejected. Basis: "must be less than 90 chars". The client-side check should block it with "Firstname provided is too long".

#### Actual Result

After selecting Submit, the form was not submitted. The page's client-side (JavaScript) validation showed the red message "Firstname provided is too long" under the First name field, and the page stayed on the input form. The request did not reach the server, so this does not show whether the server also enforces the 90-character limit.

#### Evidence

[90-character first name blocked client-side](../evidence/member-a/own-a-05.png)

---

### Follow-up (change of approach)

OWN-A-01 (3 characters) was rejected and OWN-A-02 (5 characters) was accepted. The Activity 2 baseline `Alex` (4 characters) was also rejected. That points to a server minimum of 5 characters. OWN-A-06 adds a different 4-character name, to check that the rejection is about length and not the specific name `Alex`. Together with OWN-A-02, it forms a 2-point boundary at 4 → 5.

### Test ID: OWN-A-06

| Item | Details |
|---|---|
| Test type | Exploratory |
| Tester | member-a |
| Status | Fail |

#### Purpose

Confirm that the server rejects 4-character first names in general (one below the suspected server minimum of 5).

#### Preconditions

Validation form open and restored. All other fields hold the team baseline (Surname `TestingStudent`, Age `30`, Country Singapore, Notes `Manual testing classroom exercise`).

#### Test Data

| Field | Value |
|---|---|
| First name | `Anna` (4 characters) |

#### Steps

1. Restore the form and enter the baseline.
2. Replace the first name with `Anna`.
3. Submit.
4. Record whether the browser blocks it or the server returns a Validation Report, and the exact message.

#### Expected Result

Per the published requirement, accepted. Based on OWN-A-01, OWN-A-02 and the `Alex` baseline, the server is likely to reject it as too short.

#### Actual Result

The browser allowed the submission, but the server's Validation Report showed "Firstname Error — Firstname too short", with `Anna` listed under "You submitted". A second, different 4-character name was rejected the same way as `Alex`, so the rejection depends on length, not on the specific name. Status is Fail against the published requirement, as in OWN-A-01.

#### Evidence

[`Anna` rejected by the server](../evidence/member-a/own-a-06.png)

---

## Overall Observations

| Length | First name | Where checked | Result |
|---:|---|---|---|
| 3 | `Amy` | Server | Rejected, "Firstname too short" |
| 4 | `Alex` (Activity 2 baseline) | Server | Rejected, "Firstname too short" |
| 4 | `Anna` | Server | Rejected, "Firstname too short" |
| 5 | `Alexa` | Server | Accepted |
| 7 | `Michael` | Server | Accepted |
| 89 | 89 characters | Server | Accepted, full value shown |
| 90 | 90 characters | Browser (JavaScript) | Blocked, "Firstname provided is too long" |

- **Maximum:** behaves as published. 89 characters is accepted and 90 is blocked.
- **Minimum:** the server rejects first names shorter than 5 characters, so its minimum appears to be 5. The 2-point boundary is 4 (rejected) → 5 (accepted).
- **Three different rules:** the published requirement gives no minimum ("must be filled"). The client-side check accepts more than 2 characters. The server requires 5 or more. A user typing a 3- or 4-character name passes the browser check and only finds out from the server's error page.
- **Impact:** real short first names (for example `Amy`, `Anna`, `Tan`) cannot be submitted.
- Recorded as a mismatch and a requirement question, not a confirmed defect: it is not stated whether the published requirement or the server rule is the intended one.

## Next Question

- What is the intended minimum: the published "must be filled", the client's 3, or the server's 5?
- Does the server enforce the 90-character maximum itself, if the client-side check is bypassed (for example by sending the request directly)?
- Are spaces counted towards length (for example `Al  ` with trailing spaces)?
