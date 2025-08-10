# Documentation

Over here you can find documentation about RoPieee - ranging from installation to advanced topics.

_Keep in mind that everything in this documentation is applicable to the latest available stable release!_

## Table of contents

- [Installation](#installation)
- [Basic Configuration](#basic-configuration)
  - [System](#system-settings)
  - [Audio](#audio-settings)
  - [Network](#network-settings)
- [Roon-only Settings](#roon-only-settings)
  - [Display](#display-settings)
  - [Remote](#remote-settings)
- [Advanced Settings](#advanced-settings)
- [Other Services](#services-settings)
    - [UPnP Bridge](#upnp-bridge)
    - [UPnP/DLNA](#upnpdlna)
    - [Airplay](#airplay)
    - [Spotify Connect](#spotify-connect)
    - [Squeezelite](#squeezelite)
    - [HQPlayer NAA](#hqplayer-naa)
- [Advanced topics](#advanced-topics)
    - [Native DSD support](#about-native-dsd-support)
- [Appendix A: supported HAT's](/docs/APPENDIX_A.md)
- [Appendix B: USB DAC's with native DSD](/docs/APPENDIX_B.md)

## Installation

### Hardware

To install RoPieee you will need supported a supported Raspberry Pi and a microSD card of at least **8 GB** in capacity. Currently, the following hardware is supported:

| Raspberry Pi Family | Model |
| ------------------- | ------------- |
| Raspberry Pi 3  | Raspberry Pi 3, Compute Module 3 and Zero W 2  |
| Raspberry Pi 4  | Raspberry Pi 4 and Compute Module 4 |
| Raspberry Pi 5  | Raspberry Pi 4 and Compute Module 5 |

In addition to the Raspberry Pi, RoPieee also supports the legacy network bridge from **Allo** called the **Usbridge (Signature)**, now discontinued.

### Preparing the microSD card

To write (copy) the RoPieee image to the microSD card, you first need software appropriate to your computer OS, like [Balena Etcher](https://etcher.balena.io/), and the latest RoPieee image which is always found [here](/docs/CHANGELOG.md) 

RoPieee images are provided both in a compressed (XZ) variant and an uncompressed one. The compressed variant is smaller in size (downloads faster), but requires decompression. Software such as [Balena Etcher](https://etcher.balena.io/) is able to do that automagically for you. There is no need to format the microSD card before writing.

> [!TIP]
> If compression sounds like 'abracadabra' to you: don't worry, just download the uncompressed variant.

> [!IMPORTANT]
> Make sure you download the correct image corresponding to your specific Raspberry Pi hardware.

### Start the installation process

Insert the microSD card in the corresponding Raspberry Pi, attach an ethernet cable, and power up the unit. RoPieee will start its installation process unattended. There is nothing for you todo, except maybe grab a cup of ☕.

### Internet access during installation

RoPieee requires internet access during installation. Ideally this is done by attaching an ethernet cable with appropriate network access. 

> [!TIP]
> Build the RoPieee device close to your main internet router or switch, even if the ultimate location in your deployment will be elsewhere using WiFi. Setup is easier and faster using ethernet.

If that's not possible (for example, the **Raspberry Pi Zero 2 W** lacks a cable connection), follow the following WiFi guide.

#### RoPieee WiFi access point setup (only if required)
If no ethernet connection is found, RoPieee will setup a WiFi access point called `RoPieee-AP-[unique_id]`. Connect your computer to this WiFi network and use `goropieee` as password.

![Connecting to the RoPieee AP](/docs/images/ropieee-ap.png)

When connected, browse to `http://192.168.250.1` to select your wireless network and enter your password.
The unit will reboot, connect to your production wireless network, and then will continue the installation process.

![Selecting your WiFi network](/docs/images/ropieee-ap-connect.png)

### Finish the installation process

During the installation process the unit will reboot a few times. It will also show a fast blinking green LED.

After 15 minutes or so the installation process will finish. This can be determined by looking at the green LED: it should have switched from fast blinking to a steady 'heartbeat' at once per second (½ Hz).

Furthermore, you should now be able to reach RoPieee's internal webpage at http://ropieee.local, and see this page:

![Welcome!](/docs/images/ropieee-welcome.png)

Congratulations! :muscle: :clap: :notes:

> [!TIP]
> If you can't reach RoPieee's webpage at http://ropieee.local, try to reach the unit directly by using its IP address. You can determine the IP using a port scan application (such as [Fing](https://www.fing.io/)) or via your router interface, often in a DHCP configuration tab that lists all connected devices.

### General navigation

If you click on **`Continue`** (after you donated of course :wink:), you will see RoPieee's regular webpage. It uses several tabs that group specific settings, so let's walk them through.

## Basic Configuration

### System settings

On the **`System`** tab you can configure the **Device Name** and **Timezone**. The device name (by default `ropieee`) is the name with which your RoPieee unit identifies on your network, and how you can reach it in a browser (via http://ropieee.local, where `ropieee` is the device name). 

If you only have one RoPieee unit in your network, then there's no real need to change its name. If you're running more than one RoPieee, you must change every one to something unique. Don't use spaces in the device name.

The timezone is used internally by RoPieee. There's no need to change this unless your using additional [display](#display-settings).

Once you **Apply** the changes, RoPieee will save the changes made and will show a popup stating that you need to run a configure step. 

> [!IMPORTANT]
> The changes made are only going to be effected after running the configure step. Depending on the changes, RoPieee may display a popup notification stating that a reboo is required. 

### Audio settings

On the **`Audio`** tab you can configure RoPieee's audio settings. First you can configure an audio HAT, if one attached. RoPieee supports an extensive set of HAT's, and is continously updated to support the latest models. You can find the complete HAT list over [here](/docs/APPENDIX_A.md)

> [!NOTE]
> Some HAT's support automatic detection, which means that RoPieee is able to detect them during installation. They will be configured automagically.

If you have configured a HAT, you can also potentially enable **Dynamic Audio Power Management (DAPM)**: with this option it is possible to remove the audio signal completely (the HAT disables its output) - this can be handy when using a HAT with a TOSLINK output, for example.

> [!WARNING]
> Not all HAT's support DAPM!

Secondly you can configure Audio USB support. This is enabled by default. RoPieee will show the USB DAC's that are connected (make sure they are powered on!):

![USB settings!](/docs/images/ropieee-usb.png)

With the **USB Force Volume** setting you have the option to force the volume control of the USB DAC when starting up RoPieee. _This option is rarely needed._

And with **USB Auto Suspend** you can make the USB DAC shutdown after a defined timeout when being idle. This can be handy when the USB DAC is directly driving your power amplifier, in which case the output is disabled.

> [!WARNING]
> Not all USB DAC's support this option. _In fact: most don't!_

### Network settings

On the **`Network`** tab you can configure RoPieee's network settings. RoPieee will use a cabled connection with DHCP as its default configuration. Click on **More Info** to display current connection information. You can change the connection type from DHCP to static by changing the **Configuration Method**.

> [!TIP]
> We advise to use DHCP at all times. In the rare case you require a static IP address, use your router's setting if possible.

RoPieee also supports wireless (WiFi) connections, if a wireless interface is available on your hardware. First you need to **Enable Wireless**, after which RoPieee will check if the necessary hardware is available. If that's the case, a new tab labelled **Wireless** will show next to the **Wired** tab:

![Wireless settings!](/docs/images/ropieee-wireless.png)

Now select the **Interface**: RoPieee supports not only the internal wireless interface, but also external USB WiFi dongles. The reason to use an external dongle is that they have a larger antenna in comparison to the onboard chip.

Next click the **SCAN** button to start scanning for wireless networks. After a few seconds the scanning will finish and you will be able to select the correct wireless network. Provide a password and your wireless connection is up and running.

> [!TIP]
> Although the debate about wired vs. wireless amongst audiophiles is on-going, we advise wired as the preferred connection type. Its advantages outweigh possible disadvantages by a large margin.

## Roon-only settings

### Display settings

If using an official Raspberry Pi Touchscreen (both generation 1 and 2) attached to your Raspberry Pi, RoPieee will show a **`Display`** tab where you can configure the behaviour of the touchscreen.

> [!IMPORTANT]
> The touchscreen functionality only works while using Roon.

If the display is upside down, change the display **Orientation** setting to “Rotated” (this is case-dependant).

Type the name of the **Roon Default Zone** that the display should be associated with (e.g. what content should display on the screen): _this must be exactly as is specified in Roon settings._

> [!TIP]
> You can change the controlled Roon Zone dynamically on the touchscreen by pressing the zone label and selecting from the dropdown.

Most settings speak for themselves. If you provide a **Screen Saver Timeout**, the screen will turn off after the specified timeout. Furthermore, if you enable the **Show Clock** option, a clock will be displayed after the timeout.

> [!TIP]
> You can toggle the different states (player, clock, and off) by pressing the cover art section on the screen.

> [!TIP]
> The display can show content from any Roon Zone, not just the Raspberry Pi attached to the display.

> [!IMPORTANT]
> To be allowed to show content from Roon, it is required to activate RoPieee's Roon Extension in Roon settings.

### Remote settings

RoPieee supports various remote control solutions: Flirc, OSMC, and generic USB input devices. They will be automatically detected, as shown in **Remote Control Type**.

> [!IMPORTANT]
> The remote control functionality only works while using Roon.

With the generic USB input device support its possible to use a generic USB keyboard, but also 'fancy' input controllers. There are even some (rare) USB DAC's that support this, which means you can use buttons directly on the DAC to control your playback experience.

> [!IMPORTANT]
> To be able to control playback, it is required to activate RoPieee's Roon Extension in Roon settings.

If there's also a display connected, it is possible to enable **Follow Display Zone**. With this functionality the remote control will 'follow' the Roon Zone as actively displayed: remote control commands will be send to the displayed zone. Otherwise you can configure the controlled zone separately from the displayed zone.

## Advanced settings

The **`Advanced`** tab contains optional settings not required for basic use. It looks something like this:

![Advanced settings!](/docs/images/ropieee-advanced.png)

The **Update Channel** defines which release type the unit is utilizing. This should normally set to `STABLE`, unless you explictly make the choice to participate in the `BETA` program (see the [Roon Community Forum](https://community.roonlabs.com/c/audio-gear-talk/ropieee/56) for that).

If you're up to it, you can enable **Auto Update**. This makes it possible to install potential updates without manual intervention. This setting requires the **Reboot Schedule** setting to be enabled too.

With **Web Authentication**, you can limit access to RoPieee's webpage by requiring a password whenever someone accesses RoPieee webpage.

The four buttons at the bottom of this webpage provide some extra functionality that normally is rarely needed. The **Send Feedback** is worth mentioning, because clicking this button results in a log archive being created and sent to RoPieee HQ. It provides debug information that could help in analysing potential issues.

## Services settings

Roon is the streaming service enabled by default in RoPieee. However, it is possible to enable and configure additional streaming solutions on the **`Services`** tab.

> [!NOTE]
> Only enable additional services if you actually plan on using them.

> [!IMPORTANT]
> If you have more than one service enabled (in addition to Roon, which is enabled by default), it is important to realize that only one service can 'claim' the audio output on your RoPieee unit at a time. This means that if you want to switch from one service to another, you need to wait a few seconds after you have stopped playing on the first service until the audio output is released and availabile for the new service to bind to.

#### UPnP Bridge

The first service, **UPnP Bridge**, makes it possible to 'bridge' your UPnP device to a Squeezebox-capable one. This makes it possible to use an UPnP device directly from within Roon because Roon supports the Squeezebox protocol out-of-the-box. This is very handy when you have an UPnP-capable streamer that does not support Roon's RAAT protocol directly.

#### UPnP/DLNA

The **UPnP/DLNA** tab on the webpage speaks for itself. The only parameter that must be set, is the **Audio Output**. The **Service Name** defines how your RoPieee unit will show up on the network when you start looking for UPnP/DLNA devices.

#### Airplay

With **Airplay** enabled you can stream music from an Apple device to your RoPieee unit. Again **Audio Output** is the only required parameter.

#### Spotify Connect

With **Spotify Connect** you have the ability to stream directly from a Spotify app to your RoPieee device.

#### Squeezelite

**Squeezelite** is a software player dedicated to the former Squeezebox ecosystem, which later was owned by Logitech, but now is open sourced as [Lyrion](https://lyrion.org/). 

#### HQPlayer NAA

**HQPlayer NAA** (Network Audio Adapter) turns your RoPieee unit in a HQPlayer endpoint. HQPlayer's advanced protocol makes it possible to configure everything server side (in your HQPlayer application).

## Advanced topics

### About native DSD support

RoPieee supports many USB DAC's out-of-the-box, as its interface is standardized. That's not necessarily the case for DSD: if your USB DAC supports DSD, it's not guaranteed to be supported on RoPieee as well. This is an ommission in the standard, with mixed results as a consequence. DoP (DSD-over-PCM) however, works almost always in these cases.

> [!IMPORTANT]
> Native DSD does not offer any advantages over DoP, except that it uses slightly less bandwith. This often results in a higher maximum sample rate with native DSD vs. DoP.

Over the years we have been able to add native DSD support for many DAC's by patching the RoPieee's underlying operating system (which is Linux). [Here](/docs/APPENDIX_B.md) are the DAC's for which RoPieee has added explicit native DSD support.
