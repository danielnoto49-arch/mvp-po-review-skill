# MVP Product Owner Review – a Claude Skill

A [Claude skill](https://code.claude.com/docs/en/skills) that turns Claude into a critical product owner. It interviews you about the MVP you built, asks for evidence instead of intent, rates readiness section by section, and writes a report you can act on before a demo, pilot, launch or investor meeting.

## What it does

1. **Captures context:** what the product is, who it's for, and the next milestone. Inside a repository, Claude reads the README and docs first.
2. **Interviews you:** 11 core sections, 2–4 questions per turn, with follow-ups when answers are vague.
3. **Rates each section:** Ready / Weak / Gap, with a one-line reason.
4. **Writes a report:** summary, scorecard, product fact sheet (features tagged as *tested*, *demo only* or *planned*), prioritized gaps and risks, contradictions, and recommendations.

### Core sections
Vision and problem · Personas and stakeholders · MVP scope · Architecture and deployment · Quality and reliability · Security, privacy and compliance · Operations and support · Positioning and competition · Business model · Measurement · Risks and limitations

### Optional modules
| Module | For products that… |
|---|---|
| AI / LLM | use language models, generative AI, agents or chat |
| Analytics / BI | answer business questions from data or show metrics |
| B2B on-premise | are installed in the customer's infrastructure |

Claude selects the modules that fit your product and inserts their questions into the matching core sections.

## Repository structure

```
skills/
└── mvp-po-review/
    ├── SKILL.md                    # Interview process, stance, rating scale
    └── references/
        ├── question-bank.md        # Core sections with questions and follow-ups
        ├── context.md              # MVP principles and further reading
        ├── report-template.md      # Structure of the final report
        └── modules/
            ├── ai-llm.md
            ├── analytics-bi.md
            └── b2b-on-prem.md
```

## Installation

### Claude Code (terminal or VS Code extension)

**Personal** – available in all your projects.

macOS / Linux:
```bash
git clone https://github.com/danielnoto49-arch/mvp-po-review-skill.git
mkdir -p ~/.claude/skills
cp -r mvp-po-review-skill/skills/mvp-po-review ~/.claude/skills/
```

Windows (PowerShell):
```powershell
git clone https://github.com/danielnoto49-arch/mvp-po-review-skill.git
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills" | Out-Null
Copy-Item -Recurse mvp-po-review-skill\skills\mvp-po-review "$env:USERPROFILE\.claude\skills\"
```

**Project** – only for one repository (commit it to share with your team). Run inside your project folder:
```bash
mkdir -p .claude/skills
cp -r path/to/mvp-po-review-skill/skills/mvp-po-review .claude/skills/
```

### Claude apps (claude.ai, desktop)
Zip the `skills/mvp-po-review` folder (the zip must contain the `mvp-po-review` folder at its root) and upload it as a custom skill in Claude's settings.

## Usage

Start it explicitly in Claude Code with `/mvp-po-review`, or just ask:

- "Review my MVP before the customer demo next week."
- "Run a PO review of this repo, we're starting a pilot in March."
- "Stress-test my product like a product owner would, focus on security and pricing."

Tip: run it inside the product's repository so Claude can check your answers against the code.

## Customizing

- **Add your own module:** create a file in `references/modules/`, note which core section each part belongs to, and add a row to the module table in `SKILL.md`.
- **Change the sections:** edit `references/question-bank.md`. Keep the "strong answer" lines; they are what Claude rates against.
- **Change the report:** edit `references/report-template.md`.

## License

MIT – see [LICENSE](LICENSE).
