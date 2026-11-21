# ~/bin

Personal, self-contained CLI scripts on `$PATH`.

## Preferences

- **Prefer Python + `uv`**: Write scripts in Python with PEP 723 inline script metadata so dependencies are bundled at the top and the script runs directly without external setup:
  ```python
  #!/usr/bin/env -S uv run --script
  # /// script
  # requires-python = ">=3.11"
  # dependencies = ["..."]
  # ///
  ```
  - Use `--quiet` (`#!/usr/bin/env -S uv run --quiet --script`) when stdout must stay clean for piping or `eval`.
  - Plain `#!/usr/bin/env python3` is fine if only the standard library is needed.
- **Fallback pragmatically**: If Python isn't the right fit (e.g. thin CLI/shell glue), pick the most logical alternative—typically `#!/usr/bin/env bash` with `set -euo pipefail`.
- **Keep scripts minimal**: Single-file, focused, low-ceremony, with a brief docstring and `--help` usage.
- **Executable**: Always `chmod +x` new scripts.

## Naming Conventions

- Use lowercase `kebab-case` with **no file extension** (e.g. `project-dir`, `cliptee`, `space`).
- Prefix vendor- or platform-specific tools with the vendor name (e.g. `aws-bedrock-ls`, `aws-copy-tags`, `aws-ddb-ctl`).
