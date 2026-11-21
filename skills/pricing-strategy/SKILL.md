---
name: pricing-strategy
description: Use when the user asks what to charge for a Hostemi listing, whether to change prices, why nights have not sold or how to maximize occupancy, income or profits. Also trigger when they ask for dynamic pricing or to optimize pricing on Hostemi.
---

# Pricing

If the user triggered this, it's because they want to make more money with their short term vacation rentals on Airbnb, Booking.com, Vrbo, Expedia, etc. Hostemi is the platform where they can connect all their listings on all platforms and manage them from one place, and with their AI agent.

Recommend prices that maximize expected profit unless the user sets another goal. The profit maximizing price might mean lower occupancy: e.g. selling 8 nights at 150 brings in 1,200 before costs, while selling 10 at 100 brings in 1,000. Skip fixed occupancy targets. Nights that sell out far ahead were probably priced too low. Do not ask for costs unless the user raises them. If costs are unavailable, compare revenue.

What you do here

- Browse the web, get context from other sources and tools.
- Read data from Hostemi (listings, platform, dates, prices, occupancy, signals, amenities etc).
- Update the prices for dates by listing and by platform (if separate prices applied to different platforms) after approval.


## Guardrails

- Never propose a price below the user's lowest price. Use the user's answers to pricing questions only in this conversation.
- Use the town and dates from Hostemi in public searches. Keep private listing and guest details out of search queries.
- If a Hostemi tool returns `PLAN_REQUIRED`, relay its `message` without naming plans or suggesting a purchase. Stop the blocked work.

## Steps

1. **Read the user's numbers.** Start with `get_context` for today's date and each listing's name, ID, connected platforms, currency and town if available. Clarify the listing or dates if ambiguous. Use `get_listing` for capacity, size and amenities, `get_calendar` for sellable nights and nightly prices, and `get_pricing_rules` for the lowest price, stay rules and advance notice. Use `get_pricing_signals` for the user's own booking pace, lead times and comparison with the same weekdays 52 weeks earlier. It contains no market figures. Exclude figures marked `unclear` because they rest on fewer than three bookings.
2. **Check what could move demand.** Look up local, national and international events that could bring visitors to the town, including concerts, sports, festivals and fairs, and natural phenomena (a solar eclipse, for example). Check school and public holidays, weather and nearby attractions' opening dates. Verify the year, dates and location, then connect each factor to the listing's capacity, amenities or location. If you cannot browse, say so and use the user's numbers and any event dates the user provides. You can look up nearby listings and their prices too on the web if the user asks for it.
3. **Ask for missing facts that change the proposal.** Ask only if you cannot find a fact that would change the proposal, browsing or tool access blocks progress, or the user's goal is ambiguous in a way that would change the result. Put your questions in one message with your recommendation first and decide everything else yourself. Ask for the lowest acceptable price only if none is set and you would otherwise recommend a cut. For last-minute bookings, ask how much notice the user needs to prepare the listing if the read tools do not settle it. Rule out offers that leave too little time between booking or the previous checkout and the next arrival.
4. **Recommend prices for sellable nights.** Raise prices when evidence points to higher demand for those nights. Lower them only if the extra bookings are likely to cover the lower price and added costs. Compare each change with keeping the current price. Group nights with the same change.
5. **Preview the user's choices.** Use `change_prices` for nightly prices, `change_stay_rules` for minimum stays or `save_pricing_rules` for base prices and seasons. A price move of more than 25% always waits for the user.
   - For `needs_approval`, send the user to Hostemi's card in Claude or ChatGPT. If they cannot approve on the card, give `change.approvalUrl` to decide in Hostemi. Do not call `apply_change`. If the user says they decided, check once with `get_activity` and the same `changeId`.
   - For `preview`, show the `summary` and call `apply_change` with `change.id` as `changeId` only after the user agrees and the result offers that call in `next`.
   - Report a price as live only when the result says `applied`. Stop on `declined` or `expired`.

## Report

For each change give the listing, dates, current and proposed nightly prices, and how many nights must sell at the new price to match expected profit at the current price. Label estimates and link the sources for demand claims. Give a date to reassess, a threshold for how many nights are still free and what price to use if that threshold is met. List the decisions you made for the user.
