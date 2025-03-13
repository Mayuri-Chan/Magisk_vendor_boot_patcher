# Magisk Vendor Boot Patcher

This script is for device which doesn't have init_boot partition, and the init_boot ramdisk is stored in vendor_boot.
This script patches a vendor boot image to enable rooting with Magisk.

## Usage

```bash
./patch.sh [options] <vendor_boot.img>
Options
--help: Show this help message and exit.
--no-verity: Disable verity.
--no-forceencrypt: Disable forceencrypt.
--target-arch <arch>: Specify target arch (x86, x86_64, arm, arm64).
                      Default is the same as host arch.
                      This is useful when patching vendor boot image for a different device.
```

## Example
### Termux (Recommended)
> ⚠️ Playstore version of termux is not supported
```bash
./patch.sh vendor_boot_OS2.0.1.0.VNQIDXM.img
```

### Linux
```bash
./patch.sh --target-arch arm64 vendor_boot_OS2.0.1.0.VNQIDXM.img
```

## Prerequisites
- jq
- cpio
- wget

## Steps
- Download the script and make it executable:
- Run the script with the vendor boot image as an argument:
- The script will prompt you to select a Magisk version (Stable, Beta, Canary, or Custom).
- The script will download Magisk, extract the necessary files, patch the ramdisk, and repack the vendor boot image.
- The patched vendor boot image will be located at `<vendor_boot>-patched-<random>.img`.

## Flashing Instructions
- Reboot to bootloader.
- Flash the patched image to the vendor_boot partition:
```bash
fastboot flash vendor_boot <vendor_boot>-patched-<random>.img
fastboot reboot
```
- Install Magisk Manager APK.

## Notes
- Make sure you have the correct vendor boot image for your device.
- This script is provided as is, without any warranty. Use it at your own risk.
