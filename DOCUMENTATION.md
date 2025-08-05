# Documentation

Over here you can find documentation about RoPieee - ranging from installation to advanced topics.

_Keep in mind that everything in this documentation is related to the latest available stable release!_

## Table of contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Advanced topics](#advanced-topics)
- [Appendix A: supported HAT's](https://github.com/RoPieee/RoPieee/blob/main/APPENDIX_A.md)

## Installation

### Hardware

To be able to install RoPieee you need an Micro SD card of at least **8 GB**. Furthermore you need hardware to run RoPieee. 
At this moment the following hardware is supported:

| Raspberry Pi Family | Model |
| ------------------- | ------------- |
| Raspberry Pi 3  | Raspberry Pi 3, Compute Module 3 and Zero W 2  |
| Raspberry Pi 4  | Raspberry Pi 4 and Compute Module 4 |
| Raspberry Pi 5  | Raspberry Pi 4 and Compute Module 5 |

Next to the Raspberry Pi, RoPieee also supports the now legacy network bridge from **Allo**, called the **Usbridge (Signature)**.

### Preparing the Micro SD card

To be able to write the RoPieee image to the Micro SD card you first need software like [Balena Etcher](https://etcher.balena.io/), and of course the latest RoPieee image that you can find [here](https://github.com/RoPieee/RoPieee/blob/main/CHANGELOG.md) 

RoPieee images are provided in a compressed (XZ) variant and an uncompressed one. The compressed variant is smaller in size, but requires decompression. Software such as [Balena Etcher](https://etcher.balena.io/) is able to do that automagically for you.

> [!TIP]
> If compression sounds like 'abracadabra' to you: don't worry, just download the uncompressed variant.

> [!IMPORTANT]
> Make sure you download the correct image corresponding your hardware.

### Start the installation process

Insert the Micro SD card in the corresponding Raspberry Pi, attach an ethernet cable, and power up the unit.
RoPieee will start its installation process unattended. There is nothing for you todo, except maybe grab a cup of ☕

### Internet access during installation

RoPieee requires internet access during installation. Ideally this is done by attaching an ethernet cable. If that's not possible (for example, the **Raspberry Pi Zero 2 W** lacks a cable connection), RoPieee will setup a WiFi access point called `RoPieee-AP-[unique_id]`. 

Connect your computer to this WiFi network and use `goropieee` as password.

![Connecting to the RoPieee AP](images/ropieee-ap.png)

When connected, browse to `http://192.168.250.1` to select your wireless network and enter your password.
The unit will reboot, connect to your production wireless network, and then will continue the installation process.

![Selecting your WiFi network](images/ropieee-ap-connect.png)

### Finish the installation process

During the installation process the unit will reboot a few times. It will also show a fast blinking green LED.

After 15 minutes or so the installation process has finished. This can be seen by looking at the green LED: it should have switched from fast blinking to a steady 'heartbeat' with ½ Hz.

Furthermore you should now be able to reach RoPieee's internal webpage at http://ropieee.local, and see this page:

![Welcome!](images/ropieee-welcome.png)

Congratulations! :muscle: :clap: :notes:

> [!TIP]
> If you can't reach RoPieee's webpage at http://ropieee.local, try to reach the unit directly by using its IP address. You can determine the IP using a port scan application (such as [Fing](https://www.fing.io/)) as  or via your router interface, often in a
DHCP tab.

### General navigation

If you click on **`Continue`** (after you donated of course :wink:), you will see RoPieee's regular webpage. It uses several tabs to group specific settings, so let's walk them through.

## Configuration

### System settings

On the **`System`** tab you can configure the **Device Name** and **Timezone**. The device name (by default `ropieee`) is the name with which your RoPieee unit identifies on your network, and how you can reach it in a browser (via http://ropieee.local, where `ropieee` is the device name). 

If you only have one RoPieee unit in your network, then there's no real need to change its name. If you're running more than 1 unit, it is required to change its name to something unique. Don't use spaces in the device name.

The timezone is used internally by RoPieee. There's no need to change this, unless your using an additional display (TODO).

Once you **Apply** the changes, RoPieee will save the changes made and will show a popup stating that you need to run a configure step. 

> [!IMPORTANT]
> The changes made are only going to be effected after running the configure step. Depending on the changes, RoPieee can show a follow up notification stating that it requires a reboot. 

### Audio settings

On the `Audio` tab you can configure RoPieee's audio settings. First you can select a audio HAT, if one attached. RoPieee supports an extensive set of HAT's, and is continously updated to support the latest models. You can find the complete HAT over [here](https://github.com/RoPieee/RoPieee/blob/main/CHANGELOG.md)

> [!NOTE]
> Some HAT's support auto detection, which means that RoPieee is able to detect them during installation. They will be configured automagically.

## Advanced topics

### About native DSD support

RoPieee supports many USB DAC's out-of-the-box, as its interface is standardized. 
That's not necessarily the case for DSD: if your USB DAC supports DSD, it's not guaranteed to be supported on RoPieee as well. This is an ommission in the standard, with mixed results as a consequence. DoP (DSD-over-PCM) however, works almost always in these cases.

> [!IMPORTANT]
> Native DSD does not offer any advantages over DoP, except that it uses slightly less bandwith. This often results in a higher maximum sample rate with native DSD vs. DoP.

Over the years we have been able to add native DSD support for many DAC's by patching the RoPieee's underlying Operating System (which is Linux). Here are the DAC's for which RoPieee has added explicit native DSD support:

_Warning: this list does **not** mean that native DSD is only suppported on these DAC's_

| Manufacturer | Model |
| -------------| ----- |
| Amanero | Combo384 USB interface |
| APL | Hi-Fi DSD-MR |
| APL | Hi-Fi DSD-SR |
| Astell&Kern | PEE51
| Audiolab | M-DAC+
| Audiolab | 8300CDQ
| Aune | X1S 32BIT/384 DSD DAC
| AURALiC | VEGA
| AURALiC | Altair G2.1
| Bryston | BDA3
| CH Precision | C1 DAC
| Classé | Delta PRE
| Cyrus | QXR
| Denafrips | Ares DAC
| DIYINHK | DSD DXD 384kHz USB to I2S/DSD
| Eastern El. | MiniMax Tube DAC Supreme
| Furutech | ADL Stratos
| Gustard | DAC-X20U
| HDTA | Serenade DSD
| Hegel | HD12
| Holo Springs | Level 3 R2R DAC
| iFi | Audio micro/nano iDSD
| iFi | Audio Pro iDSD
| JLsounds | I2SoverUSB
| LH Labs | VI DAC Infinity
| M2TECH | Young MkIII
| Matrix | Audio X-Sabre
| Matrix | Audio Mini-i Pro
| Matrix | Audio X-SPDIF 2
| MiniDSP | MCHStreamer
| Mola Mola | DAC
| Mola Mola | Makua
| Mola Mola | Kula
| Mola Mola | Tambaqui
| MSB | Technology
| MSB | Pro USB
| Musical Fidelity | M6x DAC
| Mutec | MC3+ USB
| Mytek | Brooklyn DAC
| Mytek | Brooklyn DAC+
| Mytek | Manhattan DAC
| Nagra | DAC
| NuPrime | uDSD
| NuPrime | DAC-9
| NuPrime | DAC-10
| NuPrime | IDA-16
| OPPO | HA-1
| OPPO | HA-2
| OPPO | UDP-205
| OPPO | Sonica
| PS Audio | NuWave DAC
| Quad | Vena 2
| Rotel | DAC
| TEAC | UD-503
| Topping | DX7s
| Singxer | F-1 converter board
| SMSL | M8A
| SMSL | M100
| SMSL | M300 MkII
| Unison Research | Unico CD Due
| Wyred 4 Sound | DAC-2 DSD
| Wyred 4 Sound | DAC-2v2SE



