# Keeping costs down on this project

## GitHub

- The workflow that deploys my site keeps running on every push to main. Keep it a single job, with no tests inside it, under 5 minutes. The rules below apply to all other workflows.
- Don't create new GitHub Actions workflows (anything in .github/workflows/) unless I ask for one. Run tests on my computer instead.
- For any other workflow that already exists:
  - Run it only on pull requests or by hand, not on every push.
  - Add a concurrency block with cancel-in-progress: true so a newer push cancels the older run.
  - Set timeout-minutes: 10 on every job.
  - Skip runs when only docs or text files changed (paths-ignore).
- Never use matrix builds or run several copies of a job side by side. Each copy is billed separately.
- No scheduled (cron) workflows unless I ask.
- Use the standard ubuntu-latest runner. Never use macOS or Windows runners; they cost 2 to 10 times more.
- Batch commits: push when a piece of work is done, not after every small change.
- Before adding anything that runs automatically or on a schedule, tell me what it will cost per run and per month.

## Claude itself

- If the app calls the Claude API, use the smallest model that does the job well (Haiku for simple tasks), and set a low max_tokens.
- Don't call the API in loops or on every keystroke or page load. Cache results that don't change.
- Never put an API key in the code or push it to GitHub.
- Set a monthly spending limit in the Anthropic console before anything goes live.
