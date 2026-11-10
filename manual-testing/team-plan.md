# Team Plan

## Team Identifier

manual-testing-team

## Members

### Member A
- GitHub username: KCJJ0203
- Coordination responsibility: Team coordination (timekeeping, activity sequence, task allocation). Shares repository integration with Member D.

### Member B
- GitHub username: ignatius5k
- Coordination responsibility: Requirements and baseline (checks published requirements, records agreed baseline data, flags unclear or changed requirements).

### Member C
- GitHub username: W1nnie69
- Coordination responsibility: Guided test coverage (checks all required guided test values are covered, identifies missing or unexecuted cases).

### Member D
- GitHub username: Naix-Here
- Coordination responsibility: Evidence organisation (consistent evidence filenames, no sensitive info in screenshots, working evidence links). Shares repository integration with Member A.

## Guided Test Allocation

| Member | Login (Activity 1) | Equivalence (Activity 2) | 2-Point Boundary (Activity 3) | 3-Point Boundary (Activity 4) |
|---|---|---|---|---|
| A | LOGIN-P01, LOGIN-R01 | Age 30 | Age 17 | Age 16 |
| B | LOGIN-N01 | Age 10 | Age 18 | Age 19 |
| C | LOGIN-N02 | Age 90 | Age 80 | Age 79 |
| D | LOGIN-N03 | Blank age, non-numeric `abc` | Age 81 | Age 82 |

For Activity 4, the results for 17, 18, 80 and 81 from Activity 3 are reused, since the baseline, environment and procedure did not change. Each member only ran one new 3-point value.

3-point convention: ISTQB CTFL v4.0 eight-value set (16, 17, 18, 19, 79, 80, 81, 82).

## Agreed Baseline Data

| Field | Baseline value |
|---|---|
| First name | `Alexander` |
| Surname | `TestingStudent` |
| Age | `30` |
| Country | `Singapore` |
| Notes | `Manual testing classroom exercise` |

This baseline passed validation ("Your Input passed validation"), as recorded in [Member B's AGE-EP-10-B preconditions](results/member-b.md#test-id-age-ep-10-b) and [Member A's AGE-EP-30-A](results/member-a.md#test-id-age-ep-30-a).

Change from the README baseline: the README first name `Alex` (4 characters) was rejected by the server with "Firstname too short", even though the published requirement only says the first name must be filled and be under 90 characters. The team changed the first name to `Alexander`, which was accepted. All other baseline values are the same as the README. See the baseline note in [AGE-EP-30-A](results/member-a.md#test-id-age-ep-30-a) and the evidence [baseline with `Alex` rejected](evidence/member-a/baseline-alex-rejected.png).

Requirement question raised: what is the server's real minimum first-name length? This was followed up in Member A's open-ended testing.

## Open-Ended Testing Allocation

### Member A - Open-Ended Testing

- Chosen area: Test Pages validation form, First name field
- Question to investigate: What first-name lengths does the server actually accept, given that the baseline `Alex` was rejected as too short although no minimum is published?

### Member B - Open-Ended Testing

- Chosen area: Test Pages validation form, Age field (recovery after an invalid value)
- Question to investigate: After the form blocks age `10`, can the user change only the age to `18` and submit again without resetting the form?

### Member C - Open-Ended Testing

- Chosen area: Surname field on the Test Pages validation form
- Question to investigate: Does the form accept surnames of exactly 11 and 79 characters, and reject 10 and 80?

### Member D - Open-Ended Testing

- Chosen area: SauceDemo login form (recovery after a missing username)
- Question to investigate: After login is blocked for a missing username, can the user enter `standard_user` and log in again without clearing or re-entering the password?

## Repository Integration Arrangements

- Each member works on their own branch `testing/member-x` and edits only their own files.
- Changes reach `main` through pull requests only.
- Members A and D review and merge pull requests.
