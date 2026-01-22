# 💡 AI Prompts Library (Prompts)

`i18n/en/prompts/` stores the prompt assets of this repository: use **system prompts** to constrain AI boundaries and preferences, use **task prompts** to drive the "requirements clarification → planning → execution → review" development pipeline.

## Recommended Usage Path (From 0 to Controllable)

1. **Define boundaries first**: Choose a system prompt version (recommended `v8` or `v10`).
2. **Then run the process**: Select from `coding_prompts/` by stage during specific tasks (clarification / planning / execution / review).
3. **Finally productize**: When you repeatedly do similar work in a certain domain, upgrade "prompts + materials" to a Skill in `skills/` (more reusable, more stable).

## Directory Structure (Based on actual repository directories)

```
i18n/en/prompts/
├── README.md
├── coding_prompts/                 # Programming/development prompts (currently 41 .md files)
│   ├── index.md                    # Auto-generated index and version matrix (do not edit manually)
│   ├── Standardized_Process.md
│   ├── Project_Context_Document_Generation.md
│   ├── Intelligent_Requirements_Understanding_and_Development_Navigation_Engine.md
│   └── ...
├── system_prompts/                 # System prompts (CLAUDE multiple versions + other collections)
│   ├── CLAUDE.md/                  # Versions 1~10 directory (v9 currently placeholder only)
│   │   ├── 1/CLAUDE.md
│   │   ├── 2/CLAUDE.md
│   │   ├── ...
│   │   ├── 9/AGENTS.md             # v9 currently has no CLAUDE.md
│   │   └── 10/CLAUDE.md
│   └── ...
└── user_prompts/                   # User-defined/one-time prompts
    ├── ASCII_Art_Generation.md
    ├── Data_Pipeline.md
    └── Project_Variables_and_Tools_Unified_Maintenance.md
```

## `system_prompts/`: System-level Prompts (Make AI "Controllable" First)

System prompts are used to define **working modes, code preferences, output formats, security boundaries**. The directory uses a versioned structure:

- Path convention: `i18n/en/prompts/system_prompts/CLAUDE.md/<version>/CLAUDE.md`
- Recommended versions:
  - `v8`: Comprehensive version, suitable for general Vibe Coding
  - `v10`: Focuses on Augment/context engine standardization constraints
- Note: `v9` directory is currently placeholder only (no `CLAUDE.md`)

## `coding_prompts/`: Task-level Prompts (Get the Process Running)

`coding_prompts/` is oriented toward "a single task": from requirements clarification, plan decomposition to delivery and review. It's recommended to treat it as a workflow script library:

- **Entry-level** (required for new sessions/new projects)
  - `Project_Context_Document_Generation.md`: Solidify context, reduce cross-session drift
  - `Intelligent_Requirements_Understanding_and_Development_Navigation_Engine.md`: Break vague requirements into executable tasks
- **Delivery-level** (ensure output is auditable)
  - `Standardized_Process.md`: Defines "what to do first, what to do next" to reduce losing control
  - `System_Architecture_Visualization_Generate_Mermaid.md`: Output architecture as visualizations (a picture is worth a thousand words)

### About `index.md` (Important)

[`coding_prompts/index.md`](./coding_prompts/index.md) is an auto-generated index (including version matrix and links), **do not edit manually**. If you batch add/delete/adjust versions, it's recommended to generate the index through the toolchain then sync.

## `user_prompts/`: Personal Workbench (Not Systematized)

Place some personal habits, temporary scaffold prompts. The principle is **usable, not messy, don't pollute the main library**.

## Quick Use (Copy and Use)

```bash
# View a task prompt
sed -n '1,160p' i18n/en/prompts/coding_prompts/Standardized_Process.md

# Select system prompt version (backup your current CLAUDE.md first)
cp i18n/en/prompts/system_prompts/CLAUDE.md/10/CLAUDE.md ./CLAUDE.md
```

## Maintenance and Batch Management (Optional)

If you need Excel ↔ Markdown batch maintenance capability, the repository has a built-in third-party tool: `libs/external/prompts-library/`. It's recommended to treat it as "production tool for prompt assets", while treating `i18n/en/prompts/` as "curated collection for daily development".

## Related Resources

- [`../skills/`](../skills/): Consolidate high-frequency domain capabilities into Skills (stronger reuse)
- [`../documents/`](../documents/): Methodology and best practices (prompt design and workflow principles)
- [`../../../libs/external/prompts-library/`](../../../libs/external/prompts-library/): Prompt Excel ↔ Markdown management tool
