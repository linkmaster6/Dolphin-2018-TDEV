# Dolphin-2018-TDEV
A build of the Dolphin Emulator biased off of 5.0-8710 modified specifically to run the Metroid Prime 3 Prototype on Android

### Development Acknowledgement
I am an IT System Analyst, not a C++ developer. I built this project by using Google Gemini to help me navigate, debug, and patch the legacy C++ codebase and setup
the build environment as that required manual installation of outdated and deprecated
packages that had to be tracked down. I have a very elementary understanding of coding. The last time I made anything significant was Android 1.5 in eclipse and it was tic tac toe. However I was responsible for the hardware testing, ADB deployment,and final verification. This build exists because I really wanted to run it on my phone and Android Handheld

### Key Technical Patches
* **Memory Map:** Increased `REALRAM_SIZE` to 48MB (0x03000000) to accommodate TDEV-style debug memory allocations. Shoutout to Hakairyu at for posting at forums.dolphin-emu.org
a build and explaining what it does
* **Hypervisor:** Hard-coded `bMMU = true` and `Fastmem = true` overrides to bypass modern SoC memory controller conflicts.

### Developer Guide
This environment requires legacy tools to compile:
1. **JDK:** Java 8 (1.8).
2. **CMake:** Version 3.10.2.4988404.
3. **NDK:** NDK r17c.

**Build Command:**
Navigate to `Source/Android` and run:
`./gradlew clean assembleDebug`

### Installation (Mandatory ADB Override)
Because this build targets API 21, standard installation will be blocked by modern Android security policies. Use ADB:
`adb install --bypass-low-target-sdk-block app-debug.apk`


