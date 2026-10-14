# AutoBleem 2 User Manual

AutoBleem 2 is a game launcher for the **PlayStation Classic** - and, since version 2, for a **Raspberry Pi**,
a **PC booted from a USB stick** and **Windows**. It shows your PS1 games as a shelf of covers with their
box art and details, starts them in the bundled PCSX emulator, and, with RetroArch installed next to it,
plays the games of other systems too. This manual covers installing it on each platform, everyday use, and
the tools that come with it.

> The downloads for every platform are at **https://autobleem.retromenele.pl/**. The page is organised by
> platform: the *Install* panel of each one is what you download; the *Build inputs* below it are what the
> installers fetch by themselves.

## 1. What you get

AutoBleem turns your PlayStation Classic - or a Raspberry Pi, an old PC or your Windows computer - into a small
game console with a proper menu for your own games. This is what you get:

- **The launcher.** This is what you see when you switch on: a shelf of game covers you scroll through, with
  each game's details beside it. From here you start games, sort them into sets (PlayStation, RetroArch,
  Apps), change settings, look after memory cards and save states, and download apps and games from the Store.
  It looks and works the same on every platform.
- **Two PS1 emulators.** `pcsx-abnxt` is the current one and the default; `pcsx-ab` is the classic emulator
  AutoBleem has always shipped. You choose between them in the options. Both use the same settings and memory
  cards, so you can switch at any time without losing anything.
- **RetroArch**, if you want games from other systems too - NES, SNES, Mega Drive, Game Boy, arcade machines and
  many more. It is optional on every platform. Copy in your ROMs, and AutoBleem sorts them into lists and starts
  each game with the right core. PlayStation games can run in RetroArch as well; its *PlayStation 1* core is at
  the top of the core list (section 3.8). Games such as Doom run from your own game files in a `Packages` folder
  (section 3.9).
- **The console tools.** *PSC-Bios* - in the menus it is called *Network & Controllers* - sets up WiFi, the
  clock, Bluetooth pads and pad mapping, on the console as well as on a Raspberry Pi and the PC stick.
  *ABFlashKit* installs the AutoBleem kernel on a PlayStation Classic (chapter 6).
- **UpdateRoms** for Windows. The PlayStation Classic has no network of its own, so this PC program refreshes
  the RetroArch lists and fetches box art for a console stick while it is plugged into your PC.

![The launcher: the shelf of covers, the selected game's details, the button hints](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Installation

### 2.1 PlayStation Classic

AutoBleem runs entirely from a USB stick. Nothing inside the console is changed: take the stick out and the
console works exactly as it did before. All you need is a Windows PC, a USB stick (USB 2.0, 8 GB or more) and
the console.

The stick does not have to be empty, and it is **not formatted** unless you ask for it: AutoBleem is installed
next to whatever is already on it, and a stick you already use with AutoBleem 1.0 is upgraded in place (see
below). For a stock console the stick must be **FAT32**, because the console's own kernel cannot read exFAT.
Once the AutoBleem kernel is installed (ABFlashKit, chapter 6), the console also starts from an exFAT stick,
which gets rid of FAT32's limit of 4 GB per file.

1. Download **AutoBleemInstaller-<version>.zip** from the PlayStation Classic panel of the site and unpack it
   anywhere. Inside are `AutoBleemInstaller.exe` and its README. AutoBleem itself is downloaded during the
   installation, so the PC needs an internet connection.
2. Plug in the stick and start `AutoBleemInstaller.exe`. Choose the **channel** - *Release* is the tested
   version and the right choice for most people, *Testing* is the next version while it is being tested, and
   *Nightly* is the newest development build, which may not work - and then choose the stick's drive. The line
   underneath tells you which AutoBleem version you are about to install and what is on the stick now: *a fresh
   install* (the other files on the stick are left alone) or *AutoBleem <version> is on this stick: it will be
   updated* (your games, saves, memory cards and settings stay).
   **You do not need to format.** The **Format** button next to the drive is only for a brand-new stick without a
   file system, for one the console cannot read (NTFS, for example), or for one you want to wipe clean. It asks
   first and then erases everything on the stick. Choose FAT32 there, unless the console already has the
   AutoBleem kernel.
   Then tick what you want installed:
   - **Cover databases** - the box art and descriptions of the whole PS1 library, so your games get their covers
     by themselves (ticked by default; about 300 MB).
   - **RetroArch** - RetroArch with its cores, extra applications (Doom, Quake, Amiga, ...) and libretro's
     assets, for games from other systems. Off by default; you can add it later by running the installer again.
   - **BIOS files** - the BIOS files some RetroArch cores need before they start (only with RetroArch).
   - **Sample games** - a few free homebrew games, so the shelf is not empty the first time you start.
3. Press **Install** and wait. The progress bars and the log show every step. At the end the stick is named
   `SONY` and gets a copy of `UpdateRoms` (see chapter 5).
4. Remove the stick safely, plug it into the console's **second front USB port** (the right one, player 2) -
   the first one stays free for your pad - and switch the console on. Instead of the stock menu, AutoBleem
   starts. For a second pad, use a USB hub on the front port or a Bluetooth pad. Do not put the stick in the
   micro-USB port at the back (see below).

**Switching on and off.** With the stick in, the console starts, blinks its light for a few seconds while it
notices AutoBleem, and then goes to standby before anything appears on the screen. That is normal: AutoBleem
starts through the console's own update mechanism, and this is how that mechanism works. Press **Power** once
and the launcher appears.

When you choose *Power off* in the system menu, or press the console's Power button, the console goes into
**AutoBleem's standby**: AutoBleem first disconnects the stick safely, then the light turns **orange** - the
sign that everything went as it should. The next press of Power brings the launcher back within a few seconds.
**While the light is orange you can pull the stick out** and put it into your PC; Windows will not ask to
check it, because it was disconnected properly. Put it back before you press Power. If you unplug the
console's power cable, it goes through the start-up standby again next time. A **red** light means the
console is really switched off.

**Use a front USB port for the stick.** The micro-USB port at the back is the power port. With the AutoBleem
kernel it can also take a USB device, but anything plugged in there keeps the console from sleeping: with a
stick or a hub on it, the console switches off completely instead of going to standby, and Power then has to
start it from scratch, which takes longer.

**If the stick is missing.** When the console starts without a stick, or you pull the stick out while
AutoBleem is running, a picture asks you to put it in - any USB port will do. AutoBleem waits for 5 minutes
and then puts the console to sleep; press Power if you want it to sleep straight away.

![The picture that asks for the stick](../images/en/insert-stick.jpg)

**When the stick is checked.** If the stick was not disconnected properly - you pulled it out while AutoBleem
was running, or the power went off - AutoBleem checks it for errors before it uses it again: at start-up,
after waking up, or when you plug it back in. A progress bar shows how far the check has got. On a big stick
this can take a while; let it finish and do not switch the console off in the meantime.

![The stick check](../images/en/stick-check.jpg)

**Updating.** To update a stick, run the installer on it again - the button now says *Update*. It installs the
newest version of the channel you choose; your games, saves, settings and RetroArch content stay, and only
AutoBleem's own files are replaced. A console with the AutoBleem kernel and WiFi can also update itself
(section 3.11).

**Upgrading from AutoBleem 1.0 (or AutoBleem-NG).** You use the same installer on the same stick, without
formatting it:

1. First copy the whole stick to your PC, as a backup - just in case.
2. Plug it in, start `AutoBleemInstaller.exe`, and choose the channel and the drive. Do **not** press Format.
3. Press **Install**. The installer moves the old layout to the new one: RetroArch, the ROMs and the themes go
   where AutoBleem 2 expects them, and the old ROM folders (`nes`, `snes`, ...) get RetroArch's system names.
   Your games, save states, memory cards, ROMs and RetroArch saves all stay, and so does `config.ini` - only its
   PS1 emulator is switched to pcsx-abnxt.
4. Put the stick back into the console. The first scan rebuilds the game list and the playlists. To get box
   art for your RetroArch games, run UpdateRoms on the PC (chapter 5).

> The stock console has no clock and no network. Dates appear only after the AutoBleem kernel is installed
> (chapter 6), and box art for RetroArch games comes from UpdateRoms on the PC (chapter 5).

Your PS1 games go into the stick's `Games` folder, one folder per game - section 3.9 explains the layout.

### 2.2 Raspberry Pi

With AutoBleem a Raspberry Pi becomes a small console: it starts straight into the launcher, with no desktop in
between. The site has two ready-made card images, 32-bit and 64-bit, and a package for a Raspberry Pi OS Lite
you already have.

| Model | 32-bit image | 64-bit image | Notes |
|---|---|---|---|
| Raspberry Pi 5 | yes | yes | |
| Raspberry Pi 4 Model B, Pi 400 | yes | yes | |
| Raspberry Pi 3 Model B / B+ / A+ | yes | yes | fine for the launcher and PS1 |
| Raspberry Pi Zero 2 W | yes | yes | 512 MB of RAM: PS1 runs, the heavier RetroArch cores do not |
| Raspberry Pi 2 Model B | yes | v1.2 only | slow for anything 3D |
| Raspberry Pi 1, Zero, Zero W | no | no | ARMv6 - neither image runs |

**For PS1 games, take the 32-bit image.** The fast ARM recompiler of the classic `pcsx-ab` exists only in
32-bit, so PS1 games run slower on the 64-bit build. The 64-bit image has more RetroArch cores, so take it if
the other systems matter more to you than PS1.

**With Raspberry Pi Imager:**

1. Install Raspberry Pi Imager (raspberrypi.com/software). In *Choose OS* pick *Use custom* and the
   `autobleem-<version>-rpi-armhf.img.xz` (32-bit) or `-arm64.img.xz` (64-bit) you downloaded - or add
   a repository URL in the app's settings and pick AutoBleem from the list. There is one per channel:
   `https://autobleem.retromenele.pl/rpi-imager/os_list.json` for the latest release,
   `.../os_list-testing.json` for the build being tested and `.../os_list-nightly.json` for the newest
   development build. The download page's Raspberry Pi tab lists the ones that exist, with a *Copy*
   button each.
2. Use Imager's customisation screen (the gear, or the question after *Next*) to set the **user name and
   password, the WiFi network and country, and enable SSH**. AutoBleem needs a network on its first boot.
3. Write the card, put it in the Pi with a screen and a keyboard or pad connected, and power it on.

**The first start** takes 5 to 25 minutes, and the screen tells you what is happening. If there is no network,
it asks you for one: pick your WiFi from the list and type the password. Then it asks whether to install
RetroArch - if you do not answer within a minute, it does. After that it enlarges the system partition, turns
the rest of the card into the `AUTOBLEEM` partition for your games, installs RetroArch with its cores, the BIOS
packs and the sample games, and restarts into the launcher.

If you would rather not answer questions at the first start, put the answers into **`autobleem.txt`** on the
card's boot partition beforehand - any PC can open and edit it:

| Key | Default | Meaning |
|---|---|---|
| `root_gib` | 8 | The system partition's size in GiB; the rest becomes the games partition. |
| `hdmi_mode` | 1920x1080@60 | The screen mode for the whole boot (`1280x720@60` for an older TV). |
| `retroarch` | (asked) | `yes` / `no` - RetroArch and the other systems, or PS1 only. |
| `thumbnails` | none | `boxarts` mirrors the whole box-art set for offline covers (~9000 files). |
| `bios`, `downloads`, `samples` | yes | Set to `no` to skip the BIOS packs, every download, or the sample games. |

**On a Raspberry Pi OS Lite you already have** (Bookworm or Trixie): copy `autobleem-rpi.tar.gz` (or the arm64
one) to the Pi, unpack it and run `sudo bash install.sh`. It asks the same questions, makes room for the data
partition by shrinking the system partition at the next start (`--shrink-root <GiB>`), and puts the launcher on
the first console.

After the installation you fill the card's **`AUTOBLEEM` partition** (exFAT) with your games: take the card out
and open it on any PC, or copy over the network (SSH is on). PS1 games go into `Games/`, other systems' ROMs
into `RetroArch/roms/<system>/`, the PS1 BIOS into `System/Bios/` (section 3.10) and themes into `Themes/`.

### 2.3 PC USB stick

The same thing for any PC that can start from USB: the stick starts the PC straight into AutoBleem and leaves
the PC's own disk alone. It is a 32-bit system, so old machines work too.

1. Write the image to a stick of 8 GB or more. **On Windows** use **AutoBleemFlasher** (PC panel of the
   site - unzip it and run `AutoBleemFlasher.exe`; it asks for administrator rights, since it writes a
   whole disk): pick the channel and the stick, press *Write* and confirm twice - it downloads the image,
   checks it, writes it and reads it back. Only USB sticks and SD cards are offered, never the disk Windows
   runs from, and **everything on the chosen stick is erased**. On Linux or macOS, download
   `autobleem-<version>-pcusb-i386.img.xz` from the PC panel and write it with
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (or balenaEtcher).
2. Boot the PC from the stick (the boot menu key of your PC - F12, F8, Esc...). Both BIOS and UEFI boot
   work; **Secure Boot must be off**.
3. The first start works like the Pi's: it asks for a network if no cable is plugged in, asks about RetroArch,
   installs everything - about eight minutes with a wired network - and restarts into the launcher.

Afterwards the stick has an `AUTOBLEEM` partition for your games. Plug the stick into a running Windows 10 PC
(version 1903 or newer) and it shows up as a second drive you can copy games to. `autobleem.txt` is on the
first partition, with the same keys as on the Pi (except `hdmi_mode` - a PC always uses the screen's own mode).

### 2.4 Windows

If you simply want AutoBleem on your Windows computer, it also runs as an ordinary program: full screen, with
the emulators and RetroArch started as programs of their own.

1. Download **AutoBleemSetup-<version>.exe** and run it. It installs per user, without administrator
   rights: the program under `%LOCALAPPDATA%\Programs\AutoBleem`, the data (games, settings, themes,
   RetroArch) in a folder you choose - `Documents\AutoBleem` by default.
2. Tick the components - the cover databases, RetroArch (the official Windows build and its cores), the
   BIOS files, the sample games - and let the setup helper download them.
3. Start AutoBleem from the Start Menu or the Desktop. On a PC the keyboard works as a pad (section 3.2).

To update, run a newer setup over it: the program is replaced and your data folder stays as it is. The
launcher also checks the site once a day and offers an update when there is one (section 3.11).

<!-- pagebreak -->

## 3. Using AutoBleem

### 3.1 The launcher

The launcher opens on the shelf: the covers of the current set, the selected one in the middle with a
soft reflection under it, its details next to it as a compact grid - publisher, year, serial, region,
players, when it was last played (a fact a game does not have is left out) - and a play button. The default
look is the **ab2.0.0** theme; a fresh install and an update that brings it switch to it once. The hint bar at the bottom has
two lines of four slots. The first line is what the buttons do for the selected game (play, play in
RetroArch, open the icon row, the Quick menu); the second always shows Select (the set), Start (a random game), Triangle (the
guide) and L2 + R2 (the system menu), dimmed in a state where one does nothing. A game with no cover shows a disc lying in the case's black tray. A scan of the games folder runs in the
background on every start; while it runs, a bubble at the top right shows its progress, and new games
appear on the shelf as they are found.

**A fresh install** has no games yet: instead of an empty shelf the launcher shows a welcome card - *Hi, and
welcome to AutoBleem!* - telling you to drop games into `Games` and press *Re-scan games*, and naming the
place for your platform: on your stick (PlayStation Classic, PC stick), on your SD card (Raspberry Pi) or in your
AutoBleem folder (Windows). The card goes as soon as a scan finds the first game.

**Notifications** appear as bubbles at the top right: the scan's progress, the name of the set you
switched to (*Showing: ...*, for as long as Options → *Notification timeout* says), a low pad battery, a note after a crash, a scanner processor at work, and the Store's download in progress. The download's bubble shows its
speed and the time left, e.g. `1.4 MB/s · 0:42`.

**The channel tag.** A build that is not a final release shows a small tag under the pad battery plate in the
top-left corner: a chip with the channel - `ALPHA`, `BETA` or `RC` for a pre-release, `TESTING` for any other pre-release,
`NIGHTLY` for a nightly build, `DEV` for a build made by hand - and the short version beside it (for `DEV`, the commit it was
built from). A release shows no tag.

A wireless pad with a battery reading - the console, a Pi or the PC stick, not Windows - shows as a small icon with its percentage, stacked from the top-left corner on its own plate. A pad matched to Player 1 or Player 2 (following the Swap Player 1 / Player 2 option) is tagged P1/P2; an unmatched pad, or a third one, has no tag. When a pad's battery runs low, a notification line reports it once, by name and percentage.

![The set picker: three tabs, and the groups of the current one with their game counts](../images/en/set-picker.jpg)

### 3.2 Controls

| Button | On the shelf |
|---|---|
| Left / Right | Previous / next game. Holding scrolls on. |
| L1 / R1 | Jump to the previous / next first letter of the titles. On an empty shelf with a drive, R1 opens *Disc* (section 3.8a). |
| Cross | Start the selected game (a PS1 game in the PS1 emulator; a RetroArch game in its core; an App after its read-me). |
| Square | Start the selected PS1 game in RetroArch instead. On a disc in a USB drive: *Copy disc* (section 3.8a). |
| Circle | Back to the disc view, when a disc is in the drive (section 3.8a). |
| Triangle | The button guide. |
| Start | A random game from the current set. |
| Select | The set picker: PlayStation / RetroArch / Apps tabs (L1 / R1), the groups of the tab (Up / Down, L2 / R2 a page), Cross picks. |
| Up | The Quick menu (section 3.4). |
| Down | Open the icon row under the game (Settings, Game, Memory Card, Resume). Up closes it. |
| L2 + R2 | The system menu (section 3.5). |

**With a keyboard** (a PC without a pad, or a USB keyboard on the console, a Pi or the PC stick) the keys stand in: **Arrow keys** = d-pad, **Enter** = Cross, **Esc or Backspace** = Circle, **Tab** = Triangle, **Space** = Square, **F1 / F2** = Select / Start, **Page Up / Page Down** = L1 / R1, **Home / End** = L2 / R2, **F10** = the system menu. On a development machine Esc closes the program and Space is Start.

In every list and menu: Up / Down move, **L2 / R2 turn pages**, L1 / R1 jump to the first / last row,
**Cross selects, Circle goes back**. A screen with settings saves them when you leave it with Circle.

**In a game or an App**: hold **Start + Select, or Home, for 2 seconds** to go back to AutoBleem. It works on
every pad - the console's, a USB pad, a Bluetooth pad. A short press opens the emulator's menu; an App has no
such menu, only the hold works.

![The icon row under the selected game](../images/en/launcher-icons.jpg)

### 3.3 The sets

**Select** opens the set picker. The PlayStation tab lists, on a PlayStation Classic, *All games* and
*Internal games* (the console's built-in twenty), then *USB games* (everything in `Games/`) and every folder you made
under it (a game in a sub-folder belongs to that group), then *Favorite games*, *Game history* and, when any game is flagged as one, *Lightgun
games*. On a Raspberry Pi, a PC stick and Windows there are no internal games, so the list starts at *USB games*, which is
the whole library. The RetroArch tab (only where RetroArch is installed) lists one group per system that has games, plus
RetroArch's own Favorites and History. The Apps tab groups applications by type: *All apps*, then *Games*,
*Emulators*, *Tools*, *Media* and *Other* (the category is set in each app's `app.ini` file). The Apps tab also shows **PE apps** - Windows programs run
by the PE runner; one the console cannot start is marked *cannot run on this console*. Where the launcher shows it, a *Packages* row
is in the list too (section 3.9). Each row shows how
many items it holds; a group with none opens on an empty shelf with the icon row showing Settings only.
The footer shows the keys: L1 / R1 for the tabs, L2 / R2 for a page, Cross to pick, Circle for *Back*.

### 3.4 The Quick menu

**Up** in the launcher, or the **gear icon** in the icon row (where Settings / Game / Memory Card / Resume are):
the Quick menu for actions you reach for from the carousel. A short list: *Re-scan games* (starts a scan
now), *Store* (browse and install games, apps and extensions), *Network & Controllers* (only where an installed extension provides the `network` entry - PSC-Bios on the console, a Pi and the PC stick: Wi-Fi, Bluetooth pairing, the gamepad mapping wizard - see section 6; greyed out with "enable it in Extensions" when that extension is disabled - Cross opens the Extensions list), *Restart launcher*
(closes AutoBleem and starts it again; on the console, a Pi and the PC stick only), and *System menu...*
(everything else: Options, Game Manager, Power off and more - the full menu below). Up / Down move (wrapping), Cross picks, Circle back. Each item has a
one-line description on its row. Apart from the Store and Restart launcher, every item is also in the system menu.

![The Quick menu](../images/en/quick-menu.jpg)

### 3.5 The system menu

**L2 + R2** (together, in either order) opens the system menu over the shelf. Each row has a one-line
description, and the menu is grouped into sections:

| Section | Item | What it does |
|---|---|---|
| (top) | Re-scan games | Looks for new, changed or removed games now (the scan also watches the folder by itself). |
| | Extensions | The extensions on the stick - the AutoBleem Store and others (section 3.12). |
| **Library** | Game Manager | The PS1 games as a list with their folders: delete a game, flush the covers. Disabled while a scan is running. |
| | Memory Cards | Your memory card sets (section 3.7). |
| | Scanner processors | The programs every scan runs first - their order, on or off (section 3.13). Disabled while a scan is running. |
| **System** | Options | AutoBleem's settings (section 3.6). |
| | Network & Controllers | Only where an installed extension provides the `network` entry (`Provides=network` in its `extension.ini` - PSC-Bios on the console, a Pi and the PC stick) - Wi-Fi, Bluetooth controller pairing, DualShock 3 setup, and the gamepad mapping wizard - see chapter 6. When that extension is installed but disabled, this item stays greyed with a note "enable it in Extensions" - Cross opens the Extensions list at it. |
| | Hardware Information | The machine's facts: system, CPU, storage, network interfaces, time zone, display, the pads and their mappings - the same page on every platform (section 4.2). Circle returns to the system menu. |
| | Virtual gamepad | The pads Apps are given and the pads the daemon sees (section 4.5). Circle returns to the system menu. |
| | Software Update | (Raspberry Pi and PC) Check the site for a newer AutoBleem or RetroArch now; the row says *Update available* when the launcher already knows of one. |
| | About | Credits and license. |
| **Leave** | RetroArch | (Only where RetroArch is installed.) Leaves the launcher for RetroArch's own menu. Closing RetroArch comes back. |
| | Power off | After a confirmation: on the console AutoBleem's standby - the stick disconnected, the light orange, Power brings the launcher back (section 2.1); on a Pi or PC the machine shuts down. |

![The system menu](../images/en/system-menu.jpg)

### 3.6 Options

The settings are in groups, each under a heading; Up / Down move between rows, Left / Right change a value
(a tap is one step, a hold scrolls), L1 / R1 jump to the first / last row, L2 / R2 page, Circle leaves and
saves. Every change is applied at once. On/off values read **ON** / **OFF**.

| Group / setting | What it does |
|---|---|
| **Interface**: Display | The screen's resolution, for the launcher and the PS1 emulator: *Auto* (the screen's own mode, shown as *Auto (1920x1080)*) or any mode the screen lists; the console offers 720p, 1080p and *CRT 4:3* (720x480, for a CRT or a 4:3 capture device). A new mode is asked about: *Keep this display mode?* - if you do not confirm, it goes back after a countdown. Not on a development window. |
| CRT margin: | The safe area on a 4:3 output, 0 to 10 % in steps of 1 %. Applied at once, and read before the start-up splash. |
| Picture height: | The height of the picture on any 4:3 output (*CRT 4:3*, or a 4:3 window on a VGA / PC output), -40 to +40 in steps of 2, applied at once. RetroArch's game picture follows it. |
| Emulator screen scaling | How the PS1 emulator fits a game's picture to the screen: *1x1* (the PlayStation's own pixels), *2x (integer)*, *4:3*, *4:3 (integer)* or *Full screen*. Integer scaling uses whole multiples only (the sharpest). It replaces the old Widescreen switch; the classic `pcsx-ab` and RetroArch know only full screen and 4:3. |
| Screen halo: | ON fills the bands beside a game's picture (where it does not fill the screen) with the picture's own glow (`pcsx-abnxt`). |
| AutoBleem theme | The look. Themes live in `Themes/`; a theme zip dropped there is listed by name too. The themes AutoBleem ships are refreshed with every update - to customise one, copy it under a new name first. The default is **ab2.0.0**. On *CRT 4:3* the list shows only themes that have a 4:3 layout; if the theme in use has none, the default theme replaces it after the confirmation (also at start) and a notice says *Theme switched to the default (CRT 4:3)*. |
| Cover style | The jewel-case frame drawn around PS1 covers. |
| Cover shine | A shine that crosses the selected cover when the shelf comes to rest. |
| Language | The launcher's language, applied at once (17 languages). |
| Notification timeout | How long the information bubbles ("Showing: ...", the scan's summary) stay, 0 to 20 seconds; 0 shows *Off*. Errors keep their own fixed time. |
| Splash screen | The AutoBleem picture when the launcher starts; off goes straight to the shelf. |
| Animations | The movement between screens; off makes every screen change instant. |
| **Fonts**: Use default font | The launcher uses its default font (Red Hat Text), or - switched off - the font chosen below. |
| Font | Any `.ttf`/`.otf` from `resources/fonts`, `RetroArch/fonts` or the theme's folder; the row names the font in use. |
| **Sound**: Music, Background music | Which track plays under the launcher (the theme's, or a file from `resources/music`), and whether one plays at all. |
| **Emulation**: PS1 emulator | `pcsx-abnxt` (the default: current PCSX-ReARMed with AutoBleem's additions) or `pcsx-ab` (the classic). A resume point saved by one continues in the other, unless the game ran without a BIOS file. |
| Swap Player 1 / Player 2 (PS1 emulators) | Swaps which of the first two pads is Player 1 and which is Player 2, in both PS1 emulators (pcsx-abnxt and the classic pcsx-ab). It only takes effect with two or more pads connected; with one pad, play is always Player 1. RetroArch is not affected. A PS1 emulator that cannot swap yet shows *This PS1 emulator does not support swapping pads yet*. |
| Play all PSX games with RA, Update RA config, Persist RetroArch config | (Only where RetroArch is installed.) Every PS1 game starts in RetroArch's PS1 core (*PlayStation 1*; on a PC it is SwanStation); AutoBleem writes its settings into RetroArch's config when it starts a game there; a change made in RetroArch's own menu is kept when RetroArch quits. |
| **Library**: Show internal games | The console's built-in games in the PlayStation lists (PlayStation Classic only). |
| Clean game names: | ON (the default): RetroArch game lists show names without bracketed tags such as (USA), (Rev 1) or [!]. OFF shows the file names. The file name stays in the game's details. PS1 games are not affected - their titles come from the database. |
| Fetch box art online | The scan fetches missing covers from libretro's servers (Raspberry Pi, PC, Windows). |
| **Updates** | The update channel: `release` (the tested version), `testing` (the next version, being tested), `nightly` (the newest development build) or `off`. The default follows the version installed. Not shown on a development host. |
| **Diagnostics**: Keep logs on the stick | Keep every log on the stick from the next start, not only after a crash (chapter 7). |
| Show performance | An overlay in the bottom-left corner: frame rate, CPU load, threads and memory; the emulator shows its FPS and CPU in the game too. |

![The options, in groups](../images/en/options.jpg)

![The Display group: CRT margin and Picture height](../images/en/options-display.jpg)

![The notice after switching to CRT 4:3 with a theme that has no 4:3 layout](../images/en/crt43-theme-notice.jpg)

### 3.7 A game's settings

With a game selected, **Down** opens its icon row: **Settings** (the options above), **Game** (the game's
own settings), **Memory Card** (its memory card) and **Resume** (its save states). Cross opens the one under
the cursor.

The **game editor** shows the game's details on the right (title, publisher, year, players, folder, memory card) and its settings on the left, in four groups:

- **Game**: *Favorite* (in the Favorite games group), *Lightgun game* and *Play using RA* (only where RetroArch is
  installed: a light-gun game joins the Lightgun group and always runs in RetroArch, whose PS1 core has the GunCon;
  *Play using RA* runs this game in RetroArch), *Lock data* (the scanner leaves the game's title, serial and disc list as you set them),
  and *Resume:* - what happens when a game with resume points starts: *Ask* shows the resume-slot picker, *Last
  slot* continues from the newest slot at once, *Never* starts the game from the beginning.
- **Display**: *Resolution* (1x or 2x, on the built-in GPU), *Remove seams* (only with 2x), *Dithering* (Off, On, Always),
  *Smoothing*, the *Filter* - how the picture is scaled: Nearest (plain pixels), Linear (smoothed), Sharp or Sharp (simple)
  (crisp pixels without shimmer), Quilez, or the CRT filters CRT (fast), CRT (raster) and CRT-Pi (they draw their own scanlines,
  so the scanline rows grey out) - and *Scanlines* with their *Scanline brightness*. Resolution, remove seams, dithering, smoothing and the
  filters other than Linear and Nearest are for `pcsx-abnxt`; the classic `pcsx-ab` and RetroArch show the rest as Nearest.
- **Rendering**: the GPU *Plugin* and the *Frameskip* (Auto, Off, 1 to 3).
- **Emulator**: *Speedhack*, the CPU *Clock*, *Spu interpolation*, the *Boot logo* (off skips the BIOS shell - for a
  homebrew disc whose custom logo breaks the boot), and with `pcsx-abnxt` the *Sony hacks* toggle.

The picture shape and the screen's resolution are global (Options → *Emulator screen scaling* and *Display*).
A game with no title in its data is shown under its folder's name.

Triangle renames the game, Square changes its memory card, Start shares a new card. Circle saves and leaves.
Holding Left / Right or Up / Down repeats the move, in the editor and also in RetroArch's game options and
cores screens. A drive game that has no `pcsx.cfg` cannot save: the editor says *Not saved: this game has no pcsx.cfg*.

For a **disc in the drive** (section 3.8a) the editor greys the rows the disc cannot use and says *Not
available for a disc in the drive*.

![The game editor for a disc in the drive](../images/en/game-editor-disc.jpg)

**Settings saved in the emulator.** The emulator's own menu has *Save settings for this game*. Once a game
has settings saved there, they are the ones it plays with, and the game editor shows its Display,
Rendering and Emulator rows greyed out, with those values, under the heading *Saved in the emulator*. To go back to the
game editor's settings, pick **Unlock the settings** and confirm: this deletes the settings the emulator
saved, and the rows can be changed again. Both emulators, `pcsx-ab` and `pcsx-abnxt`, read and write the
same saved settings.

![The game editor](../images/en/game-editor.jpg)

### 3.7 Memory cards and save states

Every PS1 game has its own memory card by default (kept with its save states in `Games/!SaveStates/<game
folder>/`). **Memory Cards** in the system menu manages **shared sets** - a card several games use, kept in
`Games/!MemCards/`: create one (Square, with the on-screen keyboard), rename (Cross), delete (Triangle).
A game is put on a set with *Change memory card* in its editor, or from its Memory Card icon. A set
with no card yet says *no card yet*, and saving asks *Do you want to save memory card data?*

The **memory card editor** (the Memory Card icon) shows the game's card and a second card side by side, with
every save's icon and title: copy a save between the two (Square), delete one (Triangle), defragment a
card (Select). Start swaps the card on the right for another set.

![The memory card editor](../images/en/memory-card-editor.jpg)

**Resume points**: when you leave a PS1 game with the console's Reset button (or the emulator's menu on a
Pi or PC), AutoBleem keeps a save state of where you were and offers it under the **Resume** icon - four
slots, shown as framed cards, each with a picture of the moment, its slot number and date; the newest is
marked **NEWEST** and an unused slot says *No resume point*. Cross continues from the slot, Triangle deletes
it. A game with a resume point shows a small picture on its Resume icon; a game without any has the Resume icon
greyed out. While the resume point is being written on the way out of a game, the emulator shows *Please wait...*.
PS1 games played in RetroArch have resume slots too. A slot carries a badge - the AutoBleem 2 or the RetroArch
logo - so you see which emulator wrote it.

![The resume-slot picker](../images/en/resume-picker.jpg)

### 3.8 Starting games, RetroArch and Apps

**Cross** starts the selected game. A PS1 game runs in the chosen PS1 emulator (section 3.6), full screen,
until you leave it - on the console with the front **Reset** button (back to the launcher with a resume
point; it works from inside the in-game menu too) or **Power** (the console turns off); on a Pi or PC through the emulator's in-game
menu (below). **Square** starts a PS1 game in RetroArch instead.

**The way out of a game** is the same on every pad - the console's, a USB pad, a Bluetooth pad: **hold
Start + Select, or Home, for 2 seconds** (*Hold Select+Start or Home for 2 seconds: back to AutoBleem*). A short press
of Select + Start or Home opens the emulator's menu (*Short press of Select+Start or Home: the emulator's menu*); an
App has no such menu, only the hold works. On the console, **Reset** always stops an App as well.

**The in-game menu** (`pcsx-abnxt`). Press the menu button - the pad's Home, **Select + Start** on a pad without
one, or **Esc** on a keyboard - and the game stops behind a menu with the game's last picture. **Holding the menu button for 2 seconds** is the same as
Reset: it leaves the game. L1 / R1 switch between its three tabs, and the menu opens on the tab and row it
was left on:

- **Game**: *Resume game*; under *Saves*: *Quick save*, *Quick load* and *Load autosave* (the game as it was up to 30 seconds ago -
  the emulator saves it in memory while you play); under *CD disc*: *Change disc* and *Reset game* (starts it over);
  *Save settings for this game* (see section 3.7), *PCSX menu* (PCSX-ReARMed's own pages: options, cheats, About) and *Exit* (back to AutoBleem).
- **Picture**: *Display* (the screen's resolution - on the console it is chosen in Options and only shown here), *Resolution*
  (1x or 2x), *Remove seams*, *Dithering*, *Scaling*, *Smoothing*, *Filter*, *Scanlines* and *Scanline brightness*. Each row has a help line on
  the right. CRT-Pi is too heavy for the console at 1080p. A row that does not apply is greyed, and its help says why.
- **Controllers**: *Controller 1* and *Controller 2*: standard (digital), analog (DualShock), a gun or none; takes effect when the game goes on.

The menu is drawn in the launcher's ab2.0.0 look, with the pad batteries and the last quick save's picture.

A **RetroArch** game starts in RetroArch with the core the launcher chose for its system; *Close Content*
or *Quit RetroArch* in its menu comes back to the launcher. The RetroArch item in the system menu opens
RetroArch's own menu (XMB) with nothing loaded, for its settings and its own content lists. The cores window
opens with *PlayStation 1* first.

![The RetroArch cores window](../images/en/retroarch-cores.jpg)

An **App** (the Apps set: the console tools, and on a console the extra applications RetroArch's package
brings - Doom, Quake, Amiga, ...) shows its read-me first; Cross starts it, Circle goes back.

![An App's read-me before it starts](../images/en/app-start.jpg)

**An App's settings.** *Game settings* ("Change how this program is started") has *Pad mode:* (*Automatic*,
*PSC pad*, *Xbox 360 pad*, *PSC pad (system)*, *Xbox 360 pad (system)*), *D-pad as stick:* and *Stick as D-pad:*.
Some Apps ask once, on the first start, *Which controls does your pad have?* (*One D-pad* or *Analog sticks*);
a Windows-type App asks *What do you want to do?* (*Run Windows*, *Install Windows*, *Run DOS*, *Uninstall
Windows*). To map a key the screen says *Press one of the buttons.*

![An App's game settings](../images/en/app-game-settings.jpg)

The texts and questions a Windows program (a PE app) asks appear as AutoBleem screens (*Message*, *Choose an
option*), titled with the App's name.

![A question from a PE app](../images/en/pe-dialog.jpg)

### 3.8a A disc in a USB drive

A USB CD/DVD drive with a PlayStation or audio disc in it puts that disc on the shelf as a game. Not on
Windows, which has no drive support.

- **The disc view** opens by itself when a disc is detected; R1 *Disc* opens it from the shelf. It shows
  the disc's cover (from the cover databases, or fetched online), its serial and its title. Cross plays the
  disc. A PS1 game played from the disc resumes and saves into the disc's folder. After a game, the options or
  an extension's settings, you are back in the disc view; Circle on the shelf brings it back, and there R1 is the
  first-letter jump again.
- **The drive chip** shows the drive's state: hidden with no drive, dim with a drive and no disc,
  blinking *Reading the disc...* while it reads, then the disc's title. Other messages are *This is not a
  PlayStation disc* and *The disc cannot be read now*.

![The disc view](../images/en/disc-view.jpg)

![The drive chip](../images/en/disc-chip.jpg)

- **An audio CD** opens the **CD player** (*CD PLAYER*, *Audio CD*, with *TRACKS* and *TOTAL TIME*). Its keys
  are *Play track*, *Stop*, *Previous/next*, *Seek*, *Pause*, *Repeat:* (off or on) and *Shuffle:*, and *Selected:*
  names the track. A disc that does not play says *This disc cannot be played*.

![The CD player](../images/en/cd-player.jpg)

- **Copy disc** (Square) copies a PlayStation disc to `Games` as a **CHD**, with a `.m3u` file for a game on
  several discs (disc 1 first). It asks first: *Copy "%1" to %2? It takes %3 of the %4 free.* A progress
  window, *Copying the disc*, shows the *Speed* and the *Time left* and blocks the launcher; *Abort* cancels
  it (*Cancelling...*, then *Cancelled*). At the end it says *The disc is copied to Games.* It refuses with
  *Already in Games: %1*, *Not enough room in Games: the copy needs %1, %2 is free.* or *The copy failed: %1*. Sectors
  that cannot be read are written as zeros, and the message *%1 sectors could not be read and were written as zeros.* tells
  you how many (*Unreadable sectors*). A disc the databases do not know is named by its serial.

![Copying a disc](../images/en/disc-copy.jpg)

- **LibCrypt discs**: the `.sbi` file of a LibCrypt game is fetched from the site before the disc plays and
  when it is copied. That needs a network: on a Raspberry Pi or PC the one it already has, on the console the
  Wi-Fi set up in PSC-Bios.
- The game editor of a disc greys the rows it cannot use (section 3.7).

### 3.9 Adding games

**PS1 games** go into the `Games` folder, **one folder per game**, named after the game:

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                a folder of games: a group of its own in the set picker
    Klonoa/                   Klonoa.pbp
```

- Formats: `.cue` + `.bin` (or `.img`), `.pbp`, `.chd` (zstd too), `.ecm` (decoded by the scan), `.iso`.
  A zipped game works too: the **Unzip** processor unpacks it before the scan (section 3.13).
- A multi-disc game is one folder with every disc in it; folders named `Game (Disc 1)`, `Game (Disc 2)`
  ... are merged into one `Game` folder by the scan.
- Games dropped straight into `Games/` (loose files) are sorted into folders by the scan.
- A **cover** is a PNG or JPEG next to the game's image, named like it. Without one, the box art comes from the
  cover databases, or - with RetroArch installed - from libretro's thumbnail set; on a Pi, a PC or Windows
  a missing one is fetched online (Options → *Fetch box art online*).
- The scan reads each disc's serial number and takes the title, publisher, year, players and region from
  RetroArch's PlayStation database or the cover databases. Change anything in the game editor and tick
  *Lock data* to keep it.

**Other systems** go under `RetroArch/roms/`, **one folder per system, named as RetroArch's databases
are** (the folder is made for you): `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo
Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance`, `FBNeo - Arcade Games`
(or `Arcade`), ... ROMs may stay zipped. On a Pi, a PC or Windows the scan reads them by itself and writes
RetroArch's play lists; on a console stick, run **UpdateRoms** on the PC (chapter 5).

**Apps** go under `Apps/<name>/` with an `app.ini` (the name, the icon, what to run) and a `run.sh`.

**Packages.** Game data for engines - Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow
Warrior, Theme Hospital, DOS games and more - goes into a `Packages` folder on the stick, for example
`Packages/Doom/DOOM2.WAD`. AutoBleem recognises the data by a table that ships with it (`rc/packages.ini`); the loose
game files of a recognised folder are packages of their own. Your own files are only read, never changed. A package
can also come from the Store. The **Packages picker** lists what was found. **Package info** shows a package's
*Contents*, *Description*, *Location*, *Source*, *Runs with*, *Mod*, *Shareware*, *In this App* and *Your files*,
and *Choose game data* picks the data to start with. The messages are *No game data found*, *Unknown data*, *Nothing
installed runs this*, *%1 needs game data it can run: %2.* and *Not recognized. If this is a game, see the manual:
Your own games.*

![The Packages picker](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Scanning one part.** *Re-scan games* can scan just one part - a set or a folder - and takes its bubble down at
the end.

**Themes** go under `Themes/<name>/` (`theme.json` and the images) - or drop the theme's zip into `Themes/`.

### 3.10 The PS1 BIOS

On a **PlayStation Classic** the emulator uses the console's own BIOS. On a **Raspberry Pi, a PC and
Windows** put your own PS1 BIOS into `System/Bios/`: `romw.bin` (the US/European SCPH-5501/5502) and
`romJP.bin` (the Japanese SCPH-5500). The installers fill them from the RetroArch BIOS packs unless your
own files are already there. Without them the emulator runs on its built-in HLE BIOS, which many games
tolerate and some do not.

### 3.11 Updates

The launcher checks the site at start and once a day for a new version on its **channel** (Options →
*Updates*: `release`, `testing`, `nightly` or `off`); *Software Update* in the system menu checks now. When
there is one it asks: *Update now* downloads it, *Remind me tomorrow* and *Skip this version* are the other
answers. Your games, saves and settings always stay; the launcher rescans once after an update. The channel
tag in the top-left corner (section 3.1) shows what is installed.

- **Raspberry Pi, PC stick**: after the download the installer runs again with its first-boot progress
  screen (a newer RetroArch is offered too), then the launcher is back.
- **Windows**: the downloaded setup opens, installs, and starts the new launcher.
- **PlayStation Classic**: only a console with the **AutoBleem kernel** (ABFlashKit, section 6.2) and a
  **WiFi network** set up in PSC-Bios (section 6.1) checks - a stock console has no network, and the
  launcher does not look. After *Update now* the launcher closes, the AutoBleem picture stays on screen
  while the stick is updated (a few minutes), and the new launcher starts. Without a network *Software
  Update* says *Not connected*. Any console stick can also be updated from a PC with
  `AutoBleemInstaller.exe` (section 2.1).

### 3.12 Extensions and the AutoBleem Store

**Extensions** add their own screens to the launcher. They live in `Extensions/<name>/` on the stick (on a
Raspberry Pi its data partition, on Windows the data folder); to install one, unpack its zip there.
**L2 + R2 → Extensions** lists them: Cross runs one, Triangle turns it off or on again. An extension that
needs the network is not started without one, and one that stopped the launcher is turned off - the list
says so.

![The Extensions list](../images/en/extensions.jpg)

**The AutoBleem Store** is the first extension: Apps and games to install with one press, on every system
AutoBleem runs on (a PlayStation Classic needs the AutoBleem kernel's WiFi). Its four tabs, L1 / R1 between
them:

- **Apps** and **Games**: what the sources offer (the Apps tab also lists PE apps, with their license and source, and game-data packages, section 3.9), each with its picture, version, size and source favicon. Installed items carry an *Installed* badge. Cross installs (or updates, or tries again after a failure, or cancels a download that is queued or running), Triangle removes what the Store installed, Square refreshes the lists. L2 / R2 jump by letter, **Select** shows one source at a time, **Start** searches the titles. The footer shows the keys that apply to the selected row. Item pictures are cached and can be retried if they fail to load.
- **Downloads**: what is downloading, waiting, failed or installed. The progress bar updates steadily, and while you are elsewhere in the launcher a bubble shows the running download with its speed and the time left (`1.4 MB/s · 0:42`). Downloads go on in the background, also after you leave the Store; starting a game or powering off only pauses them, and a stopped download resumes where it stopped. If the network drops, the item says *Waiting for the network* and carries on from where it stopped when the network is back (it gives up after 30 minutes). An installed game appears on the shelf after the next scan, with the Store's picture as its cover. Downloads over 2 GB work on all platforms, including 32-bit builds.
- **Sources**: where the lists come from - AutoBleem's own catalog, a TSV list dropped into
  `System/Extensions/store/sources/`, and the addresses you add with **Add a source URL**. Each source shows its favicon in the list. Cross on one you added renames it, changes its address, switches it between `http://` and `https://`, or removes it.

![The Store's Apps tab](../images/en/store-apps.jpg)

![A source's menu](../images/en/store-source-menu.jpg)

What AutoBleem's catalog offers is also listed on the download site, `https://autobleem.retromenele.pl/store/`.
**You are responsible for what the sources you add contain.**

**Your own games on your network**: `abstored`, the Store's LAN server, serves a folder of PS1 games to
the Store on the same network. It runs on any Linux machine - a Raspberry Pi, a home server - and only reads
the folder. Start it with `abstored <games folder>`, open `http://<that machine>:8124/` in a browser to see
what it serves and any problems it found, and add `http://<that machine>:8124/store.tsv` as a source. Ready
programs for Linux and Windows are on the Store's page, in its **LAN server** tab; setting it up as a service
is `INSTALL-linux.md` (`ext_store/server/` in the source). **LAN Share** (section 5.2) puts games and discs
from a PC on such a server.

### 3.13 Scanner processors

**Scanner processors** are small programs that every scan runs before it reads your games. One can turn a
format AutoBleem does not read into one it does - a zipped game, for example - or change a game's data, such
as a translation patch. They live in `System/Processors/<name>/` on the stick (on a Raspberry Pi its data
partition, on Windows the data folder); to install one, unpack its folder there. The next scan runs it.

- **Unzip comes with AutoBleem**: it unpacks zipped PS1 games in `Games/` before the scan reads them, and
  zipped ROMs one at a time (arcade sets stay zipped). Updating AutoBleem updates it too, and leaves it
  switched off if you switched it off.
- A processor that has already dealt with a game is not run on it again until the game changes.
- While a processor works, the bubble at the top right shows what it is doing; a warning or a failure appears
  on the line under it. `processors.log` in the logs folder has the details.
- Starting a game or RetroArch stops a processor that changes files; the next scan finishes its work.

**L2 + R2 → Scanner processors** shows them in the order they run, one tab for the PS1 games and one for the
ROMs (L1 / R1). **Square** picks a processor up and Up / Down move it - the order matters: a processor that
unpacks has to come before one that patches what was unpacked. **Cross** switches one off or on, **Triangle**
has it look at every game again at the next scan, **Circle** goes back and starts a scan if you changed
anything. A processor built for another machine stays on the list, greyed.

![Scanner processors](../images/en/processors.jpg)

Writing your own: Unzip's page, `https://github.com/autobleem2/proc_unzip`, explains everything a processor
has to do, and
`tools/proc_check.py` in AutoBleem's source checks one before you share it.

<!-- pagebreak -->

## 4. Screens

### 4.1 Game Manager

The screen is titled *Game Manager - Select game*. The PS1 games as a list of their titles (the selected game's folder is in its details) and the selected one's cover. Cross opens the game
editor, **Square deletes the game** (its folder and, after a second question, its save states), Triangle
deletes every cover picture (PNG or JPEG) next to the games (the scan takes them from the databases again), L2 / R2 page.
The free space of the drive is at the top right. The Game Manager waits while a scan runs.

![The Game Manager](../images/en/game-manager.jpg)

### 4.2 Hardware Information

The machine's facts - system, hardware, storage with its free space, network addresses, the display and
audio drivers, the connected pads - re-read every second. It is the same page on every platform,
the console included; the network and controller setup screens are **Network & Controllers** (PSC-Bios, chapter 6).

The first two controllers are shown as Player 1 and Player 2 - the ports the PS1 emulator gives them.
Any further controller is shown as not used by the PS1 emulator. RetroArch assigns controllers by its own
settings and may order them differently. When a controller is plugged in or pulled out, the launcher
briefly shows which pad is Player 1 and Player 2. Circle returns to the system menu.

![Hardware Information](../images/en/hardware-info.jpg)

### 4.3 The button guide

Triangle on the shelf: every button of every screen on one page. When a USB keyboard is connected or has been used, a Keyboard column shows the keys alongside the pad buttons. Two lines explain the way out of a game: *Hold
Select+Start or Home for 2 seconds: back to AutoBleem* and *Short press of Select+Start or Home: the emulator's menu*.

![The button guide](../images/en/button-guide.jpg)

### 4.4 The on-screen keyboard

Wherever text is typed - a memory card set, a game's title, a WiFi password, a source's address - the same
keyboard, laid out like a phone's: letters, a page of symbols (`/ \ : ? & = % @ #` and the rest an address
or a password needs) and two pages of accented letters, with Shift, the page key, Space, Backspace and
Confirm on the bottom row. The directions move, Cross types, Triangle deletes, Square is a space, **L1** is
Shift (twice for caps lock), **R1** the next page, **L2 / R2** move the cursor, Start confirms, Circle
cancels. A USB keyboard types at any time: Enter confirms, Esc cancels.

![The on-screen keyboard](../images/en/keyboard.jpg)

### 4.5 Virtual gamepad

*Virtual gamepad* in the system menu shows the pads as the program that serves them sees them. It has three
parts: *The pads Apps are given*, *Pads the daemon sees* and *Daemon*. A pad can carry the marks *connected*,
*not readable*, *from the controller database*, *guessed by the daemon* or *unknown driver*, and *Look again*
reads the pads once more. A part the build does not have says *Not in this build*. Circle returns to the system menu.

![Virtual gamepad](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. On the PC

### 5.1 UpdateRoms - refreshing a console stick

The PlayStation Classic has no network, so the RetroArch lists and box art of its stick are made on the PC:
**UpdateRoms** does on the PC what the launcher's scan does on a Pi, with the PC's network and the console's
paths, so the console boots and finds everything in place.

1. Copy your ROMs onto the stick under `RetroArch/roms/<system>/` (section 3.9). The folder names must be
   RetroArch's database names; the installer makes the common ones.
2. Start **`UpdateRoms\UpdateRoms.exe` from the stick** (the installer put it there). It finds the stick from
   where it sits, shows a stage line, a progress bar and a log, and:
   - downloads RetroArch's database bundle when the stick has none, and identifies every ROM by it - a
     game the database knows gets its proper name;
   - writes one play list per system into `RetroArch/bin/playlists/` with the console's paths, keeping
     whatever RetroArch itself added there;
   - fetches the box art of every ROM that has none from libretro's thumbnail servers into
     `RetroArch/bin/thumbnails/`.
3. Take the stick out safely and put it back into the console. The RetroArch tab of the set picker lists
   every system that has games.

Run it again after every change to the ROM folders; a folder nothing changed in is skipped, so a re-run is
quick. The log is `System/Logs/updateroms.log`. A Raspberry Pi card in a card reader can be refreshed the
same way (`UpdateRoms.exe <drive> --target rpi`), though a Pi does it by itself when it has a network.

### 5.2 LAN Share - your games and discs on the server on your network

**LAN Share** (`LanShare.exe`, on the Store's page in its **LAN server** tab) puts your PS1 games on the
Store's server on your home network - an `abstored` on a Raspberry Pi, a NAS or another PC - and reads a PS1
disc in the PC's CD/DVD drive for it. The Store on the console, the Pi or the PC then installs them from there.
Nothing to install; the settings are kept in `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![The LAN Share window](../images/en/lanshare.jpg)

1. **The server**: enter its address (`http://<its address>:<port>`, as the Store has it) and press
   **Connect**. Its games and any problems its scan found are listed on the left. To put games on it, give
   one of:
   - **Share** - the server's games folder as it is shared on the network (Samba), e.g. `\\raspberrypi\games`:
     LAN Share copies the games there and asks the server to scan. The server itself stays read only.
   - **Token** - when the server was started with `--allow-uploads`: its token (the server prints it at start
     and keeps it in `<state>/upload-token`). LAN Share uploads over HTTP, and a stopped upload goes on where
     it stopped.
2. **Games on this PC**: choose a folder of games (one folder per game), tick games and press **Publish the
   ticked games**. **On the server** says whether the server has a game already (by its serial, else by its
   title); such a game is never sent twice. **Tick those not on the server** ticks the rest.
3. **A disc**: put a PS1 disc in the drive and press **Read a disc and publish it**. The disc is read whole
   into a `.bin` + `.cue` (and an `.sbi` for a LibCrypt game, when the drive gives the subchannel), named
   after its title, checked against the known good dump (when the databases are chosen) and published. For
   a game on several discs tick **The game has more than one disc**: LAN Share asks for each next disc and
   publishes them together as one game.
4. **Remove from the server...** takes the selected games off the server. Nothing is deleted: each is moved
   into a `.removed` folder next to the server's games, and moving it back puts it back.

The **Databases** - AutoBleem's covers folder (`coversU/P/J.db`) and RetroArch's `Sony - PlayStation.rdb` -
give the titles and the check of a read disc; both are optional. **Also share the games on this PC with the
Store** (off by default) serves the folder on this PC to the Store directly. The first time, Windows asks about
its firewall: allow private networks only.

<!-- pagebreak -->

## 6. The console tools (PlayStation Classic)

Two tools for a PlayStation Classic stick. Both draw in the launcher's theme and language, and both are
driven by the pad - and, in the gamepad wizard, by the console's front buttons. **PSC-Bios** is an
extension that comes with the console package: the *Network & Controllers* item of the Quick menu and the system menu opens it, and it
is in the Extensions list. **ABFlashKit** is an App in the Apps set.

### 6.1 PSC-Bios

An extension that comes with the console package, also available on a Raspberry Pi and the PC stick. It is
opened from the System menu's *Network & Controllers* item (or from the Extensions list). When that extension is installed but disabled, the *Network & Controllers* item in the Quick menu and System menu is greyed out with a note "enable it in Extensions" - Cross there opens the Extensions list at it.

The opening screen shows machine facts: time, timezone, WiFi/Ethernet/Bluetooth network adapters with their
addresses, and every connected controller with whether it has a button mapping. The network and Bluetooth
parts need the AutoBleem kernel on the console (section 6.2) or system tools on a Raspberry Pi / PC stick;
the gamepad wizard works on any system.

![PSC-Bios: the Network & Controllers hub](../images/en/pscbios-main.jpg)

- **Select - Wi-Fi Network** (kernel or NetworkManager): the network name (typed, or picked from a
  scan), password, driver mode, and *Apply / Restart Network*. The time zone is set here too. The console's IP address is shown once connected.
- **Square - Bluetooth Controllers**: a scan for Bluetooth gamepads (DualShock 4, etc.), to pair or remove.
- **L1 - DualShock 3 Pairing**: USB-only connection for the first DualShock 3, through the kernel's sixaxis plugin.
- **R1 - Controller Mapping**: the mapping wizard (below).
- **Triangle - About**, **Circle - back** to the launcher.

**The gamepad wizard** shows the connected pad raw - every axis, button and hat as numbers, and a
DualShock picture that lights up as you press. Because the pad under test cannot be trusted, the wizard
is driven by the console's **front buttons**: **RESET** switches to the next pad, **OPEN** starts the mapping
(then answers each question - press the button lit on the picture, or OPEN when the pad has no such
button), **POWER** cancels or leaves. Holding Circle on the pad for 2 seconds leaves the wizard (a bar fills and the footer hint says "Hold 2 s: Exit"). While the pad has no mapping yet, holding any button for 2 seconds does it ("Hold any button 2 s: Exit"). A short press is mapped as usual. On a keyboard, Esc / Space / Enter stand in for POWER / RESET / OPEN. At the end the new mapping is added for a test and OPEN saves it under a name of your choice; the launcher loads it from then on.

![PSC-Bios: the controller mapping wizard](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - the AutoBleem kernel

The AutoBleem kernel is an optional replacement of the console's Linux kernel: it brings a working clock,
USB WiFi and Bluetooth dongles (for PSC-Bios and Bluetooth pads) and the front-button support the emulator
uses for resume points. ABFlashKit installs it, backs the console up first, and can put the console back
to stock through Sony's own recovery.

> **This tool writes to the console's flash memory.** A flash that is interrupted - the power cut, the
> stick pulled - can leave the console unable to start, and installing a custom kernel voids its warranty.
> Keep the console powered and the stick in until it reboots by itself. ABFlashKit opens on this warning;
> *I understand* goes on, *Quit* leaves.

![ABFlashKit's menu](../images/en/abflashkit-menu.jpg)

- **Flash Kernel**: makes a recovery backup of the console's partitions on the stick (`LBOOT.EPB`) if there
  is none yet, checks it and the kernel image, writes the kernel and AutoBleem's system files, and reboots.
  *All done - when the screen goes black replace power cord*: pull the console's power and plug it back in.
- **Full backup**: all four partitions to `LBOOT.EPB`, for a restore later (the previous backup is
  overwritten after a question).
- **Restore Mode**: checks the backup is a stock one, sets the recovery flag and reboots into Sony's
  recovery, which restores the console from `LBOOT.EPB` on the stick - the way back to the stock firmware.

A progress bar under every step shows how far the action is. The tool refuses to flash a console that
runs another custom firmware (BleemSync, Project Eris): restore it to stock first.

**Logging in from a PC.** With the AutoBleem kernel installed (not on a stock console) you can log in to the
console over a USB cable:

1. Connect the console's micro-USB port to the PC with a USB cable. The PC shows the console as a new network
   adapter; the console's address is in that adapter's settings on the PC.
2. Log in with `ssh root@<the console's address>`. The default password is `autobleem`.

Instead of the password you can use a key: put your public key into the file `System/ssh/authorized_keys` on the
stick and restart the console. At the next boot it is added to the root account. Updating or reinstalling the launcher does not remove it.

> **The default password is the same on every console**: anyone who can plug a cable into it can log in as
> root. Use a key where you can, and do not leave a console with the default password where others can reach it.

<!-- pagebreak -->

## 7. If something goes wrong

- **Logs**: AutoBleem keeps its logs in memory, so the stick is not written to all the time - they reach
  `System/Logs/` on the stick, card or data folder only when something went wrong: a crash of the launcher,
  of a PS1 game or of RetroArch saves them to `System/Logs/crash-<n>/` (the last three are kept), and the
  launcher says so once when it comes back. To keep every log, switch on *Options -> Diagnostics -> Keep
  logs on the stick* (from the next start), or create an empty file `System/Logs/keep` on a PC. On a Pi or
  a PC, *Hardware Information* shows where the logs are and Square saves them to `System/Logs/saved-<n>/`.
  The files: `autobleem.log` (the launcher), `launch.log` and `pcsx.log` (a PS1 game's start and the
  emulator's output), `retroarch.log`, and - always on the stick - `update.log` (an online update) and
  `updateroms.log` (UpdateRoms).
- **The picture asks for a stick, or the console went to sleep**: there is no stick in the console, or it was
  pulled. Put it in (any USB port; a front one is best, section 2.1) before the 5 minutes are over, or press Power.
  A stick that was not removed cleanly is checked first - wait for the progress bar to finish.
- **RetroArch says it needs a newer system library than this console has**: the console's own library is too
  old for that RetroArch. Use the RetroArch that comes with AutoBleem.
- **A PSN game says it is protected by its PSN license and cannot be started**: that game cannot run on
  AutoBleem.
- **A game is not on the shelf**: check the folder layout (one folder per game, the image formats of
  section 3.9). The *Game Manager* lists the folders the scan refused after the games, marked *Not added*,
  with the reason; Square deletes such a folder. *Re-scan games* in the system menu runs the scan again.
- **No covers**: the cover databases were not installed (run the installer again with them ticked), or,
  for RetroArch games on a console, UpdateRoms has not been run on the PC.
- **A pad does nothing or has its buttons mixed up**: PSC-Bios's gamepad wizard (a console) maps it; on a
  Pi or PC the Hardware Information page lists what SDL sees.
- **The console shows a black screen after a game**: AutoBleem rebuilds its window by itself (up to three
  times); if it stays black, hold the power button and switch the console on again.
- **Raspberry Pi**: `Alt+F2` gives a login prompt on the second console; SSH is enabled from the first boot.
  `sudo journalctl -u autobleem` shows the launcher's service; `sudo systemctl restart autobleem` restarts it.
  A first boot that could not finish (no network) retries on the next boot.
- **Windows**: `Esc` leaves the launcher; the data folder is the one chosen in the setup
  (`Documents\AutoBleem` by default), the logs are in its `System\Logs`.

**The console restarts again and again after an online update (stick formatted as ext4).** Some users format the stick as ext4 (Linux) instead of FAT32 or exFAT. Until the next AutoBleem release, the online update on such a stick unpacked every file without its executable permission, so AutoBleem does not start and the console restarts over and over. FAT32 and exFAT sticks are not affected.

**Fix A** (needs a Linux PC): plug the stick in and make the AutoBleem programs executable again. Use your own mount path instead of `/media/USER/STICK` (the last line is only needed if RetroArch is installed):

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Fix B**: install the newest AutoBleem release onto the stick again, as in section 2.1 (the installer needs a PC that can read the stick; a stick it cannot read has to be formatted first, which erases it - copy your games off first).

> Use **FAT32** (a stock console reads FAT32 only; exFAT needs the AutoBleem kernel, chapter 6) - the next release keeps the permissions and AutoBleem repairs them at every start.

AutoBleem is free software (GNU GPL v3 or later), with no warranty. Support and news: the Discord server
linked on the About screen, and https://autobleem.retromenele.pl/.
