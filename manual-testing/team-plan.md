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

| Member | Login (Activity 1) | Equivalence (Activity 2) |
|---|---|---|
| A | LOGIN-P01, LOGIN-R01 | Age 30 |
| B | LOGIN-N01 | Age 10 |
| C | LOGIN-N02 | Age 90 |
| D | LOGIN-N03 | Blank age, non-numeric `abc` |

Boundary allocations (Activities 3 and 4) to be added when reached.

## Agreed Baseline Data

To be recorded by Member B during Activity 2.

## Open-Ended Testing Allocation

### Member A — Open-Ended Testing

- Chosen area: Test Pages validation form, First name field
- Question to investigate: What first-name lengths does the server actually accept, given that the baseline `Alex` was rejected as too short although no minimum is published?

### Member C - Open-Ended Testing

- Chosen area: Surname field on the Test Pages validation form
- Question to investigate: Does the form accept surnames of exactly 11 and 79 characters, and reject 10 and 80?

## Repository Integration Arrangements

- Each member works on their own branch `testing/member-x` and edits only their own files.
- Changes reach `main` through pull requests only.
- Members A and D review and merge pull requests.
