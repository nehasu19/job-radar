# Scheduled task prompt

Use this as the prompt of a Claude scheduled task (for example weekdays at 8:45). Replace `<TRACKER_URL>` with your own Job Radar tracker link.

```
Run the job-radar skill in full-run mode for my tracker at <TRACKER_URL>.
Work unattended: don't ask questions, make reasonable calls and note them in the summary.
NEVER apply to a job, submit any form, or contact an employer, recruiter or anyone else.
When finished, send me a short push notification with the number of new jobs,
the top 3 (Score – Role – Company – City – Language level), and which got tailored resumes.
If nothing new was found, stay silent.
```
