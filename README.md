# Job Radar – a Claude skill for job searching

Job Radar is a [Claude](https://claude.ai) skill that runs a personal job search for you, in any country:

- searches the right job boards for **your** markets (about 40 countries plus remote boards) and company career pages, in English and the local language
- opens each posting to check it is still live and recent
- scores each job 0–100 against your resume (role, skills, domain, location, languages, work rights, salary in your currency)
- saves good matches to your own **Job Radar tracker**, without duplicates
- drafts **truthful** tailored resumes and cover letters for the best matches, following the local CV style (photo or not, length, date format, greeting)
- flags postings that have been taken down, and sends you a weekly digest

It **never** applies to jobs, fills in forms or contacts anyone. You stay in control.

## What you need

- A Claude plan with skills and artifacts enabled (claude.ai or the Claude app)
- Web search enabled
- Optional: Claude Docs (for tailored resumes and cover letters as editable documents)
- Recommended: the `tailored-cv` and `no-ai-slop` skills included here; Job Radar follows them when it drafts resumes and cover letters, and falls back to its own rules without them
- Optional: scheduled tasks, to run the search every morning and send the weekly digest

## Install

1. Download this repository (green **Code** button → **Download ZIP**), or download `job-radar.skill` from the [latest release](https://github.com/nehasu19/job-radar/releases/latest) (or from the repository root).
2. In Claude, go to **Settings → Capabilities → Skills** and upload the `job-radar` folder (zipped) or the `.skill` file.
   If your organisation manages skills, ask your admin to add it.
3. Recommended: upload `tailored-cv.skill` and `no-ai-slop.skill` the same way. They are the companion skills Job Radar uses for resumes and cover letters, and you can also use them on their own ("tailor my CV for this job", "make this cover letter sound less like AI").

| Skill | What it does |
|---|---|
| `job-radar` | Finds and scores jobs, keeps the tracker current, drafts application documents |
| `tailored-cv` | Tailors a resume (and cover letter) to one posting, using only facts from your base resume |
| `no-ai-slop` | Strips buzzwords, filler and AI-sounding phrasing from anything you'll send as your own |

## First run

Say to Claude:

> Set up Job Radar for me

Claude will ask for your resume, target roles, locations, home country, time zone, languages, where you can work (and where you'd need a visa), salary expectation with currency, availability and any employers to exclude, then create your tracker page. See [`examples/profile.example.json`](examples/profile.example.json) for the profile fields and [`job-radar/examples/profiles.md`](job-radar/examples/profiles.md) for filled-in examples from Berlin, London, Bengaluru, Toronto and Dubai.

**One tracker per person.** Your tracker holds your resume and contact details. To let a friend or colleague use Job Radar, share the skill, not your tracker – they run "Set up Job Radar for me" and get their own.

## Everyday use

| You say | What happens |
|---|---|
| "Run job radar" | Full search: closed postings flagged, new jobs scored and added to your tracker, tailored resumes and cover letters for the best ones |
| "Add this job to my tracker" + a link or pasted posting | Checks and scores that one job |
| "Tailor my resume for the <company> job" | Writes a tailored resume and cover letter for a job already in your tracker |
| "Write a cover letter for the <company> job" | Writes just the cover letter |
| "Check for closed postings" | Rechecks open jobs and flags the ones that were taken down |
| "Send my weekly digest" | The weekly summary, on demand |

## Run it automatically

**Daily search.** Ask Claude: *"Create a scheduled task that runs Job Radar every day at 8:45"* (in your own time zone). It runs on weekends too, so new roles are in your tracker before your week starts. A short prompt is in [`examples/scheduled-task-prompt.md`](examples/scheduled-task-prompt.md); the full version is [`job-radar/prompt/job-radar-routine.md`](job-radar/prompt/job-radar-routine.md).

**Weekly digest.** Ask Claude: *"Create a scheduled task at the end of my week using the prompt in job-radar/prompt/weekly-digest.md"*, with your tracker link filled in. It is read-only and sends you the week's top 5 roles, jobs found vs last week, jobs still waiting on you and your progress. If your week runs Sunday–Thursday, set `week_start` to `sunday` in your profile. The prompt is in [`job-radar/prompt/weekly-digest.md`](job-radar/prompt/weekly-digest.md).

## LinkedIn

LinkedIn blocks automated reading of its pages, and Job Radar respects that. Instead, set up LinkedIn **job alerts** sent to your email, connect your email to Claude, and ask Job Radar to include those alerts – it then checks each job on the company's own careers page.

## Principles

- **Truthful resumes and cover letters:** only your real experience, reordered and reworded – never invented skills, titles, dates or degrees.
- **No actions on your behalf:** no applications, no messages, no form submissions.
- **Your data stays yours:** your profile and jobs live in your own private tracker.

## What's inside

| Path | What it is |
|---|---|
| `job-radar/SKILL.md` | The skill |
| `job-radar/tracker/index.html` | The tracker page Claude publishes at setup |
| `job-radar/docs/schema.md` | Every profile and job field |
| `job-radar/references/` | Job boards by country, CV conventions by market, work-rights rules |
| `job-radar/prompt/` | Scheduled-task prompts (daily run, weekly digest) |
| `job-radar/examples/profiles.md` | Example profiles for several countries |
| `tailored-cv/`, `no-ai-slop/` | Companion skills |
| `*.skill` | Ready-to-upload packages of each skill |

## Contributing job boards and CV norms

Job boards and hiring customs change. If a board in [`job-radar/references/job-boards.md`](job-radar/references/job-boards.md) or a row in [`job-radar/references/cv-conventions.md`](job-radar/references/cv-conventions.md) is out of date for your country, open an issue or pull request.

## Licence

MIT – see [LICENSE](LICENSE).

## What's new in v4.0.0

- **Works in any country.** Boards for about 40 countries plus remote and specialist boards; searches in English and the local language.
- **Languages, work rights and salary for anyone:** a list of languages with levels, where you can work and where you'd need sponsorship, and a salary with currency. Jobs you can't legally take are skipped; salaries are only compared in the same currency.
- **Local CV style:** tailored resumes and cover letters follow the job market's norms (photo, length, date format, spelling, greeting).
- **Everything ships in the skill:** the tracker page, schema and prompts now live in `job-radar/` and are included in `job-radar.skill`.
- **Tracker:** country filter, language and work-rights tags, your name in the title, your own week start.
- **Upgrading from v3:** nothing breaks. Old profiles and trackers keep working; Claude offers once to move your profile to the new fields.

See [CHANGELOG.md](CHANGELOG.md) for details.

## What's new in v3.3.0

- **Application details** on the tracker: your contact details, work permit, visa needs, salary expectation and start date, with a Copy button per field for pasting into application forms. Edit them on the page.
- Cover letters take their header, start date, salary and work-permit lines from those details, so they always match what you put in forms.
- Scoring knows whether you need visa sponsorship, and lowers the score a little when a posting's salary is clearly below your expectation.
- **Two companion skills included:** `tailored-cv` (tailors a resume and cover letter to one posting) and `no-ai-slop` (plain, human wording). Job Radar uses them when they're installed.
- Each job card says what to upload: the tailored resume and cover letter, or your base resume.

See [CHANGELOG.md](CHANGELOG.md) for details.

## What's new in v3.0.1

- Fixes the skill file so it actually includes the v3 features (cover letters, closed-posting check, weekly digest), and it now uploads to Claude without errors
- The daily task prompt now uses your own profile for language rules and thresholds

## What's new in v3.0.0

- **Weekly digest** every Sunday: top 5 roles, jobs found vs last week, and jobs still waiting on you
- **Cover-letter drafts** next to each tailored resume — truthful, with gaps handled honestly
- **Closed-posting detection:** taken-down jobs are flagged automatically
- **Tracker stats:** jobs per week, average match score, and progress from found to interviewing

See [CHANGELOG.md](CHANGELOG.md) for details.

## What's new in v2.0.0

- Runs **every day, including weekends** (v1 ran weekdays only)
- Searches StepStone, LinkedIn, Indeed, XING, Glassdoor, Arbeitsagentur, Arbeitnow, Built In, TestDevJobs, Jobgether and company career pages
- Better duplicate detection when the same role is listed under a parent company
- Adds the tracker page (`tracker/`), the daily task prompt (`prompt/`) and the data model (`docs/`)

See [CHANGELOG.md](CHANGELOG.md) for details.
