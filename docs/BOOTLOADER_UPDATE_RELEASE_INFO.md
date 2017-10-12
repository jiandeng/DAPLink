# DAPLink bootloader release configurations

| HDK MCU   | Offset 0x8000 | Offset 0x5000 |
|-----------|:-------------:|:-------------:|
|  k20dx    |       x       |       x       |
|  kl26z    |       x       |               |
|  sam3u2c  |       x       |       x       |
|  lpc4322  |               |               |
|  lpc11u35 |               |               |


## Building for offset 0x5000

* Clean or create a fresh clone of DAPLink
* Build the bootloader images
  * Checkout the commit with a small bootloader - 4a0b3d9266f21bfca651df35d68857c5bbd7c4d3 - "Remove features so bootloader fits in 20K"
  * Regenerate projects with project generator `progen generate -t uvision`
  * Build the k20dx bootloader by opening the project `DAPLink\projectfiles\uvision\k20dx_bl\k20dx_bl.uvproj` and building
  * Build the sam3u2c bootloader by opening the project `DAPLink\projectfiles\uvision\sam3u2c_bl\sam3u2c_bl.uvproj` and building
* Build the interface to deliver the bootloader
  * Checkout the commit with the update interface for 0x5000 -  8ee2d1b9d8f5d834d0de1211130c8dcb24e0e1f2 - "Update app offset to 20K"
  * Regenerate projects with project generator `progen generate -t uvision`. **Do not clean or remove the previously built bootloaders**
  * Build the k20dx update image by opening the project `DAPLink\projectfiles\uvision\k20dx_frdmk64f_if\k20dx_frdmk64f_if.uvproj` and building
  * Build the sam3u2c update image by opening the project `DAPLink\projectfiles\uvision\sam3u2c_mkit_dk_dongle_nrf5x_if\sam3u2c_mkit_dk_dongle_nrf5x_if.uvproj` and building
* Take bootloader update images `k20dx_frdmk64f_if_crc_legacy_0x5000.bin` and `sam3u2c_mkit_dk_dongle_nrf5x_if_crc_legacy_0x5000.bin` from their build directory and rename appropriately for release - `0244_k20dx_bootloader_update_0x5000.bin` and `0244_sam3u2c_bootloader_update_0x5000.bin`

## Building for offset 0x8000

* Clean or create a fresh clone of DAPLink
* Checkout the commit with the update interface -  8c28f0668c17127c3161bd04b65cc89121c7076f - "Update interface to only apply an update"
* Regenerate projects with project generator `progen generate -t uvision`
* Build the k20dx bootloader by opening the project `DAPLink\projectfiles\uvision\k20dx_bl\k20dx_bl.uvproj` and building
* Build the sam3u2c bootloader by opening the project `DAPLink\projectfiles\uvision\sam3u2c_bl\sam3u2c_bl.uvproj` and building
* Build the kl26z bootloader by opening the project `DAPLink\projectfiles\uvision\kl26z_bl\kl26z_bl.uvproj` and building
* Build the k20dx update image by opening the project `DAPLink\projectfiles\uvision\k20dx_frdmk64f_if\k20dx_frdmk64f_if.uvproj` and building
* Build the sam3u2c update image by opening the project `DAPLink\projectfiles\uvision\sam3u2c_mkit_dk_dongle_nrf5x_if\sam3u2c_mkit_dk_dongle_nrf5x_if.uvproj` and building
* Build the sam3u2c update image by opening the project `DAPLink\projectfiles\uvision\kl26z_microbit_if\kl26z_microbit_if.uvproj` and building
* Take bootloader update images `k20dx_frdmk64f_if_crc_legacy_0x8000.bin`, `sam3u2c_mkit_dk_dongle_nrf5x_if_crc_legacy_0x8000.bin` and `kl26z_microbit_if_crc_legacy_0x8000.bin` from their build directory and rename appropriately for release - `0244_k20dx_bootloader_update_0x8000.bin`, `0244_sam3u2c_bootloader_update_0x8000.bin` and `0244_kl26z_bootloader_update_0x8000.bin`

## Bootloader features removed for the 0x5000 build
* Hex file support
* Info files MBED.HTM, ASSERT.TXT, NEED_BL.TXT
* Entries from details.txt
* All action commands aside from REFRESH.ACT and START_IF.ACT
* All error messages in FAIL.TXT except for success and failure

## Bootloader features were removed for the 0x8000 build
No bootloader features were removed for the 0x8000 build.
