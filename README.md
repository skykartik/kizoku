<div align="center">

<img src="kizoku_logo.png" alt="Kizoku" width="128" />

# Kizoku &nbsp;<sub>貴族</sub>

**A tiny, native live wallpaper app for Windows.**
Play any video, or a link, as your desktop wallpaper. One small `.exe`, no .NET, no WebView2.

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-1f1f23)
![Language](https://img.shields.io/badge/made%20with-C%2B%2B%20%2F%20Win32-c8213f)
![License](https://img.shields.io/badge/license-MIT-1f1f23)

[**Download**](../../releases/latest) &nbsp;·&nbsp; [Features](#features) &nbsp;·&nbsp; [Using Kizoku](#using-kizoku)

</div>

<!--
  Screenshots: add 2-3 images to /assets and show them here, for example:
  <p align="center"><img src="assets/screenshot-wallpaper.png" width="760" /></p>
-->

## Why Kizoku

Most live wallpaper tools are heavy: a browser engine, a runtime, or a background service eating RAM.
Kizoku is a single native Windows program. It hands the video to Windows' own media stack, draws its
interface itself, and goes quiet whenever you're gaming, running on battery, or covering the desktop
with a maximized window.

## Features

- **Any video as a wallpaper** &ndash; plays through Windows Media Foundation, so it uses the codecs already on your PC (H.264 and more; see [Codecs](#codecs)).
- **Loops smoothly** &ndash; restarts shortly before the end so the last frame stays on screen instead of flashing black.
- **Library** &ndash; every wallpaper you apply is saved with a thumbnail. Click one to bring it back, add or delete entries, and see which one is active.
- **Links** &ndash; paste a direct video link, or a YouTube-style page link. Kizoku downloads it once, keeps a local copy and shows progress.
- **Dim, volume, speed, fit/stretch** &ndash; the basics, with smooth sliders.
- **Saves resources automatically** &ndash; pauses for full-screen apps and games, when a window is maximized, and optionally on battery.
- **Tray app** &ndash; close the window and it keeps playing from the system tray. Optional start with Windows.
- **Right-click menu** &ndash; "Set as Kizoku live wallpaper" on video files (optional; on Windows 11 it's under *Show more options*).
- **Drag & drop** &ndash; drop a video on the window to apply it instantly.
- **Updates built in** &ndash; check for updates, or install the new version with one click. Downloads can be verified with a SHA-256 hash.
- **Private** &ndash; no telemetry, no accounts. See [Privacy](#privacy).

<img width="800" height="450" alt="{5822888A-1D29-488E-ACDB-3CB550B1DEDC}" src="https://github.com/user-attachments/assets/39d157cf-a669-4177-8918-f9d29ed124e8" /> 


## Download

1. Go to the [**latest release**](../../releases/latest) and download `Kizoku.exe`.
2. Put it anywhere you like (a normal folder, not `Program Files`, so it can update itself) and run it.

> **Windows SmartScreen:** because the app isn't code-signed, Windows may say *"Windows protected your PC"*.
> Click **More info → Run anyway**. You can compare the file's hash with the one in the release notes:
> `certutil -hashfile Kizoku.exe SHA256`

## Using Kizoku

| I want to... | Do this |
| --- | --- |
| Set a wallpaper | **Browse** a video, or drag it onto the window |
| Use a link | **Link** (or *Add link* in the Library), paste the address, press Enter |
| Go back to an old wallpaper | **Library** tab, click its thumbnail |
| Remove one from the Library | Hover its thumbnail and click the **✕** |
| Dim the video | **Dim** slider. It applies a moment after you let go |
| Keep it running in the background | Close the window; Kizoku stays in the system tray |
| Quit | Tray icon → **Exit**, or **Settings → Exit** |

## Codecs

Kizoku plays whatever Windows can decode.

| Works out of the box | Needs a free/paid add-on from the Microsoft Store |
| --- | --- |
| H.264 (MP4, MOV, M4V), WMV, MPEG-4, most AVI, MKV with H.264 | HEVC / H.265, VP9 (WebM), AV1 |

If a file won't play, Kizoku says so. Installing the matching video extension from the Microsoft Store
normally fixes it (availability and price are set by Microsoft).

## Links and YouTube

- **Direct links** (`.mp4`, `.webm`, ...) are downloaded straight to a local cache.
- **Other pages** (YouTube and many more) need [yt-dlp](https://github.com/yt-dlp/yt-dlp). The first time you add such a link, Kizoku asks before downloading it (about 18 MB, official release) into `%APPDATA%\Kizoku`.
- Downloads are saved locally, so they loop smoothly, don't expire, and get a real thumbnail. Deleting a Library entry deletes its download.
- To get up to 1080p, the video-only stream is used, so **link wallpapers play without sound**. If no such stream exists, a lower-quality file with sound is used instead.
- Please only download content you have the right to use.

## Updates

*Settings → Check for updates* looks at an `update.json` file hosted in this repository. If there is a newer
version the button becomes **Update to x.y.z**: Kizoku downloads it, verifies its hash (when the file lists one),
replaces itself and restarts. An optional automatic check runs at most twice a day and never installs anything on its own.

## Known limitations

- Only the **primary monitor** is covered.
- Link wallpapers from sites are **video only** (no audio).
- There is **no blur** option yet

## Privacy

Kizoku has no telemetry. It only uses the network when you add a link, when it downloads the yt-dlp helper
(after asking), and when it checks for updates. Settings, thumbnails and downloaded videos live in `%APPDATA%\Kizoku`.

## Uninstall

Turn off **Start with Windows** and **Right-click menu** in Settings (this removes their registry entries),
exit Kizoku, delete `Kizoku.exe`, and optionally delete `%APPDATA%\Kizoku`.

## Acknowledgements

- [yt-dlp](https://github.com/yt-dlp/yt-dlp) for link support.
- Video playback by Windows Media Foundation.

## License

[MIT](LICENSE)
