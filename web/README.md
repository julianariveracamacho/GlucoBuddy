# GlucoBuddy V2 — Ubuntu browser prototype

Includes the V1.1 UI, all 15 user-supplied hedgehog poses, plus medication-event history and supply ordering workflow.

## Run

```bash
unzip GlucoBuddy-V2-Ubuntu.zip
cd GlucoBuddy-V2
python3 -m http.server 8080
```

Open http://localhost:8080 in a modern desktop browser. Allow notifications in the Medicine screen.

## New in V2
- Click medication checkboxes to record timestamped `taken` or `undone` events; history survives refresh in that browser. V1 checks are not retrospectively timestamped.
- Download dose history as CSV.
- Optional desktop notifications for scheduled medications, checked approximately every 30 seconds while the page is open, limited to the first 15 minutes after schedule time; a notification is only attempted once per medication/day.
- Inventory threshold reminders while the browser page is open (once per item/day when due and not ordered).
- Supply status (`not ordered`, `ordered`, `received`) and optional supplier URL; user must order on the external site themselves.
- Preserves existing V1.1 browser data by using the same storage key.

## Important limitations
- **Not native push notifications or reliable background alarms.** The browser may suppress notification delivery, especially when closed, suspended, or on iOS. `localhost` or HTTPS is required for notification permission.
- **No automatic purchases.** It only tracks order status and links to the shop.
- The demo uses unencrypted `localStorage`, not suitable for sensitive clinical records, cross-device access, or reliable backups.
- Medication checkmarks are self-reports; this app does not prescribe doses or verify ingestion. Do not depend on this for critical medication reminders.
- Timezone follows the computer. Scheduled reminders only represent one event per medication per day. No support yet for multiple doses/day, schedules by weekday, time-zone travel, missed-dose decisions, or syncing.

## iPhone path
Rebuild in Expo React Native (the HTML project is not an Expo project); use secure native persistence and tested local scheduled notifications, then use EAS cloud builds from Ubuntu and distribute through TestFlight subject to Apple signing and developer requirements.
