# MovieFinder

**Find something to watch in under 60 seconds — and see exactly where to watch it.**

MovieFinder is a movie discovery web app. Users answer a few quick questions (or type a search), get a ranked list of matching movies, and see every legal way to watch each one: **Free**, **Subscription**, **Rent**, **Buy**, or **In Theatres** nearby.

> Status: Requirements complete — entering the AI-DLC **Inception** phase.

---

## Table of contents

- [Why MovieFinder](#why-moviefinder)
- [Key features](#key-features)
- [Roadmap](#roadmap)
- [Who it's for](#who-its-for)
- [How it works](#how-it-works)
- [Requirements summary](#requirements-summary)
- [Data sources](#data-sources)
- [Success metrics](#success-metrics)
- [Project status and AI-DLC](#project-status-and-ai-dlc)
- [Open questions](#open-questions)
- [Contributing](#contributing)
- [Legal](#legal)

---

## Why MovieFinder

Deciding what to watch usually means two separate searches: one to pick a movie, another to find where it's streaming, how much it costs, or whether it's in theatres. MovieFinder does both in one flow.

**Design principles**

- **Answer in under 60 seconds** — from landing page to a watchable choice.
- **Legal sources only** — every link goes to an official provider. No piracy.
- **Transparent pricing** — exact rent/buy prices; ad-supported services are labelled.
- **Mobile-first** — built for the phone-on-the-couch moment.

---

## Key features

### MVP

| Feature | Description |
| --- | --- |
| Guided quiz ("Help me choose") | Up to 6 optional tap-only questions: mood, genre, time available, who's watching, language, era |
| Keyword search | Title, actor, director or keyword, with autocomplete and typo tolerance |
| "My services" filter | Pick the subscriptions you already have; included titles are shown first |
| Region-aware availability | All results and providers filtered by your country (auto-detected, editable) |
| Ranked results with "Why this movie" | Relevance ranking plus a one-line reason for each pick |
| Where to watch | Providers grouped into Free / Subscription / Rent / Buy / Theatre, with price, quality (SD/HD/4K), deep links and "last updated" time |
| Theatre showtimes | Nearby cinemas, distance, 7-day showtimes, link to the official booking page |
| Watchlist | Works for guests (on device) and signed-in users (synced); merges on sign-up |
| Accounts | Email or Google/Apple sign-in; mark Seen / Liked / Not interested |
| Admin dashboard | Usage, top and zero-result searches, outbound clicks, curated collections |

---

## Roadmap

| Phase | Features |
| --- | --- |
| **MVP** | Everything in [Key features](#key-features) |
| **Phase 2** | AI natural-language search ("a funny heist movie, not too long"), "Surprise me", group/family mode, availability and price-drop alerts, parental content controls, TV series |
| **Phase 3** | Personalized recommendations from viewing history and ratings |

**Out of scope:** hosting or streaming video, in-app ticket payment, native mobile apps, user reviews and social features.

---

## Who it's for

| Persona | Need |
| --- | --- |
| Undecided viewer with subscriptions | A quick pick that's already on their services |
| Budget viewer, no subscriptions | Good movies that are free and legal |
| Parent planning family night | Age-appropriate picks everyone will like |
| Cinema-goer | What's in theatres nearby, and when |

---

## How it works

```
Landing page
   ├── "Help me choose" → guided quiz ─┐
   └── Search bar ─────────────────────┤
                                       ▼
                         Ranked results + "Why this movie"
                         (refine filters, sort, load more)
                                       ▼
                              Movie detail page
                                       ▼
            Where to watch: Free | Subscription | Rent | Buy | Theatre
                                       ▼
                 Official provider page / cinema booking page
```

---

## Requirements summary

### Functional (highlights)

- **FR-01–05** Search and guided input (quiz, keyword search, my services, price preference, region)
- **FR-06–11** Results list (badges, relevance ranking, "why this", filters, zero-result fallback, pagination)
- **FR-12–16** Movie detail and where-to-watch (five categories, legal providers only, theatre showtimes, freshness label)
- **FR-17–20** Watchlist and accounts (guest mode, social login, Seen/Liked/Not interested, settings)
- **FR-21–22** Admin (analytics dashboard, curated collections)

### Non-functional

| Area | Target |
| --- | --- |
| Performance | Results ≤ 2 s p95; detail page ≤ 1.5 s p95 |
| Data freshness | Availability ≤ 24 h old; showtimes ≤ 6 h old |
| Scale and uptime | 10,000 concurrent users; 99.5% monthly uptime; graceful fallback if a provider fails |
| Mobile and accessibility | Responsive from 360 px; Lighthouse mobile ≥ 85; WCAG 2.2 AA |
| Security | HTTPS only, OWASP Top 10 mitigations, rate limiting |
| Privacy | Consent-based location, data export/deletion, cookie consent |
| Legal | Comply with data-provider licences and attribution; legal sources only |
| Other | SEO-friendly server-rendered movie pages, i18n-ready, logging and monitoring |

The full requirements document (personas, user stories with acceptance criteria, NFRs, risks) is maintained separately and is the source of truth.

---

## Data sources

MovieFinder links out and relies on licensed third-party data. Vendors, pricing and licence terms are to be confirmed during Inception.

| Data | Candidates |
| --- | --- |
| Movie metadata (titles, posters, cast, ratings, trailers) | TMDB, OMDb, IMDb datasets |
| Streaming availability by region | TMDB watch providers (JustWatch-sourced), Watchmode, Streaming Availability API |
| Theatre showtimes and booking | Gracenote, MovieGlu, Fandango/Atom partner programs |
| Natural-language search (Phase 2) | A large language model API |

---

## Success metrics

Targets for 6 months after launch:

| Metric | Target |
| --- | --- |
| Median time from landing to "watch" click | < 60 s |
| Searches ending in an outbound provider click | ≥ 35% |
| Zero-result search rate | < 5% |
| 30-day returning users | ≥ 25% |
| Wrong or broken availability links | < 1% of clicks |

---

## Project status and AI-DLC

This project follows the **AI-Driven Development Lifecycle (AI-DLC)**:

1. **Inception** *(current)* — refine the intent into user stories, units of work, a domain model, an architecture proposal and a risk register.
2. **Construction** — build and test each unit of work.
3. **Operations** — deploy, monitor and iterate.

**Expected Inception outputs:** user stories with acceptance criteria, units of work for parallel delivery, a domain model (Movie, Provider, Availability, Region, Cinema, Showtime, User, Watchlist, Preference), a high-level architecture and a risk register.

### Assumptions

- Launch in the United States first, then expand by region.
- Movies only in the MVP.
- Budget available for paid data APIs.

---

## Open questions

- [ ] Launch country or countries?
- [ ] Monetization: affiliate links, ads, or both?
- [ ] Monthly budget for data APIs?
- [ ] TV series in the MVP or Phase 2?
- [ ] AI natural-language search at launch or Phase 2?
- [ ] Preferred tech stack and cloud provider?

---

## Contributing

Setup, tech stack and contribution guidelines will be added once the Inception phase settles the architecture.

---

## Legal

MovieFinder does not host, stream or distribute any video. All "where to watch" links point to licensed providers. Movie data and images are provided by third-party services under their respective terms, and required attributions will be displayed in the app.