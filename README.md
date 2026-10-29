# Flip Launcher — a KaiOS-style Android launcher

A KaiOS-style Android launcher built for feature-phone-shaped devices (small,
low-resolution, D-pad/soft-key driven screens like the TCL Flip 2 / Flip Go)
rather than touch-first flagships. Navigation leans on the physical soft keys
and D-pad: number keys 1-9 double as shortcuts everywhere they make sense, and
every screen mirrors the three-soft-key layout (left / center / right) KaiOS
users already know.

![Home Screen](reference/home.png)

## What's different in this fork

This is a fork of
[ambercaravalho/flip-launcher](https://github.com/ambercaravalho/flip-launcher),
tuned for daily use on a TCL Flip 2. It adds four changes on top of the
upstream launcher; everything else works as described in the rest of this
README.

### Rename apps

Give any app a custom name in the App Drawer. The new name is used everywhere
the launcher shows the app: the drawer (sorted by the new name), the Home
shortcut rail, soft-key assignments and the Hide / Show Apps list.

- **Rename:** open All Apps, highlight an app, press **Options** (right soft
  key) and choose **Rename**. Type the name on the keypad, then press Down and
  choose **Save** (or press the keyboard's Done key). Saving an empty name
  restores the app's own label.
- **Reset:** **Options → Reset Name** appears once an app has a custom name.
- Custom names are removed automatically when the app is uninstalled.

### Uncluttered Home screen

- No AM/PM line above the clock (the status bar still shows it; turn on
  24-hour time in system settings for an unambiguous clock).
- No dashed **+** tile on the shortcut rail. Add shortcuts from the App
  Drawer (**Options → Add to Home Shortcuts**) or **Settings → Home Screen &
  Keys → Customize Home Shortcuts**.
- No apps icon above the center soft key. The center key still opens All Apps,
  and a long-press still opens Settings.

### D-pad shortcuts on Home

Each D-pad direction (Up, Down, Left, Right) can open an app, or a specific
screen inside an app, when pressed on Home. This replaces the stock home
screen's "Key shortcuts", which stop working once another launcher is the
default Home app.

- Set them in **Settings → Home Screen & Keys → D-pad Shortcuts**.
- **Choose App** opens the app picker; its **Activities** soft key lets you
  target a specific screen inside an app.
- Assigning Left replaces Left's default job of jumping to the shortcut rail.

### Recent apps (TCL Flip 2)

On phones with TCL's recents screen, each D-pad shortcut also offers
**Recent Apps**, which opens the phone's own Recent apps list. Assigning it to
**Down** matches the stock TCL setup.

## Features

### Home screen

- A vertical rail of up to 9 shortcut icons on the left (mapped to number keys
  1-9, top to bottom). The disc size adapts to the screen so all five visible
  slots fit without clipping, even on a 240x320 display.
- A large clock and date on the right.
- Bottom soft keys: **Notices** (left), **All Apps** (center — press to open;
  long-press for **Settings**), and a configurable right key (Contacts by
  default).
- A notification summary (missed calls / messages / other) under the clock,
  each independently toggleable.
- Typing a digit anywhere on Home jumps straight into the dialer, prefilled.
- Long-pressing Back launches a configurable app.

### App Drawer ("All Apps")

- Every installed, non-hidden app, in **grid** or **list** view (toggle in
  **Settings → Apps & Drawer**):
  - **Grid**: a 3x3 icon page at a time, tracked by a column of dots on the
    right. Number keys 1-9 launch the matching icon on the current page.
  - **List**: one continuous scroll, icon + label per row — no pages, no dots,
    just normal scrolling.
- Long-press (or the Options soft key) on any app to:
  - Add it to Home shortcuts
  - Hide it from the drawer
  - Change its icon (from an installed icon pack or the launcher's own bundled
    icon set)
  - Reset a per-app icon override
  - Uninstall it

![App Drawer Grid](reference/apps.png)
![App Drawer List](reference/list.png)

### Notices

A custom notification list standing in for the system shade, which isn't
designed for a screen this small. Shows icon, title, body text and a relative
timestamp ("2 minutes ago", "8:30 AM", …) per notification.

- **Dismiss** (left soft key) — dismiss the focused notice
- **Select** (center) — open the notice's action, then dismiss it
- **Dismiss All** (right) — clear every active notification

Requires Notification Access, granted from **Settings → Notifications**.

![Notices](reference/notices.png)

### Settings

Everything lives in one **Settings** hub, so there's a single, followable place
for customization. Open it by long-pressing the center soft key on Home; it's
also listed in the app drawer like a normal app. Settings are grouped into
categories you drill into:

- **Appearance**
  - **Set Wallpaper** — pick from bundled wallpapers or the system chooser
  - **Accent Color** — cyan (default), red, orange, yellow, green, blue,
    indigo, violet — applied to focus highlights, page dots, toggles, and other
    accents throughout the launcher
  - **Icon Shape** — squircle, square, rounded square, circle, or none;
    adaptive icons are masked into the shape, legacy icons get an optional
    tinted background disc
  - **Icon Pack** — apply any installed icon pack (Nova/ADW/Apex-compatible)
    launcher-wide
  - **App Icon Size** — small / medium / large
  - **Background for Plain Icons** — toggle the synthesized tint disc for
    non-adaptive icons
  - **Animations** (Motion) — fast, lightweight transitions are on by default;
    turn them off to make navigation instant on the slowest hardware
- **Notifications**
  - **Notification Access** — grants/checks the permission that powers Notices
    and the Home badges
  - **Show Missed Calls / Messages / Other Notifications** — independent
    toggles for the Home badge summary
  - **Notification Dots on Icons** — small dot over app icons with pending
    notifications
- **Home Screen & Keys**
  - **Home Left Key / Home Right Key** — assign an app to either soft key, or
    leave them as Notices / Contacts
  - **Back Button (Long-Press)** — assign an app to launch on long-press Back
  - **Customize Home Shortcuts** — see below
- **Apps & Drawer**
  - **App Drawer View** — Grid or List
  - **Hide / Show Apps** — see below
- **System**
  - **Set as Default Launcher**
  - **System Settings**

Rows are designed to read clearly on a small screen: section headers group
related settings, On/Off toggles show a switch-style pill, and rows that open
another screen or chooser show a chevron.

#### Home Shortcuts

Customize the ordered list of up to 9 Home rail shortcuts. Pick a shortcut row
(or its number key) to reassign it, including pinning a specific *activity*
inside an app rather than just its main entry point. The trailing "Add
shortcut" row appends a new one; the Clear soft key removes the focused
shortcut.

#### Hide / Show Apps

Lists every installed app with a "Hidden" badge; Center/OK toggles whether the
focused app is hidden from Home and the App Drawer.

#### Icon packs & built-in icons

- Apply any installed icon-pack app launcher-wide from **Settings → Appearance
  → Icon Pack**.
- Override a single app's icon independently of the active pack, choosing from
  that pack's full icon set or from the launcher's own bundled icon collection
  — so there's always something to pick from even with no icon pack installed.

## Built for small, non-touch screens

- Tuned for QVGA (~240x320) portrait displays driven by a D-pad, soft keys, and
  a number pad — no touch required.
- A shared design-token system (typography, spacing, corner radii) keeps every
  screen consistent and easy to retune.
- Focus highlights follow the chosen accent color, and animations are kept
  short and cheap (alpha/scale only) so they stay smooth on weak chipsets — and
  can be turned off entirely.

## Requirements

- Android 5.0 (API 21) or newer on the device.
- An Android SDK with `platforms;android-36` and `build-tools;36.0.0` (point
  the build at it via `local.properties` or `ANDROID_HOME`).
- A JDK is **not** something you need to install or configure — the Gradle
  toolchain auto-provisions JDK 17 for the build. Gradle itself runs on any
  JDK 17-26.

See [CONTRIBUTING.md](CONTRIBUTING.md) for a from-scratch environment setup.

## Building

```bash
./gradlew :app:assembleDebug
```

The debug APK lands in `app/build/outputs/apk/debug/`.

## Installing

```bash
adb install -r app/build/outputs/apk/debug/app-debug.apk
```

Then set Flip Launcher as your default Home app (**Settings → System → Set as
Default Launcher**), and grant Notification Access from **Settings →
Notifications** if you want the Notices screen and Home notification badges to
work.

## Permissions

- `BIND_NOTIFICATION_LISTENER_SERVICE` (via Notification Access, granted by the
  user in system settings) — powers Notices and the Home badge summary.
- `SET_WALLPAPER` — used by the bundled wallpaper picker.

No runtime permissions are requested at launch. App enumeration uses a
`<queries>` declaration rather than `QUERY_ALL_PACKAGES`.
