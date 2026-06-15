Help the user set up automatic recurring lead searches.

First, check that `config/config.json` exists. If not, tell them to run `/setup` first and stop.

Then ask: "How often do you want to automatically search for leads?"

Give these options:
- Every day
- Every 3 days
- Weekly (every 7 days)
- Weekdays only (Mon–Fri)
- Custom interval

Once they choose, use the `/schedule` skill to create a scheduled routine that runs `/find-leads` on that interval.

After scheduling, confirm:
- What interval was set
- That results will be saved to the `outputs/` folder each run
- How to cancel: "Run `/schedule` and delete the routine, or use the Claude Code schedule manager"
