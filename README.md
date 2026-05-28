# travel-web-app
# Vancouver Trip 2026 — Travel Web App

A luxury-style mobile-first travel planner web app designed for iPhone Home Screen usage (PWA-like experience).

This app was built as a lightweight offline-friendly trip companion for a Vancouver / Squamish wedding trip, with a strong focus on:

- fast mobile usage
- elegant UI
- Google Sheet live sync
- offline access
- iPhone Add to Home Screen experience
- easy editing without rebuilding the app

---

# Main Features

## Home Dashboard

The Home tab acts like a modern travel dashboard.

Features:

- immersive hero banner
- live Vancouver weather
- today's itinerary preview
- quick access cards
- trip countdown
- responsive iPhone-first layout

UI style:

- forest green + luxury beige palette
- soft gradients
- rounded glass-like navigation bar
- minimal luxury travel aesthetic
- inspired by boutique hotel / travel apps

---

## Itinerary Planner

Users can:

- view trip by date
- switch dates using calendar cards
- swipe left/right between tabs
- edit itinerary directly inside app
- store:
  - destination
  - activities
  - reservation details
  - notes
  - addresses
  - booking links
  - who's joining

The itinerary is divided into:

- Morning
- Afternoon
- Evening

Each section supports:

- Google Maps links
- copy address button
- booking links
- inline editing modal

---

## Hotel / Accommodation Management

Features:

- hotel booking overview
- check-in / check-out display
- nights calculation
- direct booking links
- copy address
- open in maps

Designed to behave like a hotel itinerary wallet.

---

## Expense Tracking

Expense system supports:

- shared trip expenses
- per-person split tracking
- CAD / HKD toggle
- category summaries
- filtering by participant
- hotel nights
- car rental tracking

Expense categories:

- Hotel
- Car Rental
- Meal
- Grocery
- Admission Tickets
- Others

Users can:

- add
- edit
- delete
- sync expenses directly to Google Sheets

---

## Emergency Contacts

Simple emergency contact management:

- emergency phone list
- tap-to-call
- add/edit/delete contacts
- synced with Google Sheets

---

# Google Sheet Integration

The app is powered by Google Sheets + Google Apps Script.

Architecture:

```text
Google Sheet
    ↓
Apps Script Web App API
    ↓
Travel Web App (HTML + Tailwind + JS)
```

The app reads and writes:

- itinerary
- accommodation
- expenses
- emergency contacts

without requiring:

- backend server
- database hosting
- Firebase
- authentication system

This makes the app:

- cheap
- portable
- easy to duplicate
- beginner friendly

---

# Offline Support

The app includes lightweight offline caching using:

```javascript
localStorage
```

Cached items:

- itinerary
- hotels
- expenses
- emergency contacts
- weather data

Benefits:

- usable during poor signal
- works while travelling
- Home Screen app feels more native

---

# PWA / iPhone Home Screen Support

The app supports:

- Add to Home Screen
- custom app icon
- custom app name
- standalone app mode
- fullscreen iPhone experience

Files added:

- manifest.json
- app-icon.png

Important meta tags:

```html
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-title" content="Vancouver Trip 2026">
<meta name="theme-color" content="#1A2E28">
```

---

# Important iPhone PWA Lessons Learned

## Safe Area / Bottom Spacer Issue

A major UI bug appeared after enabling:

```html
apple-mobile-web-app-capable
```

and adding:

```html
manifest.json
```

Symptoms:

- mysterious bottom gap
- floating navigation bar
- app appears pushed upward
- white / beige rectangle below app
- only happens after Add to Home Screen

Important discovery:

The problem was NOT mainly caused by the bottom spacer.

The real cause was:

- iOS standalone app mode
- safe-area handling
- Apple PWA meta tags
- status bar behavior

Most problematic tag:

```html
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
```

Fix:

```html
<meta name="apple-mobile-web-app-status-bar-style" content="default">
```

or removing that line entirely.

This changed how iOS calculates safe-area space.

Important lesson:

When debugging iPhone Home Screen apps:

DO NOT immediately blame spacer height.

Instead check:

- viewport-fit=cover
- safe-area-inset-bottom
- apple-mobile-web-app-capable
- apple-mobile-web-app-status-bar-style
- manifest.json behavior
- standalone app viewport handling

---

# UI / UX Design Decisions

## Navigation Bar

The floating rounded navigation bar was intentionally designed to feel:

- modern
- luxury
- lightweight
- app-like

Features:

- glassmorphism blur
- floating dock design
- swipe navigation support
- auto-scroll to top when switching tabs

---

## Swipe Navigation

Implemented:

- swipe left/right to switch tabs
- ignores swipes inside forms/buttons/modals
- optimized for iPhone usage

---

## Scroll Behavior

When changing tabs:

- app automatically resets to top
- smooth scroll animation removed
- instant navigation feels more native

---

# Tech Stack

## Frontend

- HTML
- TailwindCSS
- Vanilla JavaScript
- Font Awesome

## Backend

- Google Sheets
- Google Apps Script Web App

## Hosting

- GitHub Pages

---

# Why This Project Is Valuable

This project demonstrates:

- mobile-first web app design
- no-backend architecture
- Google Sheets as CMS/database
- offline-first thinking
- iPhone PWA optimization
- UI/UX iteration process
- safe-area debugging
- real-world travel workflow design

It also shows how AI-assisted development can rapidly prototype highly personalized apps.

---

# Future Ideas

Potential future upgrades:

- shared real-time collaboration
- photo gallery
- travel journal
- map visualization
- push notifications
- weather forecast timeline
- flight tracking
- AI itinerary assistant
- packing list module
- dark mode
- multi-trip support

---

# Notes For Future AI / Developers

This app intentionally avoids heavy frameworks.

The project philosophy is:

- simple
- editable
- portable
- human-readable
- beginner friendly
- AI-collaboration friendly

Most UI is generated dynamically using:

```javascript
renderHomeTab()
renderAllData()
renderItineraryTab()
```

Main state:

```javascript
appData
```

Main external dependency:

```javascript
Google Apps Script API
```

When modifying this app in the future:

Always test:

- Safari
- Add to Home Screen mode
- different iPhone sizes
- safe-area behavior
- bottom navigation overlap
- scrolling behavior
- offline caching

especially after changing:

- manifest.json
- viewport meta tags
- navigation positioning
- iOS safe-area CSS

---

# Project Goal

Create a beautiful, lightweight, offline-friendly travel companion app that feels close to a native iPhone app while remaining simple enough to maintain using only:

- HTML
- JavaScript
- Google Sheets
- GitHub Pages

without requiring a traditional backend.