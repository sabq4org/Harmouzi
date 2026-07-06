# OpenClaw -> Hermes Migration Report

- Timestamp: 20260704T155144
- Mode: execute
- Source: `/Users/alialhazmi/.openclaw`
- Target: `/Users/alialhazmi/.hermes`

## Summary

- migrated: 7
- archived: 4
- skipped: 31
- conflict: 2
- error: 0

## Warnings

- Conflicts were found. Re-run with --overwrite to replace conflicting targets after item-level backups.
- A config.yaml write hit a conflict or error mid-apply; later config items were skipped to avoid a partial write.

## What Was Not Fully Brought Over

- `/Users/alialhazmi/.openclaw/workspace/AGENTS.md` -> `(n/a)`: No workspace target was provided
- `/Users/alialhazmi/.openclaw/openclaw.json` -> `/Users/alialhazmi/.hermes/.env`: No Discord settings found
- `/Users/alialhazmi/.openclaw/openclaw.json` -> `/Users/alialhazmi/.hermes/.env`: No Slack settings found
- `/Users/alialhazmi/.openclaw/openclaw.json` -> `/Users/alialhazmi/.hermes/.env`: No Signal settings found
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `/Users/alialhazmi/.hermes/skills/openclaw-imports`: No OpenClaw skills directory found
- `(n/a)` -> `/Users/alialhazmi/.hermes/skills/openclaw-imports`: No shared OpenClaw skills directories found
- `(n/a)` -> `/Users/alialhazmi/.hermes/tts`: Source directory not found
- `/Users/alialhazmi/.openclaw/openclaw.json` -> `(n/a)`: Selected Hermes-compatible values were extracted; raw OpenClaw config was not copied.
- `/Users/alialhazmi/.openclaw/credentials/telegram-default-allowFrom.json` -> `(n/a)`: Selected Hermes-compatible values were extracted; raw credentials file was not copied.
- `/Users/alialhazmi/.openclaw/memory/main.sqlite` -> `(n/a)`: Contains secrets, binary state, or product-specific runtime data
- `/Users/alialhazmi/.openclaw/credentials` -> `(n/a)`: Contains secrets, binary state, or product-specific runtime data
- `/Users/alialhazmi/.openclaw/devices` -> `(n/a)`: Contains secrets, binary state, or product-specific runtime data
- `/Users/alialhazmi/.openclaw/identity` -> `(n/a)`: Contains secrets, binary state, or product-specific runtime data
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `(n/a)` -> `(n/a)`: blocked by earlier apply conflict
- `/Users/alialhazmi/.openclaw/workspace/SOUL.md` -> `/Users/alialhazmi/.hermes/SOUL.md`: Target exists and overwrite is disabled
- `/Users/alialhazmi/.openclaw/openclaw.json` -> `/Users/alialhazmi/.hermes/config.yaml`: Model already set and overwrite is disabled

## Next Steps

- Review the migration report at /Users/alialhazmi/.hermes/migration/openclaw/20260704T155144/summary.md
- Start a new Hermes session (or /reset) to pick up the imported config.
- Re-run with --overwrite to apply items that were blocked by conflicts.
