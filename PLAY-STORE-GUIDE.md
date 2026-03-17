# Publishing Pomo to Google Play Store

## Overview

Your app is built as a **PWA (Progressive Web App)**. The fastest way to get it on the Play Store is by wrapping it in a **TWA (Trusted Web Activity)** — this is Google's official method for packaging web apps as Android apps. No Java/Kotlin needed.

---

## Step-by-Step

### 1. Host Your App Online

You need a live URL first. Free options:

- **Netlify** — Drag and drop the `pomo-app` folder at [netlify.com/drop](https://app.netlify.com/drop)
- **Vercel** — Connect a GitHub repo at [vercel.com](https://vercel.com)
- **GitHub Pages** — Push to a repo and enable Pages in settings

After hosting, verify the PWA works by visiting your URL on Android Chrome and checking if "Add to Home Screen" appears.

### 2. Set Up Digital Asset Links

Create a file at `/.well-known/assetlinks.json` on your hosted site. This proves you own the website. You'll fill this in after Step 3.

### 3. Package with PWABuilder (Easiest Method)

1. Go to [pwabuilder.com](https://www.pwabuilder.com)
2. Enter your hosted URL
3. Click **"Package for stores"** → choose **Android**
4. PWABuilder generates a signed APK/AAB ready for upload
5. It also gives you the `assetlinks.json` content — upload that to your site

### 4. Alternative: Use Bubblewrap CLI

If you prefer the command line, search for "Bubblewrap CLI" on npm (it's a Google ChromeLabs package). It generates the TWA wrapper project from your manifest URL.

That said, **PWABuilder (Step 3) is the recommended approach** — it uses Bubblewrap under the hood but adds a visual interface and handles APK signing automatically.

### 5. Create a Google Play Developer Account

1. Go to [play.google.com/console](https://play.google.com/console)
2. Pay the **one-time $25 registration fee**
3. Complete identity verification (takes 1-2 days)

### 6. Create Your Store Listing

You'll need:
- **App name**: Pomo — Focus Timer
- **Short description** (80 chars): Beautiful Pomodoro timer to boost your focus and productivity.
- **Full description** (4000 chars): Write about features, benefits, how it works
- **Screenshots**: At least 2 phone screenshots (1080x1920). Take these from your app on a phone or emulator
- **Feature graphic**: 1024x500 banner image
- **App icon**: 512x512 (already included in your package)
- **Privacy policy URL**: Required — you can generate one at [privacypolicytemplate.net](https://privacypolicytemplate.net)

### 7. Upload and Submit

1. In Play Console, create a new app
2. Go to **Release** → **Production** → **Create new release**
3. Upload the AAB file from PWABuilder
4. Fill in release notes
5. Submit for review

**Review typically takes 1-3 days** for new developers (can be up to 7 days).

---

## Checklist Before Submitting

- [ ] App works offline (service worker caches assets)
- [ ] Icons at all required sizes (included)
- [ ] manifest.json is valid
- [ ] Site is served over HTTPS
- [ ] assetlinks.json is accessible at /.well-known/assetlinks.json
- [ ] Privacy policy page is live
- [ ] Screenshots captured on a real device or emulator
- [ ] Tested on multiple screen sizes

---

## Cost Summary

| Item | Cost |
|------|------|
| Google Play Developer Account | $25 (one-time) |
| Hosting (Netlify/Vercel free tier) | $0 |
| PWABuilder | $0 |
| **Total to launch** | **$25** |
