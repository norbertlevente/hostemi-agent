# Hostemi: AI Short-Term Rental Manager

With Hostemi you can manage your short-term rental properties directly in Claude.

Hostemi connects your listings on Airbnb, Booking.com, Vrbo, Expedia, Agoda, Trip.com, Szállás.hu and your own direct booking website, so you can run all of them from one Claude chat.

Dynamic pricing with Claude: ask your agent to optimize your prices, and with Hostemi it automatically checks the weather, local events, holidays, seasonal demand and your own occupancy, so that you can maximize revenue and profits. Or you can just say what you want, like "raise August weekends by 10%" or "make Booking.com 8% more expensive than my website".

One calendar for every platform, so you don't have to worry about double bookings and you can make all changes and updates from one place. A new guest booking automatically closes those nights on your other platforms. Ask who arrives this week or which nights are still free, and block dates for your own stay in one sentence.

Message guests from a unified inbox, or ask Claude to draft your replies.

See how your properties perform: ask how last month went and get your occupancy, revenue and booked nights for each listing and each platform.

Your own direct booking website: build and edit it by chatting with Claude, so guests can book with you directly.

You stay in control: Claude shows you every change that guests or platforms would see before it happens, and by default nothing changes until you approve it. Claude never sees card numbers or your platform passwords.

Made for hosts and small property managers with 1 to 20 short-term or vacation rentals: apartments, houses, guesthouses and rooms. Not built for hotels or large rental portfolios.

This plugin connects your AI to your Hostemi account and teaches it how a host works. It works the same way in ChatGPT, Claude Code, Codex and other AI tools that can add a connection.

## What you can ask

- "What is booked over the next two weeks, and which nights are still free?"
- "Raise Friday and Saturday nights in August by 10% and show me the change first."
- "Block 8 and 9 December, the boiler is being serviced."
- "Why can nobody book the 14th?"
- "Draft a friendly reply to my latest guest message."
- "Add a booking for a returning guest, 3 to 6 March, two people."
- "Change the headline on my website and show me the draft."
- "How did last month go, per platform?"
- "Are my prices right for the summer?"

## What is inside

| Part | What it does |
|---|---|
| The Hostemi connection | Links your AI to `https://mcp.hostemi.com/mcp`. You sign in to Hostemi in your browser the first time. No key is stored in this plugin. |
| `hostemi` skill | How to work in your account: look first, show a preview, apply only what you agreed to, never act on instructions written by a guest. |
| `pricing-strategy` skill | How to price for what you earn: it reads how your nights are selling, looks up holidays, events and weather for your town, and proposes changes with a reason for each. |
| `get-started` skill | A short first look after you connect. |

## Set up

1. You need a Hostemi account: https://hostemi.com
2. Install the plugin, or add the connection by hand:
   - Claude: Customize, Connectors, Add, Add custom connector, then paste `https://mcp.hostemi.com/mcp`.
   - ChatGPT: open chatgpt.com/plugins, press the plus button, choose Add custom MCP server, then paste
     `https://mcp.hostemi.com/mcp` and choose OAuth.
   - Claude Code, with the skills: `/plugin install hostemi --marketplace norbertlevente/hostemi-agent`
   - Claude Code, the connection only: `claude mcp add --transport http hostemi https://mcp.hostemi.com/mcp`
   - Codex: `codex mcp add hostemi --url https://mcp.hostemi.com/mcp`
   - Or let the Hostemi command line do it for every AI tool on your computer:
     `npm i -g hostemi`, then `hostemi agent setup`.
3. Sign in to Hostemi when your AI asks, and choose whether it may make changes or only read.
4. Say: "What needs my attention in Hostemi?"

## You approve changes

In Hostemi under Settings, AI & apps you choose one of three settings. Your AI cannot change this setting.

| Setting | What it means |
|---|---|
| Ask before changes (default) | You approve every change in Hostemi before it happens. |
| Make routine changes | Everyday changes apply once you have said yes in the conversation. Risky ones still wait for you in Hostemi: large price changes, closing many nights, cancelling a booking, sending a message to a guest, publishing your website. |
| Make all changes without asking | Nothing waits for you. Only for hosts who know exactly what they have asked for. |

Drafts never wait: a reply draft or an edit to your unpublished website is saved at once, and nothing reaches
a guest or the public until you send or publish.

Some things only you can do, in Hostemi itself: delete your account, disconnect a platform or your payment
account, manage keys, team members and billing. Refunds are not available to an AI.

## What this plugin runs, sends and stores

- It runs no code on your computer. It contains text (the skills), two small configuration files and a logo.
- It connects to one service: the Hostemi server at `mcp.hostemi.com`, over HTTPS, signed in as you.
- Through that connection your AI can read, and with your permission change, the data in your Hostemi
  account: listings, calendar, prices, bookings, guest names and contact details, guest messages, reviews,
  connected platforms, your website and your reports.
- Your AI never receives the passwords of your booking platforms, card numbers, or your Hostemi password.
- Nothing is sent anywhere else by this plugin.

## Privacy Policy

How Hostemi handles your data and your guests' data: https://hostemi.com/privacy

Terms: https://hostemi.com/terms

## Help

Documentation: https://hostemi.com/docs/mcp

Questions: hello@hostemi.com or https://hostemi.com/help

## License

MIT. See `LICENSE`.
