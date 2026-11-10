# Self-Designed Testing — Member D

## Testing Idea

After SauceDemo blocks login due to a missing username, enter the valid username `standard_user` and click **Login** again without clearing or re-entering the password field.

## Reason

The guided tests showed that leaving the username empty (`LOGIN-N03`) is blocked. This exploratory test checks whether the SauceDemo login form recovers correctly from validation errors without losing existing field inputs (password) or locking the form state.

## Test Basis

Standard web application behavior assumes that fixing a missing input field allows immediate authentication recovery without requiring the user to refresh the page or clear valid entries.

## Approach

Start with an empty username field and enter `secret_sauce` into the Password field. Attempt submission to trigger the missing username error, then enter `standard_user` into the Username field without touching the Password field and attempt submission again.

## Test Cases

### Test ID: EXP-D-01

| Item | Details |
|---|---|
| Test type | Recovery |
| Tester | member-d |
| Status | Pass |

#### Purpose

Check whether entering a missing username allows successful login recovery without resetting the password field.

#### Preconditions

The SauceDemo login page (`https://www.saucedemo.com/`) is open and all fields are cleared.

#### Test Data

| Field | Value |
|---|---|
| Username, first attempt | *Empty* |
| Password | `secret_sauce` |
| Username, corrected attempt | `standard_user` |

#### Steps

1. Open the SauceDemo login page.
2. Leave the Username field empty.
3. Enter `secret_sauce` into the Password field.
4. Click **Login** and note the error feedback.
5. Without refreshing or clearing the Password field, enter `standard_user` into the Username field.
6. Click **Login** again.
7. Note whether the application redirects to the inventory page (`/inventory.html`).

#### Expected Result

The first attempt is rejected with "Epic sadface: Username is required". After entering `standard_user`, the second attempt succeeds and redirects to the inventory page.

#### Actual Result

The first submission was blocked with the red error banner "Epic sadface: Username is required". The password field retained its hidden value. Entering `standard_user` and clicking Login immediately authenticated the session and redirected to the inventory page.

#### Evidence

[View Evidence](../evidence/member-d/EXP-D-01_LoginRecovery_Pass.png)

---

## Overall Observations

The SauceDemo login form recovers cleanly after validation failure. The form maintained the entered password state after throwing the missing username error, allowing immediate recovery and authentication once the missing username was providxed.

Member D verified this flow on Google Chrome on Windows 11 and confirmed that no manual page refresh or password re-entry was required.