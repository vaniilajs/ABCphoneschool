# Expo Release It - Keys & Credentials

This directory contains sensitive credentials for building and uploading to app stores.
These files should NOT be committed to version control.

## Required Files

### 1. `android_play_console_service_account.json`
Google Play Console service account JSON key for uploading to Play Store.

**How to get:**
1. Go to Google Cloud Console > APIs & Services > Credentials
2. Create a Service Account
3. Download the JSON key
4. Link it to Google Play Console: Setup > API access > Link service account

References:
- https://docs.fastlane.tools/actions/supply/#setup

### 2. `android_release.keystore`
Android release keystore file for signing APK/AAB builds.

**How to generate:**
```bash
keytool -genkey -v -keystore android_release.keystore \
  -alias refugee-literacy-project \
  -keyalg RSA \
  -keysize 2048 \
  -validity 10000
```

Save the passwords - you'll need them during `expo-release-it init`.

### 3. `ios_app_store_connect_api_key.p8`
App Store Connect API key (.p8 file) for uploading to TestFlight.

**How to get:**
1. Go to App Store Connect > Users and Access > Keys
2. Create a new API key with Admin access
3. Download the .p8 file (only available once!)
4. Note the Key ID and Issuer ID

References:
- https://developer.apple.com/documentation/appstoreconnectapi/creating_api_keys_for_app_store_connect_api

## keyholder.json

After running `expo-release-it init`, a `keyholder.json` file will be created containing:
- Android keystore password and alias
- iOS App Store Connect Key ID and Issuer ID

Keep this file secure and share with your team via secure means (not in VCS).
