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
  the top of the core list (section 3.9). Games such as Doom run from your own game files in a `Packages` folder
  (section 3.10).
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
   starts. For a second pad, use a USB hub on the front port or a Bluetooth pad.

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

**The port at the back.** The micro-USB port at the back is the console's power port. With the AutoBleem kernel
it can also take a USB device, but the stick belongs in a front port.

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
(section 3.12).

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

Your PS1 games go into the stick's `Games` folder, one folder per game - section 3.10 explains the layout.

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
into `RetroArch/roms/<system>/`, the PS1 BIOS into `System/Bios/` (section 3.11) and themes into `Themes/`.

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

If you want AutoBleem on your Windows computer, it also runs as an ordinary program: full screen, with
the emulators and RetroArch started as programs of their own.

1. Download **AutoBleemSetup-<version>.exe** and run it. It installs per user, without administrator
   rights: the program under `%LOCALAPPDATA%\Programs\AutoBleem`, the data (games, settings, themes,
   RetroArch) in a folder you choose - `Documents\AutoBleem` by default.
2. Tick the components - the cover databases, RetroArch (the official Windows build and its cores), the
   BIOS files, the sample games - and let the setup helper download them.
3. Start AutoBleem from the Start Menu or the Desktop. On a PC the keyboard works as a pad (section 3.2).

To update, run a newer setup over it: the program is replaced and your data folder stays as it is. The
launcher also checks the site once a day and offers an update when there is one (section 3.12).

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
| L1 / R1 | Jumps to the previous or next first letter of the titles, so you get through a long shelf quickly. On an empty shelf with a USB drive connected, R1 opens *Disc* (section 3.9a). |
| Cross | Starts the selected game: a PS1 game in the PS1 emulator, a RetroArch game in its core, and an App after its read-me. |
| Square | Starts the selected PS1 game in RetroArch instead. When a disc in a USB drive is selected, it copies the disc instead (*Copy disc*, section 3.9a). |
| Circle | Takes you back to the disc view when a disc is in the drive (section 3.9a). |
| Triangle | Opens the button guide. |
| Start | Picks a random game from the current set, for when you cannot decide. |
| Select | Opens the set picker, where you choose which games the shelf shows (section 3.3). |
| Up | Opens the Quick menu (section 3.4). |
| Down | Opens the icon row under the game (*Settings*, *Game*, *Memory card*, *Resume*); Up closes it again. |
| L2 + R2 | Opens the system menu (section 3.5). |

**With a keyboard.** On a PC without a pad, or with a USB keyboard on the console, a Pi or the PC stick, the keys
stand in for the buttons. The arrow keys are the d-pad, Enter is Cross, Esc or Backspace is Circle, Tab is
Triangle and Space is Square. F1 and F2 are Select and Start, Page Up and Page Down are L1 and R1, Home and End
are L2 and R2, and F10 opens the system menu.

On Windows a few keys work differently. Esc closes AutoBleem (chapter 7), so Circle is Backspace there, Space is
Start and S is Square. The letter keys also stand in for the whole pad, so you can play the launcher without
reaching for the arrow keys: X, O, S and T are Cross, Circle, Square and Triangle, I, J, K and L are the d-pad (up,
left, down, right), B is Select, Q and E are L1 and R1, and 1 and 2 are L2 and R2.

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
Where the launcher shows it, a *Packages* row is in the list as well (section 3.10).

### 3.4 The Quick menu

The Quick menu is a short list of the things you reach for most often while browsing your games, so you do not
have to dig through the full system menu for them. Open it with **Up** on the shelf, or with the **gear icon** in
the icon row (the row with *Settings*, *Game*, *Memory card* and *Resume*).

Up and Down move through the items (from the last one the cursor goes round to the first), Cross picks one and
Circle closes the menu. A line under the menu describes the selected item. These are the items:

- *Re-scan games* looks for new, changed or removed games straight away - useful when you have just copied
  games in and do not want to wait.
- *Store* opens the AutoBleem Store, where you browse and install games, apps and extensions (section 3.13).
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
| | *Extensions* | Lists the extensions on the stick, such as the AutoBleem Store, so you can run them or switch them off (section 3.13). |
| *Library* | *Game Manager* | Shows the PS1 games as a list with their folders, where you can delete a game or flush the covers (section 4.1). It cannot be opened while a scan is running. |
| | *Memory Cards* | Manages your shared memory card sets (section 3.8). |
| | *Scanner processors* | Sets the order of the programs every scan runs first, and switches them on or off (section 3.14). It cannot be opened while a scan is running. |
| *System* | *Options* | Opens AutoBleem's settings (section 3.6). |
| | *Network & Controllers* | Opens the Wi-Fi, Bluetooth pad pairing, DualShock 3 setup and gamepad mapping screens (chapter 6). It is there only when an extension provides them - see below. |
| | *Hardware Information* | Shows the machine's facts - system, CPU, storage, network interfaces, time zone, display, and the pads with their mappings - on the same page on every platform (section 4.2). Circle brings you back to the system menu. |
| | *Virtual gamepad* | Shows the pads Apps are given and the pads the daemon sees, which helps when a pad does not work in an App (section 4.5). Circle brings you back to the system menu. |
| | *Software Update* | Checks the site for a newer AutoBleem or RetroArch now, instead of waiting for the daily check (section 3.12). When the launcher already knows of one, the row says *Update available*. On a PlayStation Classic this needs the AutoBleem kernel and a Wi-Fi network. |
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
| *Updates*: *Updates:* | Chooses which updates the launcher looks for (section 3.12): `release` (the tested version), `testing` (the next version, being tested), `nightly` (the newest development build) or `off`. The default follows the version you installed. It is not shown on a development host. |
| *Diagnostics*: *Keep logs on the stick:* | Keeps every log on the stick from the next start, not only after a crash - switch it on when you are chasing a problem (chapter 7). |
| *Show performance:* | Shows an overlay in the bottom-left corner with the frame rate, the CPU load, the threads and the memory; in a game the emulator shows its FPS and CPU too. |

**Changing the screen mode.** When you leave Options with a new *Display:* mode, AutoBleem switches to it and
asks *Keep this display mode?*. If the picture is fine, confirm it. If your TV shows nothing, wait: without a
confirmation AutoBleem goes back to the previous mode after a countdown.

**Themes on a 4:3 screen.** In the *CRT 4:3* mode the theme list shows only the themes that have a 4:3 layout.
If the theme you use has none, the default theme takes its place after you confirm the mode (and at every start
in that mode), and a notice tells you: *Theme switched to the default (CRT 4:3)*.

![The options, in groups](../images/en/options.jpg)

![The Interface group: CRT margin and Picture height](../images/en/options-display.jpg)

![The notice after switching to CRT 4:3 with a theme that has no 4:3 layout](../images/en/crt43-theme-notice.jpg)

### 3.7 A game's settings

Every game can have settings of its own. Most games play fine as they are, but now and then one needs a little
help - a sharper or softer picture, a frame skipped to keep it smooth, a different memory card - or you
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
a new shared set, so other games can use it too (*Share memory card*, section 3.8). These two are not offered
for the console's internal games. Holding Left / Right or
Up / Down repeats the move here, and also in RetroArch's game options and cores screens.

A game keeps its settings in its own `pcsx.cfg` file. Every game on the stick has one, because the scan makes it.
An original disc in a USB drive (section 3.9a) gets its own folder with a `pcsx.cfg` only the first time you
start it; until then, a change you make in the editor cannot be kept, and the editor tells you *Not saved: this
game has no pcsx.cfg*. So start the disc once - from then on its settings are kept like any other game's. A disc
that belongs to a game already in your library uses that game's folder and settings from the start.

For a **disc in the drive** (section 3.9a) some settings make no sense, so the editor greys those rows out, and
the line at the bottom says *Not available for a disc in the drive* when you move onto one.

![The game editor for a disc in the drive](../images/en/game-editor-disc.jpg)

**Settings saved in the emulator.** You can also tune a game while you play it: the emulator's own menu has
*Save settings for this game* (section 3.9). Once a game has settings saved there, those are the ones it plays
with. The game editor then shows its Display, Rendering and Emulator rows greyed out, with the saved values, under
the heading *Saved in the emulator*, so you can read them but not change them. If you would rather use the game
editor's settings again, pick *Unlock the settings* and confirm: this deletes the settings the emulator saved,
and the rows can be changed again. Both emulators, `pcsx-ab` and `pcsx-abnxt`, read and write the same saved
settings, so it does not matter which one saved them.

![The game editor](../images/en/game-editor.jpg)

### 3.8 Memory cards and save states

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

### 3.9 Starting games, RetroArch and Apps

Starting a game is what you will do most, so it takes one button: select the game on the shelf and press
**Cross**. A PS1 game opens full screen in the PS1 emulator you chose in Options (section 3.6) and plays until you
leave it. If you would rather play a PS1 game in RetroArch - because it runs better there, or because you like
RetroArch's options - press **Square** instead.

**Leaving a game.** On the PlayStation Classic the console's own buttons do what you would expect. **Reset** on
the front takes you back to the launcher and keeps a resume point of where you were, so you can carry on later
(section 3.8); it works even while the in-game menu is open. **Power** switches the console off. A Raspberry Pi or
a PC has no such buttons, so there you leave through the emulator's in-game menu, described below.

There is also a way out that works the same on every pad - the console's own, a USB pad or a Bluetooth pad:
**hold Start + Select, or Home, for 2 seconds**, and you are back in AutoBleem. A short press of the same buttons
opens the emulator's menu instead. The launcher reminds you of both in its hints (*Hold Select+Start or Home for
2 seconds: back to AutoBleem* and *Short press of Select+Start or Home: the emulator's menu*). An App has no
emulator menu, so there only the long hold does anything. On the console, Reset always stops an App as well.

**The in-game menu.** With `pcsx-abnxt` the emulator has a menu of its own for the things you want while you play:
saving, changing discs, adjusting the picture, choosing the controllers. Press the menu button - Home on a pad
that has one, **Select + Start** on a pad without it, or **Esc** on a keyboard - and the game pauses behind the
menu, with its last picture in the background. Holding the menu button for 2 seconds does the same as Reset: it
leaves the game. The menu has three tabs, and L1 and R1 move between them. It remembers where you were, so the
next time it opens on the same tab and row.

- The **Game** tab is about the game itself. *Resume game* closes the menu and lets you play on. Under *Saves*,
  *Quick save* keeps the moment you are in and *Quick load* brings it back. *Load autosave* takes you back to how
  the game was up to 30 seconds ago - the emulator keeps that copy in memory while you play, which rescues you
  from a mistake you cannot undo. Under *CD disc*, *Change disc* is for a game on several discs when it asks for
  the next one, and *Reset game* starts the game over. *Save settings for this game* keeps the settings you have
  chosen for this one game (section 3.7). *PCSX menu* opens PCSX-ReARMed's own pages, with its options, cheats
  and About, and *Exit* takes you back to AutoBleem.
- The **Picture** tab lets you change how the game looks while you watch it: *Display*, *Resolution* (1x or 2x),
  *Remove seams*, *Dithering*, *Scaling*, *Screen halo*, *Smoothing*, *Filter*, *CRT mask*, *Scanlines* and
  *Scanline brightness*. They are the same settings as in the game editor (section 3.7), and every row has a help
  line on the right that says what it does. *Display* is the screen's resolution; on the console you choose it in
  Options, and here it is only shown. *Screen halo* is for the dark bands beside a 4:3 picture on a wide screen:
  it fills them with the picture's own edges, mirrored and dimmed, so the game seems to glow out into them instead
  of sitting between two black bars. *CRT mask* lays the pattern of an old tube's phosphors over the picture -
  *Aperture* gives the fine stripes of a Trinitron, *Slot* and *Delta* the dots of other tubes; it is there only
  with the CRT (raster) filter. The CRT-Pi filter is too heavy for the console at 1080p. A row that does not
  apply is greyed out, and its help line tells you why.
- The **Controllers** tab decides what is plugged into the PlayStation's two ports, *Controller 1* and
  *Controller 2*: a standard (digital) pad, an analog pad (DualShock), a gun, or nothing. Some games only work
  with one kind of pad. The change takes effect when you go back to the game.

The menu is drawn in the launcher's own ab2.0.0 look, so it does not feel like a different program, and it
shows your pad batteries and the picture of your last quick save.

**RetroArch games.** A game from another system starts in RetroArch, with the core the launcher chose for its
system. When you have finished, *Close Content* or *Quit RetroArch* in RetroArch's menu brings you back to the
launcher. If you want to change which core plays a system, open *RetroArch cores* in the Quick menu (section
3.4); the list opens with the *PlayStation 1* core at the top. And if you want RetroArch's own menu (the XMB) for
its settings and its own content lists, choose *RetroArch* in the system menu: RetroArch then opens with nothing
loaded.

![The RetroArch cores window, with the PlayStation 1 core at the top](../images/en/retroarch-cores.jpg)

**Apps.** Apps are programs rather than games: the console tools and, on the console, the extra applications
that come with RetroArch's package - Doom, Quake, Amiga and more. You find them in the Apps set. Before an App
starts, AutoBleem shows its read-me, so you know what it is and how it is controlled. Cross starts it, and
Circle takes you back to the shelf.

![An App's read-me, shown before the App starts](../images/en/app-start.jpg)

**An App's settings.** Many Apps were written for one particular pad, so you can change how they see yours.
Select the App, open the icon row and choose *Game*: the App's *Game settings* open (*Change how this program is
started*). *Pad mode:* decides which pad the App is told it has. *Automatic* uses what the App itself asks for;
*PSC pad* and *Xbox 360 pad* present your pad as the console's pad or as an Xbox 360 pad, and *PSC pad (system)*
and *Xbox 360 pad (system)* do the same through the system itself. Try another mode when an App does not react
to your pad as it should. *D-pad as stick:* lets the d-pad move the analog stick, for an App that only listens to
the stick, and *Stick as D-pad:* does the opposite.

Some Apps ask you a question the first time you start them. One wants to know *Which controls does your pad
have?*, so it can set up its controls: answer *One D-pad* for a pad with only the d-pad, or *Analog sticks*. An
App that runs Windows asks *What do you want to do?* and offers to run Windows, install it, run DOS or uninstall
Windows. When an App lets you set a key, it asks you to *Press one of the buttons.*

![An App's game settings](../images/en/app-game-settings.jpg)

A Windows program run by the PE runner (a PE app, section 3.3) talks to you through AutoBleem's own screens: a
message it wants to show appears as *Message*, and a question with choices as *Choose an option*, each with the
App's name as its title.

![A question from a PE app, shown as an AutoBleem screen](../images/en/pe-dialog.jpg)

### 3.9a A disc in a USB drive

You can connect an ordinary USB CD/DVD drive to the console, a Raspberry Pi or a PC started from the
AutoBleem stick and play straight from an original PlayStation disc - without copying anything. A disc you
put in appears in the launcher like one more game. This does not work on Windows.

**Copying a disc to the stick.** If you want the game always at hand, without the disc, press Square
(*Copy disc*). AutoBleem first asks whether to copy the game and how much room it will take, then saves it in
the `Games` folder as a single CHD file (a game on several discs also gets an `.m3u` file, so changing discs
works in the game). While it copies you see the speed and the time left, and *Abort* stops it. When it is
done, the game is on the shelf like any other. AutoBleem will not copy a game that is already in `Games`, or
one there is no room for - it then tells you how much room it needs. A scratched disc can be copied too: the
parts that could not be read are filled with zeros, and AutoBleem tells you how many there were. Such a copy
may or may not work.

Square offers the copy for every PlayStation game disc in the disc view, also for one the cover databases do not
know. A game the databases know is copied under its title; for a game on several discs, copy the discs one after
another, and the `.m3u` lists them in order, disc 1 first. A disc the databases do not know is named by its
serial instead, is copied as a single disc, and has no cover on the shelf. The copy window, *Copying the disc*,
stays on the screen until the copy is finished or stopped - the launcher waits meanwhile - and shows the speed
as a multiple of an ordinary CD drive. If the copy fails, AutoBleem tells you why.

![Copying a disc](../images/en/disc-copy.jpg)

**Playing from the disc.** When you put a disc in, the **disc view** opens by itself as soon as the disc has
been read. It shows the disc's cover - from the cover databases, or fetched online - with its serial and its
title, and Cross starts the game. A PS1 game played from the disc keeps its resume points and saves in a folder of
its own, so you can stop and carry on later just as with a game on the stick. After the game, or after you have
been in the options or an extension's settings, you come back to the disc view. If you leave it with Circle to
browse your other games, the disc stays in the drive and Circle on the shelf brings the view back; on an empty
shelf, R1 (*Disc*) opens it too. On a shelf with games R1 keeps its usual job of jumping between first letters.
When you take the disc out, the disc view closes.

![The disc view](../images/en/disc-view.jpg)

**The drive chip** at the top of the screen tells you what the drive is doing, so you know whether to wait. With
no drive connected you see nothing. A drive with no disc in it shows a dim disc icon. While a disc is being read,
the icon blinks and says *Reading the disc...*, and once it is ready the icon lights up with the disc's title. If
you put in a disc that is not a PlayStation game or an audio CD, the chip says *This is not a PlayStation disc*,
and if the drive cannot read the disc at the moment, it says *The disc cannot be read now*.

![The drive chip](../images/en/disc-chip.jpg)

**Audio CDs.** The drive plays music CDs too. An audio CD opens the **CD player** instead of the disc view. It
shows the disc as an *Audio CD* with its list of tracks and its total time, and the line under it names the
selected track and says whether repeat and shuffle are on. A disc the player cannot play is marked *This disc
cannot be played*. These are its buttons:

| Button | In the CD player |
|---|---|
| Cross | Plays the selected track. |
| Start | Pauses the music, and starts it again. |
| Square | Stops the music. |
| L1 / R1 | Go to the previous or the next track. |
| L2 / R2 | Wind back or forward through the track, five seconds at a time. |
| Triangle | Changes what repeats: nothing, the whole disc, or the current track. |
| Select | Switches shuffle on or off, so the tracks play in a random order. |
| Circle | Leaves the CD player. |

![The CD player](../images/en/cd-player.jpg)

**LibCrypt discs.** Some PlayStation games, most of them European, carry a copy protection called LibCrypt. To
run them, the emulator needs a small `.sbi` file with the protection's data. AutoBleem fetches that file from the
site by itself before such a disc plays and when you copy it, and it is copied with the game. For this it needs a
network: on a Raspberry Pi or a PC the one it already has, on the console the Wi-Fi you set up in PSC-Bios.

For a disc in the drive some of a game's settings make no sense, so its game editor greys those rows out (section
3.7).

### 3.10 Adding games

AutoBleem finds your games by itself, as long as they are in the right place. This section tells you where each
kind goes, so that every scan puts them on the shelf with their names and covers.

**PS1 games** go into the `Games` folder, **one folder per game**, named after the game. You can also group games
into folders of your own, and each such folder becomes a group in the set picker (section 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                a folder of games: a group of its own in the set picker
    Klonoa/                   Klonoa.pbp
```

AutoBleem reads the usual disc image formats: `.cue` with its `.bin` (or `.img`), `.pbp`, `.chd` (including
zstd-compressed ones), `.iso`, and `.ecm`, which the scan decodes for you. A zipped game works too: the **Unzip**
processor unpacks it before the scan reads it (section 3.14).

You do not have to be tidy. A game on several discs belongs in one folder with all its discs, but if you copy in
folders named `Game (Disc 1)`, `Game (Disc 2)` and so on, the scan merges them into one `Game` folder. Games
dropped straight into `Games/` as loose files are sorted into folders of their own by the scan as well.

**Names and covers** come by themselves. The scan reads each disc's serial number and takes the title, the
publisher, the year, the number of players and the region from RetroArch's PlayStation database or from the cover
databases. If you want your own cover, put a PNG or JPEG next to the game's image, with the same name. Without one,
the box art comes from the cover databases or, with RetroArch installed, from libretro's thumbnail set; on a
Raspberry Pi, a PC or Windows a missing cover is fetched online (Options → *Fetch box art online*). If the scan
gets something wrong, correct it in the game editor and switch on *Lock data*, so the next scan keeps your change.

**Other systems' games** go under `RetroArch/roms/`, **one folder per system, named the way RetroArch's databases
name it** - for example `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo Entertainment
System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` or `FBNeo - Arcade Games` (or `Arcade`). The
folders are made for you, and the ROMs may stay zipped. On a Raspberry Pi, a PC or Windows the scan reads them
by itself and writes RetroArch's playlists. A console stick cannot do this alone, so there you run **UpdateRoms**
on the PC (chapter 5).

**Apps** go under `Apps/<name>/`, each with an `app.ini` - its name, its icon and what to run - and a `run.sh`.

**Packages.** Some Apps are game engines: they need the data of a game you own before they can play it. Doom,
Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, DOS games and more work
this way. Put the game's files into a `Packages` folder on the stick, one folder per game - for example
`Packages/Doom/DOOM2.WAD` - and AutoBleem recognises them by a table that comes with it (`rc/packages.ini`). In a
folder it recognises, loose game files are packages of their own. AutoBleem only reads your files and never
changes them. A package can also come from the Store (section 3.13).

Where the launcher shows it, the *Packages* row of the Apps tab (section 3.3) lists the game data that was found.
Cross on an entry opens its **Package info**: what the data contains, a description, where the files are and
where they came from (your own files, the Store, a mod, or files that come inside an App), whether it is shareware
or free, and which installed App runs it. If nothing you have installed can run it, the info tells you so.

When you start an engine App, AutoBleem looks for game data it can run. With one set of data the game starts at
once. With several, a list (*Choose game data*) asks which one to play, and it starts on the one you chose last
time. If there is none, AutoBleem tells you which data the App needs and where to put it, and nothing starts.

**Your own games.** When AutoBleem does not recognise some data, its Package info says *Not recognized. If this is
a game, see the manual: Your own games.* The table only knows the games it was made for. For another one, write a
row for it in a `packages.ini` of your own in the `Packages` folder: AutoBleem reads yours first, so your rows win.

![The Packages picker, where you choose the game data to start with](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Scanning one part.** If you have only added games to one set or folder, *Re-scan games* can scan just that part,
which is quicker than scanning everything, and its bubble goes away when it has finished.

**Themes** go under `Themes/<name>/`, with their `theme.json` and their pictures - or drop the theme's zip into
`Themes/` as it is.

### 3.11 The PS1 BIOS

The BIOS is the PlayStation's own start-up program, and the emulator plays games most faithfully with the real
one. On a **PlayStation Classic** you do not need to do anything: the emulator uses the console's own BIOS. On a
**Raspberry Pi, a PC and Windows** put your own PS1 BIOS files into `System/Bios/`: `romw.bin` (the US/European
SCPH-5501/5502) and `romJP.bin` (the Japanese SCPH-5500, used for Japanese games). The installers fill these in from
the RetroArch BIOS packs, unless your own files are already there - they never replace yours. Without them the
emulator runs on its built-in HLE BIOS, a stand-in that many games accept and some do not, so if a game will not
start, a missing BIOS is the first thing to check.

### 3.12 Updates

AutoBleem keeps itself up to date, so you get new features and fixes without reinstalling anything. When the
launcher starts, and once a day after that, it checks the site for a new version on its **channel**. You choose the
channel in Options → *Updates*: `release`, `testing`, `nightly`, or `off` if you do not want it to look at all.
If you do not want to wait for the daily check, *Software Update* in the system menu checks now.

When there is a new version, AutoBleem asks you what to do. *Update now* downloads it and installs it, which takes
a few minutes. *Remind me tomorrow* asks again in a day, and *Skip this version* does not ask about this version
again. Whatever you choose, your games, saves and settings always stay; after an update the launcher scans your
games once more. The channel tag in the top-left corner (section 3.1) shows which build you have.

How the update is installed depends on the machine:

- On a **Raspberry Pi** and the **PC stick**, the installer runs again after the download, with the same progress
  screen as the first start, and offers a newer RetroArch too. Then the launcher is back.
- On **Windows**, the downloaded setup opens, installs the new version and starts the new launcher.
- On a **PlayStation Classic**, only a console with the **AutoBleem kernel** (ABFlashKit, section 6.2) and a
  **Wi-Fi network** set up in PSC-Bios (section 6.1) can update itself - a stock console has no network, so the
  launcher does not look. After *Update now* the launcher closes and the AutoBleem picture stays on the screen
  while the stick is updated, which takes a few minutes; then the new launcher starts. Without a network,
  *Software Update* tells you *Not connected*. Any console stick can also be updated from a PC with
  `AutoBleemInstaller.exe` (section 2.1).

### 3.13 Extensions and the AutoBleem Store

**Extensions** add new things to the launcher - their own screens and features - without changing AutoBleem
itself. The AutoBleem Store and PSC-Bios are extensions. An extension lives in `Extensions/<name>/` on the stick
(on a Raspberry Pi on its data partition, on Windows in the data folder); to install one, unpack its zip there.

To see them, open the system menu (**L2 + R2**) and choose *Extensions*. The ones that come from the AutoBleem team
are at the top, and any others follow under *Third-party extensions*. Cross runs the selected one, and Triangle
switches it off, or on again. PSC-Bios on the console is the exception: you set up the Wi-Fi, the pads and the
clock with it, so it cannot be switched off there. When an extension cannot run, its row tells you why - it needs
a network and there is none, it is not made for this system, it was made for a different version of AutoBleem
and needs an update, or it could not be loaded. If an extension ever stops the launcher, AutoBleem switches it off
and the list tells you so; you can switch it on again here.

![The Extensions list](../images/en/extensions.jpg)

**The AutoBleem Store** is the first extension: a place to browse Apps and games and install them with one press,
on every system AutoBleem runs on. A PlayStation Classic needs the AutoBleem kernel for it, because the Wi-Fi
comes with the kernel. Open it from the Quick menu (*Store*, section 3.4). It has four tabs, and L1 and R1 move
between them.

The **Apps** and **Games** tabs list what the sources offer, each item with its picture, its version, its size and
the small icon of the source it comes from. The Apps tab also lists PE apps, with their license and source, and
game-data packages (section 3.10). What you have already installed carries an *Installed* badge. The hint bar shows
the buttons that apply to the selected row:

| Button | In the Apps and Games tabs |
|---|---|
| Cross | Installs the item - or updates it, tries again after a failure, or cancels a download that is waiting or running. |
| Triangle | Removes something the Store installed. |
| Square | Refreshes the lists from the sources. |
| L2 / R2 | Jump to the previous or next first letter. |
| Select | Shows one source at a time, when you want to see what a single source offers. |
| Start | Searches the titles. |

The pictures are kept once they have been loaded, so the lists come up quickly next time, and a picture that did
not load can be tried again.

The **Downloads** tab shows what is downloading, waiting, failed or installed, with a progress bar that moves
steadily. You do not have to watch it: downloads go on in the background, also after you leave the Store, and
while you are elsewhere in the launcher a bubble shows the running download with its speed and the time left
(for example `1.4 MB/s · 0:42`). Starting a game or powering off only pauses them, and a stopped download carries
on where it stopped. If the network drops, the item says *Waiting for the network* and goes on from where it was
when the network is back; after 30 minutes without a network it gives up. Downloads over 2 GB work on every
platform, including the 32-bit builds. A game you install appears on the shelf after the next scan, with the
Store's picture as its cover.

The **Sources** tab shows where the lists come from, each with its icon: AutoBleem's own catalog, any TSV list
dropped into `System/Extensions/store/sources/`, and the addresses you add yourself with *Add a source URL*. Cross
on a source you added lets you rename it, change its address, switch it between `http://` and `https://`, or
remove it.

![The Store's Apps tab](../images/en/store-apps.jpg)

![The menu of a source you added](../images/en/store-source-menu.jpg)

What AutoBleem's own catalog offers is also listed on the download site, at
`https://autobleem.retromenele.pl/store/`. A source you add yourself is another matter: **you are responsible for
what the sources you add contain.**

**Your own games on your network.** If you keep your PS1 games on another computer at home, `abstored`, the Store's
LAN server, can offer them to the Store over your network, so you install them like any other item. It runs on any
Linux machine - a Raspberry Pi, a home server - and only reads the folder, never changing it. Start it with
`abstored <games folder>`, then open `http://<that machine>:8124/` in a browser: the page shows what it serves and
any problems it found. In the Store, add `http://<that machine>:8124/store.tsv` as a source. Ready programs for
Linux and Windows are on the Store's page, in its **LAN server** tab, and `INSTALL-linux.md` (`ext_store/server/`
in the source) explains how to set it up as a service. **LAN Share** (section 5.2) puts games and discs from a PC
on such a server.

### 3.14 Scanner processors

Scanner processors prepare your games before AutoBleem reads them. A processor is a small program that every scan
runs first. It can turn a format AutoBleem does not read into one it does - unpacking a zipped game, for example -
or change a game's data, such as applying a translation patch. Processors live in `System/Processors/<name>/` on
the stick (on a Raspberry Pi on its data partition, on Windows in the data folder); to install one, unpack its
folder there, and the next scan runs it.

**Unzip comes with AutoBleem.** It unpacks zipped PS1 games in `Games/` before the scan reads them, and zipped ROMs
one at a time; arcade sets stay zipped, because that is how the arcade cores read them. Updating AutoBleem updates
Unzip too, and if you switched it off, it stays off.

A processor does its work once: when it has dealt with a game, it is not run on it again until the game changes.
While a processor works, the bubble at the top right shows what it is doing, and a warning or a failure appears on
the line under it; `processors.log` in the logs folder has the details. Starting a game or RetroArch stops a
processor that changes files, so the game has the machine to itself, and the next scan finishes the work.

To manage them, open the system menu (**L2 + R2**) and choose *Scanner processors*. You see them in the order they
run, with one tab for the PS1 games and one for the ROMs; L1 and R1 switch between the tabs. The order matters: a
processor that unpacks has to come before one that patches what was unpacked.

| Button | In Scanner processors |
|---|---|
| Square | Picks the selected processor up, so Up and Down move it to its new place; Square puts it down again. |
| Cross | Switches the processor off, or on again. |
| Triangle | Has the processor look at every game again at the next scan, also the ones it has already dealt with. |
| Circle | Goes back, and starts a scan if you changed anything. |

A processor that was built for another machine stays on the list, greyed out, so you can see it is there but
that it does not run here.

![Scanner processors](../images/en/processors.jpg)

If you want to write a processor of your own, Unzip's page, `https://github.com/autobleem2/proc_unzip`, explains
everything a processor has to do, and `tools/proc_check.py` in AutoBleem's source checks yours before you share
it.

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

1. Copy your ROMs onto the stick under `RetroArch/roms/<system>/` (section 3.10). The folder names must be
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

The Store can install games from a server on your own home network (section 3.13). **LAN Share** is the
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
is not a crash, keep every log: switch on Options → *Diagnostics* → *Keep logs on the stick* (it works from the
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
game has a folder of its own and is in one of the formats of section 3.10. The *Game Manager* (section 4.1) lists
the folders the scan refused after the games, marked *Not added*, and tells you why each was refused; Square
deletes such a folder. After fixing a folder, *Re-scan games* in the system menu runs the scan again.

**Games have no covers.** Either the cover databases were not installed - run the installer again with them
ticked - or, for RetroArch games on a console, UpdateRoms has not been run on the PC yet (chapter 5).

**A pad does nothing, or its buttons are mixed up.** AutoBleem does not know that pad's layout. On a console,
map it with PSC-Bios's gamepad wizard (section 6.1). On a Pi or a PC, the Hardware Information page (section
4.2) shows what the system sees of the pad, which helps you tell whether it is detected at all.

**The screen stays black after a game on the console.** The launcher's picture did not come back when the game
ended. AutoBleem rebuilds its window by itself, up to three times. If the screen still stays black, hold the
Power button and switch the console on again.

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
