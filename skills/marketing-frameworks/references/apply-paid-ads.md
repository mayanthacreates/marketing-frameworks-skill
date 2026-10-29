# Playbook: paid ads

**When to use this file:** planning, launching, reviewing or troubleshooting paid campaigns on Meta, Google, TikTok or similar: campaign structure, budget, tracking setup, creative testing, weekly optimisation, or explaining why ad numbers and real sales disagree. Metric definitions, formulas and platform facts live in [paid-media-metrics.md](paid-media-metrics.md); open it for any metric used below.

Why this order: ads multiply whatever is already there. A weak offer, a leaky page or broken tracking gets more expensive at scale, so confirm the economics (what can you afford to pay per customer) and the measurement (do events reach the platform) before spending, then optimise from the leakiest funnel stage. Apply a step only if the account or goal calls for it.

## Workflow

1. **Set the economics before the campaign.** Work out contribution margin, break-even ROAS (1 / margin), the CAC you can afford, and LTV if customers repeat. Ads that look fine at ROAS 3.0 can lose money at a 30% margin. Mark any missing number "to measure" and never borrow an "industry average" ([metrics](paid-media-metrics.md), Return).
2. **Name the one behavior and the audience (STP, TPB).** Pick one segment by need, write the positioning sentence, and name the exact action the ad must cause (book a quote, buy, start a trial). If leads exist but do not book, diagnose which TPB factor blocks it: attitude (is it worth it?), norms (do people like me trust this?) or control (is booking easy?). Use 5-10 short chats, call notes or form comments; with no data, state the assumption ([STP](stp-model.md), [TPB](theory-of-planned-behavior.md)).
3. **Map KPIs to RACE stages.** Reach: CPM, reach, frequency. Act: CTR, CPC, landing page rate. Convert: lead, book, show, close rates and CAC. Engage: repeat rate and LTV. One KPI per stage, each against the account's own baseline ([RACE](race-framework.md)).
4. **Fix tracking first.** Install the pixel and the server-side Conversions API with a shared `event_id` per event. Send the deepest useful event (for booked appointments, Meta's `Schedule`), confirm each event with a test conversion in Events Manager, check deduplication and match quality, and fix the attribution window per report. No tracking means a 2-week baseline and qualitative review only ([metrics](paid-media-metrics.md), Measurement).
5. **Build the offer and landing page.** The page's message must match the ad (STP). If showing tiers, test a decoy as an A/B hypothesis, with honest options ([decoy](decoy-effect.md), [apply-websites.md](apply-websites.md)). Add reminders, confirmation page and proof for the back end so booked people show up and close ([metrics](paid-media-metrics.md), Funnel and sales).
6. **Structure the campaign.** Separate prospecting (cold) from retargeting (warm) and from existing customers: they have different frequency, creative and cost expectations. Optimise for the deepest event that has enough volume; start shallower and move down as volume allows. Keep one attribution setting across ad sets you will compare.
7. **Plan the creative.** Brief concepts, not variants: problem, outcome, proof, objection, offer. Tag every ad with its concept and aim for several distinct concepts at once (creative diversity). Rotate fresh concepts before fatigue shows ([metrics](paid-media-metrics.md), Creative and delivery).
8. **Plan frequency and retargeting.** Cap or watch frequency by audience. Retarget people who started but did not finish (a quote form, a booking) with a short, useful "finish this" message; the pull is the urge to finish, so cap it and stop when they complete ([Zeigarnik](zeigarnik-effect.md)). Judge frequency from your own conversion data; seven is not a magic number ([rule of 7](rule-of-7.md)).
9. **Review weekly, decide monthly.** Use the weekly sheet below. Read the funnel left to right, find the first stage that moved, and change one thing at a time. Do not edit budgets and creative on the same day for the same ad set, or you cannot tell what worked.
10. **Check what attribution cannot tell you.** When platform results and sales disagree, compare windows first, then run a holdout or lift test on the biggest retargeting or brand spend. Consider media mix modeling only with enough channels, spend variation and history ([metrics](paid-media-metrics.md), incrementality and MMM).
11. **Prioritise the optimisation backlog (Eisenhower).** Do: broken tracking, a failing landing page, an ad spending on a rejected link. Schedule: new concepts, lift test, back-end sequence. Delegate: asset resizing, report pulls. Drop: tweaking colours on ads that already fit ([Eisenhower](eisenhower-matrix.md)).
12. **Set kill and scale rules in advance.** For example, pause an ad set when CAC is worse than the affordable CAC for two review cycles; scale in small steps only when CAC holds. Write the rule before launch so it is not argued under pressure.

Fits weakly: **brand pyramid** helps choose the proof and creative angle for an unknown or untrusted brand but is not an ad metric ([brand pyramid](brand-resonance-pyramid.md)). **Pygmalion** only matters if you brief an agency, freelancers or sales reps: give specific, believable standards plus support (small, contested effect). **4 Ps**: check once that Price and Place fit the position, not per ad ([4 Ps](4ps-marketing-mix.md)).

## Framework or metric to tactics to measures

| Framework or metric | Tactics in paid ads | Measure |
|---|---|---|
| Break-even ROAS, CAC, LTV | Set the affordable CAC and the review thresholds before launch | ROAS vs break-even, CAC, LTV:CAC and payback period |
| STP | One segment per ad set, message-matched landing page | CPR and CAC by segment; page conversion by source |
| RACE | One KPI per stage; spend weighted to the leakiest stage | Reach (CPM, frequency), Act (CTR, CPC), Convert (stage rates), Engage (repeat) |
| TPB | Proof for attitude, reviews and named customers for norms, easy booking and reminders for control | Book rate, show rate, cost per booked call |
| Rule of 7 | Frequency watched or capped by audience; fresh creative | Frequency, CTR and CPR trend per ad |
| Zeigarnik | "Finish your booking" retargeting, capped | Retarget conversions, completion rate |
| Decoy | Tier test on offer or landing page | Target-option share, revenue per visitor |
| Eisenhower | Ranked optimisation backlog | Share of Do and Schedule items shipped |
| CAPI and Schedule event | Deepest event sent server-side with `event_id` | Match rate, EMQ, deduplicated counts, Schedule volume |
| Attribution window | One fixed window per report | Same-window comparisons only |
| Lift test or MMM | Holdout on retargeting; MMM when sources disagree | Lift, iROAS, modeled channel return |
| Creative fatigue and diversity | New concept rotation; tag ads by concept | Distinct concepts / active ads; CPR, volume and frequency per ad |

## Output template: campaign plan and weekly ad review

```
# Campaign plan: [business], [period]
Goal and behavior: [one action, one number, one date]
Economics: AOV [..]  Contribution margin [..]  Break-even ROAS [..]  Affordable CAC [..]  LTV (horizon) [..]
Audience and position (STP): [..]
Offer and landing page: [..]  Decoy test: [yes/no, how]
TPB diagnosis: [blocking factor, evidence or assumption]
Tracking: pixel [ ]  server events [ ]  event_id shared [ ]  Schedule or deep event [ ]  test conversion confirmed [ ]  attribution window [..]
Structure: prospecting [budget, audience, event]  retargeting [budget, window, frequency cap]  customers [..]
Creative concepts: [concept | angle | proof | ad count]   Diversity target: [..]
Budget and test reserve: [..]
Kill and scale rules: [..]
```

```
# Weekly ad review: [account], week of [date], window [..]
| Stage | Metric | Last week | This week | Change | Note |
|-------|--------|-----------|-----------|--------|------|
| Reach | CPM, frequency | | | | |
| Act | CTR, CPC | | | | |
| Convert | Lead, book, show, close rates | | | | |
| Money | CAC, ROAS vs break-even, LTV:CAC | | | | |
| Tracking | Match rate, dedup check, event volume | | | | |
| Creative | Concepts live, fatigue signs (CPR up, results down, frequency up) | | | | |
First stage that moved: [..]   Hypothesis: [..]   One change: [..]   Next review: [..]
Backlog (Eisenhower): Do [..]  Schedule [..]  Delegate [..]  Drop [..]
```

## Worked example: home-cleaning service, 4-week lead campaign

Business: "Spotless", a home-cleaning service with 4 cleaners. Goal: more booked quote calls from households that have never used a cleaning service. All numbers are **fictional**.

```
# Campaign plan: Spotless, 4 weeks
Goal and behavior: book a quote call; 40 booked calls per week by week 4
Economics: first clean 120, contribution margin 40% (48 per clean),
  break-even ROAS on a first clean = 1 / 0.40 = 2.5.
  Repeat: average 6 cleans in 12 months, 12-month LTV = 6 x 48 = 288.
  Affordable CAC if we want LTV:CAC of at least 3 (a common rule of thumb, not a law) = 96.
Audience and position: "For busy households, Spotless is the cleaning service that
  gives you a fixed price and the same cleaner every visit, unlike marketplaces where
  the person changes each time."
Offer and landing page: free 10-minute quote call. Page repeats the ad's promise.
  Decoy test (see table below).
TPB diagnosis (assumption, no calls reviewed yet): attitude fine; norms weak
  (letting a stranger into the home), control weak (finding a time to call).
Tracking: pixel, server events, shared event_id, Schedule on confirmed booking only,
  test booking confirmed, window 7-day click for all reports.
Structure: prospecting 70% (broad local audience, optimise for Schedule once enough volume,
  Lead until then); retargeting 25% (form starters and page visitors, capped);
  customers 5% (referral offer).
Creative concepts: 1 "same cleaner every visit" (proof: cleaner profiles)
  2 "fixed price, no surprises" (proof: price card) 3 "vetted and insured" (proof: checks)
  4 "weekend back" (outcome). 3 ads per concept, 12 ads total, diversity = 4 / 12 = 0.33.
Budget and test reserve: 1,400 per week, 10% reserve for new concepts.
Kill and scale rules: pause an ad when CAC is worse than affordable CAC for two review
  cycles; raise budget in small steps only if CAC holds for two cycles.
```

Funnel in week 2, from the weekly sheet (the first full week with tracking confirmed):

| Stage | Number | Working |
|---|---|---|
| Spend | 1,400 | |
| Impressions | 70,000 | CPM = 1,400 / 70,000 x 1,000 = 20.00 |
| Clicks | 1,000 | CPC = 1.40, CTR = 1.43% |
| Leads | 80 | 8% of clicks |
| Booked calls | 40 | 50% of leads, cost per booked call = 35.00 |
| Calls held | 30 | show rate 75% |
| New customers | 12 | close rate 40% |
| CAC | 150 | (1,400 + 400 sales cost) / 12 |
| First-clean ROAS | 1.03 | 12 x 120 = 1,440 / 1,400; break-even is 2.5 |
| LTV:CAC | 1.92 | 288 / 150 |

Reading it:
- ROAS looks like "break-even" at about 1.0 but is far below the true break-even of 2.5. On the first clean alone the campaign loses money; only repeat cleans can repay it.
- CAC 150 is above the affordable 96, so the campaign is not yet fundable on the 3:1 rule of thumb. Payback depends on repeat behavior, so check the repeat rate for these customers before scaling.
- Stage multiplication: 1,000 x 8% x 50% x 75% x 40% = 12. The weakest stage by headroom is book rate (50%). TPB suggests control and norms, so the experiment is a reminder text, a booking link in the confirmation, and the cleaner profiles as proof on the confirmation page (back end). A 10% relative lift in book rate gives about 1.2 more customers for the same spend.
- Retargeting: form starters get a capped "finish your quote" ad for 7 days (urge to finish). Frequency capped at a level chosen from the account's own data, and reviewed after two weeks.
- Fatigue watch: concept 2 shows (illustrative) frequency 1.4 to 2.6 across recent reviews, CPR 20 to 31, results 50 to 32, all moving together on one ad. Rotate in a new price-card concept; do not just change its colour.
- Offer test (near-decoy, honest options):

| Option | Price | Included |
|---|---|---|
| Standard | 120 | 2 hours, whole home |
| Standard Plus (decoy) | 175 | 2 hours, whole home, oven |
| Deep clean (target) | 180 | 4 hours, whole home, oven, fridge, windows |

  Standard Plus costs almost the same as Deep clean and offers much less, so Deep should look like the obvious upgrade. With real services the effect is unreliable, so run it as an A/B test and keep it only if revenue per visitor rises ([decoy](decoy-effect.md)).
- Measurement check: platform ROAS for the retargeting ad set looks excellent, but many of those people were already finishing a quote. Plan a 2-week holdout (no retargeting for a randomised share) to measure the incremental part before moving budget there.
- Eisenhower backlog: Do: confirm the Schedule event fires only after a booking. Schedule: new concepts, holdout test, confirmation page. Delegate: ad resizing. Drop: more colour variants.

## Common mistakes

- Treating ROAS 1.0 as break-even, or the platform's ROAS as profit.
- Judging campaigns on CPC or CPM while the funnel leaks later.
- Optimising for leads when only booked or closed customers matter, with no Schedule or deeper event.
- No `event_id`, so pixel and server events double count, or no test conversion before launch.
- Comparing reports with different attribution windows, or reading a reporting-window change as a performance change.
- Calling it fatigue without seeing cost up, volume down and frequency up on the same ad.
- Counting three edits of one idea as three concepts.
- One frequency cap for cold, warm and customer audiences.
- Changing budget, audience and creative at once, so nothing can be learned.
- Treating LTV:CAC of 3:1 or the rule of 7 as laws, or inventing a "good CTR" instead of using the account's own history.
- Scaling spend on retargeting that attribution flatters, without a holdout.

## Go deeper

[paid media metrics](paid-media-metrics.md), [STP](stp-model.md), [RACE](race-framework.md), [TPB](theory-of-planned-behavior.md), [rule of 7](rule-of-7.md), [decoy](decoy-effect.md), [Zeigarnik](zeigarnik-effect.md), [Eisenhower](eisenhower-matrix.md), [brand pyramid](brand-resonance-pyramid.md), [4 Ps](4ps-marketing-mix.md), [Pygmalion](pygmalion-effect.md). For the landing page see [apply-websites.md](apply-websites.md); for organic and ad creative on social see [apply-social-media.md](apply-social-media.md); for budget and KPIs in the whole plan see [apply-marketing-plans.md](apply-marketing-plans.md).
