Walk the user through setting up their lead finder configuration. Ask each question one at a time and wait for their answer before continuing. Be conversational and friendly.

Ask these questions in order:

1. "What industry or niche are you targeting? (e.g. plumbers, e-commerce brands, real estate agencies, SaaS companies)"

2. "What location should I search in? (e.g. Austin TX, United States, London UK — or 'anywhere' for no location filter)"

3. "What size company are you looking for?"
   Give these options:
   - Solo / freelancer (1 person)
   - Small (2–50 employees)
   - Medium (50–500 employees)
   - Large (500+ employees)
   - Any size

4. "Who at the company do you want to reach? (e.g. CEO, founder, marketing manager, sales director, office manager)"

5. "Any extra filters or keywords? (e.g. 'must have a website', 'B2B only', 'bootstrapped', 'funded' — or press enter to skip)"

6. "How many leads do you want per search run? (e.g. 10, 25, 50)"

7. "What format should leads be saved in?"
   Give these options:
   - Markdown only (.md)
   - CSV only (.csv)
   - Both Markdown and CSV

8. "Would you like me to draft outreach emails for each lead after a search?"
   Give these options:
   - Yes — draft emails automatically after every search
   - No — I'll run `/draft-emails` manually when I want them

   If yes, ask: "Briefly describe who you are and what you're offering (this will be used to personalize the emails): "

9. "Where should I save your lead files?"
   Give these options:
   - Default (outputs/ folder inside this project)
   - Custom folder — I'll enter a path

   If they choose custom, ask: "Enter the full folder path where you want files saved (e.g. C:\Users\you\Documents\Leads or ~/Documents/Leads)"
   Accept whatever path they provide exactly as typed. Remind them the folder must already exist.

Once you have all answers, save them to `config/config.json` in this exact format:

```json
{
  "industry": "<their answer>",
  "location": "<their answer>",
  "company_size": "<their answer>",
  "contact_role": "<their answer>",
  "extra_filters": "<their answer or empty string>",
  "leads_per_run": <number>,
  "output_format": "<markdown | csv | both>",
  "auto_draft_emails": <true | false>,
  "sender_context": "<their description of who they are and what they offer, or empty string>",
  "output_folder": "<absolute path they entered, or empty string for default>",
  "last_updated": "<today's date YYYY-MM-DD>"
}
```

After saving, confirm: "Your config is saved! Run `/find-leads` to search for leads now, or `/schedule-leads` to set up automatic runs."
