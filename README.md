# NextUI for Powkiddy V90S (Unofficial Preview)

An unofficial NextUI build for the **Powkiddy V90S**, built on oakMOSS. Thanks to the upstream NextUI, MinUI, oakMOSS, PortMaster, and emulator contributors.

The changes were made with Codex and tested on a V90S throughout three weeks of updates.

## GBA performance at lower clocks

The modified **gpSP** is tuned for smooth GBA play and fast-forward at lower CPU speeds. The goal is to keep the V90S cooler and make better use of its battery. In personal testing, GBA fast-forward ran smoothly at **4× with the V90S CPU capped at 1,000 MHz**. The clean install starts at 2×. With fast-forward audio enabled, the sound plays faster and at a higher pitch, as it does in other standalone GBA emulators, which prevents crackling.

Performance improvements draw on GBAdhoc and armGBA, including how they handle games that rewrite code during play. Accuracy fixes adapted from GBAdhoc also let gpSP play **Pokémon Monomyth**. [GBAdhoc](https://github.com/ShoshinFauteux/GBAdhoc) · [armGBA](https://github.com/MagnominusGit/armGBA)

Hold **Y** on a game in the GBA list to switch its core. **gpSP** is the default, with **armGBA 2.0** and **mGBA** as alternatives. You can change the default core in settings. Save states are separate for each core.

## What else is included

- **Per-core CPU limits.** Set a lower maximum CPU speed for cores that already run smoothly. This can save battery without having to use the same limit for every system.
- **60 Hz display.** oakMOSS sets the V90S screen to 60 Hz. It measured about 59 Hz with the stock timing. [oakMOSS hardware notes](https://github.com/spruceUI/oakMOSS/blob/main/docs/hardware-notes.md)
- **BatteryPlus and battery fixes.** oakMOSS uses BatteryPlus from KNULLI for its battery estimate. Run **Battery Setup** once to fix the false 0% startup issue that can leave the V90S refusing to turn on even when it has charge left unless you connect USB power, and to update the charging screen. [KNULLI BatteryPlus](https://knulli.org/configure/batteryplus/)
- **Default display settings** with artwork from Perfect Overlays by ourigen, based on the original work of 1playerinsertcoin. [Perfect Overlays on GitHub](https://github.com/ourigen/perfect_overlays/)
- **USB headphones and USB file transfer (MTP).** Copy files from a PC over USB without removing the SD card.
- **Windows title-screen scraper.** The optional Windows Tools ZIP saves original-size title screens over USB or directly to an SD card. It includes a standalone app with Node.js bundled. [mini-scraper](https://github.com/sinedied/mini-scraper)
- **PortMaster preview** for playing ports on the V90S. Game compatibility varies.

## Clean install

1. Download **oakmoss-v90s-v0.7.0-beta.1-sd1.img.xz**. Use Rufus or any disk-image flasher to write it to SD card. Boot oakMOSS once to initialize the data partition. [Official oakMOSS release](https://github.com/spruceUI/oakMOSS/releases/tag/v0.7.0-beta.1)
2. Power off and extract the clean-install ZIP directly to the card’s **SPRUCEOS** data partition.
3. Boot NextUI and run **Menu button → Tools → Battery Setup** once to fix the false 0% boot issue and update the charging display. Shut down and boot again.
4. Add games to **`Roms`** and any required BIOS files to **`Bios`**. In-game saves go under **`Saves`**. Empty systems, Tools, and Recents are hidden from the main list by default. Systems with games appear in this order: **NES → SNES → GB → GBC → GBA → Mega Drive → PlayStation**.

## Updating an existing SD card

The clean-install ZIP includes default emulator settings. Copying the whole ZIP over an existing installation can overwrite your settings. Future updates will have a separate ZIP that preserves your settings.

## Add title screens on Windows

1. Extract **NextUI-V90S-Windows-Tools.zip** on your PC and open **NextUI-Title-Screen-Scraper.exe**. The EXE is about 100 MB because it includes Node.js. Windows SmartScreen may warn because the EXE is unsigned.
2. For USB, open **Menu button → Tools → USB File Transfer** on the V90S, connect its **left USB port** to your PC, and wait for **NextUI V90S** to appear under **This PC**. Choose **2** in the scraper. For a card reader or a local ROM folder, choose **1** and select the folder.
3. Wait for the summary before leaving USB File Transfer or removing the card. The scraper saves original-size title screens and keeps existing artwork. If thumbnails are hidden in NextUI, enable **Settings → Appearance → Show Game Art**.

## Credits

Made possible by the teams behind [NextUI](https://github.com/LoveRetro/NextUI), [MinUI](https://github.com/shauninman/MinUI), [oakMOSS](https://github.com/spruceUI/oakMOSS), [PortMaster](https://github.com/PortsMaster/PortMaster-GUI), and [Libretro](https://github.com/libretro).

- **Game Boy Advance** includes [gpSP](https://github.com/libretro/gpsp), [GBAdhoc](https://github.com/ShoshinFauteux/GBAdhoc), [armGBA](https://github.com/MagnominusGit/armGBA), and [mGBA](https://github.com/mgba-emu/mgba).
- **Other systems** use [Gambatte](https://github.com/libretro/gambatte-libretro) (GB/GBC), [FCEUmm](https://github.com/libretro/libretro-fceumm) (NES), [Snes9x](https://github.com/snes9xgit/snes9x) (SNES), [Genesis Plus GX](https://github.com/ekeeke/Genesis-Plus-GX) (Mega Drive), and [PCSX-ReARMed](https://github.com/notaz/pcsx_rearmed) (PlayStation).
- **Windows title-screen scraper** uses mini-scraper by Yohan Lasorsa (sinedied) for game matching and Libretro’s thumbnail archive for the artwork. [mini-scraper](https://github.com/sinedied/mini-scraper) · [Libretro Thumbnails](https://github.com/libretro-thumbnails)

## Possible future work

Run-ahead, preemptive frames, and offline RetroAchievements.
