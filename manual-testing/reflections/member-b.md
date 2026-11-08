# Reflection — Member B

1. **What makes a test positive or negative?** A positive test uses valid input and checks that the application accepts it. A negative test uses invalid input and checks that the application rejects it appropriately.

2. **Why can a negative test pass?** A negative test passes when the invalid input is handled as expected. My incorrect-password login and age `10` tests passed because both attempts were rejected.

3. **How did equivalence partitioning help you select data?** It divided ages into below 18, 18–80, and above 80. I tested age `10` as a representative of the below-minimum group while the other fields stayed valid.

4. **What did boundary testing help you investigate?** It checked the edge of the valid age range. Age `18` was accepted at the minimum, and age `19` was accepted immediately above it.

5. **What did you choose to test during the open-ended activity, and why?** I tested a recovery sequence that starts with invalid age `10` and then corrects it to `18` without resetting the form. This checked whether a user can recover from validation feedback without re-entering the other fields.

6. **Did your observations lead to follow-up tests?** The separate age `10` rejection and age `18` acceptance led to the recovery sequence. The successful recovery suggests checking whether correcting a different invalid field, such as a short surname, works the same way.

7. **How does your Git history show your contribution?** My work is on the `testing/member-b` branch and includes my guided results, an executed self-designed test, and this reflection. I still need to commit and push the changes so the repository history shows those steps.
