# Opencore-HP-Pavilion-Gaming-15-EC2144AX

<B>OpenCore Hackintosh - HP Pavilion Gaming 15-ec2144ax</B>

## Specifications

| Specifications      | Detail                                      |
| ------------------- | ------------------------------------------- |
| Computer model      | HP Pavilion Gaming 15-ec2144ax              |
| CPU                 | Ryzen 5 5600H                               |
| Memory              | 16GB/8GB Crucial / SK Hynix                 |
| SSD	Nvme            | SK Hynix PC711 512 GB Nvme                  |
| SSD SATA 		        | Crucial BX500 SSD 2.5" 240GB 		 	          |
| Dedicated Graphics  | NVIDIA GeForce GTX 1650                     |
| Sound Card          | Realtek ALC295					                    |
| Wireless Card       | Intel® Wireless-AC 9560 802.11b/g/n/ac      |
| Ethernet/LAN        | Realtek RTL8168/8111 PCI-E Gigabit Ethernet |

## Working
- iGPU using NootedRed.kext
- CPU Power Management
- Battery Status / Time
- Ethernet LAN
- Audio Combo Jack
- Keyboard & Media/Function Keys
- Trackpad & Gestures support
- USB Type-A & Type-C ports
- Screen LID sleep
- Screen Brightness & F2/F3 Keys
- And pretty much everything not listed below



## Not Working
- Dedicated Nvidia GPU (Disabled in SSDT)
- HDMI Port output (hooked to the dedicated GPU)
- NVMe Storage (Hynix OEM SSD not supported as mentioned in OpenCore Anti-Hackintosh Guide)

## Kexts
| Kext                                                                                  |  Usage                                                           |
| ------------------------------------------------------------------------------------- |  --------------------------------------------------------------- |
| [AirportItlwm](https://github.com/OpenIntelWireless/itlwm)                            |  Intel Wi-Fi Adapter Kext for macOS                              |
| [AppleALC](https://github.com/acidanthera/AppleALC)                                   |  Native macOS HD audio for not officially supported codecs       |
| [BrightnessKeys](https://github.com/acidanthera/BrightnessKeys)                       |  Handler for brightness keys without DSDT patches                |
| [ECEnabler](https://github.com/1Revenger1/ECEnabler)                                  |  Allows reading Embedded Controller fields over 1 byte long      |
| [Lilu](https://github.com/acidanthera/Lilu)                                           |  Arbitrary kext and process patching on macOS                    |
| [NVMeFix](https://github.com/acidanthera/NVMeFix)                                     |  Set of patches for the Apple NVMe storage driver                |
| [RTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X)                           |  OS X open source driver for the Realtek RTL8111/8168 family     |
| [SMCBatteryManager](https://github.com/acidanthera/VirtualSMC)                        |  Battery Management For Laptops                                  |
| [SMCProcessor](https://github.com/acidanthera/VirtualSMC)                             |  Improved CPU measurement                                        |
| [SMCSuperIO](https://github.com/acidanthera/VirtualSMC)                               |  Measurement of Fans For Laptops                                 |
| [USBToolBox](https://github.com/USBToolBox/kext)                                      |  USB Mapping                                                     |
| [UTBMap](https://github.com/USBToolBox/kext)                                          |  Generated USB Map                                               |
| [VirtualSMC](https://github.com/acidanthera/VirtualSMC)                               |  Advanced Apple SMC emulator in the kernel                       |
| [VoodooPS2](https://github.com/acidanthera/VoodooPS2)                                 |  Controller For various PS2 Gestures                             |
| [VoodooRMI](https://github.com/VoodooSMBus/VoodooRMI)                                 |  A port for macOS of Synaptic's RMI Trackpad driver from Linux   |
| [VoodooSMBUS](https://github.com/VoodooSMBus/VoodooRMI)                               |  VoodooRMI Extension for PS2 Trackpad                            |

## OpenCore
- OpenCore v0.9.7 

## ACPI Patch list
- SSDT-AWAC: System Clock fix
- SSDT-dGPU-Off: Disables dedicated GPU (Optimus Method)
- SSDT-EC-USBX-LAPTOP: Embedded Controller fix
- SSDT-GPRW: Instant wake fix
- SSDT-HP-FixLidSleep: Screen LID Sleep Fix
- SSDT-PLUG-DRTNIA: Power Management Fix
- SSDT-PMC: NVRAM Fix (Optional on H370)
- SSDT-PNLF: Brightness Fix

## Misc information
- Audio Layout ID: 13
- Disable NootedRed.kext when installing (It will cause black screen on bootup). And after installing, Enable it again and reboot.
- USB Port Map: [info](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/e6eb9aa1a21bef35153f1993c7ae1534bd0b33ad)
- Quirks adjusted to fix kernel panic on boot [commit](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/8258d55462a9d0fe94edc516f2be52b85ebb0799)
- XhciPortLimit is broken since MacOS 11.3. The quirk has been disabled to avoid kernel panics.
- Bootup Chime and Theme Enabled
- SMBIOS MacBookPro16,3 is used
- dGPU is disabled via SSDT edit
- iGPU power management is handeled by [Apple GUC](https://github.com/ananjaser1211/Opencore-HP-Pavilion-Gaming-15-cx0056wm/commit/471b26d67147d0fa8871a69b448f73835302dfeb)

## Screenshots
| About this Mac                                                                                                | neofetch                                                                                                      |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |

## Quick Installation
- Follow [OpenCore guide](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) and create a bootable macOS recovery USB
- Download the EFI and place it onto your USB drive
- Boot to OpenCore and setup your disk in Disk Utility

## Dualbooting Notes
- To install along side Windows make sure you have a GPT formatted disk, resize your Windows partition using tools such as Easeus Partition Master then while in macOS Disk Utility, make the unallocated space into APFS
- I also left a 500MB unallocated space for an EFI partition using gparted on Linux earlier I set the ESP / boot flags
- Finally copy the EFI from the repo to your disk EFI partition that you created and boot from it with the F9 key

## Credits
- @1Revenger1 for ECEnabler
- @acidanthera for bootloader, VirtualSMC, NVMeFix, Lilu and other kexts
- @Apple for macOS
- @dortania for guides
- @USBToolBox Team for USB mapping
- @Voodoo Team for TrackPad
