# 🌤️ Skyline — Weather New Tab

A minimal Chrome extension that replaces your new tab page with a live weather dashboard. Glass morphism UI, zero API keys, completely free.

![Chrome](https://img.shields.io/badge/Chrome-Extension-4285F4?logo=googlechrome&logoColor=white)
![Manifest](https://img.shields.io/badge/Manifest-V3-green)
![License](https://img.shields.io/badge/License-MIT-blue)

---

## Features

- **Live weather** — current temperature, feels like, humidity, wind speed
- **3-day forecast** — the next three days at a glance
- **One-time setup** — location is stored locally, no geolocation prompt on every tab open
- **Instant load** — reads from cache, refreshes silently in the background
- **°C / °F toggle** — set once in settings, remembered forever
- **Glass UI** — dark background, frosted glass cards, Inter font
- **No API key** — uses [Open-Meteo](https://open-meteo.com/), a free and open weather API
- **No tracking** — nothing leaves your device except the weather API request

---

## Installation

This extension is not on the Chrome Web Store. Install it in developer mode — this works permanently with no expiry.

**1. Clone or download this repo**

```bash
git clone https://github.com/yourusername/skyline-weather-newtab.git
```

Or download the ZIP and unzip it.

**2. Open Chrome extensions**

Navigate to `chrome://extensions` in your browser.

**3. Enable Developer Mode**

Toggle **Developer mode** on in the top-right corner.

**4. Load the extension**

Click **Load unpacked** and select the `weather-extension` folder (the one containing `manifest.json`).

**5. Open a new tab**

The setup wizard will run once to ask for your location and preferred temperature unit. After that, every new tab loads instantly.

---

## First-time Setup

On first launch you'll see a two-step setup:

1. **Location** — choose to use your device's GPS, or type a city name manually
2. **Units** — pick °C or °F

Your location (coordinates + city name) is stored in `chrome.storage.local` on your device only. It is never sent anywhere except the Open-Meteo weather API to fetch your forecast.

---

## Settings

Click the **⚙** icon in the top-right corner of any new tab to:

- **Change location** — search for a new city
- **Switch units** — toggle between °C and °F
- **Reset** — wipe all stored data and re-run setup

---

## File Structure

```
weather-extension/
├── manifest.json      # Extension config (Manifest V3)
├── newtab.html        # Main new tab page
├── weather.js         # Weather fetching, rendering, clock
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

All three are free for non-commercial use with no sign-up required.

---

## Developer Mode Note

Chrome will occasionally show a **"Developer mode extensions are enabled"** dismissal popup on browser restart. This is cosmetic and does not affect functionality. Running extensions in developer mode permanently is completely supported for personal use.

---

## Tech Stack

- Vanilla HTML, CSS, JavaScript — no build step, no dependencies
- Chrome Extension Manifest V3
- `chrome.storage.local` for persistent preferences
- `backdrop-filter` for glass morphism UI
- [Inter](https://rsms.me/inter/) via Google Fonts

---

## License

MIT — do whatever you want with it.
