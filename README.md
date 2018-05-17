# android_vendor_huawei_eva

# lynxis' notes about the files

I've taken a short look on the following files:

- proprietary
- root
- system

# system

- `./system/priv-app/GeofenceLocation/GeofenceLocation.apk`
 - GeoFencing
 - i dont need GeoFencing ;)
 - **remove**

# root

## root/sbin

- `./root/27c11b57-14ff-48bf-abbe-92e345092278.sec`
 - high entropy
 - encrypted or compressed?
 - who is using this?
 - firmware for a core?

- `./root/sbin/hdbd`
 - contains an ssh public key
 - what is libminijail?
 - have strings like 993e26b8-0273-408e-98d3-60c997c37121.sec
 - another debug daemon?
 - has path /dev/socket/oeminfo_nvma
 - hdb stands for high silicon debug?
 - connecting to it via usb?
 - **remove**

- `./root/sbin/hw_healthd`
 - looks at battery/charger
 - display brightness
 - controls the power management?
 - can it be removed?

- `./root/sbin/hw_ueventd`
 - switches the usb mode
 - **can it be removed?**

- `./root/sbin/oeminfo_nvm_server`
 - seems another debug daemon
 - **can it be removed?**

- `./root/sbin/teecd`
 - Links to booringssl
 - do profiling/tracing
 - use `/res/native_packages.xml`
 - runs as service
 - TRUSTZONE
 - a lot debug stuff in there
 - **should be removed**

# proprietary

## proprietary/bin

- `proprietary/bin/79b77788-9789-4a7a-a2be-b60155eef5f4.sec`
 - high entropy. look like the same as ./root/27c11b57-14ff-48bf-abbe-92e345092278.sec
 - who is using this?
 - cryptosms?

- `proprietary/bin/dts_hpx_service`
 - links to
  - libdts_hpx_service_c.so
  - libmedia
  - libbinder
  - [..]
 - dts means sound?
 - /data/misc/dts/hpx

- `proprietary/bin/fingerprintd`
 - links to
  - libperfhub_client.so
  - libc++.so
  - libkeystore_binder.so
  - libhardware.so
  - libbinder.so
 - loads as module hw/fingerprint.hw.ex.so

- `proprietary/bin/gatekeeper`
 - TRUSTZONE
 - could be compiled with opensource

- `proprietary/bin/imonitor`
 - a debug app?
 - collects crash dumps
 - has iunteresting paths
 - **remove**

- `proprietary/bin/keystore`
 - can it be replaced by opensource?hex

## proprietary/etc/dts/*

This seems to be some hardware config or firmware for the voice routing?

## proprietary/etc/global/*

Seems to have only data about operatos/network. including mcc, mnc, voicemal,...

## proprietary/etc/lib{,64}/*

Lots of lots library. Is it really not possible to build more than half out of AOSP?

## proprietary/usr/keylayout

- `fingerprint.kl`
 - Adds key bindings for fingerprint sensors
- `usbaudio.kl`
 - Adds key bindings for media buttons [volume up/down/mute/stop/next/play_pause/previous]

## proprietary/usr/keychars

- `proprietary/usr/keychars/Vendor_18d1_Product_5018.kcm`
 - headline Key character map for Google Pixel C Keyboard
 - is this really the pixel C\'s map?

## proprietary/usr/idl/*

- Seems to be settings for the touch screen drivers

## proprietary/emu/*

- EMUI is the UI of huawei
- should be completely removed
- which applications are using this?
