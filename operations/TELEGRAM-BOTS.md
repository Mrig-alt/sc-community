# Telegram Bots — Full Specification

All bots are built using the Telegram Bot API and hosted on a lightweight server or Cloudflare Workers. The founder has existing experience building Telegram bots (see telegram-email-watcher project).

---

## Bot 1: SC Signal Bot

**Purpose**: Deliver one sharp SC disruption or market signal every Monday morning — keeps the community informed without members having to hunt for news.

**Trigger**: Scheduled — every Monday at 9:00 AM (Madrid time)

**Data sources**:
- Supply Chain Dive (RSS feed)
- McKinsey Supply Chain Insights
- Reuters / FT trade and logistics tags
- Manual curation by founder (override option)

**Message format**:
```
📡 SC Signal — [Date]

[One-line headline]

[2-3 sentence summary of what happened and why it matters for practitioners]

Source: [link]

💬 What does this mean for your sector? Reply below.
```

**Build timeline**: Month 1
**Complexity**: Low — RSS fetch + scheduled message

---

## Bot 2: Event Reminder Bot

**Purpose**: Automatically remind members 24 hours and 1 hour before each community session — removes the admin burden from the founder.

**Trigger**: Scheduled — 24h and 1h before each event (manually set per event)

**Message format (24h)**:
```
📅 Tomorrow: [Event Name]

🕐 [Time] Madrid / [Time] Mumbai
📍 [Location or video link]

Come with one SC challenge in mind — even if you're not the case-bringer.
```

**Message format (1h)**:
```
⏰ Starting in 1 hour: [Event Name]

[Video link or address]

See you there.
```

**Build timeline**: Month 1
**Complexity**: Low — time-based scheduler with stored event data

---

## Bot 3: Case Prompt Bot

**Purpose**: Run a weekly async discussion in the Telegram group — keeps the community active between sessions and surfaces problems for future roundtables.

**Trigger**: Scheduled — every Wednesday at 12:00 PM (Madrid time)

**Rotating prompt bank**:
- "What's one SC decision you've seen go wrong? What was the real cause?"
- "What's a supply chain myth you believed before working in the field?"
- "If you could fix one thing in your current or last SC role, what would it be?"
- "What's a framework you use that most MBAs never hear about?"
- "Describe a disruption you experienced. How was it handled? What would you do differently?"
- "What's the most underrated skill in supply chain?"

**Message format**:
```
🔁 Weekly Case Prompt

[Prompt question]

Reply below — anything goes, no wrong answers. Best responses will be anonymised and used in the next newsletter.
```

**Build timeline**: Month 1
**Complexity**: Low — rotating prompt array + scheduled message

---

## Bot 4: GitHub Update Bot

**Purpose**: Notify the Telegram group every time a new case write-up, framework, or resource is pushed to the GitHub repo — keeps both platforms alive and connected.

**Trigger**: GitHub webhook on push to main branch (filtered to `/updates/`, `/resources/`, `/chapters/` paths)

**Message format**:
```
📂 New on GitHub

[File name / title]
[One-line description of what was added]

🔗 [Direct GitHub link]
```

**Build timeline**: Month 2
**Complexity**: Medium — GitHub webhook → bot message pipeline

**Integration note**: This is the key connector between GitHub and Telegram. Every time a case write-up is published after a session, the community is automatically notified.

---

## Bot 5: AMA Collector Bot

**Purpose**: Before each AMA / Operator Session, collect questions from the community and rank them by upvote — so the best questions rise to the top and the session is high-quality.

**Trigger**: Manual activation by founder 48 hours before each AMA

**Flow**:
1. Founder activates bot with `/startama [Speaker Name] [Topic]`
2. Bot posts collection message to group
3. Members submit questions by replying to the bot
4. Bot creates a voting thread — members upvote their favourites
5. 1 hour before the AMA, bot posts the top 5 questions
6. Founder uses the ranked list to run the session

**Message format (collection)**:
```
🎤 AMA with [Speaker Name] — [Date]

Topic: [Topic]

Submit your questions below. The top-voted questions will be answered live.

Reply to this message with your question.
```

**Message format (top questions)**:
```
🏆 Top Questions for Today's AMA

1. [Question 1] — [X votes]
2. [Question 2] — [X votes]
3. [Question 3] — [X votes]
4. [Question 4] — [X votes]
5. [Question 5] — [X votes]

Starting in 1 hour. Link: [link]
```

**Build timeline**: Month 2
**Complexity**: High — voting system, state management, ranked output

---

## Bot 6: Welcome Bot

**Purpose**: Automatically send a structured welcome message to every new member who joins the Telegram group — orients them immediately without the founder having to do it manually.

**Trigger**: New member joins the group (Telegram `new_chat_members` event)

**Message format**:
```
👋 Welcome to the Madrid–Mumbai SC Community, [Name]!

Here's what you need to know:

📌 What we do: Monthly SC roundtables, build sprints, and curated connectors. Every session produces a written output.

📂 Our GitHub: [link] — case write-ups, frameworks, templates, and the community roadmap all live here.

💬 How to participate:
• Bring a real SC problem to the next session
• Reply to the weekly Case Prompt
• Introduce yourself below — name, background, one SC topic you care about

📅 Next session: [date] — details pinned above.

Glad you're here.
```

**Build timeline**: Month 2
**Complexity**: Low — event trigger + templated message with dynamic name

---

## Tech Stack

- **Language**: JavaScript (Node.js) — consistent with existing bot work
- **Hosting**: Cloudflare Workers (serverless, zero cost at this scale)
- **Telegram library**: node-telegram-bot-api or grammy
- **Scheduler**: Cloudflare Cron Triggers for time-based bots
- **GitHub integration**: GitHub Webhooks → Cloudflare Worker endpoint
- **State storage** (for AMA bot): Cloudflare KV or Supabase

---

## Build Order

| Priority | Bot | Why |
|----------|-----|-----|
| 1 | SC Signal Bot | Keeps community active from day one with zero manual effort |
| 2 | Event Reminder Bot | Removes admin burden immediately |
| 3 | Case Prompt Bot | Drives weekly async engagement |
| 4 | GitHub Update Bot | Connects the two main platforms |
| 5 | Welcome Bot | Needed once member count grows beyond ~20 |
| 6 | AMA Collector Bot | Only needed from Month 3 when AMA format begins |
