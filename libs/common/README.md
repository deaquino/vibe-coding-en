# 🔧 libs/common: Common Modules

`libs/common/` contains project-internal reusable "glue code": **small, stable, loosely coupled, and replaceable**. The goal here is not to pile on functionality, but to provide a small set of reliable basic capabilities for the repository.

## Directory Structure

```
libs/common/
├── README.md
├── __init__.py
├── models/                 # Reserved: Data models (currently just a placeholder)
│   └── __init__.py
└── utils/
    └── backups/            # Quick backup tools based on .gitignore
        ├── README.md
        ├── quick_backup.py
        └── one_click_backup.sh
```

## Current Contents

- `utils/backups/`: Quick backup tools (currently identical content to repository root [`backups/`](../../backups/), to avoid scripts scattered everywhere)

## Constraints & Conventions

1. **No business logic**: `common/` only provides basic capabilities and tools
2. **Stable interfaces**: Once referenced, treat it as a public API
3. **Auditable output**: Script/tool output should be reviewable (clear input, output paths, failure reasons)
4. **Document new additions**: New modules/directories must synchronize updates to this README and `libs/README.md`

## Usage (Current Recommendation)

The contents of this directory currently exist primarily as "scripts/tools". Direct execution is recommended:

```bash
# Backup current repository (preferably use root directory backups/ entry point)
python3 backups/quick_backup.py
```

For more parameters and documentation, see: [`../../backups/README.md`](../../backups/README.md).
