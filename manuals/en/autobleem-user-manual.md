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

The Game Manager is where you tidy up your PS1 library. Use it when you want to remove a game you no longer
play, open a game's settings without first finding it on the shelf, or make AutoBleem fetch every cover
again. Open it from the system menu (L2 + R2, *Game Manager*). While a scan is running it is greyed out, and
it waits until the scan has finished.

The screen is titled *Game Manager - Select game*. On the left you see all your PS1 games as a list of titles
in alphabetical order; on the right, the selected game's cover with its publisher, year, serial and the folder
it is in. The free space left on the drive is shown at the top right, so you can see how much room a delete
gives you back. Up and Down move through the list, L2 / R2 turn a page and L1 / R1 jump to the first or the
last game.

- **Cross** opens the selected game in the game editor - the same editor as the Game icon on the shelf
  (section 3.7). When you leave it, you are back on the same game in the list.
- **Square deletes the game.** AutoBleem asks you first, then removes the game's whole folder. If the game's
  save states and memory card are not used by any other game, it asks a second question: whether to delete
  those too. Say no if you might want the game back later with your saves.
- **Triangle deletes every cover picture** (PNG or JPEG) that sits next to your games, after a question. This
  is useful when you have collected covers you do not like: the next scan takes the covers from the cover
  databases again.

At the end of the list, after the games, you may see folders marked *Not added*. These are folders in `Games`
that the scan looked at but could not turn into a game. Select one and the right side tells you where it is
and why it was not added - a missing cue file, for example (chapter 7). Square deletes such a folder after a
question. When you leave with Circle after changing something, AutoBleem scans the games again.

![The Game Manager: the list of games on the left, the selected game's cover and details on the right](../images/en/game-manager.jpg)

### 4.2 Hardware Information

Hardware Information is the page to look at when you want to know what your machine is and what it sees: how
much room is left on the stick, which network address it has, which display and audio drivers it uses, and
which pads are connected. It is the same page on every platform, the console included. Open it from the
system menu (L2 + R2, *Hardware Information*); Circle takes you back to the system menu.

The page shows the system, the hardware, the storage with its free space, the network addresses, the display
and audio drivers and the connected pads. It reads everything again every second, so you can leave it open
while you plug a pad in or connect a cable and watch the change appear. It only shows things - to set up the
network or a pad, use *Network & Controllers* (PSC-Bios, chapter 6).

The pads part answers the question "which pad is which player?". The first two pads are shown as *Player 1*
and *Player 2* - the ports the PS1 emulator gives them. Any further pad is shown as *not used by the PS1
emulator*. RetroArch gives out the ports by its own settings, so in a RetroArch game the order may be
different. You do not have to open this page every time: whenever a pad is plugged in or pulled out, the
launcher briefly shows which pad is now Player 1 and which is Player 2.

![Hardware Information: the machine's facts and the connected pads](../images/en/hardware-info.jpg)

### 4.3 The button guide

If you forget what a button does somewhere, press **Triangle** on the shelf. The button guide shows every
button of every screen on one page, so you can look it up without leaving the launcher. If a USB keyboard is
connected, or has been used, a *Keyboard* column shows the matching key next to each pad button.

The guide also reminds you of the one thing worth remembering for every game: how to get out of it. Hold
Select + Start, or Home, for 2 seconds to go back to AutoBleem; a short press opens the emulator's menu
instead.

![The button guide: every screen's buttons, with the keyboard keys beside them](../images/en/button-guide.jpg)

### 4.4 The on-screen keyboard

Whenever AutoBleem needs you to type something - the name of a memory card set, a game's title, a WiFi
password, the address of a Store source - the same on-screen keyboard appears, so you can type with the pad
alone. It is laid out like a phone's keyboard. Besides the letters it has a page of symbols, with
`/ \ : ? & = % @ #` and the rest of what an address or a password needs, and two pages of accented letters.
The bottom row holds Shift, the key that changes the page, Space, Backspace and Confirm.

Move over the keys with the directions and press **Cross** to type the one under the cursor. **Triangle**
deletes a letter and **Square** types a space. **L1** is Shift; press it twice for caps lock. **R1** goes to
the next page of keys, and **L2 / R2** move the cursor inside the text. **Start** confirms what you typed and
**Circle** cancels. If a USB keyboard is connected, you can type on it at any time instead: Enter confirms and
Esc cancels.

![The on-screen keyboard](../images/en/keyboard.jpg)

### 4.5 Virtual gamepad

Apps - the programs in the Apps set, such as Doom or Quake - do not read your pad themselves. A small helper
program, the virtual gamepad daemon, reads the real pads and hands each App a pad it understands. This page
shows you which pads that helper sees and how it reads them. Look here when an App does not react to your pad,
or when its buttons are mixed up. Open it from the system menu (L2 + R2, *Virtual gamepad*); Circle takes you
back to the system menu.

Under *Pads the daemon sees* every pad is listed with a number and its name. Beside it you read three things:
whether the helper could open the pad (*connected*) or not (*not readable*); the driver the pad came through;
and where its button layout comes from - *from the controller database* means the pad is known and its buttons
are where they should be, *guessed by the daemon* means it is not known and the helper made its best guess. If
the buttons in an App feel wrong, a guessed layout is the likely reason.

The helper only runs while an App does, so the page asks it once when it opens. If you plug in a pad while the
page is open, press **Cross** (*Look again*) to ask again. On Windows there is no such helper, and the page
says *Not in this build*.

![Virtual gamepad: the pads the Apps' helper sees](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. On the PC

### 5.1 UpdateRoms - refreshing a console stick

On a Raspberry Pi, a PC or Windows the launcher's scan sorts your RetroArch games into lists and fetches their
box art by itself. The PlayStation Classic cannot do that, because it has no network of its own. **UpdateRoms**
does that work on your Windows PC instead: it uses the PC's network but writes everything with the paths the
console expects, so when you put the stick back, the console starts and finds everything in place. Run it
whenever you have added or removed RetroArch games on a console stick.

1. Copy your ROMs onto the stick under `RetroArch/roms/<system>/` (section 3.9). The folder names must be
   RetroArch's database names; the installer has already made the common ones.
2. Start **`UpdateRoms\UpdateRoms.exe` from the stick** - the installer put it there. It works out by itself
   which stick it is on. While it works you see a line saying what it is doing, a progress bar and a log.
   - If the stick has no RetroArch database yet, it downloads RetroArch's database bundle first. It then
     identifies every ROM with it, so a game the database knows gets its proper name.
   - It writes one play list per system into `RetroArch/bin/playlists/`, with the console's paths. Anything
     RetroArch itself added to those lists is kept.
   - For every ROM without box art, it fetches a cover from libretro's thumbnail servers into
     `RetroArch/bin/thumbnails/`.
3. Remove the stick safely and put it back into the console. The RetroArch tab of the set picker now lists
   every system that has games.

You can run it as often as you like: a folder where nothing has changed is skipped, so a second run is quick.
If something goes wrong, the log is `System/Logs/updateroms.log` on the stick. A Raspberry Pi card in a card
reader can be refreshed the same way, with `UpdateRoms.exe <drive> --target rpi`, though a Pi does this by
itself when it has a network.

### 5.2 LAN Share - your games and discs on the server on your network

The Store can install games from a server on your own home network (section 3.12). **LAN Share** is the
Windows program that fills that server from your PC: it puts the PS1 games you have on the PC onto the server,
and it can read a PS1 disc in the PC's CD/DVD drive and put it there too. The server is an `abstored` running
on a Raspberry Pi, a NAS or another PC. Once a game is on it, the Store on the console, the Pi or the PC can
install it from there.

You get `LanShare.exe` from the Store's page, in its **LAN server** tab. There is nothing to install: start it,
and it keeps its settings in `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![The LAN Share window: the server's games on the left, the games on this PC on the right](../images/en/lanshare.jpg)

1. **Connect to the server.** Enter its address the way the Store has it, `http://<its address>:<port>`, and
   press **Connect**. The games already on the server, and any problems its own scan found, appear on the left.
   To put games on the server, LAN Share needs one of two ways in:
   - **Share** is the server's games folder as it is shared on your network (Samba), for example
     `\\raspberrypi\games`. LAN Share copies the games into it and asks the server to scan; the server itself
     still only reads its folder.
   - **Token** is for a server started with `--allow-uploads`. Enter its token - the server prints it when it
     starts and keeps it in `<state>/upload-token`. LAN Share then uploads over HTTP, and an upload that stops
     part-way goes on from where it stopped.
2. **Publish the games on your PC.** Choose the folder your games are in (one folder per game), tick the ones
   you want and press **Publish the ticked games**. **On the server** tells you whether the server
   already has a game - it compares the serial, or the title when there is no serial - and a game the server
   has is never sent twice. **Tick those not on the server** ticks all the others for you.
3. **Publish a disc.** Put a PS1 disc in the PC's drive and press **Read a disc and publish it**. LAN Share
   reads the whole disc into a `.bin` + `.cue`, named after the game's title. For a LibCrypt game it also
   writes the `.sbi` file, when the drive can read the subchannel. If you chose the databases (below), it
   checks the copy against the known good dump. Then it publishes the game. For a game on several discs, tick
   **The game has more than one disc** first: LAN Share asks you for each next disc and publishes them
   together as one game.
4. **Take games off the server.** Select them and press **Remove from the server...**. Nothing is deleted:
   each game is moved into a `.removed` folder next to the server's games, and moving it back puts it back.

The **Databases** are optional. If you point LAN Share at AutoBleem's covers folder (`coversU/P/J.db`) and
RetroArch's `Sony - PlayStation.rdb`, it uses them to name the games and to check a disc it has read.

If you would rather not copy anything, tick **Also share the games on this PC with the Store** (it is off by
default): LAN Share then serves the games folder on your PC to the Store directly. The first time you do this,
Windows asks about its firewall - allow private networks only.

<!-- pagebreak -->

## 6. The console tools (PlayStation Classic)

Two tools come with a PlayStation Classic stick and help you set the console up beyond what it can do out of
the box. Both look like the rest of the launcher, in its theme and language, and you work them with the pad -
in the gamepad wizard also with the console's front buttons. **PSC-Bios** is an extension that comes with the
console package: the *Network & Controllers* item in the Quick menu and in the system menu opens it, and you
also find it in the Extensions list. **ABFlashKit** is an App, in the Apps set.

### 6.1 PSC-Bios

PSC-Bios is where you connect the machine to the world: your WiFi network, the time zone, Bluetooth pads, and
the button layout of a pad AutoBleem does not know. It comes with the console package and is also there on a
Raspberry Pi and the PC stick. Open it with *Network & Controllers* in the system menu (or the Quick menu), or
from the Extensions list. If the extension is installed but switched off, the *Network & Controllers* item is
greyed out and says it *is switched off - enable it in Extensions*; press Cross on it and the Extensions list
opens at PSC-Bios, so you can switch it back on.

The first screen gives you an overview: the time and the time zone, the network adapters (WiFi, Ethernet,
Bluetooth) with their addresses, and every connected pad, with a note whether it has a button mapping. On the
console, the network and Bluetooth parts need the AutoBleem kernel (section 6.2); on a Raspberry Pi or the PC
stick they use the system's own tools. The gamepad wizard works everywhere.

![PSC-Bios: the Network & Controllers hub](../images/en/pscbios-main.jpg)

From the first screen, one button takes you to each part:

| Button | What it opens |
|---|---|
| Select | **Wi-Fi Network** connects you to your WiFi (through the kernel, or NetworkManager on a Pi or PC): type the network's name or pick it from a scan, enter the password, choose the driver mode and press *Apply / Restart Network*. You set the time zone here too, and once you are connected you see the console's IP address. |
| Square | **Bluetooth Controllers** searches for Bluetooth pads such as the DualShock 4, so you can pair a new one or remove one you no longer use. |
| L1 | **DualShock 3 Pairing** connects your first DualShock 3, which has to be plugged in by USB for this, through the kernel's sixaxis plugin. |
| R1 | **Controller Mapping** opens the gamepad wizard, described below. |
| Triangle | **About** shows what PSC-Bios is. |
| Circle | **Back** takes you out of PSC-Bios, back to the launcher. |

**The gamepad wizard.** Use it when a pad does nothing in AutoBleem or has its buttons in the wrong places. It
shows the connected pad as it really is - every axis, button and hat as numbers - and a DualShock picture that
lights up as you press. Because the pad you are testing cannot be trusted yet, you drive the wizard with the
console's **front buttons**: **RESET** switches to the next pad, **OPEN** starts the mapping, and **POWER**
cancels or leaves. During the mapping the wizard asks for one button after another: press the button that is
lit on the picture, or OPEN if your pad has no such button. A short press is mapped as usual.

You can also leave from the pad: hold Circle for 2 seconds - a bar fills up and the footer says *Hold 2 s:
Exit*. While the pad has no mapping yet, holding any button for 2 seconds does the same (*Hold any button 2 s:
Exit*). On a keyboard, Esc, Space and Enter stand in for POWER, RESET and OPEN.

At the end the new mapping is put into use so you can try it out, and OPEN saves it under a name you choose.
From then on the launcher loads it every time.

![PSC-Bios: the controller mapping wizard](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - the AutoBleem kernel

The AutoBleem kernel replaces the console's own Linux kernel, and it is optional. You want it if you want more
from the console: it gives it a working clock, makes USB WiFi and Bluetooth dongles work (for PSC-Bios and
Bluetooth pads), and adds the front-button support the emulator uses for resume points. ABFlashKit is the tool
that installs it. It backs up the console first, and it can also put the console back to stock through Sony's
own recovery.

> **This tool writes to the console's flash memory.** If writing is interrupted - the power is cut, or the
> stick is pulled out - the console may no longer start, and installing a custom kernel voids its warranty.
> Keep the console powered and the stick in until the console restarts by itself. ABFlashKit opens on this
> warning: *I understand* goes on, *Quit* leaves.

![ABFlashKit's menu](../images/en/abflashkit-menu.jpg)

ABFlashKit has three actions:

- **Flash Kernel** installs the kernel. If there is no recovery backup on the stick yet, it first makes one of
  the console's partitions (`LBOOT.EPB`). It checks the backup and the kernel image, writes the kernel and
  AutoBleem's system files, and restarts the console. When it says *All done - when the screen goes black
  replace power cord*, wait for the black screen, then pull the console's power cable and plug it back in.
- **Full backup** saves all four of the console's partitions to `LBOOT.EPB`, so you can restore them later. If
  there is already a backup, it asks before it overwrites it.
- **Restore Mode** is the way back to the stock firmware. It checks that the backup on the stick is a stock
  one, sets the recovery flag and restarts into Sony's recovery, which restores the console from `LBOOT.EPB`.

A progress bar under every step shows how far it has got. ABFlashKit will not flash a console that runs
another custom firmware, such as BleemSync or Project Eris: restore that console to stock first.

**Logging in from a PC.** If you know Linux and want to look inside the console, you can log in to it from a
PC over a USB cable. This needs the AutoBleem kernel; it does not work on a stock console.

1. Connect the console's micro-USB port to the PC with a USB cable. The PC sees the console as a new network
   adapter, and you find the console's address in that adapter's settings on the PC.
2. Log in with `ssh root@<the console's address>`. The default password is `autobleem`.

Instead of the password you can use a key. Put your public key into the file `System/ssh/authorized_keys` on
the stick and restart the console: at the next start it is added to the root account. Updating or reinstalling
the launcher does not remove it.

> **The default password is the same on every console**, so anyone who can plug a cable into yours can log in
> as root. Use a key where you can, and do not leave a console with the default password where others can
> reach it.

<!-- pagebreak -->

## 7. If something goes wrong

Most problems have a simple cause. Below, each one starts with what you see, says why it happens and then what
to do. If you need to ask for help, the logs are the first thing anyone will ask for, so that comes first.

**Finding the logs.** AutoBleem keeps its logs in memory while it runs, so that the stick is not written to all
the time. They reach `System/Logs/` on the stick, the card or the data folder only when something went wrong:
when the launcher, a PS1 game or RetroArch crashes, the logs are saved to `System/Logs/crash-<n>/` (the last
three crashes are kept), and the launcher tells you once when it comes back. If you are chasing a problem that
is not a crash, keep every log: switch on *Options -> Diagnostics -> Keep logs on the stick* (it works from the
next start), or create an empty file `System/Logs/keep` from a PC. *Hardware Information* (section 4.2) also
shows where the logs are, and Square there saves the current ones to `System/Logs/saved-<n>/`.

These are the files you will find:

| File | What it tells you |
|---|---|
| `autobleem.log` | What the launcher itself did. |
| `launch.log`, `pcsx.log` | How a PS1 game was started, and what the emulator said while it ran. |
| `retroarch.log` | What RetroArch said while it ran. |
| `update.log` | How an online update went; it is always kept on the stick. |
| `updateroms.log` | How UpdateRoms went on the PC (chapter 5); it is always kept on the stick. |

**A picture asks you to put in the stick, or the console went to sleep.** AutoBleem cannot find its stick:
none was in when the console started, or it was pulled out. Put it into any USB port (a front one is best,
section 2.1) before the 5 minutes are over, or press Power. If the stick was not removed cleanly, AutoBleem
checks it first - wait for the progress bar to finish.

**RetroArch says it *needs a newer system library than this console has*.** That RetroArch was built for a
newer system than the console's, so it cannot run there. Use the RetroArch that comes with AutoBleem.

**A game says it *is protected by its PSN license and cannot be started*.** Games bought on the PlayStation
Network are locked to their license, and AutoBleem cannot run them. There is nothing to fix.

**A game is not on the shelf.** Usually its folder is not laid out the way the scan expects. Check that every
game has a folder of its own and is in one of the formats of section 3.9. The *Game Manager* (section 4.1) lists
the folders the scan refused after the games, marked *Not added*, and tells you why each was refused; Square
deletes such a folder. After fixing a folder, *Re-scan games* in the system menu runs the scan again.

**Games have no covers.** Either the cover databases were not installed - run the installer again with them
ticked - or, for RetroArch games on a console, UpdateRoms has not been run on the PC yet (chapter 5).

**A pad does nothing, or its buttons are mixed up.** AutoBleem does not know that pad's layout. On a console,
map it with PSC-Bios's gamepad wizard (section 6.1). On a Pi or a PC, the Hardware Information page (section
4.2) shows what SDL sees of the pad, which helps you tell whether it is detected at all.

**The screen stays black after a game on the console.** The launcher's picture did not come back when the game
ended. AutoBleem rebuilds its window by itself, up to three times. If the screen still stays black, hold the Power button and
switch the console on again.

**On a Raspberry Pi** you can get behind the launcher when you need to: `Alt+F2` gives you a login prompt on
the second console, and SSH is on from the first start. `sudo journalctl -u autobleem` shows what the
launcher's service did, and `sudo systemctl restart autobleem` restarts it. If the first start could not finish
because there was no network, it tries again at the next start.

**On Windows**, `Esc` leaves the launcher. Your data folder is the one you chose during the setup
(`Documents\AutoBleem` unless you changed it), and the logs are in its `System\Logs` folder.

**The console restarts again and again after an online update (stick formatted as ext4).** Some people format
the stick as ext4, the Linux file system, instead of FAT32 or exFAT. Until the next AutoBleem release, an
online update on such a stick unpacks every file without the permission that lets it run as a program. AutoBleem
then cannot start, and the console restarts over and over. FAT32 and exFAT sticks are not affected. There are
two ways to fix it.

**Fix A** needs a Linux PC. Plug the stick in and make the AutoBleem programs runnable again. Put your own
mount path in place of `/media/USER/STICK`; you only need the last line if RetroArch is installed:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Fix B**: install the newest AutoBleem release onto the stick again, as in section 2.1. The installer needs a
PC that can read the stick. If it cannot read yours, the stick has to be formatted first, which erases
everything on it - copy your games off it before you do.

> To avoid this, use **FAT32** (a stock console reads only FAT32; exFAT needs the AutoBleem kernel, chapter 6).
> The next release keeps the permissions and AutoBleem repairs them at every start.

AutoBleem is free software (GNU GPL v3 or later) and comes with no warranty. For support and news, join the
Discord server linked on the About screen, or visit https://autobleem.retromenele.pl/.
