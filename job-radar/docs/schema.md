# Job Radar data schema (v4)

The tracker is an artifact page with a `db` capability. Two collections are used: `config` (one document, `profile`) and `jobs` (one document per job). The page's db rule keeps `config` readable and writable by the owner only.

## `config/profile`

| Field | Type | Required | Notes |
|---|---|---|---|
| `name` | string | yes | Full name, used in document titles |
| `resume` | string | yes | Full base resume as plain text. The only source for tailored documents. |
| `resume_updated` | string (ISO date) | no | Shown on the tracker |
| `roles` | string[] | yes | Target roles |
| `locations` | string[] | yes | Places or remote rules, e.g. "Munich area", "Remote within Germany", "London", "Remote – EU timezones" |
| `home_country` | string | yes | ISO 3166 alpha-2, e.g. "DE" |
| `timezone` | string | yes | IANA, e.g. "Europe/Berlin", "Asia/Kolkata", "America/Toronto" |
| `week_start` | string | no | "monday" (default) or "sunday" / "saturday" for the weekly digest |
| `date_format` | string | no | e.g. "DD.MM.YYYY", "DD/MM/YYYY", "MM/DD/YYYY", "YYYY-MM-DD"; default from `cv_style` |
| `languages` | object[] | yes | `{lang: "German", level: "B1", can_write_applications: false}`; level is A1–C2 or "native" |
| `language_policy` | string | no | Free text: what to include / flag as stretch / skip |
| `work_rights` | object | yes | `{authorised: string[], needs_sponsorship_for: string[], notes: string}` – see `references/work-rights.md` |
| `salary` | object | no | `{amount: number, currency: "EUR", period: "year"\|"month"\|"day"\|"hour", basis: "gross"\|"net"}` |
| `salary_display` | string | no | How to write the salary in letters, e.g. "EUR 85,000 gross per year" |
| `cv_style` | string | no | Key from `references/cv-conventions.md` |
| `availability` | string | no | Notice period / start date |
| `excluded_employers` | string[] | no | Never add jobs from these |
| `target_companies` | string[] | no | Careers pages always searched |
| `key_skills`, `domains` | string[] | no | Help search terms and scoring |
| `boards` | string[] | no | Extra boards to always search |
| `contract_ok` | boolean | no | Whether contractor/freelance roles are acceptable (default false) |
| `min_score` | number | no | Default 60 |
| `resume_min_score` | number | no | Default 75 |
| `max_age_days` | number | no | Default 21 |
| `max_new_per_run` | number | no | Default 10 |
| `max_closed_checks` | number | no | Default 12 |
| `schedule` | string | no | Free text shown on the tracker |
| `application` | object | no | Application details – see below |

### `application` (edited on the tracker page)

| Field | Example |
|---|---|
| `full_name` | "Alex Example" |
| `email` | "alex@example.com" |
| `phone` | "+44 7700 900000" |
| `linkedin` | "https://www.linkedin.com/in/…" |
| `location` | "London, United Kingdom" |
| `work_rights_summary` | "Right to work in the UK (settled status)" |
| `visa_sponsorship` | "No" / "Yes, for the US" |
| `salary` | "GBP 70,000 per year" |
| `current_job_ends` | "31 March 2027" |
| `earliest_start` | "1 April 2027" |
| `languages_summary` | "English native, Spanish B2" |

### Accepted v3 fields (read, never required)

| v3 field | Read as |
|---|---|
| `german`, `language_rules` | `language_policy` (+ derive `languages` from resume) |
| `work_permit`, `application.work_permit` | `work_rights` / `application.work_rights_summary` |
| `salary_expectation`, `application.salary` (text) | `salary` (parsed) / `salary_display` |
| `application.german`, `application.english` | `application.languages_summary` |
| no `timezone` | timezone of `home_country` or first location |

## `jobs/<doc_id>`

`doc_id`: lowercase ASCII slug of company + title, letters/digits/hyphens, max 80 chars.

| Field | Type | Set by | Notes |
|---|---|---|---|
| `title` | string | run | As posted |
| `company` | string | run | Hiring company; note the aggregator if the employer is hidden |
| `location` | string | run | "City, Country" |
| `country` | string | run | ISO alpha-2 (v4+) |
| `work_mode` | string | run | "On-site" \| "Hybrid" \| "Remote" |
| `url` | string | run | Prefer the employer's own posting |
| `source` | string | run | Board or site found on |
| `posted` | string | run | ISO date if known, else posting wording, or "Date not shown" |
| `found_at` | string | run | ISO timestamp (UTC) |
| `score` | number | run | 0–100 |
| `language_required` | string | run | e.g. "English only", "French B2 nice to have" (v3: `german`) |
| `work_auth` | string | run | See `references/work-rights.md` (v4+) |
| `salary` | string | run | As posted, with currency and period, or "" (v4+) |
| `why` | string | run | 1–2 sentences |
| `gaps` | string | run | Short |
| `status` | string | candidate | "new" \| "shortlisted" \| "applied" \| "interview" \| "offer" \| "rejected" \| "not-interested". Runs only set "new" on creation. |
| `status_changed` | string | page | ISO timestamp, written by the tracker page |
| `resume_url`, `cover_url` | string | run | Tailored documents |
| `closed` | boolean | run | Posting taken down |
| `closed_checked_at` | string | run | ISO timestamp of the last check |
