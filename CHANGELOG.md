# Changelog

## [4.1.0] — 2026-11-10

New companion skill: resume-check. Job Radar itself is unchanged.

### Added
- **`resume-check/`** (plus `resume-check.skill`): scores a resume 0–100 against 39 ATS and recruiter checks in seven areas (file and parsing, contact, sections, content, job match, recruiter red flags, bias and gaps). With an uploaded PDF or DOCX it tests what an ATS can read; with a posting it scores the keyword match, counting must-haves double. Fixes are ranked by points gained, and rewrites use placeholders for numbers instead of inventing them. Missing skills are reported as gaps, never added. Shows a short report by default and the full report on request. Works on its own or reads the resume from the Job Radar tracker, and hands accepted fixes to `tailored-cv`.
- `resume-check/examples/`: a fictional resume, job posting and the resulting report.
- README: a "Which skill do I use?" guide and a tip to upload the file you actually send.

## [4.0.0] — 2026-11-05

Global release: Job Radar now works for candidates in any country. Existing v3 trackers and profiles keep working unchanged.

### Added
- `job-radar/references/job-boards.md`: job boards for Europe, the Americas, Asia-Pacific, the Middle East and Africa, plus global remote and specialist boards, and tips for local-language queries.
- `job-radar/references/cv-conventions.md`: CV and cover-letter norms by market (length, photo and personal data, date format, spelling, greeting, closing).
- `job-radar/references/work-rights.md`: how to read work-authorisation lines in postings and match them to the profile.
- `job-radar/examples/profiles.md`: sample profiles for Berlin, London, Bengaluru, Toronto and Dubai.
- Profile fields: `home_country`, `languages` (list with CEFR levels), `language_policy`, `work_rights`, `salary` (amount, currency, period, basis), `salary_display`, `cv_style`, `week_start`, `date_format`, `boards`, `contract_ok`.
- Job fields: `country`, `language_required`, `work_auth`, `salary`.
- Tracker page: title taken from the profile, generic "Language" and "Work rights" tags, salary tag, a country filter when jobs span several countries, week start from the profile, dates in the viewer's locale, and a search-profile panel showing languages, work rights, salary and time zone.

### Changed
- **The tracker page, data schema and scheduled-task prompts now ship inside the skill** (`job-radar/tracker/`, `job-radar/docs/`, `job-radar/prompt/`), so `job-radar.skill` contains everything the skill refers to. They moved from the repository root.
- Search picks boards per target market and queries in English plus each market's local language.
- Scoring checks every required language against the profile, applies work-rights rules, and compares salaries only in the same currency and period (no currency conversion).
- Tailored documents follow the job market's CV convention and are written in the posting's language only when the candidate can write applications in it.
- `timezone` is required for new profiles (no Europe/Berlin default).
- Setup asks for country, time zone, languages, work rights and salary currency, and reminds the user that each person keeps their own tracker.
- The closed-posting check recognises closed / expired / archived / filled wording in any language, and treats an aggregator copy as closed when the employer's original is.
- Scheduled-task prompts load the skill instead of repeating its steps, so they stay in sync with it.
- `examples/profile.example.json` uses the v4 fields.

### Compatibility
- v3 fields (`german`, `language_rules`, `work_permit`, `salary_expectation`, `application.german`, `application.english`, `application.work_permit`) are still read. Profiles are not rewritten unless the user asks.
- Jobs with `german` show a "German:" tag; new jobs use `language_required`.
- A v3 tracker page keeps working with v4 data; republishing `job-radar/tracker/index.html` is optional.

## [3.3.0] — 2026-11-04

Versions 3.1 and 3.2 were never released; their changes are included here.

### Added
- **Application details:** optional `application` block in `config/profile` (name, email, phone, LinkedIn, location, work permit, visa sponsorship, salary, current job end, earliest start, German, English). The tracker shows it as "Application details" with a Copy button per field and lets you edit it. Documented in `docs/schema.md` and `examples/profile.example.json`.
- Tracker job cards show what to upload for each job (tailored resume and cover letter, or the base resume).
- **Companion skills:** `tailored-cv/` and `no-ai-slop/` (plus `tailored-cv.skill` and `no-ai-slop.skill`). `tailored-cv` tailors a resume and cover letter to one posting from the base resume in the tracker profile; `no-ai-slop` is the wording and style pass. Both work on their own too.

### Changed
- The skill reads `application` fresh on every run. Cover-letter headers, availability, salary (only when the posting asks) and work-authorisation lines come from it; resume notes compare the posting's salary and start date against it.
- Scoring: roles requiring EU work authorisation are fine when `visa_sponsorship` is "No"; postings with a stated salary clearly below `application.salary` are kept with a slightly lower score and the salary noted in `gaps`.
- Resume and cover-letter drafting loads the `tailored-cv` and `no-ai-slop` skills when they are installed and does a final relevance and style pass before saving.

## [3.0.1] — 2026-11-04

### Fixed
- **The skill itself now has the v3 features.** In 3.0.0 only the tracker, prompts and docs were updated; `job-radar/SKILL.md` and `job-radar.skill` were still v2. They now include the cover-letter step, the closed-posting check, the weekly digest mode, the TestDevJobs / Jobgether / Startup Insider sources and the parent-company duplicate check. The skill states its version.
- The skill description no longer contains angle brackets, which the Claude skill uploader rejected.
- `prompt/job-radar-routine.md` no longer hard-codes one person's language rules, scoring angle and thresholds; everything comes from the profile. The weekly digest uses the profile's timezone.
- `docs/schema.md` and `examples/profile.example.json` now list the same profile fields, including `key_skills`, `timezone` and `max_closed_checks`.
- README and the example scheduled-task prompt described weekday-only runs; they now say every day, including weekends. The README explains how to set up the weekly digest and removes a duplicated section.
- CHANGELOG: removed a duplicated 3.0.0 entry.

## [3.0.0] — 2026-11-01

### Added
- **Weekly digest:** a Sunday-evening scheduled task (`prompt/weekly-digest.md`) that sends the week's top 5 roles, jobs found vs last week, jobs waiting on you and progress. Read-only.
- **Cover-letter drafts:** a short, truthful cover letter (Claude Docs) next to each tailored resume, addressing the main gap honestly. Linked on each job as "Cover letter".
- **Closed-posting detection:** each daily run rechecks up to 12 New/Shortlisted jobs and flags taken-down postings with a "Posting closed" tag and filter. Status is never changed.
- **Tracker stats:** found this week, average match, applied, interviewing, waiting on you, postings closed, a jobs-per-week chart (last 6 weeks) and a Found → Interviewing progress funnel.

### Changed
- Data model: new `cover_url`, `closed` and `closed_checked_at` fields (see `docs/schema.md`).

## [2.0.0] — 2026-11-01

### Changed
- Runs **every day, including weekends** (was weekdays only), so new roles are in the tracker before Monday.
- Tracker copy updated from "weekday search" to "daily search".
- Search sources documented, including Arbeitnow, Built In, TestDevJobs, Jobgether and Startup Insider.

### Improved
- Duplicate detection across job boards that list the same role under a parent company name.
- Clearer notes when a posting or site can't be reached, so it is retried on the next run.

## [1.0.0] — 2026-10-30

### Added
- Weekday scheduled job search across German and international job boards and company career pages.
- 0–100 match scoring against the base resume, with German-language rules.
- Live tracker with status filters (New, Shortlisted, Applied, Interviewing, Offer, Rejected, Not interested).
- Truthful tailored resumes as Claude Docs for top matches (score ≥ 75), with a private notes section.
- Short daily report and push notification.
