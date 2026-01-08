# Git Annual Summary - Claude Code Skill

Generate comprehensive year-end summary reports for your Git repositories.

## Features

- 📊 **Annual Overview**: Total commits, code changes, contributor rankings
- 📅 **Work Rhythm Analysis**: Monthly trends, most active days/hours
- 📝 **Work Content Analysis**: Categorize commits by type (feat/fix/refactor/docs)
- 💻 **Code Impact Analysis**: Most changed files, tech stack breakdown
- ⭐ **Highlights**: Key achievements and improvements
- 🔮 **Summary & Outlook**: Year-end reflection and suggestions

## Installation

Copy and run the command for your platform:

**macOS / Linux**
```bash
mkdir -p ~/.claude/commands && curl -fsSL -o ~/.claude/commands/git-annual-summary.md https://raw.githubusercontent.com/iiYeung/git-annual-summary-skill/main/SKILL.md
```

**Windows (PowerShell)**
```powershell
New-Item -Force -ItemType Directory "$env:USERPROFILE\.claude\commands" | Out-Null; Invoke-WebRequest -Uri "https://raw.githubusercontent.com/iiYeung/git-annual-summary-skill/main/SKILL.md" -OutFile "$env:USERPROFILE\.claude\commands\git-annual-summary.md"
```

## Usage

In any Git repository, use Claude Code with the following commands:

```bash
# Generate summary for current year (all contributors)
/git-annual-summary

# Generate summary for specific year
/git-annual-summary 2025

# Generate summary for specific author
/git-annual-summary 2025 "John Doe"

# Generate summary for current git user
/git-annual-summary 2025 me
```

## Example Output

```
# 2025 Git Annual Work Summary Report

## I. Annual Overview

- Total commits: 156
- Code changes: +12,345 / -4,567 lines
- Contributors: 5

### Monthly Commit Distribution

Jan ████████████████ 32
Feb ████████████ 24
Mar ██████████████████ 36
...

## II. Work Rhythm Analysis
...
```

## Requirements

- Claude Code CLI
- Git repository with commit history

## License

MIT

## Contributing

Issues and PRs are welcome!
