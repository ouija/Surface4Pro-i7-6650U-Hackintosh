# Asus-S510UA-DS71-Hackintosh
**Hackintosh Installation Guide for the Surface 4 Pro i7-6650U**

Please consider [donating](https://paypal.me/djouija) to support this project. Thanks!

## Preface
This is still a work in progress, using latest version of macOS Monterey 12.3 with OpenCore 0.7.9.
Installation successfull using `EFI_Install` files.
Note USB Hub with Keyboard and Mouse needed to complete the installation.

## Hardware Specs
- Intel Core i7-6650U (Skylake)
- More to come

## OpenCore Configuration Notes
- SMBIOS Definition set for **MacBookPro14,2** which closely matches the hardware of Surface Pro 4.
- Using `HfsPlus.efi` instead of `OpenHfsPlus.efi`
- `AppleIntelLpssI2CController` will have timeout and connection issues without porperly patched `SSDT-GPIO.aml`
  - Alternatively, patched version of `SSDT-XOSI.aml` may be used instead of `SSDT-GPIO.aml`
- Using `USBInjectAll.kext` and `XhciPortLimit` patch may cause issues with `AppleIntelLpssI2CController`; Not enabled.
- Used Dortainia Guide to configure and originally found SSDTs (from here)[https://dsdt-database.monster/surface-pro-4-core-i7-opencore/]
