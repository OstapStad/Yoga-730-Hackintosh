# OpenCore config for installing macOS 12 Monterey on Lenovo Yoga 730-13IKB

# Credits:
- [OpenCore](https://github.com/acidanthera/OpenCorePkg) Boot
- [Lilu.kext](https://github.com/acidanthera/Lilu/releases/latest)
- [OpenCore Install Guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/coffee-lake.html)

# What is half working:
- Active Pen works as mouse
- Brightness control has a dead zone

# What is working:
- Intel Graphic UHD620 inject 0xC0870000 to ig-platform-id, [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases/latest)
- Realtek ALC236 inject "layout-id" 15, [AppleALC.kext](https://github.com/acidanthera/AppleALC/releases/latest)
- PS2 Keyboard [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2/releases/latest)
- TouchPad and TouchScreen work, [VoodooI2C.kext](https://github.com/alexandred/VoodooI2C/releases/latest)
- Battery and CPU sensor, [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC/releases/latest)
- [BrightnessKeys.Kext](https://github.com/acidanthera/BrightnessKeys/releases/latest)
- Camera and microphone work fine
- Hibernation and wake up
- Intel Dual-Band Wireless-AC 8265, [AirportItlwm.kext](https://github.com/OpenIntelWireless/itlwm)
- Intel Bluetooth 4.2, [IntelBluetoothFirmware.kext](https://github.com/OpenIntelWireless/IntelBluetoothFirmware), [BlueToolFixup.kext](https://github.com/acidanthera/BrcmPatchRAM)
# UEFI Setting before install:
- Disable "Intel SGX" (Security -> Intel SGX -> Intel SGX Controller)
- Disable "Secure Boot" (Security -> Secure Boot)
- Switch RAID to AHCI (Configuration -> SATA Controller Mode)

# Misc after install:
- [Enable HiDPI](https://github.com/xzhih/one-key-hidpi):
```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/xzhih/one-key-hidpi/master/hidpi.sh)"
```
- To activate AppleID and other iServices you need to edit the "config.plist" file. Follow [this](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html) guide

# FAQ:
- Q: Touchpad not work on First boot?
  A: Enter command `sudo kextcache -system-prelinked-kernel` in terminal and reboot
- Q: Can't boot Windows when BIOS swtch to AHCI?
  A: Boot Windows in [Safe Mode](https://support.microsoft.com/help/12376)
