# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Stitch Simple Drum Academy** ("Rhythm Studio") is a collection of standalone HTML screens for a drum learning mobile app. Each subfolder contains a `code.html` (the screen implementation) and a `screen.png` (reference screenshot). There is no build system — files open directly in a browser.

## Screens

| Folder | Screen |
|---|---|
| `drum_pad_1/` | Drum pad layout variant 1 |
| `drum_pad_2/` | Drum pad layout variant 2 |
| `progress_tracker/` | User progress dashboard |
| `quick_lessons/` | Lesson browsing screen |
| `technique_library/` | Drumming technique reference |

## Design System ("Velocity Neon")

The canonical design spec lives in `velocity_neon/DESIGN.md`. Key rules that affect every screen:

### Tech Stack (per file)
- **Tailwind CSS** loaded via CDN (`https://cdn.tailwindcss.com?plugins=forms,container-queries`) — no build step
- **Google Fonts**: `Space Grotesk` (headlines/labels) and `Be Vietnam Pro` (body)
- **Material Symbols Outlined** icon font

### Color Tokens (defined in each file's inline `tailwind.config`)
All screens share the same token set. Key values:
- `surface` / `background`: `#0e0e0e`
- `surface-container`: `#1a1919`, `surface-container-high`: `#201f1f`, `surface-container-highest`: `#262626`
- `primary`: `#89acff` (electric blue), `primary-container`: `#739eff`
- `secondary`: `#fd9000` (punchy orange)
- `tertiary`: `#f3ffcd` (vibrant lime — success/perfect states only)
- `on-surface`: `#ffffff`, `on-surface-variant`: `#adaaaa`
- `outline-variant`: `#494847`

### Typography
- `font-headline` / `font-label` → `Space Grotesk`
- `font-body` → `Be Vietnam Pro`

### Core Design Rules
- **No borders or dividers** — use tonal background shifts and 32px gaps instead
- **Ghost Border fallback**: `outline-variant` at 15% opacity only (never 100% opaque)
- **Glassmorphism** for floating controls: `surface-container-high` at 60% opacity + `backdrop-blur-[20px]` (utility class `.glass-effect`)
- **Ambient glow shadows** instead of Material drop shadows: high-blur (`40–60px`), low-opacity (`rgba(255,255,255,0.04)`) white glow
- **Drum pad press**: `active:scale-90 active:translate-y-1` + inner glow shadow
- All transitions must feel "snappy" with bounce — use `transition-all`, `active:scale-95`/`active:scale-90`

### Layout Structure (shared across all screens)
```
<header>  — fixed top bar with menu + logo + avatar
<main>    — pt-24 pb-32 scrollable content area (clears header + bottom nav)
<nav>     — fixed bottom nav bar with 4 tabs: Drum Pad, Techniques, Lessons, Progress
```
Active bottom nav item uses `secondary` (#fd9000) color + drop shadow glow. Inactive items are `on-surface` at 40% opacity.

### Surface Hierarchy
Layer UI as physical depth: `surface` (base) → `surface-container` (stage) → `surface-container-highest` (interactive elements like drum pads/cards). Never use pure `#000000` for surfaces — use `surface-container-lowest` (`#000000`) only for deepest backgrounds.

### Components
- **Drum pads**: round (`rounded-full`), `surface-container-highest` bg, `border-b-4 border-black/40` for physical depth, glow on active state
- **Rhythm cards**: `surface-container-high` bg, 24px internal padding, no dividers
- **Progress bar ("Metronome")**: vertical block series transitioning from `surface-variant` → `tertiary` with strobe animation
- **Chips**: `rounded-full`; unselected = `surface-container-highest` bg; selected = `secondary` bg + `on-secondary` text
- **Input fields**: no background fill, only bottom ghost border; active state → 100% `primary` border with glow
