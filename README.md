# 🦌 CritterCross Alert

**Live wildlife alerts for the roads you actually drive.**

🔗 **Live app:** [crittercross.netlify.app](https://crittercross.netlify.app/)

CritterCross Alert is a community-driven web application that helps drivers avoid wildlife collisions and helps injured animals get rescued faster. It combines live, crowdsourced sighting reports with geo-aware alerts, a voice-guided high-risk-zone warning system, and a direct SOS dispatch line to wildlife rescue organizations — plus a full planning dashboard for city and wildlife agencies to act on the data.

---

## Inspiration

The catalyst for CritterCross Alert was a deeply unsettling and heartbreaking personal experience. While driving, I came across a small baby monkey injured on the side of the road. It was bleeding, terrified, and in immense pain. As I stood there, a profound sense of helplessness washed over me — I wanted to help, but there was no immediate system in place to do so. These animals are living beings that feel pain just as we do; the forest is their home, and they deserve to be safe within it. I realized I couldn't just walk away and forget it. I needed to channel that distress into an actionable solution to protect our wildlife and ensure no one else has to feel that same helplessness.

## What it does

CritterCross Alert is a community-driven application and data dashboard designed to promote safe coexistence between humans and wildlife. It actively prevents collisions and aids injured animals through three core features:

1. **Dynamic Geo-fenced Alerts** — Warns drivers of approaching animal hotspots, with alert radii that scale to the driver's speed.
2. **Crowdsourced Intelligence** — Lets users log live sightings, processed through a time-decay model so drivers only see relevant, currently-active threats rather than stale reports.
3. **Emergency SOS Loop** — An integrated dispatch flow that connects drivers directly to wildlife rescue organizations for rapid triage of injured animals.

## How it was built

As a solo developer, I built the entire conceptual framework, application logic, and UI/UX architecture using **Google AI Studio**.

1. **Ideation & Logic Setup** — Used Gemini models within AI Studio to iteratively map out the complex logic required for the app, such as the dynamic alert radii and hotspot mapping features.
2. **UI/UX Prompting** — Generated the specific "dusk-shift" color palette (optimized for low-light dawn/dusk driving, when most collisions occur) and designed the 10 mobile screens and 6 dashboard views purely through advanced, structured prompting.
3. **System Instructions** — By configuring custom system instructions in Google AI Studio, I was able to rapidly simulate how the app's backend would triage an SOS report, ensuring the workflow between a driver and a rescue dispatcher was seamless.

The app originally shipped as a native Android (Kotlin + Jetpack Compose) prototype, and has since been ported to a single, dependency-free HTML/CSS/JavaScript web app so it can run instantly in any browser, on any device, with no install.

## Challenges

Building this as a solo project under a strict time limit was immensely challenging. Turning a raw, emotional idea into a practical, workable software architecture required intense focus. I struggled with figuring out how to simulate real-world testing environments without a live user base. Furthermore, increasing the app's utility so it was truly *animal-friendly* — and not just a human convenience tool — required multiple pivots, ultimately leading to the addition of the dedicated SOS Rescue Dispatch dashboard.

## Accomplishments

I am incredibly proud of designing a comprehensive, end-to-end ecosystem completely on my own. Translating the helpless feeling I had on the side of the road into a functional SOS rescue feature is my most meaningful achievement.

## What I learned

I learned that empathy is the most powerful driver for innovation. Technically, I discovered the immense potential of leveraging large language models in Google AI Studio to accelerate software architecture and UI/UX design. I learned how to structure complex application state flows — like managing user permissions, alert details, and verification timelines — and how to design an interface that prioritizes critical safety and fast response times over generic aesthetics.

## What's next

The ultimate goal is to evolve CritterCross Alert into a worldwide, implementable platform:

- Partner with local NGOs and wildlife rescue organizations.
- Integrate publicly available DOT (Department of Transportation) roadkill datasets to pre-seed hazard maps with real data.
- Develop fully native frontend clients for iOS and Android alongside the web app.
- Scale the alert network globally, transforming road infrastructure planning and saving as many innocent animal lives as possible.

---

## Features & Screens

The app is a single-page experience with the following flow:

| # | Screen | Description |
|---|--------|-------------|
| 1 | **Splash** | Two-slide animated intro explaining the mission, with pulsing paw-print motifs. |
| 2 | **Login** | Simulated Google sign-in, plus optional ID document upload for verified-user status. |
| 3 | **Permissions** | Requests location and notification access needed to trigger nearby alerts. |
| 4 | **Check-Post Verification** | QR-style scan simulation that syncs the local road's posted speed limit. |
| 5 | **Map (Home)** | Live crowdsourced heat map of sighting activity, high-risk-zone banner with voice alert, in-app route planner (primary vs. safer alternative route), current speed-limit badge, Report and Emergency SOS quick actions. |
| 6 | **Report a Sighting** | Species picker, animal count, photo attachment, and auto-pinned location. |
| 7 | **Active Alert** | Full-screen alert modal showing distance to an active sighting and recommended speed, with a link into the reasoning behind the alert. |
| 8 | **Alert Detail** | Explains why an alert fired (recent nearby reports) plus in-the-moment driving safety tips. |
| 9 | **Report History** | A driver's own submitted sightings, filterable by verification status. |
| 10 | **Sighting Detail** | Timeline of a single report's lifecycle: reported → verified → alert sent → zone cleared. |
| 11 | **Profile & Impact** | Personal stats, estimated collisions prevented, Wildlife Guardian level progress, and earned badges. |
| 12 | **Settings** | Alert radius slider, notification preferences, and species-specific filters. |
| 13 | **Emergency SOS** | GPS location capture, one-tap dispatch to a rescue partner, AI-assisted photo identification of the animal, and severity triage. |
| 14 | **Planner Dashboard** | A separate, six-tab command center for city/wildlife agencies: **Overview** (KPIs), **Hotspots** (species breakdown & trends), **Reports** (sortable table), **Corridors** (proposed infrastructure projects with cost/priority), **Rescue** (live case board + partner network), **Team** (access management). |

### Design language

CritterCross uses a **"dusk-shift" dark palette** — deliberately tuned for readability during the dawn/dusk hours when the vast majority of wildlife collisions occur:

| Token | Hex | Use |
|---|---|---|
| Night | `#0A0F1E` | Primary background |
| Dusk / Surface | `#1B2740` | Cards, elevated surfaces |
| Mist | `#8E9BC0` | Secondary text |
| Amber | `#FFB454` | Primary accent, CTAs |
| Coral | `#FF6B5A` | Danger / alert states |
| Moss | `#7FBF9E` | Safe / verified states |

---

## Tech Stack

- **Frontend:** Vanilla HTML, CSS, and JavaScript — no build step, no framework, no dependencies to install.
- **Fonts & Icons:** Google Fonts (Inter) and Material Symbols, loaded via CDN.
- **Browser APIs used:**
  - `Geolocation API` — requesting location during onboarding.
  - `Notification API` — requesting push permission during onboarding.
  - `SpeechSynthesis API` — spoken high-risk-zone and route-planning alerts.
  - `FileReader API` — local image preview for SOS animal-identification uploads.
- **Hosting:** Static site, currently deployed on [Netlify](https://www.netlify.com/).

> Note: This is a **frontend prototype/demo**. Data such as sightings, reports, and dashboard metrics are simulated locally in the browser — there is no live backend, database, or real Gemini API call wired in yet. The AI-identification and dispatch flows are simulated to demonstrate the intended user experience.

## Project Structure

```
crittercross-web.html   # The entire application — markup, styles, and logic in one file
README.md               # This file
```

## Running Locally

No installation required:

1. Download `crittercross-web.html`.
2. Double-click it, or open it in any modern browser (Chrome, Edge, Firefox, Safari).

That's it — the whole app runs client-side.

## Deployment

The app is currently live at **[crittercross.netlify.app](https://crittercross.netlify.app/)**, hosted for free on Netlify as a static site (drag-and-drop deploy, no server required). Since it's a single static file, it can just as easily be hosted on GitHub Pages, Vercel, or Cloudflare Pages.

## Roadmap

- [ ] Real backend (database + auth) to replace simulated local state
- [ ] Live Gemini Vision integration for SOS animal identification
- [ ] Real-time crowdsourced sighting feed with time-decay expiry
- [ ] DOT roadkill dataset ingestion to pre-seed hotspot maps
- [ ] Native iOS and Android clients
- [ ] Partnerships with wildlife rescue NGOs for live dispatch

## License

TBD

## Acknowledgments

Built solo, prototyped end-to-end using Google AI Studio and Gemini models for ideation, UI/UX design, and system-instruction simulation of the SOS dispatch workflow.
