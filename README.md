EDK2 for Samsung Galaxy A72.

Based on zhuowei's commits for Pixel3XL - https://github.com/Pixel3Dev/edk2-pixel3

## Status
Boot Windows10 PE: boot.wim loads fine. winload.efi gives error 0xc000000d(Fatal error transitioning to the operating system.)

2022-2-8 Source of 0xc000000d error is function EfiGetNtStatusCode in winload.efi. This error means efi error code 0x8000000000000002(EFI_INVALID_PARAMETER)

## Working
UFS Storage (using UFSDxe from edk2-sdm845-binary)

## WARNING

**DO NOT EVER TRY TO PORT IT TO *SONY* and *GOOGLE* DEVICES**

**YOUR UFS WILL BE WIPED CLEAN!!!**

## Building
Tested on:

Ubuntu 20.04 (WSL2)

Ubuntu 18.04 arm64 (android chroot)

Setup
```
git clone https://github.com/map220v/edk2-a72q
git clone https://github.com/tianocore/edk2.git --recursive --depth 1
sudo apt install build-essential uuid-dev iasl git nasm python3-distutils gcc-aarch64-linux-gnu abootimg
cd edk2-a72q
./firstrun.sh
```
Build
```
./build.sh
```
Flash
```
heimdall flash --BOOT boot-a72q.img
```

# Credits

SimpleFbDxe screen driver is from imbushuo's [Lumia950XLPkg](https://github.com/WOA-Project/Lumia950XLPkg).

`fxsheep` for his original `edk2-sagit`

`strongtz` for maintaining Renegade Project
