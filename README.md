# Planner for Windows

A simple, private planner for school, as a Windows PC app. It's the PC version of [Planner-app](https://github.com/GreenBud4623/Planner-app) (Android).

- **Your data stays on your PC.** No account, no server, no tracking. Tasks are saved in your Windows user profile and never sent anywhere.
- **Works offline.** It doesn't need internet at all.

## Install

1. Open the newest release on the **Releases** page and download `Planner-Setup.exe`.
2. Run it. If Windows shows **"Windows protected your PC"**, click **More info → Run anyway**. It only warns because the app isn't signed with a paid certificate.
3. Planner installs for your user only (no admin needed) and adds a Start menu and desktop shortcut.

Don't want to install? Download `Planner-Portable.exe` and just run it.

New versions install over the old one and keep your tasks.

## Features

Four tabs: **Planner** (your day: classes, then tasks), **Timetable** (weekly classes), **Homework** (past due, to recover, homework, long-term) and **Tests** (upcoming tests with countdowns, past tests with grades).

On the PC:
- **Reminders** and the after-class *"Homework for Maths?"* check-ins show as Windows notifications. Click one to open that day or answer the check-in.
- Closing the window keeps Planner in the **system tray** (by the clock) so reminders still arrive. Right-click the tray icon to **Quit**, or tick **Start with Windows** so reminders work after a restart.
- **Keyboard shortcuts:** **N** new item, **T** today, **← / →** previous / next day, **Ctrl + ← / →** previous / next week, **1–4** switch tabs, **Esc** closes a sheet.
- **Backups** (in the ••• menu) save to **Documents › Planner** by default. Backup files work with the Android app too: **Restore from a backup file** adds what's missing and doesn't delete anything.

> **Tip:** Uninstalling the app deletes your tasks. Use **••• → Save a backup file** now and then.

## Automatic builds

Every push to `main` builds `Planner-Setup.exe` and `Planner-Portable.exe` with GitHub Actions and posts them on the **Releases** page. No setup needed.

## Building it yourself

You need Node.js 22+ on Windows.

```sh
npm install
npm start        # run it
npm run build    # makes dist/Planner-Setup.exe and dist/Planner-Portable.exe
```

## Project layout

| Path | What it is |
| --- | --- |
| `www/` | The app itself (HTML, CSS, JS) |
| `www/app.js` | All app logic: planner, timetable, homework check-ins, reminders, keyboard shortcuts |
| `main.js` | The Windows side (made with [Electron](https://www.electronjs.org)): window, tray, notifications, backups |
| `preload.js` | The small bridge that lets `app.js` schedule Windows notifications |
| `scheduler.js` | Works out when each reminder is due |
| `.github/workflows/build.yml` | Builds the app and publishes it on Releases |
