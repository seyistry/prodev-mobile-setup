# Expo project + Expo Go — Quick Setup

This README documents a minimal, practical workflow to create an Expo app locally and run it on a physical device using Expo Go.

## Prerequisites
- Node.js (LTS recommended). Use nvm to manage versions if needed.
- Git
- A phone with Expo Go (iOS App Store / Android Play Store)
- (Optional) Android Studio for Android emulator, Xcode for iOS simulator (macOS only)

## Create a new Expo project
Use the official starter tool:

```
npx create-expo-app my-app
cd my-app
```

Choose a template (blank, tabs, etc.) when prompted.

## Run the development server
Start Metro/dev server:

```
npx expo start
```

This opens the Expo Dev Tools in your browser and prints a QR code in the terminal.

Common keys in the Dev Tools terminal:
- a — open Android emulator
- i — open iOS simulator (macOS + Xcode)
- r — reload
- d — toggle developer menu

## Run on a physical device with Expo Go
1. Install Expo Go from the App Store / Play Store.
2. Ensure your phone and development machine are on the same Wi‑Fi network (or use tunnel).
3. From the Dev Tools or terminal, scan the QR code:
    - iOS: open Camera app and tap the QR → open in Expo Go
    - Android: open Expo Go → Scan QR Code, or use device camera if it supports deep links

If network issues occur, select the connection type "Tunnel" in Dev Tools or start with:

```
npx expo start --tunnel
```

Notes:
- Expo Go runs JavaScript and the Expo SDK; it works out of the box for managed projects.
- If you add custom native modules, use a custom dev client (expo-dev-client) and EAS Build.

## Android USB debugging (alternative)
For USB testing with Android device:
- Enable USB debugging on device.
- Connect via USB and run:
  - `npx expo start`, then choose "Tunnel" or run `adb reverse tcp:8081 tcp:8081` (if using LAN and adb is installed).

## When you need a standalone app or native modules
- Use EAS Build to produce signed APK/AAB or IPA:
  - Configure `eas.json`
  - Build with `eas build --platform android` or `eas build --platform ios`
- For custom native code during development, use `expo-dev-client` and build a dev client with EAS.

## Useful commands
- Start: `npx expo start`
- Create: `npx create-expo-app my-app`
- Run Android emulator: press `a` in dev tools or `npx expo start` then `a`
- Run iOS simulator: press `i` (macOS only)
- Start with tunnel: `npx expo start --tunnel`

## Troubleshooting
- QR won’t connect: check firewall, same network, try Tunnel.
- "Expo Go can't load the app": make sure Metro is running and the correct connection mode is selected.
- Needing native modules: switch to dev client + EAS Build.

That's all you need to get a new Expo project running locally and on a phone with Expo Go. Adjust steps per OS and network environment as needed.