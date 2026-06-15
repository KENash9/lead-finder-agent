# Lead Finder Agent

This agent finds business leads via web search based on your target criteria.

## Getting Started

Run `/setup` first — it will ask you a few questions and save your preferences to `config/config.json`.

## Commands

- `/setup` — One-time onboarding: set your target industry, location, company size, contact role, output format, and email preferences
- `/find-leads` — Run a lead search using your saved config. Pass a niche to override for one run: `/find-leads plumbers in Austin`
- `/draft-emails` — Draft personalized cold outreach emails for your most recent leads. Pass a filename to target a specific run: `/draft-emails leads-2026-06-14-plumbers`
- `/schedule-leads` — Set up automatic recurring lead searches on an interval you choose

## Output

Results are saved to `outputs/` with a date timestamp. Depending on your format setting:

- `outputs/leads-YYYY-MM-DD.md` — human-readable markdown
- `outputs/leads-YYYY-MM-DD.csv` — spreadsheet-ready CSV (importable into Excel, Google Sheets, CRMs)
- `outputs/emails-YYYY-MM-DD.md` — drafted outreach emails per lead

Each lead includes company name, website, location, description, and contact info (where findable).

## Config

Your preferences live in `config/config.json` (gitignored — stays local to your machine).
Run `/setup` again any time to update them.
