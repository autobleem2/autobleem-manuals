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

- **The launcher** - the carousel of covers, the sets (PlayStation, RetroArch, Apps), the game details, the
  Quick menu and the system menu, the options, the memory-card and save-state tools, and the Store for
  downloading apps and games. The same program on every platform.
- **Two PS1 emulators** - `pcsx-abnxt`, the current one (the default), and `pcsx-ab`, the classic one
  AutoBleem has always shipped. You pick one in the options; both use the same settings and memory cards.
- **RetroArch** (optional on every platform) for the other systems: NES, SNES, Mega Drive, Game Boy, arcade
  and many more. AutoBleem builds its RetroArch lists from the ROMs you copy in and starts each game with
  the right core. The core list starts with *PlayStation 1* (section 3.8). Doom-type games run from your own
  game data in a *Packages* folder (section 3.9).
- **The console tools**: *PSC-Bios* (shown in the menus as *Network & Controllers*) for WiFi, the clock,
  Bluetooth and gamepad mapping - on the console, and also on a Raspberry Pi and the PC stick - and
  *ABFlashKit* for installing the AutoBleem kernel (PlayStation Classic only).
- **UpdateRoms** for Windows: refreshes the RetroArch lists and box art of a console stick on a PC, because
  the console itself has no network.

![The launcher: the shelf of covers, the selected game's details, the button hints](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Installation

### 2.1 PlayStation Classic

You need a Windows PC, a USB stick (USB 2.0, 8 GB or more) and the stock console. The stick does not have
to be empty and is **not formatted** unless you ask for it: AutoBleem is installed next to what is on it, and
a stick you already use with AutoBleem 1.0 is upgraded in place (below). AutoBleem runs from the stick
without any change to the console. The stick must be
**FAT32** for a stock console - its kernel cannot read exFAT. Only a console with the AutoBleem kernel
installed (ABFlashKit, chapter 6) also boots from an exFAT stick, which lifts FAT32's 4 GB file limit.

1. Download **AutoBleemInstaller-<version>.zip** from the PlayStation Classic panel of the site and unpack
   it anywhere. It holds `AutoBleemInstaller.exe` and its README; AutoBleem itself is downloaded while it
   installs, so the PC needs the internet.
2. Plug the stick in and start `AutoBleemInstaller.exe`. Pick the **channel** - *Release* (the tested
   version), *Testing* (the next version, being tested) or *Nightly* (the newest development build, which
   may not work) - and the drive. The line under them says which AutoBleem version the channel would
   install, and what is on the stick now: *a fresh install* (the stick's other files are left alone) or
   *AutoBleem <version> is on this stick: it will be updated* (games, saves, memory cards and settings stay).
   **Formatting is optional**: the **Format** button next to the drive is only for a new stick with no file
   system, one the console cannot read (NTFS, for example) or one you want to wipe - it asks first, then
   erases everything on the stick. Pick FAT32 there unless the console has the AutoBleem kernel.
   Tick what you want:
   - **Cover databases** - the box art and details of the PS1 library (ticked by default; about 300 MB).
   - **RetroArch** - RetroArch with its cores, the extra applications (Doom, Quake, Amiga, ...) and the
     libretro assets, for the other systems' games. Off by default; it can be added later by running the
     installer again.
   - **BIOS files** - the BIOS files the RetroArch cores need (needs RetroArch).
   - **Sample games** - a few free homebrew games so the shelf is not empty.
3. Press **Install** and wait. The progress bars and the log show every step; the stick is named `SONY`
   at the end, and `UpdateRoms` is put on it (see chapter 5).
4. Take the stick out safely, plug it into the console's **second front USB port** (right, player 2) - the
   first one is for the pad - and switch the console on. AutoBleem starts instead of the stock menu. A second
   pad needs a USB hub on the front port or a Bluetooth pad. Keep the stick out of the micro-USB port at the
   back (see below).

**Switching on and off.** With the stick in, the console boots, blinks its light for a few seconds
(AutoBleem is being picked up) and then goes to standby before anything is shown - that is the console's
own way of staging an update, which is how AutoBleem gets to run. Press **Power** once and the launcher
comes up. *Power off* in the system menu, or the console's Power button, puts the console into
**AutoBleem's standby**: the stick is disconnected first, then the light turns **orange** - the sign that
AutoBleem is working as intended - and the next press of Power brings the launcher straight back, in a
few seconds. **While the light is orange the stick can be pulled** and put into a PC without Windows asking
to check it; put it back before pressing Power. Unplugging the console's power goes through the boot
standby again next time. A light that is **red** means the console really powered off.

**Use a front USB port for the stick.** The micro-USB port at the back (a host there only works with the
AutoBleem kernel) keeps the console awake: with a stick or a hub on it the console powers off instead of
going to standby, and Power starts a cold boot.

**No stick.** With no stick in the console, a picture says to insert one - in any USB port. After 5 minutes,
or at once on Power, the console goes to sleep. The same picture appears if the stick is pulled while
AutoBleem runs.

![The picture that asks for the stick](../images/en/insert-stick.jpg)

**Stick check.** A stick that was not removed cleanly is checked at boot, at wake and after a pull, with a
progress bar. On a big stick this can take a while; do not interrupt it.

![The stick check](../images/en/stick-check.jpg)

To **update** a stick, run the installer over it again (the button says *Update*): it installs the chosen
channel's newest version, and your games, saves, settings and RetroArch content stay; only AutoBleem's own
files are replaced. A console with the AutoBleem kernel and WiFi can also update itself (section 3.11).

**Upgrading from AutoBleem 1.0 (or AutoBleem-NG).** The same installer, on the same stick - no format:

1. Copy the whole stick to the PC first, as a backup.
2. Plug it in, start `AutoBleemInstaller.exe`, pick the channel and the drive. Do **not** press Format.
3. Press **Install**. The installer brings the old layout up to date: RetroArch, the ROMs and the themes move
   to where AutoBleem 2 looks for them, and the old ROM folders (`nes`, `snes`, ...) are renamed to RetroArch's
   system names. Games, save states, memory cards, ROMs and RetroArch's saves stay; `config.ini` is kept, with
   the PS1 emulator set to pcsx-abnxt.
4. Put the stick back into the console. The first scan rebuilds the game list and the playlists (UpdateRoms
   on the PC fetches box art for the RetroArch games, chapter 5).

> The stock console has no clock and no network: dates are only shown after the AutoBleem kernel is
> installed (chapter 6), and box art for RetroArch games comes from UpdateRoms on the PC (chapter 5).

Games go into the `Games` folder of the stick, one folder per game - see section 3.9 for the layout.

### 2.2 Raspberry Pi

AutoBleem turns a Pi into a small console: it boots straight into the launcher, with no desktop. Two ready
images are on the site - 32-bit and 64-bit - plus a tarball for an existing Raspberry Pi OS Lite.

| Model | 32-bit image | 64-bit image | Notes |
|---|---|---|---|
| Raspberry Pi 5 | yes | yes | |
| Raspberry Pi 4 Model B, Pi 400 | yes | yes | |
| Raspberry Pi 3 Model B / B+ / A+ | yes | yes | fine for the launcher and PS1 |
| Raspberry Pi Zero 2 W | yes | yes | 512 MB of RAM: PS1 runs, the heavier RetroArch cores do not |
| Raspberry Pi 2 Model B | yes | v1.2 only | slow for anything 3D |
| Raspberry Pi 1, Zero, Zero W | no | no | ARMv6 - neither image runs |

The **32-bit image is the recommended one** for PS1 games: `pcsx-ab`'s fast ARM recompiler is 32-bit only,
so the 64-bit build runs PS1 games slower. The 64-bit image has the larger set of RetroArch cores.

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

**The first boot** takes 5 to 25 minutes and shows what it does on the screen. Without a network it asks
for one (a WiFi list, the password), then asks whether to install RetroArch (a minute without an answer
means yes), grows the system partition, makes the `AUTOBLEEM` data partition from the rest of the card,
installs RetroArch and its cores, the BIOS packs and the sample games, and reboots into the launcher.

The answers can be given in advance in **`autobleem.txt`** on the card's boot partition (editable on any
PC before the first boot):

| Key | Default | Meaning |
|---|---|---|
| `root_gib` | 8 | The system partition's size in GiB; the rest becomes the games partition. |
| `hdmi_mode` | 1920x1080@60 | The screen mode for the whole boot (`1280x720@60` for an older TV). |
| `retroarch` | (asked) | `yes` / `no` - RetroArch and the other systems, or PS1 only. |
| `thumbnails` | none | `boxarts` mirrors the whole box-art set for offline covers (~9000 files). |
| `bios`, `downloads`, `samples` | yes | Set to `no` to skip the BIOS packs, every download, or the sample games. |

**On an existing Raspberry Pi OS Lite** (Bookworm or Trixie): copy `autobleem-rpi.tar.gz` (or the arm64 one)
to the Pi, unpack it and run `sudo bash install.sh`. It asks the same questions, makes the data partition
by shrinking the root at the next boot (`--shrink-root <GiB>`), and puts the launcher on the first console.

After the install the card's **`AUTOBLEEM` partition** (exFAT) is what you fill: pull the card and open it on
any PC, or copy over the network (SSH is on). `Games/` for PS1 games, `RetroArch/roms/<system>/` for the
other systems, `System/Bios/` for the PS1 BIOS (section 3.10), `Themes/` for themes.

### 2.3 PC USB stick

The same appliance for any PC that boots from USB - a 32-bit system, so old machines work too:

1. Write the image to a stick of 8 GB or more. **On Windows** use **AutoBleemFlasher** (PC panel of the
   site - unzip it and run `AutoBleemFlasher.exe`; it asks for administrator rights, since it writes a
   whole disk): pick the channel and the stick, press *Write* and confirm twice - it downloads the image,
   checks it, writes it and reads it back. Only USB sticks and SD cards are offered, never the disk Windows
   runs from, and **everything on the chosen stick is erased**. On Linux or macOS, download
   `autobleem-<version>-pcusb-i386.img.xz` from the PC panel and write it with
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (or balenaEtcher).
2. Boot the PC from the stick (the boot menu key of your PC - F12, F8, Esc...). Both BIOS and UEFI boot
   work; **Secure Boot must be off**.
3. The first boot is the Pi's: a network question if there is no cable, the RetroArch question, then the
   install - about eight minutes with a wired network - and a reboot into the launcher.

The stick then has an `AUTOBLEEM` partition for your games, visible on Windows 10 (1903 and newer) as a
second drive when you plug the stick into a running PC. `autobleem.txt` is on the first partition, with the
same keys as on the Pi (no `hdmi_mode` - the PC uses the screen's native mode).

### 2.4 Windows

AutoBleem as a Windows program: full screen, the emulators and RetroArch started as programs.

1. Download **AutoBleemSetup-<version>.exe** and run it. It installs per user, without administrator
   rights: the program under `%LOCALAPPDATA%\Programs\AutoBleem`, the data (games, settings, themes,
   RetroArch) in a folder you choose - `Documents\AutoBleem` by default.
2. Tick the components - the cover databases, RetroArch (the official Windows build and its cores), the
   BIOS files, the sample games - and let the setup helper download them.
3. Start AutoBleem from the Start Menu or the Desktop. On a PC the keyboard works as a pad (section 3.2).

Running a newer setup over it updates the program and keeps the data folder. The launcher also checks the
site once a day and offers an update when there is one (section 3.11).

<!-- pagebreak -->

## 3. Using AutoBleem

### 3.1 The launcher

The launcher is where you choose what to play. It shows your games as a shelf of covers, the way you would
see the boxes on a real shelf, and you scroll along it until you find the one you want. Everything else in
AutoBleem - the settings, the memory cards, the Store - opens from here, and you come back here when you leave
a game.

The selected game sits in the middle of the shelf, with a soft reflection under it. Next to it you see its
details in a small grid: the publisher, the year, the serial number, the region, how many players it is for and
when you last played it. When AutoBleem does not know one of these facts, it leaves that line out rather than
showing it empty. A play button sits beside the details. A game that has no cover picture is shown as a disc
lying in the black tray of an empty case, so it still has a place on the shelf.

The look of the launcher comes from its theme. The default one is **ab2.0.0**: a fresh install switches to it,
and so does an update that brings it, but only once - if you pick another theme afterwards (section 3.6), it
stays.

**The hint bar** at the bottom of the screen tells you what the buttons do at the moment. It has two lines of
four slots each. The first line is about the selected game: play it, play it in RetroArch, open the icon row
under it, or open the Quick menu. The second line never changes: Select chooses the set, Start picks a random
game, Triangle shows the button guide and L2 + R2 opens the system menu. A hint is dimmed while its button has
nothing to do.

**Finding new games by itself.** Every time the launcher starts, it scans your games folder in the background,
so a game you copied in while the machine was off turns up without you doing anything. While the scan runs, a
bubble at the top right shows how far it has got, and new games appear on the shelf as they are found - you can
keep browsing meanwhile.

**A fresh install** has no games yet. Instead of an empty shelf you see a welcome card, *Hi, and welcome to
AutoBleem!*, which tells you to drop your games into `Games` and press *Re-scan games*. It names the place for
your platform: on your stick (PlayStation Classic, PC stick), on your SD card (Raspberry Pi) or in your
AutoBleem folder (Windows). The card goes away as soon as a scan finds the first game.

**Notifications** are the bubbles at the top right. They keep you informed without getting in the way: the
scan's progress, the name of the set you have just switched to (*Showing: ...*), a pad whose battery is low, a
note after a crash, a scanner processor at work, and a download from the Store. A download's bubble shows its
speed and the time left, for example `1.4 MB/s · 0:42`. How long the informational bubbles stay is up to you:
Options → *Notification timeout*.

**Pad batteries.** On the console, a Raspberry Pi and the PC stick (not on Windows), every wireless pad that
reports its battery shows as a small icon with its percentage, on its own plate, stacked down from the top-left
corner. A pad that plays as Player 1 or Player 2 carries a P1 or P2 tag, following the *Swap Player 1 / Player 2*
option (section 3.6); a pad that is not matched to a player, or a third pad, has no tag. When a pad's battery
runs low, a notification tells you once, with the pad's name and the percentage.

**The channel tag.** If you run a build that is not a final release, a small tag under the pad battery plate in
the top-left corner reminds you of it. It is a chip with the channel and the short version beside it: `ALPHA`,
`BETA` or `RC` for a pre-release, `TESTING` for any other pre-release, `NIGHTLY` for a nightly build, and `DEV`
for a build made by hand (for `DEV`, the version is the commit it was built from). A release shows no tag.

![The set picker: three tabs, and the groups of the current one with their game counts](../images/en/set-picker.jpg)

### 3.2 Controls

AutoBleem is made to be used with the pad alone, and the buttons mean the same thing on every screen: Cross
confirms, Circle goes back, Triangle helps. If you forget what a button does, the hint bar at the bottom of the
screen tells you, and Triangle on the shelf opens the button guide with every button of every screen (section
4.3). This is what the buttons do on the shelf:

| Button | On the shelf |
|---|---|
| Left / Right | Moves to the previous or next game; hold the button to keep scrolling. |
| L1 / R1 | Jumps to the previous or next first letter of the titles, so you get through a long shelf quickly. On an empty shelf with a USB drive connected, R1 opens *Disc* (section 3.8a). |
| Cross | Starts the selected game: a PS1 game in the PS1 emulator, a RetroArch game in its core, and an App after its read-me. |
| Square | Starts the selected PS1 game in RetroArch instead. When a disc in a USB drive is selected, it copies the disc instead (*Copy disc*, section 3.8a). |
| Circle | Takes you back to the disc view when a disc is in the drive (section 3.8a). |
| Triangle | Opens the button guide. |
| Start | Picks a random game from the current set, for when you cannot decide. |
| Select | Opens the set picker, where you choose which games the shelf shows (section 3.3). |
| Up | Opens the Quick menu (section 3.4). |
| Down | Opens the icon row under the game (*Settings*, *Game*, *Memory card*, *Resume*); Up closes it again. |
| L2 + R2 | Opens the system menu (section 3.5). |

**With a keyboard.** On a PC without a pad, or with a USB keyboard on the console, a Pi or the PC stick, the keys
stand in for the buttons. The arrow keys are the d-pad, Enter is Cross, Esc or Backspace is Circle, Tab is
Triangle and Space is Square. F1 and F2 are Select and Start, Page Up and Page Down are L1 and R1, Home and End
are L2 and R2, and F10 opens the system menu. On a development machine Esc closes the program and Space is
Start.

**In every list and menu** the same moves work: Up and Down move the cursor, L2 and R2 turn a page, L1 and R1
jump to the first or the last row, Cross selects and Circle goes back. You never need to look for a Save
button: a screen with settings saves them when you leave it with Circle.

**Getting out of a game or an App.** Hold Start + Select, or Home, for 2 seconds and you are back in AutoBleem.
This works on every pad - the console's own, a USB pad or a Bluetooth pad. A short press of the same buttons
opens the emulator's menu instead. An App has no such menu, so there only the long hold does anything.

![The icon row under the selected game](../images/en/launcher-icons.jpg)

### 3.3 The sets

A big library is easier to browse in parts. The sets let you narrow the shelf down to one kind of game - only
your favourites, only the Super Nintendo games, only the games in one folder - so you are not scrolling past
hundreds of covers to find the one you want.

Press **Select** and the set picker opens. It has three tabs, PlayStation, RetroArch and Apps: L1 and R1 switch
between them, Up and Down move through the groups of the tab (L2 and R2 a page at a time), and Cross shows the
group you picked on the shelf. Circle (*Back*) closes the picker without changing anything. The footer shows
these keys too. Every row says how many items it holds. A group with nothing in it opens on an empty shelf,
where the icon row offers only *Settings*.

**The PlayStation tab.** On a PlayStation Classic it starts with *All games* and *Internal games* (the twenty
games built into the console), followed by *USB games* - everything in `Games/` - and one group for each folder
you made under it, so a game in a sub-folder belongs to that folder's group. Then come *Favorite games*, *Game
history* and, once you have flagged at least one game as a light-gun game, *Lightgun games*. A Raspberry Pi, a PC
stick and Windows have no internal games, so there the list starts at *USB games*, which is your whole library.

**The RetroArch tab** is there only where RetroArch is installed. It has one group for each system you have games
for, plus RetroArch's own Favorites and History.

**The Apps tab** sorts the applications by type: *All apps*, then *Games*, *Emulators*, *Tools*, *Media* and
*Other*. Which group an app belongs to is set in its `app.ini` file. This tab also lists the **PE apps**, which
are Windows programs run by the PE runner; one the console cannot start is marked *cannot run on this console*.
Where the launcher shows it, a *Packages* row is in the list as well (section 3.9).

### 3.4 The Quick menu

The Quick menu is a short list of the things you reach for most often while browsing your games, so you do not
have to dig through the full system menu for them. Open it with **Up** on the shelf, or with the **gear icon** in
the icon row (the row with *Settings*, *Game*, *Memory card* and *Resume*).

Up and Down move through the items (from the last one the cursor goes round to the first), Cross picks one and
Circle closes the menu. A line under the menu describes the selected item. These are the items:

- *Re-scan games* looks for new, changed or removed games straight away - useful when you have just copied
  games in and do not want to wait.
- *Store* opens the AutoBleem Store, where you browse and install games, apps and extensions (section 3.12).
- *RetroArch cores*, where RetroArch is installed, lets you choose the core that plays each system.
- *Network & Controllers* opens the Wi-Fi, Bluetooth pairing and gamepad mapping screens (chapter 6). It is
  only there when an installed extension provides them - PSC-Bios does, on the console, a Raspberry Pi and the
  PC stick. If that extension is installed but switched off, the item is greyed out and its description says
  to enable it in Extensions; Cross then opens the Extensions list at it.
- *Restart launcher* closes AutoBleem and starts it again (on the console, a Raspberry Pi and the PC stick only).
- *System menu...* opens the full system menu with everything else - Options, Game Manager, Power off and more
  (section 3.5).

Everything here except the Store, the RetroArch cores and Restart launcher is in the system menu as well.

![The Quick menu](../images/en/quick-menu.jpg)

### 3.5 The system menu

The system menu holds everything AutoBleem can do beyond playing: the settings, the tools for your library and
memory cards, information about the machine, and the way to switch off. Press **L2 + R2** together (in either
order) and it opens over the shelf. Its items are grouped under the headings *Library*, *System* and *Leave*,
with the two you use most at the top. A line at the bottom of the menu describes the selected item, so you can
look around before you pick one.

| Section | Item | What it does |
|---|---|---|
| (top) | *Re-scan games* | Looks for new, changed or removed games now. The scan also watches the folder by itself, so you need this only when you do not want to wait. |
| | *Extensions* | Lists the extensions on the stick, such as the AutoBleem Store, so you can run them or switch them off (section 3.12). |
| *Library* | *Game Manager* | Shows the PS1 games as a list with their folders, where you can delete a game or flush the covers (section 4.1). It cannot be opened while a scan is running. |
| | *Memory Cards* | Manages your shared memory card sets (section 3.7). |
| | *Scanner processors* | Sets the order of the programs every scan runs first, and switches them on or off (section 3.13). It cannot be opened while a scan is running. |
| *System* | *Options* | Opens AutoBleem's settings (section 3.6). |
| | *Network & Controllers* | Opens the Wi-Fi, Bluetooth pad pairing, DualShock 3 setup and gamepad mapping screens (chapter 6). It is there only when an extension provides them - see below. |
| | *Hardware Information* | Shows the machine's facts - system, CPU, storage, network interfaces, time zone, display, and the pads with their mappings - on the same page on every platform (section 4.2). Circle brings you back to the system menu. |
| | *Virtual gamepad* | Shows the pads Apps are given and the pads the daemon sees, which helps when a pad does not work in an App (section 4.5). Circle brings you back to the system menu. |
| | *Software Update* | Checks the site for a newer AutoBleem or RetroArch now, instead of waiting for the daily check (section 3.11). When the launcher already knows of one, the row says *Update available*. On a PlayStation Classic this needs the AutoBleem kernel and a Wi-Fi network. |
| | *About* | Shows the credits and the license. |
| *Leave* | *RetroArch* | Leaves the launcher for RetroArch's own menu, for its settings and content lists; when you close RetroArch you are back in the launcher. It is there only where RetroArch is installed. |
| | *Power off* | Switches the machine off after asking you to confirm (see below). |

**Network & Controllers** appears only where an installed extension provides the `network` entry, which an
extension declares with `Provides=network` in its `extension.ini`. PSC-Bios does this on the console, a Raspberry
Pi and the PC stick. If that extension is installed but switched off, the item stays in the menu, greyed out,
and its description tells you to enable it in Extensions; Cross on it opens the Extensions list right at that
extension.

**Power off** does what suits the machine. On the console it puts it into AutoBleem's standby: the stick is
disconnected, the light turns orange, and Power brings the launcher back in a few seconds (section 2.1). On a
Raspberry Pi or a PC the machine shuts down.

![The system menu](../images/en/system-menu.jpg)

### 3.6 Options

Options is where you make AutoBleem your own: the picture on your screen, the look of the launcher, the
language, the sound, which PS1 emulator plays your games. You open it from the system menu (*Options*) or with
the *Settings* icon under a game. You will usually set the screen and the language once, and come back when
something looks wrong on a particular TV or you want a change.

The settings are sorted into groups, each under a heading. Up and Down move from row to row, and Left and Right
change the value of the row you are on: a tap moves one step, holding the button keeps going. L1 and R1 jump to
the first or the last row, and L2 and R2 turn a page. On a row with a choice of themes, music or fonts, Start
picks one at random. A setting that is on or off reads **ON** or **OFF**. You see each change at once, and Circle
leaves the screen and saves everything - there is nothing else to confirm. The one exception is the screen mode,
which is tried when you leave Options (see *Display* below).

Some rows appear only where they make sense: the CRT rows only on a 4:3 picture, the RetroArch rows only where
RetroArch is installed, the internal games only on a PlayStation Classic.

| Group / setting | What it is for |
|---|---|
| *Interface*: *Display:* | Sets the screen's resolution, for the launcher and the PS1 emulator. *Auto* uses the screen's own mode and shows which one it is, for example *Auto (1920x1080)*; you can also pick any mode the screen lists. The console offers 720p, 1080p and *CRT 4:3* (720x480), the mode for an old CRT TV or a 4:3 capture device. Change it when the picture does not fit your TV or looks blurry. This row is not there when AutoBleem runs in a window on a development machine. |
| *CRT margin:* | Shrinks everything a little, from 0 to 10 % in steps of 1 %, because old TVs cut off the edges of the picture. Raise it until the hint bar and the corners are fully visible. It is shown only on a 4:3 output, takes effect at once, and is applied even before the start-up splash. |
| *Picture height:* | Makes the picture taller or shorter, from -40 to +40 in steps of 2, on any 4:3 output - *CRT 4:3*, or a 4:3 mode on a VGA or PC output. Use it when the picture on an old TV is squashed or runs off the top and bottom. It takes effect at once, and RetroArch's game picture follows it. |
| *Emulator screen scaling:* | Decides how the PS1 emulator fits a game's picture to your screen. *1x1* shows the PlayStation's own pixels, small and exact; *2x (integer)* and *4:3 (integer)* scale by whole multiples only, which gives the sharpest picture; *4:3* keeps the picture's original shape; *Full screen* stretches the picture over the whole screen. It replaces the old Widescreen switch. The classic `pcsx-ab` and RetroArch know only full screen and 4:3. |
| *Screen halo:* | When it is ON, the empty bands beside a game's picture (where the picture does not fill the screen) are filled with the picture's own soft glow instead of black. It works with `pcsx-abnxt`. |
| *AutoBleem theme:* | Changes the look of the launcher. Themes live in `Themes/`, and a theme zip dropped there is listed by its name too. The themes AutoBleem ships are refreshed by every update, so if you want to customise one, copy it under a new name first. The default is **ab2.0.0**. |
| *Cover style:* | Chooses the jewel-case frame drawn around the PS1 covers. |
| *Cover shine:* | Lets a shine cross the selected cover each time the shelf comes to rest. |
| *Language:* | Sets the launcher's language; there are 17, and the change is immediate. |
| *Notification timeout:* | Sets how long the information bubbles (*Showing: ...*, the scan's summary) stay, from 0 to 20 seconds; 0 shows *Off* and turns them off. Error messages keep their own fixed time, so you never miss one. |
| *Splash screen:* | Shows the AutoBleem picture while the launcher starts; switch it off to go straight to the shelf. |
| *Animations:* | Animates the change from one screen to the next; switch it off if you prefer every screen to appear instantly. |
| *Fonts*: *Use default font:* | When it is ON, the launcher uses its own font (Red Hat Text); switch it off to use the font chosen in the next row. |
| *Font:* | Picks a font of your own: any `.ttf` or `.otf` file in `resources/fonts`, `RetroArch/fonts` or the theme's folder. The row shows the name of the font really in use. |
| *Sound*: *Music:*, *Background music:* | *Music:* chooses the track that plays under the launcher - the theme's own, or a file from `resources/music`. *Background music:* decides whether any music plays at all. |
| *Emulation*: *PS1 emulator:* | Chooses the emulator your PS1 games start in: `pcsx-abnxt`, the default (the current PCSX-ReARMed with AutoBleem's additions), or `pcsx-ab`, the classic one. Try the other one when a game does not run well. A resume point saved by one continues in the other, unless the game ran without a BIOS file. |
| *Swap Player 1 / Player 2 (PS1 emulators):* | Swaps which of the first two pads is Player 1 and which is Player 2, in both PS1 emulators - handy when the pads are plugged in the "wrong" way round. It only matters with two or more pads connected; with one pad you always play as Player 1. RetroArch is not affected. If the PS1 emulator in use cannot swap yet, AutoBleem tells you so. |
| *Play all PSX games with RA:*, *Update RA config:*, *Persist RetroArch config:* | These three are there only where RetroArch is installed. The first starts every PS1 game in RetroArch's PS1 core (*PlayStation 1*; on a PC this is SwanStation). The second lets AutoBleem write its settings into RetroArch's config when it starts a game there. The third keeps a change you make in RetroArch's own menu when RetroArch quits. |
| *Library*: *Show internal games:* | Shows the console's built-in games in the PlayStation lists (PlayStation Classic only). |
| *Clean game names:* | When it is ON (the default), the RetroArch game lists show tidy names, without bracketed tags such as (USA), (Rev 1) or [!]; OFF shows the file names. The file name is still in the game's details. PS1 games are not affected, since their titles come from the database. |
| *Fetch box art online:* | Lets the scan download missing covers from libretro's servers (Raspberry Pi, PC, Windows). |
| *Updates*: *Updates:* | Chooses which updates the launcher looks for (section 3.11): `release` (the tested version), `testing` (the next version, being tested), `nightly` (the newest development build) or `off`. The default follows the version you installed. It is not shown on a development host. |
| *Diagnostics*: *Keep logs on the stick:* | Keeps every log on the stick from the next start, not only after a crash - switch it on when you are chasing a problem (chapter 7). |
| *Show performance:* | Shows an overlay in the bottom-left corner with the frame rate, the CPU load, the threads and the memory; in a game the emulator shows its FPS and CPU too. |

**Changing the screen mode.** When you leave Options with a new *Display:* mode, AutoBleem switches to it and
asks *Keep this display mode?*. If the picture is fine, confirm it. If your TV shows nothing, wait: without a
confirmation AutoBleem goes back to the previous mode after a countdown.

**Themes on a 4:3 screen.** In the *CRT 4:3* mode the theme list shows only the themes that have a 4:3 layout.
If the theme you use has none, the default theme takes its place after you confirm the mode (and at every start
in that mode), and a notice tells you: *Theme switched to the default (CRT 4:3)*.

![The options, in groups](../images/en/options.jpg)

![The Display group: CRT margin and Picture height](../images/en/options-display.jpg)

![The notice after switching to CRT 4:3 with a theme that has no 4:3 layout](../images/en/crt43-theme-notice.jpg)

### 3.7 A game's settings

Every game can have settings of its own. Most games play fine as they are, but now and then one needs a little
help - a sharper or softer picture, a frame skipped to keep it smooth, a different memory card - or you simply
want to mark it as a favourite. The game editor is where you change these things for that one game, without
touching any other.

With a game selected, press **Down** to open the icon row under it. It has four icons: *Settings* (the options
of section 3.6), *Game* (this game's own settings), *Memory card* (its memory card) and *Resume* (its save
states). Move to one and press Cross to open it.

**The game editor** (the *Game* icon) shows the game's details on the right - the title, the publisher, the year,
the number of players, the folder and the memory card - and its settings on the left. Up and Down move between
the settings and Left and Right change them, as in Options; holding a button repeats the move. When you are done,
Circle saves your changes and takes you back. A game that has no title in its data is shown under the name of its
folder.

The settings come in four groups:

- **Game** is about how AutoBleem treats the game. *Favorite:* puts it in the *Favorite games* group of the set
  picker. *Lock data:* tells the scanner to leave the game's title, serial and disc list exactly as you set them,
  so a later scan does not overwrite your changes. *Resume:* decides what happens when you start a game that has
  resume points: *Ask* shows the resume-slot picker, *Last slot* continues from the newest slot at once, and
  *Never* always starts the game from the beginning. Where RetroArch is installed there are two more rows.
  *Lightgun game:* is for a light-gun game: it joins the *Lightgun games* group and always runs in RetroArch,
  because RetroArch's PS1 core has the GunCon (switching it on also switches on the next row). *Play using RA:*
  runs this one game in RetroArch instead of the PS1 emulator.
- **Display** is about how the picture looks. *Resolution:* draws the game at 1x or 2x (on the built-in GPU), and
  *Remove seams:*, which only works with 2x, hides the thin lines that can appear between parts of the picture
  at that size. *Dithering:* (*Off*, *On*, *Always*) controls the fine dot pattern the PlayStation uses to blend
  colours, and *Smoothing:* picks one of the emulator's smoothing scalers. *Filter:* decides how the picture is scaled to the screen: *Nearest* shows plain pixels, *Linear* smooths them,
  *Sharp* and *Sharp (simple)* keep the pixels crisp without shimmering, and there is *Quilez*. The CRT filters
  *CRT (fast)*, *CRT (raster)* and *CRT-Pi* imitate an old TV and draw their own scanlines, so the scanline rows
  grey out while one of them is chosen. Otherwise *Scanlines:* adds the dark lines of an old TV, and *Scanline
  brightness:* sets how dark they are. *Resolution*, *Remove seams*, *Dithering*, *Smoothing* and the filters
  other than *Linear* and *Nearest* are for `pcsx-abnxt`; the classic `pcsx-ab` and RetroArch show any other
  filter as *Nearest*.
- **Rendering** has the GPU *Plugin:* and *Frameskip:* (*Auto*, *Off*, or 1 to 3 frames). Skipping frames helps a
  game that runs too slowly to keep its speed, at the cost of a less fluid picture.
- **Emulator** has *Speedhack:*, the CPU *Clock:*, *Spu interpolation:* (how the sound is smoothed), *Boot logo:*
  and, with `pcsx-abnxt`, *Sony hacks:*. Switch *Boot logo:* off to skip the BIOS shell - you need this for a
  homebrew disc whose custom logo stops it from booting.

The picture's shape and the screen's resolution are not set per game but for all of them, in Options
(*Emulator screen scaling:* and *Display:*).

**Other buttons in the editor.** Triangle renames the game, with the on-screen keyboard. Square gives the game
another memory card (*Change memory card*). While the game still uses its own card, Start turns that card into
a new shared set, so other games can use it too (*Share memory card*, section 3.7). These two are not offered
for the console's internal games. Holding Left / Right or
Up / Down repeats the move here, and also in RetroArch's game options and cores screens.

A drive game that has no `pcsx.cfg` file cannot keep its settings; when you change one, the editor tells you
*Not saved: this game has no pcsx.cfg*.

For a **disc in the drive** (section 3.8a) some settings make no sense, so the editor greys those rows out, and
the line at the bottom says *Not available for a disc in the drive* when you move onto one.

![The game editor for a disc in the drive](../images/en/game-editor-disc.jpg)

**Settings saved in the emulator.** You can also tune a game while you play it: the emulator's own menu has
*Save settings for this game* (section 3.8). Once a game has settings saved there, those are the ones it plays
with. The game editor then shows its Display, Rendering and Emulator rows greyed out, with the saved values, under
the heading *Saved in the emulator*, so you can read them but not change them. If you would rather use the game
editor's settings again, pick *Unlock the settings* and confirm: this deletes the settings the emulator saved,
and the rows can be changed again. Both emulators, `pcsx-ab` and `pcsx-abnxt`, read and write the same saved
settings, so it does not matter which one saved them.

![The game editor](../images/en/game-editor.jpg)

### 3.7 Memory cards and save states

On a real PlayStation you would share one or two memory cards between all your games, and run out of room
sooner or later. In AutoBleem every PS1 game has a memory card of its own by default, so you never need to think
about space or about which card a save is on. The card is kept with the game's save states in
`Games/!SaveStates/<game folder>/`.

**Shared memory card sets.** Sometimes games need to see each other's saves - a sequel that reads the save of
the first game, for example, or the discs of a series you want on one card. For this you make a shared set: one
card that several games use. The sets are kept in `Games/!MemCards/`, and you manage them with *Memory Cards* in
the system menu. Square creates a new set (you type its name with the on-screen keyboard), Cross renames the
selected one and Triangle deletes it, after asking you first. To put a game on a set, use *Change memory card*
in its game editor (section 3.7), or its *Memory card* icon.

**The memory card editor** opens from a game's *Memory card* icon. It shows the game's card and a second card
side by side, with every save's icon and title, like the memory card screen of the original console. Square
copies the selected save to the other card, Triangle deletes it, and Select defragments a card, gathering its
free blocks together so a large save fits again. Start lets you choose which set is shown on the right, and
Cross reloads both cards from the stick. A card the game has not written to yet - a game you have not saved in -
is empty and says *no card yet* next to its name. If you made changes, AutoBleem asks *Do you want to save memory
card data?* before it leaves the editor, reloads the cards or shows another set.

![The memory card editor](../images/en/memory-card-editor.jpg)

**Resume points.** Many PS1 games only let you save at certain places, and you do not always reach one before you
have to stop. Resume points take care of that: when you leave a PS1 game with the console's Reset button (or
through the emulator's menu on a Pi or a PC), AutoBleem keeps a save state of exactly where you were. While it
writes it, on the way out of the game, the emulator shows *Please wait...*. Next time, you carry on from that
moment.

You find them under the game's *Resume* icon. A game with a resume point shows a small picture of it on the
icon; a game without any has the icon greyed out. The resume-slot picker has four slots, shown as framed cards,
each with a picture of the moment, its slot number and its date. The newest one is marked **NEWEST**, and a slot
that has not been used says *No resume point*. Cross continues the game from the selected slot, and Triangle
deletes it. Whether the picker appears at all when you start the game is up to the game's *Resume:* setting
(section 3.7).

PS1 games you play in RetroArch have resume slots too. Each slot carries a badge - the AutoBleem 2 logo or the
RetroArch logo - so you can see which emulator wrote it.

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
