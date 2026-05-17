# Sony Google TV Debloat Guide (A80J & Similar Models)

A tested and verified debloat guide for Sony Google TVs using ADB. Removes unnecessary bloatware to improve performance and reduce background processes without breaking the system.

---

## Requirements

- A Sony Google TV (tested on A80J, should work on most Sony Google TV models)
- A PC with ADB installed — download [Android Platform Tools](https://developer.android.com/tools/releases/platform-tools)
- Your TV and PC on the same WiFi network

---

## Setup

### Enable ADB on your TV
1. Go to **Settings > Device Preferences > About**
2. Scroll to **Build Number** and click it 7 times to unlock developer options
3. Go back to **Device Preferences > Developer Options**
4. Enable **USB Debugging**

### Connect ADB over WiFi
1. Find your TV's IP address under **Settings > Network & Internet > View connection details**
2. Open a terminal/command prompt in your platform-tools folder
3. Run:

`adb connect YOUR_TV_IP`

4. Confirm the connection with:

`adb devices`

You should see your TV listed.

---

## Debloat Command

Paste this into your terminal in one go. Each package is separated with `&` so failures don't stop the chain:

`adb shell pm uninstall --user 0 com.sony.dtv.demomode & adb shell pm uninstall --user 0 com.sony.dtv.multiscreendemo & adb shell pm uninstall --user 0 com.sony.dtv.demosupport & adb shell pm uninstall --user 0 com.sony.dtv.imanual & adb shell pm uninstall --user 0 com.sony.dtv.smarthelp & adb shell pm uninstall --user 0 com.sony.dtv.b2b.hotelmode & adb shell pm uninstall --user 0 com.sony.dtv.b2b.prosettings & adb shell pm uninstall --user 0 com.sony.dtv.b2b.rs232csupport & adb shell pm uninstall --user 0 com.sony.dtv.b2b.vendorprotocol & adb shell pm uninstall --user 0 com.sony.dtv.sonybugreportsys & adb shell pm uninstall --user 0 com.sony.dtv.sonyloglevelsettingvnd & adb shell pm uninstall --user 0 com.sony.dtv.sonyloglevelsettingsys & adb shell pm uninstall --user 0 com.sony.dtv.customersupport & adb shell pm uninstall --user 0 com.sony.dtv.reminderservice & adb shell pm uninstall --user 0 com.sony.dtv.promos & adb shell pm uninstall --user 0 com.android.printspooler & adb shell pm uninstall --user 0 com.android.dreams.basic & adb shell pm uninstall --user 0 com.google.android.play.games & adb shell pm uninstall --user 0 com.google.android.backdrop & adb shell pm uninstall --user 0 com.google.android.tv.bugreportsender & adb shell pm uninstall --user 0 com.android.providers.calendar & adb shell pm uninstall --user 0 com.android.providers.contacts & adb shell pm uninstall --user 0 com.android.providers.userdictionary & adb shell pm uninstall --user 0 com.android.wallpaperbackup & adb shell pm uninstall --user 0 com.android.vpndialogs & adb shell pm uninstall --user 0 com.google.android.syncadapters.calendar & adb shell pm uninstall --user 0 com.google.android.syncadapters.contacts & adb shell pm uninstall --user 0 com.google.android.partnersetup & adb shell pm uninstall --user 0 com.google.android.backuptransport & adb shell pm uninstall --user 0 com.google.android.feedback & adb shell pm uninstall --user 0 com.google.android.marvin.talkback & adb shell pm uninstall --user 0 com.google.android.videos & adb shell pm uninstall --user 0 com.youview.tv.servicehost & adb shell pm uninstall --user 0 com.vewd.core.integration.dia & adb shell pm uninstall --user 0 tv.samba.ssm & adb shell pm uninstall --user 0 com.sony.dtv.osat.music & adb shell pm uninstall --user 0 com.sony.dtv.smartmediaapp & adb shell pm uninstall --user 0 com.sony.dtv.system.crashlog & adb shell pm uninstall --user 0 com.sony.dtv.youview & adb shell pm uninstall --user 0 com.sony.dtv.hbbtvlauncher & adb shell pm uninstall --user 0 com.android.captiveportallogin & adb shell pm uninstall --user 0 com.sony.dtv.interactivetvutil & adb shell pm uninstall --user 0 com.sony.dtv.seconddispsetting & adb shell pm uninstall --user 0 com.sony.dtv.tvxlauncher.titlelist & adb shell pm uninstall --user 0 com.sony.dtv.tvxlauncher.programguide & adb shell pm uninstall --user 0 com.sony.dtv.homenetwork & adb shell pm trim-caches 999999G`

---

## Performance Tweaks

Reduces UI animation speeds for a snappier feel:

`adb shell settings put global window_animation_scale 0.5 & adb shell settings put global transition_animation_scale 0.5 & adb shell settings put global animator_duration_scale 0.5`

---

## ⚠️ Do NOT Remove These

These packages look like bloat but will cause a boot loop if removed. Your TV will not boot and you will need to factory reset:

| Package | Reason |
|---|---|
| `com.google.android.webview` | Core rendering engine, removing this breaks the entire UI |
| `com.google.android.katniss` | Google Assistant integration, essential for the Google TV launcher |
| `com.sony.dtv.tvx` | Sony's core TV app framework, removing this kills the boot process |
| `com.google.android.tvrecommendations` | Google TV home screen depends on this |
| `com.google.android.tts` | Text to speech engine, tied to deeper system functions than it appears |
| `com.android.location.fused` | Core Android location service, causes boot loop despite appearing to be simple bloat |

---

## If Your TV Boot Loops

If you removed something you shouldn't have, do a factory reset:

1. Unplug the TV from the wall
2. Press and hold the **power button on the TV itself** (not the remote)
3. While holding, plug the power cable back in
4. Hold for 10-15 seconds until you see a green LED or recovery screen

---

## What Gets Removed

- **Sony bloat** — demo modes, hotel/B2B commercial apps, iManual, Smart Help, bug reporters, log tools
- **Google bloat** — Play Games, Google Videos, Backdrop screensaver, backup/sync adapters, TalkBack
- **YouView/HbbTV** — interactive TV services irrelevant if you use streaming only
- **Samba TV** — ad tracking and viewing data collection
- **Android system bloat** — print spooler, calendar/contacts providers, wallpaper backup, VPN dialogs

---

*Tested on Sony Bravia A80J. Should work on most Sony Google TV models. Use at your own risk.*



