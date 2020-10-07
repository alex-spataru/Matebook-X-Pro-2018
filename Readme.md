# Huawei Matebook X Pro (2018 Edition)
[![Model](https://img.shields.io/badge/Model-MACH_W29-orange)](https://consumer.huawei.com/it/support/laptops/matebook-x-pro/)
[![BIOS](https://img.shields.io/badge/BIOS-1.28-red)](https://consumer.huawei.com/it/support/laptops/matebook-x-pro/)
[![LICENSE](https://img.shields.io/badge/License-MIT-purple)](/LICENSE)
[![Release](https://img.shields.io/badge/Download-Releases-blue.svg)](https://github.com/profzei/Matebook-X-Pro-2018/releases)
[![Wiki](https://img.shields.io/badge/Support-Wiki-green.svg)](https://github.com/profzei/Matebook-X-Pro-2018/wiki)

### macOS on Huawei Matebook X Pro 2018
<p align="center">
<img src="/Wiki/Images/matebook-x-pro-big-sur.png" alt="Huawei Big Sur 11.0" />
</p>

#### This repo is currently compatible with macOS Catalina 10.15.7 (19H2) and OpenCore 0.6.1
|     macOS Catalina     |       macOS Mojave       |
|------------------------|--------------------------|
|     10.15.7  (19H2)    |       10.14.6  (18G87)   |
|     10.15.6  (19G2021) |       10.14.5  (18F132)  |
|     10.15.5  (19F101)  |       10.14.4  (18E226)  |
|     10.15.4  (19E287)  |       10.14.3  (18D42)   |
|     10.15.3  (19D76)   |       10.14.2  (18C54)   |
|     10.15.2  (19C57)   |       10.14.1  (18B75)   |
|     10.15.1  (19B88)   |       10.14    (18A389)  |
|     10.15    (19A583)  |                          |

#### Preparation for macOS Big Sur 11.0 is [on the way](https://github.com/profzei/Matebook-X-Pro-2018/wiki/Upgrade-to-macOS-Big-Sur)

#### DISCLAIMER
Read the entire README before you start.
I am not responsible for any damages you may cause.  
Should you find an error or improve anything — whether in the config or in the documentation — please consider opening an issue or pull request.
If you find this bootloader configuration useful, consider **giving** it **a star** to make it more visible.

### Status: Work in Progress

This repo contains information for getting macOS 10.15.x Catalina working on a **Huawei MateBook X Pro (2018 Edition)** laptop.

This is intended to create a "fully" functional (as far as possible) hackintosh for the Huawei Matebook X Pro. There are some well-written guides ([here](https://dortania.github.io/getting-started/)), so it's not a particular issue getting macOS installed onto my MBXP; but the reason why I didn't stop my efforts into resolving each bug, there was because of "minor issues" I ran into. The installation is not perfect yet since it's a continuos work-in-progress, but I'm glad to say that **I learned a lot** in the meantime.

The compatibility is good for the most part, most of the stuff works like it would on a real MacBook, including camera, audio, touchpad, iCloud services. The experience is pleasant, as the laptop is smooth and responsive under macOS Catalina. Battery life is quite great (from personal experience it lasts from 8 to 10 hours for light works depending on its age with a behaviour very similar to Windows 10). The Intel WiFi card is soldered onto the motherboard, which means it can't be replaced with a Broadcom one, but the Intel card is now functional albeit not operating at full speeds - I am getting 50/10 mbit up/down on a 200/20 connection, which is fine for most use cases. With the latest `itlwm.kext` even Handoff and Continuity features are working, except for AirDrop. 

**This repository is for personal purposes**


## Configuration

| Specifications      | Details                                          |
| :--- | :---|
| Computer model      | Huawei Matebook X Pro 2018 Space Gray            |
| Processor           | Intel Core i7-8550U Processor @ 1.8 GHz          |
| Memory              | 8 GB LPDDR3 2133 MHz                             |
| Hard Disk           | LiteON SSD PCIe NVMe 512 GB [CA3-8D512]          |
| Integrated Graphics | NVIDIA GeForce MX150 / Intel(R) UHD Graphics 620 |
| Screen              | JDI 3k Display @ 3000 x 2000 (13.9 inch)         |
| Sound Card          | Realtek ALC256                                   |
| Wireless Card       | Intel Dual Band Wireless-AC 8265/8275            |
| Bluetooth Card      | Intel Bluetooth 8265/8275                        |


## Changelog

#### 2020 - October - 06
<details>
<summary>Show more</summary>

#### Current status:
- **10-06-2020**

    Add a new section in [Wiki](https://github.com/profzei/Matebook-X-Pro-2018/wiki/Activate-Surround-Sound-via-MIDI-on-internal-speakers) for activating **surround sound** via MIDI on internal speakers with support for **native audio shortcuts**

- **10-04-2020**

    **Update**
    - Update `SSDT-FnKey.aml` for switching Command - Option keys

    **OpenCore**
    - Update `config.plist` to support OpenCore v. 0.6.2

- **09-30-2020**

    - Support for Big Sur Beta 9 (20A5384c)
    - Added macOS Boot chime support: disabled by default, set `PlayChime` and `AudioSupport` to `True` if you want it. Boot chime was upsampled by @tylernguyen using Audacity: this upsampled file will be used until `AudioDxe.efi` can upsample audio on the fly.

- **09-25-2020**

	Update to macOS Catalina 10.15.7 (19H2)

- **09-23-2020**

    Support for Big Sur Beta 8 (20A5374i)

- **09-21-2020**

    **Update**
    - Update `SSDT-EC-USBX.aml`: improved ACPI Darwin detection in `USBX` device

- **09-20-2020**

    **Update**
    - Update `Network` section with new instructions for `AirportItlwm` using `OC Force` (i.e. forcing injection of `IO80211Family.kext`)

    **OpenCore**
    - Update [config] `Force` section with `IO80211Family.kext` code to support proper loading for `AirportItlwm`

- **09-19-2020**

    **OpenCore**
    - Update `config.plist` to support OpenCore v. 0.6.2

- **09-18-2020**

    **Update**
    - Update [kext] `itlwm` v. 1.1.0 stable
    - Update `Network` section for supporting `AirportItlwm` beta

    **OpenCore**
    - Update `config.plist` to support `AirportItlwm` beta
    - Add [kext] `AirportItlwm` beta

- **09-15-2020**

    **Update**
    - Add `SSDT-PWRB.aml` for enabling Power Button Device: just press down for 1-2 seconds to shown `Shut Down Dialog`

    **OpenCore**
    - Add [config] 1 binary patch in ACPI section to pair `SSDT-PWRB.aml`:
        - `PWRB._STA to PWRB.XSTA`

- **09-13-2020**

    **Update**
    - Update `OpenCore` v. 0.6.1
    - Update [kext] `Lilu` v. 1.4.7
    - Update [kext] `VirtualSMC` and plugins v. 1.1.6
    - Update [kext] `AppleALC` v. 1.5.2
    - Update [kext] `WhateverGreen` v. 1.4.2
    - Update `SSDT-TPXX.aml` with a better approach for GPI0 pinning (issue [#46 ](https://github.com/profzei/Matebook-X-Pro-2018/issues/46) **still unresolved**! ...wip)

    **OpenCore**
    - Update `config.plist` to support `OpenCore` v. 0.6.1
    - Add [config] 2 binary patches to pair `SSDT-TPXX.aml`:
        - `TPD0._STA to TPD0.XSTA` for touchscreen
        - `TPL1._STA to TPL1.XSTA` for touchpad
    - Add [kext] `EFICheckDisabler`
    - Add [kext] `HibernationFixup` v. 1.3.5
    - Add [kext] `itlwm` v. 1.0.0 stable (enabled by default)

    This release is compatible also with macOS **Big Sur Beta 6**

- **08-27-2020**

    **OpenCore**
    - Update `config.plist` to support `OpenCore` v. 0.6.1

- **08-22-2020**

    **OpenCore**
    - Update `config.plist` to support `OpenCore` v. 0.6.1

    **Update**
    - Updated support for macOS Big Sur Beta 5 (20A5354i) in Wiki section](https://github.com/profzei/Matebook-X-Pro-2018/wiki/Upgrade-to-macOS-Big-Sur): "everything" seems to be working fine!

- **08-20-2020**
    - Initial support for macOS Big Sur Beta 4 (20A5343i): for details and an installation guide, please, refer to [Wiki section](https://github.com/profzei/Matebook-X-Pro-2018/wiki/Upgrade-to-macOS-Big-Sur)

- **08-16-2020**
    - Support for macOS Catalina 10.15.6 Supplemental Update (19G2021)

- **08-15-2020**
    - Update `OpenCore` v. 0.6.0
    - Update `SSDT-BATT-HUAWEI.aml` to support memory management for Thermal Framework
    - Add `SSDT-ADP1.aml` to properly load `AppleACPIACAdapter`
    - Update `SSDT-TPXX.aml`: re-enabled and improved support for touchscreen due to the numerous requests (default option)
    - Add `SSDT-TPXX-NO.aml` (to be renamed in `config.plist` as `SSDT-TPXX.aml`): version for disabling touchscreen
    - Add [kext] `ACPIBatteryManager` for fixing (just for now) the very annoying issue due to flooding messages in `Console.app` -> `kernel PMRD: clamshell closed 0, disabled 0, desktopMode 0, ac 0 sleepDisabled 0` (ThreadID 0x74): atm the switch from `SMCBatteryManager` to `ACPIBatteryManager` has been necessary to obtain maximum system stability and ensure the best possible user experience... I'm not happy about this decision because `ACPIBatteryManager` breaks external battery managers! This is a very old random issue (references can be found [tonymacx86](https://www.tonymacx86.com/threads/lid-sensor-flooding-log-with-clamshellstatechanged.272312/), [reddit](https://www.reddit.com/r/MatebookXPro/comments/bvirux/dat_june_hackintosh_update/?sort=new), [InsanelyMac](https://www.insanelymac.com/forum/topic/342497-help-needed-virtualsmc-causes-periodic-updates-of-clamshell-state/), [gnodipac886's repo](https://github.com/gnodipac886/MatebookXPro-hackintosh/issues/75)). **Any contribute is very welcomed!**

    **OpenCore**
    - Update `config.plist` to support `OpenCore` v. 0.6.0
    - Delete [config] unuseful entries for cleaner structure
    - Add [config] 1 binary patch `AC0_ to ADP1` to pair `SSDT-ADP1.aml`
    - Add [config] 5 binary patches to pair `SSDT-BATT-HUAWEI.aml`:
        - `TPWR.ACUR to TPWR.XCUR (Thermal Batt)`
        - `TPWR.AVOL to TPWR.XVOL (Thermal Batt)`
        - `TPWR.PBSS to TPWR.XBSS (Thermal Batt)`
        - `TPWR.PMAX to TPWR.XMAX (Thermal Batt)`
        - `TPWR.PSOC to TPWR.XSOC (Thermal Batt)`

- **08-07-2020**
	- Update support for `Intel Dual-Band Wireless-AC 8265/8275` card:
        - in section [Network](/Network) instructions and support for the **OpenIntelWireless** project, i.e. `itlwm.kext` and `HeliPort.app`
        - since `itlwm.kext` and `HeliPort.app` are in beta phase, [**pipeline**](https://github.com/1hbb/OpenIntelWireless-Factory/releases) can be used for compiling `itlwm.kext` and `HeliPort.app` with latest changes every 8 hours!
        
    **OpenCore**
    - Update `config.plist` with support for `itlwm` in `Kernel -> Add` section

- **08-03-2020**
	- Update [kext]`AppleALC` v. 1.5.1
	- Update [kext] `CodecCommander` v. 2.7.2
	- Update [kext] `CPUFriend` v. 1.2.1
	- Update [kext] `Lilu` v. 1.4.6
	- Update [kext] `NVMeFix` v. 1.0.3
	- Update [kext] `VirtualSMC` and plugins v. 1.1.5
	- Update [kext] `VoodooPS2Controller` v. 2.1.6
	- Update [kext] `WhateverGreen` v. 1.4.1
	- Update [kext] `IntelBluetoothFirmware` v. 1.1.2

- **07-30-2020**
    - Update `SSDT-EC-USBX.aml` to be compliant with Dortania guide
    - Update [kext] `NoTouchID` v. 1.0.4
    - Update [OC] `config.plist`:
        - improved loading kexts order

- **07-27-2020**
	- Update `SSDT-BATT-HUAWEI.aml`
	- Update [kext] `IntelBluetoothFirmware` v. 1.1.1:
		- udate firmwares to official (Intel) June release
		- fix kernel panic when waking up from sleep (Sleep transition timed out 180 seconds while ...)
		- fix wakeup BT unavailable issue
		- fix some memory leaks
	- Update [kext] `AppleALC` v. 1.5.1 (up to [acidanthera/AppleALC@f07c1f8](https://github.com/acidanthera/AppleALC/commit/f07c1f8c65270f58a50f96bac2588710d0ff7683))
	- Update [kext] `Lilu` v. 1.4.6 (up to [acidanthera/Lilu@28122d0](https://github.com/acidanthera/Lilu/commit/28122d0084dc5fe1b486bd52945160cf5be64d49))
	- Update [kext] `NVMeFix` v. 1.0.3 (up to [acidanthera/NVMeFix@48a0fda](https://github.com/acidanthera/NVMeFix/commit/48a0fda97650fd6a7563d65e479421524685bcee))
	- Update [kext] `VirtualSMC` v. 1.1.5 (up to [acidanthera/VirtualSMC@fab53dc](https://github.com/acidanthera/VirtualSMC/commit/fab53dc600eef3b559c9a99b6cfd598c5f24927e))
	- Update [kext] `VoodooPS2Controller` v. 2.1.6 (up to [acidanthera/VoodooPS2Controller@60a4566](https://github.com/acidanthera/VoodooPS2/commit/60a4566c237f9c39bf38122ec8c0910a388dbe9d))
	- Update [kext] `WhateverGreen` v. 1.4.1 (up to [acidanthera/WhateverGreen@b97c692](https://github.com/acidanthera/WhateverGreen/commit/b97c692aee9672786a181423dd476a05782ba7e9))


- **07-26-2020**
	- Add `SSDT-ALSD.aml` for better support for native Ambient Light Sensor Device
	- Add `SSDT-DTPG.aml` to be compliant with ACPI rules
	- Add `SSDT-TPXX.aml` for enabling proper GPI0 pinning for touchpad device and disabling touchscreen for saving power
	- Update [kext] `VoodooI2C` v. 2.4.3 (smoother behaviour in gestures)
	- Update [kext] `VoodooI2CHID` v. 2.4.3 (smoother behaviour in gestures)
	- Update [OC] `config.plist`:
        - Added `SSDT-ALSD` in `ACPI -> Add` section
        - Added `SSDT-DTPG` in `ACPI -> Add` section
        - Added `SSDT-TPXX` in `ACPI -> Add` section
        - Removed double istance for `VoodooInput` in `Kernel -> Add` section
        - Removed istance for `VoodooPS2Keyboard` in `Kernel -> Add` section
        - Removed istance for `VoodooPS2Mouse` in `Kernel -> Add` section

- **06-23-2020**
	- Support for **OpenCore 0.5.9**
	- Update `SSDT-PLUG-PR.PR00.aml`: better Power Management
    - Update `SSDT-PNLF.aml`
	- Better Sleep support
	- Detailed guide in [Wiki section](https://github.com/profzei/Matebook-X-Pro-2018/wiki/Converting-from-Clover-to-OpenCore) for converting from Clover to OpenCore
		- [script](https://github.com/profzei/Matebook-X-Pro-2018/raw/master/Wiki/Converting_Clover_to_OpenCore.sh) for automated deletion
    - Changed [OC] ProductName to `MacBookPro15,2` for better statistics support
    - Support for dual booting Windows 10 with rEFInd
    - Added a simple black theme for rEFInd bootloader
    - Detailed guide in [Wiki section](https://github.com/profzei/Matebook-X-Pro-2018/wiki/Converting-from-Clover-to-OpenCore) for configuring rEFInd

- **06-01-2020**
	- Update [kext] `Lilu` v. 1.4.5
    - Update [kext] `WhateverGreen` v. 1.4.0
    - Update [kext] `AppleALC` v. 1.5.0
    - Update [kext] `VirtualSMC` and related plugins v. 1.1.4
    - Regression [kext] for a more stability to `VoodooI2C` v. 2.3
    - Regression [kext] for a more stability to `VoodooI2CHID` v. 2.3
	- Update [kext] `VoodooPS2Controller` v. 2.1.5

- **05-31-2020**
    - Add initial support for `Intel Dual-Band Wireless-AC 8265/8275` card:
        - in (new) section [Network](/Network) instructions and support for `AppleIntelWiFi.kext`
        - in (new) section [Network](/Network) instructions and support for a totally automated loader script `IntelKextAutoLoader`
    - Add `ALCPlugFix` for a better support to the switch between the headset and the built-in input [ComboJack & Realtek ALC256](https://github.com/profzei/ALCPlugFix)
</details>

#### Earlier status
- See previous updates [here](Changelog.md)

## Current Status
- Discrete graphics card (NVIDIA GeForce MX150) is not working, since macOS doesn't support Optimus technology
	- Have used `SSDT-DDGPU.aml` to disable it in order to save power.
- Fingerprint sensor is not working
	- Have used `SSDT-UIAC.aml` to disable it in order to save power.
- Intel Wi-Fi (Intel Wireless 8265/8275) is ~~not (yet)~~ working:
	- see in Network section](/Network) for instructions to load [`itlwm`](https://github.com/OpenIntelWireless/itlwm) and [`HeliPort`](https://github.com/OpenIntelWireless/HeliPort) to drive our Intel Wi-Fi card: it is still in beta phase, but with support for WPA/WPA2 and 2.4 - 5 GHz bands
	- see in [Network section](/Network) for instructions to load `AppleIntelWiFi.kext` for enabling our Intel Wi-Fi card: it is still in beta phase, but with support for WPA/WPA2 and 2.4 - 5 GHz bands ~~there is hard work and, therefore, some progress in Intel Wi-Fi support. Hope to see a fully functional `kext` asap.~~
	- Previously I bought a USB Wi-Fi dongle: [tp-link](https://www.tp-link.com/it/support/download/tl-wn823n/?utm_medium=select-local#Driver) TL-WN823Nv3 with macOS updated driver support [Wireless-USB-Adapter Driver](https://github.com/chris1111/Wireless-USB-Adapter-Clover/releases) 

### What's working
- [x] Intel(R) UHD 620 Graphics card  
- [x] Intel(R) Wireless-AC 8265/8265 & Intel(R) Bluetooth
- [x] Audio for Realtek ALC256 card (via AppleALC and layout-id 97)
- [x] Power Management with support for HWP (Intel Speed Shift & Intel SpeedStep)
- [x] Automatic Backlight control (with more granular levels)
- [x] Backlight shortcuts (F1 [brightness level down] - F2 [brightness level up])
- [x] Volume shortcuts (F4 [mute] - F5 [audio level down] - F6 [audio level up])
- [x] Sleep and Wake (or Hibernation)
- [x] Battery support with better memory access
- [x] Headphone jack [2 in 1]  (via ALCPlugFix)
- [x] Speaker (4 Channels) & Internal Mic
- [x] HDMI 2.0 up to two 4K @60 Hz monitors (via LSPCON)
- [x] Native Color Profile for Display JDI 3k
- [x] TouchPad (via GPIO interrupt mode) and native gestures
- [x] Touchscreen
- [x] Updated support for LiteON SSD PCIe NVMe 
- [x] PCI Devices latency support and complete description for System Information app
- [x] USB Ports (Type-A & Type-C) with proper power levels
- [x] Thunderbolt Port
- [x] HD Camera
- [x] NVRAM (via [OcQuirks](https://github.com/ReddestDream/OcQuirks/releases))

## Device Firmware
- Bios version: `1.28`

## Bootloader Firmware
- Default bootloader: `OpenCore 0.6.1` [Official release](https://github.com/acidanthera/OpenCorePkg/releases)
- Alternative bootloader: Clover `r5118` [Official release](https://github.com/CloverHackyColor/CloverBootloader/releases) ~~`r5103` [Dids release](https://github.com/Dids/clover-builder/releases)~~

### OpenCore
- Support macOS10.14 ~ macOS11.0 beta 9
- Should **clean NVRAM** after using `Clover`: press `Space` in OpenCore boot page and then select `Reset NVRAM` entry
- Limited theme with `OpenCanopy`

### Clover
- Support macOS10.14 ~ macOS10.15.7, but **not macOS11+**
- Should **clean NVRAM** after using `OpenCore`: press `Fn + F11` in Clover boot page

## SMBIOS
- Default SMBIOS settings of this repo is `MacBookPro15,2` ~~`MacBookPro14,1`~~

## Post - Install
<details>  
<summary><strong>Enable Apple Services</strong></summary>

Default **SMBIOS** settings of this repo is `MacBookPro15,2` ~~`MacBookPro14,1`~~
1. Launch `Terminal` app
2. Copy the following script, paste it into the `Terminal` window, then press `Enter`
   ```bash
   git clone https://github.com/corpnewt/GenSMBIOS && cd GenSMBIOS && ./GenSMBIOS.command 
   ```
3. Type `2`, then press `Enter`
4. Drag your `config.plist` inside the `Terminal` window
5. Type `3`, then press `Enter`
6. Type `MacBookPro15,2`, then press `Enter`
</details>

<details>  
<summary><strong>Activate Surround Sound via MIDI</strong></summary>

For a detailed guide on how to activate surround sound via MIDI on internal speakers and native audio shortcuts, see [Wiki section](https://github.com/profzei/Matebook-X-Pro-2018/wiki/Activate-Surround-Sound-via-MIDI-on-internal-speakers) 
</details>

## Power management: CPUFriend
CPU power management can be achieved by using `CPUFriend.kext` while `CPUFriendDataProvider.kext` defines how it should be done. `CPUFriendDataProvider.kext` is generated for a specific CPU and power setting. The one supplied in this repository was made for `i7-8550U` and is optimized for balanced performance.
- The kexts and SSDT for `i7-8550U` are [here](/CPUFriend/1.2.0).
- `CPUFriendDataProvider.kext` is generated for SMBIOS `MacBookPro15,2` because of Kaby Lake R architecture.
- `CPUFriend.kext` and `CPUFriendDataProvider.kext` need to be put in `CLOVER/kexts/Other`
- Furthermore, you also need to put `SSDT-XCPM.aml` in `CLOVER/ACPI/patched` for working as normal after awake.

## Power management: Hibernation
Hibernation (suspend to disk or S4 sleep) is not fully supported on a Hackintosh: so it's recommended to disable it.
```
sudo pmset -a hibernatemode 0
sudo rm -rf /private/var/vm/sleepimage
sudo touch /private/var/vm/sleepimage
sudo chflags uchg /private/var/vm/sleepimage
```
Also, it's important to disable the other hibernation related functions.
```
sudo pmset -a standby 0
sudo pmset -a autopoweroff 0
```
Disabling additional features prevents random wakeups while the lid is closed.
```
sudo pmset -a powernap 0
sudo pmset -a proximitywake 0   [optional]
sudo pmset -b tcpkeepalive 0    [optional]
```
After every update, ALL these settings should be reapplied manually.

You can verify yuor power settings by typing in terminal `sudo pmset -g live` . If you ever want to reset these settings: `sudo pmset -a restoredefaults`

## Power management: sleep discharge fix
Sleep function works flawlessly (both via software and via clamshell) thanks to the following improvements:
- "right" choice of framebuffer `C0870005` for Intel(R) UHD 620 Graphics card
- use of attribute `acpi-wake-type` for the USB Controller `PciRoot(0x0)/Pci(0x14,0x0)`
- set `HWPEnable` value to true for SpeedShift CPU support
About power consumption, [HWMonitor](https://github.com/kzlekk/HWSensors/releases) reports for the idle state both before and after sleep phase the same value for "CPU package total" (0.65-0.70 W). Sleep discharge rate is about 1% every 4:30 hours (during night).


## USB port mapping
Proper `SSDT-UIAC.aml` and `SSDT-USBX.aml` are used for USB Host Controller (XHCI-Device-ID: `<2f 9d 00 00>`): these files are configured to map only the necessary ports (tested with IOReg) with the correct connector type and prevent it from shutdown issues.

| Port      | Address               | Physical Location                                         | Internal/External |
| :--- | :--- | :--- | :--- |
| HS01/SS01 | `00000001`/`0000000D` | Left Port type-C (Power Source) - next to 3.5mm jack port | E                 |
| HS02/SS02 | `00000002`/`0000000E` | Right Port type-A                                         | E                 |
| HS03      | `00000003`            | Left Port type-C Thunderbolt                              | E                 |
| HS05      | `00000005`            | Bluetooth USB Port                                        | I                 |
| HS07      | `00000007`            | Integrated HD Camera module                               | I                 |

## Optional

#### Monitor temperatures and power consumption with [HWMonitor](https://github.com/kzlekk/HWSensors/releases) 
This app is relatively old and no longer supported, but it gets the job done.

#### Make dock animation faster and without delay
Run these lines in terminal:
```
defaults write com.apple.dock autohide-delay -float 0
defaults write com.apple.dock autohide-time-modifier -float 0.5
killall Dock
```

#### Graphics section
Refer to: [here](/Graphics/)

## Update tracker

| Item | Version | Remark |
| :--- | :--- | :--- |
| MacOS | 10.15.7 | |
| [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases) | 0.6.1 | Default Bootloader|
| [Clover](https://github.com/CloverHackyColor/CloverBootloader/releases) | 5118 | Alternative (not more supported) Bootloader|
| [Lilu](https://github.com/acidanthera/Lilu/releases) | 1.4.7 | Kext/process/framework/library patcher |
| [WhateverGreen](https://github.com/acidanthera/whatevergreen/releases) | 1.4.2 | Handle Graphics card |
| [AppleALC](https://github.com/acidanthera/AppleALC/releases) | 1.5.2 | Handle/fix onboard audio |
| [CodecCommander](https://github.com/Sniki/EAPD-Codec-Commander/releases) | 2.7.2 | |
| [CPUFriend](https://github.com/acidanthera/CPUFriend/releases) | 1.2.1 | Power management |
| [HibernationFixup](https://github.com/acidanthera/HibernationFixup/releases) | 1.3.5 | |
| [IntelBluetoothFirmware](https://github.com/OpenIntelWireless/IntelBluetoothFirmware/releases) | 1.1.2 | Handle Bluetooth |
| [itlwm](https://github.com/OpenIntelWireless/itlwm/releases) | 1.1.0 | Handle WiFi with HeliPort app |
| NullEthernet | 1.0.6 | |
| [NoTouchID](https://github.com/al3xtjames/NoTouchID/releases) | 1.0.4 | Disable TouchID|
| [NVMeFix](https://github.com/acidanthera/NVMeFix/releases) | 1.0.3 | Fix for NVMe SSDs |
| [VoodooI2C](https://github.com/alexandred/VoodooI2C/releases) | 2.4.3 | Handle I2C device |
| [VoodooI2CHID](https://github.com/alexandred/VoodooI2C/releases) | 2.4.3 | Touchpad I2C satellite |
| [VoodooPS2Controller](https://github.com/acidanthera/VoodooPS2/releases) | 2.1.6 | Enable keyboard, alternative trackpad driver |
| [VirtualSMC + plugins](https://github.com/acidanthera/VirtualSMC/releases) | 1.1.6 | SMC chip emulation |
| [USBInjectAll](https://github.com/Sniki/OS-X-USB-Inject-All/releases) | 0.7.5 | Inject USB ports |

## Development: Catalina 10.15.4 support

- Update `Clover` to r5107+ to support macOS 10.15.4
- Remove [config] `MSR 0xE2` kernel patch because `Clover` can automatically patch
```
	<dict>
		<key>Comment</key>
		<string>MSR 0xE2 _xcpm_idle instant reboot(c) Pike R. Alpha</string>
		<key>Disabled</key>
		<false/>
		<key>Find</key>
		<data>ILniAAAADzA=</data>
		<key>Replace</key>
		<data>ILniAAAAkJA=</data>
	</dict>
```
- Add [config] `setpowerstate_panic=0` kernel patch for macOS 10.15 according to [Acindathera/AppleALC#513](https://github.com/acidanthera/bugtracker/issues/513#issuecomment-542838126)
```
	<dict>
		<key>Comment</key>
		<string>Disable setPowerState panic with setpowerstate_panic=0 boot-args on 10.15 (credit vit9696)</string>
		<key>Disabled</key>
		<false/>
		<key>MatchOS</key>
		<string>10.15</string>
		<key>Find</key>
		<data>Y29tLmFwcGxlAA==</data>
		<key>Replace</key>
		<data>bm90LmFwcGxlAA==</data>
	</dict>
```
- Add [config] `complete-modeset-framebuffers` property to Intel UHD Graphics 620 device section to improve HDMI
```
	<key>PciRoot(0x0)/Pci(0x2,0x0)</key>
	<dict>
		...
		<key>complete-modeset-framebuffers</key>
		<data>AAAAAAAAAAE=</data>
		...
	</dict>
```
- Add [config] `force-online` and `force-online-framebuffers` properties to Intel UHD Graphics 620 device section to fix HDMI on macOS 10.15.4
```
	<key>PciRoot(0x0)/Pci(0x2,0x0)</key>
	<dict>
		...
		<key>force-online</key>
		<data>AQAAAA==</data>
		<key>force-online-framebuffers</key>
		<data>AAAAAAAAAAE=</data>
		...
	</dict>
```

### Fix AppleID issue on macOS Catalina

- If you encounter the problem with AppleID which cannot login and logout, this problem happened on both Hackintosh and Macintosh.
- Fix this issue with the following commands:
```
sudo -v
killall -9 accountsd com.apple.iCloudHelper
defaults delete MobileMeAccounts
rm -rf ~/Library/Accounts
killall -9 accountsd com.apple.iCloudHelper
sudo reboot
```

## Credits

- [Acidanthera](https://github.com/acidanthera)
- [Dortania OC guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [Rehabman's battery patch guide](https://www.tonymacx86.com/threads/guide-how-to-patch-dsdt-for-working-battery-status.116102/) and [Rehabman's ACPI hotpatching guide](https://www.tonymacx86.com/threads/guide-using-clover-to-hotpatch-acpi.200137/)
- [CorpNewt's tools](https://github.com/corpnewt)
- [OpenWireless and itlwm](https://github.com/OpenIntelWireless/itlwm)
- [Daliansky's OC-little repo](https://github.com/daliansky/OC-little)
- [Gnodipac886's MatebookXPro-hackintosh repo](https://github.com/gnodipac886/MatebookXPro-hackintosh): this project was *initially* based on the hard work done by Gnodipac886 guy, but *now* it can be considered as a different project due to **many and original very significant personal improvements in ALL the sections**.
