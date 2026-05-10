# 🌤️ Skyline — Weather New Tab

A minimal Chrome/Brave extension that replaces your new tab page with a live weather dashboard and Google Calendar feed. Glass morphism UI, zero API keys, completely free.

![Chrome](https://img.shields.io/badge/Chrome-Extension-4285F4?logo=googlechrome&logoColor=white)
![Brave](https://img.shields.io/badge/Brave-Supported-FB542B?logo=brave&logoColor=white)
![Manifest](https://img.shields.io/badge/Manifest-V3-green)
![License](https://img.shields.io/badge/License-MIT-blue)

---

## Features

- **Live weather** — current temperature, feels like, humidity, wind speed
- **3-day forecast** — the next three days at a glance
- **Google Calendar** — today's events pulled from your iCal feed
- **Strong visual hierarchy** — massive clock on the left, bento-style weather tiles on the right
- **One-time setup** — location stored locally, no geolocation prompt on every tab open
- **Instant load** — reads from cache, refreshes silently in the background
- **°C / °F toggle** — set once in settings, remembered forever
- **Glass UI** — dark background, frosted glass cards, Inter font
- **No API key** — uses [Open-Meteo](https://open-meteo.com/), a free and open weather API
- **No tracking** — nothing leaves your device except weather and calendar API requests

---

## Screenshots

> Clock dominates the left. Weather bento stack on the right: current temp, details, 3-day forecast, today's calendar events.

---

## Installation

This extension is not on the Chrome Web Store. Install it in developer mode — this works permanently with no expiry.

**1. Clone or download this repo**

```bash
git clone https://github.com/yourusername/skyline-weather-newtab.git
```

Or download the ZIP and unzip it.

**2. Open your browser's extensions page**

- Chrome: `chrome://extensions`
- Brave: `brave://extensions`

**3. Enable Developer Mode**

Toggle **Developer mode** on in the top-right corner.

**4. Load the extension**

Click **Load unpacked** and select the `weather-extension` folder (the one containing `manifest.json`).

**5. Open a new tab**

The setup wizard will run once to ask for your location and preferred temperature unit. After that, every new tab loads instantly.

---

## First-time Setup

On first launch a two-step wizard runs:

1. **Location** — use your device's GPS or type a city name manually
2. **Units** — pick °C or °F

Your location (coordinates + city name) is stored in `chrome.storage.local` on your device only. It is never sent anywhere except the Open-Meteo weather API.

---

## Google Calendar Integration

Skyline uses your Google Calendar **secret iCal address** — no OAuth, no API keys, no Google Cloud setup required.

**How to connect:**

1. Go to [calendar.google.com](https://calendar.google.com) → **⚙ Settings**
2. Left sidebar → click your calendar name under **Settings for my calendars**
3. Scroll to the bottom → **Secret address in iCal format** → **Copy**
4. Open a new tab in Skyline → click **Connect →** on the calendar tile
5. Paste the URL → **Save**

**Notes:**
- Only timed events are shown (all-day events are filtered out)
- Google updates the iCal feed roughly every 15–20 minutes
- Current/in-progress events are highlighted in white
- Past events are dimmed
- Up to 5 events shown per day
- To disconnect: open **⚙ Settings** → Calendar section → **Disconnect**

**Google Workspace users:** If you don't see the secret iCal URL, your admin may have restricted external calendar sharing. An admin can enable it via Admin Console → Apps → Google Workspace → Calendar → Sharing settings → External sharing options → "Share all information".

---

## Settings

Click the **⚙** icon in the top-right corner of any new tab to:

- **Change location** — search for a new city
- **Switch units** — toggle between °C and °F
- **Disconnect calendar** — remove the iCal URL
- **Reset** — wipe all stored data and re-run setup

---

## File Structure

```
weather-extension/
├── manifest.json      # Extension config (Manifest V3)
├── newtab.html        # Main new tab page
├── weather.js         # Weather fetching, rendering, clock
├── calendar.js        # iCal fetching, parsing, rendering
├── setup.html         # First-run onboarding wizard
├── setup.js           # Setup logic
├── settings.html      # Settings page
├── settings.js        # Settings logic
├── shared.css         # Shared styles across all pages
└── icons/             # Extension icons (16px, 48px, 128px)
```

---

## APIs Used

| Service | Purpose | Cost |
|---|---|---|
| [Open-Meteo](https://open-meteo.com/) | Weather forecast | Free, no key required |
| [Open-Meteo Geocoding](https://open-meteo.com/en/docs/geocoding-api) | City name → coordinates | Free, no key required |
| [Nominatim](https://nominatim.org/) | Coordinates → city name (GPS mode only) | Free, no key required |
| Google Calendar iCal | Today's events | Free, no key required |

All are free for non-commercial use with no sign-up required.

---

## Developer Mode Note

Chrome and Brave will occasionally show a **"Developer mode extensions are enabled"** dismissal popup on browser restart. This is cosmetic and does not affect functionality. Running extensions in developer mode permanently is completely supported for personal use.

---

## Multi-device Note

Each browser install gets a unique extension ID. The iCal calendar integration works across all devices with the same setup — just paste your iCal URL on each machine. No per-device credentials needed.

---

## Tech Stack

- Vanilla HTML, CSS, JavaScript — no build step, no dependencies
- Chrome Extension Manifest V3
- `chrome.storage.local` for persistent preferences and caching
- `backdrop-filter` for glass morphism UI
- [Inter](https://rsms.me/inter/) via Google Fonts
- iCal parsing done client-side, no third-party libraries

---

## License

MIT — do whatever you want with it.
