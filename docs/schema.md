# Data model

The tracker artifact's database has two collections.

## `config/profile` (owner-only)

| Field | Type | Notes |
|---|---|---|
| `name` | string | Full name, used in resume and cover-letter titles |
| `resume` | string | Full base resume, plain text |
| `roles` | string[] | Target roles |
| `locations` | string[] | Acceptable locations / remote rules |
| `german` | string | Language rule used for filtering |
| `availability` | string | Start date |
| `excluded_employers` | string[] | Never logged |
| `schedule` | string | Shown on the tracker |
| `resume_updated` | string | ISO date |
| `timezone` | string | Optional, for the weekly digest (default `Europe/Berlin`) |

## `jobs/<doc_id>`

`doc_id` = lowercase slug of company + title (letters, digits, hyphens; max 80 chars).

| Field | Type | Set by | Example / notes |
|---|---|---|---|
| `title` | string | daily run | Senior QA Automation Engineer |
| `company` | string | daily run | Example GmbH |
| `location` | string | daily run | Munich, Germany |
| `work_mode` | string | daily run | `On-site` \| `Hybrid` \| `Remote` |
| `url` | string | daily run | Posting URL |
| `source` | string | daily run | Job board or `Company site` |
| `posted` | string | daily run | `2026-10-23` or `~1 week ago` |
| `found_at` | string | daily run | ISO timestamp; drives the weekly chart |
| `score` | number | daily run | 0–100 |
| `german` | string | daily run | `Not required (English)`, `C1 required – stretch` |
| `why` | string | daily run | 1–2 sentences on fit |
| `gaps` | string | daily run | What's missing or risky |
| `resume_url` | string | daily run | Tailored resume (Claude Docs) |
| `cover_url` | string | daily run | Cover letter (Claude Docs) — **new in v3** |
| `closed` | boolean | daily run | `true` when the posting was taken down — **new in v3** |
| `closed_checked_at` | string | daily run | ISO timestamp of the last live check — **new in v3** |
| `status` | string | user | `new`, `shortlisted`, `applied`, `interview`, `offer`, `rejected`, `not-interested` |
| `status_changed` | string | tracker | Set when the user changes status |
