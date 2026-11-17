# GlucoBuddy V2.1 — Expo iPhone development on Ubuntu

A React Native / Expo starter using the original 15 watercolor hedgehog PNGs.

## Run on Ubuntu

Requires Node.js >= 22.13 (check `node --version`), npm and a smartphone.

```bash
cd GlucoBuddy-Expo-V2.1
npm install
npx expo install --fix
npx expo start
```

Install **Expo Go** on the phone, connect the phone and computer to the same Wi‑Fi network, and scan the QR shown by Expo. If your network blocks LAN connections, use `npx expo start --tunnel` (Expo account may be required). Test notification permissions and delivery **on an actual phone**.

If `npm install` reports dependency conflicts, use Expo's dependency resolver (`npx expo install --fix`), not `--force`.

## Current behavior

- Five native navigation sections: Home, Medicine, Supplies, Recipes and Discover.
- Add/delete medications, record daily *taken/undone* manual events, view up to 100 recent history events.
- Schedule daily device-local notifications when adding medication (subject to notification permission / OS restrictions).
- Track stock, update counts, manually mark orders, calculate reorder lead time, schedule a one-off local stock check.
- Recipes and wishlist stored locally.
- Data kept in AsyncStorage on *this device*. **No automatic import from V2 browser localStorage**.
- No remote push notifications, automatic purchasing, account sync, medical device integration, secure clinical record, or verified dose tracking.

## iOS distribution without owning a Mac

1. Create an Expo account: https://expo.dev
2. Install EAS CLI: `npm install -g eas-cli`
3. Run: `eas login`, then `eas build:configure`.
4. Set a unique iOS bundle identifier in `app.json` instead of the example `com.glucobuddy.companion`.
5. Join the Apple Developer Program for signing and TestFlight distribution.
6. Run: `eas build --platform ios --profile production`.
7. Test a signed build on a real iPhone and publish to TestFlight with `eas submit --platform ios` after configuring App Store Connect.

## Safety / engineering limitations

- This is an **unvalidated prototype**. Do **not** rely on it as the sole alarm for essential medicine or life-critical supplies. Continue an established reminder method.
- Local alarms are scheduled by the OS, but delivery is subject to user permission, iOS Focus, device settings, and platform restrictions. Schedule deletion/edits must be tested end-to-end.
- Only store test or non-sensitive data initially. AsyncStorage is not encrypted at rest; production needs appropriate privacy architecture, security review, backups and consent.
- Manual checkbox actions record events, **not confirmation of ingestion**. No dose calculations, insulin recommendations or continuous glucose monitor integration.
- Reorder estimate assumes a constant daily consumption rate; ordering is manual. Quantities must be reviewed.
- Native builds and phone notification behavior have **not been verified** in this environment.
