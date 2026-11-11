# Changelog

All beta releases of Cyclone. Download them from [Releases](https://github.com/zakusworo/cyclone-beta/releases);
the app also offers each new version as a notification.

Version numbers are **major.minor.patch**: the last number goes up for very small changes and fixes, the
middle one for small updates, the first one for major updates.

## 0.15.3 · 2026-11-12 · Tamaki

**New**
- **Type the size on your tyre.** The tyre list in Gear (edit a bike → Tyre size) now starts with *Type the size
  on the tyre*: enter it as printed on the side, like `26 x 1.50`, `700x25C`, `650b x 47`, `26 x 1-3/8` or the two
  numbers `40-559`, and Cyclone shows the wheel size as you type. Sizes in Garmin's wheel-size table use Garmin's
  measured value; others are worked out from the size. The wheel field on the Sensors screen takes a size too.
- **Your own brand and model.** Not in the list? The brand and model lists now start with *Not listed? Type your
  own brand…*, and what you type shows at the top as *Use "…"*.
- **More tyre sizes** from Garmin's table, including 26 × 1.50, 26 × 1.75, 26 × 1-3/8, 27 × 1-1/4 and the 650 sizes.

**Fixed**
- **Stops ahead on Android 8 and 9.** On these versions Cyclone could reach only some of the backup stops servers;
  one of them was refused because of a missing security certificate. Cyclone now includes it. (The servers
  themselves were overloaded on 11–12 November, so a download may still need another try.)
- **700 × 30C** was set to 2170 mm; Garmin's table says 2146 mm. Road, gravel, city and touring bikes on
  700 × 30C move to 2146 mm by themselves.
- An unreadable stops file no longer closes the ride screen.

## 0.15.2 · 2026-11-11 · Jervois

**Fixed**
- **Stops ahead missing on some routes.** When the OpenStreetMap server answered a route's stops search with
  an empty list (it sometimes does when it is busy, without saying so), Cyclone kept that empty list for good and
  never searched again, so the Ahead page kept saying *Stops not downloaded yet* however often you synced. Now
  an empty answer is checked with a second server, kept for 6 hours at most, and **Sync now** always searches
  again. Routes that showed no stops get them at the next sync.
- **An empty GPX no longer replaces your route.** A downloaded GPX can hold only the route's name and
  no points (it happened with a RideWithGPS download). Importing one used to overwrite your route of the same
  name; now Cyclone says the file has no points and keeps your route.

**Better**
- **Faster sync for a new route.** Stops now download before the BMKG weather warnings, and **Sync now** skips
  warnings fetched in the last 10 minutes. A busy stops server is left after 75 seconds instead of being waited
  on for minutes and then asked again, and the Online screen shows which server Cyclone is waiting on.
- **Sync now** no longer starts a second sync while one is running; it tells you what the running one is doing.
- When a search really found no stops along a route, the Ahead and Online screens now say so, instead of
  *not downloaded yet*.

## 0.15.1 · 2026-11-10 · Britomart

**New**
- **Faster GPS start.** When the phone's last GPS fix is more than an hour old, Cyclone now asks Android for
  fresh GPS time and satellite orbit data as GPS starts (at most every 30 minutes, and again while it
  searches if the phone comes online later). With it, a first fix under open sky takes seconds instead of
  minutes on most phones. Phones with a MediaTek chip fetch their own orbit data and take only the time.
- **Why GPS is slow, on screen.** With no fix 90 seconds after GPS starts, the ride screen says either
  *No satellites yet · needs open sky* (the phone hears nothing: indoors, under a roof, or a covered pocket)
  or *GPS searching · N satellites heard* (it hears them and is still working out the position).
- **GPS log in problem reports.** Cyclone keeps a short log of what GPS did: when it started, satellites heard
  while searching, how long the first fix took and how accurate it was. Problem reports (Options → Beta &
  updates → Send problem report) now include it, since some phones hide this from Android's own log.

## 0.15.0 · 2026-11-09 · O'Connell

**New**
- **Ride insights.** The summary of every ride now opens with an **Insights** card: a label for the kind of
  ride (Endurance · Rolling · 38 km), a few sentences on how it went, and up to seven short notes, each with
  a line on what it means. Depending on what you recorded, they cover:
  - new personal bests (fastest 5, 10, 20, 40 and 100 km, best power), longest ride, most climbing;
  - how this ride compares with your earlier rides of a similar distance, and your rides in the last 30 days;
  - pacing: the first half against the second, and why one was slower (more climbing, or the wind);
  - wind and temperature at the time of the ride (Open-Meteo), and how much of the ride was into the wind;
  - with a heart-rate sensor or power meter: time in zones, training load with a recovery tip, and whether
    your heart rate crept up later in the ride;
  - the biggest climb with its climbing speed (VAM), stops, calories and progress towards your goals.
  Everything is worked out on the phone from your own rides: no account and no AI service. Only an
  approximate location (about 1 km) and the ride's date go to Open-Meteo for the weather.

**Fixed**
- **Thousands of metres of climbing on rides without altitude.** On phones that record no altitude, Cyclone
  adds it from terrain data after the ride. One GPS fix far away made it follow a straight line to that spot
  and back, adding the hills in between: one test ride showed 15,000 m on 1.8 km. It now follows the ride's
  own distance, which already leaves such jumps out. Rides filled in by earlier versions are filled in again
  once, by themselves, the next time they are opened or synced.
- **Climbing speed (VAM) in the summary's Climbs list** was too high on phones that write records less
  often than once a second; it now uses the real riding time.

## 0.14.6 · 2026-11-09

**Fixed**
- **Weather forecast not updating after rides without altitude.** Before a ride goes online, Cyclone fills in
  missing heights from terrain data. Several such rides in one sync used up the weather service's per-minute
  limit within seconds, and everything after them failed, the forecast included. The forecast now updates
  first, and Cyclone waits out the per-minute limit (about a minute) instead of giving up.
- **Bluetooth sensors not found on Android 8 to 11 while Location is off.** These Android versions show no
  Bluetooth sensors to apps while the Location switch is off. The pairing window now says so and asks you to
  turn Location on, instead of searching in vain.

## 0.14.5 · 2026-11-08

**Fixed**
- **Stops along the route never appeared on Android 8 and 9** (water, minimarkets, toilets, bike shops on the
  Ahead page). Their map server, overpass-api.de, now only accepts TLS 1.3 connections, which Android has from
  version 10. On older Android, Cyclone now asks public mirrors that still accept these phones, one after
  another until one answers; Android 10 and newer still ask overpass-api.de first.
- **"Finish" at the start of out-and-back routes.** On a route that comes back along the same road, the
  position could be matched to the way home: the turn card said "Finish" and the distance to go read 0.2 km a
  few hundred metres into a 2 km route. You now stay on the way out until you have turned around, also when
  the ride was started away from the route.

## 0.14.4 · 2026-11-06

**Fixed**
- **Button labels cut short.** On Android 8 the green button showed only ► instead of ► START or
  ► RESUME, and on any phone the pause button showed only ❚❚ after switching between day and night
  colours: the word had wrapped onto a hidden second line. Button labels are now sized to fit the button
  in capitals and always show in full.

**Guide**
- New screenshots in the [tutorial](TUTORIAL.md) and on the main page, taken with 0.14.4 in day and night
  colours. The tutorial also covers what changed since 0.14.1: small screens and large text, the home screen
  scrolling, the **RIDE RESUMED** banner, rides kept in internal storage on some phones, and two new
  troubleshooting answers.

## 0.14.3 · 2026-11-06

**Fixed**
- **Ride numbers cut in half on some phones** (reported with a photo by a beta tester). On smaller screens,
  or when the phone's font size or display size is turned up, the numbers on the ride screen showed only
  their top half and the red button read "HOLD TO" without "STOP". Every number and label now takes the
  largest size that fits its box, so they stay whole from small phones to tablets (and grow a little on
  tablets). The ride buttons fit their labels and get a little shorter on short screens, leaving more room
  for the data. Text follows the phone's font size up to 1.3×.
- **Home screen tiles squashed to bare icons** on short screens or with large text. Home now fills the
  screen when there is room and scrolls when there isn't. Tile names shrink to fit instead of being cut off.
- **Text cut off at the bottom** when a long label was shortened with "…": the last line of the Ride card
  on Home and the tile subtitles. They now sit on one line, still shortened with "…" when needed, but no
  longer clipped.

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
