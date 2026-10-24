# My Info Home YouTube Tracker

A mobile-friendly, installable web app (PWA) for planning Shorts, tracking uploads, recording metrics, and keeping lessons learned.

## What works immediately
- Add/edit/delete video records
- Schedule 9 AM and 6 PM upload slots
- Track status, video URL, duration, views, stayed-to-watch, AVD, APV, 24-hour and 7-day views
- Record hook, what worked, possible issues, lesson, and next action
- Dashboard, calendar, lesson log, CSV export, JSON backup/restore
- Local storage in the browser; service worker for basic offline app loading
- YouTube channel uploads sync via Google OAuth when configured

## Install on Android
1. Host these files on an HTTPS static host (for example, a static site service you control).
2. Open the hosted URL in Chrome on Android.
3. Open Chrome's menu and choose **Install app** or **Add to Home screen**.
4. Use the app from the home screen.

This package is a PWA, not a signed APK. An APK/Play Store release requires a separate Android wrapper/build and signing workflow.

## Enable YouTube sync
Automatic import is optional and needs your own Google Cloud project:
1. Open Google Cloud Console and create/select a project.
2. Enable **YouTube Data API v3** and **YouTube Analytics API**.
3. Configure the OAuth consent screen for your use and add your Google account as a test user if the app is in testing.
4. Create an **OAuth Client ID** of type **Web application**.
5. Add the deployed HTTPS origin (not a full page path) to **Authorized JavaScript origins**.
6. Open the app, paste the Client ID into Settings, and click **Connect / sync YouTube**.
7. Consent to read-only YouTube scopes.

The app uses Google Identity Services token flow in the browser. It does not include a client secret. Never put a client secret in browser code.

## Important limitations
- The tracker stores data locally in one browser/device. Export JSON backups regularly. Clearing browser data can delete your tracker.
- This sync imports channel uploads, publish dates, video URLs, duration, and public view/like/comment counts. API quota and permissions apply.
- The app does not currently auto-import Studio's “Stayed to watch” value. Enter it manually from YouTube Studio. Additional per-video YouTube Analytics queries can be added, but metric availability and access depend on the channel/API.
- This is a practical starter app, not a production-secured multi-user service. Test with your channel before relying on it.
- Do not enter passwords or channel secrets into the app.
