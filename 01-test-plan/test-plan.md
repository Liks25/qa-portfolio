# Test Plan: Automation Exercise (UI) & Restful-Booker (API)

| Field | Detail |
|---|---|
| Document version | 1.0 |
| Author | Likhona |
| Date | 2026-10-05 |
| Status | Draft |

---

## 1. Introduction

This document describes the approach for testing two practice applications: **Automation Exercise**, an e-commerce web application, and **Restful-Booker**, a booking REST API. The goal is to verify that core user flows and API endpoints behave as expected, to find and document defects, and to report on overall quality.

## 2. Applications Under Test

| Application | Type | URL |
|---|---|---|
| Automation Exercise | Web UI | https://automationexercise.com |
| Restful-Booker | REST API | https://restful-booker.herokuapp.com |

Both sites are built for software testing practice.

## 3. Scope

### In scope: Automation Exercise (UI)
- User registration and account creation
- Login and logout
- Product search
- Product listing and product detail pages
- Shopping cart (add, update, remove)
- Contact Us form (including file upload)
- Site navigation (menu, footer, logo, back button)
- Input validation and negative scenarios on all forms

### In scope: Restful-Booker (API)
- Authentication (`POST /auth`)
- Retrieve bookings (`GET /booking`, `GET /booking/{id}`)
- Create booking (`POST /booking`)
- Update booking (`PUT /booking/{id}`)
- Delete booking (`DELETE /booking/{id}`)
- Status codes, response structure, and error handling

### Out of scope
- Performance, load, and stress testing
- Payment processing and checkout payment details
- Mobile applications and mobile browsers
- Automated UI test scripts
- Penetration testing or any security testing beyond basic input checks

## 4. Objectives

1. Verify that the core user flows of Automation Exercise work as expected.
2. Verify that input validation handles valid, invalid, and boundary data correctly.
3. Verify that each Restful-Booker endpoint returns correct status codes and response bodies.
4. Identify, document, and classify defects with clear steps to reproduce and evidence.
5. Produce a Test Summary Report with an honest assessment of quality.

## 5. Test Environment

| Item | Detail |
|---|---|
| Operating system | Windows 11 |
| Primary browser | Mozilla Firefox, version: *156.0.1 (64-bit)* |
| Screen resolution | *1366 x 768* |
| API tool | Postman, version: *1.54.1* |
| Network | Home broadband |
| Test execution period | *05 OCT 2026* to *07 OCT 2026* |
| Test data | See section 9 |

## 6. Testing Types

| Type | Description |
|---|---|
| Functional testing | Verifying each feature works against expected behaviour |
| Positive testing | Valid inputs produce the expected outcome |
| Negative testing | Invalid inputs and unexpected actions are handled gracefully |
| Boundary value testing | Behaviour at limits (empty, minimum, maximum length) |
| UI / usability testing | Layout, labels, messages, and navigation are clear and consistent |
| Compatibility testing | Basic checks of key flows in a second browser |
| API testing | Status codes, response structure, headers, and error handling in Postman |
| Regression testing | Re-testing fixed or related areas where applicable |
| Exploratory testing | Unscripted exploration to uncover issues not covered by test cases |

## 7. Entry Criteria

Testing can begin when:
- Both applications are accessible.
- The test plan is reviewed and saved in the repository.
- Test cases are written for the modules being tested.
- Test data is prepared.
- Tools (Firefox, Postman, VS Code, Git) are installed and working.

## 8. Exit Criteria

Testing is complete when:
- All planned test cases have been executed, with each marked Pass, Fail, or Blocked.
- All failed tests have a documented bug report with evidence.
- All Critical and High severity bugs have been reported.
- The Postman collection has been run and exported.
- The Test Summary Report is complete.

## 9. Test Data

| Data type | Examples |
|---|---|
| Valid email | A dedicated test email address created for this project |
| Valid password | A password you create for the test account (do not reuse a real password) |
| Invalid emails | `abc`, `abc@`, `@test.com`, `abc@test`, empty |
| Boundary inputs | Empty, 1 character, very long string (255+ characters) |
| Special characters | `!@#$%^&*()`, `<script>alert(1)</script>`, `' OR 1=1 --` |
| Whitespace | Leading and trailing spaces |
| Files for upload | A small `.txt`, a small `.jpg`, and a large file |

**Important:** use only fake or dedicated test data. Never enter real personal or payment details into the applications.

## 10. Test Deliverables

| Deliverable | Location |
|---|---|
| Test plan | `01-test-plan/test-plan.md` |
| Test cases | `02-test-cases/test-cases.csv` |
| Test execution results | `03-test-execution/execution-results.csv` |
| Bug reports | `04-bug-reports/` |
| API test cases and Postman collection | `05-api-testing/` |
| Test summary report | `06-test-summary/test-summary-report.md` |

## 11. Bug Severity and Priority Definitions

| Severity | Definition |
|---|---|
| Critical | Core functionality is broken with no workaround (e.g. users cannot register or log in) |
| High | Major feature is impaired, but a workaround exists |
| Medium | Minor feature issue or incorrect validation that does not block the main flow |
| Low | Cosmetic issue, typo, or minor usability concern |

| Priority | Definition |
|---|---|
| High | Should be fixed immediately |
| Medium | Should be fixed in the next release |
| Low | Can be fixed when time allows |

## 12. Test Case Status Definitions

| Status | Meaning |
|---|---|
| Pass ✅ | Actual result matches expected result |
| Fail ❌ | Actual result does not match expected result; a bug is logged |
| Blocked ⚠️ | The test cannot be executed because of an external issue (e.g. site down, dependency failed) |

## 13. Risks and Assumptions

| # | Risk / Assumption | Mitigation |
|---|---|---|
| 1 | Public practice sites may go down or be slow | Retry later; mark affected tests Blocked and note the date |
| 2 | Shared practice data may be changed or deleted by other users (especially Restful-Booker) | Create your own bookings and use their IDs rather than relying on existing ones |
| 3 | Sites may change over time, so results reflect the date tested | Record the execution date in all results |
| 4 | Limited to one primary browser | Add a basic Edge check for key flows |
| 5 | Assumption: expected behaviour is based on common web standards and the API's published documentation, as no formal requirements exist | State the basis for expected results in each test case |

## 14. Roles

| Role | Responsibility |
|---|---|
| QA Tester (Likhona) | Test planning, test case design, execution, bug reporting, reporting |