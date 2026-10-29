# Playbook: websites

**When to use this file:** building, rewriting or auditing a landing page, homepage, pricing page, product page, onboarding or signup flow, or running a conversion (CRO) review. Open this first, then the per-framework files it links to.

Why this order: a page converts when the right person (STP) sees a clear promise (position), believes it (brand pyramid), finds the next step easy (TPB), and sees a price that makes sense (4 Ps, decoy). Fixing the page before knowing who it is for just polishes the wrong message.

Steps marked "only if relevant" apply only when the page has that feature or the leak points there. Skip the rest.

## Workflow

1. **Name the page's one job and its one behavior.** "Start a free trial", "book a class", "request a quote". Specific action, specific audience ([TPB](theory-of-planned-behavior.md)).
2. **Fix the audience and position (STP).** Pick the one segment this page speaks to and write the positioning sentence. The hero headline is that sentence in plain words. If the site serves several segments, give each its own page ([STP](stp-model.md)).
3. **Find the stage that leaks (RACE).** Is the problem Reach (nobody arrives), Act (arrive, don't engage), or Convert (engage, don't act)? Pull the user's own analytics. Do not guess a "good" rate; record the baseline and compare later. If there are no analytics, install tracking first, take a 2-week baseline, and meanwhile audit qualitatively ([RACE](race-framework.md)).
4. **Diagnose the barrier (TPB).** Which factor is low for visitors who stop? Attitude ("is this worth it?") is addressed by benefits and proof. Norms ("do people like me use it?") by testimonials and named customers. Control ("can I do this easily?") by shorter forms, clear pricing, fewer steps. Diagnose with 5-10 short customer interviews, an on-page survey or support tickets; if there is no data, state the assumption. TPB is a diagnostic checklist; moving a factor may not change behavior, so test.
5. **Check the Ps (4 Ps).** Price and Product must be visible and coherent with the position. Place = where checkout or booking happens. Promotion = how traffic arrives, which sets what the visitor expects on landing ([4 Ps](4ps-marketing-mix.md)).
6. **Decide the proof the page needs (brand pyramid).** Unknown brand: make name and visuals recognisable. Known but unproved: add performance proof and reviews. Use it to choose proof, not layout ([brand pyramid](brand-resonance-pyramid.md)).
7. **Pricing pages only if relevant: design the options (decoy).** Decoy = same or higher price than the target and worse on every attribute, but better than the cheaper option on at least one. All options real and honestly described; A/B test it and keep the version that wins on the user's own metric ([decoy](decoy-effect.md)).
8. **Flows only if relevant: add progress (Zeigarnik).** Onboarding and signup can show a started task with a small next step, and abandoned-flow reminders can resume it. Lean on the urge to finish, not on any memory claim ([Zeigarnik](zeigarnik-effect.md)).
9. **Plan the repeat visits (rule of 7).** Many visitors do not convert on the first visit. Add retargeting, email capture or a "save for later" path, and judge frequency by your own data, not a magic number ([rule of 7](rule-of-7.md)).
10. **Prioritise the fix list (Eisenhower).** Do now, schedule, delegate, drop. A broken checkout is Do; a full redesign is Schedule ([Eisenhower](eisenhower-matrix.md)).
11. **Set up the test and the measures** below, then re-measure after changes.

Frameworks that do not fit here: **Pygmalion** is about managing people, so it does not shape page copy (small, contested effect; relevant only if you manage the writers or designers). **Brand pyramid** is a whole-brand diagnostic, not a page layout.

## Framework to tactics to measures

| Framework | Tactics on a website | Measure |
|---|---|---|
| STP | One segment per page; hero headline states who it is for and the benefit | Conversion by traffic source and segment; message match between ad and page |
| RACE | Page assigned to a funnel stage; one primary call to action | Stage KPI: visits (Reach), clicks or engaged sessions (Act), completions (Convert), return rate (Engage) |
| 4 Ps | Price and product visible without hunting; short checkout path | Drop-off at each step; pricing page exits |
| TPB | Benefits and proof (attitude), logos and reviews (norms), fewer fields and clear steps (control) | Form completion rate; step drop-off; support questions about "how" or "how much" |
| Brand pyramid | Recognisable name and visuals; proof such as specs, demos, reviews, case studies | Branded search volume, review rating and count, repeat visitors |
| Decoy | Tiers where one option is worse than the target on every attribute | Target plan share and revenue per visitor (A/B test) |
| Zeigarnik | Progress indicator, pre-ticked first step, resume link | Flow completion; return-to-finish rate |
| Rule of 7 | Retargeting, email capture, content for return visits | Returning-visitor conversion; assisted conversions |
| Eisenhower | Ranked audit backlog | Share of Do and Schedule items shipped per month |

Measurement methods: speed = PageSpeed Insights and Core Web Vitals field data. Tracking = complete a test conversion end to end and confirm each event fires. If the page receives paid traffic, also send conversions server-side (Conversions API with a shared `event_id` for deduplication) and the right events, such as a booking event; see [apply-paid-ads.md](apply-paid-ads.md) and [paid-media-metrics.md](paid-media-metrics.md).

## Output template: page audit

```
# Page audit: [page name and URL]
Job of the page: [one behavior, one audience]
Baseline (user's own numbers): [visits, conversion, drop-off points; or "not yet measured"]

## Findings
| # | Area | What I found | Framework | Barrier (attitude / norms / control) | Fix | Priority (Do / Schedule / Delegate / Drop) |
|---|------|--------------|-----------|---------------------------------------|-----|---------------------------------------------|

## Checklist
- [ ] Headline says who it is for and the benefit (STP)
- [ ] One primary call to action, repeated at natural points
- [ ] Proof near the claim: reviews, numbers, named customers (attitude, norms)
- [ ] Price or "how pricing works" visible (4 Ps, control)
- [ ] Form or checkout asks only what is needed (control)
- [ ] Tiers have a clear target plan; decoy test planned if relevant
- [ ] Flow shows progress and a resume path
- [ ] Return-visit path exists (email capture, retargeting)
- [ ] Mobile and speed checked (PageSpeed Insights, field data)
- [ ] Tracking confirmed by a test conversion

## Test plan
Hypothesis | Change | Metric | Run length | Decision rule
```

## Worked example: small B2B SaaS pricing page

Business: "TidyBooks", invoicing software for freelancers. Job: start a 14-day free trial. Audience: freelance designers and consultants. Position: "For freelancers who hate chasing payments, TidyBooks is the invoicing tool that sends reminders for you, unlike spreadsheets and general accounting suites." Analytics show plenty of pricing views but few trial starts, so the leak is Convert. Baseline (fictional example): to be pulled from analytics before any change. Five short interviews with lapsed visitors: attitude fine, norms weak, control weak.

```
# Page audit: TidyBooks /pricing
Job of the page: start a 14-day free trial; freelancers
Baseline: trial starts per pricing visit, from analytics (recorded before changes)

## Findings
| # | Area | What I found | Framework | Barrier | Fix | Priority |
|---|------|--------------|-----------|---------|-----|----------|
| 1 | Button area | No mention of card requirement; interviewees unsure | TPB | control | "No card needed" under the button | Do |
| 2 | Proof | No customer names or quotes | TPB, pyramid | norms | Three named freelancer testimonials near the plans | Do |
| 3 | Tiers | Two plans, big feature jump | Decoy | attitude | A/B test a third tier (table below) | Schedule |
| 4 | Post-signup | Empty dashboard, no guidance | Zeigarnik | control | 4-step checklist with "Create account" pre-ticked | Schedule |

## Checklist (abbreviated)
- [x] Headline says who it is for ("Get paid without the awkward emails")
- [ ] Proof near the claim: fails, see finding 2
- [ ] Form asks only what is needed: pass, email and password only
- [ ] Tracking confirmed by a test conversion: to do

## Test plan
Hypothesis: a worse-on-every-attribute third tier raises Team plan share | Change: add Solo Plus | Metric: Team share of paid plans, revenue per visitor | Run length: set before launch, whole weeks | Decision rule: keep only if the metric beats the two-tier page; otherwise remove
```

Tier table (target = **Team**; decoy = **Solo Plus**; all three are real, honestly described plans):

| Attribute | Starter $12 | Solo Plus $39 (decoy) | Team $39 (target) |
|---|---|---|---|
| Users | 1 | 1 | 5 |
| Invoices per month | 20 | 100 | Unlimited |
| Automatic payment reminders | Yes | Yes | Yes |
| Client import from CSV | No | No | Yes |

Solo Plus costs the same as Team and is worse on every attribute, and it beats Starter on invoice volume. Both keep the headline feature (reminders), so no plan looks fake. Because real products make the effect unreliable, the A/B test decides whether it stays.

## Common mistakes

- Optimising the page before deciding the audience, so the headline stays generic.
- Using an "industry average conversion rate" as the target instead of the page's own baseline.
- Shipping a decoy without a test, or adding a tier that looks fake and erodes trust.
- Applying every framework to every page. Apply only the steps your leak and page type warrant, and skip the rest; all nine applicable frameworks together are almost never needed.
- Adding social proof when the real barrier is control (a long form, hidden price).
- Making the call to action compete with five other links.
- Changing many things at once, so no test can say what worked.

## Go deeper

[STP](stp-model.md), [RACE](race-framework.md), [4 Ps](4ps-marketing-mix.md), [TPB](theory-of-planned-behavior.md), [brand pyramid](brand-resonance-pyramid.md), [decoy](decoy-effect.md), [Zeigarnik](zeigarnik-effect.md), [rule of 7](rule-of-7.md), [Eisenhower](eisenhower-matrix.md). For a whole plan see [apply-marketing-plans.md](apply-marketing-plans.md); for traffic sources see [apply-social-media.md](apply-social-media.md) and [apply-paid-ads.md](apply-paid-ads.md).
