# Paid media metrics

**What it is:** The core vocabulary of paid-media and performance marketing: what each metric means, the formula, a small worked calculation, what decision it drives, and how people misread it. Covers 15 concepts plus break-even ROAS, LTV:CAC and incrementality tests (the check on attribution).

All numbers in worked calculations are **fictional**. Currency is generic units. No benchmark ("good CTR", "healthy ratio") is stated as fact: compare against your own history. Where a platform rule is described, it is cited with its doc URL and was checked in October 2026; platforms change settings often, so confirm in your own ad account before acting.

## Contents

1. [How the metrics chain together](#how-the-metrics-chain-together)
2. [Cost metrics](#cost-metrics): CPM, CPC, CPR, CAC
3. [Return metrics](#return-metrics): ROAS, break-even ROAS, LTV, LTV:CAC
4. [Funnel and sales](#funnel-and-sales): full funnel metrics, back-end selling systems, schedule events
5. [Measurement](#measurement): attribution windows, Conversions API, media mix modeling, incrementality and lift tests
6. [Creative and delivery](#creative-and-delivery): creative fatigue, creative diversity, frequency and frequency capping
7. [Evidence and honesty notes](#evidence-and-honesty-notes)
8. [Sources](#sources)

## How the metrics chain together

Delivery metrics (CPM, frequency) feed click metrics (CTR, CPC), which feed funnel rates (lead, book, show, close), which produce customers (CAC), which earn money (ROAS, LTV). A bad number downstream usually has a cause upstream, so read left to right and find the first stage that moved.

```
CPM -> CTR -> CPC -> lead rate -> book rate -> show rate -> close rate -> CAC -> ROAS / LTV:CAC
```

Useful identity: CPC = CPM / (1,000 x CTR). With CPM 4.00 and CTR 0.32%, CPC = 4.00 / 3.2 = 1.25.

---

## Cost metrics

### CPM (cost per thousand impressions)

- **Definition:** What you pay to be shown 1,000 times. An impression is one ad display, so one person can account for many.
- **Formula:** CPM = spend / impressions x 1,000
- **Worked calc:** spend 500, impressions 125,000. CPM = 500 / 125,000 x 1,000 = 4.00.
- **How to read it:** CPM is the price of attention in the auction. It rises with competition, narrow audiences, seasonal demand and low ad relevance. It does not say whether the attention was any good.
- **Decisions it drives:** a sudden CPM jump with stable CTR points to the auction or audience size, not the creative. A low CPM with no results usually means cheap, wrong attention.
- **Common mistakes:** optimising for the lowest CPM (cheap reach to people who never buy); comparing CPM across placements, countries or objectives; treating CPM as quality.

### CPC (cost per click)

- **Definition:** What you pay for each click.
- **Formula:** CPC = spend / clicks
- **Worked calc:** spend 500, clicks 400. CPC = 1.25. CTR = 400 / 125,000 = 0.32%.
- **How to read it:** CPC = CPM divided by how often people click. Lower CPC comes from a cheaper CPM, a higher CTR, or both.
- **Decisions it drives:** high CPC with normal CPM means the creative or offer is not earning clicks; test the hook and the promise. Normal CPC with weak downstream results means the click is the wrong click.
- **Common mistakes:** a cheap click to an expensive page is still a problem: judge cost per lead and per customer, not per click. Check whether your column counts all clicks or only link clicks; they differ, and platforms may have changed what "click" includes (verify in your ad account), so label which one you use.

### CPR (cost per result)

- **Definition:** Meta's headline cost metric: spend divided by "results", where a result is the event the ad set is optimised for (purchase, lead, schedule, landing page view, link click, and so on).
- **Formula:** CPR = spend / results for the chosen objective and optimisation event
- **Worked calc:** spend 500, 20 results. CPR = 25.
- **How to read it:** CPR is only comparable between ad sets that count the same result with the same attribution setting. A CPR of 25 per lead and 25 per link click are not the same thing.
- **Decisions it drives:** use it for ranking ads and ad sets inside one campaign with one objective. Then translate to money with the funnel rates below.
- **Common mistakes:** comparing CPR across objectives; ignoring that changing the attribution setting changes the result count; celebrating a falling CPR after switching the optimisation event to something shallower (clicks are cheaper than customers). The exact wording of Meta's definition of "results" was not confirmed from an official page in this research: verify the definition in the Ads Manager column tooltip.

### CAC (customer acquisition cost)

- **Definition:** All the money spent to win one new customer, not just ad spend.
- **Formula:** CAC = (ad spend + sales cost) / new customers. Sales cost includes salaries or commissions of the people who close, tools, creative production and agency fees where you can attribute them.
- **Worked calc:** ad spend 3,000, sales cost 1,000, new customers 20. CAC = 4,000 / 20 = 200. The ad-only figure (3,000 / 20 = 150) understates it by 25%.
- **How to read it:** CAC answers "what does a customer cost me?" and is the denominator in LTV:CAC and payback calculations.
- **Decisions it drives:** whether the channel can scale, how much you can bid, whether sales capacity or ads are the real cost.
- **Common mistakes:** counting only ad spend; counting repeat customers in the denominator (CAC is for new customers); mixing time periods (spend this month, customers who closed over a longer cycle). For long sales cycles, match spend to the cohort that spend produced.

---

## Return metrics

### ROAS (return on ad spend)

- **Definition:** Revenue the platform credits to the ads, per unit of ad spend.
- **Formula:** ROAS = revenue from ads / ad spend
- **Worked calc:** spend 3,000, attributed revenue 9,000. ROAS = 3.0.
- **How to read it:** ROAS is a revenue ratio. It ignores cost of goods, delivery, payment fees, refunds, and whether the sale would have happened anyway. A ROAS of 1.0 is **not** break-even.
- **Decisions it drives:** comparing ads and campaigns that sell the same kind of product. Scaling or cutting only makes sense against break-even ROAS (next section).
- **Common mistakes:** treating the platform's ROAS as profit; comparing ROAS across products with different margins; comparing ROAS from different attribution windows; ignoring refunds and cancellations.

### Break-even ROAS

- **Definition:** The ROAS at which ads pay for themselves on contribution margin.
- **Formula:** break-even ROAS = 1 / contribution margin, where contribution margin = (revenue minus COGS, delivery, fees, expected refunds) / revenue.
- **Worked calc:** contribution margin 40%. Break-even ROAS = 1 / 0.40 = 2.5. At ROAS 3.0 on spend 3,000: revenue 9,000 x 0.40 = 3,600 contribution, minus 3,000 spend = +600. At ROAS 2.0: 6,000 x 0.40 = 2,400, minus 3,000 = -600.
- **How to read it:** below it you lose money on the first order; above it you profit. If customers repeat, you may knowingly run below first-order break-even and use LTV instead (see below), but that is a cash-flow decision with a stated payback period, not a default.
- **Common mistakes:** using gross margin when delivery or fees are material; forgetting that platform-attributed revenue may be over- or under-counted (see attribution and incrementality).

### LTV (customer lifetime value)

- **Definition:** The total value a customer brings over their relationship with you. Use **contribution margin**, not revenue, when comparing with CAC.
- **Formula (simple, repeat purchase):** LTV = average order value x purchases per customer over the period x contribution margin. For subscriptions, one common form is monthly contribution per customer / monthly churn rate.
- **Worked calc:** average booking 80, contribution margin 45% (36 per booking), average 5 bookings in 12 months. 12-month LTV = 5 x 36 = 180. Revenue LTV would be 400, which overstates what you can spend.
- **How to read it:** prefer observed cohorts (customers who started in the same month, followed for a fixed period) over projections from a few early buyers. State the time horizon ("12-month LTV").
- **Common mistakes:** revenue-based LTV; projecting a lifetime from three weeks of data; averaging heavy and light customers into a number nobody matches; ignoring that LTV for a promotional cohort differs from organic customers.

### LTV:CAC

- **Definition:** LTV divided by CAC, the return on acquisition spend over the customer lifetime.
- **Formula:** LTV:CAC = LTV / CAC. Pair it with **payback period** = CAC / monthly contribution per customer, which says how long the cash is tied up.
- **Worked calc:** LTV 180, CAC 60. LTV:CAC = 3.0. If a customer contributes 15 per month, payback = 60 / 15 = 4 months.
- **How to read it:** a ratio of 3:1 is often quoted as a rule of thumb, especially in software circles. It is a convention, not a law: the right ratio depends on margins, payback tolerance, cash available and how reliable the LTV estimate is. A business with thin cash may need a short payback more than a high ratio.
- **Decisions it drives:** how much you can pay per customer, which channels to scale, whether to fund acquisition from the first order or from repeat orders.
- **Common mistakes:** a high ratio from an optimistic LTV; ignoring payback; using blended CAC when paid CAC is what you control (and the reverse: judging paid on a blended figure that includes organic customers).

---

## Funnel and sales

### Full funnel metrics

- **Definition:** The chain of stage rates from click to customer. Each stage is a multiplier.
- **Formula:** clicks x apply rate x book rate x show rate x close rate = customers
- **Worked calc:** 1,000 clicks x 10% apply = 100 applications. x 40% book = 40 booked calls. x 70% show = 28 calls held. x 25% close = 7 customers. With 3,500 ad spend, ad-only cost per customer = 500 (CAC would add sales cost on top).
- **How to read it:** because stages multiply, a 10% relative improvement at any stage gives 10% more customers. "Fix the worst stage first" is therefore a heuristic, not arithmetic: in practice pick the stage with the most headroom against **your own** past performance and the cheapest fix. Raising show rate from 70% to 77% (+10% relative) is often cheaper than raising CTR by the same relative amount.
- **Decisions it drives:** where to spend effort. Weak apply rate means page or offer; weak book rate means scheduling friction or lead quality; weak show rate means reminders and pre-selling; weak close rate means sales process or fit.
- **Common mistakes:** looking only at the top (CTR, CPC); defining stages differently each week; measuring each stage on different date ranges, so late-closing sales are missed; assuming rates stay the same when you scale spend (cold audiences are usually worse).

### Back-end selling systems

- **Definition:** Everything between the application or lead and the sales call that gets the person pre-sold: confirmation page, email and text sequences, reminders, proof (case studies, short videos), qualification questions.
- **Formulas:** show rate = calls held / calls booked. Close rate = closes / calls held.
- **Worked calc:** 40 booked, 28 held, 7 closed. Show rate = 28 / 40 = 70%. Close rate = 7 / 28 = 25%. (Closes over booked would be 17.5%, a different and blended number: say which one you use.)
- **How to read it:** the back end is where paid media wins or loses after the click. Better pre-selling lifts show rate and close rate without buying one more click, so it lowers CAC at no media cost.
- **Decisions it drives:** build or fix the confirmation page, reminder sequence and proof before raising spend; route low-intent leads to a lighter path.
- **Common mistakes:** sending booked people to a blank thank-you page; no reminders; no proof; judging a campaign's quality while ignoring that the sales team never called the leads in time.

### Schedule events

- **Definition:** Sending booked-appointment events back to the ad platform so it optimises for real appointments, not form fills. On Meta the standard event is named `Schedule`, described in the Meta Pixel reference as "when a person books an appointment to visit one of your locations". Its promoted-object value is `SCHEDULE`.
- **Formula:** cost per scheduled call = spend / Schedule events. Optimise for the deepest event that still has enough volume to learn from.
- **Worked calc:** 100 leads at CPR 15 (spend 1,500). Only 40 book. Cost per lead 15, cost per booked call 37.50. An ad set optimised for leads may find cheap leads who never book; the same budget optimised for Schedule is trained on the people who do.
- **How to read it:** the event hierarchy runs click, lead, schedule, show, close. Each deeper event is more valuable and rarer. Meta's description speaks of visiting a location, so using it for a booked phone or video call is a common convention rather than a documented definition; the alternative is a custom event. Pick one and use it consistently. Send it from the browser pixel and, ideally, from the server (see the Conversions API) with a shared `event_id`.
- **Decisions it drives:** switching the optimisation event from Lead to Schedule once there are enough Schedule events per week for the platform to optimise on. Meta publishes a minimum-volume guideline: verify the current figure in your ad account rather than relying on a remembered number.
- **Common mistakes:** firing Schedule on the button click rather than on a confirmed booking; double-counting Schedule from pixel and server without deduplication; switching to a deep event with too little volume, which stalls delivery.
- **Other platforms:** TikTok and Google have their own conversion-event and offline-import mechanisms; confirm the equivalent event in each ad account.

---

## Measurement

### Attribution windows

- **Definition:** The number of days after a click, and after a view or engagement, in which a conversion is credited to the ad.
- **Formula:** none. It is a setting. Reported conversions = conversions inside the window on the stated attribution model.
- **Worked calc:** same ad, same week, spend 500. Under 7-day click, 40 purchases are reported (CPR 12.50). Under 1-day click, 28 are reported (CPR 17.86). Nothing about sales changed; only the credit rule did.
- **How to read it:** longer windows credit more conversions, and with a view window they also credit people who may never have noticed the ad. Short windows undercount products with a long consideration time.
- **Decisions it drives:** choose the window to match the real buying cycle (an impulse buy and a sofa differ), then keep it fixed. Never compare reports using different windows, and mark the window on every report.
- **Platform facts (checked October 2026, confirm in your account):**
  - **Meta:** the Ads Insights API stopped returning the 7-day view and 28-day view windows on 12 January 2026. Still returned: 1-day click, 7-day click, 28-day click, 1-day engaged view and 1-day view (Meta for Developers blog, 16 October 2025; the 1-day engaged view / engage-through setting at ad-set level is described only by secondary sources, so verify it in your account). Ad-set attribution settings as described by a secondary source (Jon Loomer, 2026): 7-day click-through (or 1-day), 1-day engage-through (or none), 1-day view-through (or none); defaults 7-day click, 1-day engage, 1-day view; the 28-day window is viewable through "Compare Attribution Settings" but not an optimisation setting. That article also says non-link clicks moved from "click-through" to the new "engage-through" type. Meta's own help page for these settings could not be retrieved, so verify the defaults in your ad set's attribution setting.
  - **Google Ads:** defaults for a new conversion action are 30 days click-through, 3 days engaged-view and 1 day view-through, each customisable (click-through up to 30, 60 or 90 days depending on campaign type, engaged-view 1 to 30 days, view-through 1 to 30 days). Source: Google Ads Help, "About conversion windows".
  - **TikTok:** attribution window defaults were not confirmed from an official TikTok page. Check the attribution setting in TikTok Ads Manager.
- **Common mistakes:** comparing a Meta report with a Google report as if windows matched; switching windows mid-test; reading the January 2026 drop in reported view-through conversions as a performance drop when it is a reporting change; trusting any platform's attribution as proof of cause (see incrementality).

### Conversions API (CAPI) and match rate

- **Definition:** Sending conversion events from your server (or a CRM or tag server) to the ad platform, instead of or alongside the browser pixel. Browser tracking loses events to blockers, browser privacy limits and consent choices; server events are not subject to those browser limits, though they still need user consent where law requires it.
- **Formulas:** match rate = matched events / events sent (a simple working definition; Meta's own measure is Event Match Quality, a score out of 10). Deduplication key = `event_id` + `event_name`.
- **Worked calc:** 200 purchase events sent from the server, 150 matched to a Meta account. Match rate = 75%. If the pixel also sent 190 of the same purchases with the same `event_id`, Meta should count about 200 purchases, not 390. If dedup is broken you will see roughly double.
- **How to read it:**
  - **Deduplication (Meta):** when you send the same event through pixel and server, the pixel's event ID must equal the server's `event_id`, and the pixel's event name must equal the server's `event_name`. Duplicates are discarded only if received within 48 hours of the first event with that ID, and the first received is generally kept. A fallback uses `event_name` plus `fbp` and/or `external_id`, and does not deduplicate events from a single source. In the pixel the parameter is `eventID` (the fourth argument of `fbq('track', ...)`); on the server it is `event_id`. Use a stable value such as an order or booking ID.
  - **Event Match Quality (EMQ):** each server event gets a score out of 10 in Events Manager indicating how effective its customer information (email, phone, IP address, name and similar fields) may be for matching to a Meta account. Meta states that unmatched events cannot be used for attribution or ad delivery optimisation, and that sending more customer information parameters may improve EMQ. EMQ is currently for web events. Meta does not publish a numeric target; treat third-party "good score" bands as opinion.
  - **TikTok:** the Events API deduplicates with the same `event_id` and event name from pixel and server, within 48 hours; without `event_id` it may fall back to the `_ttp` cookie.
  - **Google:** offers enhanced conversions and offline conversion import for the same purpose. Not verified in this research: check Google Ads Help for the current requirements.
- **Decisions it drives:** whether the platform is optimising on real, complete data. Weak match rate means send more identifiers (with consent) and check parameter hashing and formatting.
- **Common mistakes:** sending server events without `event_id`, so every sale counts twice; mismatched event names between pixel and server (`Purchase` vs `purchase`); sending events more than a few days late; assuming CAPI fixes attribution (it improves signal, not causality); not testing with a real conversion in Events Manager.

### Media mix modeling (MMM)

- **Definition:** A statistical model of total business outcomes (usually revenue or sales) over time against spend by channel and other drivers, without relying on user-level tracking.
- **Formula (conceptual):** revenue = baseline + sum over channels of (spend in channel x its effect). Real models add adstock (carry-over of ad effect over time) and saturation (diminishing returns), plus seasonality, promotions and price.
- **Worked calc (toy):** weekly revenue 20,000 = baseline 12,000 (would happen anyway) + search 4,000 + social 3,000 + email 1,000. If social spend is 1,500, its modeled return is 3,000 / 1,500 = 2.0, regardless of what the platform's own ROAS says.
- **How to read it:** MMM gives an incremental estimate per channel and suggests where extra budget would still pay. It is slow (weekly or daily data over a long history), uncertain (report ranges, not single numbers) and cannot judge creative.
- **Decisions it drives:** use it when platform-attributed numbers and the bank account disagree, when privacy limits user-level tracking, or when budgets are large enough to justify the effort. Calibrate it with lift experiments where you can.
- **Open-source tools (checked October 2026):**
  - **Meridian (Google):** Bayesian MMM framework, Apache-2.0 licence, Python 3.11 to 3.13, `pip install google-meridian`. Active repository with 2026 versioning in its citation. Source: github.com/google/meridian.
  - **Robyn (Meta Marketing Science):** MIT licence, R package using ridge regression and evolutionary hyperparameter optimisation; a Python API is in beta and wraps the R package. The repository describes it as experimental and semi-automated, with no archive or deprecation notice. Source: github.com/facebookexperimental/Robyn.
  - Release dates and the exact minimum data history were not stated on the repository pages: read each tool's docs before promising a client a timeline.
- **Common mistakes:** feeding too little or too flat spend history (the model cannot separate channels that always moved together); treating output as exact; running MMM when one channel is 95% of spend (a lift test is simpler); ignoring organic drivers such as promotions and seasonality.

### Incrementality and lift tests

- **Definition:** An experiment that compares people (or regions) who could see the ads with a randomised holdout who could not, to measure conversions the ads actually caused. This is the check on attribution, which only counts conversions that happened after an ad touch.
- **Formulas:** lift = (test conversion rate minus control conversion rate) / control conversion rate. Incremental conversions = test conversions minus control conversions scaled to the same audience size. iROAS = incremental revenue / spend.
- **Worked calc:** test group 50,000 people, 600 conversions (1.2%). Holdout scaled to 50,000 people, 500 conversions (1.0%). Lift = 20%. Incremental conversions = 100. With revenue 80 each and spend 2,000: iROAS = 100 x 80 / 2,000 = 4.0. The platform, crediting all 600, would report 600 x 80 / 2,000 = 24.0. Retargeting often shows this gap, because many of those buyers were already coming back.
- **How to read it:** a platform-run test (Meta Conversion Lift, Google conversion lift) is convenient but the seller of the media designs the test and holds the control group; geo holdouts (pause ads in matched regions) measure across channels. Experiments sit above attribution and models in strength of causal evidence. Test availability, minimum budgets and duration were not confirmed from official pages: check your ad account.
- **Decisions it drives:** whether to keep spending on retargeting or brand search, and how to calibrate MMM.
- **Common mistakes:** stopping a test early; leaking the holdout (they still saw the ads via another route); too few conversions to detect a difference; testing during an unusual promotion; reading a "no significant lift" as proof of zero effect when the test was underpowered.

---

## Creative and delivery

### Creative fatigue

- **Definition:** An ad stops working because the same people have seen it too many times. Diagnose it only when **three signs appear together on the same ad**: cost per result rising, result volume falling, and frequency rising.
- **Formula:** none. Compare the same ad's CPR, results and frequency across equal periods.
- **Worked calc:** week 1: frequency 1.4, 50 results, CPR 20. Week 3: frequency 2.6, 32 results, CPR 31. All three moved the wrong way, so fatigue is likely. If CPR rose but frequency stayed flat, suspect the auction, the audience or tracking instead.
- **How to read it:** fatigue is usually an audience and frequency problem; the fix is fresh concepts or a bigger audience, not a new colour on the same ad.
- **Decisions it drives:** rotate in a new concept, expand the audience, exclude recent converters, or cap frequency on retargeting.
- **Common mistakes:** calling any bad week fatigue; judging from CTR alone; pausing an ad that is still the best in a weak set; ignoring seasonality or a changed attribution setting.

### Creative diversity

- **Definition:** How many genuinely different ideas you are testing.
- **Formula:** creative diversity = distinct concepts / active ads. A concept is a different angle, hook, audience problem or proof, not a different crop, caption or colour.
- **Worked calc:** 12 active ads built from 3 concepts. Diversity = 3 / 12 = 0.25. Three edits of one idea count as one concept.
- **How to read it:** low diversity means you are really running few experiments and will fatigue faster. Platforms tend to deliver to the most promising ads, so near-duplicates compete with each other and add little learning.
- **Decisions it drives:** plan a concept backlog (problem, outcome, proof, objection, offer) and ship a fixed number of new concepts per week or month. Tag each ad with its concept so you can read results by concept, not by ad.
- **Common mistakes:** counting variants as concepts; testing ten concepts at once with too little budget each; killing a concept after one weak ad when the execution was the issue.

### Frequency and frequency capping

- **Definition:** Frequency is the average number of times each reached person saw the ad. Capping limits how often one person sees it.
- **Formula:** frequency = impressions / reach
- **Worked calc:** 90,000 impressions, 36,000 people reached. Frequency = 2.5. That is an average: some people saw it once, others ten times.
- **How to read it:** rising frequency with falling results points toward fatigue; low frequency on a warm retargeting audience can mean you are leaving money on the table. There is no universal right number. The rule of 7 is folklore (see [rule-of-7.md](rule-of-7.md)); set caps from your own conversion data and test them.
- **Platform facts (checked October 2026, confirm in your account):**
  - **Meta:** the Reservation buying type (formerly Reach and Frequency) lets you plan with a fixed cost and a frequency cap; it is aimed at awareness and engagement goals optimised for reach, has a default minimum reach of 200,000 accounts, and is available to certain accounts. Source: Meta for Developers, "Reservation". A secondary source (Jon Loomer, https://www.jonloomer.com/reservation-buying-type-replaces-reach-and-frequency/) says a target frequency option exists alongside the frequency cap; not confirmed in Meta's docs. For ordinary auction campaigns, I could not verify a hard cap setting: check your ad set options and watch the frequency column instead.
  - **Google Ads:** frequency capping works in Display and Video campaigns, not in Demand Gen campaigns. Display caps can be set at campaign, ad group or ad level; Video caps at campaign level. Source: Google Ads Help, "About frequency capping".
  - **TikTok:** not verified in this research; check the delivery settings in TikTok Ads Manager.
- **Decisions it drives:** cap retargeting so buyers are not chased; widen the audience or add concepts when frequency climbs on prospecting.
- **Common mistakes:** one cap for all audiences (cold, warm and customers differ); reading average frequency as if everyone got that number; capping so hard that the audience is starved and cost per result rises; no exclusion of recent buyers.

---

## Evidence and honesty notes

- Metric definitions (CPM, CPC, CAC, LTV, frequency) are accounting identities, not empirical claims. Their evidence problem is data quality, not theory.
- Platform-reported ROAS and conversions are model-based and window-dependent. Treat them as directional and verify with a lift test, MMM or your own sales records.
- LTV:CAC of 3:1 is a widely repeated rule of thumb with no single authoritative source. Use it as a conversation starter.
- Meta's 2026 attribution-setting details come partly from a secondary source and are flagged as such above. Platform interfaces change; confirm in the account.
- Not verified and therefore left as "check in your ad account": Meta's official wording of "results", Meta's minimum-volume guideline for optimisation events, TikTok attribution defaults and frequency controls, Google and Meta lift-test minimums, Google enhanced-conversion requirements.

## Sources

- Meta for Developers, Conversions API, deduplication: https://developers.facebook.com/documentation/ads-commerce/conversions-api/deduplicate-pixel-and-server-events
- Meta for Developers, Conversions API best practices (Event Match Quality): https://developers.facebook.com/docs/marketing-api/conversions-api/best-practices
- Meta for Developers, Conversions API overview: https://developers.facebook.com/docs/marketing-api/conversions-api
- Meta Pixel reference (standard event `Schedule`): https://developers.facebook.com/docs/meta-pixel/reference
- Meta for Developers blog, Ads Insights API metric availability updates (7-day and 28-day view windows removed 12 January 2026): https://developers.facebook.com/blog/post/2025/10/16/ads-insights-api-metric-availability-updates/
- Meta for Developers, Reservation buying type and frequency cap: https://developers.facebook.com/documentation/ads-commerce/marketing-api/reservation
- Jon Loomer, How Meta Ads Attribution Works in 2026 (secondary): https://www.jonloomer.com/meta-ads-attribution-2026/
- Google Ads Help, About conversion windows: https://support.google.com/google-ads/answer/3123169
- Google Ads Help, About frequency capping: https://support.google.com/google-ads/answer/6034106
- TikTok Ads Help, About event deduplication: https://ads.tiktok.com/help/article/event-deduplication
- Google Meridian: https://github.com/google/meridian
- Meta Robyn: https://github.com/facebookexperimental/Robyn

Related: [rule of 7](rule-of-7.md), [RACE](race-framework.md), [apply-paid-ads.md](apply-paid-ads.md).
