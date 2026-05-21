# 🚀 START HERE - What You Need to Install & How to Document

## 📦 SOFTWARE YOU NEED TO DOWNLOAD

### Already Installed ✅
| Software | Version | Purpose |
|----------|---------|---------|
| Node.js | v22.14.0 | Runs the app |
| npm | 11.12.1 | Package manager |
| Git | 2.51.0 | Version control / CI/CD |
| VS Code | ✅ | Code editor |
| Python | 3.13 | (Optional, for some test utilities) |

### Need to Download ❌

| # | Software | Download Link | Purpose | Size |
|---|----------|--------------|---------|------|
| 1 | **Postman** | https://www.postman.com/downloads/ | API Testing (5 tests) | ~200MB |
| 2 | **Apache JMeter** | https://jmeter.apache.org/download_jmeter.cgi | Performance Testing | ~60MB |
| 3 | **Java (JDK 17+)** | https://adoptium.net/temurin/releases/ | Required for JMeter | ~200MB |
| 4 | **Playwright** (via npm) | `npx playwright install` | Automated Testing | ~400MB |
| 5 | **GitHub Account** | https://github.com/signup | CI/CD Pipeline | Free |

### Installation Order
```
1. Install Java (required for JMeter)
2. Install Postman
3. Install Apache JMeter (extract ZIP)
4. Run: npm install (already done)
5. Run: npx playwright install (I'll help you)
```

---

## 📝 HOW TO DOCUMENT EVERYTHING IN WORD

**Step-by-step for your Word Report:**

### 1. Create the Word Document Structure
```
Open Word → Create "TishCommerce_Testing_Project.docx"

Set page size: A4
Set margins: 2.5cm all sides
Font: Times New Roman 12pt
Line spacing: 1.5
Heading styles: Heading 1 = 16pt Bold, Heading 2 = 14pt Bold
```

### 2. How to Copy My Content into Word

I'm saving everything as `.md` (Markdown) files in this folder:
```
C:\Users\behar\OneDrive\Desktop\testim\TishCommerce\project_deliverables\
```

**Method 1: Copy-Paste (Easiest)**
1. Open each `.md` file from the folder
2. Select All (Ctrl+A) → Copy (Ctrl+C)
3. Paste into Word (Ctrl+V)
4. Re-apply formatting in Word (tables may need adjustment)

**Method 2: Convert to Word directly**
I can also save files as `.docx` if you prefer. Just tell me.

### 3. What Each File Contains

| File | What's Inside | For Report Section |
|------|---------------|-------------------|
| `01_System_Analysis.md` | System description, actors, 8 use cases, activity diagram, critical functionalities | Chapter 2 & 3 |
| `02_Test_Strategy_And_Plan.md` | Test strategy, test levels, test types, risk analysis, test plan | Chapter 4 & 5 |
| `03_Manual_Test_Cases.md` | 53 test cases (BB, EP, BVA, DT, ST) | Chapter 6 |
| (Next files will be created as we go) | API, Automated, Performance, Bugs, Quality, CI/CD | Chapters 7-11 |

---

## 🎮 HOW TO RUN THE APPLICATION

The app is ALREADY running at:
```
http://localhost:3000
```

If you close the terminal and need to restart:
```
1. Open CMD or PowerShell
2. cd C:\Users\behar\OneDrive\Desktop\testim\TishCommerce
3. npm run dev
4. Open http://localhost:3000 in browser
```

---

## ✅ WHAT I'VE CREATED SO FAR (Check these files exist)

Go to this folder on your computer:
```
C:\Users\behar\OneDrive\Desktop\testim\TishCommerce\project_deliverables\
```

You should see:
- ✅ `00_START_HERE_Installation_Guide.md` (this file)
- ✅ `01_System_Analysis.md`
- ✅ `02_Test_Strategy_And_Plan.md`
- ✅ `03_Manual_Test_Cases.md`

**Next I will create:**
- Automated Tests (Playwright)
- API Tests (Postman collection)
- Bug Reports
- Performance Test Plan
- CI/CD Pipeline
- Quality Analysis (ISO 25010)
- Final Report Template
- Presentation Slides

Tell me when you're ready and I'll continue! Type **"continue"** or ask any questions.