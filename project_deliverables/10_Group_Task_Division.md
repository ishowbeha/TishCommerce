# Task Division for Your 3-Person Group

Since everything is already created, your friends don't need to install anything complex. Here's how to split the **remaining work**:

---

## 👤 Person 1: YOU (Project Lead)
**You already did:** System analysis, test strategy, test cases, all document creation

**Still needs to do:**
1. ✅ Run the Playwright automated tests:
   ```bash
   cd C:\Users\behar\OneDrive\Desktop\testim\TishCommerce
   npx playwright test
   npx playwright show-report
   ```
2. ✅ Run the 53 manual tests on the actual website (fill Pass/Fail)
3. ✅ Take screenshots of everything for the report
4. ✅ Present the project (you know it best)

---

## 👤 Person 2: "API & Performance Tester"

### What they need to install:
- ✅ **Postman** → Already downloaded (from https://www.postman.com/downloads/)
- ✅ **JMeter** → Already downloaded, Java is installed, it opens

### What they need to DO:

**In Postman (takes 30 min):**
1. Open Postman
2. Follow `04_API_Testing_Postman.md` instructions
3. Create 5 API requests to `http://localhost:3000`
4. Take screenshots of each response
5. Fill in the results table

**In JMeter (takes 30 min):**
1. Open JMeter (double-click `jmeter.bat`)
2. Follow `06_Performance_Testing_JMeter.md` instructions
3. Create 3 test plans
4. Run them
5. Take screenshots of the results (graphs, summary report)

---

## 👤 Person 3: "Report & Presentation Builder"

### What they need to install:
- ✅ **Microsoft Word** (already have it)
- ✅ **PowerPoint** or Google Slides

### What they need to DO:

**Build the Word Report (2-3 hours):**
1. Open Word → New document
2. Use `09_Final_Report_Template.md` as structure
3. Open each `.md` file from `project_deliverables\` folder
4. Copy-paste content into matching chapters
5. Insert screenshots from Person 1 and Person 2
6. Format: Times New Roman 12pt, 1.5 spacing, A4
7. Add table of contents
8. **Add your group names** on the title page
9. Save as PDF when done

**Build the PowerPoint (1 hour):**
1. Open PowerPoint
2. Follow `08_Presentation_Outline.md` for the 15 slides
3. Each slide only needs 3-4 bullet points
4. Add screenshots
5. Save and share with Person 1 for the presentation

---

## 📋 CHECKLIST FOR EACH PERSON

### Person 1 Checklist:
- [ ] Run `npx playwright test` → take screenshot of results
- [ ] Run `npx playwright show-report` → take screenshot of HTML report
- [ ] Execute all 53 manual tests on the website
- [ ] Fill in Pass/Fail for each test case
- [ ] Take screenshots of bugs found (browser console, pages)
- [ ] Practice the 15-minute presentation

### Person 2 Checklist:
- [ ] Open Postman
- [ ] Test GET /api/localization → screenshot
- [ ] Test GET /api/products → screenshot
- [ ] Test GET /api/products?slug=X → screenshot
- [ ] Test POST /api/newsletter (both valid + invalid) → screenshot
- [ ] Test POST /api/contact (both valid + invalid) → screenshot
- [ ] Open JMeter
- [ ] Create Homepage Load Test Plan → run → screenshot
- [ ] Create Multi-Page Navigation Test Plan → run → screenshot
- [ ] Create API Performance Test Plan → run → screenshot

### Person 3 Checklist:
- [ ] Create Word document with title page
- [ ] Copy Chapter 1-2 (Introduction + System Description) from 01_System_Analysis.md
- [ ] Copy Chapter 3 (Use Cases + Activity Diagram) from 01_System_Analysis.md
- [ ] Copy Chapter 4-5 (Test Strategy + Plan) from 02_Test_Strategy_And_Plan.md
- [ ] Copy Chapter 6 (Manual Testing) from 03_Manual_Test_Cases.md
- [ ] Copy Chapter 7 (Automated Testing) from automated-tests.spec.ts
- [ ] Copy Chapter 8 (API Testing) from 04_API_Testing_Postman.md
- [ ] Copy Chapter 9 (Performance) from 06_Performance_Testing_JMeter.md
- [ ] Copy Chapter 10 (Bug Reports) from 05_Bug_Reports.md
- [ ] Copy Chapter 11 (Quality Analysis) from 07_Quality_Analysis_ISO25010.md
- [ ] Copy Chapter 12 (Conclusions)
- [ ] Add all screenshots from Person 1 and Person 2
- [ ] Create PowerPoint with 15 slides
- [ ] Add group names and professor name

---

## ⏱️ TIME ESTIMATE PER PERSON

| Person | Task | Time Needed |
|--------|------|-------------|
| **You (Person 1)** | Run tests + screenshots + prepare presentation | ~3 hours |
| **Person 2** | Postman + JMeter + screenshots | ~1.5 hours |
| **Person 3** | Word report + PowerPoint from templates | ~3-4 hours |

---

## 📸 Screenshots Everyone Needs to Take

### Person 1 (Manual + Automated):
1. Playwright test results (terminal output)
2. Playwright HTML report
3. Homepage at localhost:3000
4. Products page
5. Cart with items
6. Checkout page
7. Contact form
8. Browser console (BUG-01)
9. Cart with many items (BUG-06)
10. Mobile view (BUG-11)

### Person 2 (API + Performance):
1. Postman - GET /api/localization response
2. Postman - GET /api/products response
3. Postman - POST /api/newsletter error response
4. Postman - POST /api/contact missing fields error
5. Postman collection overview
6. JMeter - Thread Group configuration
7. JMeter - Summary Report results
8. JMeter - Graph Results
9. JMeter - View Results Tree

---

## 💡 SHORT SUMMARY FOR YOUR FRIENDS

*"Hey, everything is already created. I just need you to:*
- *Person 2: Open Postman, make 5 API calls and screenshot them. Then open JMeter and run 3 tests. Takes 1.5 hours.*
- *Person 3: Open Word and copy-paste from the files I created into a 25-page report. Then make a 15-slide PowerPoint. Takes 3-4 hours.*
- *I'll run the Playwright tests and do the presentation.*

*Simple!"* 👍