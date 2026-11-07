# Test Plan: SauceDemo

## Introduction
I tested SauceDemo.com as an internship assignment to demonstrate manual testing skills and the ability to find bugs without automation tools.

## Scope
**In scope:** Login, sorting functions, cart functions, product pricing and imagining, checkout overview, 

**Out of scope:** mobile testing, other browsers

## Types of testing
- Functional
- UI / Visual
- Negative
- Edge cases

Cross-browser testing was not covered. Only Chrome was used.

## Test environment
- OS: Windows 11
- Browser: Google Chrome 156.0.8078.80
- Device: laptop only

## Test data
Password for all accounts: `secret_sauce`

| Username | Expected behaviour |
|---|---|
| standard_user | every function to be working as per how standard user acc would work |
| locked_out_user | no access to the acc |
| problem_user | will have multiple problems and cant checkout easily |
| performance_glitch_user | there would be a lag or a delay in browser while performing activities |
| error_user | multiple errors |
| visual_user | visually different acc |

## Approach
Manual inspection of every element and each account. I have used multiple chrome browsers to access each account individually and check for any bugs or functionality issues throughout the page and all the bugs i've found are documented properly

## Test cases

| ID | Title | Preconditions | Steps | Expected result | Actual result | Status | Bug ID |
|---|---|---|---|---|---|---|---|
| TC-01 |verify login with valid credentials |you need to know valid username and password |open the website and enter credentials |login successful |login successful |pass |none |
| TC-02 |verify login with invalid credentials |username or password any one should be incorrect |same procedure as TC-01 | login failed with error message | login failed with error message |pass | none|
| TC-03 |verify login with no credentials or empty  |you should ignore either password or username |same as TC-01 |login failed with error  |login failed with error |pass |none |
| TC-04 |verify login for locked out user |enter username and password for locked out user |same as TC-01 |login failed account is locked |login failed account is locked |pass |none |
| TC-05 |verify product listing accross all accounts |username and password for all accounts |login with the credentials given and check |displays all products listed in the inventory with prices and product id's | displays all pdroducts with price but some acc show a different image and price | pass |BUG-008, BUG-010|
| TC-06 |verify product pricing accross all accounts |you need to know valid username and password |login to each account and cross verify the prices |all prices should be the same |price difference is observed |fail |BUG-010|
| TC-07 |verify product images accross all accounts |you need to know valid username and password |login to each account and cross verify the images |all images should be the same |different images are observed in a few accounts |fail |BUG-008|
| TC-08 |Verify behaviour when accessing an invalid product ID |you need to know valid username and password |login to each account and cross verify product id change it to anything more than 5 |it should show invalid and redirect back to inventory |lets you add a product to cart whose value is invalid |fail |BUG-001|
| TC-09 |Verify sorting function accross all accounts |you need to know valid username and password |login to each account and cross verify the sort dropdown button if it lets your sort or not |the sorting function should sort based on what option user chooses |the sorting function does not work for few accounts |fail |BUG-007|

## Risk Assessment

| Area | Why it might fail | Likelihood | Impact | Related Bugs |
|---|---|---|---|---|
| Product ID Validation | Invalid product IDs may not be handled correctly, causing the cart badge to increase even though the product is not added to the cart. | High | Medium | BUG-001 |
| Checkout Navigation | Users may access the checkout overview page directly without completing the customer information step. | Medium | High | BUG-002 |
| Add to Cart Functionality | The Add to Cart button may fail for Bolt T-Shirt, Fleece Jacket, and Test.allTheThings() T-Shirt (Red). | Medium | High | BUG-003 |
| Cart Item Removal | The Remove button on the inventory page may fail to remove the selected product from the cart. | Medium | Medium | BUG-004 |
| Order Completion | Clicking the Finish button may trigger a JavaScript error and prevent order completion. | High | High | BUG-005 |
| Checkout Form Validation | The Last Name field may reject valid user input, preventing users from proceeding with checkout. | High | Medium | BUG-006 |
| Product Sorting | Product sorting options may fail or produce unexpected results. | Medium | Medium | BUG-007 |
| Product Image Display | The same incorrect dog image may be displayed for multiple products. | Medium | Medium | BUG-008 |
| Application Performance | Login and page-loading operations may experience significant delays for certain user accounts. | Medium | High | BUG-009 |
| Product Price Consistency | The same product may display different prices across pages or user accounts. | Medium | High | BUG-010 |
