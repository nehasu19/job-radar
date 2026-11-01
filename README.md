# Job Radar – a Claude skill for job searching

Job Radar is a [Claude](https://claude.ai) skill that runs a personal job search for you:

- searches job boards and company career pages for roles that match **your** profile
- opens each posting to check it is still live and recent
- scores each job 0–100 against your resume (role, skills, domain, location, language)
- saves good matches to your own **Job Radar tracker**, without duplicates
- drafts **truthful** tailored resumes for the best matches

It **never** applies to jobs, fills in forms or contacts anyone. You stay in control.

## What you need

- A Claude plan with skills and artifacts enabled (claude.ai or the Claude app)
- Web search enabled
- Optional: Claude Docs (for tailored resumes as editable documents)
- Optional: a scheduled task, to run the search automatically every morning

## Install

1. Download this repository (green **Code** button → **Download ZIP**), or download `job-radar.skill` from the Releases page.
2. In Claude, go to **Settings → Capabilities → Skills** and upload the `job-radar` folder (zipped) or the `.skill` file.
   If your organisation manages skills, ask your admin to add it.

## First run

Say to Claude:

> Set up Job Radar for me

Claude will ask for your resume, target roles, locations, language level, availability and any employers to exclude, then create your tracker page. See [`examples/profile.example.json`](examples/profile.example.json) for the profile fields.

## Everyday use

| You say | What happens |
|---|---|
| "Run job radar" | Full search: new jobs scored and added to your tracker, tailored resumes for the best ones |
| "Add this job to my tracker" + a link or pasted posting | Checks and scores that one job |
| "Tailor my resume for the <company> job" | Writes a tailored resume for a job already in your tracker |

## Run it automatically

Ask Claude: *"Create a scheduled task that runs Job Radar every weekday at 8:45"*. A ready-made prompt is in [`examples/scheduled-task-prompt.md`](examples/scheduled-task-prompt.md).

## LinkedIn

LinkedIn blocks automated reading of its pages, and Job Radar respects that. Instead, set up LinkedIn **job alerts** sent to your email, connect your email to Claude, and ask Job Radar to include those alerts – it then checks each job on the company's own careers page.

## Principles

- **Truthful resumes:** only your real experience, reordered and reworded – never invented skills, titles, dates or degrees.
- **No actions on your behalf:** no applications, no messages, no form submissions.
- **Your data stays yours:** your profile and jobs live in your own private tracker.

## Licence

MIT – see [LICENSE](LICENSE).

## What's new in v2.0.0

- Runs **every day, including weekends** (v1 ran weekdays only)
- Searches StepStone, LinkedIn, Indeed, XING, Glassdoor, Arbeitsagentur, Arbeitnow, Built In, TestDevJobs, Jobgether and company career pages
- Better duplicate detection when the same role is listed under a parent company
- Adds the tracker page (`tracker/`), the daily task prompt (`prompt/`) and the data model (`docs/`)

See [CHANGELOG.md](CHANGELOG.md) for details.
