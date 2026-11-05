# Job Radar — weekly digest prompt (v4.0.0)

Schedule: once a week at the end of your week, in your own time zone, e.g. `CRON_TZ=Europe/Berlin 37 18 * * 0` (Sunday evening) or `CRON_TZ=Asia/Dubai 37 18 * * 4` (Thursday evening for a Sunday–Thursday week; set `week_start` to "sunday" in your profile).

Replace `<TRACKER_URL>` before use. The job-radar skill must be installed.

```
Run the job-radar skill (anthropic-skills:job-radar) in weekly-digest mode, unattended. Load it with the Skill tool first and follow it exactly.
Tracker: <TRACKER_URL>
This is read-only: don't search the web and don't change any job. Don't ask questions.
Send the digest with SendUserMessage and as a push notification. If nothing happened this week, send a one-line note saying so.
If the job-radar skill is not listed, send a push notification saying the skill is missing and stop.
```
