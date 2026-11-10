# Team Summary

## Guided Testing Coverage

























 ## Member D 

## Guided Testing Coverage

### Login Testing
Required coverage:
- Valid credentials
- Incorrect password
- Missing password
- Missing username
- Recovery after an invalid attempt

Results:
- `LOGIN-N03` (Missing username): [View record](results/member-d.md)

### Equivalence Partitioning
Required coverage:
- Age below the accepted range
- Age within the accepted range
- Age above the accepted range

Results:
- `AGE-EP-10-B` (Age below range): [View record](results/member-d.md)

### Input-Format Observations
Required observations:
- Blank age
- Non-numeric age input

Results:
- See individual member results files.

### 2-Point Boundary Testing
Required values:
- 17, 18, 80, 81

Results:
- `AGE-2P-81-D` (Boundary value 81): [View record](results/member-d.md)

### 3-Point Boundary Testing
Required values:
- 16, 17, 18, 19, 79, 80, 81, 82

Results:
- `AGE-3P-79-C` (Boundary value 79): [View record](results/member-d.md)

---

## Member Contributions

### Member D
- Guided results: [View results](results/member-d.md)
- Self-designed tests: [View tests](exploratory/member-d.md)
- Reflection: [View reflection](reflections/member-d.md)
- Chosen investigation: SauceDemo login form input recovery after triggering a missing username validation error (EXP-D-01).
- Main observation: The web applications properly reject invalid inputs and allow smooth recovery without clearing valid form fields or throwing raw system errors.
- Pull request: Add member D manual testing work