# Free Platforms to Practice QA

Everything below is free (or has a free tier that is enough for learning and for a portfolio). Grouped by the phases in [ROADMAP.md](./ROADMAP.md).

---

## 1. Web apps to test manually and automate

These are *built* for testing practice — you cannot break anything, and they intentionally contain quirks and bugs.

| Site | Why use it |
|---|---|
| https://www.saucedemo.com | Small, stable login → cart → checkout flow. Best first automation target. Has deliberately broken users (`problem_user`, `performance_glitch_user`) — great for bug reports. |
| https://demo.opencart.com | Full e-commerce app: register, search, cart, checkout, admin panel. Best target for a large manual test-case suite. |
| https://opensource-demo.orangehrmlive.com | HRMS with roles, leave requests, admin config. Good for permission/role-based test scenarios. Login: `Admin` / `admin123`. |
| https://demoqa.com | Every widget type: forms, date pickers, frames, alerts, uploads, dynamic elements. Best for practising Selenium locators and waits. |
| https://the-internet.herokuapp.com | Classic hard cases: dynamic loading, file download, drag & drop, JS alerts, basic auth, shadow DOM. |
| https://automationexercise.com | E-commerce with an official list of 26 test cases — compare your written test cases against theirs. |
| https://parabank.parasoft.com | Banking app (transfers, bill pay, account history) and it exposes a REST/SOAP API for the same data — good for UI + API cross-verification. |
| https://practice.expandtesting.com | Login, file upload, notifications, plus a free API for the same app. |
| https://magento.softwaretestingboard.com | Large real Magento store — good for exploratory and regression practice. |
| https://katalon-test.s3.amazonaws.com/aut/html/form.html | Simple form for EP/BVA practice. |

**Local/self-hosted options** (useful for testing installs, logs, and DB verification together):

- **Juice Shop** — `docker run -p 3000:3000 bkimminich/juice-shop` (also the standard app for security-testing basics)
- **WebGoat**, **DVWA** — deliberately vulnerable apps
- Any open-source app with a `docker-compose.yml`

---

## 2. API testing

| Resource | Use |
|---|---|
| https://reqres.in | Real request/response with predictable data; supports POST/PUT/PATCH/DELETE and delayed responses. |
| https://jsonplaceholder.typicode.com | Fake REST API — fine for learning methods and status codes (writes are simulated). |
| https://petstore.swagger.io | Live Swagger/OpenAPI docs — practise reading a spec and testing from it. |
| https://gorest.co.in | Requires a free token — good for practising Bearer auth. |
| https://restful-booker.herokuapp.com | Booking API with auth, deliberate bugs, and a documented spec. Excellent for negative testing. |
| https://openweathermap.org/api, https://api.github.com | Real public APIs with rate limits and real error responses. |

Tools: **Postman** (free), **Insomnia**, **Hoppscotch** (browser-based, no install), **Newman** (CLI runner), **curl**.

---

## 3. SQL

- https://sqlzoo.net — guided exercises, browser-based
- https://www.hackerrank.com/domains/sql — easy → medium, good interview overlap
- https://leetcode.com/problemset/database/ — free tier covers plenty
- https://www.sql-practice.com — hospital schema, difficulty-tagged
- https://sqlbolt.com — short interactive lessons
- https://www.w3schools.com/sql/trysql.asp — instant editor, no signup
- **db-fiddle.com** / **sqliteonline.com** — paste your own schema and run queries
- Locally: SQLite (zero setup) or MySQL/PostgreSQL via Docker with the Sakila or Chinook sample database

---

## 4. Tools with free tiers

| Tool | Free tier |
|---|---|
| **Jira Cloud** | Free up to 10 users — enough to run a real bug workflow and JQL practice |
| **Qase** | Free test case management, good UI, exportable |
| **TestRail** | 14-day trial — take screenshots for your portfolio while it lasts |
| **Zephyr Scale / Xray** | Free trials as Jira add-ons |
| **GitHub Actions** | Free minutes on public repos — run your test suite in CI |
| **BrowserStack / LambdaTest / Sauce Labs** | Free plans for open-source projects and limited free minutes; enough for cross-browser screenshots |
| **Allure Report / pytest-html** | Open source reporting |
| **Postman** | Free workspaces, collection runner, monitors |
| **Bugzilla / MantisBT** | Free open-source defect trackers you can self-host if Jira feels heavy |

---

## 5. Learning + certification (free)

- **ISTQB Foundation syllabus & sample papers** — https://www.istqb.org (documents are free; only the exam costs money). Study it even if you don't sit the exam; interview questions come straight from it.
- **Test Automation University** (Applitools) — https://testautomationu.applitools.com — free full courses on Selenium, Playwright, API testing, with certificates
- **Ministry of Testing** — https://www.ministryoftesting.com — free articles, "99 second talks", community
- **Google Test Automation Conference** talks on YouTube
- **Postman Student Expert** certification — free
- **freeCodeCamp** — free Python and JS courses for the automation phases
- **Playwright / Cypress official docs** — both have free, high-quality tutorials

---

## 6. Practice that counts as real experience

Cheap credibility for a CV, all free:

- **Open-source bug hunting** — find GitHub repos with a `good first issue` or `bug` label, reproduce the bug, and comment with clean reproduction steps. A public, well-written repro on a real project is worth more than 50 practice test cases.
- **uTest / Testlio / Test IO** — crowdtesting platforms; free to join, paid per accepted bug. Real applications, real defect reports.
- **Bug bounty for functional bugs** — some products (e.g. open-source apps on GitHub) accept UX/functional reports without security expertise.
- **Test a friend's / your own side project** and file the issues on GitHub.

---

## Suggested order

1. Weeks 3–4 manual project → **saucedemo** + **demo.opencart.com**, track bugs in **Jira free**
2. Week 6 SQL → **sqlzoo** then **HackerRank SQL**
3. Weeks 7–8 API → **restful-booker** and **reqres.in** in **Postman**
4. Weeks 9–10 automation → **saucedemo** first, then **the-internet.herokuapp.com** for the hard cases
5. Week 11 CI → **GitHub Actions** on this repo
