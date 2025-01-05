# GTM Container, Tags for WhatsApp Tracking Home

# 🛠️ Remote Services | Serviços remotos

🇺🇸 - If you wish, [we can track you](https://academiadetrackeamento.com.br), just hire our services via the email below.
<br>
🇧🇷 - Se desejar, podemos [fazer o seu trackeamento](https://academiadetrackeamento.com.br) basta contratar nossos serviços através do email abaixo.
<br>
✉️ - Endereço EXCLUSIVO para contratação de serviços: raylan.gig@gmail.com.

# Basic Info

Note|Description
:----|:----
Supported GTM Side|Web and Server.

- Current tagging server version: 2.4.0
- Release date: 05/01/2025

# Basic Steps

1. Include necessary variables (userData, Geolocation, Cookies);
2. Review the special notes;
3. Generate a Webhook URL in n8n
4. Adjust key value in GA4 tag

# Features
- [x] Basic tags, very light and clean for your tracking.
- [x] Built with the latest versions of Google Tag Manager

# TAG's included (**Required**)

TAG|Description
:----|:----
[HTTP Request](https://github.com/stape-io/json-http-request-tag)|Required to send requests to n8n
Google Analytics: evento do GA4|Use the standard tag or use a [Stape GA4 Advanced tag](https://github.com/stape-io/ga4-advanced-tag).

# Other (not included)

Triggers, variables and folders

### Trigger
Trigger|Description
:----|:----
[gtm.dom / visitor-api-success]|Triggered when loading the visitor-api-success event in order to capture the visitor's geolocation data
[WhatsAppTrackingTag]|Same name used at the GA4 event.

### Variables
Variable|Description
:----|:----
First-party cookie|Store fixed data
Custom JavaScript|capture data from input fields on the form
DataLayer Variable|capture geolocation data

### Extract the selector from the form fields

Open DevTools and select the field
```
Right-click/inspect
```

# Attention

Update **config.plist** in PlatformInfo > Generic with YOUR informations.
<br><br>
*1. MLB (Board Serial)
<br>
2. ROM (Mac Address)
<br>
3. SystemSerialNumber (Serial)
<br>
4. SystemUUID (SmUUID)*

Please use [*genSMBIOS*](https://github.com/corpnewt/GenSMBIOS/archive/refs/heads/master.zip) for generate values for above itens.
<br>
Please use [*ProperTree*](https://github.com/corpnewt/ProperTree/archive/refs/heads/master.zip) for configure/edit your config.plist.

# Compatible SMBIOS

SMBIOS|Description
:----|:----
MacPro7,1|Because GPU integrated in 12th gen without support for Apple.
iMacPro1,1|Because GPU integrated in 12th gen without support for Apple.

# Catalina and older versions of macOS

- Please configure `MinDate` and `MinVersion` in UEFI > APFS to `-1`;
- Please configure `SecureBootModel` in Misc > Security to `j137`;

\* *Without above settings, macOS will not be able to boot.*

# macOS Sonoma 14.4 or above versions (including macOS Sequoia (v15))
- Please configure `SecureBootModel` to `Disabled`;
- After the installation is completed, you can return the value to 'Default';
- If the above adjustment is not performed, the installation will be in a looping.

# Special notes

- USB port mapping is **REQUIRED**.
- **`XhciPortLimit`** - Please `**ENABLE**` to map the USB ports
	- You can use USBMap.command Utility - [USBMap](https://github.com/corpnewt/USBMap).
- **`AppleXcpmCfgLock`** - Please **`ENABLE`** if you cannot disable`CFG-Lock` in BIOS.
- Does NOT SUPPORT iGPU in 12th Gen.
- You NEED dGPU (dedicated/discrete GPU (eg. RX 560, 570, 580, 590, RX 5700 XT, etc).
- **`SetupVirtualMap`** - Please **`ENABLE`** if you stuck in Early boot.
- **`EnableWriteUnprotector`** - Please **`ENABLE`** if you get a Kernel Panic while booting macOS Installer.

# Special notes [DeviceProperties > Add]

- PLEASE EDIT/ADD DEVICE FOR ETHERNET i225 (You can identify with Hackintool on `PCIe` tab).
	- If your board didn't ship with the Intel I225 NIC, there's no reason to add this entry.
	- If you get a kernel panic on the `AppleIntelI210Ethernet` kext, your Ethernet's path is likely `PciRoot(0x0)/Pci(0x1C,0x4)/Pci(0x0,0x0)`.
	- Please **`ENABLE`** Patch for i225 on `Kernel > Patch`.
	- for macOS Monterey 12.2.1 and below, please add `dk.e1000=0` in `boot-args`.
	- for macOS Monterey 12.3 or newer, please add `e1000=0` in `boot-args`.
	- for macOS Ventura, please add `e1000=0` in `boot-args` and add Kext [AppleIntelI210Ethernet.kext](https://github.com/luchina-gabriel/youtube-files/raw/main/AppleIntelI210Ethernet.kext.zip)

### GPU-Specific `boot-args`
Parameter|Description
:----|:----
agdpmod=pikera|Used for disabling board ID checks on Navi GPUs(RX 5000 series & RX 6000 series), without this you'll get a black screen.<br>**Don't use if you don't have Navi** (ie. Polaris and Vega cards shouldn't use this).

### Ethernet (Intel i225) `boot-args`
Parameter|Description
:----|:----
dk.e1000=0|Disables `com.apple.DriverKit-AppleEthernetE1000` (Apple's DEXT driver) from matching to the Intel I225-V Ethernet controller found on higher end Comet Lake boards, causing Apple's I225 kext driver to load instead.<br>This boot argument is optional on most boards as they are compatible with the DEXT driver. However, it is required on Gigabyte and several other boards, which can only use the kext driver, as the DEXT driver causes hangs.<br>You don't need this if your board didn't ship with the I225-V NIC.
e1000=0|for macOS 12.3.1 or newer<br>Disables `com.apple.DriverKit-AppleEthernetE1000` (Apple's DEXT driver) from matching to the Intel I225-V Ethernet controller found on higher end Comet Lake boards, causing Apple's I225 kext driver to load instead.<br>This boot argument is optional on most boards as they are compatible with the DEXT driver. However, it is required on Gigabyte and several other boards, which can only use the kext driver, as the DEXT driver causes hangs.<br>You don't need this if your board didn't ship with the I225-V NIC.

# BIOS Settings

### Disable
- Fast Boot
- Secure Boot
- Serial/COM Port
- Parallel Port
- VT-d (can be enabled if you set `DisableIoMapper` to YES)
- Compatibility Support Module (CSM).
- Thunderbolt(For initial install, as Thunderbolt can cause issues if not setup correctly)
- Intel SGX
- Intel Platform Trust
- CFG Lock (MSR 0xE2 write protection)
	- This must be off, if you can't find the option then **`ENABLE`** `AppleXcpmCfgLock`. 
	- Your hack will not boot with `CFG-Lock` enabled.

### Enable
- VT-x
- Above 4G decoding. 
	- This must be on, if you can't find the option then add `npci=0x2000` to `boot-args`. 
	- Do not have both this option and `npci` on `boot-args` enabled at the same time.
	- When enabling Above4G, Resizable BAR Support may become an available on some motherboards. Please ensure this is **`DISABLED`** instead of set to Auto.
- Hyper-Threading
- Execute Disable Bit
- EHCI/XHCI Hand-off
- OS type: Windows 8.1/10 UEFI Mode
- SATA Mode: AHCI

# References
https://dortania.github.io/OpenCore-Install-Guide/config.plist/comet-lake.html
<br>
https://dortania.github.io/Getting-Started-With-ACPI/

## Discord - Universo Hackintosh
- [Access Discord](https://discord.universohackintosh.com.br)
