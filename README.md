# Marketing Frameworks Skill for Claude Code, Codex and Gemini CLI

**An open-source AI agent skill for marketing.** It teaches your AI assistant to audit websites and landing pages, write marketing plans, plan social media content and run paid ads (Meta, Google, TikTok) using 10 proven marketing frameworks and 15 performance-marketing metrics (ROAS, CAC, LTV, CPM, attribution, Conversions API, MMM).

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/format-SKILL.md-orange.svg)](https://agentskills.io)
![Claude Code](https://img.shields.io/badge/Claude%20Code-supported-8A63D2)
![Codex](https://img.shields.io/badge/OpenAI%20Codex-supported-10A37F)
![Gemini CLI](https://img.shields.io/badge/Gemini%20CLI-supported-4285F4)

**Install in one line (Claude Code):**

```
/plugin install marketing-frameworks --marketplace mayanthacreates/marketing-frameworks-skill
```

Using Codex, Gemini CLI or another agent? See [Install](#install) for the other one-line options.

## Why this skill

- **Built for real marketing work, not definitions.** Four playbooks (websites, marketing plans, social media, paid ads) each give the agent an ordered workflow, a fill-in template and a worked example, so you get a usable audit, plan or calendar instead of a lecture.
- **Honest about evidence.** Every framework carries an evidence rating. The rule of 7 is folklore, the Zeigarnik memory claim failed to replicate, the decoy effect is unreliable with real products. The agent tells you before you bet budget on it.
- **No invented benchmarks.** The skill tells the agent to work from your own numbers (break-even ROAS from your margin, affordable CAC from your LTV), not "industry average" figures.
- **Current platform facts.** Meta, Google and TikTok details (attribution windows, Schedule events, Conversions API dedup) are linked to official docs, dated, and flagged "verify in your ad account" where unconfirmed.
- **One file format, every agent.** Plain `SKILL.md` plus markdown references, so it works in Claude Code, OpenAI Codex, Gemini CLI and any tool that reads Agent Skills.

## What's inside

| Framework | Use it for | Evidence |
|---|---|---|
| RACE (Plan, Reach, Act, Convert, Engage) | Digital marketing plans and funnel KPIs | Practitioner model |
| Decoy effect | Pricing tiers and bundles | Strong with numeric tables, unreliable with real products |
| STP (Segmentation, Targeting, Positioning) | Choosing who to sell to and how to stand out | Foundational |
| Eisenhower Matrix | Prioritising tasks and content backlogs | Heuristic |
| Rule of 7 | Ad frequency and touchpoint planning | Folklore (the number is) |
| Pygmalion effect | Managing teams, creators and sales reps | Real but small, disputed |
| 4 Ps (marketing mix) | Product, price, place, promotion decisions | Foundational |
| Zeigarnik effect | Progress bars, onboarding, cliffhangers | Memory claim failed to replicate |
| Brand resonance pyramid (Keller CBBE) | Brand strategy and audits | Widely used model |
| Theory of planned behavior | Behavior-change messaging | Good for intention, modest for behavior |
| Paid media metrics (ROAS, CAC, LTV, CPM, attribution, CAPI, MMM and more) | Paid campaigns and ad reporting | Accounting identities plus platform-reported data; platform facts dated and cited |

**Main use: four playbooks.** The skill is built around applying the frameworks to websites, marketing plans, social media and paid ads. Each playbook sequences the frameworks for that job, with a framework-to-tactics-to-measures table, a fill-in output template, a worked example with a fictional business and common mistakes:

- `apply-websites.md` - landing pages, homepages, pricing pages, onboarding and signup flows, CRO audits
- `apply-marketing-plans.md` - a full marketing plan end to end
- `apply-social-media.md` - strategy, pillars, calendars, hooks, captions, community, short-form video
- `apply-paid-ads.md` - Meta, Google and TikTok campaigns: economics, tracking, structure, creative testing, weekly review sheet

**Paid-media metrics.** `paid-media-metrics.md` covers 15 concepts with a definition, formula, fictional worked calculation, how to read it and common mistakes: cost metrics (CPM, CPC, cost per result, CAC), return (ROAS, break-even ROAS, LTV, LTV:CAC), funnel and sales (full funnel, back-end selling, schedule events), measurement (attribution windows, Conversions API, media mix modeling, incrementality tests) and creative and delivery (fatigue, diversity, frequency capping). Platform facts are dated and linked to official docs where available; secondary sources and unverified items are labelled, and open points say "verify in your ad account".

Each framework has its own reference file with a definition, step-by-step application, a worked example, common mistakes and an honest evidence note. `SKILL.md` routes the agent to the matching playbook first, or to the one or two frameworks a single question needs.

```
skills/marketing-frameworks/
├── SKILL.md
└── references/
    ├── apply-websites.md
    ├── apply-marketing-plans.md
    ├── apply-social-media.md
    ├── apply-paid-ads.md
    ├── paid-media-metrics.md
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

**Claude Code** (plugin, recommended - gets updates):

```
/plugin install marketing-frameworks --marketplace mayanthacreates/marketing-frameworks-skill
```

or in two steps: `/plugin marketplace add mayanthacreates/marketing-frameworks-skill`, then `/plugin install marketing-frameworks@mayanthacreates-marketing`.

**Any agent** (Claude Code, Codex, Gemini CLI, Cursor and more) with the open-source [skills CLI](https://github.com/vercel-labs/skills):

```bash
npx skills add mayanthacreates/marketing-frameworks-skill
```

**Manual install.** Clone once, then copy the skill folder to where your tool looks for skills:

```bash
git clone https://github.com/mayanthacreates/marketing-frameworks-skill.git
cd marketing-frameworks-skill
```

| Tool | Personal (all projects) | Per project |
|---|---|---|
| Claude Code | `cp -r skills/marketing-frameworks ~/.claude/skills/` | `.claude/skills/` |
| OpenAI Codex | `cp -r skills/marketing-frameworks ~/.agents/skills/` | `.agents/skills/` |
| Gemini CLI | `cp -r skills/marketing-frameworks ~/.gemini/skills/` | `.gemini/skills/` |

Restart the tool. Check it loaded with `/skills` in Claude Code or Codex, or `gemini skills list` in Gemini CLI. Gemini skips project-level skills in folders it doesn't trust, so use the personal path or trust the folder. The skill triggers on its own when a task matches, or you can ask for it by name.

## Example prompts

- "Audit this landing page and pricing page for conversion, and give me a prioritised fix list."
- "Write a 90-day marketing plan for our small B2B SaaS using STP, the 4 Ps and RACE."
- "Plan four weeks of Instagram and TikTok content for a yoga studio, with pillars, hooks and a calendar table."
- "Use the RACE framework to audit our cafe's Instagram-to-order funnel."
- "Our SaaS has two plans at $19 and $49. Should we add a decoy tier?"
- "Write an STP and positioning statement for a gym aimed at busy professionals."
- "Plan a Meta lead-gen campaign for a home-cleaning service: work out break-even ROAS and affordable CAC first, then structure, tracking and a weekly review sheet."
- "Our Meta ROAS says 4.0 but the bank account disagrees. Walk me through attribution windows, Conversions API dedup and whether we need a lift test."
- "Quiz me on these 10 marketing frameworks, one question at a time."
- "Is the rule of 7 actually true?"

## Credits

Topic list inspired by a short-form "how well do you know marketing? (niche edition)" video by gigi.yaps (Instagram). The paid-media topic list (ROAS, CAC, LTV, CPM, CPR, CPC, back-end selling, attribution windows, MMM, creative fatigue and diversity, frequency, schedule events, full funnel metrics, Conversions API) is inspired by a short-form "Marketing IQ, scale edition" video by bryson.bowman (Instagram), which only names the concepts and shows one formula card each. The explanations, examples and evidence notes are original writing. The sources behind each framework are named in its reference file.

## Contributing

Issues and pull requests are welcome: new frameworks, better worked examples, corrections to platform facts (please link the official doc). If the skill helped you, a star helps other marketers find it.

## License

MIT
