# Home Display

**Turn an old iPad into an iOS-style smart home display.** It shows a big clock, live weather, kitchen timers, reminders, notes, a map and a radio player, plus one-tap Home scenes, spread over two pages you swipe between. It's a single web page, so there's nothing to install from the App Store, and it's built to run on iPads as old as the **iPad Air 1 (iOS 12)**.

![Home Display, page 1](preview-landscape.png)

![Home Display, page 2](preview-page2.png)

---

## Features

- 🕙 **Lock-screen clock:** a big bold time and date, like the iOS lock screen.
- ⛅ **Live weather tile:** current conditions, the next 6 hours and a 6-day forecast with temperature bars, in iOS Weather style. It refreshes every 5 minutes, and whenever the screen wakes. Tap it to refresh straight away.
  - **Rain soon:** "Rain starting in about 30 min" from the short-term forecast.
  - **Air quality, UV, wind and humidity** at a glance.
  - **Warnings** for thunderstorms, heavy rain, strong winds, extreme heat and very poor air. These are worked out from the forecast, not official alerts.
  - **Animated sky:** rain, snow, drifting clouds, stars or sun glow behind the card. It can be turned off in Settings.
- ⏱ **Timers:** one-tap presets from 1 minute to 1 hour. You can pause, resume or cancel them, and an iOS-style alert chimes when one is done (with Repeat and Stop buttons).
- ✅ **Reminders:** a to-do list saved on the iPad. It can also show your open reminders from Apple's **Reminders** app (see below).
- 🗒 **Notes:** shows the notes you choose from Apple's **Notes** app, one at a time. Tap a note to read all of it.
- 🗺 **Maps:** a live map around your location with your saved places. Tap a place for directions in **Apple Maps** or **Google Maps**, or search from the tile.
- 🎵 **Music:** an internet radio player with an **AirPlay button** to choose the speaker (HomePod, Apple TV, Bluetooth or the iPad). It can also show ⏮ ⏯ ⏭ buttons for the Music app.
- 📱 **Two pages:** swipe left and right like the iPad Home Screen. Page 1 has the clock, weather, timers, reminders and scenes. Page 2 has Maps, Music and Notes.
- 🏠 **Scenes:** Home app–style tiles that run your shortcuts, for example to switch HomeKit lights and devices on or off.
- 🌙 **StandBy screensaver:** a giant clock appears after a few idle minutes and turns red at night.
- 🔅 **Night mode:** dims the screen during the hours you choose.
- 🎨 **5 wallpapers**, plus an iOS-style Settings sheet.
- Works in **landscape and portrait**.

No account, API key or server is needed. Weather comes free from [Open-Meteo](https://open-meteo.com/).

---

## What you need

- An iPad on **iOS 12 or later** (an iPad Air 1, iPad mini 2/3 or anything newer). Any other modern browser works too.
- Wi-Fi.
- A charger, so the iPad can stay on all the time.
- *Optional:* HomeKit devices set up in Apple's **Home** app, if you want the scene tiles.

---

## Setup: get your own copy (free, about 5 minutes)

You'll host your own copy for free on **GitHub Pages**. You only need a web browser.

### Option A: fork this repository (easiest)

1. Sign in to [github.com](https://github.com) (a free account is fine).
2. Click **Fork** at the top of this page, then **Create fork**.
3. In your fork, go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**. Choose branch **main** and folder **/ (root)**, then click **Save**.
5. Wait 1–2 minutes and refresh. Your link appears at the top of the Pages settings:
   ```
   https://YOUR-USERNAME.github.io/REPOSITORY-NAME/
   ```

### Option B: start a new repository

1. Download `index.html` from this repository: click the file, then the **Download raw file** button.
2. On GitHub, click **+ → New repository**, give it a short name (for example `home`), set it to **Public**, and click **Create repository**.
3. Click **uploading an existing file**, drag in `index.html`, and click **Commit changes**.
4. Turn on Pages as in steps 3–5 of Option A.

> **Is my data public?** No. The repository only holds the page's code. Your city, reminders and timers are saved on your iPad, never on GitHub.

---

## Set up the iPad

1. **Open your link** (`https://YOUR-USERNAME.github.io/...`) in **Safari**.
2. **Add it to the Home Screen:** tap the **Share** button (the square with an arrow), then **Add to Home Screen**, then **Add**. Always open it from this icon so it runs **full-screen**.
3. **Choose your city.** Settings opens the first time. Search for your city, tap it, then tap **Done**. You can also tap **Use Current Location**.
4. **Keep the screen on:** in the iPad's Settings app, go to **Display & Brightness → Auto-Lock → Never**, and leave the iPad plugged in.
5. **Turn the sound on:** tap the screen once after opening so the timer chime is allowed to play. Make sure the side switch isn't set to mute and the volume is up.

You can change settings any time with the **•••** button next to the clock.

---

## Scene tiles (controlling your Home)

Web pages can't talk to HomeKit directly, so each tile runs a shortcut from Apple's **Shortcuts** app instead.

1. Open **Shortcuts** on the iPad and tap **+** to make a new shortcut.
2. Add the **Home** action (for example *Set Living Room Lights Off*, or run a Home scene).
3. Give the shortcut a name, for example `Lights Off`.
4. In the dashboard, tap **••• → Scenes**. Put the tile's label on the left and the **exact shortcut name** on the right.

When you tap a tile, it lights up and the iPad briefly opens Shortcuts to run it. If you're using the full-screen Home Screen version, tap the **◀** back link in the top-left corner to come back. In plain Safari it returns on its own.

Tile icons are chosen from the name, so words like *morning*, *night*, *movie*, *lights*, *leaving* and *home* get matching icons.

> **Tip:** iOS's **Guided Access** (Settings → General → Accessibility) can lock the iPad to the dashboard, but it also stops scene tiles from opening Shortcuts. Use it only if you don't need scenes.

---

## Apple Reminders & Notes (optional)

A web page can't read Apple's apps directly, so a shortcut collects your reminders and notes and passes them to the dashboard. You build it once.

**Important:** syncing only works when the dashboard is open **in Safari**, not from the Home Screen icon. When Shortcuts opens a link it always uses Safari, and Safari keeps its data separate from the Home Screen version.

1. **Choose your notes:** in **Notes**, add `#home` to the first line of each note you want shown, for example `Wi-Fi password #home`. The tag is hidden on the dashboard.
2. **Turn it on:** in the dashboard, tap **••• → Reminders & Notes** and switch on **Sync from Apple Apps**.
3. **Build the shortcut:** tap **How to Set It Up** in that same section. It lists every step and shows the exact link for your copy. In short:
   - **Find Reminders** (Is Completed is false), then **Combine Text** (New Lines), then **Set Variable** `Rem`
   - **Find Notes** (Name contains `#home`), then **Repeat with Each** containing a **Text** of `@@NOTE`, a new line and the **Repeat Item**
   - after the repeat, **Combine Text** (New Lines), then **Set Variable** `Notes`
   - **Text** of `@@REMINDERS`, then `Rem`, then `Notes`, each on its own line
   - **URL Encode**
   - **Text** of `https://YOUR-USERNAME.github.io/REPOSITORY-NAME/#sync=` followed by the encoded text
   - **Open URLs**
4. **Sync:** tap ↻ on the Reminders or Notes tile. The iPad switches to Shortcuts for a moment, then comes back with your items.

Good to know:
- **It's a snapshot.** It updates each time you tap ↻, because iOS 12 can't run shortcuts on a schedule.
- **Ticking a synced reminder only hides it on the dashboard.** It stays open in the Reminders app.
- **Tip:** to show separate lists, change the first line of the Text step to `@@REMINDERS Groceries` and repeat the reminder steps for each list.

---

## Maps

Tap **••• → Maps** and:
- **Open In:** choose **Apple Maps** or **Google Maps**.
- **Directions:** choose Drive, Walk or Transit.
- **Places:** add a name and a full address for each, for example *Work* with *Hinjewadi Phase 1, Pune*.

The map is centred on your weather location. For your exact spot, use **Use Current Location** under Weather. Tapping a place opens directions from wherever you are. Live traffic times aren't shown, because they need a paid service.

---

## Music

- **Radio:** in **••• → Music**, search for a station (for example *Mirchi*, *Lofi* or *BBC*) and tap it to add it. You can also paste your own `https://` stream link. Tap the station buttons on the tile to switch.
- **Choose the speaker:** tap the **AirPlay** button at the top right of the Music tile to send the radio to a HomePod, Apple TV, AirPlay or Bluetooth speaker, or back to the iPad.
- **Music app buttons (optional):** turn on **Music App Buttons**, then make three shortcuts named `Music Previous`, `Music Play Pause` and `Music Next`. Each one needs a single action: Skip Back, Play/Pause or Skip Forward. The iPad switches to Shortcuts briefly on each tap.
- **Limits on iOS 12:** a web page can't show what the Music app is playing, and iOS 12 has no shortcut action for changing the Music app's speaker (that arrived in iOS 13). Use Control Center for that.

---

## Security & privacy

**Built in:**
- **Your data stays on the iPad.** Reminders, notes, places, stations and settings are saved in the iPad's browser. The GitHub repository only holds the code, so anyone else who opens your link sees an empty dashboard.
- **Synced data isn't sent to GitHub.** It travels after the `#` in the link, and browsers never send that part to the server.
- **Lock rules:** a Content Security Policy only lets the page connect to the services it uses: Open-Meteo, OpenStreetMap map tiles, the Radio Browser station directory and the radio streams you add. Other services are only sent your site's address, not the full page link.
- **Safe text:** everything typed or synced is shown as plain text, so it can't run code.

**Options in ••• → Passcode & Privacy:**
| Option | What it does |
|---|---|
| Passcode | A 4-digit code to open Settings, with an iOS-style keypad. After 5 wrong tries it locks for a while. "Forgot?" removes the code **and** erases synced notes and reminders. |
| Require for Notes | Asks for the passcode before showing synced notes. |
| 🔒 on a scene | Tap the lock next to a scene in **••• → Scenes** to require the passcode before it runs. |
| Hide Note Contents | Notes show as "Tap to show" and hide again after a minute. |
| Approximate Location | Rounds your location to about 1 km before it's sent to the weather and map services. On by default. |
| Keep Synced Items | Erases synced reminders and notes after 1, 7 or 30 days, or never. 7 days by default. |

> The passcode keeps visitors and children out. It's checked on the iPad itself, so it isn't bank-level security.

**Recommended:**
- **Use a separate Apple ID on the dashboard iPad,** so your photos, messages and iCloud data aren't on it. Invite that Apple ID into your Home from the Home app on your phone, and turn off **Allow Editing** and **Remote Access** for it. Alternatively, hide apps with **Screen Time → Content & Privacy Restrictions**.
- **Don't add scenes that unlock doors, open the garage or turn off alarms,** or protect them with 🔒.
- **Don't sync passwords, PINs or bank details.** Synced text passes through the sync link and may be saved in Safari's history.
- **Turn on two-factor authentication on your GitHub account,** so nobody else can change the page your iPad loads.

---

## Updating your copy

- **If you forked:** on your fork's main page, click **Sync fork → Update branch** to get the latest version.
- **If you uploaded the file yourself:** click **Add file → Upload files**, drag in the new `index.html` (it replaces the old one), and commit.

GitHub Pages updates within a minute or two. On the iPad, close the dashboard from the app switcher (double-click Home, then swipe it up) and open it again.

---

## Settings

| Setting | What it does |
|---|---|
| Location | The city used for weather. Search by name, or use the iPad's location. |
| Temperature | °C or °F |
| Animated Weather | Turns the moving sky behind the weather card on or off. |
| 24-Hour Time | Switches the clock format. |
| StandBy After | How long the screen sits untouched before the big StandBy clock appears (Off, 2, 5 or 15 minutes). Tapping the clock also opens it. |
| Dim at Night / From / To | Dims the screen and turns StandBy red during these hours. |
| Scenes | Add, rename or remove scene tiles (up to 8). |
| Reminders & Notes | Turn syncing on, set the shortcut's name, sync now, see the setup guide, or clear synced items. |
| Maps | Apple Maps or Google Maps, travel mode, and your places. |
| Music | Find and remove radio stations, add a stream link, and turn on the Music app buttons. |
| Passcode & Privacy | Passcode, notes protection, hiding notes, approximate location, and how long synced items are kept. |
| Wallpaper | Dusk, Ocean, Meadow, Rose or Graphite. |

---

## Troubleshooting

**The weather says "Unavailable", or shows ⚠︎ next to "Updated".**
Check the Wi-Fi. It retries on its own and shows the last forecast it got in the meantime. You can tap the weather card to try again.

**"Use Current Location" doesn't work.**
Location only works on an `https://` link, which GitHub Pages provides. Check that **Settings → Privacy → Location Services → Safari Websites** is turned on, or just search for your city instead.

**The timer didn't make a sound.**
Tap the screen once after opening the dashboard (iOS only allows sound after a tap), check the mute switch and volume, and keep the dashboard open on screen. Timers keep counting while it's closed, but they can only ring while it's open.

**A scene tile says the shortcut can't be found.**
The name in **••• → Scenes** has to match the shortcut's name in the Shortcuts app exactly, including capital letters and spaces.

**My changes didn't show up after updating.**
Wait a couple of minutes for GitHub Pages, then close the dashboard from the app switcher and reopen it.

**Synced reminders or notes don't appear.**
Make sure the dashboard is open in Safari rather than from the Home Screen icon, that the shortcut's name matches **••• → Reminders & Notes → Shortcut Name**, and that the link in the shortcut's last Text step is exactly your dashboard's link followed by `#sync=`.

**A radio station won't play.**
Some stations' streams are offline or in formats Safari can't play. Try another one. Only stations with secure `https://` streams can play.

**Everything reset.**
Your settings and lists are stored in the browser. Clearing Safari's website data, or removing and re-adding the Home Screen icon, can erase them.

---

## How it works

- It's a single file (`index.html`) of plain HTML, CSS and JavaScript, with no frameworks and no build step.
- It's written for **Safari 12** and avoids newer JavaScript and CSS features, so it also runs on old iPads.
- The see-through "glass" panels are translucent colours rather than live blur, which keeps it smooth on older hardware.
- Weather, air quality and city search use the free [Open-Meteo](https://open-meteo.com/) APIs. Air quality is shown on the US AQI scale. Nothing else is sent anywhere, and there's no tracking.

## Credits

Weather data by [Open-Meteo.com](https://open-meteo.com/), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Map data © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors. Radio station directory by [Radio Browser](https://www.radio-browser.info/).

Inspired by Apple's iOS design. This project is not affiliated with or endorsed by Apple. iPad, iOS, HomeKit and Shortcuts are trademarks of Apple Inc.
