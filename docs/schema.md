# Data model

The tracker artifact's database has two collections.

## `config/profile` (owner-only)

| Field | Type | Notes |
|---|---|---|
| `resume` | string | Full base resume, plain text |
| `roles` | string[] | Target roles |
| `locations` | string[] | Acceptable locations / remote rules |
| `german` | string | Language rule used for filtering |
| `availability` | string | Start date |
| `excluded_employers` | string[] | Never logged |
| `schedule` | string | Shown on the tracker |
| `resume_updated` | string | ISO date |

## `jobs/<doc_id>`

`doc_id` = lowercase slug of company + title (letters, digits, hyphens; max 80 chars).

| Field | Type | Example |
|---|---|---|
| `title` | string | Senior QA Automation Engineer |
| `company` | string | Example GmbH |
| `location` | string | Munich, Germany |
| `work_mode` | string | `On-site` \| `Hybrid` \| `Remote` |
| `url` | string | Posting URL |
| `source` | string | Job board or `Company site` |
| `posted` | string | `2026-10-23` or `~1 week ago` |
| `found_at` | string | ISO timestamp |
| `score` | number | 0–100 |
| `german` | string | `Not required (English)`, `B2 nice to have`, `C1 required – stretch` |
| `why` | string | 1–2 sentences on fit |
| `gaps` | string | What's missing or risky |
| `status` | string | `new`, `shortlisted`, `applied`, `interview`, `offer`, `rejected`, `not-interested` (user-managed) |
| `resume_url` | string | Optional link to the tailored resume |
| `status_changed` | string | Set by the tracker when you change status |
