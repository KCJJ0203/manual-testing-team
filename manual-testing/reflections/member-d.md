# Individual Reflection — Member D

1. **What makes a test positive or negative?**
   A positive test verifies that valid inputs produce expected successful outcomes, while a negative test verifies that invalid inputs are properly rejected with feedback.

2. **Why can a negative test pass?**
   A negative test passes when the system correctly detects invalid input and handles it safely, matching the expected rejection behavior.

3. **How did equivalence partitioning help you select data?**
   Equivalence partitioning helped group similar input values into valid and invalid classes, allowing me to pick representative samples without running redundant tests.

4. **What did boundary testing help you investigate?**
   Boundary testing allowed me to evaluate system behavior directly at the edge limits (such as minimum and maximum age values) where bugs are most likely to occur.

5. **What did you choose to test during the open-ended activity, and why?**
   I chose to test login recovery behavior after triggering a missing username error to verify if the password input persisted cleanly.

6. **Did your observations lead to follow-up tests?**
   Yes, observing standard error messages during recovery made me curious about how password fields handle incorrect passwords prior to correction.

7. **How does your Git history show your contribution?**
   My Git commit logs clearly show step-by-step progress under the `testing/member-d` branch, tracking my environment setup, result additions, screenshot uploads, and reflection file updates.