# Quick Backup Tool

A project backup tool based on `.gitignore` rules that automatically excludes unnecessary files.

## Features

- Automatically reads `.gitignore` rules
- Supports negation rules (`!` syntax)
- Directory-level pruning optimization
- Generates `.tar.gz` compressed archives
- Zero dependencies (only uses Python built-in modules)

## File Structure

```
backups/
├── quick_backup.py    # Core backup engine
├── one_click_backup.sh    # Shell startup script
└── README.md      # This document
```

## Usage

```bash
# Method 1: Shell script (recommended)
bash backups/one_click_backup.sh

# Method 2: Run Python directly
python3 backups/quick_backup.py

# Specify output file
python3 backups/quick_backup.py -o my_backup.tar.gz

# Specify project directory
python3 backups/quick_backup.py -p /path/to/project
```

## Output Location

Default output to `backups/gz/backup_YYYYMMDD_HHMMSS.tar.gz`

## Parameter Description

| Parameter | Description | Default Value |
|-----------|-------------|---------------|
| `-p, --project` | Project root directory | Current directory |
| `-o, --output` | Output file path | `backups/gz/backup_timestamp.tar.gz` |
| `-g, --gitignore` | gitignore file path | `.gitignore` |

## Dependencies

- Python 3.x (no additional packages required)
- Bash (for shell script)
