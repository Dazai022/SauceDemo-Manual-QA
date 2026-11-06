# Test Plan – SauceDemo Manual QA

## 1. Project Overview

This document outlines the test strategy and approach for manually testing the SauceDemo web application.

The purpose of this testing exercise is to evaluate the application's core functionality, identify defects, verify expected behaviour, and assess the overall user experience.

The testing focuses on four major modules: Login, Product Browsing, Shopping Cart, and Checkout.

This project follows the **Pure QA** track, with emphasis on manual testing, exploratory testing, test documentation, and defect reporting.

**Application URL:** https://www.saucedemo.com/

## 2. Testing Objectives

The primary objectives of this testing exercise are:

- Verify that users can log in using valid credentials and receive appropriate feedback for invalid login attempts.
- Validate product listings, product details, images, and pricing information.
- Verify shopping cart operations, including adding and removing products.
- Validate checkout workflows and customer information fields.
- Identify functional inconsistencies, UI defects, and unexpected application behaviour.
- Explore negative scenarios and edge cases that may not be covered by standard user flows.
- Document identified defects with clear reproduction steps and supporting evidence.

## 3. Scope of Testing

### 3.1 In Scope

The following application modules are included in the testing scope.

**A. Login Module**
- Login with valid credentials.
- Login with invalid credentials.
- Login with empty fields.
- Login behaviour for locked-out users.
- Account-specific login behaviour and error messages.

**B. Product Browsing Module**
- Verify product listing and product information.
- Validate product names, descriptions, images, and prices.
- Open individual product detail pages.
- Verify navigation between the inventory and product detail pages.
- Check product-specific behaviour across different test accounts.

**C. Shopping Cart Module**
- Add products to the cart.
- Remove products from the cart.
- Verify cart badge updates.
- Validate cart contents and product information.
- Verify cart behaviour when navigating between pages.
- Check for inconsistencies in cart contents and pricing.

**D. Checkout Module**
- Verify checkout navigation.
- Validate customer information fields.
- Test mandatory field validation.
- Verify checkout overview details.
- Validate item totals and pricing information.
- Complete an order and verify the confirmation page.
- Explore direct navigation and invalid checkout flows.

### 3.2 Out of Scope

The following areas are outside the scope of this manual testing exercise:

- Backend API testing.
- Database-level validation.
- Source code review.
- Security penetration testing.
- Load and stress testing.
- Automated test framework development.
- Third-party payment gateway testing.

## 4. Testing Approach

Testing will be performed manually using the application's browser interface.

The testing approach includes:

**Functional Testing**

Verify that application features work according to their expected behaviour, including login, product selection, cart operations, and checkout.

**UI Testing**

Check the visual presentation and consistency of interface elements such as product images, buttons, labels, input fields, and displayed prices.

**Negative Testing**

Provide invalid, incomplete, or unexpected inputs to verify that the application handles them appropriately.

**Edge Case Testing**

Explore unusual scenarios such as invalid product identifiers, direct navigation to checkout pages, and unexpected cart behaviour.

**Exploratory Testing**

Navigate through the application beyond standard test scenarios to identify unexpected behaviour and defects that may not be immediately apparent.

**Cross-Browser Considerations**

Consider browser compatibility and consistency across commonly used browsers. Detailed cross-browser execution will be documented only if performed.

## 5. Test Environment

Testing is conducted using the following environment:

| Parameter | Details |
|---|---|
| Application | SauceDemo |
| Application URL | https://www.saucedemo.com/ |
| Operating System | Windows 11 |
| Browser | Google Chrome |
| Browser Version | 156.0.8078.80 |
| Device | Desktop / PC |
| Testing Type | Manual Testing |
| Testing Approach | Functional and Exploratory Testing |

## 6. Test Data

The following six predefined test accounts provided by SauceDemo are included in the testing scope.

| Username | Intended Testing Purpose |
|---|---|
| `standard_user` | Verify standard application functionality and expected user workflows. |
| `locked_out_user` | Verify login restrictions and appropriate error handling for locked accounts. |
| `problem_user` | Explore account-specific functional and UI inconsistencies. |
| `performance_glitch_user` | Observe application behaviour under performance delays. |
| `error_user` | Investigate application errors and unexpected behaviour during user workflows. |
| `visual_user` | Identify visual defects, including incorrect images, layout inconsistencies, and UI issues. |

**Common Password:** `secret_sauce`

All six predefined accounts use the common password provided by SauceDemo.

**Note:** Each account is used to investigate its respective behaviour. Account-specific observations are documented separately in the relevant test cases and bug reports.

## 7. Entry Criteria

Testing can begin when:

- The SauceDemo application is accessible.
- The test environment and browser are ready.
- Valid test credentials are available.
- The application is sufficiently accessible to execute the planned test scenarios.

## 8. Exit Criteria

Testing can be considered complete when:

- All planned test scenarios have been executed or their execution status documented.
- Identified defects have been recorded with reproduction steps.
- Relevant screenshots and recordings have been collected.
- Critical observations and unresolved issues have been documented.
- The test execution summary has been updated.

## 9. Risk Assessment

| Risk | Potential Impact | Mitigation |
|---|---|---|
| Account-specific application behaviour | Different accounts may produce inconsistent results | Verify observations across relevant accounts |
| Performance delays | Test execution may be affected by slow responses | Allow sufficient time and record observed delays |
| Browser-specific behaviour | UI or functional differences may occur | Record browser and version; consider additional browsers |
| Session or cart inconsistencies | Incorrect cart state may affect checkout | Verify cart behaviour across navigation and sessions |
| Incomplete test coverage | Some defects may remain unidentified | Include negative, exploratory, and edge case testing |
| Intermittent defects | Issues may not reproduce consistently | Repeat the scenario and preserve evidence |

## 10. Defect Reporting Process

Every identified defect will be documented individually.

Each defect report will include:

- Bug ID
- Bug title
- Application module
- Test environment
- Test account used
- Preconditions
- Steps to reproduce
- Expected result
- Actual result
- Severity
- Priority
- Supporting screenshots or recordings
- Current status

Defects will be assigned unique identifiers (BUG-001, BUG-002, etc.) to maintain traceability.

## 11. Deliverables

The following deliverables are included in this project:

1. Test Plan – Testing objectives, scope, approach, environment, and risks.
2. Test Cases – Documented test scenarios with steps and expected results.
3. Bug Reports – Individual reports for identified application defects.
4. Evidence – Screenshots and recordings supporting reported defects.
5. Test Execution Summary – Summary of executed scenarios and their results.
6. Demonstration Videos – Walkthrough of the testing approach and selected defect reproductions.

## 12. Conclusion

This test plan establishes a structured approach for evaluating the SauceDemo application through manual testing.

The focus is on validating core user workflows, exploring unexpected application behaviour, identifying defects, and maintaining clear documentation supported by reproducible evidence.

The findings from this exercise will help demonstrate practical QA skills, analytical thinking, and the ability to communicate software defects effectively.

---

**Document:** SauceDemo Manual QA – Test Plan  
**Testing Track:** Pure QA  
**Testing Method:** Manual Testing  
**Status:** In Progress
