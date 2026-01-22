# Repository Guidelines

## Project Structure & Module Organization
- Root directory: `README.md` provides the full picture, `Makefile` encapsulates daily commands, `CONTRIBUTING.md` explains the contribution process, and `LICENSE` specifies the license. Keep the root directory flat and avoid monolithic files.
- Multilingual i18n: `i18n/<lang>/` uses a unified three-tier structure (documents / prompts / skills). Existing languages: Chinese `zh`, English `en`, Hebrew `he`, and other common languages including `es`, `hi`, `ar`, `pt`, `ru`, `fr`, `de`, `ja`, `ko`, `it`, `tr`, `nl`, `pl`, `id`, `vi`, `th`, `fa`, `uk`, `bn`, `ta`, `ur`, `ms`, `sw`, `ha`. New languages should follow the same hierarchy.
- Documentation library: `i18n/en/documents/` is the default English methodology entry point. New language documents should be created under the corresponding `documents/` folder and kept in sync.
- Prompt assets: `i18n/en/prompts/` is split by role (system / assistant / coding / user). `libs/external/prompts-library/` provides Excel ↔ Markdown conversion tools and script directories for batch prompt maintenance, serving as the "single source of truth".
- Code and integration: `libs/` contains the core implementation skeleton, with `common/`, `database/`, and `external/` corresponding to common models, storage adapters, and external dependencies respectively. New modules should maintain layered boundaries and single responsibility, avoiding cross-layer calls.
- Backups: `backups/` contains `one_click_backup.sh` and `quick_backup.py` for local snapshots or syncing. Please test in an isolated directory first to confirm output paths and permissions.

## Build, Test, and Development Commands
- `make help`: Lists all Make targets; the entry point for newcomers to get started quickly.
- `make lint`: Uses `markdownlint-cli` to validate all Markdown files in the repository. Run this after adding new documentation (requires local Node/npm environment; install with `npm install -g markdownlint-cli`).
- `make build` / `make test` / `make clean`: Currently placeholders. Update the scripts and documentation after implementing specific functionality. Keep scripts idempotent and avoid modifying global state.
- Prompt conversion: Navigate to `libs/external/prompts-library/` and run `python main.py` to convert interactively. Confirm the virtual environment, dependencies, and output directory before running, and check that the generated Markdown complies with lint rules after completion.

## Coding Style & Naming Conventions
- Text layer: Documentation, comments, and logs should be in English. Code symbols (functions / variables / modules) should use English with clear semantics, avoiding obscure abbreviations.
- Indentation and formatting: Use space indentation throughout the repository (2 or 4 spaces—choose one but don't mix). Keep Markdown lists, code blocks, and tables clearly aligned, with line width under 120 columns. Prioritize Git diff readability.
- Design principles: Prioritize eliminating branches and duplication. Functions should have a single responsibility and be short. Use lowercase with hyphens or underscores for naming, avoiding spaces and special characters. Cross-module interfaces should maintain stable signatures.
- Dependency management: When adding new tools or libraries, record the installation method, minimum version, and source. Supplement in `i18n/en/documents/Templates and Resources/Tool_Set.md` or README as needed, explaining why it's needed (performance, compatibility, functionality).

## Testing Guidelines
- Currently no test cases exist. When introducing code, please provide at least minimal reproducible tests. For Python, use `pytest` with `test_*.py` naming convention, keep fixtures concise and readable, and follow the red-green-refactor cycle.
- Documentation and prompt changes: Run `make lint` before committing. If conversion scripts involve data, include example input/output descriptions or minimal data samples to ensure reproducibility.
- Coverage baselines are set by module maintainers. If no standard exists, ensure main flows and edge cases can be verified by tests. If necessary, note uncovered risks in the PR description and suggest follow-up testing plans.

## Commit & Pull Request Guidelines
- Commits should follow simplified Conventional Commits: `feat|fix|docs|chore|refactor|test: scope – summary`. Describe the action and scope in one sentence; avoid vague messages like "update".
- PR requirements: Change summary, motivation or related Issue, testing and verification steps (list commands run and results overview). Documentation/UI changes should include before/after screenshots or links for quick reviewer review.
- Pre-commit checklist: Run `make lint`. If adding new scripts/dependencies, update corresponding documentation and `Makefile` targets. Confirm no temporary files or sensitive data are included, and note potential risks or areas needing special reviewer attention in the description.

## Security & Configuration Tips
- Before running backup or conversion scripts, confirm the output directory won't overwrite private data. Test in a temporary directory first and check generated files; use read-only copies when necessary.
- External dependency sources are recorded in the `libs/external/` directory. Maintain synchronization when adding or removing dependencies for traceability. Third-party scripts must have their license and source clearly marked.

## Architecture Overview & Workflow
- The workflow advocates "Plan → Lock Context → Step-by-step Implementation → Self-test → Review", with corresponding assets stored in `i18n/en/documents/`, `i18n/en/prompts/`, `libs/`, and backup scripts. Maintaining unidirectional data flow and clear responsibility boundaries helps avoid skyrocketing maintenance costs later.
- After design decisions and directory structure updates, please synchronize revisions to this file and related documentation to ensure the team shares a single source of truth, reducing verbal agreements and implicit rules.

---

# CLAUDE.md

This file provides guidance to Claude series models when working with code in this repository.

## Repository Overview

This is the **Vibe Coding** repository, a workflow, toolset, and knowledge base for advanced AI-assisted programming. The project's core assets are its extensive `prompts` and `skills` libraries.

## Key Commands

### Prompt Library Management
```bash
# Enter the library directory
cd libs/external/prompts-library

# Run the interactive conversion tool
python3 main.py
```

### Development & Maintenance
```bash
# Lint all markdown files in the repository
make lint

# Create a full project backup (respects .gitignore)
bash backups/one_click_backup.sh
```

## Architecture & Structure

### Core Directories
- **`i18n/en/prompts/`**: The core asset. A massive, well-organized library of prompts.
  - `coding_prompts/`, `system_prompts/`, `user_prompts/`, `meta_prompts/`
- **`i18n/en/skills/`**: A modular library of skills for the AI, providing domain-specific knowledge for various tools like `ccxt`, `postgresql`, `telegram-dev`, 
etc.
- **`i18n/en/documents/`**: The project's knowledge base, containing methodology, principles, and guides.
- **`libs/external/prompts-library/`**: A Python-based tool for converting prompts between Excel and Markdown formats.
- **`backups/`**: Scripts for project backups.
- **`libs/`**: Skeleton for shared Python library code.

### Key Technical Details
1.  **Prompt Organization**: Prompts use a `(row,col)_` prefix for categorization.
2.  **Conversion Tool**: The `prompts-library` uses Python with `pandas` and `openpyxl`.
3.  **Documentation Standard**: User-facing documentation is in English. Code, file names, and structure are in English.
4.  **Skills**: The `skills` directory provides context and knowledge for specific tools and domains, each with its own `SKILL.md`.

## Development Workflow

When modifying this repository:
1.  Follow the existing prompt and skill categorization systems.
2.  Use the `prompts-library` tool to maintain consistency when updating prompts.
3.  Run `make lint` after changing any Markdown files.
4.  Run a backup with `bash backups/one_click_backup.sh` before any major refactoring.

---

# GEMINI.md - Project Context Document

## Project Overview

The `vibe-coding-en` project aims to provide the ultimate workflow for turning ideas into reality through AI pair programming. It emphasizes the core principles of "planning-driven" and "modularity", aiming to prevent project chaos caused by AI going out of control. This project is not just a code repository, but a comprehensive AI pair programming guide, a vast prompt library, and a modular skill toolset, covering the entire process from project conception, technology selection, implementation planning to specific development, debugging, and expansion.

**Core Philosophy:** Planning is the core. Guide the AI through structured and modular approaches to ensure the project is controllable and maintainable.

## Technology Stack

The main technology stack and related tools for this project include:

*   **Core Language:** Python (for `prompts-library` tool and backup scripts)
*   **CLI Interaction:** `rich`, `InquirerPy` (for `prompts-library` to provide friendly command-line interface)
*   **Data Processing:** `pandas`, `openpyxl` (for `prompts-library` to handle Excel files)
*   **Configuration Management:** `PyYAML` (for `prompts-library` configuration)
*   **Documentation Standards:** `markdownlint-cli` (for `lint` task in `Makefile`)
*   **Version Control:** Git
*   **Automation:** Makefile
*   **Operating System:** Linux-compatible

## Key Features & Workflow

1.  **AI Prompt Library (`i18n/en/prompts/`):**
    *   An extremely large and meticulously categorized collection of prompts—the project's core asset.
    *   `coding_prompts/`: Prompts focused on programming and code generation.
    *   `system_prompts/`: System-level prompts for setting AI behavior and thinking frameworks.
    *   `user_prompts/`: User-defined or frequently used prompts.
    *   `meta_prompts/`: Meta-prompts and prompt engineering assistance.

2.  **Prompt Library Management Tool (`libs/external/prompts-library/`):**
    *   Provides Python tool (`main.py`) for bidirectional conversion between Excel workbooks (`prompt_excel/`) and Markdown documents (`prompt_docs/`).
    *   Supports both interactive and non-interactive operations.

3.  **Skills Library (`i18n/en/skills/`):**
    *   A modular collection of skills that provides AI with domain-specific knowledge for various tools.
    *   Each skill (e.g., `ccxt`, `postgresql`, `telegram-dev`) contains an independent `SKILL.md` description, reference materials, and scripts.

4.  **Project Backup Tool (`backups/`):**
    *   The `quick_backup.py` script intelligently packages project files into `.tar.gz` format based on `.gitignore` rules.

5.  **Knowledge Base & Documentation (`i18n/en/documents/`):**
    *   Contains various documents including code organization, development experience, system prompt construction principles, project architecture templates, and more.

6.  **External Tools & Personal Configurations (`libs/external/`):**
    *   Stores useful external tools, personal configurations, or experimental code that are not core to the project. Examples: `my-nvim/` (nvim configuration), `XHS-image-to-PDF-conversion/` (image to PDF converter).

## File Structure

```
.
├── .gitignore                   # Git version control ignore file configuration
├── AGENTS.md                    # Contribution guidelines and behavioral rules for AI agents.
├── CLAUDE.md                    # Context and instructions for Claude model.
├── CODE_OF_CONDUCT.md           # Project code of conduct.
├── CONTRIBUTING.md              # Contribution guide.
├── GEMINI.md                    # Context and instructions for Gemini model (this document).
├── LICENSE                      # Project license.
├── Makefile                     # Project automation scripts (lint, backup, etc.).
├── README.md                    # Main project documentation, including overview and usage guide.
│
├── i18n/
│   ├── zh/{documents,prompts,skills}   # Chinese primary materials and methodology.
│   ├── en/{documents,prompts,skills}   # English version assets.
│   ├── he/{documents,prompts,skills}   # Hebrew (Israel).
│   ├── es|hi|ar|pt|ru|fr|de|ja|ko|it|tr|nl|pl|id|vi|th|fa|uk|bn|ta|ur|ms|sw|ha/{documents,prompts,skills}  # Other common language skeletons.
│
├── libs/                        # Core library code.
│   ├── common/                  # Common functionality and utility library.
│   │   ├── __init__.py          # Python package initialization file.
│   │   ├── models/              # Data model definitions.
│   │   └── utils/               # Utility functions.
│   ├── database/                # Database-related code.
│   └── external/                # External tools, personal configurations, or experimental code.
│       ├── prompts-library/     # Prompt library management tool (Excel-Markdown conversion).
│       │   ├── main.py          # Prompt library management tool main program.
│       │   ├── requirements.txt # Tool dependencies.
│       │   ├── prompt_excel/    # Excel format prompts.
│       │   ├── prompt_docs/     # Markdown format prompt documents.
│       │   └── ... (other prompts-library internal files)
│       ├── l10n-tool/           # Multi-language batch translation script, protects code blocks, machine translate then polish.
│       ├── my-nvim/             # Personal Neovim configuration.
│       └── XHS-image-to-PDF-conversion/ # Image to PDF conversion tool.
│
├── i18n/en/prompts/                     # Core asset: AI prompt library.
│   ├── coding_prompts/                  # Programming and code generation prompts.
│   ├── system_prompts/                  # AI system-level prompts (includes CLAUDE version directory).
│   ├── user_prompts/                    # User-defined prompts.
│   └── meta_prompts/                    # Meta-prompts and prompt engineering assistance.
│
└── i18n/en/skills/                      # Modular skills library.
    ├── ccxt/                    # CCXT cryptocurrency trading library skill.
    ├── claude-code-guide/       # Claude Code usage guide skill.
    ├── postgresql/              # PostgreSQL database skill.
    ├── telegram-dev/            # Telegram Bot development skill.
    └── ... (10+ other skills)
```
