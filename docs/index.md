# Agnostos

**Resume-driven outreach for research internships.** Agnostos is a free, open-source command-line tool
that helps students find research internships:

- **Who should I write to?** It ranks a professor list against your resume locally, for free, or builds
  the list for you from a research topic using the OpenAlex paper index.
- **What have they worked on lately?** It pulls each professor's recent first- and last-author papers.
- **What do I say?** One language-model call per professor returns an acceptance estimate and a short,
  specific, honest draft. Common AI tells are stripped out and unverifiable claims are flagged.
- **Is the address right?** It checks every address and can find the one each professor publishes on
  their own page.
- **When do I send it?** Slowly, from your own SMTP account; you can restrict sends to each recipient's local working hours.
- **Did they answer?** It tracks replies, auto-replies and bounces, and drafts follow-ups for you to approve.

First-contact drafts are saved locally for review; a scheduled live CLI sender can dispatch
eligible drafts over your SMTP account without approving each one individually. Replies
require approval before a live send.

## Get it

[Source on GitHub](https://github.com/Amandacode4/agnostos-aman){ .md-button .md-button--primary }
[Technical report (PDF)](Agnostos_Technical_Report.pdf){ .md-button }

```bash
git clone https://github.com/Amandacode4/agnostos-aman
cd agnostos-aman
pip install -r requirements.txt
cp .env.example .env                       # Windows: copy .env.example .env
python -m outreach.cli profile             # check resume parsing
python -m outreach.cli run --mode list     # score + draft into your xlsx
python -m outreach.cli send --dry-run      # preview the emails
```

The full command reference is in the
[README](https://github.com/Amandacode4/agnostos-aman#readme).

## Documentation

| | |
|---|---|
| Setup: [Windows](install-windows.md) · [macOS](install-macos.md) · [Linux](install-linux.md) | Step-by-step installation and daily use for each operating system |
| [FAQ](faq.md) | Common questions about costs, sending, replies and safety |
| [Diagnostics](diagnostics.md) | Health checks and fixes for every common error message |
| [Google Calendar](calendar.md) | One-time setup for meeting-slot checks and calendar holds |
| [Technical report (PDF)](Agnostos_Technical_Report.pdf) | Architecture and every scoring rule: matcher, discovery ranking, cost estimate, AI-tell score, address confidence, scheduling |

!!! note
    First-contact live sends require `--live` (or an explicitly configured unattended task using it);
    `--review` sends copies to your own inbox. Review workbook drafts before enabling unattended sends.
    Replies need approval and `replies --send --live`. The acceptance percentage is a model's estimate
    for ordering your list, not a statistical probability.
