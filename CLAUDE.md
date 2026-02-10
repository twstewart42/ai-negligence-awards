# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A static website — "The AI Negligence Awards" — tracking AI security incidents with snarky commentary. No frameworks, no build step, no dependencies.

## Running Locally

```bash
python3 -m http.server 8080
```

Must be served over HTTP; `file://` breaks the `fetch()` call to `incidents.json`.

## Architecture

Two files, tightly coupled:

- **`index.html`** — self-contained single file with all HTML, CSS, and vanilla JS. Loads `incidents.json` via fetch at runtime. Handles filtering, search, sorting, and card rendering entirely client-side.
- **`incidents.json`** — flat JSON array of incident objects. This is the database. All content lives here.

## Critical Coupling: Award Names

Award category names must match **exactly** between `incidents.json` (each incident's `"award"` field) and the `AWARD_ICONS` object in `index.html` (~line 430). If you rename a category, update both files or filtering breaks silently.

Current award categories:
- `Oops, Was That Public?`
- `Move Fast and Break Everything`
- `Hallucinari Ex Machina`
- `YOLO!!`
- `Trust Me, I'm an Algorithm`
- `The Insider Threats We Made Along the Way`
- `Achievement Unlocked: Regulatory Action`
- `Skynet Is Self-Aware`

## Adding Incidents

Append to the JSON array in `incidents.json`. Required fields:

```json
{
  "id": "unique-slug",
  "title": "Short headline",
  "date": "YYYY-MM-DD",
  "organization": "Company name",
  "award": "Must match an AWARD_ICONS key exactly",
  "severity": "critical | high | medium | low",
  "summary": "2-3 sentence snarky summary",
  "details": "Longer factual description",
  "impact": "What was affected",
  "sources": [{"title": "...", "url": "..."}],
  "tags": ["lowercase", "hyphenated"]
}
```

Validate JSON after editing: `python3 -c "import json; json.load(open('incidents.json'))"`

## Tone

Summaries are written in a snarky, tongue-in-cheek voice (Corey Quinn style). Details and impact sections are factual. All incidents must include real source URLs.

## Stats Bar

The damages figure (`$113B+`) in `updateStats()` (~line 497 in `index.html`) is hardcoded. Update it manually when adding incidents with significant financial impact.
