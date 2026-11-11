# FCE Ultra GX with PS3/PS4 controller support

An **unofficial** build of [FCE Ultra GX](https://github.com/dborth/fceugx) 4.0.4 for the Wii that adds one thing: **wired PlayStation 3 and PlayStation 4 controllers** on the Wii's USB ports, for 2 players (one in each port). Everything else is the original FCE Ultra GX.

**All the credit for FCE Ultra GX goes to its creators.** FCE Ultra GX is made by Tantric (dborth), with menu artwork by the3seashells, menu sound by Peter de Man, logo by mvit, and updates and fixes by Zopenko, Burnt Lasagna, Askot and bladeoner. It's built on [FCEUX](https://fceux.com) and FCE Ultra by Xodnizel, from the original FCE by BERO, with the GameCube port by SoftDev, askot and dsbomb. This build only adds the controller support. For the official FCE Ultra GX, go to [github.com/dborth/fceugx](https://github.com/dborth/fceugx).

> Please don't report problems with this build to the FCE Ultra GX developers. Open an issue here instead.

## Download and install

1. Go to **[Releases](../../releases)** and download **`FCEUltraGX-PS3-PS4-Wii-SD-card.zip`**.
2. Unzip it and copy the `apps` folder onto your Wii's SD card. If you already have FCE Ultra GX in `apps/fceugx`, it replaces the program and keeps your settings, saves and ROMs. You may want to copy your old `boot.dol` somewhere first, as a backup.
3. Start FCE Ultra GX from the Homebrew Channel. The menu shows **4.0.4 PS3/PS4 v1**.

## Controllers

Plug the controllers into the USB ports on the back of the Wii with their USB cables. You can plug them in or unplug them at any time, in the menu or during a game. There's no need to press the PS button first.

| Controller | Model |
| --- | --- |
| PS3 DualShock 3 / Sixaxis | |
| PS4 DualShock 4, original | CUH-ZCT1 |
| PS4 DualShock 4, newer (light bar on the touchpad) | CUH-ZCT2 |

Official Sony controllers only. Clones may not be detected.

- **2 players, any mix** of PS3 and PS4 controllers: the first one found is player 1, the next player 2. Each one plays alongside the Wii Remote or GameCube controller for that player.
- PS3 controllers show their **player number light**. PS4 controllers show a **light bar colour**: player 1 red, player 2 blue.
- Rumble works on both.
- The code handles up to 4 controllers, so more may work through a USB hub, but that hasn't been tested.

Each controller works like a **Classic Controller** for its player, so you can change its buttons on the Button Mapping screen under Classic Controller. The defaults are:

| PS3 / PS4 | Classic Controller | NES (default) |
| --- | --- | --- |
| Square | Y | B |
| Cross (X) | B | A |
| Triangle | X | Turbo B |
| Circle | A | Turbo A |
| Select (PS3) / Share (PS4) | − | Select |
| Start (PS3) / Options (PS4) | + | Start |
| D-pad or left stick | D-pad, stick | D-pad |
| L1 / R1 / L2 / R2 | L / R / ZL / ZR | |
| PS button | Home | Opens the menu |

## What's changed from FCE Ultra GX 4.0.4

- A new PS3/PS4 controller driver (`source/drivers/ogc/wii/ds3.c` and `ds3.h`).
- `WiiInputDriver.cpp`: reads the PS controllers as Classic Controllers, one per player, with rumble.
- `WiiFileSystemDriver.cpp`: after checking for USB drives, the PS3 controllers are woken up again (that check can make them stop sending).
- The menu and `meta.xml` show the build version.

## Source code

The full source code of each version is attached to its release (`fceugx-4.0.4-ps3-ps4-v1.zip`), as the license requires, along with `fceugx-ps3-ps4.patch`: all the changes as one patch against the official source. The PS3 controller protocol is based on xerpi's SickSaxis library.

To build it yourself, put `build_fceugx.sh` next to the source zip and run `bash build_fceugx.sh`. It builds in the same libogc2 container (with Docker or Podman) that FCE Ultra GX's own builds use, and makes `boot.dol` and the SD card zip.

## Also see

- [Genesis Plus GX PS3/PS4](https://github.com/gabbycat4/genesis-plus-gx-ps3-ps4): Genesis / Mega Drive, Sega CD and Master System.
- [Snes9x RX PS3/PS4](https://github.com/gabbycat4/snes9xrx-ps3-ps4): SNES.
- [VBAGX PS3/PS4](https://github.com/gabbycat4/vbagx-ps3-ps4): Game Boy / GBA.
- [Wii Menu PS3/PS4 Controller](https://github.com/gabbycat4/wii-menu-ps3-ps4-controller): a Priiloader hack that lets the same controllers work as the pointer on the Wii Menu (4.3U).

## License

FCE Ultra GX is free software under the GNU General Public License, version 2 or later, and so is this build. See [`LICENSE`](LICENSE).
