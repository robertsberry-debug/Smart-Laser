# Daily 8:00 AM Central Report Setup (Option A)

This repository cannot autonomously email without external automation + credentials.
Use one of the options below to send the report daily to:

- **Recipient:** `streeter@smartlasermfg.com`
- **Schedule:** `8:00 AM America/Chicago` daily

## Recommended: Zapier (lowest friction)

### Zap steps
1. **Trigger:** Schedule by Zapier → Every Day at 8:00 AM, timezone `America/Chicago`.
2. **Action 1:** Call your LLM/API with the contents of `automation/daily_prompt.md`.
3. **Action 2:** Gmail/SMTP action:
   - To: `streeter@smartlasermfg.com`
   - Subject: `Smart Laser Daily 8AM Intelligence Brief - {{zap_meta_human_now}}`
   - Body: output from Action 1.
4. Turn Zap ON.

### Why recommended
- Native timezone scheduling with DST handled.
- Native email connectors.
- Minimal engineering overhead.

---

## Alternative: GitHub Actions + email API

Use `.github/workflows` only if you already have an email API (SendGrid, Mailgun, SES) configured.

### Notes
- GitHub cron runs in UTC.
- 8:00 AM Central changes with DST (13:00 UTC in CST, 12:00 UTC in CDT).
- For strict local-time consistency, schedule hourly and gate in script by `TZ=America/Chicago` current hour.

---

## Reminder backup (manual)

Import `automation/smart_laser_daily_8am.ics` into your calendar for a visible reminder.

