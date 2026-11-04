# Data model

The tracker artifact's database has two collections.

## `config/profile` (owner-only)

See [`examples/profile.example.json`](../examples/profile.example.json) for a filled-in example.

| Field | Type | Required | Notes |
|---|---|---|---|
| `name` | string | yes | Full name, used in resume and cover-letter titles |
| `resume` | string | yes | Full base resume, plain text |
| `roles` | string[] | yes | Target roles |
| `locations` | string[] | yes | Acceptable locations / remote rules |
| `language_rules` | string | yes | Languages you can work in and what to skip or flag as "stretch". Older trackers may use `german` instead; both are read |
| `availability` | string | yes | Notice period / start date |
| `excluded_employers` | string[] | yes | Never logged (e.g. current employer) |
| `target_companies` | string[] | no | Career pages to check directly |
| `domains` | string[] | no | Industries to favour in search and scoring |
| `key_skills` | string[] | no | Skills to weigh more heavily in scoring |
| `timezone` | string | no | IANA zone for the weekly digest; default `Europe/Berlin` |
| `min_score` | number | no | Minimum score to log a job; default 60 |
| `resume_min_score` | number | no | Minimum score for a tailored resume and cover letter; default 75 |
| `max_age_days` | number | no | Skip postings older than this; default 21 |
| `max_new_per_run` | number | no | New jobs added per run; default 10 |
| `max_closed_checks` | number | no | Open jobs rechecked for closure per run; default 12 |
| `schedule` | string | no | Shown on the tracker |
| `resume_updated` | string | no | ISO date |

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
