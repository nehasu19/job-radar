# Changelog

## [3.0.0] — 2026-11-01

### Added
- **Weekly digest:** a Sunday-evening scheduled task (`prompt/weekly-digest.md`) that sends the week's top 5 roles, jobs found vs last week, jobs waiting on you and progress. Read-only.
- **Cover-letter drafts:** a short, truthful cover letter (Claude Docs) next to each tailored resume, addressing the main gap honestly. Linked on each job as "Cover letter".
- **Closed-posting detection:** each daily run rechecks up to 12 New/Shortlisted jobs and flags taken-down postings with a "Posting closed" tag and filter. Status is never changed.
- **Tracker stats:** found this week, average match, applied, interviewing, waiting on you, postings closed, a jobs-per-week chart (last 6 weeks) and a Found → Interviewing progress funnel.

### Changed
- Data model: new `cover_url`, `closed` and `closed_checked_at` fields (see `docs/schema.md`).
- `job-radar/SKILL.md` and `job-radar.skill` updated to v3: cover-letter step, closed-posting check, weekly digest mode, TestDevJobs / Jobgether / Startup Insider sources, parent-company duplicate check. The skill now states its version.

### Fixed
- README and example scheduled-task prompt still described weekday-only runs; they now say every day, including weekends.
- README now explains how to set up the weekly digest.

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
