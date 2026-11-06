# SauceDemo – Manual QA Test Cases

**Project:** SauceDemo Manual Testing  
**Application:** https://www.saucedemo.com/  
**Testing Type:** Manual Testing  
**Test Environment:** Windows 11, Google Chrome  
**Browser Version:** 156.0.8078.80  
**Device:** Desktop / PC  
**Execution Status:** In Progress

---

## 1. Test Accounts

All six predefined accounts use the password `secret_sauce`.

| Account | Purpose |
|---|---|
| `standard_user` | Standard application behaviour |
| `locked_out_user` | Verify locked-out account behaviour |
| `problem_user` | Identify account-specific UI and functionality issues |
| `performance_glitch_user` | Check behaviour under delayed performance |
| `error_user` | Identify account-specific errors |
| `visual_user` | Identify visual and product display issues |

## 2. Test Case Status Definitions

| Status | Meaning |
|---|---|
| Pass | Actual result matches expected result |
| Fail | Actual result differs from expected result |
| Pending Verification | Initial issue observed, but further verification is required |
| Not Executed | Test has not yet been performed |

---

# 3. Login Test Cases

## TC-001: Verify login with valid credentials

**Module:** Login  
**Priority:** High  
**Test Type:** Functional  
**Precondition:** User is on the SauceDemo login page.

**Test Data:** Valid account credentials.

**Steps:**
1. Open https://www.saucedemo.com/.
2. Enter a valid username.
3. Enter the password `secret_sauce`.
4. Click the Login button.
5. Verify the resulting page.

**Expected Result:** The user should successfully log in and be redirected to the inventory page.

| Account | Actual Result | Status |
|---|---|---|
| `standard_user` | Not Executed | Not Executed |
| `problem_user` | Not Executed | Not Executed |
| `performance_glitch_user` | Not Executed | Not Executed |
| `error_user` | Not Executed | Not Executed |
| `visual_user` | Not Executed | Not Executed |

**Remarks:** `locked_out_user` is covered separately in TC-004.

---

## TC-002: Verify login with invalid credentials

**Module:** Login  
**Priority:** High  
**Test Type:** Negative  
**Precondition:** User is on the login page.

**Test Data:**
- Username: `invalid_user`
- Password: `wrong_password`

**Steps:**
1. Open the login page.
2. Enter an invalid username.
3. Enter an incorrect password.
4. Click Login.

**Expected Result:** Login should fail, and an appropriate error message should be displayed.

**Actual Result:** Not Executed.

**Status:** Not Executed.

---

## TC-003: Verify login with empty credentials

**Module:** Login  
**Priority:** Medium  
**Test Type:** Negative  
**Precondition:** User is on the login page.

**Steps:**
1. Open the login page.
2. Leave the username field empty.
3. Leave the password field empty.
4. Click Login.

**Expected Result:** The application should prevent login and display a validation message indicating that the username is required.

**Actual Result:** Not Executed.

**Status:** Not Executed.

---

## TC-004: Verify login using a locked-out account

**Module:** Login  
**Priority:** High  
**Test Type:** Negative  
**Precondition:** User is on the login page.

**Test Data:**
- Username: `locked_out_user`
- Password: `secret_sauce`

**Steps:**
1. Open the login page.
2. Enter `locked_out_user`.
3. Enter `secret_sauce`.
4. Click Login.

**Expected Result:** Login should be prevented, and the application should display an appropriate locked-out account error message.

**Actual Result:** Not Executed.

**Status:** Not Executed.

---

# 4. Product Browsing Test Cases

## TC-005: Verify product listings on the inventory page

**Module:** Product Browsing  
**Priority:** High  
**Test Type:** Functional / UI  
**Precondition:** User is successfully logged in.

**Steps:**
1. Log in using a SauceDemo account.
2. Navigate to the inventory page.
3. Verify that the product listings are displayed.
4. Check product names, images, prices and descriptions.

**Expected Result:** Products should be displayed correctly with their corresponding names, images, descriptions and prices.

**Actual Result:** Not Executed as a complete listing verification.

**Status:** Not Executed.

**Remarks:** A specific product image issue was observed under `visual_user`. Refer to TC-007 and BUG-002.

---

## TC-006: Verify product detail page navigation

**Module:** Product Browsing  
**Priority:** Medium  
**Test Type:** Functional  
**Precondition:** User is logged in and the inventory page is displayed.

**Steps:**
1. Select a product from the inventory page.
2. Click the product name or image.
3. Verify that the product detail page opens.
4. Check the product name, description, image and price.
5. Navigate back to the inventory page.

**Expected Result:** The selected product's detail page should open and display the correct product information.

**Actual Result:** Not Executed.

**Status:** Not Executed.

---

## TC-007: Verify product images across user accounts

**Module:** Product Browsing  
**Priority:** High  
**Test Type:** UI / Visual  
**Precondition:** User is logged in.

**Steps:**
1. Log in using `visual_user`.
2. Navigate to the inventory page.
3. Locate the Sauce Labs Backpack.
4. Inspect the displayed product image.
5. Compare the image with the expected backpack product.

**Expected Result:** The Sauce Labs Backpack should display its correct product image.

**Actual Result:** The Sauce Labs Backpack displays a dog image instead of the correct backpack image when logged in using `visual_user`.

**Status:** Fail.

**Related Bug:** BUG-002 – Incorrect product image displayed for Backpack.

---

## TC-008: Verify product prices between inventory and cart pages

**Module:** Product Browsing / Shopping Cart  
**Priority:** High  
**Test Type:** Functional / Data Consistency  
**Precondition:** User is logged in and can access the inventory and cart pages.

**Steps:**
1. Log in using the relevant account.
2. Note the price of the Sauce Labs Backpack on the inventory page.
3. Add the Backpack to the cart.
4. Open the cart.
5. Compare the displayed price with the inventory page.
6. Repeat the comparison for the Sauce Labs Bike Light.

**Expected Result:** Product prices should remain consistent between the inventory page and the cart.

**Actual Result:**
- Under `visual_user`, the Backpack displayed a price of **$93.30** on the inventory page and **$29.99** in the cart.
- The Bike Light price was observed as **$9.99** under `standard_user` and **$42.06** under `visual_user`.

**Status:** Pending Verification.

**Related Bugs:**
- BUG-003 – Backpack price discrepancy.
- BUG-004 – Bike Light price discrepancy.

**Remarks:** Further verification is required before treating these price discrepancies as fully confirmed defects.

---

## TC-009: Verify behaviour when accessing an invalid product ID

**Module:** Product Browsing  
**Priority:** High  
**Test Type:** Negative / Edge Case  
**Precondition:** User is logged in.

**Test Data:** Product ID `6`.

**Steps:**
1. Log in using `standard_user`.
2. Open the following URL directly:

   `https://www.saucedemo.com/inventory-item.html?id=6`

3. Observe the displayed product information.
4. Click Add to Cart.
5. Check the cart badge.
6. Open the cart and verify whether the product is present.

**Expected Result:** The application should handle an invalid product ID gracefully. An invalid product should not be added to the cart or affect the cart count.

**Actual Result:**
- The page displayed `ITEM NOT FOUND`.
- The product price appeared as `$√-1`.
- Clicking Add to Cart increased the cart badge.
- However, the invalid product did not appear in the cart.

**Status:** Fail.

**Related Bug:** BUG-001 – Invalid product ID causes inconsistent cart badge behaviour.

---

# 5. Shopping Cart Test Cases

## TC-010: Verify adding a product to the shopping cart

**Module:** Shopping Cart  
**Priority:** High  
**Test Type:** Functional  
**Precondition:** User is logged in and the inventory page is displayed.

**Steps:**
1. Select a product.
2. Click Add to Cart.
3. Observe the cart badge.
4. Open the shopping cart.
5. Verify that the selected product is displayed.

**Expected Result:** The selected product should be added to the cart, and the cart badge should reflect the correct item count.

**Actual Result:** Not Executed as a complete test case.

**Status:** Not Executed.

---

## TC-011: Verify removing a product from the shopping cart

**Module:** Shopping Cart  
**Priority:** Medium  
**Test Type:** Functional  
**Precondition:** User is logged in and at least one product is present in the cart.

**Steps:**
1. Open the shopping cart.
2. Select a product.
3. Click Remove.
4. Verify that the product is removed.
5. Check the cart badge.

**Expected Result:** The selected product should be removed from the cart, and the cart badge should update accordingly.

**Actual Result:** Not Executed.

**Status:** Not Executed.

---

## TC-012: Verify cart contents after navigating between pages

**Module:** Shopping Cart  
**Priority:** Medium  
**Test Type:** Functional  
**Precondition:** User is logged in.

**Steps:**
1. Add a product to the cart.
2. Navigate to the product detail page.
3. Return to the inventory page.
4. Open the shopping cart.
5. Verify that the previously added product is still present.

**Expected Result:** Cart contents should remain unchanged while navigating between application pages.

**Actual Result:** Not Executed.

**Status:** Not Executed.

---

## TC-013: Verify cart isolation between different user accounts

**Module:** Shopping Cart  
**Priority:** High  
**Test Type:** Functional / Session Handling / Edge Case  
**Precondition:** Google Chrome is open with the SauceDemo application.

**Steps:**
1. Open SauceDemo in one browser tab.
2. Log in using one SauceDemo account.
3. Add a product to the shopping cart.
4. Open SauceDemo in another tab using the same Chrome profile.
5. Log in using a different SauceDemo account.
6. Inspect the shopping cart in both tabs.
7. Compare the cart contents and displayed values.

**Expected Result:** Different SauceDemo accounts should maintain separate shopping cart data. One user's cart should not display another user's cart contents.

**Actual Result:** When different SauceDemo accounts were used in separate tabs under the same Chrome profile, the cart contents and displayed value appeared to be shared.

**Status:** Fail.

**Related Bug:** BUG-008 – Shopping cart data appears shared across different SauceDemo accounts in separate tabs.

**Remarks:** The observation was made using separate tabs, different SauceDemo usernames and the same Chrome profile.

---

# 6. Checkout Test Cases

## TC-014: Verify navigation to the checkout information page

**Module:** Checkout  
**Priority:** High  
**Test Type:** Functional  
**Precondition:** User is logged in and has at least one product in the cart.

**Steps:**
1. Open the shopping cart.
2. Verify that the selected product is present.
3. Click Checkout.
4. Observe the resulting page.

**Expected Result:** The application should navigate to the checkout information page and display the required customer information fields.

**Actual Result:** Not Executed.

**Status:** Not Executed.

---

## TC-015: Verify checkout form validation with empty fields

**Module:** Checkout  
**Priority:** High  
**Test Type:** Negative  
**Precondition:** User is logged in, has a product in the cart and is on the checkout information page.

**Steps:**
1. Leave First Name empty.
2. Leave Last Name empty.
3. Leave Postal Code empty.
4. Click Continue.

**Expected Result:** The application should prevent the user from proceeding and display an appropriate validation message.

**Actual Result:** Not Executed.

**Status:** Not Executed.

---

## TC-016: Verify validation of customer information fields

**Module:** Checkout  
**Priority:** High  
**Test Type:** Functional / Negative  
**Precondition:** User is logged in and is on the checkout information page.

**Steps:**
1. Enter a value in the First Name field.
2. Enter a value in the Last Name field.
3. Enter a value in the Postal Code field.
4. Attempt to edit or paste text into the Last Name field.
5. Observe the field behaviour.
6. Repeat the check using the relevant user accounts.

**Expected Result:** All customer information fields should accept valid input and allow the user to proceed when the required information is entered.

**Actual Result:**
- Under `problem_user`, the Last Name field rejected input.
- The Last Name field behaviour differed when using `error_user`.

**Status:** Fail.

**Related Bug:** BUG-007 – Last Name field rejects input and behaves differently between accounts.

**Remarks:** The account-specific behaviour was observed. Refer to the supporting evidence for the exact differences.

---

## TC-017: Verify direct access to the checkout overview page

**Module:** Checkout  
**Priority:** High  
**Test Type:** Negative / Security-Related Validation  
**Precondition:** User is logged in using `standard_user`.

**Steps:**
1. Log in using `standard_user`.
2. Add a product to the cart.
3. Without completing the checkout information form, directly navigate to:

   `https://www.saucedemo.com/checkout-step-two.html`

4. Observe whether the checkout overview page is accessible.
5. Check whether the user can proceed with checkout.

**Expected Result:** The application should prevent users from bypassing the required checkout information step.

**Actual Result:** The checkout overview page was accessible through direct navigation, bypassing the customer information form. The order could be completed without submitting the required customer information.

**Status:** Fail.

**Related Bug:** BUG-006 – Direct navigation bypasses required checkout information.

---

## TC-018: Verify order summary and price calculations

**Module:** Checkout  
**Priority:** High  
**Test Type:** Functional / Data Validation  
**Precondition:** User has added products to the cart and reached the checkout overview page.

**Steps:**
1. Proceed through the checkout information page.
2. Reach the checkout overview page.
3. Verify the listed products.
4. Check individual product prices.
5. Verify item total, tax and final total.
6. Compare the checkout values with the cart.

**Expected Result:** Product prices and order calculations should be accurate and consistent across the cart and checkout pages.

**Actual Result:** Not Executed as a complete checkout calculation test.

**Status:** Not Executed.

**Remarks:** Price discrepancies observed during earlier testing are documented separately in TC-008.

---

## TC-019: Verify successful order completion

**Module:** Checkout  
**Priority:** High  
**Test Type:** Functional  
**Precondition:** User is logged in, has a product in the cart and has completed the required checkout information.

**Steps:**
1. Add a product to the cart.
2. Open the cart.
3. Click Checkout.
4. Enter valid customer information.
5. Click Continue.
6. Review the order summary.
7. Click Finish.
8. Observe the confirmation page.

**Expected Result:** The order should be completed successfully, and the application should display an order confirmation message.

**Actual Result:** Not Executed as a complete successful-order test.

**Status:** Not Executed.

---

## TC-020: Verify order completion using the error_user account

**Module:** Checkout  
**Priority:** High  
**Test Type:** Functional / Negative  
**Precondition:** User is logged in using `error_user`, has a product in the cart and has reached the checkout overview page.

**Steps:**
1. Log in using `error_user`.
2. Add a product to the cart.
3. Proceed to checkout.
4. Enter the required customer information.
5. Continue to the checkout overview page.
6. Click Finish.
7. Observe the application behaviour.

**Expected Result:** The order should be completed successfully, and the order confirmation page should be displayed.

**Actual Result:** Clicking Finish caused a JavaScript error:

`Uncaught TypeError: wa.cesetRart is not a function`

The expected order confirmation was not reached.

**Status:** Fail.

**Related Bug:** BUG-005 – Finish button fails with a JavaScript TypeError for `error_user`.

---

# 7. Test Execution Summary

Update this section after completing the remaining tests.

| Metric | Count |
|---|---:|
| Total Test Cases | 20 |
| Passed | 0 |
| Failed | 8 |
| Pending Verification | 1 |
| Not Executed | 11 |

**Note:** The counts above reflect the current documented execution information. Update them if further testing changes a test case's status.

# 8. Notes

- Testing was performed manually using Google Chrome on Windows 11.
- Account-specific behaviour was considered during testing.
- Bug IDs in this document correspond to the separate bug reports in the `Bug-Reports` folder.
- Screenshots and recordings should be stored in the corresponding folders inside `Evidence`.
- Test cases marked `Not Executed` must not be treated as passed or failed until they are actually performed.
- Test cases marked `Pending Verification` require additional checks before the related issue is considered fully confirmed.

