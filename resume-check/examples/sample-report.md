<!-- Output of resume-check on examples/sample-resume.md against examples/sample-posting.md. Fictional data. The short report is what the candidate sees by default; the full report appears when they ask for it. -->

# Short report (default)

```
Resume score: 71/100 – good, fix the top items
Checked 85 of 100 points (text only, so the file and layout checks were skipped)
Job match: 88% – 4 of 6 must-haves found, 2 partly

Top 3 fixes
1. Quick fixes: one date format ("Mar 2021 – Present"), "Excuted" → "Executed",
   "MY TOOLBOX" → "Skills", add your LinkedIn URL, use an email without "1994" (+7)
2. Headline "Senior QA Engineer · Test Automation (Java, Selenium, Rest Assured)"
   and a summary without "results-driven", "passionate" or "team player" (+4)
3. Start 6 bullets with a plain verb instead of "Responsible for", "Worked on",
   "Helped with" or "Involved in" (+4)

Rewrites
- Before: Responsible for regression testing.
  After: Ran regression testing for [N] releases a [month], catching [N] release-blocking bugs in [year].
- Before: Worked on API testing using Postman and Rest Assured.
  After: Wrote API tests in Postman and Rest Assured covering [N] endpoints.
- Before: Responsible for testing the mobile payments app on Android and iOS.
  After: Tested the Android and iOS payments app before each release, covering [N] payment flows.
  (If you used Appium here, name it. It's a must-have.)

Gaps for the cover letter, not the resume: Playwright (you have Selenium, which
the posting will consider), a test strategy you owned, and leading a team of SDETs.

Upload the PDF or DOCX you send to employers and I'll check whether an ATS can read it.
Say "full report" for every check, the keyword table and more rewrites.
```

---

# Full report (on request)

## Ananya Example – Resume check – NovaPay Lead SDET

**Resume score: 71/100 – good, fix the top items.** Checked 85 of 100 points. The resume was text only, so the 15 points for file and layout checks were skipped.
**Job match: 88%.** 4 of 6 must-have skills found, 2 partly (Playwright, test strategy). Must-haves count double.

This is a checklist score, not the number an employer's system will give. There is no universal ATS score, and most systems rank and filter resumes for a recruiter rather than reject them automatically.

### Top fixes

1. **Quick fixes (+7).** Write every date the same way ("Mar 2021 – Present"). Fix "Excuted" → "Executed". Rename "MY TOOLBOX" to "Skills". Add your LinkedIn URL. Use an email address without "1994", since it reads like a birth year.
2. **Headline and summary (+4).** Change "QA Engineer" under your name to **"Senior QA Engineer · Test Automation (Java, Selenium, Rest Assured)"**. That's the title you hold now. Replace the summary with the version under Suggested rewrites, which drops "results-driven", "passionate" and "team player".
3. **Bullet openers (+4).** 6 of 11 bullets start with "Responsible for", "Worked on", "Helped with" or "Involved in". "Responsible for" starts 3 of them.
4. **Numbers (+4).** 2 of the 10 bullets in your last two roles have a number or frequency. Fill in the `[ ]` placeholders in the rewrites with your real figures, or delete the clause.
5. **Back up or cut skills (+3).** Appium is a must-have but appears only in your skills list. If you used it at PayKart, say so in a bullet; otherwise leave it as it is. The other 8 skills that appear in no bullet (JMeter, SQL, Docker, Git, Cypress, Kubernetes, AWS, Python): back each with a bullet, or cut the ones you couldn't talk about in an interview.

If you apply all five, the score comes to about 95. Leading a team and a test strategy you owned stay as gaps. Playwright stays partly met: you have Selenium, which the posting will consider. Address these in the cover letter, not the resume.

### Category scores

| Category | Points | Worst finding |
|---|---|---|
| A. ATS essentials | Not checked | No file (PDF or DOCX) to test |
| B. Contact and header | 3.3 / 5 | No LinkedIn URL |
| C. Sections and order | 9.0 / 10 | "MY TOOLBOX" isn't a standard heading |
| D. Content quality | 12.5 / 25 | 2 of 10 recent bullets have a number or frequency |
| E. Job match | 22.5 / 30 | Leading a team not shown |
| F. Recruiter review | 9.2 / 10 | 9 skills in no bullet, including Appium |
| G. Bias and gaps | 4.2 / 5 | 7-month gap (Jun–Dec 2017) with no explanation |
| **Total** | **60.7 / 85 → 71** | |

### Keyword match

The first ten rows are hard skills (E1) and make up the 88%. The last two feed checks E2 and E6.

| Term | Must / Nice | Status | Where | Action |
|---|---|---|---|---|
| Java | Must | Found | PayKart bullet 2, skills | Keep. Also put it in the headline |
| Playwright (TypeScript) | Must | Partly | – (Selenium, which the posting will consider) | Mention Selenium as your alternative in the cover letter. Add Playwright only if you've used it |
| Appium | Must | Found | Skills list only | If you used it at PayKart, name it in the mobile app bullet |
| Rest Assured | Must | Found | PayKart bullet 3 | Keep |
| CI/CD (Jenkins or GitHub Actions) | Must | Found | "nightly test runs in Jenkins" | Write "CI" next to Jenkins so the posting's term appears too |
| Test strategy for payments | Must | Partly | "test plans" (ShopEasy), payments app (PayKart) | Only if you decided how PayKart's app is tested, write "Defined the test strategy for …" |
| JMeter | Nice | Found | Skills list only | Add a bullet if you used it |
| Docker | Nice | Found | Skills list only | Same |
| SQL | Nice | Found | Skills list only | Same |
| ISTQB | Nice | Found | Certifications | Keep |
| Leading and mentoring SDETs | Must | Partly | "Mentored 3 junior testers" | Gap: no team-lead role yet. Show any planning, reviews or task assignment you really did |
| 8+ years incl. 2+ leading automation | Must | Partly | Dates add up to 9+ years | Say "9+ years". The leadership part is a gap |

### Findings by category

**A. ATS essentials** – Not checked (A1–A6). Upload the PDF or DOCX you actually send to test the file type, size, file name, layout, parse rate and hidden text.

**B. Contact and header**
- B1 Warn – 4 of 5 details present; no LinkedIn URL. Fix: add `linkedin.com/in/<you>` to the contact line.
- B2 Warn – "1994" in the email reads like a birth year. Fix: use a name-only address.
- B3 N/A – no links in the resume (the missing LinkedIn URL is counted in B1).
- B4 Pass – no photo, date of birth or ID numbers.

**C. Sections and order**
- C1 Pass – summary, skills, experience, education and certifications are all there.
- C2 Warn – 1 non-standard heading: "MY TOOLBOX". Fix: "Skills".
- C3 Pass – everything is on page one.
- C4 Pass – about 175 words, one page (estimated at 475 words per page).
- C5 Pass – roles are in reverse chronological order.

**D. Content quality**
- D1 Fail – 2 of 10 bullets (20%) in the last two roles are quantified: "3 junior testers" and "nightly". Fix: rewrites 2–5 below.
- D2 Warn – 6 of 11 bullets open with a weak phrase (threshold: 2). Fix: start each with a plain verb.
- D3 Warn – "Responsible for" starts 3 bullets. Note: "testing" is used often, which is normal for a tester and doesn't affect the mark.
- D4 Warn – 1 typo: "Excuted" (Infotech bullet).
- D5 Pass – bullets run 4–13 words, and no role has 8 or more.
- D6 Warn – 2 date formats across roles: "03/2021" next to "Jan 2018". Fix: "Mar 2021 – Present". Note: Atlassian writes "Jira", not "JIRA".
- D7 Warn – 3 vague claims: "Results-driven", "Passionate about quality", "strong team player". Fix: new summary below.

**E. Job match**
- E1 Pass – 88%. Must-haves: 4 found, 2 partly (5 of 6, counted double). Nice-to-haves: 4 of 4.
- E2 Warn – 1 of 3 soft skills shown: mentoring ("Mentored 3 junior testers"). Leading a team and working with product and engineering leads aren't shown. UAT with business users is a different thing, and "team player" is an adjective, not evidence.
- E3 Warn – the headline says "QA Engineer", but your current title is Senior QA Engineer. Fix: "Senior QA Engineer · Test Automation (Java, Selenium, Rest Assured)". Don't use "Lead" or "SDET", since you haven't held either title.
- E4 Warn – 1 must-have is in the skills list only: Appium.
- E5 Pass – no hard-skill term appears more than 4 times (Selenium 3), and the summary isn't copied from the posting.
- E6 Warn – 9+ years meets the ask. The 2+ years leading test automation aren't shown, and Senior is one level below Lead.
- E7 Pass – the degree and location match.

**F. Recruiter review**
- F1 Pass – the claims fit the titles and dates.
- F2 Pass – no metric without context, and no claim the rest of the resume contradicts.
- F3 Warn – 9 skills appear in no bullet: Appium (a must-have), JMeter, SQL, Docker, Git, Cypress, Kubernetes, AWS, Python. Fix: back Appium with a bullet if you used it (never cut a must-have); back or cut the other 8.
- F4 Pass – Junior → QA → Senior.
- F5 Pass – 2 kinds of leadership signal: mentoring ("Mentored 3 junior testers"), and setting up a framework or process ("Built a Selenium and TestNG framework", "Set up nightly test runs").
- F6 Pass – 1 role under a year (the first job), not several.
- F7 Not checked – no LinkedIn text provided.

**G. Bias and gaps**
- G1 Warn – 7 months (June–December 2017) between Infotech and ShopEasy. Fix: add one honest line, for example "Career break – relocation to Bengaluru", if that's what happened. It's your call.
- G2 Pass – no age signals.
- G3 Pass – no sensitive personal details.

### Suggested rewrites

Placeholders in `[ ]` are for you to fill in or delete. Each rewrite keeps your level of ownership.

**Headline**
- Before: QA Engineer
- After: Senior QA Engineer · Test Automation (Java, Selenium, Rest Assured)

**Summary**
- Before: Results-driven QA professional with 8+ years of experience in manual and automation testing. Passionate about quality and a strong team player.
- After: Senior QA Engineer with 9+ years in testing, the last 5 in fintech at PayKart. Builds test automation in Java with Selenium, TestNG and Rest Assured, runs it in Jenkins, and mentors junior testers.

**Bullets**
1. Before: Responsible for testing the mobile payments app on Android and iOS.
   After: Tested the Android and iOS payments app before each release, covering [N] payment flows.
   *If you used Appium here, name it. It's a must-have for this job.*
2. Before: Built a Selenium and TestNG framework in Java for the merchant web portal.
   After: Built a Java, Selenium and TestNG framework for the merchant web portal, now running [N] tests and cutting regression time from [X] to [Y] days.
3. Before: Worked on API testing using Postman and Rest Assured.
   After: Wrote API tests in Postman and Rest Assured covering [N] endpoints.
4. Before: Responsible for regression testing.
   After: Ran regression testing for [N] releases a [month/quarter], catching [N] release-blocking bugs in [year].
5. Before: Set up nightly test runs in Jenkins.
   After: Set up nightly CI runs of [N] test suites in Jenkins.
6. Before: Helped with automation of checkout flows using Selenium.
   After: Co-wrote [N] Selenium tests for the checkout flow.
   *Write "Automated" only if you wrote them yourself.*
7. Before: Involved in UAT with business users.
   After: Supported UAT with business users for [N] releases.
8. Before: Responsible for manual testing of the e-commerce website.
   After: Tested the e-commerce website manually across [N] releases, logging defects in JIRA.

### Not checked

- **A1–A6 (file and layout):** upload the PDF or DOCX you send to employers.
- **F7 (LinkedIn match):** paste your LinkedIn profile text if you want it compared.

### Next step

I can (a) apply the fixes you accept to a revised resume, (b) tailor it for this NovaPay posting with tailored-cv, or (c) check it again after your edits.
