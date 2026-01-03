# About This Branch

This is a personal branch that merges my other branches:

* dynshadow: Dynamic Shadow option [#5530](https://github.com/HarbourMasters/Shipwright/pull/5530)
* frameadvanceremap: Frame Advance Alternative Control Scheme [#5542](https://github.com/HarbourMasters/Shipwright/pull/5542)
* allowenemyrandoindebugsave: Allow Enemy Randomizer in Debug Save [#5841](https://github.com/HarbourMasters/Shipwright/pull/5841)
* invisiblenavi: Invisible Navi [#5845](https://github.com/HarbourMasters/Shipwright/pull/5845)
* nolikelikeitemsteal: Like Like don't Steal Items option [#5851](https://github.com/HarbourMasters/Shipwright/pull/5851)
* filenumedit: File Number in Save Editor [#5860](https://github.com/HarbourMasters/Shipwright/pull/5860)
* yellowleevercursor: Fix Leever's Z-Targeting Cursor option [#5863](https://github.com/HarbourMasters/Shipwright/pull/5863)
* ntscnamesaveeditor: NTSC Player Name Decoding in Save Editor [#5867](https://github.com/HarbourMasters/Shipwright/pull/5867)
* leeverbgm: Enable Battle Music for Leever option + Modularize EnemyBGMDisable [#5985](https://github.com/HarbourMasters/Shipwright/pull/5985)
* gstargetable: Targetable Gold Skulltula cheat [#5986](https://github.com/HarbourMasters/Shipwright/pull/5986)
* childholdshylianshield: Child Link can hold Hylian Shield cheat [#5990](https://github.com/HarbourMasters/Shipwright/pull/5990)
* advcamera: Advanced Camera Options (No Pull Request)
* jsonactorsetup: JSON Actor Setup (No Pull Request)
* bloodcolor: Add Blood Color options to Cosmetics Editor [#6007](https://github.com/HarbourMasters/Shipwright/pull/6007)
* autosavenotify: Add an option to disable Autosave Notification [#6081](https://github.com/HarbourMasters/Shipwright/pull/6081)

## The game crashes on launch?

Make sure your soh.o2r (actually a zip file in disguise) has "fonts/NotoSansJP-Regular.ttf" in it. If not, regenerate it (i.e. cmake --build build-cmake --target GenerateSohOtr).

This and "ntscnamesaveeditor" branch added a new font to the GUI and if it cannot be found the game crashes at launch.

# Original Readme

![Ship of Harkinian](docs/shiptitle.darkmode.png#gh-dark-mode-only)
![Ship of Harkinian](docs/shiptitle.lightmode.png#gh-light-mode-only)

## Website

Official Website: https://www.shipofharkinian.com/

## Discord

Official Discord: https://discord.com/invite/shipofharkinian

If you're having any trouble after reading through this `README`, feel free to ask for help in the Support text channels. Please keep in mind that we do not condone piracy.

# Quick Start

The Ship does not include any copyrighted assets.  You are required to provide a supported copy of the game.

### 1. Verify your ROM dump
You can verify you have dumped a supported copy of the game by using the compatibility checker at https://ship.equipment/. If you'd prefer to manually validate your ROM dump, you can cross-reference its `sha1` hash with the hashes [here](docs/supportedHashes.json).

### 2. Download The Ship of Harkinian from [Releases](https://github.com/HarbourMasters/Shipwright/releases)

### 3. Launch the Game!
#### Windows
* Extract the zip
* Launch `soh.exe`

#### Linux
* Place your supported copy of the game in the same folder as the appimage.
* Execute `soh.appimage`.  You may have to `chmod +x` the appimage via terminal.

#### macOS
* Run `soh.app`. When prompted, select your supported copy of the game.
* You should see a notification saying `Processing OTR`, then, once the process is complete, you should get a notification saying `OTR Successfully Generated`, then the game should start.

#### Nintendo Switch
* Run one of the PC releases to generate an `oot.otr` and/or `oot-mq.otr` file. After launching the game on PC, you will be able to find these files in the same directory as `soh.exe` or `soh.appimage`. On macOS, these files can be found in `/Users/<username>/Library/Application Support/com.shipofharkinian.soh/`
* Copy the files to your sd card
```
sdcard
└── switch
    └── soh
        ├── oot-mq.otr
        ├── oot.otr
        ├── soh.nro
        └── soh.otr
```
* Launch via Atmosphere's `Game+R` launcher method.

### 4. Play!

Congratulations, you are now sailing with the Ship of Harkinian! Have fun!

# Configuration

### Default keyboard configuration
| N64 | A | B | Z | Start | Analog stick | C buttons | D-Pad |
| - | - | - | - | - | - | - | - |
| Keyboard | X | C | Z | Space | WASD | Arrow keys | TFGH |

### Other shortcuts
| Keys | Action |
| - | - |
| ESC | Toggle menu |
| F2 | Toggle capture mouse input |
| F5 | Save state |
| F6 | Change state |
| F7 | Load state |
| F9 | Toggle Text-to-Speech (Windows and Mac only) |
| F11 | Fullscreen |
| Tab | Toggle Alternate assets |
| Ctrl+R | Reset |

# Project Overview
Ship of Harkinian (SOH) is built atop a custom library dubbed libultraship (LUS). Back in the N64 days, there was an SDK distributed to developers named libultra; LUS is designed to mimic the functionality of libultra on modern hardware. In addition, we are dependant on the source code provided by the OOT decompilation project.

In order for the game to function, you will require a **legally acquired** ROM for Ocarina of Time. Click [here](https://ship.equipment/) to check the compatibility of your specific rom. Any copyrighted assets are extracted from the ROM and reformatted as a .otr archive file which the code uses.

### Graphics Backends
Currently, there are three rendering APIs supported: DirectX11 (Windows), OpenGL (all platforms), and Metal (MacOS). You can change which API to use in the `Settings` menu of the menubar, which requires a restart.  If you're having an issue with crashing, you can change the API in the `shipofharkinian.json` file by finding the line `gfxbackend:""` and changing the value to `sdl` for OpenGL. DirectX 11 is the default on Windows.

# Custom Assets

Custom assets are packed in `.otr` archive files. To use custom assets, place them in the `mods` folder.

If you're interested in creating and/or packing your own custom asset `.otr` files, check out the following tools:
* [**retro - OTR generator**](https://github.com/HarbourMasters64/retro)
* [**fast64 - Blender plugin**](https://github.com/HarbourMasters/fast64)

# Development
### Building

If you want to manually compile SoH, please consult the [building instructions](docs/BUILDING.md).

### Playtesting
If you want to playtest a continuous integration build, you can find them at the links below. Keep in mind that these are for playtesting only, and you will likely encounter bugs and possibly crashes. 

* [Windows](https://nightly.link/HarbourMasters/Shipwright/workflows/generate-builds/develop/soh-windows.zip)
* [macOS](https://nightly.link/HarbourMasters/Shipwright/workflows/generate-builds/develop/soh-mac.zip)
* [Linux](https://nightly.link/HarbourMasters/Shipwright/workflows/generate-builds/develop/soh-linux.zip)

### Further Reading
More detailed documentation can be found in the 'docs' directory, including the aforementioned [building instructions](docs/BUILDING.md).

* [Credits](docs/CREDITS.md)
* [Custom Music](docs/CUSTOM_MUSIC.md)
* [Controller Mapping](docs/GAME_CONTROLLER_DB.md)
* [Modding](docs/MODDING.md)
* [Versioning](docs/VERSIONING.md)

<a href="https://github.com/Kenix3/libultraship/">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./docs/poweredbylus.darkmode.png">
    <img alt="Powered by libultraship" src="./docs/poweredbylus.lightmode.png">
  </picture>
</a>
