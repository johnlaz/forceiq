# ForceIQ — AI Workforce Suite

**Deploy a full AI workforce in minutes. No code. No cloud setup. No monthly seat fees.**

ForceIQ is a single-file web app that runs entirely in your browser. You bring the Groq API key — ForceIQ brings the agents, the workflows, the social engine, the outreach builder, and the live grant discovery. Every output is grounded in your company's real context, voice, and goals.

---

## What It Does

Most AI tools give you a chat box. ForceIQ gives you a workforce.

You configure your company once — name, mission, founder voice, target audiences, social platforms, connected apps. Every agent reads that context before producing a single word. The result is output that sounds like you, not like a generic AI.

Agents run in sequential pipelines. Agent 1 produces output. Agent 2 reads it and continues. Agent 3 reads both and finishes. Real chain-of-thought handoffs — not parallel guesses that you then have to stitch together yourself.

---

## Core Features

### ⚙️ Settings-Driven — Nothing Baked In
Everything is configurable. Company name, mission, founder voice, social platforms, target audiences, connected apps, URL sources, grant keywords — all set in a structured settings panel with eight tabs. Change the company and the entire workforce adapts. Two companies? Two workspaces. One file, zero conflict.

### 🔀 Sequential Pipeline Workflows
Five built-in workflow templates: Grant Readiness, Brand Content Batch, Outreach Strategy, Weekly Review, App Launch Prep. Each runs agents in order, passing output down the chain. Steps are visible live — you watch each agent think, then hand off to the next. Save any custom pipeline for one-click reuse.

### 📣 Social Content Engine
One update, every platform. Describe a milestone. Pick a tone (Impact Story, Milestone, Educational, Behind the Scenes). Check which platforms. Hit generate. LinkedIn gets a professional two-paragraph post. Instagram gets a short emotional story. Facebook gets a community-first message. X/Twitter gets a punchy line under 200 characters. Each platform has its own tone note you configure once in Settings.

### ✉️ Outreach Builder
Define your target audiences in Settings — SLP clinics, school districts, parent groups, grant funders, potential partners. Select an audience, pick a goal (test invite, partnership, feedback request, grant support), and generate email drafts written in your voice. One variation or three options. Subject line, body, and CTA included.

### 💰 Live Grant Discovery
Real Grants.gov API. Not a list of grants someone scraped last year — actual live federal opportunities queried at the moment you search. Keywords auto-populate from your settings. Filter by applicant type and status. Every result links directly to the official grants.gov page. No hallucinated deadlines, no invented award amounts.

### 📚 Knowledge Base with Auto-Injection
Add any URL, paste code or text, upload a file, or scan a GitHub repo. ForceIQ indexes it and injects relevant chunks into agent prompts automatically. Agents cite their source. Add your app portfolio page and every agent knows what you've built. Add a grant guideline document and the Grant Readiness pipeline quotes from it directly.

### 🧠 Long-Term Brain
Add learnings that persist across every session. "Always mention the Community Pilot Program in parent outreach." "Never use the word leverage." "Grant applications should lead with user impact numbers before features." Every agent reads these before every task. The workforce gets smarter as you add more.

### 🏢 Multi-Workspace / Multi-Company
One file. Multiple companies. Each workspace has fully isolated settings, agents, memory, KB, registry, and config. Switch between workspaces with one click. Perfect for agencies managing client accounts, or founders running multiple brands.

### 📬 Mail Hub
Connect Gmail via OAuth or route through a local IMAP bridge (same architecture as OEL Command, port 7843). Paste any email or social comment and the Growth Agent classifies it, then drafts a reply in your voice — email reply, social reply, or clinical support escalation depending on content.

### 🎨 Dark & Light Mode
Full dark luxury mode (deep navy, gold, teal) and clean light mode. Both ship in the same file. Switch in Settings → Appearance. Preference persists across sessions.

---

## Who It's For

**Non-profits and social impact organizations** building brand presence, pursuing grants, and reaching communities — without a marketing team.

**Founders and solo operators** running multiple products who need a workforce that knows the full portfolio, not just one project.

**Service businesses** that need consistent client communications, quote generation, and operations summaries without a full-time ops person.

**Agencies** managing multiple client workspaces from a single dashboard, with clean separation between accounts.

---

## Getting Started

**1. Open the file**
Open `forceiq-v5.html` in any modern browser. No server required. No install. No dependencies.

**2. Get a Groq API key**
Free tier available at [console.groq.com](https://console.groq.com). The free tier gives you ~500,000 tokens per day on `llama-3.3-70b-versatile` — more than enough for heavy use.

**3. Run the Setup Wizard**
Click "Run Setup Wizard" on the splash screen. Five steps: welcome → company profile + Groq key → agents → social & outreach → verify. Takes about five minutes.

**4. Run your first pipeline**
After the wizard, click **🚀 Grant Readiness** in the top bar. Watch the agents run. Check the output against what you told it about your company. If the output sounds generic, your settings need more specificity — especially Voice & Tone.

**5. Index your Knowledge Base**
Go to Settings → URL Sources. Add your company website or app portfolio URL. Click "Fetch & Index Now." Agents will reference that content in every subsequent task.

---

## Architecture

ForceIQ is a **single-file HTML/CSS/vanilla JS PWA**. No build tools, no npm, no bundler. Open it in a browser and it runs. Host it on GitHub Pages and it's a web app. Save it to your desktop and it's a local app.

**Data storage:** All workspace data is stored in `localStorage` using workspace-scoped keys (`fiq5_{workspaceId}_{key}`). Nothing leaves your device unless you explicitly export it or make an API call. Export at any time as a clean JSON file. API keys are redacted from exports automatically.

**AI engine:** [Groq](https://groq.com) running `llama-3.3-70b-versatile`. Optional Gemini integration for long document analysis. Every Groq call includes: org context, active memories, relevant KB chunks, voice & tone settings, and agent backstory — assembled dynamically per call.

**Real APIs used:**
- `api.grants.gov/v1/api/search2` — Live federal grants (no auth required)
- `api.github.com` — Repo scanning and file fetching
- `gmail.googleapis.com` — Gmail OAuth (requires Google Cloud Client ID)
- `api.allorigins.win` — CORS proxy for URL fetching
- `api.groq.com/openai/v1` — AI completions

**No fake data.** No simulated outputs. If an API call fails, you see the real error. If a grant doesn't exist, it doesn't appear.

---

## Settings Reference

| Tab | What Goes Here |
|-----|---------------|
| **API Keys** | Groq key (required), Gemini (optional), Gmail OAuth Client ID, IMAP bridge config, GitHub token |
| **Company** | Name, parent brand, type, founder, state, website, mission, phase, grant keywords |
| **Social Platforms** | Toggle each platform on/off, add a tone note per platform |
| **Target Audiences** | Named audience segments with type and description — drives Outreach Builder |
| **Connected Apps** | Your product roster — name, URL, status, one-liner — agents reference this |
| **URL Sources** | Add any URL to fetch and index into KB — your app portfolio, grant guidelines, brand pages |
| **Voice & Tone** | Writing voice, email signature, things to never say, brand hashtags |
| **Appearance** | Dark mode (default) or light mode |

---

## Workflow Templates

| Template | Steps | Best For |
|----------|-------|----------|
| **Grant Readiness** | Org summary → Grant strategy → Compliance posture | Non-profits preparing applications |
| **Brand Content Batch** | Brand story → Social posts → Newsletter intro | New launches, milestones, campaigns |
| **Outreach Strategy** | Audience analysis → Cold email → Follow-up sequence | Beta testing, partnerships, pilots |
| **Weekly Review** | Progress summary → Blockers → Priorities | Operations cadence |
| **App Launch Prep** | Launch checklist → Press blurb → App description | Product releases |

---

## Token Usage Reference

| Action | Approximate Tokens |
|--------|-------------------|
| Single agent task | 300–600 |
| Full 3-step pipeline | 900–1,800 |
| Social Engine (3 platforms) | 600–900 |
| Outreach Builder (3 variations) | 700–1,100 |
| Mail route + draft | 400–600 |
| Config test | ~100 |

Groq free tier: ~500,000 tokens/day. A full day of heavy use across all features typically uses 10,000–30,000 tokens.

---

## Privacy & Security

- **No data leaves your device** except API calls you explicitly trigger (Groq, Grants.gov, GitHub, Gmail)
- **API keys are stored in `localStorage`** — they are never sent anywhere except directly to their respective APIs
- **Exports redact all API keys** — safe to share workspace state with collaborators
- **No analytics, no telemetry, no tracking** — this is a local tool

---

## Built With

- Vanilla HTML/CSS/JavaScript — no framework
- [Groq](https://groq.com) — `llama-3.3-70b-versatile`
- [Syne](https://fonts.google.com/specimen/Syne) + [DM Sans](https://fonts.google.com/specimen/DM+Sans) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)
- Lazzaro Standard design system — Gold `#c9a227` · Teal `#2dd4bf` · Deep Navy `#060810`

---

## Part of the LAZLAB Ecosystem

ForceIQ is built and maintained by [LAZLAB](https://johnlaz.github.io), the parent brand behind a suite of single-file PWA tools including:

- **JVox AAC** — AI-powered augmentative communication for non-verbal individuals
- **BRVTY** — AI book intelligence with Gemini TTS for audio-first reading
- **AXIOM** — Stock intelligence PWA with multi-source data and Groq analysis
- **OEL Command** — CRM and quote intelligence for service operations (TRSAV)
- **LazForge** — Project command center with AI brainstorm and document vault
- **Scout AI** — Talent triage and interview intelligence
- **ARMORY** — Firearms inventory with insurance export
- **LazEstate** — Real estate portfolio and valuation intelligence

---

## Version

**ForceIQ v5.0** · Settings-driven · Multi-workspace · Real APIs only · No baked-in data

---

*Built by LAZLAB. Single-file. Local-first. Yours.*
