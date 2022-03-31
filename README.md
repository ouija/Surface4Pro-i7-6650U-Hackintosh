# Surface4Pro-i7-6650U-Hackintosh
**Hackintosh Installation Guide for the Surface 4 Pro i7-6650U**

Please consider [donating](https://paypal.me/djouija) to support this project. Thanks!

## Preface
This is an expermential project, using latest version of macOS Monterey 12.3 with OpenCore 0.7.9.
Installation successfull using `EFI_Install` files.
Note USB Hub with External USB Keyboard and Mouse needed to complete the installation.

## Hardware Specs
- Intel Core i7-6650U (Skylake)
- Intel Iris Graphics 540 Pro
- Marvell AVASTAR Wireless AC Network Controller [Unsupported]
- Realtek HD Audio (10EC:0298)
- Intel Precise Touch & Stylus (IPTS) Touchscreen [Unsupported]
- Surface Pro 4 Type Cover (QC7-00001)

## OpenCore Configuration Notes
- OpenCore using SMBIOS Definition **MacBookPro14,2** 
- Using `HfsPlus.efi` instead of `OpenHfsPlus.efi`
- `AppleIntelLpssI2CController` will have timeout and connection issues without porperly patched `SSDT-GPIO.aml`
  - Alternatively, patched version of `SSDT-XOSI.aml` may be used instead of `SSDT-GPIO.aml`
- Using `USBInjectAll.kext` and `XhciPortLimit` patch may cause issues with `AppleIntelLpssI2CController`; Not enabled.
- Used [Dortainia Guide](https://dortania.github.io/OpenCore-Install-Guide/config-laptop.plist/skylake.html) to configure and originally found SSDTs [here](https://dsdt-database.monster/surface-pro-4-core-i7-opencore/)
- Installation completed but system currently crashing after 'welcome' screen in macOS; Likely due to invalid gfx settings.
  - Remove `device-id` and `AAPL,ig-platform-id` allowed the initial configuration to complete, but only 19mb being reported for Iris 540 and no accelleration.
  - After installation, restored config and graphics accelleration working, but slowdown and performance issues.
  - Enable secure boot: https://github.com/badstorm/surface-pro-7-opencore/blob/master/SecureBoot.With.Grub.md


## Final Thoughts
Not a huge fan of how Monterey is performing on this unit, given the issues with Intel Iris 540 Pro not rendering YouTube and constantly slowing to a crawl after a few minutes of use, and it sucks that the IPTS (Touchscreen) AND the Marvell WLAN are unsupported.   I managed to get the [D-Link DWA-181](https://www.bestbuy.ca/en-ca/product/d-link-ac1300-wi-fi-dual-band-usb-adapter-dwa-181/13579247) working with [this driver](https://github.com/chris1111/Wireless-USB-OC-Big-Sur-Adapter) but using the only available USB port on this device is also more of a dealbreaker with me in wanting to continue with this project...  

**I'd rather use the partition space for [FydeOS](https://fydeos.io/download/device/surface-pro4) instead!**
