# OpenCore EFI

![About This Mac](./images/AboutThisMac.png "About This Mac")


 **OpenCore EFI for Intel Alder Lake**

- Intel i9-12900K (All cores (P+E+HT) activated)
- Gigabyte Z690 Aorus Elite DDR4 AX (BIOS version F21)
- AMD Radeon RX 580 8GB dGPU
- 64 GB DDR4-3000, XMP enabled
- Wifi/BT via BRCM20702
- Windows 11 23H2 on a 2nd SSD
- MacOS Sonoma 14.0 on a 3rd SSD
- Windows 11 23H2 hosted in VMWare Fusion

**[OC Version 1.0.1](https://github.com/acidanthera/OpenCorePkg/releases/tag/1.0.1)**

# What is working?

**Almost everything:**
  
- MacOS Sonoma 14.6.1
- Audio  
- DP and HDMI via dGPU  
- Screen 1: 4k via DP  
- Screen 2: 1080p via HDMI  
- DRM Content (Netflix, Amazon Prime, Apple TV+)  
- Wifi/BT working after OCLP root patching  
	After the updates/upgrades/patching I set *Secure Boot Model* to **Default** in order to use VMWare Fusion again.
- all iServices (iMessage, iCloud, AirDrop, unlock with Apple Watch)  
- CPU temperature and fan speeds in iStats and/or Intel Power Gadget  
- USB Ports mapped: 15 in use out of 21 possibly available  
  - 2x USB 2.0 on the front panel via internal USB header (one port in USB mapping)  
  - 4x USB 2.0 on the back (one port in USB mapping)  
  - 1x RGB Fusion 2.0  
  - 2x USB 3.2 Gen 1 on the front via internal USB header  
  - 2x USB 3.2 Gen 2 on the back  
  - 3x USB 3.2 Gen 1 on the back     
	- 3x with USB 2.0 personality (to connect WebCam via KVM switch to monitor and to connect IPad to the hackintosh). 
  - 2x USB-C (one back and front with up to 10 Gbps)  
- Continuity Camera with iPhone 15 Pro Max  

# Used Kexts?

| **Kext**  | **Version**  |
|:----------|:----------|
| [Lilu](https://github.com/acidanthera/Lilu/releases/tag/1.6.8)    | 1.6.8
| [AppleALC](https://github.com/acidanthera/AppleALC/releases/tag/1.9.1)| 1.9.1
| [WhateverGreen](https://github.com/acidanthera/WhateverGreen/releases/tag/1.6.7)    | 1.6.7
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases/tag/1.3.3)    | 1.3.3
| [SMCProcessor](https://github.com/acidanthera/VirtualSMC/releases/tag/1.3.3)    | 1.3.3
| [SMCSuperIO](https://github.com/acidanthera/VirtualSMC/releases/tag/1.3.3)    | 1.3.3
| [CpuTopologyRebuild](https://github.com/b00t0x/CpuTopologyRebuild/releases/tag/1.1.1)    | 1.1.1
| [CpuTscSync](https://github.com/acidanthera/CpuTscSync/releases/tag/1.1.1)    | 1.1.1
| [NVMeFix](https://github.com/acidanthera/NVMeFix/releases/tag/1.1.2)    | 1.1.2
| [LucyRTL8125Ethernet](https://www.insanelymac.com/forum/files/file/1004-lucyrtl8125ethernet/)    | 1.1.0
| [RadeonSensor](https://github.com/aluveitie/RadeonSensor/releases/tag/0.3.3) | 0.3.3
| [RestrictEvents](https://github.com/acidanthera/RestrictEvents/releases/tag/1.1.4) | 1.1.4
| [CPUFriend](https://github.com/acidanthera/CPUFriend/releases/tag/1.2.8) | 1.2.8
| [AMFIPass](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Acidanthera/AMFIPass-v1.4.0-RELEASE.zip) | 1.4.0
| [BlueToolFixup](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Acidanthera/BlueToolFixup-v2.6.8-RELEASE.zip) | 2.6.8
| [IOSkywalkFamily](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IOSkywalkFamily-v1.1.0.zip) | 1.1.0
| [IO80211FamilyLegacy](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IO80211FamilyLegacy-v1.0.0.zip) | 1.0.0
| [AirPortBrcmNIC](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IO80211FamilyLegacy-v1.0.0.zip) | 1.0.0


# Motivation?

I set up my first hack based on a **AMD Ryzen 9 3900X** and a **Gigabyte X570 Aorus Elite** mainboard. After having the USB mapped as expected, that hack was working well over the years. Survived the updates to Monterey and Ventura w/o issues. But with Venturae more and more software was not working any longer. So, I was running into more issues with **Photoshop** and **Virtualbox** was not working any longer at all. Especially Virtualbox was needed to get UEFI Secure Boot working since I used Debian to sign the OpenCore EFI files.  
After that I decided to switch to Intel by just replacing the mainboard and CPU.

# What doesn't work well?

Sleep at all, I guess. Haven't had the chance to get into sleep yet.

# Current State?

No issues currently seen.

# Outlook?

No plans except updates.


# Followed Guides?

1. Followed the Comet Lake guide provided by Dorania: 
[Dortania Team](https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html)

2. Alder Lake adaptations done according to: [ChrisWayg](https://chriswayg.gitbook.io/opencore-visual-beginners-guide/advanced-topics/using-alder-lake)

3. Root patching using OCLP [perez987](https://github.com/perez987/Fenvi-wifi-back-on-macOS-Sonoma-by-OCLP/blob/main/README.md)  
	

````text
Before just copying a config.plist from the internet go through the guids and start from skratch  
with the sample.plist provided by Dortania by your own and take that just for reference.
````  

# Disclaimer

I don't take guarantee for any hack based on that config. You do that on your own risk!

# Thanks/Credits

Since I've followed the two guides mentioned above, thanks to these guys!