# Project Showcase — PRD

## Overview
A permanent, live GitHub Pages site displaying all of Mike & Otto's shipped projects. Dark, polished visual design matching the pipeline-showcase aesthetic. Updated daily at 4:30 AM automatically by Otto.

## Live URL
`https://mikehelm.github.io/project-showcase/`

## Core Features

### 1. Project Grid
- Cards for each project in a responsive grid (2-3 columns)
- Each card shows:
  - Project name + emoji/icon
  - One-line tagline
  - 2-3 sentence description (the "elevator pitch")
  - Tech stack badges (SvelteKit, Swift, React, Python, etc.)
  - Status badge: 🟢 Live | 🟡 In Progress | 🔵 Research | ⚪ Paused
  - Progress bar (0-100%)
  - Live URL link (if deployed)
  - "Built in X hours" stat
  - "Time saved: X%" stat
  - Key highlight (e.g. "9.47/10 PRD score", "200 secrets", "3 TTS engines")
- Cards have subtle colored left border matching project category
- Hover: slight lift + glow

### 2. Hero Section
- "Otto × Mike — Shipped Projects" title
- Animated stat counters: Total projects, Total hours saved, Average quality score, Total PRD pages
- Subtle background glow animation

### 3. Categories
- 🎨 Creative Tools (StyleForge, MindMapForge, ContentForge)
- 🤖 AI Infrastructure (AI-OS, Otto Dashboard, Otto Voice, MCP Server)
- 🌐 Web Apps (TellAnything, YouTube Insights)
- 📊 Showcases (Pipeline Showcase, Velocity Report)
- Filter buttons at top to show/hide categories

### 4. Project Detail Expansion
- Click card → expands to show:
  - Full description (2-3 paragraphs)
  - Architecture overview (what models, what tools)
  - The pipeline used (Research → PRD → Review → Build → QA → Ship)
  - Screenshots or key metrics
  - Links: Live site, GitHub repo, PRD location

### 5. Timeline View (toggle)
- Alternate view: vertical timeline showing when each project was built
- Date markers on left, project summaries on right
- Shows the pace of shipping

### 6. Stats Footer
- Total projects shipped
- Combined human-equivalent hours saved
- Average quality score
- "Built with the Specification-Driven Pipeline"
- Link to pipeline-showcase page

## Data Architecture

### Source: `project-showcase-data.json`
Located at `/Users/otto/.openclaw/workspace/.otto-showcase.json`

```json
{
  "projects": [
    {
      "id": "tellanything",
      "name": "TellAnything",
      "emoji": "🤫",
      "tagline": "Anonymous secrets sharing platform",
      "description": "Full-featured anonymous confession platform with reaction system, threaded replies, Top 10 leaderboards, and 200+ original secrets with 1,178 AI-generated replies.",
      "category": "web",
      "status": "live",
      "progress": 85,
      "liveUrl": "https://mikehelm.github.io/tellanything/",
      "repoUrl": "https://github.com/mikehelm/tellanything",
      "techStack": ["HTML/CSS/JS", "GitHub Pages"],
      "builtInHours": 6,
      "humanEquivHours": 80,
      "highlight": "200 secrets + 1,178 replies",
      "dateBuilt": "2026-02-14",
      "visible": true
    }
  ],
  "lastUpdated": "2026-02-16T22:00:00+07:00"
}
```

### Visibility Control
- `visible: true/false` in each project entry
- Otto reads this file before generating the page
- Mike tells Otto "hide X project" → Otto sets `visible: false`
- Hidden projects are NOT deleted, just not rendered

## Visual Design

### Theme (matching pipeline-showcase)
- Background: #06060c / #0a0a0f
- Card bg: #0d0d14 with 1px border rgba(255,255,255,0.06)
- Accent colors per category:
  - Creative: amber #f5a623
  - AI Infra: purple #b46aff
  - Web Apps: cyan #4ae0e0
  - Showcases: green #50dc78
- Font: SF Mono / Fira Code / JetBrains Mono (monospace)
- Subtle glow effects on hover
- Gradient top border on container (like spawn-team card)
- Animated stat counters on scroll

### Responsive
- 3 columns on desktop (>1200px)
- 2 columns on tablet (800-1200px)
- 1 column on mobile (<800px)

## Daily Update Process (4:30 AM Bangkok)
1. Otto reads `.otto-showcase.json` for current project list
2. Checks `.otto-projects.json` for latest status/progress
3. Syncs any changes (new projects, updated progress, status changes)
4. Regenerates the static `index.html` with fresh data
5. Commits and pushes to `mikehelm/project-showcase`
6. Cron job: `sessionTarget: "isolated"`, `payload.kind: "agentTurn"`

## Tech Stack
- Single `index.html` file (HTML + CSS + JS, no build step)
- Data embedded as JSON in a `<script>` tag (generated from `.otto-showcase.json`)
- GitHub Pages deployment
- No framework, no dependencies

## File Structure
```
project-showcase/
├── index.html          # The full page (generated)
├── CODING-STANDARDS.md # Codex reads this
└── README.md
```

## Build Process
- **Initial build**: Full Codex CLI (`codex exec --full-auto`)
- **Daily updates**: Fast Codex CLI (`codex exec --full-auto` with targeted prompt)
- Both documented in the skill

## Quality Target
- 9/10 visual quality
- All projects accurate and up-to-date
- Responsive on mobile
- Animations smooth (60fps)
- Load time <1s (single file, no external deps)
