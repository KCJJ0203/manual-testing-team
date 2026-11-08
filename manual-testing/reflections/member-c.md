# Individual Reflection - Member C

## What makes a test positive or negative?

A positive test uses valid input and checks that the system accepts it,
like age 80 or an 11-character surname. A negative test uses invalid input
and checks that the system rejects it, like a missing password or age 90.

## Why can a negative test pass?

A negative test passes when the system correctly rejects the bad input.
For example, LOGIN-N02 passed because the login was blocked and an error
message appeared when the password was empty.

## How did equivalence partitioning help you select data?

It split age into three groups (below 18, 18 to 80, above 80), so I only
needed one value from each group. I tested 90 to represent the above-80
group instead of trying many random values.

## What did boundary testing help you investigate?

It helped me check the exact edges where the rules change, like 79 and 80
for age. These are the values most likely to break if the code uses the
wrong comparison, such as > instead of >=.

## What did you choose to test during the open-ended activity, and why?

I tested surname length at 10, 11, 79, and 80 characters. The requirement
said "between 11 and 79" but did not say if 11 and 79 were included, so I
wanted to find out.

## Did your observations lead to follow-up tests?

My tests showed that surname used red text on the page while age used a
browser bubble. This made me want to check if the server also rejects bad
surnames, or if only the page does.

## How does your Git history show your contribution?

My commits show each step of my work in order: preparing my test record,
recording my login, equivalence partitioning, and boundary results, and
then planning and running my own surname tests.
