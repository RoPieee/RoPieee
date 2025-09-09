# RoPieee Releases

We release on a regular basis to fix bugs or implement new features. Stability is of the highest importance here: RoPieee is foremost meant to listen to music and should be 'out-of-the-way'.

## Updates ##

A RoPieee unit checks for updates every few hours. When it finds an update it will download it in the background. When it's downloaded the user will get a notification in the webbrowser from where it can choose to update the unit.

## Changelog ##

**2025.08.2**

* IMPROVEMENT: update Linux kernel
* FIX: Squeezelite discovery is not working anymore ([#9](https://github.com/RoPieee/RoPieee/issues/9))

[![Static Badge](https://img.shields.io/badge/Download-2025.08.2-blue)](/docs/releases/2025_08_2.md)

**2025.08.1**

* IMPROVEMENT: update Linux kernel
* FIX: rare crash related to the SD card on a Pi3
* FIX: race condition in USB auto suspend
* FIX: USB auto suspend can not deal with 2 of the same USB DAC's
* FIX: navigating to the 'network' tab in the webinterface takes a long time ([#6](https://github.com/RoPieee/RoPieee/issues/6))

[![Static Badge](https://img.shields.io/badge/Download-2025.08.1-blue)](/docs/releases/2025_08_1.md)

**2025.08**

* NEW: new public website
* NEW: GitHub project page + documentation
* IMPROVEMENT: make (onboard) WiFi more reliable
* IMPROVEMENT: add frequency band to wireless information
* IMPROVEMENT: update Plexamp component
* IMPROVEMENT: update Librespot component (Spotify)
* IMPROVEMENT: update Linux kernel
* FIX: [display] show previous image art when there is none
* FIX: [display] volume popup is rotated on Display 2
* FIX: 'auto suspend' is only supplied to the first USB DAC
* FIX: devices tab shows channel of actual running version, not the setting

[![Static Badge](https://img.shields.io/badge/Download-2025.08-blue)](/docs/releases/2025_08.md)

**2025.06.1**

* IMPROVEMENT: update HQPlayer NAA component
* IMPROVEMENT: update Linux kernel
* IMPROVEMENT: some UI polish to the Network tab
* FIX: Spotify does not work on HAT with mixer

[![Static Badge](https://img.shields.io/badge/Download-2025.06.1-blue)](/docs/releases/2025_06_1.md)

**2025.06**

* NEW: add support for USB HID devices as remote control
* NEW: add support for InnoMaker Digi One
* NEW: update remote units from 'devices' tab
* NEW: [remote] option to 'follow display' wrt controlled zone
* IMPROVEMENT: [services] support for 2 USB DAC's
* IMPROVEMENT: some UI polish to the Audio tab
* IMPROVEMENT: improve support for Realtek based WiFi dongles
* IMPROVEMENT: [display] improve displaying long zone names
* IMPROVEMENT: make device discovery more reliable
* IMPROVEMENT: make device table sorting order persistent
* IMPROVEMENT: update Linux kernel

[![Static Badge](https://img.shields.io/badge/Download-2025.06-blue)](/docs/releases/2025_06.md)

**2025.05**

* IMPROVEMENT: [display] make zone list adaptive
* IMPROVEMENT: update Plexamp component
* IMPROVEMENT: update UPnP player component
* IMPROVEMENT: speed up configure step
* IMPROVEMENT: update Linux kernel
* FIX: cracks and pops on the Usbridge
* FIX: LEDs behave different

**2025.04**

* NEW: support for the new 'Raspberry Pi Display 2' touchscreen
* NEW: support for the Raspberry Pi Compute Module 5
* NEW: auto-update firmware on the Pi 4
* IMPROVEMENT: upgrade Linux kernel to 6.12 LTS
* IMPROVEMENT: [display] rotation now also works on the Pi 5
* IMPROVEMENT: update Plexamp component
* IMPROVEMENT: update Librespot component (Spotify)
* IMPROVEMENT: update UPnP player component
* FIX: RoPieee does not boot on Pi 5 Rev 1.1

**2025.02**

* NEW: auto-update firmware on the Pi 5
* NEW: Squeezelite: enable downsampling
* NEW: Squeezelite: support client side DSD decoding
* IMPROVEMENT: update Linux kernel
* IMPROVEMENT: slow down a bit on the Pi 5
* ENHANCEMENT: update Squeezelite component
* FIX: LEDs are inverted on Pi5

**2025.01**

* NEW: survive hostname change from webpage
* NEW: install update from display
* NEW: [display] implement Roon volume limits
* IMPROVEMENT: update Linux kernel
* IMPROVEMENT: update Plexamp component
* IMPROVEMENT: update Shairport-Sync component (Airplay)
* ENHANCEMENT: update Squeezelite (LMS) component
* IMPROVEMENT: automagically switch to HTPDATE if NTPDATE keeps failing
* IMPROVEMENT: webpage has it's own 'donate' page
* FIX: [display] volume slider initial position is not correct
* FIX: increase network online time-out
