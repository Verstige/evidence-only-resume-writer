# Evidence-Only Resume Writer: No Adjectives, Just Proof

> Write a resume and bio from what you actually shipped. No adjectives, no invented impact — just concrete work, real numbers, and the evidence behind every claim.

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg) ![Claude Code](https://img.shields.io/badge/Claude_Code-skill-blueviolet.svg) [![Available on Agensi](https://img.shields.io/badge/Agensi-%245-ff5a5f.svg)](https://agensi.io/skills/evidence-only-resume-writer-no-adjectives-just-proof)

## What it does

Write resume and bio copy from real project evidence.

Write resume bullets, bios, cover-letter copy, and interview talking points
that are grounded in what the user actually built — not what they remember
building.

## The failure it prevents

The cases that cost time are specific, and they are written down:

- **Don't inflate.** "Led" for work where the user was one of several
- **Don't write a generic bio with the user's name swapped in.** If the
- **Don't bury the strongest claim.** The best 1-2 sentences belong in the
- **Don't produce only the format asked for.** "Under 600 characters" means
- **Don't guess a metric that would make the claim stronger.** If you can't

## When to use it

- "Write me a bio" / "short bio for a job application" / "resume content"
- "Help me fill out this application" / "what should I put on this form"
- "What should I say about X for a [role type] position"
- "Turn this project into resume bullets"
- "Do I have enough to apply for [role]?"
- A live job application with a text field and a character limit

## What's inside

```
plugins/
└── evidence-only-resume-writer/
    ├── .claude-plugin/plugin.json
    └── skills/evidence-only-resume-writer/
        ├── SKILL.md
```

## Install

Add this repo as a Claude Code marketplace, then install the skill:

```bash
claude plugin marketplace add Verstige/evidence-only-resume-writer
claude plugin install evidence-only-resume-writer@evidence-only-resume-writer
```

Or copy the skill straight into your skills directory:

```bash
git clone https://github.com/Verstige/evidence-only-resume-writer.git
cp -R evidence-only-resume-writer/plugins/evidence-only-resume-writer/skills/evidence-only-resume-writer ~/.claude/skills/
```

## Usage

The skill activates on the work it describes. Ask for the outcome, and it
supplies the method:

```
> "write a resume from real project evidence"
```

## License

MIT. See [LICENSE](LICENSE).

---

**Also available as a paid skill on Agensi** — $5. Install it with one command, no clone required:

[agensi.io/skills/evidence-only-resume-writer-no-adjectives-just-proof](https://agensi.io/skills/evidence-only-resume-writer-no-adjectives-just-proof)

Part of the [Verstige](https://github.com/Verstige) skills portfolio. More at [github.com/Verstige](https://github.com/Verstige).
