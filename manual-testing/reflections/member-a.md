# Reflection — Member A

## 1. What makes a test positive or negative?

A positive test uses valid input and expects it to be accepted, like the correct login in LOGIN-P01. A negative test uses invalid input and expects it to be rejected, like age 17 in AGE-2P-17-A.

## 2. Why can a negative test pass?

A negative test passes when the system rejects the invalid input as intended, because the rejection is the expected result and shows the restriction works. For example, in AGE-2P-17-A, age 17 was rejected, so the negative test passed.

## 3. How did equivalence partitioning help you select data?

Any value inside the same partition should behave the same, so one representative is enough to test the whole group. Age 30 stood in for the whole 18 to 80 range, so we did not need to test every age.

## 4. What did boundary testing help you investigate?

It helped me find exactly where the limit is. For a minimum age of 18, testing 17, 18 and 19 shows whether 17 (below) is rejected, 18 (equal to the limit) is accepted, and 19 (above) is accepted. This catches off-by-one mistakes, such as code using `age > 18` instead of `age >= 18`, which testing a middle value like 30 would miss. My own boundary tests (16 and 17) were blocked by the browser before reaching the server, so they do not show whether the server checks the limit too.

## 5. What did you choose to test during the open-ended activity, and why?

I tested how long a first name has to be for the server to accept it. I chose this because the baseline first name `Alex` was rejected as too short, even though the published requirement does not set a minimum length, so I wanted to find the real limit.

## 6. Did your observations lead to follow-up tests?

Yes. After `Amy` (3 characters) was rejected and `Alexa` (5 characters) was accepted, I wanted to find the exact limit, so I tested another 4-character name, `Anna`. It was also rejected, which confirmed the server needs at least 5 characters.

## 7. How does your Git history show your contribution?

I worked on my own branch, `testing/member-a`, with a commit for each step: preparing my test record, designing the login tests before running them, then recording the results of each activity. My work was combined into `main` through a pull request, so the history shows what I did and in what order.
