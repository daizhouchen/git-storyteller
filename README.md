# git-storyteller

> Turn boring Git history into a cinematic project documentary.

A [Claude Code](https://claude.ai/code) skill that transforms Git repository commit history into a beautiful, interactive HTML narrative report — complete with timelines, contributor profiles, dramatic events, and code evolution charts.

## Features

- **Interactive Timeline** — Commit activity visualized as bar charts by month
- **Contributor Leaderboard** — Ranked contributor profiles with commit counts and date ranges
- **Dramatic Events Detection** — Late-night commits (22:00–06:00), reverts, hotfixes, critical fixes
- **Milestone Tracking** — Tags, merge commits, large refactors (>500 lines changed)
- **Code Volume Chart** — Additions vs deletions over time as an area chart
- **File Heatmap** — Top 30 most-changed files

## Installation

Add this skill to Claude Code:

```bash
claude skill add daizhouchen/git-storyteller
```

## How It Works

1. **Collect** — Runs `git log`, `git shortlog`, `git tag` to gather raw data
2. **Analyze** — `scripts/analyze.py` parses data into structured JSON with statistics
3. **Render** — `scripts/render.py` generates a standalone HTML report with Chart.js

## Manual Usage

```bash
# Analyze a git repository
python3 scripts/analyze.py /path/to/repo

# Generate the HTML report
python3 scripts/render.py
# Output: project-story.html
```

## Trigger Phrases

Say any of these to Claude Code and this skill activates:

- "帮我看看这个仓库的历史"
- "项目回顾" / "贡献分析"
- "git 可视化" / "代码故事"

## Project Structure

```
git-storyteller/
├── SKILL.md              # Skill definition and workflow
├── scripts/
│   ├── analyze.py        # Git data collection and analysis
│   └── render.py         # HTML report generation
└── README.md
```

## Requirements

- Python 3.8+
- A local Git repository
- No external Python packages needed (uses only stdlib + subprocess)

## Output

A standalone `project-story.html` file with:
- Dark theme responsive design
- Chart.js interactive charts (loaded from CDN)
- Zero external dependencies — just open in any browser

## Limitations

- Repos with >100k commits are limited to the most recent 2 years
- Only analyzes metadata (commits, authors, file stats) — never reads file contents

## License

MIT
