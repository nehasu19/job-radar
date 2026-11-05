# Job Radar — daily scheduled-task prompt (v4.0.0)

Schedule: every day, weekends included, in your own time zone, e.g. `CRON_TZ=Europe/Berlin 45 8 * * *`, `CRON_TZ=Asia/Kolkata 40 7 * * *` or `CRON_TZ=America/Toronto 50 6 * * *`.

Replace `<TRACKER_URL>` before use. The job-radar skill must be installed; all search rules, thresholds and markets come from the skill and your tracker profile.

```
Run the job-radar skill (anthropic-skills:job-radar) in full-run mode, unattended. Load it with the Skill tool first and follow it exactly.
Tracker: <TRACKER_URL>
Don't ask questions; make reasonable calls and note them in the report. Never apply to a job, contact an employer or recruiter, submit any form, or send any message on my behalf.
When finished, send the report with SendUserMessage, and send a push notification if there are new jobs, newly closed postings, or the run failed. Stay silent (no push) if nothing changed.
If the job-radar skill is not listed, send a push notification saying the skill is missing and stop.
```
