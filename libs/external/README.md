# 🔌 libs/external: External Integrations & Third-Party Tools

`libs/external/` is used to collect third-party tools, external dependencies, and integration modules. Core principles:

- **Keep as-is as much as possible**: Avoid "heavy modifications that prevent upgrades"
- **Isolate dependencies and risks**: External tool dependencies should not pollute the main repository
- **Traceability**: Source, license, and usage must be clearly documented

## Directory Structure

```
libs/external/
├── README.md
├── prompts-library/                 # Prompt library management tool (Excel ↔ Markdown)
├── my-nvim/                         # Neovim configuration (contains nvim-config/)
├── XHS-image-to-PDF-conversion/     # Image merge to PDF tool
└── .gitkeep
```

## Tool List (Entry Points & Documentation)

- `prompts-library/`: Batch prompt Excel ↔ Markdown conversion and index generation (see [`prompts-library/README.md`](./prompts-library/README.md))
- `my-nvim/`: Personal Neovim configuration (see [`my-nvim/README.md`](./my-nvim/README.md))
- `XHS-image-to-PDF-conversion/`: Image merge to PDF (see [`XHS-image-to-PDF-conversion/README.md`](./XHS-image-to-PDF-conversion/README.md))

## Adding New External Tools (Minimum Checklist)

1. Create directory: `libs/external/<tool-name>/`
2. Required files: `README.md` (purpose/entry point/dependencies/input-output), license and source documentation (e.g., `LICENSE` / `SOURCE.md`)
3. Dependency constraints: Use the tool's own virtual environment/containerization when possible, don't impact other parts of the repository
4. Documentation sync: Add a tool description line in this README to ensure discoverability
