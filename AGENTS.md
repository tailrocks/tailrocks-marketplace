# AGENTS.md

This repository publishes a Claude Code plugin marketplace manifest.

Every plugin listed in `.claude-plugin/marketplace.json` runs inside downstream
users' Claude Code sessions with tool access. Treat marketplace edits as changes
to software distribution metadata.

## Hard Rules

- Only add plugin sources intentionally trusted by Tailrocks.
- Treat any plugin `source.url` change as a trust boundary change.
- Never commit credentials.
- Keep `.claude-plugin/marketplace.json` parseable JSON.

## Required Checks

```sh
python3 -m json.tool .claude-plugin/marketplace.json >/dev/null
```

If plugin entries change, verify every URL is expected:

```sh
python3 - <<'PY'
import json
from pathlib import Path

marketplace = json.loads(Path(".claude-plugin/marketplace.json").read_text())
for plugin in marketplace.get("plugins", []):
    source = plugin.get("source", {})
    url = source.get("url") if isinstance(source, dict) else source
    if not str(url).startswith("https://github.com/tailrocks/"):
        raise SystemExit(f"unexpected plugin source for {plugin['name']}: {url}")
PY
```

## Commit Messages

All commits in this repository should follow Conventional Commits 1.0.0.

Subject format: `<type>[optional scope][!]: <description>`
