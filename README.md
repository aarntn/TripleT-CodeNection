# Kelana by Triple T

**Team:** Ahmad Fathir, Aaron John Tan, Muhammad Abqary Nasution

**Problem Statement:** Travel Planner

**Video Presentation:** [Unlisted YouTube Link](https://www.youtube.com/watch?v=etT5gY_F4IQ)

**Presentation Slides:** [Public Link](https://www.figma.com/proto/iBfdsxoWxp3Diyft6Vy3Te/Codenection?node-id=4200-8644&viewport=202%2C261%2C0.12&t=Sf2qz3SY7UrjGkBN-1&scaling=contain&content-scaling=fixed&starting-point-node-id=4200%3A8644&page-id=921%3A23)

## 1. Project Overview

### The Problem

Planning a group trip means juggling flights, accommodation, budgets, activities, and everyone's individual preferences, and that's before anything changes last-minute. In practice, this ends up scattered across five disconnected places: a group chat, saved social media inspiration, a spreadsheet, booking emails, and a maps app. None of these track what's already paid, what each person actually cares about, or who has already compromised. This burden typically falls on one person, the default "trip organizer," who collects everyone's dates, compares prices, builds the itinerary, and chases people for money, while feeling anxious about forgetting something and guilty when someone doesn't get what they wanted.

When something changes on the ground, such as a delay, bad weather, or a closed attraction, that person has to manually rebuild the day while the rest of the group waits. The stakeholders are the de facto organizer, the other group members whose money and preferences are at stake, and solo travelers who have no one to check their plan against.

Existing apps such as Wanderlog, Mindtrip, TripIt, Pilot, and Stippl already cover AI-generated itineraries, group voting, budgeting, and maps, while newer entrants such as TripMazer, Andante, Travolp, and Tripolam have begun offering automatic replanning after disruptions. However, each only solves one piece, such as bookings, budgeting, or itineraries, and treats "replanning" as regenerating the whole itinerary from scratch rather than making the smallest change that preserves what is already paid, agreed upon, or non-negotiable for a specific person. None of them account for group fairness when a plan breaks.

### Our Solution

Kelana is a connected trip-planning system built on the idea that a trip is not an itinerary to generate once. Instead, it is a set of live commitments, including dates, budget, preferences, non-negotiables, and payments, that should be repaired rather than rewritten whenever something changes. Rather than acting as another all-in-one itinerary generator, Kelana focuses on what happens once an existing group trip becomes difficult to maintain. It uses everything the group has already agreed on to make the smallest possible fix when plans break. Kelana supports both group and solo trips, and a completed trip can live on as a shareable template.

**Feature set:**

- **Circle** (group alignment) — collects dates, budget, interests, and non-negotiables into a group profile; helps the group pick a destination via comparison cards and voting.
- **Tally** (shared cost) — calculates real per-person cost, converts to each member's currency, collects shares before booking, and locks paid items against future changes.
- **Relay** (shared workload) — splits trip planning into tasks distributed across members, reassigning stale ones automatically.
- **Reroute** (minimum-change repair) — when a delay/closure/weather event disrupts the plan, proposes the smallest fix that leaves paid items and hard requirements untouched, asking approval only from affected members.
- **Trail** (memory & discovery) — prompts short clips during the trip, stitches them into a recap, and lets finished trips be published and forked as templates.
- Supporting features: confidence cards, swipe-to-vote for activities, a "basics" map layer (toilets, luggage storage, pharmacies, prayer rooms), optional attendance/per-person currency, and a decision log.

## 2. Ideation & Process

### 2.1 Ideas We Considered

### Kept

#### Core Features

| Idea | Why it was kept |
| :-- | :-- |
| Circle | Establishes the group's dates, budget, preferences, and non-negotiables that Reroute later checks against. |
| Tally | Tracks real per-person cost and locks paid items, which Reroute relies on to avoid undoing payments. |
| Relay | Distributes planning tasks so responsibility doesn't default to one organizer, directly addressing the core pain point. |
| Reroute | This is the actual differentiator from research: minimum-change repair rather than itinerary regeneration. |
| Trail | Extends the product past planning into memory/discovery and lets trips become reusable templates. |

#### Supporting Features

| Idea | Why it was kept |
| :-- | :-- |
| Confidence Card | Helps justify destination decisions. |
| Swipe-to-vote | Speeds up activity selection. |
| Basics map layer | Helps with practical in-trip needs. |
| Task splitting | Folded into Relay — reduces organizer workload. |
| Per-person currency | Improves cost comprehension. |
| Optional attendance | Handles differing interests without splitting the whole trip. |
| Decision log | Preserves group agreement. |
| Saved social media inspiration | Helps ideas enter the trip. |
| Advanced Trail/Setlog-style memory | Part of Trail we want to develop further — deepens the memory/discovery experience beyond the basic MVP clip capture. |

### Dropped

#### Dropped as a Main Product / Standalone Feature

| Idea | Why it was dropped |
| :-- | :-- |
| Generic AI itinerary generator (V1) | Already common across Wanderlog, Mindtrip, TripIt, Pilot, and Stippl. |
| Automatic AI replanning after disruption (V2) | Competitors (TripMazer, Andante, Travolp, and Tripolam) were already moving into this, so it wasn't distinctive alone. |
| Group voting (standalone) | Useful, but already established in existing group-travel products. |
| Expense splitting (standalone) | Solves one part of the problem but already exists in travel and dedicated expense apps. |
| Route optimization | Common mapping/planning capability, not distinctive. |
| Flight/disruption alerts (standalone) | Tells the group what failed but doesn't complete recovery. |
| Shared group chat (built-in) | Duplicates existing behavior rather than reducing the need for it. |

#### Deprioritized from MVP

| Idea | Why it was deprioritized |
| :-- | :-- |
| Full payment processing | Substantial build time; payment status alone demonstrates the concept. |
| Email booking import | TripIt already demonstrates this; it doesn't prove Kelana's main mechanism. |
| Full offline package | Practical but a weak contribution to the product's distinction. |
| Emergency contact hub | Useful but separate from the central planning/recovery problem. |
| Safety-area scoring | Requires trustworthy, location-specific safety data. |
| Solo pricing detection | Valuable but outside the strongest initial target. |
| Community travel feed | Large social-product scope, limited benefit to the core demo. |
| Automatic live disruption detection | The prototype can use a triggered disruption; live detection adds external dependencies. |
| Full booking marketplace | Enormous scope, already served by mature providers. |

### 2.2 Ideation Board

**FigJam Board Link:** [Public Link](http://s.id/IdeationBoard)

#### 2.2.1 Problem Statement

![Problem Statement](Images/Problem%20Statement.png)

#### 2.2.2 Pain Point & Affinity Diagram

![Pain Point & Affinity Diagram](Images/Pain%20Point%20%26%20Affinity%20Diagram.png)

#### 2.2.3 How Might We

![How Might We](Images/How%20Might%20We.png)

#### 2.2.4 Solution Idea

![Solution Idea](Images/Solution%20Idea.png)

#### 2.2.5 Prioritization Matrix

![Prioritization Matrix](Images/Prioritization%20Matrix.png)

#### 2.2.6 Feature Architecture

![Feature Architecture](Images/Feature%20Architecture.png)

#### 2.2.7 User Flow

![User Flow](Images/User%20Flow.png)

#### 2.2.8 Trip Cases

![Trip Cases](Images/Trip%20Cases.png)

### 2.3 Mentor Consultation

| Date | Mentor | Feedback Received | What Was Changed |
| :-- | :-- | :-- | :-- |
| September 12, 2026 | Janelle Tan | A strong product also needs to be communicated clearly and effectively. The most impressive and distinctive aspects of the concept should be presented within the first one to two minutes of the pitch. The presentation should quickly establish the strongest selling points and avoid spending too much time on secondary details. The team should define the main message they want reviewers to remember after the presentation. | Restructured the pitch so the strongest features and value proposition appear at the beginning. Reduced the time spent explaining secondary features and reorganized the presentation around a clearer core message. The opening section now focuses on the main problem, Kelana's strongest differentiators, and the end-to-end user experience. |
| September 10, 2026 | Faris Imran | The current concept appears to place significant emphasis on social-media-related features. The Setlog feature and montage experience were encouraged as potentially strong differentiators. The product positioning should be clarified to determine whether Kelana should be presented primarily as a social-media-driven travel planning platform or as a broader collaborative travel tool. The team was also encouraged to define a clear, grounded one-sentence product pitch. Particular attention should be given to the feature where users paste TikTok or social media links, and Kelana extracts useful travel information from them. Feature implementation and design decisions should clearly connect back to the core problem and demonstrate focused ideation. | Refined the product positioning to place a stronger emphasis on collaborative trip planning. We don't fully agree with the social media angle yet, as our main focus is repairing trips while making them memorable — but we remain open to suggestions for future rounds. Strengthened the Setlog/Trail concept and planned a montage-based trip recap. Clarified the social-link import flow by showing how saved TikTok or Instagram content can be converted into structured trip ideas. Updated the feature prioritization so each major feature is tied directly to a specific user problem. |

## 3. Design & Prototype

**UI Prototype:** [Public Link](https://www.figma.com/proto/iBfdsxoWxp3Diyft6Vy3Te/Codenection?node-id=670-22311&viewport=311%2C237%2C0.08&t=m63bzp6gOzhMm973-1&scaling=scale-down&content-scaling=fixed&starting-point-node-id=670%3A22311&page-id=7%3A3)

**Onboarding & Trip Setup**

![Onboarding & Trip Setup](Images/Onboarding%20%26%20Trip%20Setup.png)

Users sign in with Google or Apple in one tap, no lengthy signup form. From the home screen, they can start planning a new trip from scratch or jump-start with a featured community guide like the 5-Day Johor Bahru or 3-Day Penang trip. Once a trip is created, Kelana generates a shareable link so friends can join instantly by email, skipping the usual back-and-forth group chat. Everyone then marks their availability on a shared calendar, and Kelana highlights the overlapping days so the group can confirm the dates or adjust the trip length before locking it in.

**Itinerary, Responsibilities & Spending**

![Itinerary, Responsibilities & Spending](Images/Itinerary%2C%20Responsibilities%20%26%20Spending.png)

Each day's itinerary is laid out on a map with travel time and distance between stops, and users can switch between a day-by-day map view or a per-person schedule to see who's doing what and when. Trip tasks such as accommodation, transport, food, and activities can be assigned to specific members, alongside group-agreed rules like "must visit Penang Hill" or "back home by Thursday morning." A group spending tracker shows total expenses against each member's individual budget, flags pending payment requests, and logs recent shared expenses along with their settlement status.

## 4. What Makes It Different

**Novel features and what's original about each:**

- **Reroute — minimum-change repair.** Instead of regenerating the itinerary from scratch (the common approach), it computes the smallest possible fix that leaves paid bookings and hard requirements untouched. This is the core mechanic that came out of our research — competitors treat a disruption as a reason to replan everything.
- **Constraint-aware repair.** Each member's non-negotiables (allergies, accessibility needs, budget ceilings) are stored once and automatically re-checked on every repair, not just enforced at initial planning. The twist is that this constraint-checking travels with the trip through every later change.
- **Payment-aware planning.** Tally's payment-lock state feeds directly into Reroute, so a repair can never suggest moving or cancelling something the group already paid for. Most budgeting tools and itinerary tools don't talk to each other at all.
- **Fairness tracking.** The system remembers which member has already had to give something up in a previous repair, so the same person isn't repeatedly the one who compromises. This is a fairness dimension we didn't find addressed in any competitor.
- **Relay — distributed planning workload.** Planning tasks are generated and handed out by the system rather than falling to whoever happens to be "in charge," and stale tasks get reassigned automatically. The twist is treating organizing itself as a shared, trackable workload.
- **Trail — forced-capture memory & forkable trips.** Short clips are prompted in the moment and tied to a specific itinerary activity — no camera-roll uploads or backfilling later — and a finished trip can be published and forked by other groups as a starting template. The twist is treating a finished trip as reusable data, not just a memory.

**Comparison with existing solutions:**

| Dimension | Kelana | Existing Solutions |
| :-- | :-- | :-- |
| AI-generated itinerary | Common baseline; not treated as a differentiator | Core selling point (Wanderlog, Mindtrip, Stippl) |
| Handling disruptions | Minimum-change repair — the smallest fix that preserves paid items & hard requirements | Full itinerary regeneration (TripMazer, Andante) |
| Group budgeting | Locked once paid; feeds directly into repair logic so paid items are never touched | Tracked separately from itinerary/replanning |
| Group fairness | Tracks who has already compromised across repairs so the same person isn't shortchanged repeatedly | Not addressed by researched competitors |
| Non-negotiables | Hard requirements enforced automatically during any repair, not just at planning time | Preferences collected once, not re-checked after changes |
| Post-trip output | Trips can be published and forked as templates by other groups | Not offered by researched competitors |

## 5. Technical Architecture & Feasibility

**Tech stack**

- Swift + SwiftUI for the interface; Combine / async-await for state management and networking.
- SwiftData (or Core Data) on-device for caching trip, group, and task state so parts of the app remain usable offline.
- Firebase (Firestore + Cloud Functions + Firebase Auth) as the backend, chosen over a custom server to minimize backend build time during the hackathon window.
- Firestore's real-time listeners to keep Circle, Tally, and Relay state in sync across every group member's device.

**APIs and external services**

- Apple MapKit (or the Google Places API) — destination candidate maps and the Basics layer (toilets, luggage storage, pharmacies, prayer rooms).
- A weather API (e.g., OpenWeatherMap) — to detect or simulate the disruptions that trigger rerouting.
- A currency-conversion API (e.g., exchangerate.host) — for Tally's per-person currency conversion.
- Stripe, in test mode — to track payment status/shares for Tally, without building full payment processing for the MVP.
- Firebase Cloud Messaging over APNs — push notifications for approvals, reminders, and reroute alerts.
- AVFoundation (native iOS framework) — in-app short-clip capture for Trail.

**Build plan & scope**

Once the build phase begins, development will be split across three weeks. The priority is to get the complete group planning → commitment → disruption → repair flow working first, then add supporting features and polish.

| Phase | Main Goal | What We Will Build | End-of-Week Result |
| :-- | :-- | :-- | :-- |
| Week 1 — Foundation & Group Planning | Build the shared trip foundation | Set up the SwiftUI project, Firebase Authentication and Firestore. Build create/join trip, group members, Circle preference form, budget input, hard requirements, destination/activity data, and the basic itinerary. Add a small seeded activity dataset for reliable testing. | Multiple users can join the same trip, submit their preferences and requirements, and see shared trip information update in real time. |
| Week 2 — Costs, Tasks & Reroute Core | Make the trip state usable by the repair system | Build Tally's trip-cost and per-person breakdown, basic currency conversion, and payment-status tracking. Add Relay's task board and assignment flow. Implement itinerary states such as flexible and locked, then build the first Reroute engine using manually triggered disruptions. Filter replacements against hard requirements, paid items, time, and budget before ranking the smallest-change option. | A user can trigger a disruption and Kelana can produce a valid repair without moving locked items or violating hard requirements. |
| Week 3 — Group Approval, Integration & Testing | Complete the end-to-end experience | Add affected-member approval, change summaries, the decision log, and real-time itinerary updates. Connect MapKit and weather data where stable. Add notifications if time permits. Implement a lightweight Trail recap only after the core flow is working. Test the complete flow on physical devices, fix failure states, prepare seeded demo scenarios, and create the final deployable build. | A complete demo: create trip → collect group requirements → plan → track cost → trigger disruption → review repair → approve → update the shared trip. |

By the end of the three-week build phase, Kelana must allow a group to create and join a trip, submit preferences and hard requirements, build a shared itinerary, view per-person costs, mark confirmed items as locked, trigger a disruption, receive a minimum-change repair, collect approval from affected members, and apply the change to the shared itinerary.

If development falls behind schedule, supporting features will be reduced before the core Reroute flow. Trail video capture, push notifications, automatic task reassignment, advanced map layers, and live disruption detection can be simplified or deferred. Circle's hard requirements, Tally's locked commitments, Reroute's minimum-change repair, and affected-member approval remain the core implementation priorities.

**What we plan to build during the building phase:**

- Circle — preference form, hard-requirement flagging, and destination voting with confidence cards.
- Tally — cost overview, per-person split, and payment-status tracking (not full payment processing), with basic currency conversion.
- Relay — a task board with automatic splitting; stale-task handoff can be simplified to a manual reassign button for the demo.
- Reroute — a manually triggered disruption flow that produces a minimum-change repair draft and routes approval only to affected members.
- Trail — basic clip capture tied to an activity, plus a simple end-of-trip recap.

**Explicitly out of scope for this phase:**

Full payment processing, email booking import, a full offline package, an emergency contact hub, safety-area scoring, solo pricing detection, a community travel feed, an advanced Trail/Setlog-style memory system, live (non-triggered) disruption detection, and a full booking marketplace.

Keeping the build narrowly focused on Circle, Tally, Relay, Reroute, and a basic Trail lets the demo prove the actual differentiator — constraint-aware, minimum-change repair — rather than spreading effort across a full travel super-app.
