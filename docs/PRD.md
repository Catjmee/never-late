# Never Late – Product Requirements Document

28 October 2026 · Catherine

> Exported from the living PRD doc. The doc is the working copy; this file is a snapshot.

## Overview

Never Late is an iPhone app that plans every step between now and an event's start time, then guides you through each step with alarms, spoken prompts and reassuring progress updates. The aim is to arrive on time and settled, not just on time at the front door.

**Problem.** Today the plan is worked backwards from the arrival time across scattered tools: phone alarms, Google Maps and mental arithmetic. Steps get grouped into one big block, so small transitions go unplanned. Those include getting home first, actually leaving the house, finding parking, reaching the right room and unpacking. The result is starting late, rushing and arriving flustered.

**Goals**

1. Be at your seat, settled, 5 minutes before the event start on at least 90% of planned events, accepting that a small share of lateness is unavoidable.
2. Replace the patchwork of alarms and mental maths with one plan per event, built from reusable presets.
3. Reduce stress by making every step, including the small ones, visible and timed.
4. Learn from each trip so plans get more accurate over time.

**Non-goals for the first version:** turn-by-turn navigation (Google Maps stays the navigator), Android or web apps, and shared or family plans (each person plans their own day).

## User and journey

The first user is Catherine: an iPhone user who works mostly in Chester, attends occasional workshops elsewhere (for example Manchester), and has a dog who sometimes goes to daycare further from home. Events come from Outlook and Teams, plus plans made by text message.

The app is built for anyone whose route out of the door has many small steps, not only Catherine's routine. That includes parents getting children ready or doing a school drop-off, pet owners, carers with caring duties, and people who iron or prepare clothes on the day. Onboarding (below) lets each user build their own routine from categorised stages.

Every trip runs through eight stages. Most lost time sits in the transitions between them, not in the journey itself.

| Stage | What happens | Where time goes missing | How the app helps |
| --- | --- | --- | --- |
| 1. Back home | Return from an earlier outing, such as a dog walk | No time allowed to get home, dry and feed the dog, take off a coat | Adds a "get home first" step when you're out before an event |
| 2. Pre-getting ready | Free time before starting | Feels like plenty of time; food, drinks and phone distraction push the start back | A heads-up before the get-ready step and an alarm to start |
| 3. Getting ready | Shower, make-up, hair, dressing | Takes 45 to 60 minutes and varies with hair washing or the type of event | Presets with a min to max range and optional add-on steps |
| 4. Leaving the house | Lock up, switch off devices, dog treat and radio, bag, coat, keys and phone | No time allowed for actually leaving; worry about locks and devices | A leaving checklist with a saved record, plus night-before prep |
| 5. Travel | Drive, Uber or public transport to parking, drop-off or station | Uber arrives later than quoted; car parks are full, hard to find or need paying | Live traffic, an Uber buffer, saved parking notes per venue |
| 6. Transport to venue | Walk from the car park or station to the entrance | Unsure of the way; Maps is only opened once lost | A timed walking step plus Live Activity updates |
| 7. Into the building | Floor, room, check-in, cloakroom, bathroom, finding people or a desk | Planning stops at the building door | Venue notes and a "to your seat" step |
| 8. Event start | Unpack the bag and laptop, sit, settle | Arriving flustered; spare time when early feels wasted | Settle-in time, plus short filler tasks when early |

## Functional requirements

MVP items make up the first release. Phase 2 items build on it once the core loop of plan, prompt and learn works.

### Onboarding

New users build their routine by picking the stages that apply to them from a categorised list. The picks become their starting presets.

| Category | Example stages |
| --- | --- |
| Wardrobe | Choose outfit, iron clothes, get dressed, shoes and coat |
| Self care | Shower, wash and dry hair, make-up, shave, skincare, medication, breakfast |
| Dependents | Get kids ready, pack school bags, school or nursery drop-off, walk or feed pet, pet daycare drop-off, caring duties |
| Home and leaving | Lock up, switch off devices, pack bag, find keys and phone |
| Travel | Drive, taxi or Uber, train, bus, walk, cycle, parking |
| Arrival | Walk to entrance, check-in or security, find floor and room, cloakroom, unpack and settle |

| ID | Requirement | Priority |
| --- | --- | --- |
| O1 | Onboarding stage picker: choose stages by category, each with a suggested default time you can change | MVP |
| O2 | Add custom stages and rename any stage | MVP |
| O3 | Turn picks into starter presets (for example "Workday" and "Evening out"), editable later | MVP |
| O4 | Mark stages as optional or safety-critical (never auto-ticked, never trimmed) | MVP |
| O5 | Revisit the picker from settings at any time | MVP |
| O6 | Onboarding is skippable, fully accessible, and asks for permissions (location, notifications, calendar) only when first needed, with a plain reason | MVP |

### Event capture and planning

| ID | Requirement | Priority |
| --- | --- | --- |
| P1 | Import events from the Outlook calendar, including Teams meetings, and let you choose which to plan | MVP |
| P2 | Quick add: paste a text message, and the app pulls out the time and place for you to confirm | MVP |
| P3 | Evening-before or morning nudge: "You have 2 events tomorrow. Want to plan them?" | MVP |
| P4 | Work backwards from the start time (or a hard deadline such as daycare closing) through every step, and show the time to start each one | MVP |
| P5 | Plan against the maximum preset time, and show any slack | MVP |
| P6 | Multi-stop trips, for example work to dog daycare to home | MVP |
| P7 | Return trips: a "leave work by" plan that includes packing up the laptop and walking to the car | MVP |
| P8 | Add a "get home first" step automatically when you're out before an event | Phase 2 |
| P9 | Multi-leg travel grouped under one Travel stage, for example taxi to the station, then train to the location. Each leg is calculated through Google Maps (driving, taxi, transit, walking), including transfer time between legs such as walking to the platform. The leg view expands from the Travel stage | MVP |
| P10 | "I need more time" button (+5, +10, +15 min or custom), also from the Live Activity and by voice. The app recalibrates: it wins time back from later steps' slack (the gap between min and max), then from steps marked optional, never from travel or fixed steps, and shows what it trimmed. If the time can't be made up, it shows the new expected arrival time and how late that is, and offers to draft a "running late" message to send | MVP |
| P11 | Calendar view of upcoming events (day and week), combining imported and quick-added events. Each event shows whether it has a Never Late plan, with an icon and wording as well as colour. Open an event to add a plan from a preset, edit its steps and see the start-getting-ready and leave times, so a busy week can be planned ahead. Plans update automatically if the event time or place changes, with a heads-up | MVP |

### Presets and steps

| ID | Requirement | Priority |
| --- | --- | --- |
| S1 | Named presets, such as "Workday in Chester" or "Workshop in Manchester", each with a default step list and a min to max time for getting ready | MVP |
| S2 | Add, remove and reorder steps per event ahead of time, with buttons as well as drag | MVP |
| S3 | Optional add-on steps with their own time, such as "wash hair +15 min" or "walk dog first" | MVP |
| S4 | Built-in last-mile steps: parking, walk to entrance, check-in, find the room, cloakroom, unpack and settle | MVP |

### Places and venues

| ID | Requirement | Priority |
| --- | --- | --- |
| V1 | Saved places (home, office, dog daycare) with notes on parking, payment, entrance, floor and check-in | MVP |
| V2 | New-venue flow that asks the last-mile questions when planning somewhere new | MVP |
| V3 | Remember last-mile timings per venue and reuse them next time | MVP |

### Prompts and alerts

| ID | Requirement | Priority |
| --- | --- | --- |
| A1 | Choose per step: full alarm that sounds on silent, or a standard notification | MVP |
| A2 | Heads-up before each step, such as "5 min until you start getting ready" | MVP |
| A3 | Spoken prompts through the phone, AirPods or CarPlay for when you're driving or packing up | MVP |
| A4 | Live Activity on the lock screen and Dynamic Island during travel, such as "Car park in 5 min, then 4 min walk, 8 min to settle, on track" | MVP |
| A5 | Reassuring status at key points: say when you're on track, not only when you're behind | MVP |
| A6 | Time-of-day and live traffic from Google Maps: when planning ahead, use predicted travel times for the actual departure time and day; from about 2 hours before leaving and throughout the trip, refresh in real time, re-time every later step (including earlier start-getting-ready alarms if needed), and warn early when the leave time moves forward | MVP |
| A7 | Uber buffer: add a set margin to quoted pickup times | MVP |
| A8 | WhatsApp reminders through a dedicated channel | Phase 2 |
| A9 | Alexa announcements on an Echo at home through an Alexa skill | Phase 2 |
| A10 | Prompt level, like Google Maps: Muted (visual only, no sound or speech), Minimal (essential stages only, such as start getting ready, leave now and park), or Full (all prompts, including heads-ups like "you've got 10 mins until you leave"). Set a default, with an override per event or per trip. Switch level at any point mid-journey in one tap from the Live Activity, lock screen or app, or hands-free by voice through Siri while driving; the change applies from the next prompt | MVP |
| A11 | Calm running-late messaging: give the new expected arrival time, remind you not to panic, and frame it as a lesson to improve next time. Never blaming. The after-event check-in lets you mark lateness as unavoidable, and a small share of unavoidable late arrivals is expected and not counted against you | MVP |
| A12 | Alarm screen: a large, steady coloured block filling the screen with the step name, time and an icon, plus big Done and Snooze buttons. No flashing or strobing. Every status (on track, tight, running late) shows an icon and wording as well as colour | MVP |

### Leaving the house

| ID | Requirement | Priority |
| --- | --- | --- |
| L1 | Leaving checklist to tick off: doors locked, devices off, dog treat, radio on, bag, coat, keys, phone | MVP |
| L2 | Save a timestamped record of the ticked checklist to look back at if you're worried later | MVP |
| L3 | Evening-before pre-plan: a short list of things you can do now, such as pack your bag, check the location, floor and room number, decide on clothes and items needed, put coat and keys by the door, and set out the dog treat | MVP |

### Arriving early

| ID | Requirement | Priority |
| --- | --- | --- |
| E1 | Plans target being at your seat 5 minutes before the start. That buffer (plus any extra early time) offers swipeable cards to cycle through and pick one: take in your surroundings, set an intention for the event, or a short reminder such as "try your best" or "listen more than talk". Cards are editable, and a short meditation or messages catch-up fits longer gaps | MVP |

### Learning and review

| ID | Requirement | Priority |
| --- | --- | --- |
| R1 | Time each step through quick taps ("started getting ready", "left the house") and location for arrival | MVP |
| R2 | After-event check-in: early, on time or late; if late, tap the step that went wrong | MVP |
| R3 | Suggest adjustments rather than changing plans silently, for example "Add 10 min for parking at this venue?" | MVP |
| R4 | Spot patterns across trips, for example "Leaving the house ran over in 4 of your last 6 trips", and offer more time or earlier prep | Phase 2 |
| R5 | Trouble-spots view showing the steps most often underestimated | Phase 2 |
| R6 | Auto-complete steps from phone location: leaving the home geofence ticks "Leave house"; arriving at the car park, station or drop-off ticks the travel step; nearing the venue ticks "Walk to entrance". Each auto-tick records the real time for learning and can be undone in one tap. Safety items on the leaving checklist (doors locked, devices off) are never auto-ticked; if they're still unticked when you leave, a prompt asks "Did you lock up?" | MVP |

## Accessibility and non-functional requirements

The app must meet **WCAG 2.2 level AA** in every release. The points below matter most for this app.

### Accessibility (WCAG 2.2 AA)

- Full VoiceOver support. Every control, step and status has a meaningful label.
- Dynamic Type support up to the largest accessibility sizes, with no clipped text.
- Text contrast of at least 4.5:1 for body text and 3:1 for large text and key UI parts.
- Tap targets of at least 24 × 24 px (2.5.8), with Apple's 44 × 44 pt as the design target.
- Colour never carries meaning alone. "Running late" also uses wording and an icon.
- Every alarm has sound, vibration and visual forms.
- Timings you can adjust: snooze length, heads-up lead time and alarm timeouts (2.2.1).
- No drag-only interactions. Reordering steps also has up and down buttons (2.5.7).
- Focus is never hidden behind sticky headers or the keyboard (2.4.11).
- Consistent help and no redundant entry. Venue and preset details are remembered, not re-asked (3.2.6, 3.3.7).
- No flashing content: nothing flashes more than three times a second (2.3.1), and alarms use a steady colour block. Respect Reduce Motion, and keep wording calm, short and plain.

### Reliability and platform

- iPhone only for Phase 1, on the current and previous major iOS versions.
- Alarms fire on time even when the app is closed, the phone is on silent, or a Focus mode is on.
- Plans and alarms keep working offline. Traffic updates resume when signal returns.
- Battery-friendly location: precise tracking only during an active trip.

### Privacy

- Location and step timings stay on the device by default. Any sync is opt-in.
- Calendar access is read-only, and only the events you choose are stored.
- Clear controls to delete trip history and venue notes.

## Integrations, phasing and success measures

Phase 1 is an iPhone app that covers the full plan, prompt and learn loop. Extra channels and devices follow.

### Integrations

| Integration | Purpose | Phase |
| --- | --- | --- |
| Outlook calendar (Microsoft Graph) | Read events, including Teams meetings | 1 |
| Google Maps Platform (Routes API) | Live travel times for every leg (driving, transit, walking) and leave-time updates | 1 |
| Google Maps (hand-off) | Turn-by-turn directions; Never Late keeps the timeline around it | 1 |
| iOS alarms (AlarmKit), Live Activities, Siri and CarPlay announcements | Alarms on silent, lock-screen progress, spoken prompts | 1 |
| Uber | Read the booking's pickup time to apply the buffer automatically; manual entry until then | 2 |
| WhatsApp Business Platform | Reminder messages in a dedicated chat; small per-message costs and business setup | 2 |
| Alexa skill | Spoken reminders on an Echo at home | 2 |
| Apple Watch app | Step taps and haptic prompts on the wrist | 3 |

### Phases

| Phase | Scope |
| --- | --- |
| 1. iPhone MVP | Onboarding stage picker, calendar view with plan-ahead, Outlook import, quick add, presets with min to max ranges, step planning back from start or deadline, multi-stop and return trips, venue notes, alarms, heads-ups, spoken prompts, Live Activity, live traffic, Uber buffer, leaving checklist, step timing, after-event check-in, seat-buffer intention cards, calm running-late messaging, evening-before pre-plan, location auto-ticks, "I need more time", WCAG 2.2 AA |
| 2. Smarter and more channels | Pattern spotting and trouble-spots view, "get home first" detection, WhatsApp, Alexa, Uber link |
| 3. Wrist | Apple Watch app with step taps, haptic heads-ups and a glanceable trip status |

### Success measures

- At your seat 5 minutes before the start: at least 90% of planned events, from the after-event check-in. Lateness marked unavoidable is tracked separately.
- Average lateness on late events falls month by month.
- Planned versus actual step times converge, with per-step error under 5 minutes after 10 trips.
- Self-rated stress on arrival (1 to 5 in the check-in) trends down.
- At least 80% of calendar events with a location get planned in the app.

## Risks and mitigations

The biggest risk is that prompts become noise and get ignored. The second is that setup takes more effort than the time it saves.

| Risk | Why it matters | Mitigation |
| --- | --- | --- |
| Alert fatigue | An alarm for every step can be dismissed on autopilot, recreating today's problem | Muted, Minimal and Full prompt levels (A10), alert level per step, heads-ups instead of more alarms, and calm wording that changes with urgency |
| Setup burden | Building presets and venue notes takes effort before any payoff | Good starter presets, a fast quick add, and venues learnt from use rather than typed upfront |
| Inaccurate estimates early on | Plans start from guesses, so early trips may still run late | Plan against the maximum time, clearly mark early estimates, and let learning tighten them |
| Timing data needs taps | Learning depends on tapping "started" or "left", which is easy to forget when rushing | Use location and motion where possible, accept late taps, and keep the check-in to one tap |
| iOS limits | Apps can't draw over Google Maps, and background location and alarms have rules | Live Activities and spoken prompts instead of an overlay; AlarmKit for alarms |
| Distraction while driving | Prompts must never need a glance or a tap at the wheel | Driving mode: spoken prompts only, through CarPlay or Siri announcements |
| Third-party dependencies | WhatsApp, Uber and Alexa have costs, approvals and changing terms | Keep them in Phase 2, with the core app fully working without them |
| Calendar gaps | Plans made by text never reach a calendar | Quick add plus the evening-before nudge |
| Privacy | Location history and routines are sensitive | On-device by default, opt-in sync, and easy deletion |
| Over-correction | Learning from one bad day can add too much buffer | Suggest changes for approval and base them on several trips, not one |
| Accessibility slips | New features can break WCAG 2.2 AA | Accessibility checks in every release, including VoiceOver testing |

## Assumptions and open questions

These defaults are in the PRD until you say otherwise.

- Google Maps stays the navigator, and Never Late hands off to it while tracking the timeline.
- Step timing combines quick taps with location for arrival.
- The app is for any individual user in Phase 1, each planning their own routine, with no shared or family plans.

- [ ] Is the dog daycare's pickup or closing time a hard deadline on those days?
- [ ] Which public transport is used, if any, and should live departures be in Phase 1?
- [ ] Should WhatsApp come before Alexa in Phase 2, or the other way round?
- [ ] Is a built-in meditation wanted, or a link to an existing app?
