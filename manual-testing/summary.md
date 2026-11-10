# Team Summary

## Guided Testing Coverage

Baseline used for all form tests: `Alexander`, `TestingStudent`, age `30`, `Singapore`, `Manual testing classroom exercise` (see [team plan](team-plan.md#agreed-baseline-data)). The README first name `Alex` was rejected by the server as "Firstname too short", so the team changed it to `Alexander`.

Browsers used: Member A Microsoft Edge, Member B Google Chrome (macOS), Member C Firefox, Member D Google Chrome.

### Login Testing

Required coverage:
- Valid credentials.
- Incorrect password.
- Missing password.
- Missing username.
- Recovery after an invalid attempt.

Results:
- Valid credentials: `LOGIN-P01` (member-a), Pass. The Products page appeared with the product list. [View record](results/member-a.md#test-id-login-p01)
- Incorrect password: `LOGIN-N01` (member-b), Pass. Login rejected with "Username and password do not match any user in this service". [View record](results/member-b.md#test-id-login-n01)
- Missing password: `LOGIN-N02` (member-c), Pass. Login rejected with "Password is required". [View record](results/member-c.md#test-id-login-n02)
- Missing username: `LOGIN-N03` (member-d), Pass. Login rejected with "Username is required". [View record](results/member-d.md#test-id-login-n03)
- Recovery after an invalid attempt: `LOGIN-R01` (member-a), Pass. Wrong password rejected, then login worked after correcting only the password. [View record](results/member-a.md#test-id-login-r01)

### Equivalence Partitioning

Required coverage:
- Age below the accepted range.
- Age within the accepted range.
- Age above the accepted range.

Results:
- Below range: `AGE-EP-10-B` (member-b), age 10, Pass. Blocked by browser validation, "Value must be greater than or equal to 18". [View record](results/member-b.md#test-id-age-ep-10-b)
- Within range: `AGE-EP-30-A` (member-a), age 30, Pass. Server returned "Your Input passed validation" with age 30. [View record](results/member-a.md#test-id-age-ep-30-a)
- Above range: `AGE-EP-90-C` (member-c), age 90, Pass. Blocked by browser validation, "Please select a value that is no more than 80" (Firefox). [View record](results/member-c.md#test-id-age-ep-90-c)

Note: both rejections came from the browser, so the server's own age check was not reached.

### Input-Format Observations

Required observations:
- Blank age.
- Non-numeric age input.

Results:
- Blank age: `AGE-EP-BLANK` (member-d), Pass. Blocked by browser validation, "Please fill out this field". [View record](results/member-d.md#test-id-age-ep-blank)
- Non-numeric age: `AGE-EP-ABC` (member-d), Pass. Submission was blocked. [View record](results/member-d.md#test-id-age-ep-abc)

### 2-Point Boundary Testing

Required values:
17, 18, 80, 81.

Results:
- Age 17: `AGE-2P-17-A` (member-a), Negative, Pass. Blocked by browser validation, "Value must be greater than or equal to 18". [View record](results/member-a.md#test-id-age-2p-17-a)
- Age 18: `AGE-2P-18-B` (member-b), Positive, Pass. Server returned "Your Input passed validation" with age 18. [View record](results/member-b.md#test-id-age-2p-18-b)
- Age 80: `AGE-2P-80-C` (member-c), Positive, Pass. Form submitted and the results page showed age 80. [View record](results/member-c.md#test-id-age-2p-80-c)
- Age 81: `AGE-2P-81-D` (member-d), Negative, Pass. Blocked by browser validation, "Value must be less than or equal to 80". [View record](results/member-d.md#test-id-age-2p-81-d)

### 3-Point Boundary Testing

Required values:
16, 17, 18, 19, 79, 80, 81, 82.

Convention: ISTQB CTFL v4.0 eight-value set.

New executions:
- Age 16: `AGE-3P-16-A` (member-a), Negative, Pass. Blocked by browser validation, "Value must be greater than or equal to 18". [View record](results/member-a.md#test-id-age-3p-16-a)
- Age 19: `AGE-3P-19-B` (member-b), Positive, Pass. Server returned "Your Input passed validation" with age 19. [View record](results/member-b.md#test-id-age-3p-19-b)
- Age 79: `AGE-3P-79-C` (member-c), Positive, Pass. Form submitted and the results page showed age 79. [View record](results/member-c.md#test-id-age-3p-79-c)
- Age 82: `AGE-3P-82-D` (member-d), Negative, Pass. Blocked by browser validation, "Value must be less than or equal to 80". [View record](results/member-d.md#test-id-age-3p-82-d)

Reused from Activity 3 (counted once):
- Age 17: `AGE-2P-17-A` (member-a), reuse noted in [Member A's results](results/member-a.md).
- Age 18: `AGE-2P-18-B` (member-b).
- Age 80: `AGE-2P-80-C` (member-c).
- Age 81: `AGE-2P-81-D` (member-d).

Note: all eight values were covered. Every rejected age (16, 17, 81, 82, and 10 and 90 above) was stopped by the browser before reaching the server.

---

## Member Contributions

### Member A

- Guided results: [View results](results/member-a.md)
- Self-designed tests: [View tests](exploratory/member-a.md)
- Reflection: [View reflection](reflections/member-a.md)
- Chosen investigation: The shortest and longest first names the server accepts (OWN-A-01 to OWN-A-06), after the baseline `Alex` was rejected.
- Main observation: The server rejects first names under 5 characters (`Amy`, `Alex`, `Anna` rejected, `Alexa` accepted), while the published requirement gives no minimum and the page's own check allows 3 or more. The maximum works as published: 89 characters accepted, 90 blocked by the page. Recorded as a requirement question, not a confirmed defect.
- Pull request: https://github.com/KCJJ0203/manual-testing-team/pull/1

### Member B

- Guided results: [View results](results/member-b.md)
- Self-designed tests: [View tests](exploratory/member-b.md)
- Reflection: [View reflection](reflections/member-b.md)
- Chosen investigation: Recovery after an invalid age (OWN-B-01): submit age `10`, then change only the age to `18` and submit again without resetting the form.
- Main observation: The form kept the other values after age `10` was blocked, and the corrected submission with age `18` passed validation.
- Pull request: https://github.com/KCJJ0203/manual-testing-team/pull/2

### Member C

- Guided results: [View results](results/member-c.md)
- Self-designed tests: [View tests](exploratory/member-c.md)
- Reflection: [View reflection](reflections/member-c.md)
- Chosen investigation: Surname length boundaries at 10, 11, 79 and 80 characters (OWN-C-01 to OWN-C-04).
- Main observation: 11 and 79 characters were accepted and 10 and 80 were rejected, so "between 11 and 79" is inclusive. Surname errors show as red text on the page, while age errors use a browser bubble, so the two fields are checked in different ways.
- Pull request: https://github.com/KCJJ0203/manual-testing-team/pull/3

### Member D

- Guided results: [View results](results/member-d.md)
- Self-designed tests: [View tests](exploratory/member-d.md)
- Reflection: [View reflection](reflections/member-d.md)
- Chosen investigation: SauceDemo login recovery after a missing-username error (EXP-D-01).
- Main observation: The password stayed filled in after the "Username is required" error, and entering `standard_user` then logging in again went straight to the inventory page without a refresh.
- Pull request: https://github.com/KCJJ0203/manual-testing-team/pull/4 (later changes merged through https://github.com/KCJJ0203/manual-testing-team/pull/5 and https://github.com/KCJJ0203/manual-testing-team/pull/6)

---

## Team Conclusion

Equivalence partitioning let us test each age group with one value (10, 30, 90). The 2-point and 3-point boundary tests then checked the edges at 18 and 80, where an off-by-one bug would show. A negative test counts as a pass when the input gets rejected. All the rejected ages were blocked by the browser, so we still don't know if the server checks age on its own.

For the open-ended part, Member A looked into why `Alex` was rejected and found the server needs at least 5 characters for first name. Member C tested surname lengths and found 11 and 79 are both accepted. Members B and D tested recovery after an error (age on the form, missing username on SauceDemo) and the valid fields stayed filled in both cases.

Next, the team would investigate:
- The intended first-name minimum: the published "must be filled", the page check of 3, or the server's 5.
- Whether the server itself rejects out-of-range ages, long first names and bad surnames if the browser and page checks are bypassed.
- How the age field handles decimals such as `18.5`, which the requirements do not define.
- Recovery after an invalid value in another field, such as a short surname.
