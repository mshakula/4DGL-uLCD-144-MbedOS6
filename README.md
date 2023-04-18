![LCD image](https://os.mbed.com/media/uploads/4180_1/8185.png)

# 4DGL-uLCD-144-MBedOS6

Fork of [Jim Hamblen's 4DGL-uLCD-SE](https://os.mbed.com/users/4180_1/code/4DGL-uLCD-SE/) from MBed2 repository.
Updated to work with [MbedOS 6 API](https://os.mbed.com/docs/mbed-os/v6.16/introduction/index.html) and with modern [CMake](https://cmake.org/cmake/help/latest/index.html) build tooling.

## Installation

For easiest use in an CMake-based Mbed project, just add as a [git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules), and then `add_subdirectory` in your CMakeLists.txt, and then `target_link_libraries` to `4DGL-uLCD-144-MBedOS6`.

Also supports to be installed as a CMake installation target.

## API Reference

See [Jim Hamblen's original](https://os.mbed.com/users/4180_1/notebook/ulcd-144-g2-128-by-128-color-lcd/) reference.

## Usage Changes

Use Text_String instead of printf as stream is not longer suppored by new Mbed 6 [Unbuffered Serial](https://os.mbed.com/docs/mbed-os/v6.16/apis/unbufferedserial.html). In addition, the old method for waiting no longer works, manually wait ~100 ms between function calls.