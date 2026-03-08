# Cron Health Check

Monitors OpenClaw cron job health by analyzing run history and identifying patterns of failures, timeouts, and delivery issues.

## Quick Start

```bash
# Check health of all cron jobs (last 24 hours)
python3 scripts/check_cron_health.py

# Check last 48 hours
python3 scripts/check_cron_health.py --hours 48

# JSON output
python3 scripts/check_cron_health.py --json
```

## Configuration

Edit `config.json` to customize health thresholds:

```json
{
  "thresholds": {
    "critical_consecutive_errors": 3,
    "warning_consecutive_errors": 1,
    "critical_timeout_count": 3,
    "warning_timeout_count": 1,
    "delivery_failure_threshold": 3
  },
  "check_interval_hours": 24,
  "max_recent_runs": 20,
  "max_recent_errors_displayed": 5
}
```

## Health Statuses

- **healthy** - No issues detected
- **warning** - Some issues but not critical
- **critical** - Multiple consecutive failures or timeouts

## Exit Codes

- `0` - All jobs healthy
- `1` - Warning issues found
- `2` - Critical issues found

## Requirements

- Python 3.7+
- OpenClaw installation with cron jobs configured

## License

OpenClaw Skill - See main OpenClaw repository for license information.
