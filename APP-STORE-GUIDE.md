# Publishing Pomo to the Apple App Store

## Overview

Your app uses **Capacitor** — a free, open-source tool by Ionic that wraps your web app (HTML/JS) into a real native iOS app. This is the same approach used by many apps on the App Store today.

**What you'll need:**
- A Mac (required by Apple — no way around this)
- Xcode installed (free from the Mac App Store)
- An Apple Developer account ($99/year)
- Node.js installed (free from nodejs.org)

---

## Step-by-Step

### 1. Host Your App or Use It Locally

Unlike the Play Store approach (which needs a live URL), Capacitor bundles your app files directly into the native wrapper. No hosting required for submission.

Just make sure your `pomo-app` folder is on your Mac.

### 2. Install Dependencies

Open Terminal on your Mac and navigate to the `pomo-app` folder:

```bash
cd path/to/pomo-app
npm install
```

This installs Capacitor and all required plugins.

### 3. Build the iOS Project

```bash
npm run build:ios
```

This will:
1. Add the iOS native project
2. Copy your web app files into it
3. Open Xcode automatically

### 4. Configure in Xcode

Once Xcode opens:

1. Click your project name in the left sidebar → **Signing & Capabilities**
2. Sign in with your Apple Developer account under **Team**
3. Change the **Bundle Identifier** from `com.yourname.pomo` to something unique (e.g., `com.nicklews.pomo`)
4. Set your **Version** (e.g., 1.0) and **Build** number (e.g., 1)
5. For icons: Xcode will show a red icon warning — drag your `icons/ios/icon-*.png` files into the AppIcon slots in the asset catalog

### 5. Test on a Device or Simulator

- Press **Cmd+R** in Xcode to run in the iPhone Simulator
- To test on a real iPhone: connect it, select it from the device dropdown, press **Cmd+R**

### 6. Create an Apple Developer Account

1. Go to [developer.apple.com](https://developer.apple.com)
2. Click **Account** → enroll in the Apple Developer Program
3. Pay the **$99/year fee**
4. Complete identity verification (1-2 business days)

### 7. Set Up App Store Connect

1. Go to [appstoreconnect.apple.com](https://appstoreconnect.apple.com)
2. Click **+** → **New App**
3. Fill in:
   - **Platform**: iOS
   - **Name**: Pomo — Focus Timer
   - **Bundle ID**: match what you set in Xcode (e.g., com.nicklews.pomo)
   - **SKU**: pomo-focus-timer (any unique string)
   - **Primary Language**: English

### 8. Prepare Your Store Listing

You'll need:

- **App name**: Pomo — Focus Timer
- **Subtitle** (30 chars): Beautiful Pomodoro Timer
- **Description**: Write 4-5 sentences about the app
- **Keywords**: pomodoro, focus, timer, productivity, work, study (100 char limit)
- **Screenshots**: Required sizes:
  - 6.7" iPhone (1290×2796): at least 3 screenshots
  - 6.5" iPhone (1242×2688): at least 3 screenshots
  - iPad Pro 12.9" (2048×2732): at least 3 screenshots (if claiming iPad support)
- **App icon**: 1024×1024 PNG (no transparency, no rounded corners — Apple rounds it)
- **Privacy Policy URL**: Required — generate at [privacypolicytemplate.net](https://privacypolicytemplate.net)
- **Support URL**: Can be a simple webpage or even your email

### 9. Archive and Upload from Xcode

1. In Xcode, select **Any iOS Device (arm64)** from the device dropdown (not a simulator)
2. Go to **Product** → **Archive**
3. When archiving completes, the **Organizer** window opens
4. Click **Distribute App** → **App Store Connect** → **Upload**
5. Follow the prompts — Xcode handles signing automatically

### 10. Submit for Review

1. In App Store Connect, go to your app → **App Store** tab
2. Under **Build**, select the build you just uploaded (may take 15-30 min to appear)
3. Fill in all required metadata fields
4. Click **Submit for Review**

**Review typically takes 1-3 days**, though it can be longer for first submissions.

---

## Checklist Before Submitting

- [ ] Bundle identifier is unique and matches App Store Connect
- [ ] App runs correctly in Xcode Simulator (iPhone 14 Pro, iPhone SE)
- [ ] All icon slots filled in Xcode asset catalog
- [ ] Screenshots captured at all required sizes
- [ ] 1024×1024 app icon ready (no alpha/transparency)
- [ ] Privacy policy URL is live
- [ ] Support URL is live
- [ ] App description and keywords filled in App Store Connect
- [ ] Build uploaded and visible in App Store Connect

---

## Tips for Getting Approved

Apple is stricter than Google. Common rejection reasons for simple apps:

- **"Minimal functionality"** — Apple may reject very simple apps. If this happens, consider adding features like history/stats tracking, ambient sounds, or themes to add more value.
- **Missing privacy policy** — Required if you collect any data (even analytics).
- **Crashes during review** — Always test thoroughly in Simulator first.
- **Screenshots don't match the app** — Make sure screenshots show the actual current UI.

---

## Cost Summary

| Item | Cost |
|------|------|
| Apple Developer Account | $99/year |
| Capacitor | Free |
| Xcode | Free |
| Hosting | Not needed (files are bundled) |
| **Total to launch** | **$99/year** |

---

## Both Stores at Once

Since you already have the Android setup, you can run:

```bash
npm run build:android
```

This opens Android Studio with the same app — so you can submit to both stores from one codebase.
