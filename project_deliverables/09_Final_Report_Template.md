# Final Report - Software Testing of TishCommerce

**Course:** Software Testing
**Professor:** Dr.sc. Liridon Hoti
**Group:** [Your Group Name]
**Date:** 2026

---

## Table of Contents

1. Introduction
2. System Description
3. System Modeling (Use Cases, Activity Diagrams)
4. Test Strategy
5. Test Plan
6. Manual Testing
7. Automated Testing
8. API Testing
9. Performance Testing
10. Bug Reports
11. Quality Analysis (ISO 25010)
12. Conclusions

---

## Chapter 1: Introduction

### 1.1 Project Overview
This report presents the comprehensive software testing process performed on the TishCommerce e-commerce web application. The testing covers manual testing (53 test cases using 5 techniques), automated testing (10 Playwright tests), API testing (5 Postman tests), performance testing (3 JMeter test plans), and quality analysis based on ISO/IEC 25010 standard.

### 1.2 Objectives
- Apply modern software testing methodologies
- Perform systematic analysis of system requirements
- Design and implement a comprehensive testing strategy
- Execute manual and automated tests
- Integrate testing into a CI/CD pipeline
- Analyze system quality using ISO 25010

### 1.3 System Under Test
**Application:** TishCommerce
**Type:** E-commerce web application
**URL:** http://localhost:3000
**Technology Stack:** Next.js 16, React 19, Tailwind CSS, Redux Toolkit, PayPal SDK, Stripe

---

## Chapter 2: System Description

### 2.1 Overview
TishCommerce is a modern, database-free e-commerce web application built with Next.js 16. It allows customers to browse products, manage a shopping cart, complete purchases via PayPal or Stripe, contact the store, and subscribe to newsletters. The application uses JSON configuration files instead of a database.

### 2.2 Key Features (12 Functionalities)
1. **View Homepage** – Banner, featured products, brand story, testimonials, newsletter, brands
2. **Browse Products** – Search, sort (name/price/newest), category filtering
3. **View Product Details** – Images, price, description, Add to Cart
4. **Shopping Cart** – Add/remove items, update quantities, mini-cart
5. **Checkout** – Billing form, shipping method, payment selection
6. **PayPal Payment** – Express Checkout and Basket Express
7. **Stripe Payment** – Credit card processing
8. **Order Summary** – Post-purchase confirmation
9. **Contact Form** – reCAPTCHA-protected message submission
10. **Newsletter Signup** – Email subscription
11. **Documentation** – Help/docs pages
12. **Navigation** – Menu links, social media links

### 2.3 Actors
- **Customer** – Browses products, manages cart, checks out
- **Payment Gateway (PayPal/Stripe)** – External payment processing
- **Email Service (Nodemailer)** – Sends contact form submissions

---

## Chapter 3: System Modeling

### 3.1 Use Case Diagram
[Insert Use Case Diagram from 01_System_Analysis.md]

### 3.2 Detailed Use Cases (8 Use Cases)
[Insert 8 Use Cases from 01_System_Analysis.md]

### 3.3 Activity Diagram
[Insert Activity Diagram from 01_System_Analysis.md]

### 3.4 Critical Functionalities
| Priority | Functionality | Risk |
|----------|--------------|------|
| HIGH | Checkout Process | Financial impact |
| HIGH | PayPal/Stripe Payments | Financial transaction |
| HIGH | Shopping Cart | Core feature |
| MEDIUM | Browse Products | User experience |
| MEDIUM | Contact Form | Data validation |
| LOW | Documentation | Static content |

---

## Chapter 4: Test Strategy

### 4.1 Scope of Testing
**In Scope:** Functional testing, UI/UX, form validation, payment integration, API testing, cross-browser compatibility, performance testing
**Out of Scope:** Backend/database, security penetration, load/stress testing

### 4.2 Test Levels
| Level | Description | Tools |
|-------|-------------|-------|
| Unit | Component/function testing | Jest |
| Integration | Component interactions | Playwright |
| System | End-to-end workflows | Playwright |
| Acceptance | Business requirements | Manual |

### 4.3 Test Types
Functional, UI/UX, Form Validation, Payment Integration, Navigation, Performance, Compatibility

### 4.4 Risk Analysis
[Insert Risk Analysis table from 02_Test_Strategy_And_Plan.md]

### 4.5 Entry & Exit Criteria
[Insert from 02_Test_Strategy_And_Plan.md]

### 4.6 Test Environment
| Component | Specification |
|-----------|--------------|
| OS | Windows 11 |
| Browser | Chrome, Firefox, Edge |
| Node.js | v22.14.0 |
| URL | http://localhost:3000 |

---

## Chapter 5: Test Plan

### 5.1 Features to Test
[Insert Test Plan table from 02_Test_Strategy_And_Plan.md]

### 5.2 Testing Schedule
| Day | Activities |
|-----|------------|
| Day 1 | System Analysis, Strategy/Plan, 25 Manual Tests |
| Day 2 | 28 Manual Tests, Automated Tests, API Tests |
| Day 3 | Performance Tests, CI/CD, Quality Analysis |

---

## Chapter 6: Manual Testing

### 6.1 Testing Techniques Used
1. **Black Box Testing** – 15 test cases (TC-BB-01 to TC-BB-15)
2. **Equivalence Partitioning** – 10 test cases (TC-EP-01 to TC-EP-10)
3. **Boundary Value Analysis** – 10 test cases (TC-BV-01 to TC-BV-10)
4. **Decision Table Testing** – 8 test cases (TC-DT-01 to TC-DT-08)
5. **State Transition Testing** – 10 test cases (TC-ST-01 to TC-ST-10)

### 6.2 Test Case Format
Each test case includes: TC-ID, Description, Preconditions, Test Steps, Input Data, Expected Result, Actual Result, Status

### 6.3 Test Cases
[Insert all 53 test cases from 03_Manual_Test_Cases.md]

### 6.4 Results Summary
| Technique | Count | Pass | Fail |
|-----------|-------|------|------|
| Black Box Testing | 15 | ☐ | ☐ |
| Equivalence Partitioning | 10 | ☐ | ☐ |
| Boundary Value Analysis | 10 | ☐ | ☐ |
| Decision Table Testing | 8 | ☐ | ☐ |
| State Transition Testing | 10 | ☐ | ☐ |
| **TOTAL** | **53** | ☐ | ☐ |

---

## Chapter 7: Automated Testing

### 7.1 Tool Selection
**Tool:** Playwright
**Reason:** Industry-standard browser automation, cross-browser support, reliable selectors

### 7.2 Test Environment Setup
- npm install @playwright/test
- npx playwright install chromium
- Configuration in playwright.config.ts

### 7.3 Test Cases (10 Tests)
| ID | Test Name | Status |
|----|-----------|--------|
| AT-01 | Homepage loads with correct title | ☐ |
| AT-02 | Products page shows product grid | ☐ |
| AT-03 | All navigation links work | ☐ |
| AT-04 | Product detail with Add to Cart | ☐ |
| AT-05 | Add to Cart flow | ☐ |
| AT-06 | Cart page structure | ☐ |
| AT-07 | Checkout page loads | ☐ |
| AT-08 | Contact form renders | ☐ |
| AT-09 | Documentation page | ☐ |
| AT-10 | About page content | ☐ |

### 7.4 How to Run
```bash
npm run dev           # Start app
npx playwright test   # Run tests
npx playwright show-report  # View HTML report
```

### 7.5 Test Results
[Insert Playwright HTML report screenshots]

---

## Chapter 8: API Testing

### 8.1 Tool: Postman

### 8.2 API Test Cases (5 Tests)
| TC-ID | Endpoint | Method | Expected Status | Actual Status |
|-------|----------|--------|-----------------|---------------|
| API-01 | /api/localization | GET | 200 OK | ☐ |
| API-02 | /api/products | GET | 200 OK | ☐ |
| API-03 | /api/products?slug=X | GET | 200/404 | ☐ |
| API-04 | /api/newsletter | POST | 400 (validation) | ☐ |
| API-05 | /api/contact | POST | 400 (validation) | ☐ |

[Insert detailed test descriptions from 04_API_Testing_Postman.md]

---

## Chapter 9: Performance Testing

### 9.1 Tool: Apache JMeter

### 9.2 Test Plans
1. **Homepage Load Test** – 10 concurrent users, 5s ramp-up, 3 loops
2. **Multi-Page Navigation** – 5 users, navigate 5 pages
3. **API Performance** – 20 users, 2 API endpoints

### 9.3 Results
[Insert JMeter screenshots after running tests]

### 9.4 Analysis
[Complete analysis from 06_Performance_Testing_JMeter.md]

---

## Chapter 10: Bug Reports

### 10.1 Bugs Found: 12 Total
| Bug ID | Severity | Priority | Description |
|--------|----------|----------|-------------|
| BUG-01 | Low | Low | Image aspect ratio warnings |
| BUG-02 | Medium | Medium | Missing ALT text |
| BUG-03 | Medium | High | Empty checkout access |
| BUG-04 | Low | Medium | reCAPTCHA error page |
| BUG-05 | Medium | Medium | "No products" flash on load |
| BUG-06 | Low | Low | Unlimited quantity |
| BUG-07 | Medium | Medium | Special characters in search |
| BUG-08 | Low | Low | Social links security |
| BUG-09 | Medium | Medium | Back button behavior |
| BUG-10 | High | High | Newsletter email validation |
| BUG-11 | Medium | Medium | Mobile price alignment |
| BUG-12 | Medium | High | Keyboard focus indicators |

[Insert detailed bug reports from 05_Bug_Reports.md]

---

## Chapter 11: Quality Analysis (ISO 25010)

### 11.1 Quality Characteristics Assessment
| Characteristic | Score | Key Finding |
|----------------|-------|-------------|
| Functional Suitability | 7/10 | All core features present |
| Reliability | 7/10 | No crashes, no persistence |
| Usability | 8/10 | Clean UI, accessibility gaps |
| Performance Efficiency | 8/10 | Fast, lightweight |
| Maintainability | 7/10 | Good architecture, some `any` types |
| Security | 5/10 | No auth, no input sanitization |
| Compatibility | 7/10 | External API dependencies |
| Portability | 9/10 | No database, cross-platform |
| **TOTAL** | **58/80 (72.5%)** | |

### 11.2 Recommendations
1. Add security (authentication, input sanitization)
2. Implement cart persistence (localStorage)
3. Improve keyboard accessibility
4. Add caching for performance
5. Remove `any` types in TypeScript

---

## Chapter 12: Conclusions

### 12.1 Summary
The testing process of TishCommerce demonstrated a thorough application of modern software testing methodologies. A total of 53 manual test cases were designed using 5 different techniques (Black Box, Equivalence Partitioning, Boundary Value Analysis, Decision Table, State Transition). Automated testing was implemented using Playwright with 10 test cases. API testing covered 5 endpoints using Postman. Performance testing was prepared with 3 JMeter test plans.

### 12.2 Key Findings
- The system is **functionally complete** with all core e-commerce features
- **Usability** is strong with a clean, modern interface
- **Security** is the weakest area (no authentication, no input sanitization)
- **12 bugs** were identified ranging from low to high severity
- Overall **quality score: 72.5%** based on ISO 25010

### 12.3 Tools Used
- Playwright (Automated Testing)
- Postman (API Testing)
- Apache JMeter (Performance Testing)
- GitHub Actions (CI/CD Pipeline)

### 12.4 Recommendations
The system is suitable for basic e-commerce purposes. For production deployment, adding authentication, cart persistence, and security improvements is recommended.