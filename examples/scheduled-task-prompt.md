# Scheduled task prompt

Use this as the prompt of a Claude scheduled task (for example every day at 8:45 in your own time zone, weekends included). Replace `<TRACKER_URL>` with your own Job Radar tracker link. The full versions are in [`job-radar/prompt/`](../job-radar/prompt/).

```
Run the job-radar skill in full-run mode, unattended. Load it with the Skill tool first and follow it exactly.
Tracker: <TRACKER_URL>
Don't ask questions; make reasonable calls and note them in the report.
NEVER apply to a job, submit any form, or contact an employer, recruiter or anyone else.
When finished, send me a short push notification with the number of new jobs,
the top 3 (Score – Role – Company – City, Country – Languages), which got tailored resumes and cover letters,
and any postings newly flagged as closed.
If nothing new was found and no postings closed, stay silent.
```
