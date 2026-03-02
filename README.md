# 🏔 AdZ Counter

A lightweight macOS menu bar app that automatically tracks your **Alpe du Zwift** completions — no Strava subscription required.

![macOS](https://img.shields.io/badge/macOS-13.0%2B-blue)
![Swift](https://img.shields.io/badge/Swift-5.0-orange)
![License](https://img.shields.io/badge/license-MIT-green)

---

## How It Works

AdZ Counter monitors your Zwift log file in real time. When Zwift records a finish line crossing on the Alpe du Zwift, the app detects it and increments your counters automatically. No API keys, no accounts, no internet connection needed.

A **10-minute cooldown** after each detected climb prevents the double-counting that occurs when Zwift logs a second finish line event as you loop around at the top.

---

## Features

- **Menu bar display** — shows total and current year count at a glance: `🏔 23 | 5`
- **Automatic detection** — tails the Zwift log file live during your ride
- **Yearly tracking** — year count resets automatically on January 1st
- **Right-click quick menu** — revert the last count without opening the full app
- **Manual count editing** — set your totals if you're starting from an existing count
- **Configurable log folder** — change the log path if your Zwift installation is non-standard
- **Climb notification** — macOS notification banner when a climb is detected
- **Smart cooldown** — 10-minute debounce prevents double-counting the loop at the top

---

## Requirements

- macOS 13.0 (Ventura) or later
- [Zwift](https://www.zwift.com) installed and producing log files

---

## Installation

1. Download the latest **AdZ Counter.app** from the [Releases](../../releases) page
2. Move it to your **Applications** folder
3. Launch it — the 🏔 icon will appear in your menu bar
4. Optionally add it to your **Login Items** so it starts automatically with your Mac:
   - System Settings → General → Login Items → add AdZ Counter

> **Gatekeeper warning:** Since the app is not notarised through the Mac App Store, macOS may show a warning on first launch. To open it: right-click the app → Open → Open.

---

## Setup

### Log File Folder

AdZ Counter looks for your Zwift log file at:

```
~/Documents/Zwift/Logs/Log.txt
```

This is the default location for a standard Zwift installation. If yours is different, click the 🏔 icon → **Settings** tab → configure the folder path and click **Apply & Restart Watcher**.

### Starting Order

You can launch AdZ Counter **before or after** Zwift — it polls every 5 seconds for the log file and automatically starts watching once Zwift creates it.

### Setting Your Existing Count

If you've already completed AdZ rides before installing, go to the **Settings** tab and enter your current totals under **Set Counts Manually**.

---

## Usage

| Action | Result |
|---|---|
| **Left-click** menu bar icon | Opens the full popover |
| **Right-click** menu bar icon | Quick menu with revert option |
| **Revert Last Count** | Subtracts 1 from both total and year count |
| **Settings tab** | Configure log folder, set counts manually |
| **About tab** | Version info and support link |

### The Menu Bar Display

```
🏔 23 | 5
    │    └─ This year
    └─────── All time total
```

---

## Building from Source

1. Clone the repository
2. Open `AdZCounter.xcodeproj` in Xcode 15 or later
3. Select your signing team under **Signing & Capabilities**
4. Press **⌘R** to build and run

No external dependencies or package manager required.

---

## FAQ

**Will it count climbs I did before installing?**
Not automatically — the app only detects new events written to the log after it starts watching. Use the manual count option in Settings to set your starting numbers.

**What if I do multiple AdZ climbs in one Zwift session?**
Each climb is counted separately. The 10-minute cooldown resets after each one, so back-to-back climbs (if you're brave enough) will all be recorded.

**The count went up by 2 for one climb — what happened?**
This was the original double-counting bug caused by Zwift logging two finish line events (once at the finish arch, once on the loop). The 10-minute cooldown in v1.0+ prevents this. If you're on an older version, use **Revert Last Count** and update the app.

**My log folder is different — where do I find it?**
Open Finder, press **⌘⇧G**, and paste `~/Documents/Zwift/Logs`. If that doesn't exist, search for `Log.txt` in your Zwift installation directory and point the app to that folder via Settings.

---

## Support

If you find AdZ Counter useful, consider buying me a coffee! ☕

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-booxdk-yellow?logo=buy-me-a-coffee)](https://buymeacoffee.com/booxdk)

For bugs or feature requests, please open an [issue](../../issues).

---

## License

MIT License — see [LICENSE](LICENSE) for details.
