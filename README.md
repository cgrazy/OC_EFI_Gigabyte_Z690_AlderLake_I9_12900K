# OpenCore EFI

![About This Mac](./images/AboutThisMac.png "About This Mac")

# Motivation?

I set up my first hack based on a **AMD Ryzen 9 3900X** and a **Gigabyte X570 Aorus Elite** mainboard. After having the USB mapped as expected, that hack was working well over the years. Survived the updates to Monterey and Ventura w/o issues. But with Venturae more and more software was not working any longer. So, I was running into more issues with **Photoshop** and **Virtualbox** was not working any longer at all. Especially Virtualbox was needed to get UEFI Secure Boot working since I used Debian to sign the OpenCore EFI files.  
After that I decided to switch to Intel by just replacing the mainboard and CPU.

# Solution
### OpenCore EFI for Intel Alder Lake**

- Intel i9-12900K (All cores (P+E+HT) activated)
- Gigabyte Z690 Aorus Elite DDR4 AX (BIOS version F21)
- AMD Radeon RX 580 8GB dGPU
- 64 GB DDR4-3000, XMP enabled
- Wifi/BT via BRCM20702
- Windows 11 23H2 on a 2nd SSD
- MacOS Sequoia 15.0 RC on a 3rd SSD
  [Updates](#updates-to-sonoma)
- Windows 11 23H2 hosted in VMWare Fusion

**[OC Version 1.0.2](https://github.com/acidanthera/OpenCorePkg/releases/tag/1.0.2)**

### What is working

#### Almost everything:[[1]](#issues-with-macos-sequoia)
  
- MacOS Sequoia 15.0.1
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


### Used Kexts

| **Kext**  | **Version**  | **Comment** |   
|:----------|:----------|:--|   
| [Lilu](https://github.com/acidanthera/Lilu/releases/tag/1.6.9)    | 1.6.9
| [AppleALC](https://github.com/acidanthera/AppleALC/releases/tag/1.9.2)| 1.9.2
| [WhateverGreen](https://github.com/acidanthera/WhateverGreen/releases/tag/1.6.8)    | 1.6.8
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases/tag/1.3.4)    | 1.3.4
| [SMCProcessor](https://github.com/acidanthera/VirtualSMC/releases/tag/1.3.4)    | 1.3.4
| [SMCSuperIO](https://github.com/acidanthera/VirtualSMC/releases/tag/1.3.4)    | 1.3.4
| [CpuTopologyRebuild](https://github.com/b00t0x/CpuTopologyRebuild/releases/tag/1.1.1)    | 1.1.1
| [CpuTscSync](https://github.com/acidanthera/CpuTscSync/releases/tag/1.1.1)    | 1.1.1
| [NVMeFix](https://github.com/acidanthera/NVMeFix/releases/tag/1.1.2)    | 1.1.2
| [LucyRTL8125Ethernet](https://www.insanelymac.com/forum/files/file/1004-lucyrtl8125ethernet/)    | 1.1.0
| [RadeonSensor](https://github.com/aluveitie/RadeonSensor/releases/tag/0.3.3) | 0.3.3
| [RestrictEvents](https://github.com/acidanthera/RestrictEvents/releases/tag/1.1.5) | 1.1.5
| [CPUFriend](https://github.com/acidanthera/CPUFriend/releases/tag/1.2.8) | 1.2.8
| [AMFIPass](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Acidanthera/AMFIPass-v1.4.1-RELEASE.zip) | 1.4.1
| [BlueToolFixup](https://github.com/acidanthera/BrcmPatchRAM/actions/runs/11143115875) | 2.6.9 | not released
| [IOSkywalkFamily](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IOSkywalkFamily-v1.1.0.zip) | 1.1.0
| [IO80211FamilyLegacy](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IO80211FamilyLegacy-v1.0.0.zip) | 1.0.0
| [AirPortBrcmNIC](https://github.com/dortania/OpenCore-Legacy-Patcher/blob/main/payloads/Kexts/Wifi/IO80211FamilyLegacy-v1.0.0.zip) | 1.0.0

### Updates to Sonoma
- AMFIPass version 1.4.1 taken from [here](https://github.com/dortania/OpenCore-Legacy-Patcher/tree/main/payloads/Kexts/Acidanthera)
- IOSkyWalkFamily version 1.2.0 taken from [here](https://github.com/dortania/OpenCore-Legacy-Patcher/tree/main/payloads/Kexts/Wifi)
- OpenCore Lagacy Patcher 2.0 taken from [here](https://github.com/dortania/OpenCore-Legacy-Patcher/actions/runs/10835044097)  
See [guide](https://github.com/perez987/Fenvi-wifi-back-on-macOS-Sonoma-by-OCLP/blob/main/README.md) to enable WiFi again

#### Issues with MacOS Sequoia  
There are (minor) issues:  
  - bluetoothd process is crashing with:
      
````text  
  Exception Type:        EXC_GUARD  
  Exception Codes:       GUARD_TYPE_USER  
  Exception Codes:       0x6000000000000012, 0x0000000000000002  
[...]
Thread 1 Crashed:  
0   libsystem_kernel.dylib        	    0x7ff80abfb48a os_fault_with_payload + 10  
1   bluetoothd                    	       0x1002b63da 0x1001fa000 + 771034  
2   bluetoothd                    	       0x10067ca6a 0x1001fa000 + 4729450  
3   bluetoothd                    	       0x10067e0af 0x1001fa000 + 4735151  
4   bluetoothd                    	       0x10065c200 0x1001fa000 + 4596224  
5   bluetoothd                    	       0x10065bdea 0x1001fa000 + 4595178  
6   libdispatch.dylib             	    0x7ff80aa88455 _dispatch_call_block_and_release + 12  
7   libdispatch.dylib             	    0x7ff80aa897e2 _dispatch_client_callout + 8  
8   libdispatch.dylib             	    0x7ff80aa8f95b _dispatch_lane_serial_drain + 739  
9   libdispatch.dylib             	    0x7ff80aa903e2 _dispatch_lane_invoke + 377  
10  libdispatch.dylib             	    0x7ff80aa9a0db _dispatch_root_queue_drain_deferred_wlh + 271  
11  libdispatch.dylib             	    0x7ff80aa999dc _dispatch_workloop_worker_thread + 659  
12  libsystem_pthread.dylib       	    0x7ff80ac2dc7f _pthread_wqthread + 326  
13  libsystem_pthread.dylib       	    0x7ff80ac2cbdb start_wqthread + 15  
```` 

~~- WiFi is not connection automatically w/o issue after boot~~~  
~~- About This Mac shows Intel Xeon W CPU even using revcpuname patch.~~
 
### Current State


### Outlook

No plans for updates.


### Followed Guides?

1. Followed the Comet Lake guide provided by Dortania: 
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