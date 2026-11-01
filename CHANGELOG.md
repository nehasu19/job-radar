# Changelog

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
