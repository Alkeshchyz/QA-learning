# QA Internship Readiness Roadmap

A 12-week plan that continues from where this repo currently is (Days 1–5 of testing fundamentals) and ends with a portfolio that is enough to apply for QA / SDET internships.

## Where this repo stands today

| Done | Missing |
|---|---|
| Testing basics, SDLC/STLC, V&V, 7 principles, levels of testing | Test design techniques, written test cases, real bug reports, a tool (Jira/TestRail), SQL, API testing, automation, a CV/portfolio |

Right now the repo is **notes only**. Interviewers hire on *artifacts* — test cases you wrote, bugs you logged, scripts that run. Every phase below therefore ends with something committed to this repo, not just a note.

Suggested repo structure to grow into:

```
01-software-testing-fundamentals/    # exists
02-test-design-techniques/
03-manual-testing-project/           # test plan, test cases, bug reports
04-sql-and-databases/
05-api-testing-postman/
06-automation-selenium-python/
07-playwright-or-cypress/
08-ci-and-tools/
resume/
```

---

## Phase 1 — Finish manual testing theory (Week 1–2)

Topics, roughly one per day:

- Testing types: functional vs non-functional, smoke, sanity, regression, retesting, exploratory, ad-hoc, UAT
- Black box / white box / grey box
- **Test design techniques** (asked in almost every interview):
  - Equivalence Partitioning
  - Boundary Value Analysis
  - Decision Table Testing
  - State Transition Testing
  - Use Case Testing
  - Error Guessing
- Defect life cycle: New → Assigned → Open → Fixed → Retest → Closed / Reopen / Deferred / Rejected
- Severity vs Priority (with examples of high-severity/low-priority and vice versa)
- Test artifacts: test plan, test scenario, test case, RTM (traceability matrix), test summary report
- Agile & Scrum: sprints, standups, backlog grooming, story points, definition of done, QA's role in a sprint

**Deliverable:** `02-test-design-techniques/` with notes **plus** worked examples — e.g. BVA + EP applied to an age field (18–60) and a decision table for a login form.

---

## Phase 2 — Manual testing on a real app (Week 3–4)

Pick one public practice app and test it properly:

- https://demo.opencart.com (e-commerce)
- https://www.saucedemo.com (login/cart flows)
- https://opensource-demo.orangehrmlive.com (HRMS)
- https://demoqa.com (forms, widgets)

Do the full cycle:

1. Write a short **test plan** (scope, in/out of scope, environment, risks, entry/exit criteria)
2. Write **60–100 test cases** in a spreadsheet: ID, module, title, precondition, steps, test data, expected result, actual result, status, priority
3. Execute them and log **10–15 real bug reports**: title, environment, steps to reproduce, expected vs actual, severity, priority, screenshot/video
4. Write a **test summary report**: executed / passed / failed / blocked, defect breakdown by severity
5. Build a small **RTM** mapping requirements → test cases

**Deliverable:** `03-manual-testing-project/` with the plan, the test case sheet (CSV or Markdown), bug reports in Markdown, and screenshots. This single folder is the strongest thing you can show as a fresher.

---

## Phase 3 — Tools QA teams actually use (Week 5)

- **Jira** — free cloud account; create a project, log your Phase 2 bugs there, move them through a workflow, learn JQL basics
- **TestRail / Zephyr / Qase** — free tier; upload one test suite and run it
- **Git & GitHub** — branches, commits, pull requests (you are already doing this — keep commits clean and descriptive)
- Basic Linux/CLI: `cd`, `ls`, `grep`, `tail -f` on a log file
- Chrome DevTools for QA: Console (JS errors), Network tab (status codes, payloads), Application tab (cookies, localStorage), device emulation

**Deliverable:** `08-ci-and-tools/` notes with screenshots of your Jira board and test run.

---

## Phase 4 — SQL (Week 6)

Backend verification is a standard interview question set.

- `SELECT`, `WHERE`, `ORDER BY`, `LIMIT`, `DISTINCT`
- `JOIN` (inner, left, right), `GROUP BY` + `HAVING`
- Aggregates: `COUNT`, `SUM`, `AVG`, `MIN`, `MAX`
- Subqueries, `IN` / `BETWEEN` / `LIKE` / `IS NULL`
- `INSERT` / `UPDATE` / `DELETE` and why QA needs them for test data setup

Practice: sqlzoo.net, HackerRank SQL (easy → medium), or a local SQLite/MySQL with a sample orders/customers schema.

**Deliverable:** `04-sql-and-databases/` with 25–30 solved queries and the schema you ran them against.

---

## Phase 5 — API testing (Week 7–8)

- HTTP basics: methods, status codes (2xx/4xx/5xx), headers, request/response body, JSON
- REST vs SOAP, authentication (Bearer token, Basic auth, API key)
- **Postman**: collections, environments, variables, chaining requests, writing assertions in the Tests tab, running a collection with Collection Runner, exporting a Newman run
- Practice APIs: https://reqres.in, https://jsonplaceholder.typicode.com, https://petstore.swagger.io
- Learn to read Swagger/OpenAPI docs

**Deliverable:** `05-api-testing-postman/` with an exported collection (`.json`), 20+ requests with assertions covering positive, negative and boundary cases, and a short results note.

---

## Phase 6 — Automation with Selenium + Python (Week 9–10)

You already write clear examples in Python style in your notes, so Python + pytest is a good fit (Java + TestNG is equally valid if local job listings ask for it).

- Python essentials: variables, lists/dicts, loops, functions, classes, exceptions, file I/O
- Selenium WebDriver: locators (id, name, CSS, XPath), waits (implicit vs explicit — know the difference), handling dropdowns, alerts, frames, multiple windows, screenshots
- **pytest**: fixtures, parametrize, markers, `conftest.py`, HTML reports
- **Page Object Model** — do not skip this; it is the most common automation interview question
- Data-driven testing from CSV/Excel

**Deliverable:** `06-automation-selenium-python/` — a small framework testing saucedemo.com: POM structure, 10–15 tests (login positive/negative, add to cart, checkout, sort), pytest fixtures, HTML report, README with how to run it.

---

## Phase 7 — Modern tooling + CI (Week 11)

- **Playwright** (Python or JS) or Cypress — write the same saucedemo suite again; it takes a day and it is what newer teams use
- **GitHub Actions** — run your test suite on every push, publish the report as an artifact
- Basic reporting: Allure or pytest-html

**Deliverable:** `07-playwright-or-cypress/` plus a green CI badge on this repo's README.

---

## Phase 8 — Interview prep & applying (Week 12)

- Write a **README.md** for this repo: what it is, what you learned, links to each project. Recruiters open the repo root first — right now it is empty.
- Résumé: one page, list the projects above as experience with concrete numbers ("wrote 80 test cases and logged 14 defects for an e-commerce web app")
- LinkedIn: same projects, repo link
- Rehearse the standard questions:
  - Severity vs Priority (with an example of each combination)
  - Smoke vs Sanity, Retesting vs Regression
  - Verification vs Validation
  - Explain the defect life cycle
  - Write test cases for: a login page / an ATM / a pen / a lift (say the technique out loud — EP, BVA, decision table)
  - What is a test plan? What goes in a bug report?
  - Explicit vs implicit wait; what is POM and why use it
  - 3–5 SQL queries on the spot
  - "You have 2 days to test a feature with no documentation — what do you do?"
- Apply to 5–10 internships per week; also try open-source bug bounties on GitHub issues labelled `bug` to get real reported-defect history

---

## Weekly rhythm that works

- 1.5–2 hours/day on the topic, 30 min hands-on
- Commit **every day** — a green contribution graph on a QA repo is itself a signal
- Keep your current note format (definition → simple explanation → real-world example → memory trick); it is genuinely good and readable

## Minimum bar to start applying

You are internship-ready once the repo shows:

1. Fundamentals + test design techniques (Phases 1)
2. One complete manual testing project with test cases and bug reports (Phase 2)
3. SQL basics (Phase 4)
4. A Postman collection with assertions (Phase 5)
5. One Selenium/Playwright suite using POM (Phase 6)
6. A README tying it all together

Items 1–4 alone already qualify you for most manual QA internships — start applying after Week 8 rather than waiting for the full 12 weeks.
