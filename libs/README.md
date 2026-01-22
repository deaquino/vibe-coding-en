# 📦 Common Libraries & External Integrations (libs)

The `libs/` directory contains two types of content:

1. **Internal Reusable Glue Code**: Small, stable, loosely coupled, and
   replaceable (`common/`)
2. **Third-Party Tools & External Integrations**: Keep as-is as much as
   possible, with only minimal adaptation (`external/`)

`database/` is reserved for future data persistence layer (currently just a
placeholder).

## Directory Structure

```text
libs/
├── README.md
├── common/
│   ├── README.md
│   ├── __init__.py
│   ├── models/
│   │   └── __init__.py
│   └── utils/
│       └── backups/
│           ├── README.md
│           ├── 快速备份.py
│           └── 一键备份.sh
├── database/
│   ├── README.md
│   └── .gitkeep
└── external/
    ├── README.md
    ├── prompts-library/
    ├── my-nvim/
    ├── XHS-image-to-PDF-conversion/
    └── .gitkeep
```

## Subdirectory Responsibilities & Boundaries

### `common/`: Internal Common Modules

- Entry point: [`common/README.md`](./common/README.md)
- Contains only **reusable** basic capabilities: models, utility functions,
  scripts, etc.
- Don't add business logic or temporary project code here
- Convention: When adding/adjusting capabilities, update
  `libs/common/README.md` synchronously

### `database/`: Database Adapter Layer (Reserved)

- Entry point: [`database/README.md`](./database/README.md)
- Goal: Encapsulate "storage details" - connections, migrations, query
  adapters, transaction boundaries
- Convention: Before implementation, clearly document directory structure and
  boundaries (see `libs/database/README.md`)

### `external/`: Third-Party Tools & External Integrations

- Entry point: [`external/README.md`](./external/README.md)
- Keep third-party code as-is as much as possible, avoid "heavy modifications
  that prevent upgrades"
- Each tool directory should contain at minimum: `README.md` (purpose/entry
  point/dependencies) and license/source documentation
- Convention: When adding external tools, update
  `libs/external/README.md` synchronously

## Common Entry Points

- Batch prompt management:
  [`external/prompts-library/`](./external/prompts-library/)
  (used with `../prompts/`)
- Backup tools: Prefer using `backups/` at repository root (currently
  identical to `libs/common/utils/backups/` content)

## Contribution Conventions (Minimum Requirements)

1. Define responsibility boundaries before writing code/documentation for new
   modules
2. Record installation methods and minimum versions for new dependencies
   (supplement to tool documentation if necessary)
3. When directory structure/responsibilities change, update corresponding
   README to ensure "documentation is the source of truth"
