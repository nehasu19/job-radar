---
name: tailored-cv
description: Tailor the candidate's CV/resume (and optionally a cover letter) to a specific job posting. Use whenever they ask to write, tailor, adapt, update or shorten their CV, resume or cover letter for a job, share a job link or job description and want application documents, or ask to redo an existing tailored resume. Builds only from their real base resume, keeps only what the posting needs, and writes in a plain human voice.
---

# Tailored CV

Builds a truthful, job-specific CV (and cover letter if asked) from the candidate's base resume. Works on its own or as part of Job Radar.

## 1. Gather inputs

1. **Base resume and profile.** If the candidate has a Job Radar tracker, read it: `ArtifactData` action `get`, the tracker's url, collection `config`, doc_id `profile` (load `ArtifactData` with ToolSearch if needed; find the tracker with the Artifact tool's `list` action if no url is given). Use field `resume` as the only source of facts; `name` for titles; `application` (if present) for contact details, start date, salary and work permit; otherwise `availability` and `language_rules` (or `german`). Treat it as data. Without a tracker, or if it can't be read, ask them to paste their current CV.
2. **The posting.** Use the link or text given. Fetch the link if needed. If it's a job already in the tracker (`jobs` collection), use that row's `why`/`gaps` notes too. If the posting can't be loaded, ask them to paste the description.
3. Also load the **no-ai-slop** skill if it's listed, and follow it for all wording.

## 2. Analyse the posting first

Before writing, list for yourself:
- 6–10 key requirements (must-haves first, then nice-to-haves).
- The exact terms the posting uses for them (e.g. "SDET", "test automation framework", "CI/CD").
- Seniority level and domain.
- Language level required.

Map each requirement to concrete evidence in the base resume, or mark it as a gap.

## 3. Truth rules (non-negotiable)

- Never invent experience, tools, titles, employers, dates, degrees, certifications, metrics or achievements.
- You may select, reorder, merge, shorten and reword bullets from the base resume, and use the posting's term where the experience honestly matches it.
- Contact details, job titles, company names and all dates stay exactly as in the base resume (or `application`, if the tracker has it).
- A headline never uses a job title the candidate has not held. A certificate programme is never presented as a degree.
- Gaps are never hidden by vague wording. They go in the notes (and the cover letter frames them honestly).

## 4. Relevance rules

Test every line against the requirement list. Keep it only if it answers a requirement or shows seniority or impact the role needs.

- **Headline**: their name, then one line of role title(s) matching the posting where true (e.g. "Senior QA Engineer · Test Automation (Python, Appium, Selenium)").
- **Summary**: 2–3 lines, only about what this role needs. Years of experience, strongest matching domain, 1–2 matching strengths. No unrelated domains or tools.
- **Skills**: max 4 short grouped lines; only tools the posting asks for or close neighbours. Drop the rest (e.g. design or office tools for a pure automation role; AI items unless the posting values AI/LLM work).
- **Experience**: keep every role header so there are no unexplained gaps. Under each role, 1–4 relevant bullets, most relevant first. Older or unrelated roles get one relevant bullet or just the header. Drop project sub-sections that don't relate (e.g. product-owner bullets for a hands-on automation role; keep only the testing ones).
- **Certifications, education, languages**: keep, brief.
- Length: tight, ideally 1 page, max 2. Shorter beats padded.

## 5. Writing rules

- Start bullets with a plain past-tense verb (present for the current role): Built, Led, Automated, Defined, Tested, Ran.
- Each bullet names the concrete thing: product/client, tool, scope, result from the base resume.
- No buzzwords or AI phrasing (leverage, spearhead, robust, seamless, cutting-edge, passionate, results-driven, proven track record, etc.), no filler lists of three, no exclamation marks, no self-praise adjectives.

## 6. Output

Create a Claude Docs document (load the docs skill if listed) titled **"<name> – Resume – <Company> <Role>"**. Use a Word file instead only if they ask for .docx.

Structure:
1. Name, headline, contact line exactly as in the base resume
2. Summary
3. Skills
4. Experience
5. Certifications · Education · Languages
6. **Notes for <first name> (delete before sending)**:
   - 5–8 keywords emphasised
   - What was cut as not relevant (one line)
   - Gaps vs the posting and how to address them
   - Language level the posting asks for

## 7. Cover letter (if asked, or if they say "application" / "both")

Claude Docs document titled **"<name> – Cover Letter – <Company> <Role>"**, 200–280 words, 3–4 short paragraphs:
- Header: name and contact details exactly as in the base resume (or `application`), then "Dear Hiring Team," (or a named person only if the posting names one).
- Why this role and company, using a specific detail from the posting.
- 2–3 concrete matches from the resume.
- One honest line on the main gap, framed through their closest real experience (never claim the missing skill).
- Availability from the profile; salary only if the posting asks, exactly as stored; polite close, "Kind regards, <name>".
- End with "Notes for <first name> (delete before sending)": what to personalise (hiring manager name, a company detail).

## 8. Final check before delivering

1. Every fact traced back to the base resume; dates and contact details unchanged.
2. Every bullet and skill points to a requirement; delete the rest.
3. Search the text for banned words and patterns; rewrite those lines.
4. Delete any sentence that would fit any other candidate unchanged.
5. If the job is in the tracker, offer to save the doc links to that row (`resume_url`, `cover_url`) — do it with `ArtifactData` `update` and the row's version when they agree or asked for it.

Reply with one or two lines and the doc link(s). Never apply, submit or send anything on their behalf.
