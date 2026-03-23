## Context
The user wants Claude linked to both Google and Outlook calendars (and ideally emails) so it can compile a daily agenda summary and push that summary automatically via a custom skill. This requires connector code for each provider, a summary engine, a skill definition, and an automation hook or scheduler. We must document what credentials and configuration the user needs to supply before the integration works, and we must keep sensitive data out of source control.

## Recommended Approach
1. **Build calendar connectors** (scripts/connectors/calendar/google_calendar.py and scripts/connectors/calendar/outlook_calendar.py). Each module handles OAuth refresh flows, fetches event data for a configurable day/time window, and normalizes fields.
2. **Create the summary engine** (scripts/daily_schedule_summary.py). It should accept CLI arguments (date/mode/provider), call both connectors, deduplicate/sort events, format a markdown/text agenda (sections for morning/afternoon/evening, gaps, action items), and write the summary to `quality_reports/daily_schedules/YYYY-MM-DD_summary.md` (also printing the path for manual runs).
3. **Define the skill metadata** (`.claude/skills/daily-schedule/SKILL.md`). Describe trigger phrases, expected arguments, how to run the summary script, and troubleshooting (e.g., refresh tokens). Point to the connectors and document manual invocation steps.
4. **Add an automation hook** (`.claude/hooks/daily-schedule-push.py`). The hook loads `.claude/settings.json` configuration (schedule time, preferred providers/outputs), runs `scripts/daily_schedule_summary.py`, and records the output/log (optionally calling `notify.sh` or emailing/logging). Document how to attach this script to an external scheduler or `CronCreate` job for daily execution. The hook should write the summary to the log files and, when configured, send it via email through the connected account so the user receives both notification formats each day.
5. **Extend configuration** (`.claude/settings.json` + `.claude/settings.local.json` template). Introduce a `daily_schedule` section storing provider client IDs/secrets/refresh tokens, default calendar IDs, timezone, output directory, and notification preferences. Keep actual secrets in `settings.local.json` (document structure and mention tokens must be refreshed via OAuth).
6. **Testing and verification**: Manually run the connectors and summary script for a known date to confirm events align with calendars; trigger the hook manually to see logs/files created; configure a scheduler (e.g., `CronCreate` or system cron) to run the hook shortly to ensure automation working; review `quality_reports/daily_schedules/logs/` for success/failure entries. Highlight any webhook/notification channel status.

## Critical files and paths to update
- `scripts/connectors/calendar/google_calendar.py` (OAuth, event normalization)
- `scripts/connectors/calendar/outlook_calendar.py` (Outlook/Microsoft Graph onboarding)
- `scripts/daily_schedule_summary.py` (engine that merges providers, formats summaries, writes output)
- `.claude/skills/daily-schedule/SKILL.md` (skill metadata/invocation hints)
- `.claude/hooks/daily-schedule-push.py` (automation hook triggered daily)
- `.claude/settings.json` (default configuration schema for daily schedule) plus `.claude/settings.local.json` for secrets

## Verification strategy
- Manual CLI run: `python scripts/daily_schedule_summary.py --date <today>` and inspect generated markdown under `quality_reports/daily_schedules/`.
- Connector tests: fetch events via standalone script to ensure both APIs return expected times and normalization (log counts, errors).
- Hook test: execute `.claude/hooks/daily-schedule-push.py`, check log file, and confirm summary file creation.
- Automation test: schedule a near-term run via `CronCreate` or local cron and verify the hook runs at the desired time, writing logs.
- Review logs in `quality_reports/daily_schedules/logs/` for success/failure, including token refresh attempts and notification status.

## User inputs required
- Google OAuth client ID/secret, refresh token (scopes: Calendar read, optionally Gmail). Store in `.claude/settings.local.json`.
- Microsoft Graph app registration data (tenant ID, client ID/secret, refresh token) with `Calendars.Read` scope.
- Desired time window (e.g., 06:00 local) and timezone for daily push.
- Notification preference (email, console log, Slack); if email push is desired, extra SMTP or Graph mail configuration will be needed.
- Whether to include Outlook, Google, or both providers in each summary and how to override defaults during manual skill invocation.