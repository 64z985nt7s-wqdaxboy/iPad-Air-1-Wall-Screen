# Security Policy

Thank you for helping keep Home Display and its users safe.

## Supported versions

Home Display is a single web page (`index.html`). Only the **latest version on the `main` branch** gets security fixes. If you use a fork, sync it to get fixes (**Sync fork → Update branch** on GitHub).

| Version | Supported |
|---|---|
| Latest `main` | ✅ |
| Older copies and forks that haven't been synced | ❌ |

## Reporting a vulnerability

**Please don't report security problems in public issues, discussions or pull requests.**

Report privately instead:

1. Go to this repository's **Security** tab and click **Report a vulnerability**.
2. If that option isn't available, email **YOUR-EMAIL@example.com** with the subject `Home Display security`.

Please include:
- what the problem is and what someone could do with it
- steps to reproduce it, or a proof of concept
- the device, iOS or iPadOS version and browser you tested on
- whether you'd like to be credited, and how

### What to expect

- **Acknowledgement** within **7 days**.
- **An initial assessment** within **14 days**, saying whether the problem is confirmed and how serious it is.
- **A fix** as soon as practical, usually within **30 days** for confirmed issues. This is a small personal project maintained in spare time, so complex problems may take longer.
- **Credit** in the release notes once it's fixed, if you'd like it.

Please give a reasonable amount of time to fix a problem before sharing details publicly.

## Scope

### In scope
- Code in this repository, mainly `index.html`.
- Ways to run code or inject content into the page, for example through synced notes or reminders, radio station names, place names or the `#sync=` link.
- Ways to get around the Content Security Policy.
- Ways for another website or person to read data saved by the dashboard.
- Ways to get around the passcode **remotely**, without physical access to the device.
- Mistakes in the setup instructions that would expose users' personal data.

### Out of scope
- **Physical access to an unlocked device.** The passcode is a convenience lock, checked on the device itself. It keeps casual visitors out and isn't meant to stop someone who has the device and technical tools.
- Problems in outside services the page uses: Open-Meteo, OpenStreetMap, Radio Browser, Frankfurter and third-party radio streams. Please report those to the services themselves.
- Problems in Apple's software (Safari, Shortcuts, iOS or HomeKit), GitHub or GitHub Pages. Please report those to Apple or GitHub.
- What users' own shortcuts and scenes do once they run.
- Missing security headers that GitHub Pages doesn't let site owners set.
- Denial of service, spam or social engineering.

## How the dashboard handles data

- **No server, accounts or tracking.** The page is static and served by GitHub Pages.
- **Saved on the device only.** Settings, reminders, notes, places and radio stations are saved in the browser's local storage on the device. They're never sent to this repository or its maintainers.
- **Synced reminders and notes** reach the page after the `#` in its link. Browsers never send that part to the web server. The page removes it from the address bar after reading it. The text may still appear in Safari's history, so users are advised not to sync passwords or financial details.
- **Outside services** receive only what they need:
  - **Open-Meteo:** the location for weather and air quality, rounded to about 1 km by default.
  - **OpenStreetMap:** map image requests for the area around that location.
  - **Radio Browser:** station searches.
  - **Frankfurter:** which currencies to show rates for.
  - **Radio stations:** the streams the user chooses to play.
- **Content Security Policy:** the page may only connect to the services above, and outside services are only sent the site's address, not the full page link.
- **Passcode:** a 4-digit code, stored only as a salted hash on the device, with increasing lockouts after repeated wrong tries.

## Advice for people running their own copy

- Turn on **two-factor authentication** on your GitHub account, so nobody else can change the page your device loads.
- Use a **separate Apple ID** on the display iPad, and give it limited access to your Home.
- Don't add scenes that unlock doors, open garages or turn off alarms, or protect them with the passcode (🔒).
- Don't sync passwords, PINs or bank details.

The full details are in the **Security & privacy** section of the [README](README.md).
