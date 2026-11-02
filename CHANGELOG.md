# Changelog

All beta releases of Cyclone. Download them from [Releases](https://github.com/zakusworo/cyclone-beta/releases);
the app also offers each new version as a notification.

Version numbers are **major.minor.patch**: the last number goes up for very small changes and fixes, the
middle one for small updates, the first one for major updates.

## 0.12.1 · 2026-11-02

**Changed**
- One tap to update: **Options → Beta & updates → Check & update** checks for a new version and, if there
  is one, downloads and installs it straight away (Android still asks you to confirm). Before, a second
  tap was needed. This works from the next update after 0.12.1.

## 0.12.0 · 2026-11-02

**New**
- Problem reports. If Cyclone closes unexpectedly (a crash, "not responding", or Android stopping it), it
  notes what happened and shows a notification at the next start.
- **Options → Beta & updates → Send problem report** opens your e-mail app addressed to Cyclone support
  (cyclonebikeco@gmail.com) with the report attached; you press Send. You can send a report without a
  crash too: it carries Cyclone's log.
- Reports hold Cyclone's own log, phone model, app version and the active route's name, not your rides.
  Nothing is sent until you press Send in your e-mail app.
- On Android 11 and newer, a force close from before this update may still be found in Android's records
  and offered for sending.

## 0.11.0 · 2026-11-02

**New**
- Routes from Google Maps. Plan the route in Google Maps (any mode; motorbike works well), tap **Share**
  and pick **Cyclone route**, or copy the link and press **Paste Google Maps link** on Routes. A start and
  a destination are enough; add stops to steer the route along the roads you want. Cyclone draws a bike
  route through your stops, with climbs and turn-by-turn.
- Import KML and KMZ files (Google My Maps, Google Earth) as well as GPX. These keep their exact line.
- Bike routing built in. When you leave your route, the way back now works offline with no extra app.
  Each area's routing data (about 40 MB) downloads by itself on Wi-Fi when you pick a route, or with the
  button on Routes.

**Fixed**
- The speed bar no longer fills up at 40 km/h. It starts at 60 km/h, grows when you go faster, and
  shows its top value.
- Beta & updates says at once when there is no internet instead of waiting for minutes.
- Routes screen buttons no longer cut off their labels.

## 0.10.0 · 2026-11-01

First beta.
- Offline maps: find and download the map for where you are (Options → Offline maps).
- Recording stays at one point per second with the screen off.
- Fastest 5 km / 10 km times fixed.
- Height above sea level corrected on Android 13 and older.
- Rider & zones, auto-pause and sounds are now in Options.
- Beta updates and messages from the developer, checked twice a day.
