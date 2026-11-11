# FixTrck (Milestone 3 - integrated build)

Cordova Android app for reporting and tracking campus facility repairs.
All screens are in `www/index.html` (HTML/CSS/JS). Data is stored on the device with `localStorage`
(mock data is loaded the first time the app runs).

## Features

- Student: sign up / log in, submit a repair report (type, building, room, description, optional photo),
  track status (Submitted / In Progress / Resolved), receive alerts when status changes or maintenance adds a remark.
- Maintenance staff: dashboard with stats, search and filters, set priority and status, add remarks,
  merge duplicate reports, view history and recurring problems.
- Edit profile: change name and profile picture (tap the avatar or use the menu).
- Android back button navigates back instead of closing the app.

## Build and run

    npm install -g cordova
    cd FixTrck
    cordova platform add android
    cordova run android          # phone with USB debugging, or an emulator
    cordova build android        # APK: platforms/android/app/build/outputs/apk/debug/

## Test in a browser first

    cd www && python -m http.server 8000      (open http://localhost:8000)

(`cordova.js` is not found in the browser. That is expected and harmless.)

## Demo accounts

| Role | Email | Password |
|---|---|---|
| Student | student@xu.edu.ph | any, 6+ characters |
| Student | maria@xu.edu.ph | any, 6+ characters |
| Maintenance staff | maintenance@xu.edu.ph | any, 6+ characters |

New student accounts can be created from the login screen (email must end in @xu.edu.ph).

## Reset saved data

Clear the app's storage (Android: Settings > Apps > FixTrck > Storage > Clear data) or, in a browser,
clear site data / run `localStorage.clear()` in the console.

## Known limitations

- Login is mock authentication (no passwords are stored or checked for existing accounts).
- Data lives only on the device; connecting Firebase is the planned next step.
