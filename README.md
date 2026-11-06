# SauceDemo – Manual QA Testing

## Project Overview

This repository contains the documentation and findings from a manual QA testing exercise performed on [SauceDemo](https://www.saucedemo.com/), a sample e-commerce web application.

The objective of this project is to evaluate the application's functionality, identify defects, document reproducible issues, and assess the overall user experience through structured manual testing.

This project follows the **Pure QA** approach, focusing on manual testing rather than test automation.

## Application Under Test

- **Application:** SauceDemo
- **URL:** https://www.saucedemo.com/
- **Testing Approach:** Manual Testing
- **Testing Type:** Functional, UI, Negative, and Edge Case Testing

## Test Environment

| Parameter | Details |
|---|---|
| Operating System | Windows 11 |
| Browser | Google Chrome |
| Browser Version | 156.0.8078.80 |
| Device | Desktop |
| Testing Method | Manual Testing |

## Testing Scope

The testing activities cover the following application modules:

- **Login:** Authentication, invalid credentials, and account-specific behaviour.
- **Product Browsing:** Product listings, product details, images, and pricing.
- **Shopping Cart:** Adding and removing products, cart contents, and price consistency.
- **Checkout:** Customer information validation, checkout navigation, and order completion.

## Testing Activities

The following testing activities are included:

- Functional Testing
- UI Testing
- Negative Testing
- Boundary and Edge Case Testing
- Session and Cart Behaviour Testing
- Cross-Browser Testing Considerations
- Defect Identification and Reporting

## Test Accounts

The following predefined SauceDemo accounts are used during testing:

| Username | Purpose |
|---|---|
| `standard_user` | Standard application behaviour |
| `locked_out_user` | Login restriction testing |
| `problem_user` | Account-specific behaviour testing |
| `performance_glitch_user` | Performance-related behaviour testing |
| `error_user` | error-related behaviour testing |
| `Visual_user` | Visual-related behaviour testing |

## Repository Structure

```text
SauceDemo-Manual-QA/
│
├── README.md
│
├── Test-Plan/
│   └── Test-Plan.md
│
├── Test-Cases/
│   └── Test-Cases.md
│
├── Bug-Reports/
│   ├── BUG-001.md
│   ├── BUG-002.md
│   └── ...
│
├── Evidence/
│   ├── BUG-001/
│   ├── BUG-002/
│   └── ...
│
└── Test-Execution/
    └── Execution-Summary.md
```

## Documentation

The repository contains the following QA deliverables:

| Document | Description |
|---|---|
| Test Plan | Defines testing objectives, scope, approach, environment, and risks. |
| Test Cases | Contains documented test scenarios, steps, and expected results. |
| Bug Reports | Records identified defects with reproduction steps and supporting evidence. |
| Evidence | Contains screenshots and recordings supporting the reported findings. |
| Execution Summary | Summarises the test execution results. |

## Defect Reporting

Identified defects are documented individually with relevant details, including:

- Bug ID and title
- Application module
- Preconditions
- Steps to reproduce
- Expected result
- Actual result
- Severity and priority
- Supporting screenshots or recordings

## Testing Approach

Testing is performed manually by interacting with the application through the browser.

The approach focuses on validating expected application behaviour, exploring unusual scenarios, checking account-specific behaviour, and identifying inconsistencies that could affect users.

No automation framework or automated test scripts are included, as this project follows the Pure QA assignment track.

## Project Status

**Status:** [In Progress / Completed]

The documentation and test findings will be updated as testing and verification activities are completed.

---

*This repository was created as part of a manual QA testing assignment.*
