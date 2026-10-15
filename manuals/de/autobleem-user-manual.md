# AutoBleem 2 Benutzerhandbuch

AutoBleem 2 ist ein Spiele-Launcher für die **PlayStation Classic** und, seit Version 2, auch für den
**Raspberry Pi**, einen **PC, der von einem USB-Stick startet**, und für **Windows**. Er stellt deine PS1-Spiele
als Regal voller Cover auf, mit Hüllenbild und allen Angaben zum Spiel, und startet sie im mitgelieferten
PCSX-Emulator. Installierst du RetroArch dazu, laufen auch die Spiele anderer Systeme. In diesem Handbuch erfährst
du, wie du AutoBleem auf der jeweiligen Plattform installierst, wie du im Alltag damit spielst und was die
mitgelieferten Werkzeuge können.

> Die Downloads für alle Plattformen findest du auf **https://autobleem.retromenele.pl/**. Die Seite ist nach
> Plattformen geordnet: Was du herunterlädst, steht jeweils im Feld *Install*. Die *Build inputs* darunter holen
> sich die Installationsprogramme von selbst.

## 1. Was du bekommst

Mit AutoBleem wird aus deiner PlayStation Classic - oder aus einem Raspberry Pi, einem alten PC oder deinem
Windows-Rechner - eine kleine Spielkonsole mit einem richtigen Menü für deine eigenen Spiele. Dazu gehören:

- **Der Launcher.** Ihn siehst du, sobald du einschaltest: ein Regal mit Spiele-Covern, durch das du blätterst,
  und daneben die Angaben zum gewählten Spiel. Von hier aus startest du Spiele, ordnest sie in Sets
  (PlayStation, RetroArch, Apps), änderst Einstellungen, kümmerst dich um Memory Cards und Save States und lädst
  im Store Apps und Spiele herunter. Er sieht auf jeder Plattform gleich aus und wird überall gleich bedient.
- **Zwei PS1-Emulatoren.** `pcsx-abnxt` ist der aktuelle und voreingestellte, `pcsx-ab` der klassische Emulator,
  den AutoBleem schon immer mitbringt. Welchen du nimmst, legst du in den Optionen fest. Beide nutzen dieselben
  Einstellungen und Memory Cards, du kannst also jederzeit wechseln, ohne etwas zu verlieren.
- **RetroArch**, falls du auch Spiele anderer Systeme spielen willst: NES, SNES, Mega Drive, Game Boy,
  Arcade-Automaten und vieles mehr. Es ist auf jeder Plattform freiwillig. Du kopierst deine ROMs hinein,
  AutoBleem sortiert sie in Listen und startet jedes Spiel mit dem passenden Core. Auch PlayStation-Spiele
  laufen in RetroArch; der Core *PlayStation 1* steht ganz oben in der Core-Liste (Abschnitt 3.9). Spiele wie
  Doom laufen mit deinen eigenen Spieldateien aus einem Ordner `Packages` (Abschnitt 3.10).
- **Die Konsolen-Werkzeuge.** *PSC-Bios* - in den Menüs heißt es *Netzwerk & Controller* - richtet WLAN, Uhr,
  Bluetooth-Controller und Tastenbelegung ein, auf der Konsole ebenso wie auf dem Raspberry Pi und dem PC-Stick.
  *ABFlashKit* installiert den AutoBleem-Kernel auf einer PlayStation Classic (Kapitel 6).
- **UpdateRoms** für Windows. Die PlayStation Classic hat kein eigenes Netzwerk. Deshalb übernimmt dieses
  PC-Programm die Arbeit: Es bringt die RetroArch-Listen eines Konsolen-Sticks auf den neuesten Stand und holt die
  Cover, solange der Stick am PC steckt.

![Der Launcher: das Cover-Regal, die Angaben zum gewählten Spiel, die Tastenhinweise](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Installation

### 2.1 PlayStation Classic

AutoBleem läuft komplett von einem USB-Stick. In der Konsole selbst wird nichts verändert: Ziehst du den Stick ab,
ist sie wieder genau so wie vorher. Du brauchst nur einen Windows-PC, einen USB-Stick (USB 2.0, ab 8 GB) und die
Konsole.

Der Stick muss nicht leer sein, und er wird **nicht formatiert**, solange du das nicht ausdrücklich willst.
AutoBleem landet neben dem, was schon darauf liegt, und einen Stick, auf dem bereits AutoBleem 1.0 läuft, bringt
der Installer direkt auf den neuen Stand (siehe unten). Für eine unveränderte Konsole muss der Stick mit **FAT32**
formatiert sein, denn ihr eigener Kernel kann kein exFAT lesen. Sobald der AutoBleem-Kernel installiert ist
(ABFlashKit, Kapitel 6), startet die Konsole auch von einem exFAT-Stick - und die Grenze von 4 GB pro Datei,
die FAT32 setzt, fällt weg.

1. Lade **AutoBleemInstaller-<version>.zip** aus dem Bereich PlayStation Classic der Website herunter und entpacke
   es an einen beliebigen Ort. Darin liegen `AutoBleemInstaller.exe` und seine README. AutoBleem selbst wird
   erst während der Installation heruntergeladen, der PC braucht also eine Internetverbindung.
2. Steck den Stick an und starte `AutoBleemInstaller.exe`. Wähle zuerst den **Kanal**: *Release* ist die
   getestete Version und für die meisten die richtige Wahl, *Testing* ist die nächste Version, solange sie
   getestet wird, und *Nightly* der neueste Entwicklungsstand, der auch einmal nicht funktionieren kann. Dann wählst
   du das Laufwerk des Sticks. Die Zeile darunter verrät dir, welche AutoBleem-Version du gleich installierst und
   was jetzt auf dem Stick ist: *a fresh install* (eine Neuinstallation - die übrigen Dateien auf dem Stick
   bleiben unangetastet) oder *AutoBleem <version> is on this stick: it will be updated* (AutoBleem wird
   aktualisiert, deine Spiele, Spielstände, Memory Cards und Einstellungen bleiben erhalten).
   **Formatieren musst du nicht.** Die Schaltfläche **Format** neben dem Laufwerk ist nur für einen fabrikneuen
   Stick ohne Dateisystem gedacht, für einen, den die Konsole nicht lesen kann (zum Beispiel NTFS), oder für
   einen, den du komplett leeren willst. Sie fragt vorher nach und löscht dann alles auf dem Stick. Wähle dort
   FAT32, es sei denn, die Konsole hat bereits den AutoBleem-Kernel.
   Anschließend hakst du an, was installiert werden soll:
   - **Cover-Datenbanken** - Hüllenbilder und Beschreibungen der gesamten PS1-Bibliothek, damit deine Spiele
     ihre Cover von allein bekommen (standardmäßig angehakt, etwa 300 MB).
   - **RetroArch** - RetroArch mit seinen Cores, den zusätzlichen Anwendungen (Doom, Quake, Amiga, ...) und
     den Assets von libretro, für Spiele anderer Systeme. Standardmäßig aus; du kannst es später nachholen,
     indem du den Installer noch einmal ausführst.
   - **BIOS-Dateien** - die BIOS-Dateien, ohne die manche RetroArch-Cores nicht starten (nur zusammen mit
     RetroArch).
   - **Beispielspiele** - ein paar kostenlose Homebrew-Spiele, damit das Regal beim ersten Start nicht leer ist.
3. Klick auf **Install** und warte. Fortschrittsbalken und Protokoll zeigen dir jeden Schritt. Am Ende heißt der
   Stick `SONY` und hat eine Kopie von `UpdateRoms` bekommen (siehe Kapitel 5).
4. Wirf den Stick sicher aus, steck ihn in den **zweiten USB-Anschluss vorn** an der Konsole (den rechten, für
   Spieler 2) - der erste bleibt für deinen Controller frei - und schalte die Konsole ein. Statt des
   Originalmenüs startet AutoBleem. Für einen zweiten Controller nimmst du einen USB-Hub am vorderen Anschluss oder
   einen Bluetooth-Controller.

**Ein- und Ausschalten.** Mit eingestecktem Stick fährt die Konsole hoch, ihre Leuchte blinkt ein paar Sekunden,
während sie AutoBleem erkennt, und dann geht sie in den Standby, noch bevor überhaupt etwas auf dem Bildschirm
erscheint. Das ist normal: AutoBleem startet über den Update-Mechanismus der Konsole, und der funktioniert nun
einmal so. Drück einmal **Power**, und der Launcher erscheint.

Wählst du im Systemmenü *Ausschalten* oder drückst du die Power-Taste der Konsole, geht sie in den
**AutoBleem-Standby**: AutoBleem meldet zuerst den Stick sauber ab, dann leuchtet die Konsole **orange** - das
Zeichen, dass alles geklappt hat. Beim nächsten Druck auf Power ist der Launcher nach wenigen Sekunden wieder da.
**Solange die Leuchte orange ist, darfst du den Stick abziehen** und am PC einstecken; Windows will ihn dann nicht
prüfen, weil er ordentlich abgemeldet wurde. Steck ihn wieder ein, bevor du Power drückst. Ziehst du das Netzkabel
der Konsole, durchläuft sie beim nächsten Mal wieder den Standby beim Hochfahren. Eine **rote** Leuchte bedeutet,
dass die Konsole wirklich aus ist.

**Der Anschluss hinten.** Der Micro-USB-Anschluss auf der Rückseite ist der Stromanschluss der Konsole. Mit dem
AutoBleem-Kernel nimmt er auch ein USB-Gerät auf, aber der Stick gehört in einen vorderen Anschluss.

**Wenn der Stick fehlt.** Startet die Konsole ohne Stick oder ziehst du ihn ab, während AutoBleem läuft, bittet dich
ein Bild, ihn einzustecken - welcher USB-Anschluss, ist egal. AutoBleem wartet 5 Minuten und schickt die Konsole
dann schlafen; drück Power, wenn sie gleich schlafen soll.

![Das Bild, das um den Stick bittet](../images/en/insert-stick.jpg)

**Wenn der Stick geprüft wird.** Wurde der Stick nicht ordentlich abgemeldet - weil du ihn bei laufendem AutoBleem
abgezogen hast oder der Strom weg war -, prüft AutoBleem ihn auf Fehler, bevor er ihn wieder benutzt: beim Start,
nach dem Aufwachen oder wenn du ihn wieder einsteckst. Ein Fortschrittsbalken zeigt, wie weit die Prüfung ist. Bei
einem großen Stick kann das eine Weile dauern; lass sie durchlaufen und schalte die Konsole in der Zeit nicht aus.

![Die Prüfung des Sticks](../images/en/stick-check.jpg)

**Aktualisieren.** Um einen Stick zu aktualisieren, lässt du den Installer noch einmal darauf laufen - die
Schaltfläche heißt dann *Update*. Er installiert die neueste Version des gewählten Kanals. Deine Spiele,
Spielstände, Einstellungen und RetroArch-Inhalte bleiben, ersetzt werden nur AutoBleems eigene Dateien. Eine
Konsole mit AutoBleem-Kernel und WLAN kann sich auch selbst aktualisieren (Abschnitt 3.12).

**Umstieg von AutoBleem 1.0 (oder AutoBleem-NG).** Du nimmst denselben Installer und denselben Stick, ohne ihn zu
formatieren:

1. Kopiere zuerst den kompletten Stick als Sicherung auf deinen PC - sicher ist sicher.
2. Steck ihn ein, starte `AutoBleemInstaller.exe` und wähle Kanal und Laufwerk. Drück **nicht** auf Format.
3. Klick auf **Install**. Der Installer baut die alte Ordnerstruktur in die neue um: RetroArch, die ROMs und die
   Themes ziehen dorthin, wo AutoBleem 2 sie erwartet, und die alten ROM-Ordner (`nes`, `snes`, ...) bekommen
   die Systemnamen von RetroArch. Deine Spiele, Save States, Memory Cards, ROMs und RetroArch-Spielstände
   bleiben alle erhalten, ebenso `config.ini` - nur der PS1-Emulator darin wird auf pcsx-abnxt umgestellt.
4. Steck den Stick wieder in die Konsole. Beim ersten Scan werden die Spieleliste und die Playlists neu
   aufgebaut. Cover für deine RetroArch-Spiele holst du mit UpdateRoms auf dem PC (Kapitel 5).

> Die unveränderte Konsole hat weder Uhr noch Netzwerk. Datumsangaben siehst du erst, wenn der AutoBleem-Kernel
> installiert ist (Kapitel 6), und die Cover für RetroArch-Spiele kommen von UpdateRoms auf dem PC (Kapitel 5).

Deine PS1-Spiele kommen in den Ordner `Games` auf dem Stick, jedes in einen eigenen Ordner - wie das genau aussieht,
steht in Abschnitt 3.10.

### 2.2 Raspberry Pi

Mit AutoBleem wird ein Raspberry Pi zur kleinen Konsole: Er startet direkt in den Launcher, ohne Desktop
dazwischen. Auf der Website gibt es zwei fertige Kartenabbilder, 32-Bit und 64-Bit, und ein Paket für ein
Raspberry Pi OS Lite, das du schon installiert hast.

| Modell | 32-Bit-Abbild | 64-Bit-Abbild | Hinweise |
|---|---|---|---|
| Raspberry Pi 5 | ja | ja | |
| Raspberry Pi 4 Modell B, Pi 400 | ja | ja | |
| Raspberry Pi 3 Modell B / B+ / A+ | ja | ja | reicht gut für den Launcher und PS1 |
| Raspberry Pi Zero 2 W | ja | ja | 512 MB RAM: PS1 läuft, die anspruchsvolleren RetroArch-Cores nicht |
| Raspberry Pi 2 Modell B | ja | nur v1.2 | zu langsam für alles in 3D |
| Raspberry Pi 1, Zero, Zero W | nein | nein | ARMv6 - keines der Abbilder läuft |

**Für PS1-Spiele nimmst du das 32-Bit-Abbild.** Den schnellen ARM-Recompiler des klassischen `pcsx-ab` gibt es nur
in 32 Bit, deshalb laufen PS1-Spiele auf dem 64-Bit-System langsamer. Das 64-Bit-Abbild bringt dafür mehr
RetroArch-Cores mit - nimm es, wenn dir die anderen Systeme wichtiger sind als PS1.

**Mit dem Raspberry Pi Imager:**

1. Installiere den Raspberry Pi Imager (raspberrypi.com/software). Wähle unter *Choose OS* den Punkt *Use custom*
   und dann die heruntergeladene Datei `autobleem-<version>-rpi-armhf.img.xz` (32 Bit) oder `-arm64.img.xz`
   (64 Bit). Alternativ trägst du in den Einstellungen des Imagers eine Repository-URL ein und wählst AutoBleem
   aus der Liste. Für jeden Kanal gibt es eine eigene: `https://autobleem.retromenele.pl/rpi-imager/os_list.json`
   für das aktuelle Release, `.../os_list-testing.json` für die Version im Test und `.../os_list-nightly.json` für
   den neuesten Entwicklungsstand. Im Reiter Raspberry Pi der Download-Seite stehen die vorhandenen, jede mit einer
   Schaltfläche *Copy*.
2. Im Anpassungsdialog des Imagers (das Zahnrad oder die Frage nach *Next*) legst du **Benutzername und Passwort,
   WLAN-Netz und Land fest und schaltest SSH ein**. AutoBleem braucht beim ersten Start ein Netzwerk.
3. Schreib die Karte, steck sie in den Pi, schließ Bildschirm und Tastatur oder Controller an und schalte ihn ein.

**Der erste Start** dauert 5 bis 25 Minuten, und auf dem Bildschirm siehst du, was gerade passiert. Gibt es kein
Netzwerk, fragt er nach einem: Such dein WLAN aus der Liste aus und tipp das Passwort ein. Danach fragt er, ob
RetroArch installiert werden soll - antwortest du nicht innerhalb einer Minute, installiert er es. Dann vergrößert
er die Systempartition, macht aus dem Rest der Karte die Partition `AUTOBLEEM` für deine Spiele, installiert
RetroArch mit seinen Cores, die BIOS-Pakete und die Beispielspiele und startet in den Launcher neu.

Wenn du beim ersten Start keine Fragen beantworten willst, schreibst du die Antworten vorher in die Datei
**`autobleem.txt`** auf der Boot-Partition der Karte - die lässt sich auf jedem PC öffnen und bearbeiten:

| Schlüssel | Standard | Bedeutung |
|---|---|---|
| `root_gib` | 8 | Die Größe der Systempartition in GiB; der Rest wird zur Spielepartition. |
| `hdmi_mode` | 1920x1080@60 | Der Bildschirmmodus für den ganzen Startvorgang (`1280x720@60` für einen älteren Fernseher). |
| `retroarch` | (wird gefragt) | `yes` / `no` - RetroArch mit den anderen Systemen, oder nur PS1. |
| `thumbnails` | none | `boxarts` holt den kompletten Satz Hüllenbilder auf die Karte, damit die Cover auch offline da sind (~9000 Dateien). |
| `bios`, `downloads`, `samples` | yes | Mit `no` lässt du die BIOS-Pakete, sämtliche Downloads oder die Beispielspiele weg. |

**Auf einem vorhandenen Raspberry Pi OS Lite** (Bookworm oder Trixie): Kopiere `autobleem-rpi.tar.gz` (oder die
arm64-Variante) auf den Pi, entpacke es und führe `sudo bash install.sh` aus. Das Skript stellt dieselben Fragen,
schafft beim nächsten Start Platz für die Datenpartition, indem es die Systempartition verkleinert
(`--shrink-root <GiB>`), und legt den Launcher auf die erste Konsole.

Nach der Installation füllst du die **Partition `AUTOBLEEM`** (exFAT) auf der Karte mit deinen Spielen: Nimm die
Karte heraus und öffne sie an einem beliebigen PC, oder kopiere übers Netzwerk (SSH ist eingeschaltet).
PS1-Spiele kommen nach `Games/`, ROMs anderer Systeme nach `RetroArch/roms/<system>/`, das PS1-BIOS nach
`System/Bios/` (Abschnitt 3.11) und Themes nach `Themes/`.

### 2.3 PC-USB-Stick

Dasselbe gibt es für jeden PC, der von USB starten kann: Der Stick startet den PC direkt in AutoBleem und lässt die
Festplatte des PCs in Ruhe. Es ist ein 32-Bit-System, also laufen auch alte Rechner damit.

1. Schreib das Abbild auf einen Stick mit mindestens 8 GB. **Unter Windows** nimmst du dafür den
   **AutoBleemFlasher** (aus dem Bereich PC der Website - entpacken und `AutoBleemFlasher.exe` starten; er will
   Administratorrechte, weil er einen ganzen Datenträger beschreibt): Wähl Kanal und Stick, klick auf *Write* und
   bestätige zweimal. Er lädt das Abbild herunter, prüft es, schreibt es und liest es zur Kontrolle zurück. Er
   bietet nur USB-Sticks und SD-Karten an, nie die Platte, von der Windows läuft, und **auf dem gewählten Stick
   wird alles gelöscht**. Unter Linux oder macOS lädst du `autobleem-<version>-pcusb-i386.img.xz` aus dem Bereich
   PC herunter und schreibst es mit
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (oder mit balenaEtcher).
2. Starte den PC vom Stick (über die Taste für das Bootmenü - je nach PC F12, F8, Esc ...). BIOS- und UEFI-Start
   funktionieren beide; **Secure Boot muss ausgeschaltet sein**.
3. Der erste Start läuft ab wie beim Pi: Er fragt nach einem Netzwerk, wenn kein Kabel steckt, fragt nach
   RetroArch, installiert alles - mit Kabelnetz in etwa acht Minuten - und startet in den Launcher neu.

Danach hat der Stick eine Partition `AUTOBLEEM` für deine Spiele. Steckst du den Stick an einen laufenden PC mit
Windows 10 (Version 1903 oder neuer), erscheint sie als zweites Laufwerk, auf das du Spiele kopieren kannst.
`autobleem.txt` liegt auf der ersten Partition, mit denselben Schlüsseln wie beim Pi (bis auf `hdmi_mode` - ein PC
nimmt immer den eigenen Modus des Bildschirms).

### 2.4 Windows

Wenn du AutoBleem auf deinem Windows-Rechner haben willst, läuft es dort auch als ganz normales Programm: im
Vollbild, und die Emulatoren und RetroArch starten als eigene Programme.

1. Lade **AutoBleemSetup-<version>.exe** herunter und führe es aus. Es installiert nur für deinen Benutzer und
   braucht keine Administratorrechte: das Programm nach `%LOCALAPPDATA%\Programs\AutoBleem`, die Daten (Spiele,
   Einstellungen, Themes, RetroArch) in einen Ordner deiner Wahl - standardmäßig `Documents\AutoBleem`.
2. Hak die Bestandteile an - die Cover-Datenbanken, RetroArch (den offiziellen Windows-Build mit seinen Cores),
   die BIOS-Dateien, die Beispielspiele - und lass den Setup-Assistenten sie herunterladen.
3. Starte AutoBleem über das Startmenü oder den Desktop. Am PC dient die Tastatur als Controller (Abschnitt 3.2).

Zum Aktualisieren installierst du ein neueres Setup darüber: Das Programm wird ersetzt, dein Datenordner
bleibt, wie er ist. Außerdem schaut der Launcher einmal am Tag auf der Website nach und bietet dir ein Update an,
sobald es eines gibt (Abschnitt 3.12).

<!-- pagebreak -->

## 3. AutoBleem benutzen

### 3.1 Der Launcher

Im Launcher suchst du aus, was du spielen willst. Er zeigt deine Spiele als Regal voller Cover, so wie die
Hüllen in einem echten Regal stehen würden, und du blätterst daran entlang, bis du das gesuchte gefunden hast.
Alles andere in AutoBleem - die Einstellungen, die Memory Cards, der Store - öffnest du von hier aus, und hierher
kommst du zurück, wenn du ein Spiel verlässt.

Das gewählte Spiel steht in der Mitte des Regals, mit einer sanften Spiegelung darunter. Daneben stehen in einem
kleinen Raster seine Angaben: Publisher, Jahr, Seriennummer, Region, für wie viele Spieler es ist und wann du es
zuletzt gespielt hast. Kennt AutoBleem eine dieser Angaben nicht, lässt er die Zeile lieber weg, statt sie leer zu
zeigen. Neben den Angaben sitzt eine Play-Schaltfläche. Ein Spiel ohne Coverbild erscheint als Disc, die im
schwarzen Einsatz einer leeren Hülle liegt - so hat es trotzdem seinen Platz im Regal.

Wie der Launcher aussieht, bestimmt sein Theme. Das Standard-Theme heißt **ab2.0.0**: Eine Neuinstallation stellt
darauf um, ebenso ein Update, das es mitbringt - aber nur ein einziges Mal. Suchst du dir danach ein anderes Theme
aus (Abschnitt 3.6), bleibt es dabei.

**Die Hinweisleiste** am unteren Bildschirmrand sagt dir, was die Tasten gerade tun. Sie hat zwei Zeilen mit je
vier Plätzen. Die erste Zeile betrifft das gewählte Spiel: spielen, in RetroArch spielen, die Symbolleiste darunter
öffnen oder das Quick-Menü öffnen. Die zweite Zeile ändert sich nie: Select wählt das Set, Start sucht ein
zufälliges Spiel aus, Triangle zeigt die Tastenübersicht und L2 + R2 öffnet das Systemmenü. Hat eine Taste gerade
nichts zu tun, ist ihr Hinweis abgedunkelt.

**Neue Spiele findet er von selbst.** Bei jedem Start durchsucht der Launcher im Hintergrund deinen Spieleordner.
Ein Spiel, das du bei ausgeschaltetem Gerät hineinkopiert hast, taucht also auf, ohne dass du etwas tun musst.
Während der Scan läuft, zeigt eine Blase oben rechts, wie weit er ist, und neue Spiele erscheinen im Regal, sobald
er sie findet - du kannst dabei ganz normal weiterblättern.

**Nach einer Neuinstallation** gibt es noch keine Spiele. Statt eines leeren Regals begrüßt dich eine Karte,
*Hallo und willkommen bei AutoBleem!*, die dir sagt, dass deine Spiele in den Ordner `Games` gehören und du dann
*Spiele erneut scannen* wählen sollst. Sie nennt auch den Ort für deine Plattform: auf deinem Stick (PlayStation
Classic, PC-Stick), auf deiner SD-Karte (Raspberry Pi) oder in deinem AutoBleem-Ordner (Windows). Sobald ein Scan
das erste Spiel findet, verschwindet die Karte.

**Benachrichtigungen** sind die Blasen oben rechts. Sie halten dich auf dem Laufenden, ohne zu stören: der
Fortschritt des Scans, der Name des Sets, zu dem du gerade gewechselt hast (*Zeige: ...*), ein Controller mit
schwachem Akku, ein Hinweis nach einem Absturz, ein Scan-Prozessor bei der Arbeit und ein Download aus dem Store.
Die Blase eines Downloads zeigt Geschwindigkeit und Restzeit, etwa `1.4 MB/s · 0:42`. Wie lange die
Info-Blasen stehen bleiben, legst du selbst fest: Optionen → *Anzeigedauer der Einblendung:*.

**Akkustand der Controller.** Auf der Konsole, dem Raspberry Pi und dem PC-Stick (nicht unter Windows) erscheint
jeder kabellose Controller, der seinen Akkustand meldet, als kleines Symbol mit Prozentangabe auf einem eigenen
Schildchen; die Schildchen stapeln sich von der linken oberen Ecke nach unten. Ein Controller, der als Spieler 1
oder Spieler 2 spielt, trägt ein P1 oder P2 - je nachdem, wie die Option *Spieler 1 / Spieler 2 tauschen
(PS1-Emulatoren):* steht (Abschnitt 3.6). Ein Controller, der keinem Spieler zugeordnet ist, oder ein dritter
Controller hat keine Markierung. Wird der Akku eines Controllers schwach, sagt dir eine Benachrichtigung das
einmal, mit dem Namen des Controllers und dem Prozentwert.

**Die Kanal-Marke.** Läuft bei dir ein Build, der kein fertiges Release ist, erinnert dich eine kleine Marke unter
dem Akku-Schildchen in der linken oberen Ecke daran. Sie zeigt den Kanal und daneben die kurze Versionsnummer:
`ALPHA`, `BETA` oder `RC` für eine Vorabversion, `TESTING` für jede andere Vorabversion, `NIGHTLY` für einen
nächtlichen Build und `DEV` für einen von Hand gebauten (bei `DEV` steht als Version der Commit, aus dem er
gebaut wurde). Ein Release zeigt keine Marke.

![Die Set-Auswahl: drei Reiter und die Gruppen des aktuellen Reiters mit der Zahl ihrer Spiele](../images/en/set-picker.jpg)

### 3.2 Steuerung

AutoBleem ist dafür gemacht, nur mit dem Controller bedient zu werden, und die Tasten bedeuten überall dasselbe:
Cross bestätigt, Circle geht zurück, Triangle hilft. Weißt du einmal nicht, was eine Taste tut, schau in die
Hinweisleiste unten am Bildschirm; Triangle im Regal öffnet außerdem die Tastenübersicht mit allen Tasten aller
Bildschirme (Abschnitt 4.3). Im Regal bewirken die Tasten Folgendes:

| Taste | Im Regal |
|---|---|
| Links / Rechts | Geht zum vorigen oder nächsten Spiel; hältst du die Taste, blättert es weiter. |
| L1 / R1 | Springt zum vorigen oder nächsten Anfangsbuchstaben der Titel, damit du auch ein langes Regal schnell durchquerst. Ist das Regal leer und ein USB-Laufwerk angeschlossen, öffnet R1 *Disc* (Abschnitt 3.9a). |
| Cross | Startet das gewählte Spiel: ein PS1-Spiel im PS1-Emulator, ein RetroArch-Spiel in seinem Core, eine App nach ihrer Beschreibung. |
| Square | Startet das gewählte PS1-Spiel stattdessen in RetroArch. Ist eine Disc in einem USB-Laufwerk gewählt, kopiert es stattdessen die Disc (*Disc kopieren*, Abschnitt 3.9a). |
| Circle | Bringt dich zur Disc-Ansicht zurück, wenn eine Disc im Laufwerk liegt (Abschnitt 3.9a). |
| Triangle | Öffnet die Tastenübersicht. |
| Start | Sucht ein zufälliges Spiel aus dem aktuellen Set aus - für den Fall, dass du dich nicht entscheiden kannst. |
| Select | Öffnet die Set-Auswahl, in der du festlegst, welche Spiele das Regal zeigt (Abschnitt 3.3). |
| Hoch | Öffnet das Quick-Menü (Abschnitt 3.4). |
| Runter | Öffnet die Symbolleiste unter dem Spiel (*EINSTELLUNGEN*, *Spiel*, *MEMORY CARD*, *FORTSETZEN*); Hoch schließt sie wieder. |
| L2 + R2 | Öffnet das Systemmenü (Abschnitt 3.5). |

**Mit Tastatur.** Am PC ohne Controller oder mit einer USB-Tastatur an der Konsole, am Pi oder am PC-Stick
übernehmen Tasten die Rolle der Controller-Tasten. Die Pfeiltasten sind das Steuerkreuz, Enter ist Cross, Esc oder
Backspace ist Circle, Tab ist Triangle und die Leertaste ist Square. F1 und F2 sind Select und Start, Bild auf und
Bild ab sind L1 und R1, Pos1 und Ende sind L2 und R2, und F10 öffnet das Systemmenü. Auf einem Entwicklungsrechner
schließt Esc das Programm, und die Leertaste ist Start.

**In jeder Liste und jedem Menü** funktioniert dasselbe: Hoch und Runter bewegen den Cursor, L2 und R2 blättern
eine Seite weiter, L1 und R1 springen zur ersten oder letzten Zeile, Cross wählt aus und Circle geht zurück. Eine
Speichern-Schaltfläche suchst du vergeblich - die brauchst du nicht: Ein Bildschirm mit Einstellungen speichert
sie, wenn du ihn mit Circle verlässt.

**Raus aus einem Spiel oder einer App.** Halte Start + Select oder Home 2 Sekunden lang gedrückt, und du bist
zurück in AutoBleem. Das klappt mit jedem Controller - dem der Konsole, einem USB-Controller oder einem
Bluetooth-Controller. Drückst du dieselben Tasten nur kurz, öffnet sich stattdessen das Menü des Emulators. Eine
App hat kein solches Menü, dort wirkt nur langes Halten.

![Die Symbolleiste unter dem gewählten Spiel](../images/en/launcher-icons.jpg)

### 3.3 Die Sets

Eine große Sammlung lässt sich in Teilen leichter durchstöbern. Mit den Sets beschränkst du das Regal auf eine
bestimmte Art von Spielen - nur deine Lieblinge, nur die Super-Nintendo-Spiele, nur die Spiele aus einem Ordner -
und musst nicht an Hunderten von Covern vorbeiscrollen, bis du das richtige findest.

Drück **Select**, und die Set-Auswahl öffnet sich. Sie hat drei Reiter, PlayStation, RetroArch und Apps: L1 und R1
wechseln zwischen ihnen, Hoch und Runter gehen durch die Gruppen des Reiters (L2 und R2 seitenweise), und Cross
zeigt die gewählte Gruppe im Regal. Circle (*Zurück*) schließt die Auswahl, ohne etwas zu ändern. Die Fußzeile
nennt diese Tasten ebenfalls. In jeder Zeile steht, wie viele Einträge sie enthält. Eine leere Gruppe öffnet sich
auf einem leeren Regal, in dessen Symbolleiste es nur *EINSTELLUNGEN* gibt.

**Der Reiter PlayStation.** Auf einer PlayStation Classic beginnt er mit *Alle Spiele* und *Interne Spiele* (den
zwanzig Spielen, die in der Konsole eingebaut sind). Es folgen *USB-Spiele* - alles in `Games/` - und eine Gruppe
für jeden Ordner, den du darin angelegt hast; ein Spiel in einem Unterordner gehört also zu dessen Gruppe. Danach
kommen *Lieblingsspiele*, *Spielverlauf* und, sobald du mindestens ein Spiel als Lightgun-Spiel markiert hast,
*Lightgun-Spiele*. Raspberry Pi, PC-Stick und Windows haben keine internen Spiele; dort beginnt die Liste mit
*USB-Spiele*, und das ist deine ganze Sammlung.

**Den Reiter RetroArch** gibt es nur, wo RetroArch installiert ist. Er hat eine Gruppe für jedes System, für das du
Spiele hast, dazu die Favoriten und den Verlauf von RetroArch selbst.

**Der Reiter Apps** sortiert die Anwendungen nach Art: *Alle Apps*, dann *Spiele*, *Emulatoren*, *Werkzeuge*,
*Medien* und *Sonstige*. Zu welcher Gruppe eine App gehört, steht in ihrer Datei `app.ini`. In diesem Reiter
stehen auch die **PE-Apps** - Windows-Programme, die der PE-Runner ausführt. Eine, die die Konsole nicht starten
kann, ist mit *läuft nicht auf dieser Konsole* markiert. Wo der Launcher sie anzeigt, steht außerdem eine Zeile
*Pakete* in der Liste (Abschnitt 3.10).

### 3.4 Das Quick-Menü

Das Quick-Menü ist eine kurze Liste mit dem, was du beim Stöbern am häufigsten brauchst - so musst du dafür nicht
erst das ganze Systemmenü durchsuchen. Du öffnest es mit **Hoch** im Regal oder mit dem **Zahnrad-Symbol** in der
Symbolleiste (der Leiste mit *EINSTELLUNGEN*, *Spiel*, *MEMORY CARD* und *FORTSETZEN*).

Hoch und Runter gehen durch die Einträge (vom letzten springt der Cursor wieder zum ersten), Cross wählt einen aus,
Circle schließt das Menü. Eine Zeile unter dem Menü beschreibt den gewählten Eintrag. Diese Einträge gibt es:

- *Spiele erneut scannen* sucht sofort nach neuen, geänderten oder entfernten Spielen - praktisch, wenn du gerade
  Spiele hineinkopiert hast und nicht warten willst.
- *Store* öffnet den AutoBleem Store, in dem du Spiele, Apps und Erweiterungen findest und installierst
  (Abschnitt 3.13).
- *RetroArch-Cores* gibt es, wo RetroArch installiert ist; hier legst du fest, welcher Core welches System spielt.
- *Netzwerk & Controller* öffnet die Bildschirme für WLAN, Bluetooth-Kopplung und Controller-Belegung (Kapitel 6).
  Den Eintrag gibt es nur, wenn eine installierte Erweiterung diese Bildschirme mitbringt - PSC-Bios tut das auf
  der Konsole, dem Raspberry Pi und dem PC-Stick. Ist diese Erweiterung installiert, aber ausgeschaltet, ist der
  Eintrag ausgegraut, und seine Beschreibung sagt dir, dass du sie unter Erweiterungen einschalten sollst; Cross
  öffnet dann die Liste der Erweiterungen genau an dieser Stelle.
- *Launcher neu starten* beendet AutoBleem und startet ihn neu (nur auf der Konsole, dem Raspberry Pi und dem
  PC-Stick).
- *Systemmenü...* öffnet das vollständige Systemmenü mit allem anderen - Optionen, Spielemanager, Ausschalten und
  mehr (Abschnitt 3.5).

Bis auf den Store, die RetroArch-Cores und *Launcher neu starten* findest du alles hier auch im Systemmenü.

![Das Quick-Menü](../images/en/quick-menu.jpg)

### 3.5 Das Systemmenü

Im Systemmenü steckt alles, was AutoBleem außer Spielen noch kann: die Einstellungen, die Werkzeuge für deine
Sammlung und deine Memory Cards, Informationen über das Gerät und das Ausschalten. Drück **L2 + R2** zusammen (egal
in welcher Reihenfolge), und es legt sich über das Regal. Die Einträge sind unter den Überschriften *Bibliothek*,
*System* und *Verlassen* gruppiert; die beiden, die du am häufigsten brauchst, stehen ganz oben. Eine Zeile unten im
Menü beschreibt den gewählten Eintrag, du kannst dich also erst einmal umsehen, bevor du etwas auswählst.

| Bereich | Eintrag | Was er tut |
|---|---|---|
| (oben) | *Spiele erneut scannen* | Sucht sofort nach neuen, geänderten oder entfernten Spielen. Der Scan behält den Ordner auch von selbst im Auge; diesen Eintrag brauchst du nur, wenn du nicht warten willst. |
| | *Erweiterungen* | Listet die Erweiterungen auf dem Stick auf, etwa den AutoBleem Store, damit du sie starten oder abschalten kannst (Abschnitt 3.13). |
| *Bibliothek* | *Spielemanager* | Zeigt die PS1-Spiele als Liste mit ihren Ordnern; hier kannst du ein Spiel löschen oder die Cover entfernen (Abschnitt 4.1). Während ein Scan läuft, lässt er sich nicht öffnen. |
| | *Memory Cards* | Verwaltet deine gemeinsamen Memory-Card-Sets (Abschnitt 3.8). |
| | *Scan-Prozessoren* | Legt die Reihenfolge der Programme fest, die jeder Scan zuerst ausführt, und schaltet sie ein oder aus (Abschnitt 3.14). Während ein Scan läuft, lässt er sich nicht öffnen. |
| *System* | *Optionen* | Öffnet die Einstellungen von AutoBleem (Abschnitt 3.6). |
| | *Netzwerk & Controller* | Öffnet die Bildschirme für WLAN, Bluetooth-Kopplung, die Einrichtung des DualShock 3 und die Controller-Belegung (Kapitel 6). Den Eintrag gibt es nur, wenn eine Erweiterung diese Bildschirme mitbringt - siehe unten. |
| | *Hardwareinformationen* | Zeigt die Daten des Geräts - System, CPU, Speicher, Netzwerkschnittstellen, Zeitzone, Anzeige und die Controller mit ihrer Belegung - auf jeder Plattform auf derselben Seite (Abschnitt 4.2). Circle bringt dich zurück ins Systemmenü. |
| | *Virtuelles Gamepad* | Zeigt die Controller, die Apps bekommen, und die, die der Dienst sieht - hilfreich, wenn ein Controller in einer App nicht funktioniert (Abschnitt 4.5). Circle bringt dich zurück ins Systemmenü. |
| | *Software-Update* | Schaut sofort auf der Website nach einem neueren AutoBleem oder RetroArch, statt auf die tägliche Prüfung zu warten (Abschnitt 3.12). Weiß der Launcher schon von einem, steht in der Zeile *Update verfügbar*. Auf einer PlayStation Classic braucht das den AutoBleem-Kernel und ein WLAN. |
| | *Über* | Zeigt die Mitwirkenden und die Lizenz. |
| *Verlassen* | *RetroArch* | Verlässt den Launcher und öffnet das eigene Menü von RetroArch, mit seinen Einstellungen und Inhaltslisten; schließt du RetroArch, bist du wieder im Launcher. Den Eintrag gibt es nur, wo RetroArch installiert ist. |
| | *Ausschalten* | Schaltet das Gerät nach einer Sicherheitsabfrage aus (siehe unten). |

**Netzwerk & Controller** erscheint nur, wenn eine installierte Erweiterung den Eintrag `network` bereitstellt; das
erklärt eine Erweiterung mit `Provides=network` in ihrer `extension.ini`. PSC-Bios macht das auf der Konsole, dem
Raspberry Pi und dem PC-Stick. Ist diese Erweiterung installiert, aber ausgeschaltet, bleibt der Eintrag ausgegraut
im Menü, und seine Beschreibung sagt dir, dass du sie unter Erweiterungen einschalten sollst; Cross darauf öffnet
die Liste der Erweiterungen direkt bei dieser Erweiterung.

**Ausschalten** tut, was zum Gerät passt. Die Konsole schickt es in den AutoBleem-Standby: Der Stick wird
abgemeldet, die Leuchte wird orange, und Power holt den Launcher in wenigen Sekunden zurück (Abschnitt 2.1). Ein
Raspberry Pi oder ein PC fährt herunter.

![Das Systemmenü](../images/en/system-menu.jpg)

### 3.6 Optionen

In den Optionen machst du AutoBleem zu deinem eigenen: das Bild auf deinem Bildschirm, das Aussehen des Launchers,
die Sprache, den Ton und den PS1-Emulator, mit dem deine Spiele laufen. Du öffnest sie im Systemmenü (*Optionen*)
oder über das Symbol *EINSTELLUNGEN* unter einem Spiel. Bildschirm und Sprache stellst du meist einmal ein; wieder
hineinschauen wirst du, wenn auf einem bestimmten Fernseher etwas nicht stimmt oder du Lust auf Abwechslung hast.

Die Einstellungen sind in Gruppen sortiert, jede unter einer eigenen Überschrift. Hoch und Runter gehen von Zeile
zu Zeile, Links und Rechts ändern den Wert der aktuellen Zeile: Ein kurzer Druck geht einen Schritt weiter, Halten
läuft weiter. L1 und R1 springen zur ersten oder letzten Zeile, L2 und R2 blättern eine Seite. In einer Zeile mit
einer Auswahl an Themes, Musik oder Schriftarten sucht Start zufällig etwas aus. Eine Einstellung, die nur an oder
aus sein kann, zeigt **AN** oder **AUS**. Jede Änderung siehst du sofort, und Circle verlässt den Bildschirm und
speichert alles - bestätigen musst du nichts. Die einzige Ausnahme ist der Bildschirmmodus: Ihn probiert AutoBleem
aus, wenn du die Optionen verlässt (siehe *Anzeige:* unten).

Manche Zeilen gibt es nur dort, wo sie Sinn ergeben: die CRT-Zeilen nur bei einem 4:3-Bild, die RetroArch-Zeilen
nur, wo RetroArch installiert ist, die internen Spiele nur auf einer PlayStation Classic.

| Gruppe / Einstellung | Wofür sie da ist |
|---|---|
| *Oberfläche*: *Anzeige:* | Legt die Auflösung des Bildschirms fest, für den Launcher und den PS1-Emulator. *Auto* nimmt den eigenen Modus des Bildschirms und zeigt an, welcher das ist, zum Beispiel *Auto (1920x1080)*; du kannst aber auch jeden Modus wählen, den der Bildschirm anbietet. Die Konsole bietet 720p, 1080p und *CRT 4:3* (720x480) - den Modus für einen alten Röhrenfernseher oder ein 4:3-Aufnahmegerät. Ändere ihn, wenn das Bild nicht zu deinem Fernseher passt oder unscharf aussieht. Läuft AutoBleem auf einem Entwicklungsrechner im Fenster, fehlt diese Zeile. |
| *CRT-Rand:* | Verkleinert alles ein wenig, von 0 bis 10 % in Schritten von 1 %, weil alte Fernseher die Bildränder abschneiden. Erhöhe den Wert, bis die Hinweisleiste und die Ecken vollständig zu sehen sind. Die Zeile gibt es nur bei einer 4:3-Ausgabe; sie wirkt sofort und gilt schon für den Startbildschirm. |
| *Bildhöhe:* | Macht das Bild höher oder flacher, von -40 bis +40 in Schritten von 2, bei jeder 4:3-Ausgabe - *CRT 4:3* oder einem 4:3-Modus an einem VGA- oder PC-Ausgang. Nimm sie, wenn das Bild auf einem alten Fernseher gestaucht ist oder oben und unten über den Rand läuft. Sie wirkt sofort, und das Spielbild von RetroArch folgt ihr. |
| *Bildskalierung des Emulators:* | Bestimmt, wie der PS1-Emulator das Bild eines Spiels an deinen Bildschirm anpasst. *1x1* zeigt die Pixel der PlayStation in Originalgröße, klein und exakt; *2x (ganzzahlig)* und *4:3 (ganzzahlig)* vergrößern nur um ganze Vielfache, das gibt das schärfste Bild; *4:3* behält die ursprüngliche Form des Bildes; *Vollbild* zieht es über den ganzen Bildschirm. Diese Einstellung ersetzt den alten Widescreen-Schalter. Der klassische `pcsx-ab` und RetroArch kennen nur Vollbild und 4:3. |
| *Bildschirm-Halo:* | Steht sie auf AN, werden die leeren Streifen neben dem Spielbild (wo es den Bildschirm nicht ausfüllt) mit einem weichen Schimmer aus dem Bild selbst gefüllt statt mit Schwarz. Das funktioniert mit `pcsx-abnxt`. |
| *AutoBleem-Theme:* | Ändert das Aussehen des Launchers. Themes liegen in `Themes/`; ein Theme-Zip, das du dort ablegst, erscheint ebenfalls unter seinem Namen in der Liste. Die Themes, die AutoBleem mitbringt, werden bei jedem Update erneuert - willst du eines anpassen, kopiere es vorher unter einem neuen Namen. Standard ist **ab2.0.0**. |
| *Cover-Stil:* | Wählt den Jewel-Case-Rahmen, der um die PS1-Cover gezeichnet wird. |
| *Cover-Glanz:* | Lässt einen Lichtschimmer über das gewählte Cover wandern, jedes Mal wenn das Regal zur Ruhe kommt. |
| *Sprache:* | Stellt die Sprache des Launchers ein; es gibt 17, und der Wechsel wirkt sofort. |
| *Anzeigedauer der Einblendung:* | Legt fest, wie lange die Info-Blasen (*Zeige: ...*, die Zusammenfassung des Scans) stehen bleiben, von 0 bis 20 Sekunden; bei 0 steht dort *Aus*, und sie erscheinen gar nicht. Fehlermeldungen haben ihre eigene feste Dauer, damit dir keine entgeht. |
| *Startbildschirm:* | Zeigt das AutoBleem-Bild, während der Launcher startet; schaltest du es aus, geht es direkt zum Regal. |
| *Animationen:* | Animiert den Übergang von einem Bildschirm zum nächsten; schalte sie aus, wenn jeder Bildschirm sofort dastehen soll. |
| *Schriftarten*: *Standardschriftart verwenden:* | Steht sie auf AN, nimmt der Launcher seine eigene Schrift (Red Hat Text); schalte sie aus, um die Schrift aus der nächsten Zeile zu verwenden. |
| *Schriftart:* | Wählt eine eigene Schrift: jede `.ttf`- oder `.otf`-Datei aus `resources/fonts`, `RetroArch/fonts` oder dem Ordner des Themes. Die Zeile zeigt den Namen der Schrift, die tatsächlich benutzt wird. |
| *Ton*: *Musik:*, *Hintergrundmusik:* | *Musik:* wählt das Stück, das im Launcher läuft - das des Themes oder eine Datei aus `resources/music`. *Hintergrundmusik:* entscheidet, ob überhaupt Musik spielt. |
| *Emulation*: *PS1-Emulator:* | Wählt den Emulator, in dem deine PS1-Spiele starten: `pcsx-abnxt`, die Voreinstellung (das aktuelle PCSX-ReARMed mit den Erweiterungen von AutoBleem), oder `pcsx-ab`, den klassischen. Läuft ein Spiel nicht gut, probier den anderen. Ein Fortsetzungspunkt, den der eine gespeichert hat, lässt sich im anderen fortsetzen - es sei denn, das Spiel lief ohne BIOS-Datei. |
| *Spieler 1 / Spieler 2 tauschen (PS1-Emulatoren):* | Vertauscht in beiden PS1-Emulatoren, welcher der ersten beiden Controller Spieler 1 und welcher Spieler 2 ist - praktisch, wenn die Controller "falsch herum" eingesteckt sind. Das spielt nur mit zwei oder mehr Controllern eine Rolle; mit einem einzigen bist du immer Spieler 1. RetroArch bleibt davon unberührt. Kann der verwendete PS1-Emulator noch nicht tauschen, sagt AutoBleem dir das. |
| *Alle PSX-Spiele mit RA spielen:*, *RA-Konfiguration aktualisieren:*, *RetroArch-Konfiguration behalten:* | Diese drei gibt es nur, wo RetroArch installiert ist. Die erste startet jedes PS1-Spiel im PS1-Core von RetroArch (*PlayStation 1*; auf einem PC ist das SwanStation). Die zweite erlaubt AutoBleem, seine Einstellungen in die Konfiguration von RetroArch zu schreiben, wenn er dort ein Spiel startet. Die dritte behält eine Änderung, die du im eigenen Menü von RetroArch machst, auch nachdem RetroArch beendet ist. |
| *Bibliothek*: *Interne Spiele anzeigen:* | Zeigt die eingebauten Spiele der Konsole in den PlayStation-Listen (nur PlayStation Classic). |
| *Spielnamen bereinigen:* | Steht sie auf AN (Voreinstellung), zeigen die RetroArch-Spielelisten aufgeräumte Namen ohne Zusätze in Klammern wie (USA), (Rev 1) oder [!]; AUS zeigt die Dateinamen. Der Dateiname steht weiterhin in den Angaben zum Spiel. PS1-Spiele betrifft das nicht, ihre Titel kommen aus der Datenbank. |
| *Cover online laden:* | Erlaubt dem Scan, fehlende Cover von den Servern von libretro herunterzuladen (Raspberry Pi, PC, Windows). |
| *Updates*: *Updates:* | Legt fest, nach welchen Updates der Launcher sucht (Abschnitt 3.12): `release` (die getestete Version), `testing` (die nächste Version, die gerade getestet wird), `nightly` (der neueste Entwicklungsstand) oder `off`. Voreingestellt ist der Kanal der Version, die du installiert hast. Auf einem Entwicklungsrechner fehlt die Zeile. |
| *Diagnose*: *Protokolle auf dem Stick behalten:* | Behält ab dem nächsten Start alle Protokolle auf dem Stick, nicht nur nach einem Absturz - schalte das ein, wenn du einem Problem auf der Spur bist (Kapitel 7). |
| *Leistung anzeigen:* | Blendet unten links eine Anzeige mit Bildrate, CPU-Last, Threads und Speicher ein; im Spiel zeigt der Emulator dazu seine FPS und CPU-Last. |

**Den Bildschirmmodus wechseln.** Verlässt du die Optionen mit einem neuen Modus bei *Anzeige:*, schaltet AutoBleem
um und fragt *Diesen Anzeigemodus behalten?*. Sieht das Bild gut aus, bestätige. Bleibt dein Fernseher schwarz,
warte ab: Ohne Bestätigung kehrt AutoBleem nach einem Countdown zum vorigen Modus zurück.

**Themes auf einem 4:3-Bildschirm.** Im Modus *CRT 4:3* zeigt die Theme-Liste nur Themes, die ein 4:3-Layout
haben. Hat dein Theme keines, tritt nach der Bestätigung des Modus das Standard-Theme an seine Stelle (und ebenso
bei jedem Start in diesem Modus), und ein Hinweis teilt dir das mit: *Theme auf das Standard-Theme umgestellt
(CRT 4:3)*.

![Die Optionen, in Gruppen](../images/en/options.jpg)

![Die Gruppe Anzeige: CRT-Rand und Bildhöhe](../images/en/options-display.jpg)

![Der Hinweis nach dem Wechsel zu CRT 4:3 mit einem Theme ohne 4:3-Layout](../images/en/crt43-theme-notice.jpg)

### 3.7 Die Einstellungen eines Spiels

Jedes Spiel kann eigene Einstellungen haben. Die meisten Spiele laufen, wie sie sind, aber ab und zu braucht eines
ein wenig Hilfe - ein schärferes oder weicheres Bild, ein ausgelassenes Bild, damit es flüssig bleibt, eine andere
Memory Card -, oder du möchtest es als Favorit markieren. Im Spiel-Editor änderst du so etwas für genau dieses eine
Spiel, ohne ein anderes anzurühren.

Ist ein Spiel gewählt, öffnet **Runter** die Symbolleiste darunter. Sie hat vier Symbole: *EINSTELLUNGEN* (die
Optionen aus Abschnitt 3.6), *Spiel* (die Einstellungen dieses Spiels), *MEMORY CARD* (seine Memory Card) und
*FORTSETZEN* (seine Save States). Geh auf eines und drück Cross, um es zu öffnen.

**Der Spiel-Editor** (das Symbol *Spiel*) zeigt rechts die Angaben zum Spiel - Titel, Publisher, Jahr,
Spielerzahl, Ordner und Memory Card - und links seine Einstellungen. Hoch und Runter gehen von Einstellung zu
Einstellung, Links und Rechts ändern sie, wie in den Optionen; hältst du eine Taste, wiederholt sich die Bewegung.
Bist du fertig, speichert Circle deine Änderungen und bringt dich zurück. Hat ein Spiel keinen Titel in seinen
Daten, erscheint es unter dem Namen seines Ordners.

Die Einstellungen sind in vier Gruppen aufgeteilt:

- **Spiel** regelt, wie AutoBleem mit dem Spiel umgeht. *Favorit:* nimmt es in die Gruppe *Lieblingsspiele* der
  Set-Auswahl auf. *Infos sperren:* sagt dem Scanner, dass er Titel, Seriennummer und Disc-Liste genau so lassen
  soll, wie du sie eingestellt hast - ein späterer Scan überschreibt deine Änderungen dann nicht. *Fortsetzen:*
  bestimmt, was passiert, wenn du ein Spiel mit Fortsetzungspunkten startest: *Fragen* zeigt die Auswahl der
  Fortsetzungs-Slots, *Letzter Slot* macht sofort beim neuesten Slot weiter, und *Nie* startet das Spiel immer von
  vorn. Wo RetroArch installiert ist, gibt es zwei weitere Zeilen. *Lightgun-Spiel:* ist für Lightgun-Spiele: Das
  Spiel kommt in die Gruppe *Lightgun-Spiele* und läuft immer in RetroArch, weil dessen PS1-Core die GunCon kennt
  (schaltest du es ein, schaltet sich auch die nächste Zeile ein). *Mit RA spielen:* lässt dieses eine Spiel in
  RetroArch statt im PS1-Emulator laufen.
- **Anzeige** regelt, wie das Bild aussieht. *Auflösung:* berechnet das Spiel in 1x oder 2x (auf der eingebauten
  GPU), und *Nähte entfernen:*, das nur mit 2x funktioniert, verdeckt die feinen Linien, die bei dieser Größe
  zwischen Teilen des Bildes auftauchen können. *Dithering:* (*Aus*, *An*, *Immer*) steuert das feine Punktmuster,
  mit dem die PlayStation Farben mischt, und *Glättung:* wählt einen der Glättungs-Skalierer des Emulators.
  *Filter:* entscheidet, wie das Bild auf den Bildschirm vergrößert wird: *Nächster Nachbar* zeigt schlichte
  Pixel, *Linear* glättet sie, *Scharf* und *Scharf (einfach)* halten die Pixel knackig, ohne dass sie flimmern,
  und dann gibt es noch *Quilez*. Die CRT-Filter *CRT (fast)*, *CRT (raster)* und *CRT-Pi* ahmen einen alten
  Fernseher nach und zeichnen eigene Scanlines; solange einer von ihnen gewählt ist, sind die Scanline-Zeilen
  deshalb ausgegraut. Sonst fügt *Scanlines:* die dunklen Linien eines alten Fernsehers hinzu, und
  *Scanline-Helligkeit:* bestimmt, wie dunkel sie sind. *Auflösung*, *Nähte entfernen*, *Dithering*, *Glättung*
  und die Filter außer *Linear* und *Nächster Nachbar* gelten für `pcsx-abnxt`; der klassische `pcsx-ab` und
  RetroArch zeigen jeden anderen Filter als *Nächster Nachbar*.
- **Rendering** enthält das GPU-*Plugin:* und *Frameskip:* (*Auto*, *Aus* oder 1 bis 3 Bilder). Bilder
  auszulassen hilft einem Spiel, das zu langsam läuft, sein Tempo zu halten - dafür wirkt das Bild weniger
  flüssig.
- **Emulator** enthält *SpeedHack:*, die CPU-*Uhr:*, *SPU-Interpolation:* (wie der Ton geglättet wird),
  *Boot-Logo:* und, mit `pcsx-abnxt`, *Sony-Hacks:*. Schalte *Boot-Logo:* aus, um die BIOS-Oberfläche zu
  überspringen - das brauchst du für eine Homebrew-Disc, deren eigenes Logo sie am Starten hindert.

Die Form des Bildes und die Auflösung des Bildschirms stellst du nicht pro Spiel ein, sondern für alle gemeinsam in
den Optionen (*Bildskalierung des Emulators:* und *Anzeige:*).

**Weitere Tasten im Editor.** Triangle benennt das Spiel um, mit der Bildschirmtastatur. Square gibt dem Spiel eine
andere Memory Card (*Memory Card wechseln*). Solange das Spiel noch seine eigene Karte benutzt, macht Start aus
dieser Karte ein neues gemeinsames Set, das auch andere Spiele nutzen können (*Memory Card teilen*, Abschnitt 3.8).
Für die internen Spiele der Konsole gibt es diese beiden nicht. Hältst du Links / Rechts oder Hoch / Runter,
wiederholt sich die Bewegung - hier und ebenso in den Bildschirmen für die Spieloptionen und Cores von RetroArch.

Ein Spiel bewahrt seine Einstellungen in einer eigenen Datei `pcsx.cfg` auf. Jedes Spiel auf dem Stick hat eine,
denn der Scan legt sie an. Eine Original-Disc im USB-Laufwerk (Abschnitt 3.9a) bekommt ihren eigenen Ordner mit
einer `pcsx.cfg` erst, wenn du sie zum ersten Mal startest; bis dahin kann eine Änderung im Editor nicht
gespeichert werden, und der Editor meldet *Nicht gespeichert: Dieses Spiel hat keine pcsx.cfg*. Starte die Disc
deshalb einmal - von da an bleiben ihre Einstellungen erhalten wie bei jedem anderen Spiel. Eine Disc, die zu
einem Spiel gehört, das schon in deiner Sammlung ist, nutzt von Anfang an den Ordner und die Einstellungen dieses
Spiels.

Für eine **Disc im Laufwerk** (Abschnitt 3.9a) ergeben manche Einstellungen keinen Sinn. Der Editor graut diese
Zeilen aus, und gehst du auf eine davon, steht unten *Nicht verfügbar für eine Disc im Laufwerk*.

![Der Spiel-Editor für eine Disc im Laufwerk](../images/en/game-editor-disc.jpg)

**Im Emulator gespeicherte Einstellungen.** Du kannst ein Spiel auch während des Spielens einstellen: Das Menü des
Emulators hat dafür *Save settings for this game* (Abschnitt 3.9). Hat ein Spiel dort gespeicherte Einstellungen,
spielt es auch mit genau diesen. Der Spiel-Editor zeigt dann seine Zeilen für Anzeige, Rendering und Emulator
ausgegraut mit den gespeicherten Werten unter der Überschrift *Im Emulator gespeichert* - du kannst sie lesen, aber
nicht ändern. Willst du lieber wieder die Einstellungen des Spiel-Editors nutzen, wähl *Einstellungen entsperren*
und bestätige: Das löscht die Einstellungen, die der Emulator gespeichert hat, und die Zeilen lassen sich wieder
ändern. Beide Emulatoren, `pcsx-ab` und `pcsx-abnxt`, lesen und schreiben dieselben gespeicherten Einstellungen; es
ist also egal, welcher sie gespeichert hat.

![Der Spiel-Editor](../images/en/game-editor.jpg)

### 3.8 Memory Cards und Save States

An einer echten PlayStation teilst du dir ein oder zwei Memory Cards zwischen allen Spielen, und früher oder später
ist kein Platz mehr frei. In AutoBleem hat jedes PS1-Spiel von Haus aus seine eigene Memory Card - du musst dir
also nie Gedanken um den Platz machen oder darum, auf welcher Karte ein Spielstand liegt. Die Karte liegt zusammen
mit den Save States des Spiels in `Games/!SaveStates/<Spielordner>/`.

**Gemeinsame Memory-Card-Sets.** Manchmal müssen Spiele die Spielstände der anderen sehen - etwa eine Fortsetzung,
die den Spielstand des ersten Teils einliest, oder die Teile einer Reihe, die du auf einer Karte haben willst.
Dafür legst du ein gemeinsames Set an: eine Karte, die mehrere Spiele benutzen. Die Sets liegen in
`Games/!MemCards/`, und du verwaltest sie mit *Memory Cards* im Systemmenü. Square legt ein neues Set an (den Namen
tippst du mit der Bildschirmtastatur ein), Cross benennt das gewählte um, und Triangle löscht es nach einer
Rückfrage. Um ein Spiel auf ein Set zu legen, nimm *Memory Card wechseln* im Spiel-Editor (Abschnitt 3.7) oder das
Symbol *MEMORY CARD* des Spiels.

**Der Memory-Card-Editor** öffnet sich über das Symbol *MEMORY CARD* eines Spiels. Er zeigt die Karte des Spiels
und eine zweite Karte nebeneinander, mit Symbol und Titel jedes Spielstands - wie der Memory-Card-Bildschirm der
Original-Konsole. Square kopiert den gewählten Spielstand auf die andere Karte, Triangle löscht ihn, und Select
defragmentiert eine Karte: Es schiebt ihre freien Blöcke zusammen, damit auch ein großer Spielstand wieder
hineinpasst. Mit Start wählst du, welches Set rechts angezeigt wird, und Cross lädt beide Karten neu vom Stick.
Eine Karte, auf die das Spiel noch nichts geschrieben hat - weil du darin noch nie gespeichert hast -, ist leer, und
neben ihrem Namen steht *noch keine Karte*. Hast du etwas geändert, fragt AutoBleem *Möchtest du die
Memory-Card-Daten speichern?*, bevor er den Editor verlässt, die Karten neu lädt oder ein anderes Set anzeigt.

![Der Memory-Card-Editor](../images/en/memory-card-editor.jpg)

**Fortsetzungspunkte.** Viele PS1-Spiele lassen dich nur an bestimmten Stellen speichern, und nicht immer schaffst
du es bis zur nächsten, bevor du aufhören musst. Dafür gibt es Fortsetzungspunkte: Verlässt du ein PS1-Spiel mit
der Reset-Taste der Konsole (oder auf einem Pi oder PC über das Menü des Emulators), legt AutoBleem einen Save State
von genau der Stelle an, an der du warst. Während er ihn beim Verlassen des Spiels schreibt, zeigt der Emulator
*Please wait...*. Beim nächsten Mal machst du genau dort weiter.

Du findest sie unter dem Symbol *FORTSETZEN* des Spiels. Hat ein Spiel einen Fortsetzungspunkt, zeigt das Symbol
ein kleines Bild davon; hat es keinen, ist das Symbol ausgegraut. Die Auswahl der Fortsetzungs-Slots hat vier
Slots, dargestellt als gerahmte Karten, jede mit einem Bild des Moments, der Nummer des Slots und dem Datum. Der
neueste ist mit **NEUESTE** markiert, und ein unbenutzter Slot zeigt *Kein Fortsetzungspunkt*. Cross setzt das
Spiel ab dem gewählten Slot fort, Triangle löscht ihn. Ob die Auswahl beim Starten des Spiels überhaupt erscheint,
legt die Einstellung *Fortsetzen:* des Spiels fest (Abschnitt 3.7).

Auch PS1-Spiele, die du in RetroArch spielst, haben Fortsetzungs-Slots. Jeder Slot trägt ein Abzeichen - das Logo
von AutoBleem 2 oder das von RetroArch -, damit du siehst, welcher Emulator ihn geschrieben hat.

![Die Auswahl der Fortsetzungs-Slots](../images/en/resume-picker.jpg)

### 3.9 Spiele, RetroArch und Apps starten

Ein Spiel zu starten ist das, was du am häufigsten tun wirst, deshalb reicht dafür eine Taste: Wähl das Spiel im
Regal aus und drück **Cross**. Ein PS1-Spiel öffnet sich im Vollbild in dem PS1-Emulator, den du in den Optionen
gewählt hast (Abschnitt 3.6), und läuft, bis du es verlässt. Möchtest du ein PS1-Spiel lieber in RetroArch spielen -
weil es dort besser läuft oder weil dir die Möglichkeiten von RetroArch gefallen -, drück stattdessen **Square**.

**Ein Spiel verlassen.** Auf der PlayStation Classic tun die Tasten der Konsole, was du erwartest. **Reset** vorn
bringt dich zurück in den Launcher und legt einen Fortsetzungspunkt an der Stelle an, an der du warst, damit du
später weitermachen kannst (Abschnitt 3.8); das funktioniert sogar, während das Menü im Spiel offen ist. **Power**
schaltet die Konsole aus. Ein Raspberry Pi oder ein PC hat solche Tasten nicht; dort verlässt du das Spiel über das
Menü des Emulators, das weiter unten beschrieben ist.

Daneben gibt es einen Ausweg, der auf jedem Controller gleich funktioniert - dem der Konsole, einem USB-Controller
oder einem Bluetooth-Controller: **Halte Start + Select oder Home 2 Sekunden lang**, und du bist zurück in AutoBleem.
Drückst du dieselben Tasten nur kurz, öffnet sich stattdessen das Menü des Emulators. Der Launcher erinnert dich in
seinen Hinweisen an beides (*Select+Start oder Home 2 Sekunden halten: zurück zu AutoBleem* und *Select+Start oder
Home kurz drücken: das Menü des Emulators*). Eine App hat kein Emulator-Menü, dort wirkt nur das lange Halten. Auf
der Konsole beendet Reset außerdem immer auch eine App.

**Das Menü im Spiel.** Mit `pcsx-abnxt` hat der Emulator ein eigenes Menü für alles, was du beim Spielen brauchst:
speichern, Discs wechseln, das Bild anpassen, die Controller wählen. Drück die Menütaste - Home auf einem
Controller, der eine hat, **Select + Start** auf einem ohne, oder **Esc** auf der Tastatur -, und das Spiel hält
hinter dem Menü an, mit seinem letzten Bild im Hintergrund. Hältst du die Menütaste 2 Sekunden lang, wirkt das wie
Reset: Du verlässt das Spiel. Das Menü hat drei Reiter, zwischen denen du mit L1 und R1 wechselst. Es merkt sich,
wo du warst, und öffnet beim nächsten Mal wieder auf demselben Reiter und in derselben Zeile.

- Der Reiter **Spiel** dreht sich um das Spiel selbst. *Weiterspielen* schließt das Menü, und du spielst weiter.
  Unter *Spielstände* hält *Schnellspeichern* den aktuellen Moment fest, und *Schnellladen* holt ihn zurück.
  *Autospeicherstand laden* bringt dich zu dem Stand, den das Spiel vor höchstens 30 Sekunden hatte - der Emulator
  hält diese Kopie beim Spielen im Speicher, und sie rettet dich vor einem Fehler, den du sonst nicht rückgängig
  machen könntest. Unter *CD* ist *Disc wechseln* für ein Spiel auf mehreren Discs gedacht, wenn es nach der
  nächsten fragt, und *Spiel zurücksetzen* startet das Spiel von vorn. *Einstellungen für dieses Spiel speichern*
  merkt sich die Einstellungen, die du für dieses eine Spiel gewählt hast (Abschnitt 3.7). *PCSX-Menü* öffnet die
  eigenen Seiten von PCSX-ReARMed mit seinen Optionen, Cheats und der Info-Seite, und *Beenden* bringt dich zurück
  zu AutoBleem.
- Im Reiter **Bild** änderst du, wie das Spiel aussieht, während du zuschaust: *Anzeige*, *Auflösung* (1x oder 2x),
  *Nähte entfernen*, *Dithering*, *Skalierung*, *Bildschirm-Halo*, *Glättung*, *Filter*, *CRT-Maske*,
  *Scanlines* und *Scanline-Helligkeit*. Es sind dieselben Einstellungen wie im Spiel-Editor (Abschnitt 3.7), und
  jede Zeile hat rechts einen Hilfetext, der erklärt, was sie tut. *Anzeige* ist die Auflösung des Bildschirms;
  auf der Konsole wählst du sie in den Optionen, hier wird sie nur angezeigt. *Bildschirm-Halo* ist für die
  dunklen Streifen neben einem 4:3-Bild auf einem breiten Fernseher gedacht: Es füllt sie mit den Rändern des
  Bildes selbst, gespiegelt und abgedunkelt, sodass das Spiel in sie hinein zu leuchten scheint, statt zwischen
  zwei schwarzen Balken zu sitzen. *CRT-Maske* legt das Leuchtstoffmuster einer alten Bildröhre über das Bild -
  die *Streifenmaske* zeigt die feinen Streifen einer Trinitron, *Schlitzmaske* und *Lochmaske* die Punkte anderer
  Röhren; es gibt sie nur zusammen mit dem Filter CRT (raster). Der Filter CRT-Pi ist für die Konsole bei 1080p zu
  aufwendig. Eine Zeile, die nicht zutrifft, ist ausgegraut, und ihr Hilfetext sagt dir, warum.
- Der Reiter **Controller** legt fest, was an den beiden Anschlüssen der PlayStation steckt, *Controller 1* und
  *Controller 2*: ein normaler (digitaler) Controller, ein Analog-Controller (DualShock), eine Lightgun oder gar
  nichts. Manche Spiele funktionieren nur mit einer bestimmten Art von Controller. Die Änderung wirkt, sobald du
  ins Spiel zurückkehrst.

Das Menü ist im Look ab2.0.0 des Launchers gezeichnet, damit es sich nicht wie ein fremdes Programm anfühlt, und es
zeigt den Akkustand deiner Controller und das Bild deines letzten Quick saves.

**RetroArch-Spiele.** Ein Spiel eines anderen Systems startet in RetroArch, mit dem Core, den der Launcher für sein
System gewählt hat. Bist du fertig, bringen dich *Close Content* oder *Quit RetroArch* im Menü von RetroArch zurück
in den Launcher. Willst du ändern, welcher Core ein System spielt, öffne *RetroArch-Cores* im Quick-Menü (Abschnitt
3.4); ganz oben in der Liste steht der Core *PlayStation 1*. Und wenn du das eigene Menü von RetroArch (das XMB) mit
seinen Einstellungen und Inhaltslisten willst, wähl *RetroArch* im Systemmenü: RetroArch öffnet sich dann, ohne
etwas zu laden.

![Das Fenster mit den RetroArch-Cores, der Core PlayStation 1 ganz oben](../images/en/retroarch-cores.jpg)

**Apps.** Apps sind Programme statt Spiele: die Konsolen-Werkzeuge und, auf der Konsole, die zusätzlichen
Anwendungen aus dem RetroArch-Paket - Doom, Quake, Amiga und weitere. Du findest sie im Set Apps. Bevor eine App
startet, zeigt AutoBleem ihre Beschreibung, damit du weißt, was sie ist und wie sie gesteuert wird. Cross startet
sie, Circle bringt dich zurück ins Regal.

![Die Beschreibung einer App, bevor sie startet](../images/en/app-start.jpg)

**Die Einstellungen einer App.** Viele Apps wurden für einen ganz bestimmten Controller geschrieben, deshalb kannst
du ändern, wie sie deinen sehen. Wähl die App aus, öffne die Symbolleiste und wähl *Spiel*: Es öffnen sich die
*Spieleinstellungen* der App (*Ändern, wie dieses Programm gestartet wird*). *Controller-Modus:* legt fest, welchen
Controller die App zu haben glaubt. *Automatisch* nimmt, was die App selbst verlangt; *PSC-Controller* und
*Xbox-360-Controller* geben deinen Controller als den der Konsole oder als Xbox-360-Controller aus, und
*PSC-Controller (System)* und *Xbox-360-Controller (System)* tun dasselbe über das System selbst. Reagiert eine App
nicht so auf deinen Controller, wie sie soll, probier einen anderen Modus. *Steuerkreuz als Stick:* lässt das
Steuerkreuz den Analogstick bewegen, für eine App, die nur auf den Stick hört, und *Stick als Steuerkreuz:* macht es
umgekehrt.

Manche Apps stellen dir beim ersten Start eine Frage. Eine will wissen: *Welche Steuerung hat dein Controller?*,
damit sie ihre Steuerung einrichten kann - antworte *Ein Steuerkreuz* für einen Controller, der nur das
Steuerkreuz hat, oder *Analogsticks*. Eine App, die Windows ausführt, fragt *Was möchtest du tun?* und bietet an,
Windows zu starten, es zu installieren, DOS zu starten oder Windows zu deinstallieren. Wenn du in einer App eine
Taste festlegen kannst, bittet sie dich: *Drücke eine der Tasten.*

![Die Spieleinstellungen einer App](../images/en/app-game-settings.jpg)

Ein Windows-Programm, das der PE-Runner ausführt (eine PE-App, Abschnitt 3.3), spricht über die Bildschirme von
AutoBleem mit dir: Eine Mitteilung erscheint als *Meldung*, eine Frage mit Auswahlmöglichkeiten als *Option wählen*,
jeweils mit dem Namen der App als Titel.

![Eine Frage einer PE-App als AutoBleem-Bildschirm](../images/en/pe-dialog.jpg)

### 3.9a Eine Disc in einem USB-Laufwerk

An die Konsole, einen Raspberry Pi oder einen PC, der vom AutoBleem-Stick gestartet ist, kannst du ein ganz
normales USB-CD/DVD-Laufwerk anschließen und direkt von einer originalen PlayStation-Disc spielen, ohne etwas zu
kopieren. Eine eingelegte Disc erscheint im Launcher wie ein weiteres Spiel. Unter Windows funktioniert das nicht.

**Eine Disc auf den Stick kopieren.** Willst du das Spiel jederzeit griffbereit haben, auch ohne die Disc, drück
Square (*Disc kopieren*). AutoBleem fragt erst, ob er das Spiel kopieren soll, und sagt dir, wie viel Platz es
braucht. Dann legt er es im Ordner `Games` als einzelne CHD-Datei ab (ein Spiel auf mehreren Discs bekommt zusätzlich
eine `.m3u`-Datei, damit der Disc-Wechsel im Spiel funktioniert). Während des Kopierens siehst du Geschwindigkeit und
Restzeit, und *Abbrechen* hält den Vorgang an. Danach steht das Spiel im Regal wie jedes andere. Ein Spiel, das schon
in `Games` liegt, kopiert AutoBleem nicht noch einmal, ebenso wenig eines, für das kein Platz ist - dann sagt er dir,
wie viel Platz er braucht. Auch eine zerkratzte Disc lässt sich kopieren: Die Stellen, die nicht lesbar waren, werden
mit Nullen gefüllt, und AutoBleem sagt dir, wie viele es waren. Ob so eine Kopie läuft, ist Glückssache.

Square bietet das Kopieren in der Disc-Ansicht für jede PlayStation-Spiele-Disc an, auch für eine, die die
Cover-Datenbanken nicht kennen. Ein Spiel, das die Datenbanken kennen, wird unter seinem Titel kopiert; bei einem
Spiel auf mehreren Discs kopierst du die Discs nacheinander, und die `.m3u` führt sie in der richtigen Reihenfolge
auf, Disc 1 zuerst. Eine Disc, die die Datenbanken nicht kennen, wird nach ihrer Seriennummer benannt, als einzelne
Disc kopiert und hat im Regal kein Cover. Das Kopierfenster, *Disc wird kopiert*, bleibt auf dem Bildschirm, bis das
Kopieren fertig ist oder abgebrochen wird - der Launcher wartet so lange -, und zeigt die Geschwindigkeit als
Vielfaches eines gewöhnlichen CD-Laufwerks. Schlägt das Kopieren fehl, sagt AutoBleem dir, warum.

![Eine Disc wird kopiert](../images/en/disc-copy.jpg)

**Von der Disc spielen.** Legst du eine Disc ein, öffnet sich die **Disc-Ansicht** von selbst, sobald die Disc
gelesen ist. Sie zeigt das Cover der Disc - aus den Cover-Datenbanken oder online geholt - mit Seriennummer und
Titel, und Cross startet das Spiel. Ein PS1-Spiel, das du von der Disc spielst, bekommt für seine Fortsetzungspunkte
und Spielstände einen eigenen Ordner; du kannst also aufhören und später weitermachen wie bei einem Spiel auf dem
Stick. Nach dem Spiel, oder wenn du in den Optionen oder den Einstellungen einer Erweiterung warst, landest du wieder
in der Disc-Ansicht. Verlässt du sie mit Circle, um in deinen anderen Spielen zu stöbern, bleibt die Disc im
Laufwerk, und Circle im Regal holt die Ansicht zurück; auf einem leeren Regal öffnet auch R1 (*Disc*) sie. In einem
Regal mit Spielen springt R1 weiterhin wie gewohnt zwischen den Anfangsbuchstaben. Nimmst du die Disc heraus,
schließt sich die Disc-Ansicht.

![Die Disc-Ansicht](../images/en/disc-view.jpg)

**Der Laufwerks-Chip** oben auf dem Bildschirm zeigt dir, was das Laufwerk gerade macht, damit du weißt, ob du
warten musst. Ist kein Laufwerk angeschlossen, siehst du nichts. Ein Laufwerk ohne Disc zeigt ein blasses
Disc-Symbol. Während eine Disc gelesen wird, blinkt das Symbol und es steht *Disc wird gelesen...* daneben; ist sie
bereit, leuchtet das Symbol auf, mit dem Titel der Disc. Legst du eine Disc ein, die weder ein PlayStation-Spiel noch
eine Audio-CD ist, meldet der Chip *Das ist keine PlayStation-Disc*, und kann das Laufwerk die Disc gerade nicht
lesen, steht dort *Die Disc kann jetzt nicht gelesen werden*.

![Der Laufwerks-Chip](../images/en/disc-chip.jpg)

**Audio-CDs.** Das Laufwerk spielt auch Musik-CDs ab. Bei einer Audio-CD öffnet sich statt der Disc-Ansicht der
**CD-Player**. Er zeigt die Disc als *Audio-CD* mit ihrer Titelliste und der Gesamtspielzeit, und die Zeile darunter
nennt den gewählten Titel und sagt, ob Wiederholen und Zufallswiedergabe eingeschaltet sind. Eine Disc, die der
Player nicht abspielen kann, ist mit *Diese Disc kann nicht abgespielt werden* markiert. Das sind seine Tasten:

| Taste | Im CD-Player |
|---|---|
| Cross | Spielt den gewählten Titel ab. |
| Start | Hält die Musik an und lässt sie wieder weiterlaufen. |
| Square | Stoppt die Musik. |
| L1 / R1 | Gehen zum vorigen oder nächsten Titel. |
| L2 / R2 | Spulen im Titel zurück oder vor, jeweils fünf Sekunden. |
| Triangle | Ändert, was wiederholt wird: nichts, die ganze Disc oder der aktuelle Titel. |
| Select | Schaltet die Zufallswiedergabe ein oder aus, damit die Titel in zufälliger Reihenfolge laufen. |
| Circle | Verlässt den CD-Player. |

![Der CD-Player](../images/en/cd-player.jpg)

**LibCrypt-Discs.** Manche PlayStation-Spiele, vor allem europäische, tragen einen Kopierschutz namens LibCrypt.
Damit sie laufen, braucht der Emulator eine kleine `.sbi`-Datei mit den Daten des Schutzes. AutoBleem holt diese
Datei von selbst von der Website, bevor eine solche Disc läuft und wenn du sie kopierst, und sie wird mit dem Spiel
zusammen kopiert. Dafür braucht er ein Netzwerk: auf einem Raspberry Pi oder PC das, das er ohnehin hat, auf der
Konsole das WLAN, das du in PSC-Bios eingerichtet hast.

Für eine Disc im Laufwerk ergeben manche Spieleinstellungen keinen Sinn, deshalb graut ihr Spiel-Editor diese Zeilen
aus (Abschnitt 3.7).

### 3.10 Spiele hinzufügen

AutoBleem findet deine Spiele von selbst, solange sie am richtigen Ort liegen. In diesem Abschnitt erfährst du, wo
welche Art von Spiel hingehört, damit jeder Scan sie mit Namen und Cover ins Regal stellt.

**PS1-Spiele** kommen in den Ordner `Games`, **jedes Spiel in einen eigenen Ordner**, der nach dem Spiel benannt
ist. Du kannst Spiele auch in eigenen Ordnern zusammenfassen; jeder solche Ordner wird dann zu einer Gruppe in der
Set-Auswahl (Abschnitt 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                ein Ordner mit Spielen: eine eigene Gruppe in der Set-Auswahl
    Klonoa/                   Klonoa.pbp
```

AutoBleem liest die üblichen Disc-Abbilder: `.cue` mit seiner `.bin` (oder `.img`), `.pbp`, `.chd` (auch mit zstd
komprimierte), `.iso` und `.ecm`, das der Scan für dich entpackt. Auch ein gezipptes Spiel funktioniert: Der
Prozessor **Unzip** entpackt es, bevor der Scan es liest (Abschnitt 3.14).

Ordentlich musst du dabei nicht sein. Ein Spiel auf mehreren Discs gehört mit allen Discs in einen Ordner - kopierst
du aber Ordner namens `Game (Disc 1)`, `Game (Disc 2)` und so weiter hinein, fasst der Scan sie zu einem Ordner
`Game` zusammen. Spiele, die du als lose Dateien direkt in `Games/` wirfst, sortiert der Scan ebenfalls in eigene
Ordner.

**Namen und Cover** kommen von allein. Der Scan liest die Seriennummer jeder Disc und holt sich Titel, Publisher,
Jahr, Spielerzahl und Region aus der PlayStation-Datenbank von RetroArch oder aus den Cover-Datenbanken. Willst du
ein eigenes Cover, leg ein PNG oder JPEG mit demselben Namen neben das Abbild des Spiels. Ohne eigenes Cover kommt
das Hüllenbild aus den Cover-Datenbanken oder, wenn RetroArch installiert ist, aus dem Thumbnail-Satz von libretro;
auf einem Raspberry Pi, einem PC oder unter Windows wird ein fehlendes Cover online geholt (Optionen → *Cover online
laden:*). Liegt der Scan einmal daneben, korrigiere es im Spiel-Editor und schalte *Infos sperren:* ein, damit der
nächste Scan deine Änderung behält.

**Spiele anderer Systeme** kommen nach `RetroArch/roms/`, **ein Ordner pro System, benannt wie in den Datenbanken von
RetroArch** - zum Beispiel `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo Entertainment
System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` oder `FBNeo - Arcade Games` (oder `Arcade`).
Die Ordner werden für dich angelegt, und die ROMs dürfen gezippt bleiben. Auf einem Raspberry Pi, einem PC oder unter
Windows liest der Scan sie von selbst ein und schreibt die Playlists von RetroArch. Ein Konsolen-Stick kann das nicht
allein; dafür lässt du **UpdateRoms** auf dem PC laufen (Kapitel 5).

**Apps** kommen nach `Apps/<name>/`, jede mit einer `app.ini` - Name, Symbol und was gestartet werden soll - und
einer `run.sh`.

**Pakete.** Manche Apps sind Spiel-Engines: Sie brauchen die Daten eines Spiels, das du besitzt, bevor sie es
spielen können. Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital,
DOS-Spiele und weitere funktionieren so. Leg die Dateien des Spiels in einen Ordner `Packages` auf dem Stick, einen
Ordner pro Spiel - zum Beispiel `Packages/Doom/DOOM2.WAD` -, und AutoBleem erkennt sie anhand einer mitgelieferten
Tabelle (`rc/packages.ini`). In einem Ordner, den er erkennt, gelten lose Spieldateien als eigene Pakete. AutoBleem
liest deine Dateien nur und verändert sie nie. Ein Paket kann auch aus dem Store kommen (Abschnitt 3.13).

Wo der Launcher sie anzeigt, listet die Zeile *Pakete* im Reiter Apps (Abschnitt 3.3) die gefundenen Spieldaten auf.
Cross auf einem Eintrag öffnet seine **Package info**: was die Daten enthalten, eine Beschreibung, wo die Dateien
liegen und woher sie stammen (deine eigenen Dateien, der Store, ein Mod oder Dateien, die einer App beiliegen), ob es
sich um Shareware oder freie Daten handelt und welche installierte App sie ausführt. Kann nichts von dem, was du
installiert hast, sie ausführen, sagt die Info dir das.

Startest du eine Engine-App, sucht AutoBleem nach Spieldaten, die sie ausführen kann. Gibt es genau einen Satz
Daten, startet das Spiel sofort. Gibt es mehrere, fragt eine Liste (*Spieldaten wählen*), welchen du spielen willst,
und steht dabei auf dem, den du zuletzt gewählt hast. Gibt es keine, sagt AutoBleem dir, welche Daten die App
braucht und wohin sie gehören, und es startet nichts.

**Eigene Spiele.** Erkennt AutoBleem Daten nicht, steht in ihrer Package info *Nicht erkannt. Falls es ein Spiel
ist, siehe Handbuch: Eigene Spiele.* Die Tabelle kennt nur die Spiele, für die sie gemacht wurde. Für ein anderes
schreibst du selbst eine Zeile in eine eigene `packages.ini` im Ordner `Packages`: AutoBleem liest deine zuerst, deine
Zeilen haben also Vorrang.

![Die Paket-Auswahl, in der du die Spieldaten zum Starten wählst](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Nur einen Teil scannen.** Hast du nur zu einem Set oder einem Ordner Spiele hinzugefügt, kann *Spiele erneut
scannen* auch nur diesen Teil durchsuchen. Das geht schneller als alles zu scannen, und seine Blase verschwindet,
sobald er fertig ist.

**Themes** kommen nach `Themes/<name>/`, mit ihrer `theme.json` und ihren Bildern - oder du legst das Zip des Themes
so, wie es ist, in `Themes/`.

### 3.11 Das PS1-BIOS

Das BIOS ist das Startprogramm der PlayStation selbst, und am originalgetreuesten spielt der Emulator die Spiele mit
dem echten. Auf einer **PlayStation Classic** musst du nichts tun: Der Emulator nimmt das BIOS der Konsole. Auf einem
**Raspberry Pi, einem PC und unter Windows** legst du deine eigenen PS1-BIOS-Dateien nach `System/Bios/`: `romw.bin`
(die US-/europäische SCPH-5501/5502) und `romJP.bin` (die japanische SCPH-5500, für japanische Spiele). Die
Installationsprogramme füllen sie aus den BIOS-Paketen von RetroArch auf, es sei denn, deine eigenen Dateien liegen
schon dort - die ersetzen sie nie. Fehlen sie, läuft der Emulator mit seinem eingebauten HLE-BIOS, einem Ersatz, den
viele Spiele akzeptieren und manche nicht. Startet ein Spiel nicht, solltest du also zuerst nachsehen, ob das BIOS
fehlt.

### 3.12 Updates

AutoBleem hält sich selbst auf dem neuesten Stand, damit du neue Funktionen und Fehlerbehebungen bekommst, ohne
etwas neu zu installieren. Beim Start des Launchers und danach einmal am Tag schaut er auf der Website nach einer
neuen Version auf seinem **Kanal**. Den Kanal wählst du in den Optionen → *Updates:*: `release`, `testing`, `nightly`
oder `off`, wenn er gar nicht nachsehen soll. Willst du nicht auf die tägliche Prüfung warten, schaut
*Software-Update* im Systemmenü sofort nach.

Gibt es eine neue Version, fragt AutoBleem dich, was er tun soll. *Jetzt aktualisieren* lädt sie herunter und
installiert sie, das dauert ein paar Minuten. *Morgen erinnern* fragt in einem Tag wieder, und *Diese Version
überspringen* fragt bei dieser Version nicht mehr nach. Was du auch wählst: Deine Spiele, Spielstände und
Einstellungen bleiben immer erhalten, und nach einem Update scannt der Launcher deine Spiele noch einmal. Welchen
Build du hast, zeigt die Kanal-Marke in der linken oberen Ecke (Abschnitt 3.1).

Wie das Update installiert wird, hängt vom Gerät ab:

- Auf einem **Raspberry Pi** und dem **PC-Stick** läuft nach dem Download der Installer erneut, mit demselben
  Fortschrittsbildschirm wie beim ersten Start, und bietet auch ein neueres RetroArch an. Danach ist der Launcher
  wieder da.
- Unter **Windows** öffnet sich das heruntergeladene Setup, installiert die neue Version und startet den neuen
  Launcher.
- Auf einer **PlayStation Classic** kann sich nur eine Konsole mit **AutoBleem-Kernel** (ABFlashKit, Abschnitt 6.2)
  und einem in PSC-Bios eingerichteten **WLAN** (Abschnitt 6.1) selbst aktualisieren - eine unveränderte Konsole hat
  kein Netzwerk, also schaut der Launcher dort gar nicht erst nach. Nach *Jetzt aktualisieren* schließt sich der
  Launcher, und das AutoBleem-Bild bleibt auf dem Bildschirm, während der Stick aktualisiert wird; das dauert ein
  paar Minuten, dann startet der neue Launcher. Ohne Netzwerk meldet *Software-Update* *Nicht verbunden*. Jeden
  Konsolen-Stick kannst du außerdem am PC mit `AutoBleemInstaller.exe` aktualisieren (Abschnitt 2.1).

### 3.13 Erweiterungen und der AutoBleem Store

**Erweiterungen** bringen Neues in den Launcher - eigene Bildschirme und Funktionen -, ohne AutoBleem selbst zu
verändern. Der AutoBleem Store und PSC-Bios sind Erweiterungen. Eine Erweiterung liegt in `Extensions/<name>/` auf
dem Stick (auf einem Raspberry Pi auf dessen Datenpartition, unter Windows im Datenordner); um eine zu installieren,
entpackst du ihr Zip dorthin.

Um sie zu sehen, öffne das Systemmenü (**L2 + R2**) und wähl *Erweiterungen*. Die vom AutoBleem-Team stehen oben,
alle anderen folgen unter *Erweiterungen von Drittanbietern*. Cross startet die gewählte, Triangle schaltet sie aus
oder wieder ein. PSC-Bios auf der Konsole ist die Ausnahme: Damit richtest du WLAN, Controller und Uhr ein, deshalb
lässt es sich dort nicht abschalten. Kann eine Erweiterung nicht laufen, sagt ihre Zeile dir den Grund - sie braucht
ein Netzwerk und es gibt keines, sie ist nicht für dieses System gemacht, sie wurde für eine andere Version von
AutoBleem gebaut und braucht ein Update, oder sie ließ sich nicht laden. Bringt eine Erweiterung den Launcher einmal
zum Absturz, schaltet AutoBleem sie ab, und die Liste sagt es dir; hier kannst du sie wieder einschalten.

![Die Liste der Erweiterungen](../images/en/extensions.jpg)

**Der AutoBleem Store** ist die erste Erweiterung: ein Ort, an dem du Apps und Spiele durchstöberst und mit einem
Tastendruck installierst, auf jedem System, auf dem AutoBleem läuft. Eine PlayStation Classic braucht dafür den
AutoBleem-Kernel, denn das WLAN kommt mit dem Kernel. Du öffnest ihn über das Quick-Menü (*Store*, Abschnitt 3.4). Er
hat vier Reiter, zwischen denen du mit L1 und R1 wechselst.

Die Reiter **Apps** und **Games** listen auf, was die Quellen anbieten, jeden Eintrag mit Bild, Version, Größe und dem
kleinen Symbol der Quelle, aus der er stammt. Der Reiter Apps listet auch PE-Apps mit ihrer Lizenz und Quelle sowie
Spieldaten-Pakete (Abschnitt 3.10). Was du schon installiert hast, trägt ein Abzeichen *Installed*. Die Hinweisleiste
zeigt die Tasten, die für die gewählte Zeile gelten:

| Taste | In den Reitern Apps und Games |
|---|---|
| Cross | Installiert den Eintrag - oder aktualisiert ihn, versucht es nach einem Fehler erneut oder bricht einen wartenden oder laufenden Download ab. |
| Triangle | Entfernt etwas, das der Store installiert hat. |
| Square | Lädt die Listen der Quellen neu. |
| L2 / R2 | Springen zum vorigen oder nächsten Anfangsbuchstaben. |
| Select | Zeigt jeweils nur eine Quelle, wenn du sehen willst, was eine einzelne Quelle anbietet. |
| Start | Durchsucht die Titel. |

Die Bilder werden behalten, sobald sie einmal geladen sind, damit die Listen beim nächsten Mal schnell da sind, und
ein Bild, das nicht geladen werden konnte, lässt sich erneut versuchen.

Der Reiter **Downloads** zeigt, was gerade heruntergeladen wird, wartet, fehlgeschlagen oder installiert ist, mit
einem Fortschrittsbalken, der gleichmäßig vorrückt. Zuschauen musst du nicht: Downloads laufen im Hintergrund weiter,
auch wenn du den Store verlässt, und während du anderswo im Launcher bist, zeigt eine Blase den laufenden Download
mit Geschwindigkeit und Restzeit (zum Beispiel `1.4 MB/s · 0:42`). Ein Spiel zu starten oder auszuschalten hält sie
nur an, und ein unterbrochener Download macht dort weiter, wo er aufgehört hat. Bricht das Netzwerk weg, steht beim
Eintrag *Waiting for the network*, und er macht dort weiter, wo er war, sobald das Netzwerk wieder da ist; nach 30
Minuten ohne Netzwerk gibt er auf. Downloads über 2 GB funktionieren auf jeder Plattform, auch auf den 32-Bit-Builds.
Ein Spiel, das du installierst, erscheint nach dem nächsten Scan im Regal, mit dem Bild aus dem Store als Cover.

Der Reiter **Sources** zeigt, woher die Listen kommen, jede mit ihrem Symbol: der eigene Katalog von AutoBleem, jede
TSV-Liste, die in `System/Extensions/store/sources/` liegt, und die Adressen, die du selbst mit *Add a source URL*
hinzufügst. Cross auf einer selbst hinzugefügten Quelle lässt dich sie umbenennen, ihre Adresse ändern, sie zwischen
`http://` und `https://` umschalten oder sie entfernen.

![Der Reiter Apps des Stores](../images/en/store-apps.jpg)

![Das Menü einer selbst hinzugefügten Quelle](../images/en/store-source-menu.jpg)

Was der eigene Katalog von AutoBleem anbietet, steht auch auf der Download-Seite unter
`https://autobleem.retromenele.pl/store/`. Mit einer Quelle, die du selbst hinzufügst, ist das etwas anderes: **Für
den Inhalt der Quellen, die du hinzufügst, bist du selbst verantwortlich.**

**Deine eigenen Spiele in deinem Netzwerk.** Liegen deine PS1-Spiele zu Hause auf einem anderen Rechner, kann
`abstored`, der LAN-Server des Stores, sie dem Store über dein Netzwerk anbieten - du installierst sie dann wie jeden
anderen Eintrag. Er läuft auf jedem Linux-Rechner - einem Raspberry Pi, einem Heimserver - und liest den Ordner nur,
ohne ihn je zu verändern. Starte ihn mit `abstored <Spieleordner>` und öffne dann `http://<dieser Rechner>:8124/` im
Browser: Die Seite zeigt, was er anbietet und welche Probleme er gefunden hat. Im Store fügst du
`http://<dieser Rechner>:8124/store.tsv` als Quelle hinzu. Fertige Programme für Linux und Windows gibt es auf der
Seite des Stores im Reiter **LAN server**, und `INSTALL-linux.md` (`ext_store/server/` im Quellcode) erklärt, wie du
ihn als Dienst einrichtest. **LAN Share** (Abschnitt 5.2) bringt Spiele und Discs von einem PC auf so einen Server.

### 3.14 Scan-Prozessoren

Scan-Prozessoren bereiten deine Spiele vor, bevor AutoBleem sie liest. Ein Prozessor ist ein kleines Programm, das
jeder Scan zuerst ausführt. Er kann ein Format, das AutoBleem nicht liest, in eines umwandeln, das er liest - etwa ein
gezipptes Spiel entpacken -, oder die Daten eines Spiels ändern, zum Beispiel einen Übersetzungs-Patch einspielen.
Prozessoren liegen in `System/Processors/<name>/` auf dem Stick (auf einem Raspberry Pi auf dessen Datenpartition,
unter Windows im Datenordner); um einen zu installieren, entpackst du seinen Ordner dorthin, und der nächste Scan
führt ihn aus.

**Unzip ist bei AutoBleem dabei.** Es entpackt gezippte PS1-Spiele in `Games/`, bevor der Scan sie liest, und
gezippte ROMs eines nach dem anderen; Arcade-Sets bleiben gezippt, weil die Arcade-Cores sie so lesen. Ein Update von
AutoBleem aktualisiert auch Unzip, und hast du es ausgeschaltet, bleibt es aus.

Ein Prozessor erledigt seine Arbeit einmal: Hat er ein Spiel bearbeitet, läuft er darauf erst wieder, wenn sich das
Spiel ändert. Während ein Prozessor arbeitet, zeigt die Blase oben rechts, was er gerade tut, und eine Warnung oder
ein Fehler erscheint in der Zeile darunter; die Einzelheiten stehen in `processors.log` im Protokollordner. Startest
du ein Spiel oder RetroArch, hält das einen Prozessor an, der Dateien verändert, damit das Spiel das Gerät für sich
hat; der nächste Scan beendet die Arbeit.

Zum Verwalten öffnest du das Systemmenü (**L2 + R2**) und wählst *Scan-Prozessoren*. Du siehst sie in der
Reihenfolge, in der sie laufen, mit einem Reiter für die PS1-Spiele und einem für die ROMs; L1 und R1 wechseln
zwischen den Reitern. Die Reihenfolge ist wichtig: Ein Prozessor, der entpackt, muss vor einem kommen, der das
Entpackte patcht.

| Taste | In den Scan-Prozessoren |
|---|---|
| Square | Nimmt den gewählten Prozessor auf, sodass Hoch und Runter ihn an seinen neuen Platz schieben; Square setzt ihn wieder ab. |
| Cross | Schaltet den Prozessor aus oder wieder ein. |
| Triangle | Lässt den Prozessor beim nächsten Scan jedes Spiel noch einmal ansehen, auch die, die er schon bearbeitet hat. |
| Circle | Geht zurück und startet einen Scan, wenn du etwas geändert hast. |

Ein Prozessor, der für ein anderes Gerät gebaut wurde, bleibt ausgegraut in der Liste - du siehst, dass er da ist,
aber auch, dass er hier nicht läuft.

![Die Scan-Prozessoren](../images/en/processors.jpg)

Willst du einen eigenen Prozessor schreiben, erklärt die Seite von Unzip, `https://github.com/autobleem2/proc_unzip`,
alles, was ein Prozessor können muss, und `tools/proc_check.py` im Quellcode von AutoBleem prüft deinen, bevor du ihn
weitergibst.

<!-- pagebreak -->

## 4. Bildschirme

### 4.1 Spielemanager

Im Spielemanager räumst du deine PS1-Sammlung auf. Du brauchst ihn, wenn du ein Spiel loswerden willst, das du nicht
mehr spielst, wenn du die Einstellungen eines Spiels öffnen willst, ohne es erst im Regal zu suchen, oder wenn
AutoBleem alle Cover neu holen soll. Du öffnest ihn über das Systemmenü (L2 + R2, *Spielemanager*). Läuft gerade ein
Scan, ist er ausgegraut und wartet, bis der Scan fertig ist.

Der Bildschirm heißt *Spielemanager - Spiel auswählen*. Links stehen alle deine PS1-Spiele als alphabetische Liste
von Titeln, rechts das Cover des gewählten Spiels mit Publisher, Jahr, Seriennummer und dem Ordner, in dem es liegt.
Oben rechts siehst du, wie viel Platz auf dem Laufwerk noch frei ist - so erkennst du, wie viel Platz dir ein
Löschen zurückgibt. Hoch und Runter gehen durch die Liste, L2 / R2 blättern eine Seite, und L1 / R1 springen zum
ersten oder letzten Spiel.

- **Cross** öffnet das gewählte Spiel im Spiel-Editor - demselben Editor wie das Symbol *Spiel* im Regal
  (Abschnitt 3.7). Verlässt du ihn, stehst du wieder auf demselben Spiel in der Liste.
- **Square löscht das Spiel.** AutoBleem fragt vorher nach und entfernt dann den ganzen Ordner des Spiels. Werden
  seine Save States und seine Memory Card von keinem anderen Spiel benutzt, stellt er eine zweite Frage: ob sie
  ebenfalls gelöscht werden sollen. Sag Nein, wenn du das Spiel vielleicht später mit deinen Spielständen
  zurückhaben willst.
- **Triangle löscht alle Coverbilder** (PNG oder JPEG), die neben deinen Spielen liegen, nach einer Rückfrage. Das
  ist nützlich, wenn sich Cover angesammelt haben, die dir nicht gefallen: Der nächste Scan holt die Cover wieder
  aus den Cover-Datenbanken.

Am Ende der Liste, nach den Spielen, siehst du vielleicht Ordner mit der Markierung *Nicht hinzugefügt*. Das sind
Ordner in `Games`, die sich der Scan angesehen hat, aus denen er aber kein Spiel machen konnte. Wählst du einen aus,
zeigt die rechte Seite, wo er liegt und warum er nicht hinzugefügt wurde - zum Beispiel, weil eine cue-Datei fehlt
(Kapitel 7). Square löscht so einen Ordner nach einer Rückfrage. Verlässt du den Spielemanager mit Circle, nachdem du
etwas geändert hast, scannt AutoBleem die Spiele neu.

![Der Spielemanager: links die Liste der Spiele, rechts Cover und Angaben des gewählten Spiels](../images/en/game-manager.jpg)

### 4.2 Hardwareinformationen

Die Hardwareinformationen sind die Seite, auf der du nachschaust, was dein Gerät ist und was es sieht: wie viel Platz
noch auf dem Stick ist, welche Netzwerkadresse es hat, welche Grafik- und Audiotreiber es benutzt und welche
Controller angeschlossen sind. Die Seite ist auf jeder Plattform gleich, die Konsole eingeschlossen. Du öffnest sie
über das Systemmenü (L2 + R2, *Hardwareinformationen*); Circle bringt dich zurück ins Systemmenü.

Die Seite zeigt das System, die Hardware, den Speicher mit seinem freien Platz, die Netzwerkadressen, die Grafik- und
Audiotreiber und die angeschlossenen Controller. Sie liest alles jede Sekunde neu ein; du kannst sie also offen
lassen, während du einen Controller einsteckst oder ein Kabel anschließt, und zusehen, wie die Änderung erscheint.
Sie zeigt nur an - um das Netzwerk oder einen Controller einzurichten, nimmst du *Netzwerk & Controller* (PSC-Bios,
Kapitel 6).

Der Teil über die Controller beantwortet die Frage: "Welcher Controller ist welcher Spieler?" Die ersten beiden
Controller erscheinen als *Spieler 1* und *Spieler 2* - die Anschlüsse, die der PS1-Emulator ihnen gibt. Jeder weitere
Controller erscheint mit *wird vom PS1-Emulator nicht verwendet*. RetroArch verteilt die Anschlüsse nach seinen
eigenen Einstellungen, in einem RetroArch-Spiel kann die Reihenfolge also anders sein. Du musst diese Seite nicht
jedes Mal öffnen: Immer wenn ein Controller eingesteckt oder abgezogen wird, zeigt der Launcher kurz an, welcher
Controller jetzt Spieler 1 und welcher Spieler 2 ist.

![Hardwareinformationen: die Daten des Geräts und die angeschlossenen Controller](../images/en/hardware-info.jpg)

### 4.3 Die Tastenübersicht

Weißt du irgendwo nicht mehr, was eine Taste tut, drück im Regal **Triangle**. Die Tastenübersicht zeigt alle Tasten
aller Bildschirme auf einer Seite, sodass du nachschlagen kannst, ohne den Launcher zu verlassen. Ist eine
USB-Tastatur angeschlossen oder wurde eine benutzt, zeigt eine Spalte *Tastatur* neben jeder Controller-Taste die
passende Taste.

Die Übersicht erinnert dich auch an das eine, das du dir für jedes Spiel merken solltest: wie du wieder herauskommst.
Halte Select + Start oder Home 2 Sekunden lang, um zu AutoBleem zurückzukehren; ein kurzer Druck öffnet stattdessen
das Menü des Emulators.

![Die Tastenübersicht: die Tasten jedes Bildschirms, daneben die Tastaturtasten](../images/en/button-guide.jpg)

### 4.4 Die Bildschirmtastatur

Immer wenn AutoBleem eine Eingabe von dir braucht - den Namen eines Memory-Card-Sets, den Titel eines Spiels, ein
WLAN-Passwort, die Adresse einer Store-Quelle -, erscheint dieselbe Bildschirmtastatur, damit du nur mit dem
Controller tippen kannst. Sie ist aufgebaut wie die Tastatur eines Handys. Neben den Buchstaben hat sie eine Seite mit
Sonderzeichen, mit `/ \ : ? & = % @ #` und allem anderen, was eine Adresse oder ein Passwort braucht, und zwei Seiten
mit Buchstaben mit Akzenten und Umlauten. In der untersten Reihe liegen Shift, die Taste zum Seitenwechsel, Leertaste,
Rücktaste und Bestätigen.

Mit den Richtungstasten bewegst du dich über die Tasten, und **Cross** tippt die Taste unter dem Cursor. **Triangle**
löscht ein Zeichen, **Square** setzt ein Leerzeichen. **L1** ist Shift; zweimal gedrückt, rastet die
Großschreibung ein. **R1** geht zur nächsten Tastenseite, und **L2 / R2** bewegen den Cursor im Text. **Start**
bestätigt die Eingabe, **Circle** bricht ab. Ist eine USB-Tastatur angeschlossen, kannst du jederzeit stattdessen
darauf tippen: Enter bestätigt, Esc bricht ab.

![Die Bildschirmtastatur](../images/en/keyboard.jpg)

### 4.5 Virtuelles Gamepad

Apps - die Programme im Set Apps, etwa Doom oder Quake - lesen deinen Controller nicht selbst. Ein kleines
Hilfsprogramm, der Dienst für das virtuelle Gamepad, liest die echten Controller und reicht jeder App einen
Controller weiter, den sie versteht. Diese Seite zeigt dir, welche Controller dieser Dienst sieht und wie er sie
liest. Schau hier nach, wenn eine App nicht auf deinen Controller reagiert oder ihre Tasten vertauscht sind. Du
öffnest die Seite über das Systemmenü (L2 + R2, *Virtuelles Gamepad*); Circle bringt dich zurück ins Systemmenü.

Unter *Gamepads, die der Dienst sieht* steht jeder Controller mit einer Nummer und seinem Namen. Daneben liest du drei
Dinge: ob der Dienst den Controller öffnen konnte (*verbunden*) oder nicht (*nicht lesbar*); über welchen Treiber der
Controller kam; und woher seine Tastenbelegung stammt - *aus der Controller-Datenbank* heißt, dass der Controller
bekannt ist und seine Tasten da liegen, wo sie hingehören; *vom Dienst geraten* heißt, dass er nicht bekannt ist und
der Dienst so gut wie möglich geraten hat. Fühlen sich die Tasten in einer App falsch an, ist eine geratene Belegung
der wahrscheinliche Grund.

Der Dienst läuft nur, solange eine App läuft; deshalb fragt die Seite ihn einmal beim Öffnen ab. Steckst du einen
Controller ein, während die Seite offen ist, drück **Cross** (*Neu suchen*), um noch einmal zu fragen. Unter Windows
gibt es diesen Dienst nicht, und die Seite meldet *Nicht in diesem Build*.

![Virtuelles Gamepad: die Controller, die der Dienst der Apps sieht](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. Am PC

### 5.1 UpdateRoms - einen Konsolen-Stick auffrischen

Auf einem Raspberry Pi, einem PC oder unter Windows sortiert der Scan des Launchers deine RetroArch-Spiele von
selbst in Listen und holt ihre Cover. Die PlayStation Classic kann das nicht, weil sie kein eigenes Netzwerk hat.
**UpdateRoms** erledigt diese Arbeit stattdessen auf deinem Windows-PC: Es nutzt das Netzwerk des PCs, schreibt aber
alles mit den Pfaden, die die Konsole erwartet - steckst du den Stick zurück, startet die Konsole und findet alles an
seinem Platz. Lass es laufen, wann immer du auf einem Konsolen-Stick RetroArch-Spiele hinzugefügt oder entfernt hast.

1. Kopiere deine ROMs auf den Stick nach `RetroArch/roms/<system>/` (Abschnitt 3.10). Die Ordnernamen müssen die
   Datenbanknamen von RetroArch sein; die gängigen hat der Installer schon angelegt.
2. Starte **`UpdateRoms\UpdateRoms.exe` vom Stick** - der Installer hat es dort hingelegt. Auf welchem Stick es
   liegt, findet es selbst heraus. Während es arbeitet, siehst du eine Zeile, die sagt, was es gerade tut, einen
   Fortschrittsbalken und ein Protokoll.
   - Hat der Stick noch keine RetroArch-Datenbank, lädt es zuerst das Datenbankpaket von RetroArch herunter. Damit
     erkennt es dann jedes ROM, sodass ein Spiel, das die Datenbank kennt, seinen richtigen Namen bekommt.
   - Es schreibt pro System eine Playlist nach `RetroArch/bin/playlists/`, mit den Pfaden der Konsole. Was RetroArch
     selbst in diese Listen eingetragen hat, bleibt erhalten.
   - Für jedes ROM ohne Cover holt es ein Bild von den Thumbnail-Servern von libretro nach
     `RetroArch/bin/thumbnails/`.
3. Wirf den Stick sicher aus und steck ihn wieder in die Konsole. Der Reiter RetroArch der Set-Auswahl listet jetzt
   jedes System auf, für das es Spiele gibt.

Du kannst es so oft laufen lassen, wie du willst: Ein Ordner, in dem sich nichts geändert hat, wird übersprungen,
ein zweiter Durchlauf geht also schnell. Geht etwas schief, steht das Protokoll in `System/Logs/updateroms.log` auf
dem Stick. Auch die Karte eines Raspberry Pi in einem Kartenleser lässt sich so auffrischen, mit
`UpdateRoms.exe <drive> --target rpi` - wobei ein Pi das von selbst erledigt, wenn er ein Netzwerk hat.

### 5.2 LAN Share - deine Spiele und Discs auf dem Server in deinem Netzwerk

Der Store kann Spiele von einem Server in deinem eigenen Heimnetz installieren (Abschnitt 3.13). **LAN Share** ist
das Windows-Programm, mit dem du diesen Server von deinem PC aus füllst: Es bringt die PS1-Spiele, die du auf dem PC
hast, auf den Server, und es kann eine PS1-Disc im CD/DVD-Laufwerk des PCs einlesen und ebenfalls dort ablegen. Der
Server ist ein `abstored`, das auf einem Raspberry Pi, einem NAS oder einem anderen PC läuft. Liegt ein Spiel erst
einmal darauf, kann der Store auf der Konsole, dem Pi oder dem PC es von dort installieren.

`LanShare.exe` bekommst du auf der Seite des Stores im Reiter **LAN server**. Installieren musst du nichts: Starte
es, und es legt seine Einstellungen in `%LOCALAPPDATA%\AutoBleem LAN Share\` ab.

![Das Fenster von LAN Share: links die Spiele auf dem Server, rechts die Spiele auf diesem PC](../images/en/lanshare.jpg)

1. **Mit dem Server verbinden.** Gib seine Adresse so ein, wie der Store sie kennt, `http://<seine Adresse>:<port>`,
   und klick auf **Connect**. Links erscheinen die Spiele, die schon auf dem Server liegen, und alle Probleme, die sein
   eigener Scan gefunden hat. Um Spiele auf den Server zu bringen, braucht LAN Share einen von zwei Zugängen:
   - **Share** ist der Spieleordner des Servers, wie er in deinem Netzwerk freigegeben ist (Samba), zum Beispiel
     `\\raspberrypi\games`. LAN Share kopiert die Spiele dort hinein und bittet den Server, zu scannen; der Server
     selbst liest seinen Ordner weiterhin nur.
   - **Token** ist für einen Server, der mit `--allow-uploads` gestartet wurde. Gib sein Token ein - der Server zeigt
     es beim Start an und legt es in `<state>/upload-token` ab. LAN Share lädt dann über HTTP hoch, und ein Upload,
     der mittendrin abbricht, macht dort weiter, wo er aufgehört hat.
2. **Die Spiele auf deinem PC veröffentlichen.** Wähl den Ordner, in dem deine Spiele liegen (ein Ordner pro Spiel),
   hak die gewünschten an und klick auf **Publish the ticked games**. **On the server** zeigt dir, ob der Server ein
   Spiel schon hat - es vergleicht die Seriennummer, oder den Titel, wenn es keine Seriennummer gibt -, und ein Spiel,
   das der Server schon hat, wird nie zweimal geschickt. **Tick those not on the server** hakt alle übrigen für dich an.
3. **Eine Disc veröffentlichen.** Leg eine PS1-Disc ins Laufwerk des PCs und klick auf **Read a disc and publish
   it**. LAN Share liest die ganze Disc in eine `.bin` + `.cue` ein, benannt nach dem Titel des Spiels. Bei einem
   LibCrypt-Spiel schreibt es auch die `.sbi`-Datei, sofern das Laufwerk den Subkanal lesen kann. Hast du die
   Datenbanken angegeben (siehe unten), prüft es die Kopie gegen den bekannten guten Dump. Dann veröffentlicht es das
   Spiel. Bei einem Spiel auf mehreren Discs hakst du vorher **The game has more than one disc** an: LAN Share bittet
   dich dann um jede weitere Disc und veröffentlicht sie zusammen als ein Spiel.
4. **Spiele vom Server nehmen.** Wähl sie aus und klick auf **Remove from the server...**. Gelöscht wird nichts: Jedes
   Spiel wandert in einen Ordner `.removed` neben den Spielen des Servers, und schiebst du es zurück, ist es wieder da.

Die **Databases** sind freiwillig. Zeigst du LAN Share den Cover-Ordner von AutoBleem (`coversU/P/J.db`) und
`Sony - PlayStation.rdb` von RetroArch, benennt es damit die Spiele und prüft eine eingelesene Disc.

Willst du lieber gar nichts kopieren, hak **Also share the games on this PC with the Store** an (standardmäßig aus):
LAN Share bietet dann den Spieleordner auf deinem PC dem Store direkt an. Beim ersten Mal fragt Windows nach seiner
Firewall - erlaube nur private Netzwerke.

<!-- pagebreak -->

## 6. Die Konsolen-Werkzeuge (PlayStation Classic)

Zu einem Stick für die PlayStation Classic gehören zwei Werkzeuge, mit denen du die Konsole über das hinaus
einrichtest, was sie ab Werk kann. Beide sehen aus wie der Rest des Launchers, in seinem Theme und seiner Sprache,
und du bedienst sie mit dem Controller - im Controller-Assistenten auch mit den Tasten vorn an der Konsole.
**PSC-Bios** ist eine Erweiterung, die mit dem Konsolen-Paket kommt: Der Eintrag *Netzwerk & Controller* im
Quick-Menü und im Systemmenü öffnet es, und du findest es auch in der Liste der Erweiterungen. **ABFlashKit** ist eine
App im Set Apps.

### 6.1 PSC-Bios

Mit PSC-Bios verbindest du das Gerät mit der Welt: mit deinem WLAN, der Zeitzone, Bluetooth-Controllern und der
Tastenbelegung eines Controllers, den AutoBleem nicht kennt. Es kommt mit dem Konsolen-Paket und ist auch auf dem
Raspberry Pi und dem PC-Stick dabei. Du öffnest es mit *Netzwerk & Controller* im Systemmenü (oder im Quick-Menü) oder
aus der Liste der Erweiterungen. Ist die Erweiterung installiert, aber ausgeschaltet, ist der Eintrag *Netzwerk &
Controller* ausgegraut und sagt, sie *ist ausgeschaltet - unter Erweiterungen einschalten*; drück Cross darauf, und
die Liste der Erweiterungen öffnet sich bei PSC-Bios, damit du es wieder einschalten kannst.

Der erste Bildschirm gibt dir einen Überblick: Uhrzeit und Zeitzone, die Netzwerkadapter (WLAN, Ethernet, Bluetooth)
mit ihren Adressen und jeden angeschlossenen Controller, mit einem Hinweis, ob er eine Tastenbelegung hat. Auf der
Konsole brauchen die Teile für Netzwerk und Bluetooth den AutoBleem-Kernel (Abschnitt 6.2); auf einem Raspberry Pi
oder dem PC-Stick nutzen sie die Werkzeuge des Systems. Der Controller-Assistent funktioniert überall.

![PSC-Bios: die Übersicht Netzwerk & Controller](../images/en/pscbios-main.jpg)

Vom ersten Bildschirm aus bringt dich je eine Taste in jeden Teil:

| Taste | Was sie öffnet |
|---|---|
| Select | **Wi-Fi Network** verbindet dich mit deinem WLAN (über den Kernel, auf einem Pi oder PC über NetworkManager): Tipp den Namen des Netzes ein oder wähl es aus einer Suche, gib das Passwort ein, wähl den Treibermodus und drück *Apply / Restart Network*. Hier stellst du auch die Zeitzone ein, und sobald du verbunden bist, siehst du die IP-Adresse der Konsole. |
| Square | **Bluetooth Controllers** sucht nach Bluetooth-Controllern wie dem DualShock 4, damit du einen neuen koppeln oder einen nicht mehr benutzten entfernen kannst. |
| L1 | **DualShock 3 Pairing** verbindet deinen ersten DualShock 3, der dafür per USB angeschlossen sein muss, über das sixaxis-Plugin des Kernels. |
| R1 | **Controller Mapping** öffnet den Controller-Assistenten, der unten beschrieben ist. |
| Triangle | **About** zeigt, was PSC-Bios ist. |
| Circle | **Back** bringt dich aus PSC-Bios heraus, zurück in den Launcher. |

**Der Controller-Assistent.** Nimm ihn, wenn ein Controller in AutoBleem gar nichts tut oder seine Tasten an den
falschen Stellen liegen. Er zeigt den angeschlossenen Controller so, wie er wirklich ist - jede Achse, jede Taste und
jeden Hat-Schalter als Zahlen - und ein DualShock-Bild, das aufleuchtet, wenn du drückst. Weil du dem Controller, den
du gerade testest, noch nicht trauen kannst, steuerst du den Assistenten mit den **Tasten vorn an der Konsole**:
**RESET** wechselt zum nächsten Controller, **OPEN** startet die Belegung, und **POWER** bricht ab oder verlässt den
Assistenten. Bei der Belegung fragt der Assistent eine Taste nach der anderen ab: Drück die Taste, die auf dem Bild
leuchtet, oder OPEN, wenn dein Controller keine solche Taste hat. Ein kurzer Druck wird ganz normal belegt.

Du kannst den Assistenten auch vom Controller aus verlassen: Halte Circle 2 Sekunden lang - ein Balken füllt sich, und
die Fußzeile zeigt *Hold 2 s: Exit*. Solange der Controller noch keine Belegung hat, wirkt jede Taste, die du 2
Sekunden hältst, genauso (*Hold any button 2 s: Exit*). Auf einer Tastatur stehen Esc, Leertaste und Enter für POWER,
RESET und OPEN.

Am Ende wird die neue Belegung gleich verwendet, damit du sie ausprobieren kannst, und OPEN speichert sie unter einem
Namen deiner Wahl. Von da an lädt der Launcher sie jedes Mal.

![PSC-Bios: der Assistent für die Controller-Belegung](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - der AutoBleem-Kernel

Der AutoBleem-Kernel ersetzt den Linux-Kernel der Konsole, und er ist freiwillig. Du willst ihn, wenn du mehr aus der
Konsole herausholen willst: Er gibt ihr eine funktionierende Uhr, bringt USB-WLAN- und Bluetooth-Sticks zum Laufen
(für PSC-Bios und Bluetooth-Controller) und ergänzt die Unterstützung der Tasten vorn, die der Emulator für die
Fortsetzungspunkte nutzt. ABFlashKit ist das Werkzeug, das ihn installiert. Es sichert zuerst die Konsole und kann sie
auch über Sonys eigene Wiederherstellung in den Originalzustand zurückversetzen.

> **Dieses Werkzeug schreibt in den Flash-Speicher der Konsole.** Wird das Schreiben unterbrochen - weil der Strom
> ausfällt oder der Stick abgezogen wird -, startet die Konsole womöglich nicht mehr, und ein eigener Kernel lässt
> die Garantie erlöschen. Lass die Konsole am Strom und den Stick eingesteckt, bis die Konsole von selbst neu
> startet. ABFlashKit beginnt mit dieser Warnung: *I understand* geht weiter, *Quit* beendet.

![Das Menü von ABFlashKit](../images/en/abflashkit-menu.jpg)

ABFlashKit kann drei Dinge:

- **Flash Kernel** installiert den Kernel. Gibt es auf dem Stick noch keine Sicherung für die Wiederherstellung,
  sichert es zuerst die Partitionen der Konsole (`LBOOT.EPB`). Es prüft die Sicherung und das Kernel-Abbild,
  schreibt den Kernel und die Systemdateien von AutoBleem und startet die Konsole neu. Steht dort *All done - when the
  screen goes black replace power cord*, wartest du, bis der Bildschirm schwarz wird, ziehst dann das Netzkabel der
  Konsole und steckst es wieder ein.
- **Full backup** sichert alle vier Partitionen der Konsole in `LBOOT.EPB`, damit du sie später wiederherstellen
  kannst. Gibt es schon eine Sicherung, fragt es, bevor es sie überschreibt.
- **Restore Mode** ist der Weg zurück zur Original-Firmware. Es prüft, ob die Sicherung auf dem Stick aus dem
  Originalzustand stammt, setzt die Wiederherstellungs-Markierung und startet in Sonys Wiederherstellung neu, die die
  Konsole aus `LBOOT.EPB` zurückspielt.

Unter jedem Schritt zeigt ein Fortschrittsbalken, wie weit er ist. Auf einer Konsole mit einer anderen eigenen
Firmware, etwa BleemSync oder Project Eris, flasht ABFlashKit nichts: Setz diese Konsole zuerst in den Originalzustand
zurück.

**Vom PC aus anmelden.** Kennst du dich mit Linux aus und willst in die Konsole hineinschauen, kannst du dich von
einem PC aus über ein USB-Kabel an ihr anmelden. Das setzt den AutoBleem-Kernel voraus; auf einer unveränderten
Konsole geht es nicht.

1. Verbinde den Micro-USB-Anschluss der Konsole mit einem USB-Kabel mit dem PC. Der PC erkennt die Konsole als neuen
   Netzwerkadapter, und in den Einstellungen dieses Adapters auf dem PC findest du die Adresse der Konsole.
2. Melde dich mit `ssh root@<Adresse der Konsole>` an. Das voreingestellte Passwort ist `autobleem`.

Statt des Passworts kannst du einen Schlüssel verwenden. Leg deinen öffentlichen Schlüssel in die Datei
`System/ssh/authorized_keys` auf dem Stick und starte die Konsole neu: Beim nächsten Start wird er dem Konto root
hinzugefügt. Ein Update oder eine Neuinstallation des Launchers entfernt ihn nicht.

> **Das voreingestellte Passwort ist auf jeder Konsole gleich** - wer ein Kabel an deine anstecken kann, kann sich
> also als root anmelden. Nimm, wo es geht, einen Schlüssel, und lass eine Konsole mit dem voreingestellten Passwort
> nicht dort stehen, wo andere drankommen.

<!-- pagebreak -->

## 7. Wenn etwas schiefgeht

Die meisten Probleme haben eine einfache Ursache. Unten beginnt jedes mit dem, was du siehst, sagt, warum es passiert,
und dann, was du tun kannst. Brauchst du Hilfe, sind die Protokolle das Erste, wonach jeder fragt - deshalb kommen sie
zuerst.

**Die Protokolle finden.** AutoBleem hält seine Protokolle während des Betriebs im Arbeitsspeicher, damit nicht
ständig auf den Stick geschrieben wird. Nach `System/Logs/` auf dem Stick, der Karte oder im Datenordner gelangen sie
nur, wenn etwas schiefgegangen ist: Stürzt der Launcher, ein PS1-Spiel oder RetroArch ab, werden die Protokolle in
`System/Logs/crash-<n>/` gesichert (die letzten drei Abstürze bleiben erhalten), und der Launcher sagt dir einmal
Bescheid, wenn er wieder da ist. Bist du einem Problem auf der Spur, das kein Absturz ist, behalte alle Protokolle:
Schalte Optionen → *Diagnose* → *Protokolle auf dem Stick behalten:* ein (das wirkt ab dem nächsten Start) oder lege
am PC eine leere Datei `System/Logs/keep` an. Auch die *Hardwareinformationen* (Abschnitt 4.2) zeigen, wo die
Protokolle liegen, und Square sichert dort die aktuellen nach `System/Logs/saved-<n>/`.

Diese Dateien findest du dort:

| Datei | Was sie dir sagt |
|---|---|
| `autobleem.log` | Was der Launcher selbst getan hat. |
| `launch.log`, `pcsx.log` | Wie ein PS1-Spiel gestartet wurde und was der Emulator währenddessen gemeldet hat. |
| `retroarch.log` | Was RetroArch während des Laufs gemeldet hat. |
| `update.log` | Wie ein Online-Update verlaufen ist; es bleibt immer auf dem Stick. |
| `updateroms.log` | Wie UpdateRoms auf dem PC verlaufen ist (Kapitel 5); es bleibt immer auf dem Stick. |

**Ein Bild bittet dich, den Stick einzustecken, oder die Konsole ist eingeschlafen.** AutoBleem findet seinen Stick
nicht: Beim Start der Konsole steckte keiner, oder er wurde abgezogen. Steck ihn in einen beliebigen USB-Anschluss
(am besten vorn, Abschnitt 2.1), bevor die 5 Minuten um sind, oder drück Power. Wurde der Stick nicht sauber
entfernt, prüft AutoBleem ihn zuerst - warte, bis der Fortschrittsbalken durch ist.

**RetroArch meldet: *RetroArch benötigt eine neuere Systembibliothek, als diese Konsole hat*.** Dieses RetroArch wurde
für ein neueres System gebaut als das der Konsole und kann dort nicht laufen. Nimm das RetroArch, das zu AutoBleem
gehört.

**Ein Spiel meldet: *Dieses Spiel ist durch seine PSN-Lizenz geschützt und kann nicht gestartet werden*.** Spiele, die im
PlayStation Network gekauft wurden, sind an ihre Lizenz gebunden, und AutoBleem kann sie nicht ausführen. Daran lässt
sich nichts ändern.

**Ein Spiel steht nicht im Regal.** Meist ist sein Ordner nicht so aufgebaut, wie der Scan es erwartet. Prüf, ob jedes
Spiel einen eigenen Ordner hat und in einem der Formate aus Abschnitt 3.10 vorliegt. Der *Spielemanager* (Abschnitt
4.1) listet nach den Spielen die Ordner auf, die der Scan abgelehnt hat, markiert mit *Nicht hinzugefügt*, und sagt
dir bei jedem, warum; Square löscht so einen Ordner. Hast du einen Ordner in Ordnung gebracht, lässt *Spiele erneut
scannen* im Systemmenü den Scan noch einmal laufen.

**Spiele haben keine Cover.** Entweder wurden die Cover-Datenbanken nicht installiert - lass den Installer noch
einmal laufen und hak sie an -, oder, bei RetroArch-Spielen auf einer Konsole, UpdateRoms ist auf dem PC noch nicht
gelaufen (Kapitel 5).

**Ein Controller tut nichts, oder seine Tasten sind vertauscht.** AutoBleem kennt die Belegung dieses Controllers
nicht. Auf der Konsole belegst du ihn mit dem Controller-Assistenten von PSC-Bios (Abschnitt 6.1). Auf einem Pi oder
PC zeigen die Hardwareinformationen (Abschnitt 4.2), was das System von dem Controller sieht - so erkennst du, ob er
überhaupt erkannt wird.

**Nach einem Spiel bleibt der Bildschirm der Konsole schwarz.** Das Bild des Launchers ist nach dem Ende des Spiels
nicht zurückgekommen. AutoBleem baut sein Fenster von selbst neu auf, bis zu dreimal. Bleibt der Bildschirm trotzdem
schwarz, halte die Power-Taste gedrückt und schalte die Konsole wieder ein.

**Auf einem Raspberry Pi** kommst du hinter den Launcher, wenn es nötig ist: `Alt+F2` bringt dich zu einer
Anmeldeaufforderung auf der zweiten Konsole, und SSH ist ab dem ersten Start eingeschaltet. `sudo journalctl -u
autobleem` zeigt, was der Dienst des Launchers getan hat, und `sudo systemctl restart autobleem` startet ihn neu.
Konnte der erste Start nicht abgeschlossen werden, weil es kein Netzwerk gab, versucht er es beim nächsten Start
erneut.

**Unter Windows** verlässt `Esc` den Launcher. Dein Datenordner ist der, den du beim Setup gewählt hast
(`Documents\AutoBleem`, wenn du nichts geändert hast), und die Protokolle liegen darin im Ordner `System\Logs`.

**Die Konsole startet nach einem Online-Update immer wieder neu (Stick mit ext4 formatiert).** Manche formatieren den
Stick mit ext4, dem Linux-Dateisystem, statt mit FAT32 oder exFAT. Bis zum nächsten Release von AutoBleem entpackt ein
Online-Update auf so einem Stick jede Datei ohne die Berechtigung, die sie als Programm ausführbar macht. AutoBleem
kann dann nicht starten, und die Konsole startet wieder und wieder neu. Sticks mit FAT32 oder exFAT sind nicht
betroffen. Es gibt zwei Wege, das zu beheben.

**Lösung A** braucht einen Linux-PC. Steck den Stick an und mach die Programme von AutoBleem wieder ausführbar. Setz
statt `/media/USER/STICK` deinen eigenen Einhängepfad ein; die letzte Zeile brauchst du nur, wenn RetroArch
installiert ist:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Lösung B**: Installiere das neueste Release von AutoBleem noch einmal auf den Stick, wie in Abschnitt 2.1. Der
Installer braucht einen PC, der den Stick lesen kann. Kann er deinen nicht lesen, muss der Stick zuerst formatiert
werden, und dabei wird alles darauf gelöscht - kopiere vorher deine Spiele herunter.

> Damit es gar nicht erst so weit kommt, nimm **FAT32** (eine unveränderte Konsole liest nur FAT32; exFAT braucht den
> AutoBleem-Kernel, Kapitel 6). Das nächste Release behält die Berechtigungen, und AutoBleem repariert sie bei jedem
> Start.

AutoBleem ist freie Software (GNU GPL v3 oder neuer) und kommt ohne jede Garantie. Hilfe und Neuigkeiten findest du
auf dem Discord-Server, der auf dem Bildschirm *Über* verlinkt ist, oder auf https://autobleem.retromenele.pl/.
