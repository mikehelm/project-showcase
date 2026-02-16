# Coding Standards — Project Showcase

## File Limits
- Max 300 lines per file (single index.html is exempt but keep sections organized with clear comments)
- No external dependencies — everything inline
- No build step

## Style
- Dark theme matching pipeline-showcase aesthetic
- Background: #06060c / #0a0a0f
- Monospace font stack: SF Mono, Fira Code, JetBrains Mono
- Subtle animations (fade-in on scroll, hover lifts, counter animations)
- Category accent colors: Creative=#f5a623, AI Infra=#b46aff, Web Apps=#4ae0e0, Showcases=#50dc78

## Requirements
- Single index.html file
- Project data embedded as JSON in script tag
- Responsive: 3 cols desktop, 2 tablet, 1 mobile
- Each project card: name, emoji, tagline, description, tech badges, status, progress bar, live URL, stats
- Hero with animated counters
- Category filter buttons
- Click-to-expand detail view
- Timeline toggle view
- Stats footer
- Smooth 60fps animations
