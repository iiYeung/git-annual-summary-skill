---
name: git-annual-summary
description: Generate Git repository annual summary reports, analyzing commit history, code changes, and contribution statistics
allowed-tools: Bash(git:*), Read, Write
---

# Git Annual Summary Report Generator

Generate a comprehensive year-end work summary report for the current Git repository.

## Parameters
- Year: $1 (defaults to current year)
- Author (optional): $2 (if not specified, statistics for all authors; use "me" for current user)

## Analysis Steps

### 1. Data Collection

Execute the following git commands to collect data:

```bash
# Get commit statistics for the specified year
git log --since="$1-01-01" --until="$1-12-31" --oneline

# Get monthly commit distribution
git log --since="$1-01-01" --until="$1-12-31" --format="%ai" | cut -d'-' -f2 | sort | uniq -c

# Get code change statistics
git log --since="$1-01-01" --until="$1-12-31" --numstat --format=""

# Get active contributors
git shortlog -sn --since="$1-01-01" --until="$1-12-31"

# Get commit messages for topic analysis
git log --since="$1-01-01" --until="$1-12-31" --format="%s"

# Get statistics by day of week
git log --since="$1-01-01" --until="$1-12-31" --format="%ad" --date=format:"%u" | sort | uniq -c

# Get statistics by hour
git log --since="$1-01-01" --until="$1-12-31" --format="%ad" --date=format:"%H" | sort | uniq -c
```

If an author parameter ($2) is specified, add `--author="$2"` to all git log commands.
If the author parameter is "me", first get the current username via `git config user.name`.

### 2. Report Content Requirements

The generated report should include the following sections:

#### I. Annual Overview
- Total number of commits
- Code changes (lines added/deleted)
- Monthly activity distribution chart (using ASCII bar chart)
- Number of contributors and rankings

#### II. Work Rhythm Analysis
- Monthly commit trends
- Most active days/hours
- Commit frequency analysis

#### III. Main Work Content
Analyze based on commit messages:
- New feature development (feat/feature)
- Bug fixes (fix/bugfix)
- Code refactoring (refactor)
- Documentation updates (docs)
- Other types

Count by category and list representative work items.

#### IV. Code Impact Analysis
- Most changed files/directories
- Main modules/components involved
- Tech stack usage (inferred from file extensions)

#### V. Highlights & Achievements
Based on the analysis, extract:
- Important feature releases
- Significant technical improvements
- Outstanding contributions

#### VI. Summary & Outlook
- Annual work summary (2-3 sentences)
- Improvement suggestions based on commit history

### 3. Output Format
- Use Markdown format
- Include appropriate charts (ASCII art)
- Accurate data, objective analysis
- Concise and professional language

## Usage Examples
- `/git-annual-summary 2025` - Generate 2025 summary for all contributors
- `/git-annual-summary 2025 "John Doe"` - Generate John Doe's 2025 summary
- `/git-annual-summary 2025 me` - Generate 2025 summary for current git user
