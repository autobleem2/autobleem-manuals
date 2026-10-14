# English manual: changes for v2.0.0-alpha2 (for the writer and the translators)

Source: `manuals/en/autobleem-user-manual.md` (the alpha1 text, see `CHANGES-alpha1.md`), compared with the
launcher's `develop` against the tag `v2.0.0-alpha1.1`. Names in *italics* are the on-screen names from the
launcher's `src/resources/lang/English.txt` (translators: use each language's own `lang/<Language>.txt`).
Section numbers are unchanged; the new section is added after 3.8 as **3.8a** (a number the writer may change as
long as the old ones keep theirs). Launcher commits are given as short shas.

Screenshot marks: **VM** = the PC-stick VM sandbox (`tools/manual_shots.py`) can show it; **CONSOLE** = only a
PlayStation Classic (or a Pi) can. `manual_shots.py` keeps these as not-here: PSC-Bios, ABFlashKit, LanShare,
the RetroArch tab (needs RetroArch), `rescan`, `store-sources`.

## 1 What you get
- Mention the RetroArch core list now starts with *PlayStation 1* (see 3.8) and that Doom-type games run from
  *Packages* (3.9). One sentence each, no new bullet.

## 2.1 PlayStation Classic
- **Insert the stick** (5ce2045, AUTOBLEEM-28/29): with no stick in the console, a picture in the launcher's
  language says to insert one - in any USB port. After 5 minutes, or at once on POWER, the console goes to sleep.
  If the stick is pulled while AutoBleem runs, the same picture appears.
- **Stick check** (5ce2045): a stick that was not removed cleanly is checked at boot, at wake and after a pull,
  with a progress bar, using the checkers shipped on the stick (fsck.fat, fsck.exfat, e2fsck). Say that this can
  take a while on a big stick and must not be interrupted.
- The standby LED is **orange** now (6e47727, AUTOBLEEM-1). Wherever the text says the LED turns red in
  standby, change to orange. Red stays for a real power off (the console had no standby, see DOCS-12 below).
- Step 4 "second USB port (right, player 2)": CHECK result - the launcher's insert-stick code and
  `rc/selection.sh` work with a stick in any port, and the standby code treats the *rear micro-USB* port as the
  special one. The words "second USB port (right, player 2)" are not what the launcher needs; the front ports
  are the advice (see DOCS-12 (1)). Write: "plug it into one of the console's **front USB ports**". Keep a
  note that player 2's pad needs the other front port. (Not tested on a console by me.)
- Screenshots: NEW `insert-stick.jpg` (the picture, English) - CONSOLE; NEW `stick-check.jpg` (progress bar) - CONSOLE.

## 3.1 The launcher
- Start-up (17624ba, a9f2dc6, 63e1a26): the menu appears about 1.9 s after the splash on the PSC; the pads are
  set up behind the splash. Mention only if the text gives a boot time; the *Splash screen* row (3.6) is the
  place.
- Hint bar (13208ff): the line 2 slots are unchanged; no change.
- No-cover placeholder (df6ba5a, 41f7a49): a game with no cover shows a disc lying in the case's black tray
  (was a plain picture). Add one sentence.
- Covers may be PNG **or JPEG** (39d8997, AUTOBLEEM-27): where the text says `.png`, say "PNG or JPEG".
- Retake: `launcher.jpg`, `launcher-icons.jpg`, `launcher-icons-game.jpg` - **VM** (a game without a cover
  in one of them shows the placeholder). NEW `no-cover.jpg` - **VM** (optional).

## 3.2 Controls (13208ff, 9bdbb5f)
- New row / changed text: **hold Start + Select, or Home, for 2 seconds = back to AutoBleem**, on every pad
  (the console pad, a USB pad, a Bluetooth pad); a short press opens the emulator's menu (in a game). In an
  **App** only the hold works (no short-press menu).
- Hint text on screen: *Hold Select+Start or Home for 2 seconds: back to AutoBleem* and *Short press of
  Select+Start or Home: the emulator's menu*.
- Square on the shelf for a disc: *Copy disc* (see 3.8a). Circle returns to the disc view (3.8a).
- Screenshots: see 4.3.

## 3.3 The sets (7409086, 991116b)
- RetroArch tab: no change in the list; the Apps tab now also shows **PE apps** (Windows programs run by the
  PE runner; the label *PE apps*, and *cannot run on this console* for one the console cannot start).
- Row *Packages* (see 3.9) in the PlayStation / Apps set list where the launcher shows it.
- R1 in the disc view is the **first-letter jump**; on an empty shelf with a drive, R1 *Disc* (d62d674, 941b633).
- Retake `set-picker.jpg`, `set-picker-apps.jpg` - **VM**. `set-picker-retroarch.jpg` - needs RetroArch, CONSOLE
  (or a Pi).

## 3.5 The system menu
- Wherever it says the LED is red during standby, say orange (6e47727). Power off is unchanged.
- *Virtual gamepad* (new screen; see 4.5 below) and *Hardware Information*: Circle returns to the system menu
  (abd8552), not to the shelf.
- Retake `system-menu.jpg` - **VM**.

## 3.6 Options (d2bbe3b, 8b22823, ad4c38a, af3d49b, 22f7652, 60e4b89, 41f1cdb, b3959b7, 84aa9c9, 705f3fb)
In the group **Display** (and next to it):
- *Display* list on the console: *CRT 4:3* (720x480, CEA 480p, for a CRT or a 4:3 capture device) next to 720p
  and 1080p. The usual *Keep this display mode?* confirmation applies.
- *CRT margin:* 0 to 10 % in steps of 1 % (the safe area; applied live; also read before the boot splash).
- *Picture height:* -40 to +40 in steps of 2, live, on **any 4:3 output** (CRT 4:3 and a 4:3 window on a
  VGA/PC output). RetroArch's game picture follows it (590d405).
- *VGA margin* on a 4:3 VGA output: CHECK - the row is shown "on any 4:3 output" (22f7652); no separate English
  string called "VGA margin" exists in English.txt, so call it by the row's on-screen text (*CRT margin:*).
- Theme: on *CRT 4:3*, a theme without a 4:3 layout is replaced by the default theme (ab2.0.0) after the
  confirmation, also at start; the notification says *Theme switched to the default (CRT 4:3)*. The theme picker
  lists only themes that have a 4:3 layout in that mode.
- *Emulator screen scaling:* is followed by the new row *Screen halo:* (41f1cdb).
- Filter list (game editor too): *CRT (raster)* is the eighth filter, new (d2bbe3b) - the list is now Nearest,
  Linear, Sharp, Sharp (simple), Quilez, CRT (fast), CRT (raster), CRT-Pi.
- The RetroArch cores window opens with *PlayStation 1* first (7409086); *PlayStation 1 Games* names the PS1
  RetroArch games; SwanStation is the PC's PS1 core (cad6fda).
- Row *Clean game names:* in the group **Library** (ON by default; merged after the inventory was made):
  RetroArch game lists show names without bracketed tags such as (USA), (Rev 1), [!]; OFF shows the file
  names; the file name stays in the game's details; PS1 games are not affected (their titles come from the
  database).
- Retake `options.jpg` - **VM**. NEW `options-display.jpg` (Display group with CRT margin, Picture height) -
  **VM**. NEW `crt43-theme-notice.jpg` - CONSOLE (needs the 720x480 mode; the VM shows 4:3 windows only, not
  verified).

## 3.7 A game's settings (80e3871, d2bbe3b, 03e8f96)
- New row **Resume:** with the values *Ask*, *Last slot*, *Never* (EMU-26). *Ask* shows the resume-slot
  picker, *Last slot* continues from the newest slot at once, *Never* starts the game from the beginning.
- Filter: *CRT (raster)* added to the list (see 3.6).
- Message *Not saved: this game has no pcsx.cfg* for a drive game without a config.
- **A disc in the drive**: the editor greys the rows the disc cannot use and says *Not available for a disc in
  the drive*.
- Held Left / Right and Up / Down repeat on the editor, RetroArch game options and cores screens (0cfb05c,
  350f480): one sentence.
- Retake `game-editor.jpg` - **VM** (shows Resume row). NEW `game-editor-disc.jpg` - **VM** if the fake drive
  (see 3.8a) is used, else CONSOLE.

## 3.7 (second) Memory cards and save states (cad6fda, 9926846)
- PS1 games in RetroArch now have resume slots too; a slot shows the emulator badge (the AutoBleem 2 or the
  RetroArch logo) so you see which emulator wrote it.
- Empty card text *no card yet*; confirmation text now *Do you want to save memory card data?*
- Retake `memory-cards.jpg`, `memory-card-editor.jpg`; the NEW `resume-picker.jpg` promised in alpha1 -
  **VM** (badges are visible on a PC stick: AB2 and RetroArch; a PSC shot is not needed).

## 3.8 Starting games, RetroArch and Apps (13208ff, 3570ca0, 7409086, 08e4028, 991116b, 9a373dd, c33900a)
- Leaving a game: the one way out is hold Start+Select or Home 2 s (3.2); a short press opens the emulator's menu.
- **Reset** on the console always stops an App as well (3570ca0).
- **Game settings** for an App (*Game settings* - "Change how this program is started"): *Pad mode:*
  (*Automatic*, *PSC pad*, *Xbox 360 pad*, *PSC pad (system)*, *Xbox 360 pad (system)*), *D-pad as stick:*,
  *Stick as D-pad:*. A first-run question for some Apps: *Which controls does your pad have?* (*One D-pad* /
  *Analog sticks*) and for Windows-type Apps *What do you want to do?* (*Run Windows*, *Install Windows*,
  *Run DOS*, *Uninstall Windows*). *Press one of the buttons.* for a key mapping.
- **PE dialogs** (c33900a, 88a6c61): text screens and questions an App asks appear as AutoBleem screens
  (*Message*, *Choose an option*), titled with the App's name.
- RetroArch cores window: *PlayStation 1* first (7409086). The status text `RetroArch needs a newer system
  library than this console has - use the RetroArch that comes with AutoBleem` (b823028) goes in 7.
- `abupdate --retroarch install|remove` (08e4028): installs or removes RetroArch alone on the PSC. Mention in
  3.11 / 6 only if the manual describes `abupdate`; CHECK - the manual does not name it today, so probably
  no change.
- Screenshots: retake `app-start.jpg` - **VM**. NEW `app-game-settings.jpg` (pad mode, D-pad as stick) -
  **VM**. NEW `pe-dialog.jpg` - CONSOLE (PE runner on the console; VM not verified). NEW `retroarch-cores.jpg`
  - CONSOLE (RetroArch needed; NOT_HERE has the RetroArch tab).

## 3.8a A disc in a USB drive (NEW section; ca94cb0, 185dea9, eff09b7, d108990, 9d32e64, d62d674, 03e8f96, 750639e, bcc44c9)
A USB CD/DVD drive with a PlayStation or audio disc is a "game" on the shelf. Text for the writer:
- **Disc view**: it opens itself when a disc is detected (and R1 *Disc* opens it from the shelf); it shows the
  disc's cover (from the cover databases, or the thumbnails tree fetched online), its serial and the title.
  Circle on the shelf brings the disc view back; R1 is the first-letter jump again. After a game from the disc,
  options or an extension's settings, the disc view is back (c81943a). Cross plays the disc; a PS1 game from the
  disc resumes and saves into the disc's folder (379b126).
- **Drive chip** (states): hidden (no drive), dim (drive, no disc), blinking *Reading the disc...*, then
  *Disc: <title>*; *This is not a PlayStation disc* for any other disc; *The disc cannot be read now*.
- **CD player** for an audio CD: *CD PLAYER* / *Audio CD*, *TRACKS*, *TOTAL TIME*, *Track*; keys *Play track*,
  *Stop*, *Previous/next*, *Seek*, *Pause*, *Repeat:* (*off* / *on*), *Shuffle:*, *Selected:*; *This disc cannot
  be played*.
- **Copy disc** (Square): copies a known PlayStation disc to *Games* as a **CHD** (with a `.m3u` for
  several discs, disc 1 first); a blocking progress popup *Copying the disc* with *Speed*, *Time left*,
  *Cancelling...*, *Abort*; ends with *The disc is copied to Games.* Refusals: *Already in Games: %1*, *Not enough
  room in Games: the copy needs %1, %2 is free.*, *The copy failed: %1*, *%1 sectors could not be read and were
  written as zeros.* (*Unreadable sectors*), *Cancelled*; a confirmation *Copy "%1" to %2? It takes %3 of the %4
  free.* Works for a disc the databases do not know (it is named by its serial, c6f0e22).
- **LibCrypt**: the `.sbi` file of a LibCrypt disc is fetched from the site before the disc plays and when it
  is copied (bcc44c9, 6bc043e, 941b633); needs a network on a Pi / PC; on the console, the Wi-Fi of PSC-Bios.
- The game editor of a disc greys the rows it cannot use (see 3.7). Windows has no drive support.
- Screenshots: NEW `disc-view.jpg`, `disc-chip.jpg`, `cd-player.jpg` - **VM**: `Extensions/disc-fake*/fake.cue`
  (App::startDriveWatcher, any folder name starting `disc-fake`) stands for the drive's disc; not yet a step in
  `tools/manual_shots.py` and **not run by me** - the writer's helper must add the steps and put a fake cue in the
  sandbox. NEW `disc-copy.jpg` (progress popup) - **VM** only if the fake drive can be ripped (not verified),
  otherwise CONSOLE/Pi with a real drive.

## 3.9 Adding games (afba8f6, 62901fc, bd47fb9, 0009da9, 64ef9e7, 765286e, b0dffb4)
- **Packages**: a *Packages* folder on the stick (for example `Packages/Doom/DOOM2.WAD`) holds game data for
  engines (Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, DOS
  games...); a shipped table `rc/packages.ini` recognises them. Screens: the **Packages picker** and the
  **package info** (*Contents*, *Description*, *Location*, *Source*, *Runs with*, *Mod*, *Shareware*,
  *In this App*, *Your files*, *Choose game data*). Texts: *No game data found*, *Unknown data*, *Nothing
  installed runs this*, *%1 needs game data it can run: %2.*, *Not recognized. If this is a game, see the
  manual: Your own games.* A recognised folder's loose game files are packages of their own (0009da9). Your
  own files are only read, never changed. A package can also come from the Store.
- **Scoped scans**: Re-scan games can scan one part (a set or folder) and takes its bubble down at the end.
- Screenshots: NEW `packages-picker.jpg`, `package-info.jpg` - **VM** (the VM stick's `Packages/` can hold a
  fake WAD; not in manual_shots.py yet).

## 3.11 Updates
- CHECK result: no launcher code change to the update flow since alpha1.1 other than `abupdate --retroarch`
  (08e4028) and the Software Update row for RetroArch's version on the PSC (fd6349b). The existing text on
  channels (`release`, `testing`, `nightly`, `off`) stays. See DOCS-12 (2).

## 3.12 The Store (991116b, 3a13c52)
- A Store tab for **Apps** (PE Apps with licence and source), item kinds for packages. Retake `store-apps.jpg`,
  `store-source-menu.jpg` - **VM**; `store-sources.jpg` - kept (NOT_HERE).

## 4.1 Game Manager / 4.2 Hardware Information
- Title *Game Manager - Select game* (capital M). Battery text of e96aa25 - see the CHECK below.
- Retake `game-manager.jpg`, `hardware-info.jpg` - **VM**. Circle returns to the system menu (abd8552).

## 4.3 The button guide (13208ff, 9bdbb5f)
- Two new lines: *Hold Select+Start or Home for 2 seconds: back to AutoBleem* and *Short press of
  Select+Start or Home: the emulator's menu*. Retake `button-guide.jpg` - **VM**.

## 4.5 Virtual gamepad (NEW; no number yet in the manual - use 4.5)
- A system-menu screen *Virtual gamepad*: *The pads Apps are given*, *Pads the daemon sees*, *Daemon*; marks
  *connected*, *not readable*, *from the controller database*, *guessed by the daemon*, *unknown driver*, *Look
  again*, *Not in this build*. Circle returns to the system menu. Screenshot NEW `virtual-gamepad.jpg` - **VM**.

## 6 / 6.1 PSC-Bios
- No text change. Retakes of `pscbios-*.jpg` stay CONSOLE and are already in the alpha1 list.

## 7 If something goes wrong
- No stick / stick pulled / dirty stick: see 2.1 (sleep after 5 min; the check at boot). Add rows.
- `RetroArch needs a newer system library than this console has...` (b823028): the console's library is too old;
  use the RetroArch that comes with AutoBleem.
- *This game is protected by its PSN license and cannot be started* (spelling "license" now, as everywhere).

## Spelling changes to apply
`licence` -> `license`; *Link block*, *Link end block*, *Memory card manager*, *Memory card:*, *Loading... Please
wait...*, *Please wait... deleting*, *Game Manager*, *Unknown core (AutoDetect)*, *Re-scan games*.

## Screenshots that must be retaken (existing, `manuals/images/en/`)
VM: `launcher`, `launcher-icons`, `launcher-icons-game`, `launcher-apps`, `app-start`, `set-picker`,
`set-picker-apps`, `system-menu`, `options`, `game-editor`, `memory-cards`, `memory-card-editor`,
`game-manager`, `hardware-info`, `button-guide`, `keyboard`, `extensions`, `processors`, `about`, `quick-menu`,
`store-apps`, `store-source-menu`.
CONSOLE (kept or retaken on the console): `pscbios-*`, `abflashkit-*`, `set-picker-retroarch` (RetroArch),
`rescan` (scan over before a shot), `store-sources` (needs a user source). `lanshare` is a Windows program.

## New screenshots (proposed names)
| File | Section | Taken |
|---|---|---|
| `insert-stick.jpg` | 2.1 | CONSOLE |
| `stick-check.jpg` | 2.1 / 7 | CONSOLE |
| `no-cover.jpg` | 3.1 | VM (optional) |
| `options-display.jpg` | 3.6 | VM |
| `crt43-theme-notice.jpg` | 3.6 | CONSOLE |
| `game-editor-disc.jpg` | 3.7 / 3.8a | VM (fake drive, unverified) |
| `resume-picker.jpg` | 3.7 (second) | VM |
| `app-game-settings.jpg` | 3.8 | VM |
| `pe-dialog.jpg` | 3.8 | CONSOLE |
| `retroarch-cores.jpg` | 3.8 | CONSOLE |
| `disc-view.jpg`, `disc-chip.jpg`, `cd-player.jpg` | 3.8a | VM (fake drive, unverified) |
| `disc-copy.jpg` | 3.8a | CONSOLE (VM unverified) |
| `packages-picker.jpg`, `package-info.jpg` | 3.9 | VM |
| `virtual-gamepad.jpg` | 4.5 | VM |
| `store-downloads.jpg`, `ingame-menu.jpg`, `ingame-menu-picture.jpg`, `welcome-card.jpg` | as in alpha1 | VM |

## Commit e96aa25 (Swap Player 1/2, Battery) - CHECK result
Commit `e96aa25` is on `origin/feature/c11-c12-manual` of this repository (not on develop). Its **content is
already in the develop English manual**: the Options row "Swap Player 1 / Player 2 (PS1 emulators)" (line ~307)
and the pad-battery paragraph in 3.1 (line ~215), written in better form than e96aa25's. Do **not** merge it
for English. The commit also put the same text into the 16 other languages in a machine-translated, partly
broken form (e.g. the Danish edit splits a sentence in the middle: "Enhver **Batteri**-information ..." sits
inside the Player 1/2 sentence; the Czech row name is in Czech while its neighbours keep English names). The text is
still true on develop: English.txt has *Swap Player 1 / Player 2 (PS1 emulators):* and *Battery*, *battery low*,
and the message *This PS1 emulator does not support swapping pads yet*. Recommendation: skip e96aa25; the
translators follow the English text per CHANGES-alpha1 / this file. Add to the English row the sentence that
the row shows the message above for an emulator that cannot swap. (Whether the Battery paragraph in 4.2
(Hardware Information) should repeat the 3.1 text was not verified on a screen.)

## DOCS-12 additions
1. **Front port for the PSC stick** (CONSOLE; section 2.1 step 4 and 7). Launcher statement found: the comment in
   `payload/Autobleem/rc/selection.sh` (`poweroff_instead`, `suspend_wake`, CONSOLE-15 P2): a USB host on the
   micro-USB (power) port - the AutoBleem kernel's OTG, or a hub with the stick - refuses suspend-to-RAM ("trying
   to suspend as a_host while active"); the console then does a real power off instead of the standby, and the
   POWER button is a cold boot, not a quick wake. The longer account is in autobleem-main
   `docs/history/launcher-console-power-off.md` (not read; named by `docs/developer-guide.md`). CHECK result: no
   *written user advice* exists in `docs/`; the manual text is new. Proposed text for 2.1 / 7: "Use a **front**
   USB port for the stick. The rear micro-USB port (a host there only works with the AutoBleem kernel) keeps the
   console awake: with a stick or a hub on it the console powers off instead of standby, and POWER starts a
   cold boot." Later commits (CONSOLE-15 P2) idle a hub and a Wi-Fi dongle on the rear port before the standby
   so it can still suspend; I did not test it, so keep the advice as "front port recommended".
2. **Update channels and update sections.** The launcher offers (Options -> *Updates*, section 3.6; not shown on
   a development host): `release`, `testing`, `nightly`, `off`; *Software Update* in the system menu
   (*Update available* when one is known; *Checking for updates...*; *Not connected*); the answers *Update now*,
   *Remind me tomorrow* (*Ask again in a day*), *Skip this version*. The manual already says all of this in 3.6,
   3.11, 2.1 (installer), 2.2, 2.3 and 2.4; no wording is missing. Proposed small additions: (a) in 3.11 one
   sentence that the channel tag (3.1) shows what is installed; (b) in 3.11 for the PSC: `abupdate --retroarch
   install|remove` (08e4028) is a developer / support tool, not a menu item - leave out unless the writer wants
   it. No docs/ file in the launcher describes channels for users beyond what the manual says.
3. **ssh over the USB network cable.** Found in the launcher: `payload/System/ssh/README.txt` - on a console with
   the AutoBleem kernel, `System/ssh/authorized_keys` on the stick is added to dropbear's root account at boot;
   "log in as root; a password is also set on the AutoBleem kernel by default (see its own documentation)".
   `rc/selection.sh` shows the kernel starts a USB network (RNDIS, `/etc/autobleem/rndis`) on the power
   (micro-USB) port, turned off for the standby and back on after it. The launcher's docs do **not** state the
   password or the cable address; the value `autobleem` and the root user come from the task and are **not
   verified** by me (autobleem-core docs not read; the kernel's own documentation is not in this clone). Where
   it goes: section 6.2 (ABFlashKit - the AutoBleem kernel), as a new paragraph "Logging in from a PC": USB cable
   from the micro-USB port to the PC (it shows up as a network adapter), `ssh root@<console's address>`,
   password `autobleem`; plus the key file option from `payload/System/ssh/README.txt`; plus a security note
   (change the password; it is the same on every console). Not on a stock console. The cable address is open.
   Note it conflicts with the rear-port advice in (1): the micro-USB port is the device (gadget) side here and
   the host side there. Screenshots: none.

## Not verified
- No console and no VM was available: every screenshot mark is from the code and `tools/manual_shots.py`, not
  from a run. Disc view in the VM through `disc-fake*` is untested.
- The ssh password and the USB-network address (see DOCS-12 (3)).
- "VGA margin" has no English.txt string of its own.
- The 1.9 s start-up time and the stick-check details were taken from the first run of this task, not re-read.
