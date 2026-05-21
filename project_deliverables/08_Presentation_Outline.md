# Presentation - Software Testing of TishCommerce (15 Minutes)

## Slide Structure (15 Slides)

---

### Slide 1: Title Slide
**Title:** Software Testing of TishCommerce E-Commerce Application
**Subtitle:** Project for Software Testing Course
**Author:** [Your Group Name]
**Professor:** Dr.sc. Liridon Hoti
**Date:** 2026

---

### Slide 2: Agenda
1. System Overview (1 min)
2. Testing Strategy (2 min)
3. Manual Testing Demo (3 min)
4. Automated Testing Demo (3 min)
5. API Testing (1 min)
6. Performance Testing (1 min)
7. Bug Analysis (2 min)
8. Quality Assessment (1 min)
9. Conclusion (1 min)

---

### Slide 3: System Overview
**TishCommerce E-Commerce Application**
- **Technology:** Next.js 16 + React 19 + Tailwind CSS
- **Features:** 12 functionalities (browse, cart, checkout, PayPal, Stripe, contact, newsletter, docs)
- **Architecture:** Database-free (JSON config files)
- **URL:** http://localhost:3000

**[Screenshot of homepage]**

---

### Slide 4: Testing Strategy
- **Scope:** All 12 functionalities
- **Levels:** Unit → Integration → System → Acceptance
- **Techniques Used:**
  - Black Box Testing (15 TCs)
  - Equivalence Partitioning (10 TCs)
  - Boundary Value Analysis (10 TCs)
  - Decision Table Testing (8 TCs)
  - State Transition Testing (10 TCs)
- **Total:** 53 Manual Test Cases

---

### Slide 5: Manual Testing - Demo (Part 1)
**Black Box Testing Example:**
- **TC-BB-01:** Products page loads correctly → ✅ Pass
- **TC-BB-05:** Product detail page with Add to Cart → ✅ Pass

**Equivalence Partitioning Example:**
- **TC-EP-01:** Valid email "user@example.com" → ✅ Pass
- **TC-EP-02:** Invalid email "userexample.com" → ❌ Validation error

**[Show screenshots of test execution]**

---

### Slide 6: Manual Testing - Demo (Part 2)
**Boundary Value Analysis:**
- **TC-BV-01:** Minimum quantity = 1 → ✅ Pass
- **TC-BV-02:** Below minimum (qty 0) → Item removed ✅

**Decision Table Testing:**
- **TC-DT-01:** All checkout fields complete → ✅ Success
- **TC-DT-04:** No shipping selected → ❌ Error message

**State Transition Testing:**
- Cart state machine: Empty → Active → Checkout → Complete

**[Show state transition diagram]**

---

### Slide 7: Automated Testing Overview
**Tool:** Playwright
**Tests:** 10 Automated Tests
- AT-01: Homepage loads with correct title
- AT-02: Products page shows grid
- AT-03: Navigation links work
- AT-04: Product detail page
- AT-05: Add to Cart flow
- AT-06: Cart page structure
- AT-07: Checkout page loads
- AT-08: Contact form renders
- AT-09: Documentation page
- AT-10: About page content

---

### Slide 8: Automated Testing - Live Demo
**How to run:**
```bash
npx playwright test --project=chromium
```

**Test Results:**
```
✓ AT-01: Homepage loads (1.2s)
✓ AT-02: Products page (2.1s)
✓ AT-03: Navigation links (3.5s)
✓ AT-04: Product detail (2.0s)
✓ AT-05: Add to Cart (3.0s)
✓ AT-06: Cart page (1.5s)
✓ AT-07: Checkout page (1.8s)
✓ AT-08: Contact page (2.2s)
✓ AT-09: Documentation (1.3s)
✓ AT-10: About page (1.1s)
```

**[Show Playwright HTML report screenshot]**

---

### Slide 9: API Testing
**Tool:** Postman
**5 API Test Cases:**

| TC-ID | Endpoint | Method | Status |
|-------|----------|--------|--------|
| API-01 | /api/localization | GET | ✅ 200 OK |
| API-02 | /api/products | GET | ✅ 200 OK |
| API-03 | /api/products?slug=X | GET | ✅ 200/404 |
| API-04 | /api/newsletter | POST | ✅ 400 validation |
| API-05 | /api/contact | POST | ✅ 400 validation |

**[Show Postman screenshot]**

---

### Slide 10: Performance Testing
**Tool:** Apache JMeter
**3 Test Plans:**

| Test | Users | Avg Response | Errors |
|------|-------|-------------|--------|
| Homepage Load | 10 users | < 500ms | 0% |
| Multi-Page Nav | 5 users | < 1s | 0% |
| API Performance | 20 users | < 300ms | 0% |

**Conclusion:** System performs well under moderate load

**[Show JMeter graph screenshot]**

---

### Slide 11: Bug Reports
**12 Bugs Found | Severity Overview:**

| Severity | Count | Examples |
|----------|-------|---------|
| High | 2 | Newsletter validation (BUG-10), Missing focus indicators (BUG-12) |
| Medium | 5 | Empty checkout (BUG-03), "No products" flash (BUG-05), Special chars (BUG-07), Back button (BUG-09), Mobile layout (BUG-11) |
| Low | 5 | Image ratio (BUG-01), ALT text (BUG-02), reCAPTCHA error (BUG-04), Unlimited qty (BUG-06), Social links (BUG-08) |

**[Show bug tracking screenshot]**

---

### Slide 12: Bug Demo - Top 3 Bugs
**BUG-10 (High):** Newsletter accepts invalid email "abc" without validation
**Expected:** Email format validation
**Actual:** No validation shown

**BUG-03 (Medium):** Checkout accessible with empty cart
**Expected:** Redirect or block
**Actual:** Empty form loads

**BUG-01 (Low):** Brand images show console warnings
**Expected:** No console errors
**Actual:** Aspect ratio warnings

**[Show screenshots for each bug]**

---

### Slide 13: Quality Analysis (ISO 25010)
**Overall Score: 72.5% (58/80)**

| Characteristic | Score |
|----------------|-------|
| Portability | 9/10 |
| Usability | 8/10 |
| Performance | 8/10 |
| Compatibility | 7/10 |
| Reliability | 7/10 |
| Maintainability | 7/10 |
| Functionality | 7/10 |
| Security | 5/10 |

**Key Weakness:** Security (no auth, no input sanitization)

---

### Slide 14: CI/CD Pipeline
**Tool:** GitHub Actions

**Pipeline Stages:**
1. Lint & Type Check → 2. Build → 3. Automated Tests → 4. API Tests → 5. Deploy

**Benefits:**
- Tests run automatically on every push
- Test reports are generated
- Ensures code quality before deployment

**[Show GitHub Actions workflow screenshot]**

---

### Slide 15: Conclusion

**What Was Achieved:**
✅ Complete system analysis with 8 use cases
✅ Test Strategy & Test Plan documents
✅ 53 manual test cases (5 techniques)
✅ 10 automated tests (Playwright)
✅ 5 API tests (Postman)
✅ 3 performance test plans (JMeter)
✅ 12 bug reports
✅ ISO 25010 quality analysis
✅ CI/CD pipeline (GitHub Actions)
✅ Final report & presentation

**Thank you! Questions?**