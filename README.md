# Lead Finder Agent

A Claude Code agent that finds business leads via web search and drafts personalized outreach emails — shareable with anyone who has a Claude account.

## What it does

- Searches the web (and state business registries) for businesses matching your target niche, location, and company size
- Saves leads as Markdown and/or CSV with a date timestamp
- Drafts personalized cold outreach emails for each lead
- Runs on a schedule so fresh leads land automatically

---

## Requirements

- [Claude Code](https://claude.ai/code) (desktop app, CLI, or IDE extension)
- A Claude account (any plan)

No Python, no API keys, no extra installs.

---

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/lead-finder-agent.git
cd lead-finder-agent
```

### 2. Open in Claude Code

Open the `lead-finder-agent` folder in Claude Code (via the desktop app, VS Code extension, or CLI).

### 3. Run setup

Type the following in the Claude Code prompt:

```
/setup
```

You'll be asked a few questions:

| Question | Example answer |
|---|---|
| Target industry / niche | plumbers, SaaS companies, wedding photographers |
| Location | Austin TX, United States, anywhere |
| Company size | Solo, Small (2–50), Medium, Large, Any |
| Contact role | owner, CEO, founder, office manager |
| Extra filters | recently opened, no in-house accountant, B2B only |
| Leads per run | 10, 25, 50 |
| Output format | Markdown, CSV, or Both |
| Auto-draft emails | Yes / No |
| Output folder | Default (`outputs/`) or a custom path on your computer |

Your answers are saved to `config/config.json` (gitignored — stays local to your machine).

---

## Commands

### `/find-leads`

Runs a lead search using your saved config. Results are saved to your output folder with today's date.

```
/find-leads
```

**Search a specific niche for one run** (without changing your saved config):

```
/find-leads plumbers in Austin TX
/find-leads e-commerce brands
/find-leads recently opened restaurants Chicago
```

Leads are saved as:
- `leads-YYYY-MM-DD.md` — human-readable
- `leads-YYYY-MM-DD.csv` — importable into Excel, Google Sheets, or a CRM
- `leads-YYYY-MM-DD-[niche-slug].md/.csv` — when a niche override is used

The agent uses two search strategies every run:
1. **Web search** — finds businesses with an online presence
2. **State business registry** — searches for recently registered LLCs and companies that are brand new and likely don't have a bookkeeper, accountant, or vendor yet (flagged as "newly registered" in the output)

### `/draft-emails`

Drafts a personalized cold outreach email for each lead in your most recent leads file.

```
/draft-emails
```

**Target a specific leads file:**

```
/draft-emails leads-2026-06-14-plumbers
```

You'll be asked for your tone preference (casual, professional, short & punchy, or detailed). Emails are saved to `emails-YYYY-MM-DD.md` in your output folder.

> Tip: If you turned on auto-draft emails during `/setup`, emails are drafted automatically after every `/find-leads` run — no need to run this separately.

### `/schedule-leads`

Sets up automatic recurring lead searches.

```
/schedule-leads
```

Choose how often:
- Every day
- Every 3 days
- Weekly
- Weekdays only
- Custom interval

---

## Output files

All files are saved to your configured output folder (default: `outputs/` inside this project). They are gitignored so your leads stay private.

| File | Description |
|---|---|
| `leads-YYYY-MM-DD.md` | Lead list in readable markdown |
| `leads-YYYY-MM-DD.csv` | Lead list as spreadsheet |
| `emails-YYYY-MM-DD.md` | Drafted outreach emails |

---

## Re-running setup

Run `/setup` again any time to update your config — industry, location, output folder, email preferences, etc.

---

## Privacy

- Your `config/config.json` is gitignored and never leaves your machine
- Your output files (`outputs/`) are gitignored
- Nothing is sent anywhere except to Claude's web search when `/find-leads` runs

---

## Contributing

Pull requests welcome. Common improvements:
- New search strategies (LinkedIn, Google Maps, industry directories)
- Additional output formats (Notion, Airtable, HubSpot)
- More email tone options
- Multi-location support
