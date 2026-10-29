# Playbook: websites

**When to use this file:** building, rewriting or auditing a landing page, homepage, pricing page, product page, onboarding or signup flow, or running a conversion (CRO) review. Open this first, then the per-framework files it links to.

Why this order: a page converts when the right person (STP) sees a clear promise (position), believes it (brand pyramid), finds the next step easy (TPB), and sees a price that makes sense (4 Ps, decoy). Fixing the page before knowing who it is for just polishes the wrong message.

## Workflow

1. **Name the page's one job and its one behavior.** "Start a free trial", "book a class", "request a quote". Specific action, specific audience. This is the TPB definition step ([TPB](theory-of-planned-behavior.md)).
2. **Fix the audience and position (STP).** Pick the one segment this page speaks to and write the positioning sentence. The hero headline is that sentence in plain words. If the site serves several segments, give each its own page rather than one vague one ([STP](stp-model.md)).
3. **Find the stage that leaks (RACE).** Place the page in the funnel: is the problem Reach (nobody arrives), Act (arrive, don't engage), or Convert (engage, don't act)? Pull the user's own analytics for this. Do not guess a "good" rate; record the baseline and compare against it later ([RACE](race-framework.md)).
4. **Diagnose the barrier (TPB).** For visitors who stop, which factor is low? Attitude ("is this worth it?") is fixed by benefits and proof. Norms ("do people like me use it?") by testimonials and named customers. Control ("can I do this easily?") by shorter forms, clear pricing, fewer steps.
5. **Check the Ps (4 Ps).** Price and Product must be visible and coherent with the position. Place = where the checkout or booking happens. Promotion = how the traffic arrives, which sets what the visitor expects on landing ([4 Ps](4ps-marketing-mix.md)).
6. **Pricing pages only: design the options (decoy).** Decide the target plan, then test whether a near-dominated option helps. It is a hypothesis: run an A/B test and keep the version that wins on the user's own metric ([decoy](decoy-effect.md)).
7. **Flows only: add progress (Zeigarnik).** Onboarding and signup can show a started task with a small next step, and abandoned-flow reminders can resume it. Lean on the urge to finish, not on any memory claim ([Zeigarnik](zeigarnik-effect.md)).
8. **Plan the repeat visits (rule of 7).** Few visitors convert on the first view. Add retargeting, email capture or a "save for later" path, and judge frequency by your own data, not a magic number ([rule of 7](rule-of-7.md)).
9. **Prioritise the fix list (Eisenhower).** Sort audit findings into do now, schedule, delegate, drop. Broken checkout is Do; a full redesign is Schedule ([Eisenhower](eisenhower-matrix.md)).
10. **Set up the test and the measures** below, then re-measure after changes.

Frameworks that do not fit here: **Pygmalion** is about managing people, so it does not shape page copy (it helps only if you manage the writers or designers). **Brand pyramid** is a diagnostic for the whole brand; use it to decide what proof the page needs, not as a page layout.

## Framework to tactics to measures

| Framework | Tactics on a website | Measure |
|---|---|---|
| STP | One segment per page; hero headline states who it is for and the benefit; alternatives named honestly | Conversion by traffic source and segment; message match between ad and page |
| RACE | Page assigned to a funnel stage; one primary call to action | Stage KPI: visits (Reach), engaged sessions or clicks (Act), completions (Convert), return rate (Engage) |
| 4 Ps | Price and product visible without hunting; checkout path short | Drop-off at each step; pricing page exits |
| TPB | Benefits and proof (attitude), logos and reviews (norms), fewer fields and clear steps (control) | Form completion rate; step-by-step drop-off; support questions about "how" or "how much" |
| Brand pyramid | Salience: consistent name and visuals; performance proof: specs, demos; judgments: reviews, case studies | Branded search volume, review rating and count, repeat visitors |
| Decoy | Pricing tiers where one option is clearly worse than the target | Share of target plan before and after, revenue per visitor (A/B test) |
| Zeigarnik | Progress indicator, pre-ticked first step, resume link | Completion rate of the flow; return-to-finish rate |
| Rule of 7 | Retargeting, email capture, content that serves return visits | Returning-visitor conversion; assisted conversions in analytics |
| Eisenhower | Ranked audit backlog | Share of Do and Schedule items shipped per month |

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
- [ ] Mobile and speed checked
- [ ] Tracking works for each step

## Test plan
Hypothesis | Change | Metric | Run length | Decision rule
```

## Worked example: small B2B SaaS pricing page

Business: "TidyBooks", invoicing software for freelancers. Plans today: Starter $12 per month, Team $39 per month. The user reports many visitors reach pricing but few start a trial.

1. Job: start a 14-day free trial. Audience: freelance designers and consultants who invoice 5-30 clients.
2. Position: "For freelancers who hate chasing payments, TidyBooks is the invoicing tool that sends reminders for you, unlike spreadsheets and general accounting suites." Hero headline becomes "Get paid without the awkward emails."
3. RACE: traffic is fine, pricing views are fine, trial starts are low, so this is Convert. Baseline recorded from analytics before any change.
4. TPB interviews with five lapsed visitors: attitude is fine, norms are weak ("no one I know uses it"), control is weak ("do I need a card? can I import my clients?"). Fixes: three freelancer testimonials with names, "no card needed" under the button, an "import from CSV" line.
5. 4 Ps: Price is visible, but Starter and Team differ by many features, which makes the jump look big.
6. Decoy hypothesis: add a "Solo Plus" at $39 with 1 user and no reminders, worse than Team at the same price and better than Starter on invoice limits. Run it as an A/B test against the current two-tier page, since the effect is unreliable with real products. Keep it only if Team share or revenue per visitor improves; remove it otherwise.
7. Zeigarnik: after signup, show a 4-step checklist with "Create account" already ticked.
8. Rule of 7: add email capture for "email me this pricing comparison" and retarget pricing visitors with a case study, capped in frequency.
9. Eisenhower: Do now: testimonials, "no card needed", CSV line. Schedule: decoy test, onboarding checklist. Drop: full homepage redesign until Convert is fixed.
10. Measures: trial starts per pricing visit, Team share of paid plans, checklist completion.

## Common mistakes

- Optimising the page before deciding the audience, so the headline stays generic.
- Using "industry average conversion rate" as the target instead of the page's own baseline.
- Treating a decoy as a guaranteed lift and shipping it without a test, or adding a fake-looking tier that erodes trust.
- Stacking all nine frameworks on one page. Pick the two or three tied to the leak you found.
- Adding social proof when the real barrier is control (a long form, hidden price).
- Making the call to action compete with five other links.
- Changing many things at once, so no test can say what worked.

## Go deeper

[STP](stp-model.md), [RACE](race-framework.md), [4 Ps](4ps-marketing-mix.md), [TPB](theory-of-planned-behavior.md), [brand pyramid](brand-resonance-pyramid.md), [decoy](decoy-effect.md), [Zeigarnik](zeigarnik-effect.md), [rule of 7](rule-of-7.md), [Eisenhower](eisenhower-matrix.md). For a whole plan see [apply-marketing-plans.md](apply-marketing-plans.md); for traffic sources see [apply-social-media.md](apply-social-media.md).
