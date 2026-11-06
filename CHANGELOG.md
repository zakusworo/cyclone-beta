# Changelog

All beta releases of Cyclone. Download them from [Releases](https://github.com/zakusworo/cyclone-beta/releases);
the app also offers each new version as a notification.

Version numbers are **major.minor.patch**: the last number goes up for very small changes and fixes, the
middle one for small updates, the first one for major updates.

## 0.14.3 · 2026-11-06

**Fixed**
- **Ride numbers cut in half on some phones.** On smaller screens, or when the phone's font size or display
  size is turned up, the numbers on the ride screen showed only their top half and the red button read
  "HOLD TO" without "STOP". Every number and label now takes the largest size that fits its box, so they
  stay whole from small phones to tablets (and grow a little on tablets). The ride buttons fit their labels
  and get a little shorter on short screens, leaving more room for the data. Text follows the phone's font
  size up to 1.3×.
- **Home screen tiles squashed to bare icons** on short screens or with large text. Home now fills the
  screen when there is room and scrolls when there isn't.

## 0.14.2 · 2026-11-05

**Fixed**
- **Cyclone closed every time you pressed Start** on some phones (reported on a Redmi Note 10 Pro with
  Android 16). Android would not create Cyclone's folder in Android/data, so the ride file could not be
  opened. Cyclone now checks that folder first and, if it isn't usable, keeps rides, routes and maps in its
  own internal storage instead. If a ride file still can't be created, Cyclone shows a message and stays
  ready rather than closing. Rides saved in either place show up in History.

## 0.14.1 · 2026-11-03

**New**
- **Day and night colours for the whole app.** Day is black on white, the easiest to read in direct
  sunlight; Night is the familiar white on black. **Auto** (the default) follows the time of day: it
  switches at sunrise and sunset where you are (06:00 and 18:00 until the phone knows where you are),
  worked out on the phone, no internet needed. Choose in Options → Ride options → Colours, or tap the clock
  on the ride screen while riding (Auto → Day → Night).
- **Smoother speed without a speed sensor**, worked out the same way Strava draws its speed (distance over
  the last 5 seconds), so the speed and max speed in Cyclone match what Strava shows afterwards.

**Fixed**
- **Loop routes showed 0 km to go right after the start** when the route leaves and comes back on the same
  road (and when riding the same loop twice in a day). Cyclone now takes the start, and follows you along
  the route by distance.
- **Distance without a speed sensor was about 10 % short.** It was the GPS speed added up second by second,
  which phones under-read, most of all at low speed. It is now measured along your GPS track (each step
  checked against the speed, so standing still or GPS wobble adds nothing). On a tester's Jakarta ride
  ridden next to a Coros Nomad, the same recording gives 7.32 km instead of 6.69 km (Coros: 7.55 km,
  started ~80 m earlier).
- **Jumps in the track line and the speed.** A GPS position that leaps far away for a second or two (tall
  buildings, trees, flyovers) is now dropped, and the speed can no longer jump faster than a bike can
  speed up or brake. Very vague positions (worse than ±50 m) are left out of the track.
- **Elevation 0 m on Strava** for phones without a barometer whose GPS gives no usable height: such rides
  now get their altitude from terrain data (Open-Meteo, 90 m) as soon as the phone is online, before
  Strava (web), Upload or the automatic sync sends them. Older rides get it too when you open them.
- The ride summary says where the altitude came from (barometer, GPS or terrain data).
- The Online screen no longer says "No SIM in this phone" to everyone; the problem-report text now points
  to Strava (web) for saving a ride's .fit file.

## 0.14.0 · 2026-11-02

**New**
- **Android 8.0 (Oreo) and newer** can now install Cyclone; before, it needed Android 10. On Android 8 and 9
  the Strava (web) button asks once for storage access, to save the ride into the Download folder.
- **Gear**: your bikes, each with a photo. Only the type is needed; brand, model, year, weight, tyre size and
  km ridden before Cyclone are optional. Brands and models come from a list that grows without an app
  update; a bike that is not in it can be typed in and suggested (only brand, model, year and type are sent).
- Each bike keeps its own tyre size (for speed from a wheel sensor) and its own speed and cadence sensors.
  Heart rate and power sensors stay with you. **Ride this bike** switches before a ride; every ride is
  counted for the bike it was ridden on, so each bike shows its own km and rides.
- **Stats & goals**: up to four goals (distance, riding time, climbing or rides, per week, month or year)
  with a progress ring and the pace still needed. This week / month / year against the last, a bar chart,
  weekly streaks, and km per bike. The Stats tile on the home screen shows your first goal.

**Changed**
- 0.13.0 was not released on its own; its Gear and Stats are part of this version.
- The home screen has two more tiles (Stats, Gear); long tile names shrink to fit.
- Your current settings become your first bike automatically, so nothing changes until you open Gear.

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
