# 🎯 AI Skills Library

The `i18n/en/skills/` directory stores AI skills (Skills), which are higher-level capability encapsulations than prompts that enable AI to demonstrate expert-level performance in specific domains. Currently contains **14** professional skills.

## Directory Structure

```
i18n/en/skills/
├── README.md                # This file
│
├── # === Meta Skills (Core) ===
├── claude-skills/           # ⭐ Meta Skill: Skills that generate Skills (11KB)
│
├── # === Claude Tools ===
├── claude-code-guide/       # Claude Code usage guide (9KB)
├── claude-cookbooks/        # Claude API best practices (9KB)
│
├── # === Databases ===
├── postgresql/              # ⭐ PostgreSQL expert skill (76KB, most detailed)
├── timescaledb/             # Time-series database extension (3KB)
│
├── # === Cryptocurrency/Quantitative ===
├── ccxt/                    # Cryptocurrency exchange unified API (18KB)
├── coingecko/               # CoinGecko market data API (3KB)
├── cryptofeed/              # Cryptocurrency real-time data stream (6KB)
├── hummingbot/              # Quantitative trading bot framework (4KB)
├── polymarket/              # Prediction market API (6KB)
│
├── # === Development Tools ===
├── telegram-dev/            # Telegram Bot development (18KB)
├── twscrape/                # Twitter/X data scraping (11KB)
├── snapdom/                 # DOM snapshot tool (8KB)
└── proxychains/             # Proxy chain configuration (6KB)
```

## Skills Overview

### Sorted by File Size (Detail Level)

| Skill | Size | Domain | Description |
|-------|------|--------|-------------|
| **postgresql** | 76KB | Database | ⭐ Most detailed, complete PostgreSQL expert skill |
| **telegram-dev** | 18KB | Bot Development | Complete Telegram Bot development guide |
| **ccxt** | 18KB | Trading | Cryptocurrency exchange unified API |
| **twscrape** | 11KB | Data Collection | Twitter/X data scraping |
| **claude-skills** | 11KB | Meta Skill | ⭐ Skills that generate Skills |
| **claude-code-guide** | 9KB | Tools | Claude Code best practices |
| **claude-cookbooks** | 9KB | Tools | Claude API usage examples |
| **snapdom** | 8KB | Frontend | DOM snapshots and testing |
| **cryptofeed** | 6KB | Data Streams | Cryptocurrency real-time data stream |
| **polymarket** | 6KB | Prediction Markets | Polymarket API integration |
| **proxychains** | 6KB | Networking | Proxy chain configuration and usage |
| **hummingbot** | 4KB | Quantitative | Quantitative trading bot framework |
| **timescaledb** | 3KB | Database | PostgreSQL time-series extension |
| **coingecko** | 3KB | Market Data | CoinGecko market data API |

### Categorized by Domain

#### 🔧 Meta Skills and Tools

| Skill | Description | Recommended Scenarios |
|-------|-------------|----------------------|
| `claude-skills` | Skills that generate Skills | Required when creating new skills |
| `claude-code-guide` | Claude Code CLI usage guide | Daily development |
| `claude-cookbooks` | Claude API best practices | API integration |

#### 🗄️ Databases

| Skill | Description | Recommended Scenarios |
|-------|-------------|----------------------|
| `postgresql` | Complete PostgreSQL guide (76KB) | Relational database development |
| `timescaledb` | Time-series database extension | Time-series data |

#### 💰 Cryptocurrency/Quantitative

| Skill | Description | Recommended Scenarios |
|-------|-------------|----------------------|
| `ccxt` | Unified exchange API | Multi-exchange integration |
| `coingecko` | Market data API | Price queries |
| `cryptofeed` | Real-time data streams | WebSocket market data |
| `hummingbot` | Quantitative trading framework | Automated trading |
| `polymarket` | Prediction market API | Prediction market trading |

#### 🛠️ Development Tools

| Skill | Description | Recommended Scenarios |
|-------|-------------|----------------------|
| `telegram-dev` | Telegram Bot development | Bot development |
| `twscrape` | Twitter data scraping | Social media data |
| `snapdom` | DOM snapshots | Frontend testing |
| `proxychains` | Proxy chain configuration | Network proxying |

## Skills vs Prompts Differences

| Dimension | Prompts | Skills |
|-----------|---------|--------|
| Granularity | Single task instruction | Complete capability encapsulation |
| Reusability | Copy and paste | Auto-effective after configuration |
| Context | Needs manual provision | Built-in domain knowledge |
| Applicable Scenarios | Temporary tasks | Long-term projects |
| Structure | Single file | Directory (with assets/scripts/references) |

## Skill Directory Structure

Each skill follows a unified structure:

```
skill-name/
├── SKILL.md         # Main skill file, contains domain knowledge and rules
├── assets/          # Static resources (images, config templates, etc.)
├── scripts/         # Helper scripts
└── references/      # Reference documents
```

## Quick Use

### 1. View Skills

```bash
# View meta skill
cat i18n/en/skills/claude-skills/SKILL.md

# View PostgreSQL skill (most detailed)
cat i18n/en/skills/postgresql/SKILL.md

# View Telegram Bot development skill
cat i18n/en/skills/telegram-dev/SKILL.md
```

### 2. Copy to Project for Use

```bash
# Copy entire skill directory
cp -r i18n/en/skills/postgresql/ ./my-project/

# Or copy only main file to CLAUDE.md
cp i18n/en/skills/postgresql/SKILL.md ./CLAUDE.md
```

### 3. Use with Claude Code

Create `CLAUDE.md` in project root, reference skills:

```markdown
# Project Rules

Please refer to the following skill files:
@i18n/en/skills/postgresql/SKILL.md
@i18n/en/skills/telegram-dev/SKILL.md
```

## Creating Custom Skills

### Method 1: Generate Using Meta Skill (Recommended)

1. Prepare domain materials (documents, code, specifications)
2. Provide materials together with `i18n/en/skills/claude-skills/SKILL.md` to AI
3. AI will generate a specialized Skill for that domain

```bash
# Example: Have AI read meta skill then generate new skill
cat i18n/en/skills/claude-skills/SKILL.md
# Then tell AI: Please generate a new SKILL.md for [your domain] based on this meta skill
```

### Method 2: Manual Creation

```bash
# Create skill directory
mkdir -p i18n/en/skills/my-skill/{assets,scripts,references}

# Create main file
cat > i18n/en/skills/my-skill/SKILL.md << 'EOF'
# My Skill

## Overview
Brief description of skill purpose and applicable scenarios

## Domain Knowledge
- Core concepts
- Best practices
- Common patterns

## Rules and Constraints
- Rules that must be followed
- Prohibited operations
- Boundary conditions

## Examples
Specific usage examples and code snippets

## FAQ
Frequently asked questions and solutions
EOF
```

## Core Skills Explained

### `claude-skills/SKILL.md` - Meta Skill ⭐

**Skills that generate Skills**, the core tool for creating new skills.

Usage:
1. Prepare your domain materials (documents, code, specifications, etc.)
2. Provide materials together with SKILL.md to AI
3. AI will generate a specialized Skill for that domain

### `postgresql/SKILL.md` - PostgreSQL Expert ⭐

The most detailed skill (76KB), includes:
- Database design best practices
- Query optimization techniques
- Indexing strategies
- Performance tuning
- Common problem solutions
- SQL code examples

### `telegram-dev/SKILL.md` - Telegram Bot Development

Complete Telegram Bot development guide (18KB):
- Bot API usage
- Message handling
- Keyboards and callbacks
- Webhook configuration
- Error handling

### `ccxt/SKILL.md` - Cryptocurrency Exchange API

Unified exchange API encapsulation (18KB):
- Supports 100+ exchanges
- Unified data formats
- Order management
- Market data retrieval

## Related Resources

- [Skills Generator](https://github.com/yusufkaraaslan/Skill_Seekers) - Convert any materials to AI Skills
- [Meta Skill File](./claude-skills/SKILL.md) - Skills that generate Skills
- [Prompts Library](../prompts/) - Finer-grained prompt collection
- [Claude Code Guide](./claude-code-guide/SKILL.md) - Claude Code best practices
- [Documents Library](../documents/) - Methodology and development experience
