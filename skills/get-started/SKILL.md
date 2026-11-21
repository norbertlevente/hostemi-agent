---
name: get-started
description: Use when the user has just installed or connected Hostemi or asks how to start.
---

# Get started

If the user triggered this, it's because they just connected Hostemi or want to know how to start. Show what the assistant can read and what the user can do first. If they connected Hostemi during another request, resume that request after the check.

What you do here

- Check that the user's Hostemi account can be read.
- Show the listing names and connected platforms. Say what needs the user's attention.
- Explain approvals in one sentence and offer a first task.

## Guardrails

- If a Hostemi tool returns `PLAN_REQUIRED`, relay its `message` without naming plans or suggesting a purchase. Stop the blocked work.
- Ask only if you cannot find a fact that would change the result, tool access blocks progress, or the user's request is ambiguous in a way that would change the result. Put your questions in one message with your recommendation first and decide everything else yourself.

## Steps

1. **Check the connection.** Call `get_context`. If the client shows a sign-in prompt, ask the user to sign in there and retry once they finish.
2. **Show the account and what needs attention.** Give the account name if available, the listing names and the platforms for each listing. If `data.listings` is empty, call `get_add_listing_link` and give its `data.url` so the user can add a listing in Hostemi. If any item in `data.attention` needs action today or blocks their request, name one. Give the approval setting from `data.approval.name` and explain that changes guests or platforms would see start as previews for the user to approve.
3. **Offer a first task.** For a setup-only request with a listing, offer to show the next two weeks of the calendar or review prices for the season. If `data.canChange` is false, state that the connection can only read. Otherwise also offer to draft a guest reply.

Use the hostemi skill for the task the user picks and the pricing-strategy skill when they ask what to charge/price.
