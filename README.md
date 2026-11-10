# Embedded Car Infotainment System

A car-style infotainment system on a Raspberry Pi 3B+ (1 GB RAM), displayed on a TV over HDMI.
There is no desktop OS: a custom Yocto image boots straight into a Qt6/QML dashboard.

## Features
- AirPlay audio from an iPhone to HDMI (shairport-sync), with live title, artist and album art
- OpenStreetMap map with typed start/destination search, route line, distance and time
- Wi-Fi status and one-tap reconnect
- YouTube search and playback inside the dashboard (QtWebEngine, YouTube Data API)

## Stack
Yocto (scarthgap), BitBake, meta-raspberrypi, meta-qt6, Qt6/QML (eglfs), Qt Location, QtWebEngine, shairport-sync, BusyBox.

## Repo layout
`meta-infotainment/` is the custom Yocto layer: image tweaks, the dashboard recipe, the AirPlay recipe, the time-sync and Wi-Fi scripts.

## Build
1. Set up poky, meta-openembedded, meta-raspberrypi and meta-qt6 on the scarthgap branch.
2. Add `meta-infotainment` to `bblayers.conf`.
3. Build with `bitbake core-image-base` and flash the `.wic.bz2` to an SD card.

## Notes
- Spotify refuses third-party players, so audio uses AirPlay instead.
- Create your own YouTube Data API key and put it in `/etc/youtube-api-key` on the Pi.
- A GPS module is planned.
