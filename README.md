# The AI Negligence Awards

Cataloging the finest moments in AI security, privacy, and "what were they thinking?" since the industry modus operandi became move fast and break everything.

Inspired by [Corey Quinn's S3 Bucket Negligence Award](https://www.lastweekinaws.com).

## What Is This?

A static website tracking AI security incidents, data leaks, disasters, and notable news events. Each incident is assigned a snarky award category and rated by severity.

### Award Categories

- **Oops, Was That Public?** — data leaks and exposed models
- **Move Fast and Break Everything** — privacy violations
- **Hallucinari Ex Machina** — AI failures with real consequences
- **YOLO!!** — security vulnerabilities in AI systems
- **Trust Me, I'm an Algorithm** — bias, discrimination, harmful outputs
- **The Insider Threats We Made Along the Way** — insider theft, corporate espionage
- **Achievement Unlocked: Regulatory Action** — incidents that triggered government response

## Running Locally

No build step, no dependencies. Just serve the files over HTTP:

```bash
python3 -m http.server 8080
```

Then open [http://localhost:8080](http://localhost:8080).

> Opening `index.html` directly via `file://` won't work because the browser blocks `fetch()` requests to local JSON files.

## Project Structure

```
├── index.html        # Self-contained site (HTML + CSS + JS)
├── incidents.json    # Incident database
└── README.md
```

## Adding an Incident

Add an entry to `incidents.json` following this schema:

```json
{
  "id": "unique-slug",
  "title": "Short headline",
  "date": "YYYY-MM-DD",
  "organization": "Company name",
  "award": "One of the award categories above",
  "severity": "critical | high | medium | low",
  "summary": "2-3 sentence snarky summary",
  "details": "Longer description of what happened",
  "impact": "What was affected",
  "sources": [
    { "title": "Source Name", "url": "https://..." }
  ],
  "tags": ["relevant", "tags"]
}
```

No build step needed — just save the file and refresh.

## Disclaimer

This site is for informational and educational purposes. Incident descriptions include editorial commentary for entertainment. All facts are sourced from public reporting. Source links are provided for each incident.

This website was built with AI, because irony is dead.
