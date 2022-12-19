# OpenCoreEFI

 OpenCore EFI for Intel Alder Lake

- Intel i9-12900K
- Gigabyte Z690 Aorus Elite DDR4 AX
- AMD Radeon RX 580 dGPU
- 64 GB DDR4-3000
- Wifi/BT via BRCM20702

# What is working?

Almost everything:
- MacOS Ventura 13.1 Update
- Audio
- DP and HDMI via dGBPU
- DRM Content (Netflix, Amazon Prime, Apple TV+)
- Wifi/BT out of the box
- all iServices (iMessage, iCloud, AirDrop, unlock with Apple Watch)
- CPU temperature and fan speeds in iStats and/or Intel Power Gadget
- USB Ports mapped: 12 in use out of 26 possibly available
  - 2x USB 2.0 on the front panel via internal USB header (one port in USB mapping)
  - 4x USB 2.0 on the back (one port in USB mapping)
  - 1x RGB Fusion 2.0
  - 2x USB 3.1 Gen 2 on the front via internal USB header
  - 5x USB 3.1 Gen 2 on the back   
  - 2x USB-C (each on back/front)

# What doesn't work well?

Usually the hack boots as expected, but sometimes it stucks at the apple logo w/o any progress bar. So rebooting via Reset button is needed. Currently I've no clue why that is happening.

# Current State?

ACPI Patches introduced according to guide 2 for Gigabyte Z690 mainboards since neither mouse nor keyboard were working and restart of the whole system was needed. Has to be observed further if Sleep has killed USB functionality.

# Followed Guide?

1. Followed the Comet Lake guide provided by Dorania:  
[Dortania Team](https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html)

2. Alder Lake adaptations done according to:  
[ChrisWayg](https://chriswayg.gitbook.io/opencore-visual-beginners-guide/advanced-topics/using-alder-lake)

# Thanks/Credits

Since I've followed the two guides mentioned above, thanks to these guys!