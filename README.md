# schedulesorter-heartbeat

External uptime monitor for [schedulesorter.com](https://schedulesorter.com), run on
GitHub Actions. It is kept in its own public repo because Actions minutes are free
for public repos, and the private app repo's 2,000-minute allowance kept running out.

| Workflow | Cadence | Behaviour |
|---|---|---|
| `heartbeat.yml` | Every 10 min | Probes `/` and `/api/health`, and messages Telegram **only on failure** |
| `heartbeat-digest.yml` | 08:00 UTC daily | Same probes plus TLS expiry, **always** sends a summary, and re-enables both workflows so GitHub's 60-day inactivity rule never switches them off |

Required secrets (Settings → Secrets and variables → Actions): `TG_TOKEN`, `TG_CHAT`.

Run logs are public. Don't add anything that prints secrets or non-public details.
The operator runbook is `docs/operations-and-admin.html` §06 and §12 in the app repo.
