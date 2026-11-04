# Changelog

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
