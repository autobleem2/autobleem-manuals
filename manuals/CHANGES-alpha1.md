# English manual: changes for v2.0.0-alpha1 (for the translators)

Source: `manuals/en/autobleem-user-manual.md`, compared with the manual of 2026-09-27. Every section below
lists what to add or change in the other 16 languages. Use each language's own launcher terms from its
`src/resources/lang/<Language>.txt` (the launcher's menu names are now sentence case: *Re-scan games*, *Power
off*, *Favorite games*, *Game history*). Section numbers are unchanged (the manual has two sections numbered 3.7;
left as they are so the cross-references stay the same in every language).

## Chapter 1 - What you get
- The launcher bullet now names the Quick menu and the Store.
- The console-tools bullet: PSC-Bios is shown in the menus as *Network & Controllers* and is also on a Raspberry
  Pi and the PC stick; ABFlashKit stays PlayStation Classic only.

## 3.1 The launcher
- Details grid is compact; a fact a game does not have is left out; a soft reflection under the covers.
- New: the default look is the **ab2.0.0** theme (a fresh install or an update that brings it switches to it once).
- New: the hint bar has two lines of four slots (line 1 = what the buttons do for the selection; line 2 = Select,
  Start, Triangle, L2 + R2, dimmed when one does nothing).
- New paragraph **A fresh install**: the welcome card ("Hi, and welcome to AutoBleem!") shown instead of an empty shelf.
- New paragraph **Notifications**: the bubbles at the top right, including the Store download's speed and time left.
- New paragraph **The channel tag**: ALPHA / BETA / RC / TESTING / NIGHTLY / DEV chip with the short version, under the
  pad battery plate; none on a release.

## 3.2 Controls
- New table row: **Up** opens the Quick menu.

## 3.3 The sets
- PlayStation tab rewritten: *All games* + *Internal games* only on the console; *USB games* (the whole `Games/`
  folder) is the first row everywhere, then the folders; on a Pi, PC stick and Windows the list starts at *USB games*.
  Names in sentence case (*Favorite games*, *Game history*, *Lightgun games*).
- RetroArch tab only where RetroArch is installed.
- New: the footer names the keys (L1 / R1 tabs, L2 / R2 page, Cross picks, Circle *Back*).

## 3.4 The Quick menu
- Item names: *Re-scan games*, *Store* ("browse and install games, apps and extensions"), *Network & Controllers*,
  new *Restart launcher* (console, Pi, PC stick), *System menu...* ("everything else: Options, Game Manager, Power off and more").
- Each row has a one-line description. "Every item is also in the system menu" now has the two exceptions.

## 3.5 The system menu
- *Re-Scan Games* -> *Re-scan games*; *Power Off* -> *Power off*.
- *Hardware Information* is the same page on every platform (it no longer opens PSC-Bios on the console).
- *Software Update* shows *Update available* when one is known; *RetroArch* only where RetroArch is installed.
- Rows have one-line descriptions.

## 3.6 Options (table rewritten)
- Groups now: Interface, Fonts, Sound, Emulation, Library, Updates, Diagnostics.
- New rows: **Display** (resolution, with the *Keep this display mode?* confirmation), **Emulator screen scaling**
  (replaces **Widescreen**), **Cover shine**, **Splash screen**, **Animations**, **Persist RetroArch config**,
  **Show performance**.
- Renamed: *Showing Timeout* -> **Notification timeout** (0 to 20 s, 0 = Off); *Use Font from Theme* -> **Use default
  font** (Red Hat Text; the Font row names the font in use); *Update RA Config* -> *Update RA config*; sentence case on the rest.
- The three RetroArch rows only where RetroArch is installed; on/off values read ON / OFF; the default theme is ab2.0.0.
- *Updates* row not on a development host.

## 3.7 A game's settings (game editor)
- Details pane lists title, publisher, year, players, folder, memory card.
- Groups are now **Game, Display, Rendering, Emulator** (was Game, Video, Emulator): Display = Resolution, Remove seams,
  Dithering, Smoothing, Filter (Nearest, Linear, Sharp, Sharp (simple), Quilez, CRT (fast), CRT-Pi), Scanlines, Scanline
  brightness; Rendering = Plugin, Frameskip. *Lightgun game* / *Play using RA* only where RetroArch is installed.
- "Saved in the emulator" greys the Display, Rendering and Emulator rows (was Video and Emulator).
- New closing paragraph: picture shape and resolution are global Options; a game without a title is shown by its folder name.

## 3.7 (second) Memory cards and save states
- Resume points: framed cards with picture, slot number and date; **NEWEST** chip; *No resume point* for an unused slot;
  Resume icon greyed when a game has none; the emulator's *Please wait...* while the resume point is written.

## 3.8 Starting games
- Reset on the console also works from inside the in-game menu.
- **New: the in-game menu** (pcsx-abnxt): how to open it (menu button / Select + Start / Esc; hold 2 s = Reset), three
  tabs Game / Picture / Controllers (L1 / R1), what each row does, *Load autosave*, *Reset game*, *Exit*, the PCSX menu, greyed rows.
- Cross-reference fixed: the emulator choice is in section 3.6.

## 3.12 The Store
- Installed items carry an *Installed* badge (were greyed out); Cross also cancels a queued or running download; Square refreshes;
  L2 / R2 jump by letter (were pages); the footer shows the keys of the selected row.
- Downloads tab: the running download's bubble with speed and time left (`1.4 MB/s · 0:42`); *Waiting for the network*
  and automatic resume (gives up after 30 minutes).

## 4.1 Game Manager
- The list shows titles only; the folder is in the details.

## 4.2 Hardware Information
- Same page on every platform; no longer opens PSC-Bios on the console.

## 6 The console tools / 6.1 PSC-Bios
- Opened by *Network & Controllers* (Quick menu and system menu), not by *Hardware Information*.

## 7 If something goes wrong
- *Re-Scan* -> *Re-scan games* in the sentence about a game missing from the shelf.

## Screenshots that are outdated (`manuals/images/<lang>/`)
Every launcher shot is in the old look; all must be retaken in the ab2.0.0 theme. What each new shot must show:

| File | The new shot must show |
|---|---|
| `launcher.jpg` | The shelf in ab2.0.0: reflection under the covers, compact details grid, two-line hint bar. Channel tag not visible (or note it). |
| `launcher-icons.jpg`, `launcher-icons-game.jpg` | The icon row with the game-menu tiles; a Resume icon greyed (no resume point) in one of them. |
| `launcher-apps.jpg` | The Apps set in the new look. |
| `set-picker.jpg` | PlayStation tab: *USB games* row (and *All games* / *Internal games* on a console), counts, footer with *Back*. |
| `set-picker-retroarch.jpg`, `set-picker-apps.jpg` | The RetroArch and Apps tabs in the new look. |
| `system-menu.jpg` | The grouped menu (top two items, Library, System, Leave) with row descriptions. |
| `options.jpg` | Options with the headings Interface / Fonts / Sound / ..., the new rows (Display, Emulator screen scaling, Cover shine, Splash screen, Animations) and ON / OFF values. |
| `game-editor.jpg` | The editor with the Game / Display / Rendering / Emulator groups and the details pane. |
| `memory-cards.jpg`, `memory-card-editor.jpg` | New look. |
| `game-manager.jpg` | Titles only; folder in the details. |
| `hardware-info.jpg` | New layout (UIREV-19/20). |
| `about.jpg` | The new About screen (UIREV-38). |
| `button-guide.jpg`, `keyboard.jpg`, `rescan.jpg`, `app-start.jpg`, `extensions.jpg`, `processors.jpg` | New look. |
| `store-apps.jpg`, `store-sources.jpg`, `store-source-menu.jpg` | Store in the new look (Installed badge). |
| `pscbios-main.jpg`, `pscbios-network.jpg`, `pscbios-gamepads.jpg`, `pscbios-wizard.jpg` | New look; the hub titled *Network & Controllers*. |
| `abflashkit-*.jpg`, `lanshare.jpg` | ABFlashKit: new look; LanShare is a Windows program, unchanged unless retaken. |

New shots the text now needs (and a reference line to add in the manual after the shots exist):
- `quick-menu.jpg` - the Quick menu (Up on the shelf) with its descriptions (section 3.4).
- `welcome-card.jpg` - a fresh install's welcome card (section 3.1).
- `resume-picker.jpg` - the resume slots with a NEWEST chip (section 3.7, memory cards and save states).
- `store-downloads.jpg` - the Downloads tab with a running download (section 3.12).
- `ingame-menu.jpg`, `ingame-menu-picture.jpg` - the emulator's menu, Game and Picture tabs (section 3.8).
- `download-bubble.jpg` - the Store bubble with speed and time left (optional).

Note for whoever runs `tools/manual_shots.py`: its screen list is from before the redesign (it opens the system menu by
index, e.g. `menu 5` for Options, and uses Up for the icon row); it needs checking against the new menu order and the
Quick menu before it is run.
