# marketing-frameworks

An agent skill that teaches AI coding assistants 10 classic marketing, psychology and prioritisation frameworks, and how to *apply* them to real work: plans, pricing pages, positioning, brand audits, onboarding flows and campaign frequency.

Works with **Claude Code**, **OpenAI Codex** and **Gemini CLI**. All three read the same open `SKILL.md` format.

## What's inside

| Framework | Use it for | Evidence |
|---|---|---|
| RACE (Plan, Reach, Act, Convert, Engage) | Digital marketing plans and funnel KPIs | Practitioner model |
| Decoy effect | Pricing tiers and bundles | Strong in lab, weaker in field |
| STP (Segmentation, Targeting, Positioning) | Choosing who to sell to and how to stand out | Foundational |
| Eisenhower Matrix | Prioritising tasks and content backlogs | Heuristic |
| Rule of 7 | Ad frequency and touchpoint planning | Folklore (the number is) |
| Pygmalion effect | Managing teams, creators and sales reps | Real but small, disputed |
| 4 Ps (marketing mix) | Product, price, place, promotion decisions | Foundational |
| Zeigarnik effect | Progress bars, onboarding, cliffhangers | Memory claim failed to replicate |
| Brand resonance pyramid (Keller CBBE) | Brand strategy and audits | Widely used model |
| Theory of planned behavior | Behavior-change messaging | Strong |

**Main use: three playbooks.** The skill is built around applying the frameworks to websites, marketing plans and social media. Each playbook sequences the frameworks for that job, with a framework-to-tactics-to-measures table, a fill-in output template, a worked example with a fictional business and common mistakes:

- `apply-websites.md` - landing pages, homepages, pricing pages, onboarding and signup flows, CRO audits
- `apply-marketing-plans.md` - a full marketing plan end to end
- `apply-social-media.md` - strategy, pillars, calendars, hooks, captions, ads, community, short-form video

Each framework has its own reference file with a definition, step-by-step application, a worked example, common mistakes and an honest evidence note. `SKILL.md` routes the agent to the one or two frameworks a task actually needs.

```
skills/marketing-frameworks/
├── SKILL.md
└── references/
    ├── apply-websites.md
    ├── apply-marketing-plans.md
    ├── apply-social-media.md
    ├── race-framework.md
    ├── decoy-effect.md
    ├── stp-model.md
    ├── eisenhower-matrix.md
    ├── rule-of-7.md
    ├── pygmalion-effect.md
    ├── 4ps-marketing-mix.md
    ├── zeigarnik-effect.md
    ├── brand-resonance-pyramid.md
    └── theory-of-planned-behavior.md
```

## Install

Clone once, then copy or symlink the skill folder to where your tool looks for skills.

```bash
git clone https://github.com/mayanthacreates/marketing-frameworks-skill.git
cd marketing-frameworks-skill
```

**Claude Code**

```bash
# personal (all projects)
cp -r skills/marketing-frameworks ~/.claude/skills/
# or per project
cp -r skills/marketing-frameworks .claude/skills/
```

**OpenAI Codex**

```bash
# personal
cp -r skills/marketing-frameworks ~/.agents/skills/
# or per repo
cp -r skills/marketing-frameworks .agents/skills/
```

**Gemini CLI**

```bash
# personal (~/.agents/skills also works)
cp -r skills/marketing-frameworks ~/.gemini/skills/
# or per project
cp -r skills/marketing-frameworks .gemini/skills/
```

Restart the tool. Check it loaded with `/skills` in Claude Code or Codex, or `gemini skills list` in Gemini CLI. Gemini skips project-level skills in folders it doesn't trust, so use the personal path or trust the folder. The skill triggers on its own when a task matches, or you can ask for it by name.

## Example prompts

- "Audit this landing page and pricing page for conversion, and give me a prioritised fix list."
- "Write a 90-day marketing plan for our small B2B SaaS using STP, the 4 Ps and RACE."
- "Plan four weeks of Instagram and TikTok content for a yoga studio, with pillars, hooks and a calendar table."
- "Use the RACE framework to audit our cafe's Instagram-to-order funnel."
- "Our SaaS has two plans at $19 and $49. Should we add a decoy tier?"
- "Write an STP and positioning statement for a gym aimed at busy professionals."
- "Quiz me on these 10 marketing frameworks, one question at a time."
- "Is the rule of 7 actually true?"

## Credits

Topic list inspired by a short-form "how well do you know marketing? (niche edition)" video by @gigi.yaps. The explanations, examples and evidence notes are original writing. The sources behind each framework are named in its reference file.

## License

MIT
