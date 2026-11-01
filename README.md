# Cyclone beta

Cyclone turns an Android phone into a bike computer: speed, distance, heart rate, cadence and power
(ANT+ or Bluetooth sensors), offline maps, GPX routes with turn-by-turn, climbs, laps, workouts and
.fit files for Strava.

This repository only hands out the beta builds. The app's source code is not here.

## Install

1. Needs Android 10 or newer. Any phone works; ANT+ sensors need a phone with ANT+ (most pair over
   Bluetooth instead).
2. Download the newest `cyclone-x.y.z.apk` from [Releases](https://github.com/zakusworo/cyclone-beta/releases/latest)
   on the phone and open it. Android asks once to allow installing apps from your browser.
3. Open Cyclone, allow location (and "Nearby devices" for Bluetooth sensors).
4. **Options → Offline maps → Find maps for my location** to download the map for your area (pick
   the smallest one that covers where you ride; Wi-Fi recommended).
5. **Options → This phone:** turn battery optimisation off for Cyclone, or Android may thin out the
   recording while the screen is off.

## Updates

Cyclone checks this repository twice a day and shows a notification when a new beta is out. Tap it
to download and install; Android asks you to confirm, and the first time to allow Cyclone to install
apps. You can also check by hand in **Options → Beta & updates**. Rides and settings are kept.

## Found a problem?

Open an [issue](https://github.com/zakusworo/cyclone-beta/issues/new). Say what you did, what
happened and what you expected. **Options → Beta & updates → Copy phone details** gives the app
version, phone model and Android version to paste in. A ride's .fit file helps a lot
(History → the ride → share).

Maps: © OpenStreetMap contributors, built by the [Mapsforge](https://github.com/mapsforge/mapsforge) project.
