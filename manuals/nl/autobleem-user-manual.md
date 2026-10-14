# AutoBleem 2 Gebruikershandleiding

AutoBleem 2 is een gamelauncher voor de **PlayStation Classic** - en sinds versie 2 ook voor een **Raspberry Pi**,
een **pc die opstart vanaf een USB-stick** en **Windows**. Je PS1-games staan erin als een rij hoesjes op een plank,
met hun artwork en gegevens erbij. AutoBleem start ze in de meegeleverde PCSX-emulator, en als je RetroArch erbij
installeert, speel je er ook games van andere systemen mee. In deze handleiding lees je hoe je AutoBleem op elk
platform installeert, hoe je het dagelijks gebruikt en wat de meegeleverde hulpmiddelen doen.

> Alle downloads vind je op **https://autobleem.retromenele.pl/**. De pagina is ingedeeld per platform: wat je
> moet downloaden staat steeds in het paneel *Install*; de *Build inputs* daaronder zijn bestanden die de
> installatieprogramma's zelf ophalen.

## 1. Wat je krijgt

Met AutoBleem wordt je PlayStation Classic - of een Raspberry Pi, een oude pc of je Windows-computer - een kleine
spelcomputer met een echt menu voor je eigen games. Dit zit erin:

- **De launcher.** Dit is wat je ziet zodra je het apparaat aanzet: een plank vol hoesjes waar je doorheen bladert,
  met de gegevens van elke game ernaast. Van hieruit start je games, deel je ze in sets in (PlayStation, RetroArch,
  Apps), pas je instellingen aan, beheer je memory cards en savestates, en download je apps en games uit de Store.
  Op elk platform ziet hij er hetzelfde uit en werkt hij hetzelfde.
- **Twee PS1-emulators.** `pcsx-abnxt` is de nieuwe en staat standaard ingesteld; `pcsx-ab` is de klassieke
  emulator die altijd al bij AutoBleem zat. Je kiest ertussen in de opties. Ze gebruiken dezelfde instellingen en
  memory cards, dus je kunt altijd wisselen zonder iets kwijt te raken.
- **RetroArch**, als je ook games van andere systemen wilt spelen - NES, SNES, Mega Drive, Game Boy, arcadekasten en
  nog veel meer. Het is op elk platform optioneel. Kopieer je ROM's erbij, en AutoBleem zet ze in lijsten en start
  elke game met de juiste core. Ook PlayStation-games kunnen in RetroArch draaien; de core *PlayStation 1* staat
  bovenaan de lijst met cores (sectie 3.9). Games als Doom draaien vanaf je eigen gamebestanden in een map
  `Packages` (sectie 3.10).
- **De consolehulpmiddelen.** Met *PSC-Bios* - in de menu's heet het *Netwerk & controllers* - stel je wifi, de klok,
  Bluetooth-controllers en de knopindeling van controllers in, op de console maar ook op een Raspberry Pi en de
  pc-stick. *ABFlashKit* installeert de AutoBleem-kernel op een PlayStation Classic (hoofdstuk 6).
- **UpdateRoms** voor Windows. De PlayStation Classic heeft zelf geen netwerk. Daarom ververst dit pc-programma de
  RetroArch-lijsten en haalt het hoesjes op voor een consolestick terwijl die in je pc zit.

![De launcher: de plank met hoesjes, de gegevens van de gekozen game en de knophints](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Installatie

### 2.1 PlayStation Classic

AutoBleem draait helemaal vanaf een USB-stick. In de console zelf verandert niets: haal je de stick eruit, dan
werkt de console precies zoals voorheen. Je hebt alleen een Windows-pc, een USB-stick (USB 2.0, 8 GB of groter) en
de console nodig.

De stick hoeft niet leeg te zijn en wordt **niet geformatteerd**, tenzij je daar zelf om vraagt: AutoBleem komt
naast de bestanden te staan die er al op staan, en een stick die je al met AutoBleem 1.0 gebruikt, wordt ter plekke
bijgewerkt (zie verderop). Voor een console die nog in de originele staat is, moet de stick **FAT32** zijn, want de
kernel van de console kan geen exFAT lezen. Staat de AutoBleem-kernel eenmaal op de console (ABFlashKit,
hoofdstuk 6), dan start hij ook vanaf een exFAT-stick. Zo ben je verlost van de grens van 4 GB per bestand die
FAT32 heeft.

1. Download **AutoBleemInstaller-<version>.zip** uit het PlayStation Classic-paneel van de site en pak het uit waar
   je maar wilt. Er zitten `AutoBleemInstaller.exe` en een README in. AutoBleem zelf wordt tijdens de installatie
   gedownload, dus de pc moet verbinding met internet hebben.
2. Steek de stick in de pc en start `AutoBleemInstaller.exe`. Kies eerst het **kanaal**: *Release* is de geteste
   versie en voor de meeste mensen de juiste keuze, *Testing* is de volgende versie zolang die nog getest wordt, en
   *Nightly* is de allernieuwste ontwikkelversie, die misschien niet werkt. Kies daarna het station van de stick.
   De regel eronder vertelt je welke versie van AutoBleem je gaat installeren en wat er nu op de stick staat:
   *a fresh install* (de andere bestanden op de stick blijven gewoon staan) of *AutoBleem <version> is on this
   stick: it will be updated* (je games, saves, memory cards en instellingen blijven bewaard).
   **Formatteren hoeft niet.** De knop **Format** naast het station is alleen bedoeld voor een gloednieuwe stick
   zonder bestandssysteem, een stick die de console niet kan lezen (bijvoorbeeld NTFS) of een stick die je helemaal
   leeg wilt maken. Hij vraagt het eerst en wist daarna alles op de stick. Kies daar FAT32, tenzij de console de
   AutoBleem-kernel al heeft.
   Vink daarna aan wat je geïnstalleerd wilt hebben:
   - **Cover databases** - de hoesjes en beschrijvingen van de complete PS1-bibliotheek, zodat je games vanzelf
     hun hoesje krijgen (staat standaard aangevinkt; ongeveer 300 MB).
   - **RetroArch** - RetroArch met zijn cores, extra toepassingen (Doom, Quake, Amiga, ...) en de assets van
     libretro, voor games van andere systemen. Staat standaard uit; je kunt het later toevoegen door het
     installatieprogramma opnieuw te starten.
   - **BIOS files** - de BIOS-bestanden die sommige RetroArch-cores nodig hebben voordat ze starten (alleen samen
     met RetroArch).
   - **Sample games** - een paar gratis homebrew-games, zodat de plank de eerste keer niet leeg is.
3. Druk op **Install** en wacht even. De voortgangsbalken en het logboek laten elke stap zien. Aan het eind heet de
   stick `SONY` en staat er een kopie van `UpdateRoms` op (zie hoofdstuk 5).
4. Werp de stick veilig uit en steek hem in de **tweede USB-poort aan de voorkant** van de console (de rechter, voor
   speler 2) - de eerste houd je vrij voor je controller. Zet de console aan: in plaats van het originele menu start
   AutoBleem. Wil je met twee controllers spelen, gebruik dan een USB-hub in de poort aan de voorkant of een
   Bluetooth-controller.

**Aan- en uitzetten.** Zit de stick erin, dan start de console, knippert het lampje een paar seconden terwijl hij
AutoBleem opmerkt, en gaat hij vervolgens in standby nog voordat er iets op het scherm verschijnt. Dat is normaal:
AutoBleem start via het eigen updatemechanisme van de console, en zo werkt dat mechanisme nu eenmaal. Druk één keer
op **Power** en de launcher verschijnt.

Kies je *Uitschakelen* in het systeemmenu, of druk je op de Power-knop van de console, dan gaat de console in de
**standby van AutoBleem**: AutoBleem koppelt eerst de stick netjes los, en daarna wordt het lampje **oranje** - het
teken dat alles goed is gegaan. Druk je weer op Power, dan is de launcher binnen een paar seconden terug.
**Zolang het lampje oranje is, kun je de stick eruit halen** en in je pc steken; Windows vraagt dan niet om hem te
controleren, want hij is netjes losgekoppeld. Steek hem terug voordat je op Power drukt. Trek je de stroomkabel van
de console eruit, dan gaat hij de volgende keer weer door de standby bij het opstarten. Een **rood** lampje betekent
dat de console echt uit staat.

**De poort aan de achterkant.** De micro-USB-poort aan de achterkant is de stroomaansluiting van de console. Met
de AutoBleem-kernel kun je er ook een USB-apparaat op aansluiten, maar de stick hoort in een poort aan de voorkant.

**Als de stick ontbreekt.** Start de console zonder stick, of haal je de stick eruit terwijl AutoBleem draait, dan
vraagt een afbeelding je om hem erin te steken - elke USB-poort is goed. AutoBleem wacht 5 minuten en laat de
console daarna slapen; druk op Power als je wilt dat hij meteen gaat slapen.

![De afbeelding die om de stick vraagt](../images/en/insert-stick.jpg)

**Als de stick gecontroleerd wordt.** Is de stick niet netjes losgekoppeld - je hebt hem eruit gehaald terwijl
AutoBleem draaide, of de stroom viel weg - dan controleert AutoBleem hem op fouten voordat hij hem weer gebruikt:
bij het opstarten, na het ontwaken of zodra je hem terugsteekt. Een voortgangsbalk laat zien hoe ver de controle
is. Op een grote stick kan dat even duren; laat hem afmaken en zet de console in de tussentijd niet uit.

![De controle van de stick](../images/en/stick-check.jpg)

**Bijwerken.** Wil je een stick bijwerken, start dan het installatieprogramma er gewoon opnieuw op - de knop heet
nu *Update*. Het installeert de nieuwste versie van het kanaal dat je kiest; je games, saves, instellingen en
RetroArch-inhoud blijven staan, alleen de eigen bestanden van AutoBleem worden vervangen. Een console met de
AutoBleem-kernel en wifi kan zichzelf ook bijwerken (sectie 3.12).

**Overstappen van AutoBleem 1.0 (of AutoBleem-NG).** Je gebruikt hetzelfde installatieprogramma op dezelfde stick,
zonder te formatteren:

1. Kopieer eerst de hele stick naar je pc, als reservekopie - je weet maar nooit.
2. Steek hem in de pc, start `AutoBleemInstaller.exe` en kies het kanaal en het station. Druk **niet** op Format.
3. Druk op **Install**. Het installatieprogramma zet de oude indeling om naar de nieuwe: RetroArch, de ROM's en de
   thema's komen op de plek waar AutoBleem 2 ze verwacht, en de oude ROM-mappen (`nes`, `snes`, ...) krijgen de
   systeemnamen van RetroArch. Je games, savestates, memory cards, ROM's en RetroArch-saves blijven allemaal
   bewaard, net als `config.ini` - alleen de PS1-emulator daarin wordt omgezet naar pcsx-abnxt.
4. Steek de stick terug in de console. De eerste scan bouwt de gamelijst en de afspeellijsten opnieuw op. Wil je
   hoesjes voor je RetroArch-games, start dan UpdateRoms op de pc (hoofdstuk 5).

> Een console in de originele staat heeft geen klok en geen netwerk. Datums verschijnen pas als de AutoBleem-kernel
> is geïnstalleerd (hoofdstuk 6), en hoesjes voor RetroArch-games komen van UpdateRoms op de pc (hoofdstuk 5).

Je PS1-games zet je in de map `Games` op de stick, één map per game - in sectie 3.10 lees je hoe dat precies zit.

### 2.2 Raspberry Pi

Met AutoBleem wordt een Raspberry Pi een kleine spelcomputer: hij start meteen in de launcher, zonder bureaublad
ertussen. Op de site staan twee kant-en-klare images voor de geheugenkaart, 32-bits en 64-bits, en een pakket voor
een Raspberry Pi OS Lite die je al hebt draaien.

| Model | 32-bits image | 64-bits image | Opmerkingen |
|---|---|---|---|
| Raspberry Pi 5 | ja | ja | |
| Raspberry Pi 4 Model B, Pi 400 | ja | ja | |
| Raspberry Pi 3 Model B / B+ / A+ | ja | ja | prima voor de launcher en PS1 |
| Raspberry Pi Zero 2 W | ja | ja | 512 MB RAM: PS1 draait, de zwaardere RetroArch-cores niet |
| Raspberry Pi 2 Model B | ja | alleen v1.2 | traag voor alles wat 3D is |
| Raspberry Pi 1, Zero, Zero W | nee | nee | ARMv6 - geen van beide images draait |

**Neem voor PS1-games het 32-bits image.** De snelle ARM-recompiler van de klassieke `pcsx-ab` bestaat alleen in
32-bits, dus PS1-games lopen trager op de 64-bits versie. Het 64-bits image heeft wel meer RetroArch-cores; kies
dat dus als de andere systemen belangrijker voor je zijn dan PS1.

**Met Raspberry Pi Imager:**

1. Installeer Raspberry Pi Imager (raspberrypi.com/software). Kies bij *Choose OS* voor *Use custom* en selecteer
   de `autobleem-<version>-rpi-armhf.img.xz` (32-bits) of `-arm64.img.xz` (64-bits) die je hebt gedownload. Je kunt
   ook in de instellingen van de app een repository-URL toevoegen en AutoBleem dan uit de lijst kiezen. Er is er
   één per kanaal: `https://autobleem.retromenele.pl/rpi-imager/os_list.json` voor de laatste release,
   `.../os_list-testing.json` voor de versie die getest wordt en `.../os_list-nightly.json` voor de nieuwste
   ontwikkelversie. Op het tabblad Raspberry Pi van de downloadpagina staan de URL's die er zijn, elk met een
   knop *Copy*.
2. Stel in het aanpassingsscherm van Imager (het tandwiel, of de vraag na *Next*) **de gebruikersnaam en het
   wachtwoord, het wifinetwerk en het land in, en zet SSH aan**. AutoBleem heeft bij de eerste start een netwerk
   nodig.
3. Schrijf de kaart, steek hem in de Pi, sluit een scherm en een toetsenbord of controller aan en zet de Pi aan.

**De eerste start** duurt 5 tot 25 minuten, en op het scherm zie je wat er gebeurt. Is er geen netwerk, dan vraagt
hij erom: kies je wifi uit de lijst en typ het wachtwoord in. Daarna vraagt hij of RetroArch geïnstalleerd moet
worden - geef je binnen een minuut geen antwoord, dan doet hij het gewoon. Vervolgens maakt hij de systeempartitie
groter, maakt van de rest van de kaart de partitie `AUTOBLEEM` voor je games, installeert RetroArch met zijn cores,
de BIOS-pakketten en de voorbeeldgames, en herstart in de launcher.

Heb je geen zin om bij de eerste start vragen te beantwoorden, zet de antwoorden dan van tevoren in
**`autobleem.txt`** op de bootpartitie van de kaart - die kun je op elke pc openen en bewerken:

| Sleutel | Standaard | Betekenis |
|---|---|---|
| `root_gib` | 8 | Grootte van de systeempartitie in GiB; de rest wordt de gamepartitie. |
| `hdmi_mode` | 1920x1080@60 | De schermmodus voor het hele opstarten (`1280x720@60` voor een oudere tv). |
| `retroarch` | (gevraagd) | `yes` / `no` - RetroArch en de andere systemen, of alleen PS1. |
| `thumbnails` | none | `boxarts` haalt de complete set hoesjes binnen, voor hoesjes zonder internet (~9000 bestanden). |
| `bios`, `downloads`, `samples` | yes | Zet op `no` om de BIOS-pakketten, alle downloads of de voorbeeldgames over te slaan. |

**Op een Raspberry Pi OS Lite die je al hebt** (Bookworm of Trixie): kopieer `autobleem-rpi.tar.gz` (of de
arm64-versie) naar de Pi, pak het uit en start `sudo bash install.sh`. Het stelt dezelfde vragen, maakt bij de
volgende start ruimte voor de datapartitie door de systeempartitie te verkleinen (`--shrink-root <GiB>`) en zet de
launcher op de eerste console.

Na de installatie vul je de **partitie `AUTOBLEEM`** van de kaart (exFAT) met je games: haal de kaart eruit en open
hem op een willekeurige pc, of kopieer via het netwerk (SSH staat aan). PS1-games horen in `Games/`, ROM's van
andere systemen in `RetroArch/roms/<system>/`, de PS1-BIOS in `System/Bios/` (sectie 3.11) en thema's in
`Themes/`.

### 2.3 Pc-USB-stick

Hetzelfde kan op elke pc die vanaf USB kan opstarten: de stick start de pc meteen in AutoBleem en laat de eigen
schijf van de pc met rust. Het is een 32-bits systeem, dus ook oude computers doen mee.

1. Schrijf het image naar een stick van 8 GB of groter. **Op Windows** gebruik je **AutoBleemFlasher** (pc-paneel
   van de site - uitpakken en `AutoBleemFlasher.exe` starten; hij vraagt om beheerdersrechten, omdat hij een hele
   schijf beschrijft): kies het kanaal en de stick, druk op *Write* en bevestig twee keer. Hij downloadt het image,
   controleert het, schrijft het en leest het terug. Je krijgt alleen USB-sticks en SD-kaarten te zien, nooit de
   schijf waar Windows op draait, en **alles op de gekozen stick wordt gewist**. Op Linux of macOS download je
   `autobleem-<version>-pcusb-i386.img.xz` uit het pc-paneel en schrijf je het met
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (of met balenaEtcher).
2. Start de pc op vanaf de stick (met de toets voor het opstartmenu van je pc - F12, F8, Esc...). Opstarten via
   BIOS en via UEFI werkt allebei; **Secure Boot moet uit staan**.
3. De eerste start gaat zoals op de Pi: hij vraagt om een netwerk als er geen kabel in zit, vraagt naar RetroArch,
   installeert alles - zo'n acht minuten met een bekabeld netwerk - en herstart in de launcher.

Daarna heeft de stick een partitie `AUTOBLEEM` voor je games. Steek je de stick in een draaiende pc met Windows 10
(versie 1903 of nieuwer), dan verschijnt hij als tweede station waar je games naartoe kunt kopiëren.
`autobleem.txt` staat op de eerste partitie, met dezelfde sleutels als op de Pi (behalve `hdmi_mode` - een pc
gebruikt altijd de eigen modus van het scherm).

### 2.4 Windows

Wil je AutoBleem op je Windows-computer, dan draait het ook gewoon als programma: schermvullend, met de emulators
en RetroArch als aparte programma's.

1. Download **AutoBleemSetup-<version>.exe** en start het. Het installeert per gebruiker, zonder
   beheerdersrechten: het programma komt in `%LOCALAPPDATA%\Programs\AutoBleem`, de gegevens (games, instellingen,
   thema's, RetroArch) in een map die je zelf kiest - standaard `Documents\AutoBleem`.
2. Vink de onderdelen aan - de cover databases, RetroArch (de officiële Windows-versie met zijn cores), de
   BIOS-bestanden, de voorbeeldgames - en laat de installatiehulp ze downloaden.
3. Start AutoBleem vanuit het menu Start of vanaf het bureaublad. Op een pc doet het toetsenbord dienst als
   controller (sectie 3.2).

Bijwerken doe je door een nieuwere setup eroverheen te installeren: het programma wordt vervangen en je datamap
blijft zoals hij is. De launcher kijkt ook eens per dag op de site en biedt een update aan als die er is
(sectie 3.12).

<!-- pagebreak -->

## 3. AutoBleem gebruiken

### 3.1 De launcher

In de launcher kies je wat je gaat spelen. Je games staan er als hoesjes op een plank, zoals de doosjes in je kast,
en je bladert erlangs tot je de game vindt die je zoekt. Al het andere in AutoBleem - de instellingen, de memory
cards, de Store - open je vanaf hier, en als je een game verlaat, kom je hier weer terug.

De gekozen game staat in het midden van de plank, met een zachte weerspiegeling eronder. Ernaast zie je in een klein
raster de gegevens: de uitgever, het jaar, het serienummer, de regio, voor hoeveel spelers de game is en wanneer je
hem voor het laatst gespeeld hebt. Weet AutoBleem een van die dingen niet, dan laat hij die regel gewoon weg in
plaats van hem leeg te tonen. Naast de gegevens staat een afspeelknop. Een game zonder hoesje zie je als een schijfje
in de zwarte tray van een leeg doosje, zodat hij toch een plek op de plank heeft.

Hoe de launcher eruitziet, bepaalt het thema. Het standaardthema is **ab2.0.0**: een nieuwe installatie schakelt
ernaar over, en een update die het meebrengt ook, maar maar één keer - kies je daarna een ander thema (sectie 3.6),
dan blijft dat staan.

**De hintbalk** onderaan het scherm vertelt je wat de knoppen op dat moment doen. Hij heeft twee regels met elk vier
plekken. De eerste regel gaat over de gekozen game: spelen, spelen in RetroArch, de pictogrammenrij eronder openen
of het snelmenu openen. De tweede regel verandert nooit: Select kiest de set, Start kiest een willekeurige game,
Triangle laat het knoppenoverzicht zien en L2 + R2 opent het systeemmenu. Heeft een knop even niets te doen, dan is
zijn hint gedimd.

**Nieuwe games vindt hij zelf.** Telkens als de launcher start, scant hij op de achtergrond je gamemap. Een game die
je erbij hebt gezet terwijl het apparaat uit stond, verschijnt dus zonder dat je er iets voor hoeft te doen. Tijdens
de scan laat een bubbel rechtsboven zien hoe ver hij is, en nieuwe games verschijnen op de plank zodra ze gevonden
worden - je kunt ondertussen gewoon verder bladeren.

**Een nieuwe installatie** heeft nog geen games. In plaats van een lege plank zie je dan een welkomstkaart,
*Hoi, en welkom bij AutoBleem!*, die je vertelt dat je je games in `Games` moet zetten en op *Games opnieuw scannen*
moet drukken. De kaart noemt de plek voor jouw platform: op je stick (PlayStation Classic, pc-stick), op je
SD-kaart (Raspberry Pi) of in je AutoBleem-map (Windows). Zodra een scan de eerste game vindt, verdwijnt de kaart.

**Meldingen** zijn de bubbels rechtsboven. Ze houden je op de hoogte zonder in de weg te zitten: de voortgang van de
scan, de naam van de set waar je net naartoe bent gegaan (*Toont: ...*), een controller met een bijna lege batterij,
een bericht na een crash, een scanprocessor die aan het werk is, en een download uit de Store. De bubbel van een
download toont de snelheid en de resterende tijd, bijvoorbeeld `1.4 MB/s · 0:42`. Hoe lang de informatieve bubbels
blijven staan, bepaal je zelf: Opties → *Weergavetijd melding*.

**Batterijen van controllers.** Op de console, een Raspberry Pi en de pc-stick (niet op Windows) verschijnt elke
draadloze controller die zijn batterijstand doorgeeft als een klein pictogram met het percentage, op een eigen
plaatje, onder elkaar vanaf de linkerbovenhoek. Een controller die als Speler 1 of Speler 2 speelt, krijgt een
label P1 of P2, volgens de optie *Speler 1 / speler 2 wisselen* (sectie 3.6); een controller die niet aan een speler
gekoppeld is, of een derde controller, krijgt geen label. Raakt de batterij van een controller bijna leeg, dan
krijg je één keer een melding met de naam van de controller en het percentage.

**Het kanaallabel.** Gebruik je een versie die geen definitieve release is, dan herinnert een klein label onder de
batterijplaatjes in de linkerbovenhoek je daaraan. Het is een chip met het kanaal en de korte versie ernaast:
`ALPHA`, `BETA` of `RC` voor een voorlopige versie, `TESTING` voor elke andere voorlopige versie, `NIGHTLY` voor een
nightly build en `DEV` voor een versie die met de hand is gebouwd (bij `DEV` is de versie de commit waaruit hij
gebouwd is). Een release heeft geen label.

![De setkiezer: drie tabbladen, en de groepen van het huidige tabblad met het aantal games](../images/en/set-picker.jpg)

### 3.2 Besturing

AutoBleem is gemaakt om helemaal met de controller te bedienen, en de knoppen betekenen op elk scherm hetzelfde:
Cross bevestigt, Circle gaat terug, Triangle helpt. Weet je even niet meer wat een knop doet, dan zegt de hintbalk
onderaan het je, en Triangle op de plank opent het knoppenoverzicht met alle knoppen van alle schermen
(sectie 4.3). Op de plank doen de knoppen dit:

| Knop | Op de plank |
|---|---|
| Links / Rechts | Naar de vorige of volgende game; houd de knop ingedrukt om door te blijven bladeren. |
| L1 / R1 | Springt naar de vorige of volgende beginletter van de titels, zodat je snel door een lange plank heen bent. Op een lege plank met een USB-station aangesloten opent R1 *Schijf* (sectie 3.9a). |
| Cross | Start de gekozen game: een PS1-game in de PS1-emulator, een RetroArch-game in zijn core en een App na zijn leesmij. |
| Square | Start de gekozen PS1-game in plaats daarvan in RetroArch. Is een schijf in een USB-station gekozen, dan kopieert Square de schijf (*Schijf kopiëren*, sectie 3.9a). |
| Circle | Brengt je terug naar de schijfweergave als er een schijf in het station zit (sectie 3.9a). |
| Triangle | Opent het knoppenoverzicht. |
| Start | Kiest een willekeurige game uit de huidige set, voor als je het niet kunt beslissen. |
| Select | Opent de setkiezer, waar je bepaalt welke games de plank laat zien (sectie 3.3). |
| Omhoog | Opent het snelmenu (sectie 3.4). |
| Omlaag | Opent de pictogrammenrij onder de game (*INSTELLINGEN*, *Game*, *MEMORY CARD*, *HERVATTEN*); Omhoog sluit hem weer. |
| L2 + R2 | Opent het systeemmenu (sectie 3.5). |

**Met een toetsenbord.** Op een pc zonder controller, of met een USB-toetsenbord aan de console, een Pi of de
pc-stick, nemen de toetsen het werk van de knoppen over. De pijltjestoetsen zijn de d-pad, Enter is Cross, Esc of
Backspace is Circle, Tab is Triangle en de spatiebalk is Square. F1 en F2 zijn Select en Start, Page Up en
Page Down zijn L1 en R1, Home en End zijn L2 en R2, en F10 opent het systeemmenu. Op een ontwikkelcomputer sluit Esc
het programma en is de spatiebalk Start.

**In elke lijst en elk menu** werkt het op dezelfde manier: Omhoog en Omlaag verplaatsen de cursor, L2 en R2
bladeren een pagina verder, L1 en R1 springen naar de eerste of de laatste regel, Cross kiest en Circle gaat terug.
Je hoeft nooit een knop Opslaan te zoeken: een scherm met instellingen slaat ze op zodra je het met Circle verlaat.

**Een game of een App verlaten.** Houd Start + Select, of Home, 2 seconden ingedrukt en je bent terug in AutoBleem.
Dat werkt op elke controller - die van de console, een USB-controller of een Bluetooth-controller. Druk je kort op
dezelfde knoppen, dan opent in plaats daarvan het menu van de emulator. Een App heeft zo'n menu niet, dus daar doet
alleen lang ingedrukt houden iets.

![De pictogrammenrij onder de gekozen game](../images/en/launcher-icons.jpg)

### 3.3 De sets

Door een grote verzameling blader je makkelijker in stukjes. Met de sets laat je op de plank maar één soort games
zien - alleen je favorieten, alleen de Super Nintendo-games, alleen de games uit één map - zodat je niet langs
honderden hoesjes hoeft te scrollen om die ene game te vinden.

Druk op **Select** en de setkiezer gaat open. Hij heeft drie tabbladen, PlayStation, RetroArch en Apps: met L1 en R1
wissel je van tabblad, Omhoog en Omlaag lopen door de groepen van het tabblad (L2 en R2 een pagina tegelijk), en
Cross zet de gekozen groep op de plank. Circle (*Terug*) sluit de kiezer zonder iets te veranderen. Onderaan staan
die toetsen ook nog eens. Op elke regel zie je hoeveel items erin zitten. Een lege groep opent op een lege plank,
waar de pictogrammenrij alleen *INSTELLINGEN* aanbiedt.

**Het tabblad PlayStation.** Op een PlayStation Classic begint het met *Alle games* en *Interne games* (de twintig
games die in de console zitten), gevolgd door *USB-games* - alles in `Games/` - en een groep voor elke map die je
daaronder hebt gemaakt. Een game in een submap hoort dus bij de groep van die map. Daarna komen *Favoriete games*,
*Gamegeschiedenis* en, zodra je minstens één game als lightgun-game hebt gemarkeerd, *Lightgun-games*. Een Raspberry
Pi, een pc-stick en Windows hebben geen interne games; daar begint de lijst dus bij *USB-games*, en dat is je hele
verzameling.

**Het tabblad RetroArch** is er alleen als RetroArch geïnstalleerd is. Het heeft een groep voor elk systeem waar je
games voor hebt, plus de eigen Favorieten en Geschiedenis van RetroArch.

**Het tabblad Apps** deelt de programma's in naar soort: *Alle apps*, daarna *Games*, *Emulators*, *Hulpmiddelen*,
*Media* en *Overig*. In welke groep een app komt, staat in zijn bestand `app.ini`. Op dit tabblad staan ook de
**PE-apps**: Windows-programma's die de PE-runner uitvoert. Kan de console er een niet starten, dan staat erbij
*kan niet draaien op deze console*. Waar de launcher hem toont, staat er ook een regel *Pakketten* in de lijst
(sectie 3.10).

### 3.4 Het snelmenu

Het snelmenu is een kort lijstje met de dingen die je tijdens het bladeren het vaakst nodig hebt, zodat je ze niet
in het volledige systeemmenu hoeft op te zoeken. Je opent het met **Omhoog** op de plank, of met het
**tandwielpictogram** in de pictogrammenrij (de rij met *INSTELLINGEN*, *Game*, *MEMORY CARD* en *HERVATTEN*).

Met Omhoog en Omlaag loop je door de items (na het laatste spring je weer naar het eerste), Cross kiest er een en
Circle sluit het menu. Een regel onder het menu beschrijft het gekozen item. Dit staat erin:

- *Games opnieuw scannen* zoekt meteen naar nieuwe, gewijzigde of verwijderde games - handig als je net games hebt
  gekopieerd en niet wilt wachten.
- *Store* opent de AutoBleem Store, waar je games, apps en extensies bekijkt en installeert (sectie 3.13).
- Met *RetroArch-cores*, als RetroArch geïnstalleerd is, kies je welke core elk systeem speelt.
- *Netwerk & controllers* opent de schermen voor wifi, Bluetooth-koppeling en de knopindeling van controllers
  (hoofdstuk 6). Het staat er alleen als een geïnstalleerde extensie ze levert - PSC-Bios doet dat, op de console,
  een Raspberry Pi en de pc-stick. Is die extensie geïnstalleerd maar uitgeschakeld, dan is het item grijs en zegt
  de beschrijving dat je hem bij Extensies moet aanzetten; Cross opent dan de lijst met extensies precies op die
  plek.
- *Launcher herstarten* sluit AutoBleem af en start hem opnieuw (alleen op de console, een Raspberry Pi en de
  pc-stick).
- *Systeemmenu...* opent het volledige systeemmenu met al het andere - Opties, Game Manager, Uitschakelen en meer
  (sectie 3.5).

Alles hier behalve de Store, de RetroArch-cores en Launcher herstarten staat ook in het systeemmenu.

![Het snelmenu](../images/en/quick-menu.jpg)

### 3.5 Het systeemmenu

In het systeemmenu staat alles wat AutoBleem kan behalve spelen: de instellingen, de hulpmiddelen voor je
verzameling en je memory cards, informatie over het apparaat, en de manier om het uit te zetten. Druk tegelijk op
**L2 + R2** (in welke volgorde maakt niet uit) en het menu gaat open boven de plank. De items zijn ingedeeld onder
de kopjes *Bibliotheek*, *Systeem* en *Verlaten*, met de twee die je het meest gebruikt bovenaan. Een regel onderaan
het menu beschrijft het gekozen item, zodat je eerst rustig kunt rondkijken voordat je iets kiest.

| Onderdeel | Item | Wat het doet |
|---|---|---|
| (bovenaan) | *Games opnieuw scannen* | Zoekt nu naar nieuwe, gewijzigde of verwijderde games. De scan houdt de map ook zelf in de gaten; dit heb je dus alleen nodig als je niet wilt wachten. |
| | *Extensies* | Toont de extensies op de stick, zoals de AutoBleem Store, zodat je ze kunt starten of uitschakelen (sectie 3.13). |
| *Bibliotheek* | *Game Manager* | Toont de PS1-games als een lijst met hun mappen, waar je een game kunt verwijderen of de hoesjes kunt wissen (sectie 4.1). Kan niet geopend worden zolang er een scan loopt. |
| | *Memory cards* | Beheert je gedeelde sets memory cards (sectie 3.8). |
| | *Scanprocessors* | Bepaalt de volgorde van de programma's die elke scan eerst uitvoert, en zet ze aan of uit (sectie 3.14). Kan niet geopend worden zolang er een scan loopt. |
| *Systeem* | *Opties* | Opent de instellingen van AutoBleem (sectie 3.6). |
| | *Netwerk & controllers* | Opent de schermen voor wifi, het koppelen van Bluetooth-controllers, het instellen van de DualShock 3 en de knopindeling van controllers (hoofdstuk 6). Staat er alleen als een extensie ze levert - zie hieronder. |
| | *Hardware-informatie* | Toont de gegevens van het apparaat - systeem, CPU, opslag, netwerkinterfaces, tijdzone, beeldscherm, en de controllers met hun knopindeling - op elk platform op dezelfde pagina (sectie 4.2). Met Circle ga je terug naar het systeemmenu. |
| | *Virtueel gamepad* | Toont de controllers die Apps krijgen en de controllers die de daemon ziet. Dat helpt als een controller in een App niet werkt (sectie 4.5). Met Circle ga je terug naar het systeemmenu. |
| | *Software-update* | Kijkt nu meteen op de site of er een nieuwere AutoBleem of RetroArch is, in plaats van te wachten op de dagelijkse controle (sectie 3.12). Weet de launcher al van een nieuwe versie, dan staat er *Update beschikbaar*. Op een PlayStation Classic heb je hiervoor de AutoBleem-kernel en een wifinetwerk nodig. |
| | *Over* | Toont de makers en de licentie. |
| *Verlaten* | *RetroArch* | Verlaat de launcher en gaat naar het eigen menu van RetroArch, voor zijn instellingen en inhoudslijsten; sluit je RetroArch, dan ben je terug in de launcher. Staat er alleen als RetroArch geïnstalleerd is. |
| | *Uitschakelen* | Zet het apparaat uit nadat je dat bevestigd hebt (zie hieronder). |

**Netwerk & controllers** verschijnt alleen als een geïnstalleerde extensie de `network`-ingang levert. Een extensie
geeft dat aan met `Provides=network` in haar `extension.ini`. PSC-Bios doet dat op de console, een Raspberry Pi en de
pc-stick. Is die extensie geïnstalleerd maar uitgeschakeld, dan blijft het item grijs in het menu staan en zegt de
beschrijving dat je haar bij Extensies moet aanzetten; Cross erop opent de lijst met extensies meteen bij die
extensie.

**Uitschakelen** doet wat bij het apparaat past. De console gaat in de standby van AutoBleem: de stick wordt
losgekoppeld, het lampje wordt oranje, en met Power is de launcher binnen een paar seconden terug (sectie 2.1). Een
Raspberry Pi of een pc sluit gewoon af.

![Het systeemmenu](../images/en/system-menu.jpg)

### 3.6 Opties

In Opties maak je AutoBleem helemaal van jezelf: het beeld op je scherm, het uiterlijk van de launcher, de taal, het
geluid en de PS1-emulator die je games speelt. Je opent het vanuit het systeemmenu (*Opties*) of met het pictogram
*INSTELLINGEN* onder een game. Meestal stel je het scherm en de taal één keer in, en kom je pas terug als iets er op
een bepaalde tv niet goed uitziet of als je zin hebt in iets anders.

De instellingen zijn in groepen ingedeeld, elk onder een eigen kopje. Met Omhoog en Omlaag ga je van regel naar
regel, en met Links en Rechts verander je de waarde van de regel waar je op staat: kort drukken is één stap,
ingedrukt houden gaat door. L1 en R1 springen naar de eerste of de laatste regel, L2 en R2 bladeren een pagina
verder. Op een regel met een keuze uit thema's, muziek of lettertypen kiest Start er willekeurig een. Een
instelling die aan of uit kan, staat op **AAN** of **UIT**. Elke wijziging zie je meteen, en Circle verlaat het
scherm en slaat alles op - je hoeft verder niets te bevestigen. De enige uitzondering is de schermmodus: die wordt
uitgeprobeerd als je Opties verlaat (zie *Beeld:* hieronder).

Sommige regels zie je alleen waar ze zin hebben: de CRT-regels alleen bij een 4:3-beeld, de RetroArch-regels alleen
als RetroArch geïnstalleerd is, de interne games alleen op een PlayStation Classic.

| Groep / instelling | Waar het voor is |
|---|---|
| *Interface*: *Beeld:* | Stelt de resolutie van het scherm in, voor de launcher en de PS1-emulator. *Auto* gebruikt de eigen modus van het scherm en laat zien welke dat is, bijvoorbeeld *Auto (1920x1080)*; je kunt ook elke andere modus kiezen die het scherm opgeeft. De console biedt 720p, 1080p en *CRT 4:3* (720x480), de modus voor een oude beeldbuis-tv of een 4:3-opnameapparaat. Verander dit als het beeld niet op je tv past of wazig is. Deze regel ontbreekt als AutoBleem in een venster op een ontwikkelcomputer draait. |
| *CRT-marge:* | Maakt alles een beetje kleiner, van 0 tot 10 % in stappen van 1 %, omdat oude tv's de randen van het beeld afsnijden. Zet hem hoger tot de hintbalk en de hoeken helemaal te zien zijn. Verschijnt alleen bij een 4:3-uitgang, werkt meteen en geldt al vóór het startscherm. |
| *Beeldhoogte:* | Maakt het beeld hoger of lager, van -40 tot +40 in stappen van 2, op elke 4:3-uitgang - *CRT 4:3*, of een 4:3-modus op een VGA- of pc-uitgang. Gebruik het als het beeld op een oude tv platgedrukt is of boven en onder van het scherm valt. Werkt meteen, en het gamebeeld van RetroArch volgt het. |
| *Schermschaling van de emulator:* | Bepaalt hoe de PS1-emulator het beeld van een game op je scherm past. *1x1* toont de eigen pixels van de PlayStation, klein en precies; *2x (geheel)* en *4:3 (geheel)* vergroten alleen met hele veelvouden, wat het scherpste beeld geeft; *4:3* houdt de oorspronkelijke vorm van het beeld aan; *Volledig scherm* rekt het beeld uit over het hele scherm. Dit vervangt de oude schakelaar Widescreen. De klassieke `pcsx-ab` en RetroArch kennen alleen volledig scherm en 4:3. |
| *Schermhalo:* | Staat dit op AAN, dan worden de lege stroken naast het gamebeeld (waar het beeld het scherm niet vult) gevuld met een zachte gloed van het beeld zelf in plaats van zwart. Werkt met `pcsx-abnxt`. |
| *AutoBleem thema:* | Verandert het uiterlijk van de launcher. Thema's staan in `Themes/`, en een themazip die je daar neerzet, verschijnt ook met zijn naam in de lijst. De thema's die bij AutoBleem horen, worden bij elke update ververst; wil je er een aanpassen, kopieer het dan eerst onder een nieuwe naam. Het standaardthema is **ab2.0.0**. |
| *Coverstijl:* | Kiest het jewelcase-kader dat om de PS1-hoesjes wordt getekend. |
| *Glans op de hoes:* | Laat een glans over het gekozen hoesje glijden telkens als de plank tot stilstand komt. |
| *Taal:* | Stelt de taal van de launcher in; er zijn er 17, en de wijziging is meteen zichtbaar. |
| *Weergavetijd melding:* | Bepaalt hoe lang de informatieve bubbels (*Toont: ...*, de samenvatting van de scan) blijven staan, van 0 tot 20 seconden; bij 0 staat er *Uit* en zijn ze uitgeschakeld. Foutmeldingen houden hun eigen vaste tijd, zodat je er nooit een mist. |
| *Startscherm:* | Toont de AutoBleem-afbeelding terwijl de launcher start; zet het uit om meteen naar de plank te gaan. |
| *Animaties:* | Laat het ene scherm vloeiend overgaan in het volgende; zet het uit als je liever hebt dat elk scherm meteen verschijnt. |
| *Lettertypen*: *Standaardlettertype gebruiken:* | Staat dit op AAN, dan gebruikt de launcher zijn eigen lettertype (Red Hat Text); zet het uit om het lettertype uit de volgende regel te gebruiken. |
| *Lettertype:* | Kiest een eigen lettertype: elk `.ttf`- of `.otf`-bestand in `resources/fonts`, `RetroArch/fonts` of de map van het thema. De regel toont de naam van het lettertype dat echt gebruikt wordt. |
| *Geluid*: *Muziek:*, *Achtergrondmuziek:* | *Muziek:* kiest het nummer dat onder de launcher speelt - dat van het thema, of een bestand uit `resources/music`. *Achtergrondmuziek:* bepaalt of er überhaupt muziek speelt. |
| *Emulatie*: *PS1-emulator:* | Kiest de emulator waarin je PS1-games starten: `pcsx-abnxt`, de standaard (de huidige PCSX-ReARMed met de toevoegingen van AutoBleem), of `pcsx-ab`, de klassieke. Loopt een game niet lekker, probeer dan de andere. Een hervattingspunt dat de ene heeft opgeslagen, kun je in de andere voortzetten, behalve als de game zonder BIOS-bestand draaide. |
| *Speler 1 / speler 2 wisselen (PS1-emulators):* | Wisselt om welke van de eerste twee controllers Speler 1 is en welke Speler 2, in beide PS1-emulators - handig als de controllers "verkeerd om" zijn aangesloten. Het maakt alleen uit met twee of meer controllers; met één controller ben je altijd Speler 1. RetroArch merkt er niets van. Kan de gebruikte PS1-emulator nog niet wisselen, dan zegt AutoBleem dat. |
| *Speel alle PSX games met RA:*, *Update RA configuratie:*, *RetroArch-configuratie bewaren:* | Deze drie staan er alleen als RetroArch geïnstalleerd is. De eerste start elke PS1-game in de PS1-core van RetroArch (*PlayStation 1*; op een pc is dat SwanStation). Met de tweede mag AutoBleem zijn instellingen in de configuratie van RetroArch schrijven als hij daar een game start. De derde bewaart een wijziging die je in het eigen menu van RetroArch maakt wanneer RetroArch afsluit. |
| *Bibliotheek*: *Toon interne games:* | Toont de ingebouwde games van de console in de PlayStation-lijsten (alleen PlayStation Classic). |
| *Spelnamen opschonen:* | Staat dit op AAN (de standaard), dan tonen de RetroArch-gamelijsten nette namen, zonder labels tussen haakjes zoals (USA), (Rev 1) of [!]; UIT toont de bestandsnamen. De bestandsnaam staat dan nog steeds bij de gegevens van de game. PS1-games merken er niets van, want hun titels komen uit de database. |
| *Hoesjes online ophalen:* | Laat de scan ontbrekende hoesjes downloaden van de servers van libretro (Raspberry Pi, pc, Windows). |
| *Updates*: *Updates:* | Kiest naar welke updates de launcher kijkt (sectie 3.12): `release` (de geteste versie), `testing` (de volgende versie, die nog getest wordt), `nightly` (de nieuwste ontwikkelversie) of `off`. De standaard volgt de versie die je hebt geïnstalleerd. Verschijnt niet op een ontwikkelcomputer. |
| *Diagnose*: *Logbestanden op de stick bewaren:* | Bewaart vanaf de volgende start elk logbestand op de stick, niet alleen na een crash - zet het aan als je een probleem op het spoor wilt komen (hoofdstuk 7). |
| *Prestaties tonen:* | Toont linksonder een overlay met de framerate, de CPU-belasting, de threads en het geheugen; in een game laat de emulator ook zijn FPS en CPU zien. |

**De schermmodus wijzigen.** Verlaat je Opties met een nieuwe modus bij *Beeld:*, dan schakelt AutoBleem ernaar over
en vraagt *Deze beeldmodus behouden?*. Ziet het beeld er goed uit, bevestig het dan. Laat je tv niets zien, wacht dan
gewoon even: zonder bevestiging gaat AutoBleem na een aftelling terug naar de vorige modus.

**Thema's op een 4:3-scherm.** In de modus *CRT 4:3* toont de themalijst alleen thema's met een 4:3-indeling. Heeft
het thema dat je gebruikt die niet, dan neemt het standaardthema zijn plaats in zodra je de modus bevestigt (en bij
elke start in die modus), en een melding vertelt het je: *Thema gewijzigd naar het standaardthema (CRT 4:3)*.

![De opties, in groepen](../images/en/options.jpg)

![De groep Beeld: CRT-marge en Beeldhoogte](../images/en/options-display.jpg)

![De melding na het overschakelen naar CRT 4:3 met een thema zonder 4:3-indeling](../images/en/crt43-theme-notice.jpg)

### 3.7 De instellingen van een game

Elke game kan zijn eigen instellingen hebben. De meeste games spelen prima zoals ze zijn, maar soms heeft er een
een duwtje nodig - een scherper of zachter beeld, een overgeslagen frame om hem soepel te houden, een andere
memory card - of wil je hem als favoriet markeren. In de game-editor verander je dat voor die ene game, zonder
aan de andere te komen.

Kies een game en druk op **Omlaag** om de pictogrammenrij eronder te openen. Er staan vier pictogrammen in:
*INSTELLINGEN* (de opties uit sectie 3.6), *Game* (de eigen instellingen van deze game), *MEMORY CARD* (zijn memory
card) en *HERVATTEN* (zijn savestates). Ga naar een pictogram en open het met Cross.

**De game-editor** (het pictogram *Game*) toont rechts de gegevens van de game - de titel, de uitgever, het jaar, het
aantal spelers, de map en de memory card - en links zijn instellingen. Met Omhoog en Omlaag ga je van instelling naar
instelling en met Links en Rechts verander je ze, net als in Opties; houd je een knop ingedrukt, dan herhaalt de
beweging zich. Ben je klaar, dan slaat Circle je wijzigingen op en brengt je terug. Een game zonder titel in zijn
gegevens staat er onder de naam van zijn map.

De instellingen zijn in vier groepen verdeeld:

- **Game** gaat over hoe AutoBleem met de game omgaat. *Favoriet:* zet hem in de groep *Favoriete games* van de
  setkiezer. *Gegevens vergrendelen:* vertelt de scanner dat hij de titel, het serienummer en de schijvenlijst van
  de game precies zo moet laten als jij ze hebt ingesteld, zodat een latere scan je wijzigingen niet overschrijft.
  *Hervatten:* bepaalt wat er gebeurt als je een game start die hervattingspunten heeft: *Vragen* toont de keuze
  van het hervattingsslot, *Laatste slot* gaat meteen verder vanaf het nieuwste slot, en *Nooit* start de game altijd
  vanaf het begin. Is RetroArch geïnstalleerd, dan zijn er nog twee regels. *Lightgun-game:* is voor een game die je
  met een lightgun speelt: hij komt in de groep *Lightgun-games* en draait altijd in RetroArch, omdat de PS1-core van
  RetroArch de GunCon kent (zet je dit aan, dan gaat ook de volgende regel aan). *Speel met RA:* laat alleen deze game
  in RetroArch draaien in plaats van in de PS1-emulator.
- **Beeld** gaat over hoe het beeld eruitziet. *Resolutie:* tekent de game op 1x of 2x (op de ingebouwde GPU), en
  *Naden verwijderen:*, dat alleen bij 2x werkt, verbergt de dunne lijntjes die op die grootte tussen stukken van het
  beeld kunnen verschijnen. *Dithering:* (*Uit*, *Aan*, *Altijd*) regelt het fijne puntjespatroon waarmee de
  PlayStation kleuren in elkaar laat overlopen, en *Vloeiend maken:* kiest een van de verzachtende schalers van de
  emulator. *Filter:* bepaalt hoe het beeld naar het scherm wordt geschaald: *Dichtstbijzijnd* toont kale pixels,
  *Lineair* verzacht ze, *Scherp* en *Scherp (eenvoudig)* houden de pixels strak zonder te flikkeren, en dan is er nog
  *Quilez*. De CRT-filters *CRT (fast)*, *CRT (raster)* en *CRT-Pi* bootsen een oude tv na en tekenen hun eigen
  scanlines; zolang er een van gekozen is, zijn de scanline-regels grijs. Anders voegt *Scanlines:* de donkere lijnen
  van een oude tv toe, en bepaalt *Helderheid scanlines:* hoe donker ze zijn. *Resolutie*, *Naden verwijderen*,
  *Dithering*, *Vloeiend maken* en de filters behalve *Lineair* en *Dichtstbijzijnd* zijn voor `pcsx-abnxt`; de
  klassieke `pcsx-ab` en RetroArch tonen elk ander filter als *Dichtstbijzijnd*.
- **Rendering** heeft de GPU-*Plugin:* en *Frameskip:* (*Auto*, *Uit*, of 1 tot 3 frames). Frames overslaan helpt een
  game die te traag loopt om zijn snelheid vast te houden, maar het beeld wordt er minder vloeiend van.
- **Emulator** heeft *SpeedHack:*, de CPU-*Klok:*, *SPU interpolatie:* (hoe het geluid wordt gladgestreken),
  *Opstartlogo:* en, met `pcsx-abnxt`, *Sony-hacks:*. Zet *Opstartlogo:* uit om de BIOS-shell over te slaan - dat heb
  je nodig voor een homebrew-schijf die door zijn eigen logo niet wil opstarten.

De vorm van het beeld en de resolutie van het scherm stel je niet per game in maar voor alle games tegelijk, in
Opties (*Schermschaling van de emulator:* en *Beeld:*).

**Andere knoppen in de editor.** Met Triangle geef je de game een andere naam, met het schermtoetsenbord. Square geeft
de game een andere memory card (*Memory card wisselen*). Zolang de game nog zijn eigen kaart gebruikt, maakt Start
van die kaart een nieuwe gedeelde set, zodat andere games hem ook kunnen gebruiken (*Memory card delen*, sectie 3.8).
Die twee zijn er niet voor de interne games van de console. Links / Rechts of Omhoog / Omlaag ingedrukt houden
herhaalt de beweging hier, en ook in de game-opties en het coresscherm van RetroArch.

Een game op het station zonder bestand `pcsx.cfg` kan zijn instellingen niet bewaren; verander je er een, dan
meldt de editor *Niet opgeslagen: deze game heeft geen pcsx.cfg*.

Voor een **schijf in het station** (sectie 3.9a) hebben sommige instellingen geen zin. De editor maakt die regels dan
grijs, en de regel onderaan zegt *Niet beschikbaar voor een schijf in het station* als je erop komt.

![De game-editor voor een schijf in het station](../images/en/game-editor-disc.jpg)

**Instellingen die in de emulator zijn opgeslagen.** Je kunt een game ook tijdens het spelen bijstellen: het eigen
menu van de emulator heeft *Save settings for this game* (sectie 3.9). Heeft een game daar instellingen opgeslagen,
dan speelt hij voortaan met die instellingen. De game-editor toont de regels van Beeld, Rendering en Emulator dan
grijs, met de opgeslagen waarden, onder het kopje *Opgeslagen in de emulator*: je kunt ze lezen maar niet
veranderen. Wil je liever weer de instellingen van de game-editor gebruiken, kies dan *Instellingen ontgrendelen* en
bevestig: de instellingen die de emulator heeft opgeslagen, worden gewist en je kunt de regels weer aanpassen. Beide
emulators, `pcsx-ab` en `pcsx-abnxt`, lezen en schrijven dezelfde opgeslagen instellingen; het maakt dus niet uit
welke ze heeft opgeslagen.

![De game-editor](../images/en/game-editor.jpg)

### 3.8 Memory cards en savestates

Op een echte PlayStation deelde je een of twee memory cards met al je games, en vroeg of laat zaten ze vol. In
AutoBleem heeft elke PS1-game standaard zijn eigen memory card. Je hoeft dus nooit na te denken over ruimte of over
op welke kaart een save staat. De kaart wordt bewaard bij de savestates van de game, in
`Games/!SaveStates/<game folder>/`.

**Gedeelde sets memory cards.** Soms moeten games elkaars saves kunnen zien - een vervolg dat de save van het eerste
deel inleest, bijvoorbeeld, of de delen van een reeks die je op één kaart wilt hebben. Daarvoor maak je een gedeelde
set: één kaart die meerdere games gebruiken. De sets staan in `Games/!MemCards/`, en je beheert ze met
*Memory cards* in het systeemmenu. Square maakt een nieuwe set (de naam typ je met het schermtoetsenbord), Cross
geeft de gekozen set een andere naam en Triangle verwijdert hem, nadat het je eerst gevraagd is. Wil je een game op
een set zetten, gebruik dan *Memory card wisselen* in zijn game-editor (sectie 3.7), of zijn pictogram
*MEMORY CARD*.

**De memory card-editor** open je met het pictogram *MEMORY CARD* van een game. Hij toont de kaart van de game en een
tweede kaart naast elkaar, met het pictogram en de titel van elke save, net als het memory card-scherm van de
originele console. Square kopieert de gekozen save naar de andere kaart, Triangle verwijdert hem, en Select
defragmenteert een kaart: de vrije blokken worden bij elkaar gezet, zodat een grote save er weer op past. Met Start
kies je welke set rechts te zien is, en Cross laadt beide kaarten opnieuw van de stick. Een kaart waar de game nog
niets op heeft geschreven - een game waarin je nog niet hebt opgeslagen - is leeg, en naast de naam staat
*nog geen kaart*. Heb je iets veranderd, dan vraagt AutoBleem *Wil je memory card-gegevens opslaan?* voordat hij de
editor verlaat, de kaarten opnieuw laadt of een andere set toont.

![De memory card-editor](../images/en/memory-card-editor.jpg)

**Hervattingspunten.** In veel PS1-games kun je alleen op bepaalde plekken opslaan, en je haalt er niet altijd een
voordat je moet stoppen. Daar zijn hervattingspunten voor: verlaat je een PS1-game met de Reset-knop van de console
(of via het menu van de emulator op een Pi of een pc), dan bewaart AutoBleem een savestate van precies het punt
waar je was. Terwijl hij die wegschrijft, op weg uit de game, toont de emulator *Please wait...*. De volgende keer
ga je vanaf dat moment verder.

Je vindt ze onder het pictogram *HERVATTEN* van de game. Heeft een game een hervattingspunt, dan zie je er een
plaatje van op het pictogram; heeft hij er geen, dan is het pictogram grijs. De keuze van het hervattingsslot heeft
vier slots, als omlijste kaartjes, elk met een plaatje van het moment, het slotnummer en de datum. Het nieuwste is
gemarkeerd met **NIEUWSTE**, en bij een slot dat nog niet gebruikt is, staat *Geen hervattingspunt*. Cross gaat
verder vanaf het gekozen slot, Triangle verwijdert het. Of de keuze überhaupt verschijnt als je de game start,
hangt af van de instelling *Hervatten:* van de game (sectie 3.7).

Ook PS1-games die je in RetroArch speelt, hebben hervattingsslots. Elk slot heeft een badge - het logo van
AutoBleem 2 of dat van RetroArch - zodat je ziet welke emulator het heeft geschreven.

![De keuze van het hervattingsslot](../images/en/resume-picker.jpg)

### 3.9 Games, RetroArch en Apps starten

Een game starten doe je het vaakst, dus het kost maar één knop: kies de game op de plank en druk op **Cross**. Een
PS1-game opent schermvullend in de PS1-emulator die je in Opties hebt gekozen (sectie 3.6) en loopt tot je hem
verlaat. Speel je een PS1-game liever in RetroArch - omdat hij daar beter loopt, of omdat je de opties van
RetroArch fijn vindt - druk dan op **Square**.

**Een game verlaten.** Op de PlayStation Classic doen de knoppen van de console wat je zou verwachten. **Reset** aan
de voorkant brengt je terug naar de launcher en bewaart een hervattingspunt van waar je was, zodat je later verder
kunt (sectie 3.8); dat werkt zelfs als het menu in de game openstaat. **Power** zet de console uit. Een Raspberry Pi
of een pc heeft zulke knoppen niet; daar verlaat je de game via het menu van de emulator, dat hieronder beschreven
staat.

Er is ook een uitgang die op elke controller hetzelfde werkt - die van de console, een USB-controller of een
Bluetooth-controller: **houd Start + Select, of Home, 2 seconden ingedrukt**, en je bent terug in AutoBleem. Druk je
kort op dezelfde knoppen, dan opent het menu van de emulator. De launcher herinnert je aan allebei in zijn hints
(*Houd Select+Start of Home 2 seconden ingedrukt: terug naar AutoBleem* en *Kort indrukken van Select+Start of Home:
het menu van de emulator*). Een App heeft geen emulatormenu, dus daar doet alleen lang ingedrukt houden iets. Op de
console stopt Reset ook altijd een App.

**Het menu in de game.** Met `pcsx-abnxt` heeft de emulator een eigen menu voor wat je tijdens het spelen nodig hebt:
opslaan, van schijf wisselen, het beeld bijstellen, de controllers kiezen. Druk op de menuknop - Home op een
controller die er een heeft, **Select + Start** op een controller zonder, of **Esc** op een toetsenbord - en de game
pauzeert achter het menu, met het laatste beeld op de achtergrond. Houd je de menuknop 2 seconden ingedrukt, dan doet
dat hetzelfde als Reset: je verlaat de game. Het menu heeft drie tabbladen, en met L1 en R1 wissel je ertussen. Het
onthoudt waar je was, dus de volgende keer opent het op hetzelfde tabblad en dezelfde regel.

- Het tabblad **Game** gaat over de game zelf. *Hervatten* sluit het menu en je speelt verder. Onder *Saves* legt
  *Quick save* het moment vast waarin je zit, en *Quick load* haalt het terug. *Load autosave* brengt je terug naar
  hoe de game er tot 30 seconden geleden voor stond - de emulator houdt die kopie tijdens het spelen in het geheugen,
  en zo red je jezelf uit een fout die je niet ongedaan kunt maken. Onder *CD disc* is *Change disc* voor een game op
  meerdere schijven als hij om de volgende vraagt, en *Reset game* begint de game opnieuw. *Save settings for this
  game* bewaart de instellingen die je voor deze ene game hebt gekozen (sectie 3.7). *PCSX menu* opent de eigen
  pagina's van PCSX-ReARMed, met zijn opties, cheats en About, en *Exit* brengt je terug naar AutoBleem.
- Op het tabblad **Beeld** verander je hoe de game eruitziet terwijl je kijkt: *Beeld*, *Resolutie* (1x of 2x),
  *Naden verwijderen*, *Dithering*, *Scaling*, *Vloeiend maken*, *Filter*, *Scanlines* en *Helderheid scanlines*.
  Het zijn dezelfde instellingen als in de game-editor (sectie 3.7), en bij elke regel staat rechts een hulpregel die
  zegt wat hij doet. *Beeld* is de resolutie van het scherm; op de console kies je die in Opties, en hier wordt hij
  alleen getoond. Het filter CRT-Pi is te zwaar voor de console op 1080p. Een regel die niet van toepassing is, is
  grijs, en zijn hulpregel vertelt je waarom.
- Het tabblad **Controllers** bepaalt wat er in de twee poorten van de PlayStation zit, *Controller 1* en
  *Controller 2*: een gewone (digitale) controller, een analoge controller (DualShock), een lightgun of niets.
  Sommige games werken alleen met één soort controller. De wijziging gaat in zodra je teruggaat naar de game.

Het menu is getekend in dezelfde ab2.0.0-stijl als de launcher, zodat het niet als een ander programma aanvoelt, en
het toont de batterijen van je controllers en het plaatje van je laatste quick save.

**RetroArch-games.** Een game van een ander systeem start in RetroArch, met de core die de launcher voor dat systeem
heeft gekozen. Ben je klaar, dan brengt *Close Content* of *Quit RetroArch* in het menu van RetroArch je terug naar
de launcher. Wil je veranderen welke core een systeem speelt, open dan *RetroArch-cores* in het snelmenu
(sectie 3.4); de lijst opent met de core *PlayStation 1* bovenaan. En wil je het eigen menu van RetroArch (de XMB)
voor zijn instellingen en zijn eigen inhoudslijsten, kies dan *RetroArch* in het systeemmenu: RetroArch opent dan
zonder iets geladen.

![Het venster RetroArch-cores, met de core PlayStation 1 bovenaan](../images/en/retroarch-cores.jpg)

**Apps.** Apps zijn eerder programma's dan games: de consolehulpmiddelen en, op de console, de extra toepassingen die
bij het pakket van RetroArch horen - Doom, Quake, Amiga en meer. Je vindt ze in de set Apps. Voordat een App start,
toont AutoBleem zijn leesmij, zodat je weet wat het is en hoe je het bedient. Cross start de App, Circle brengt je
terug naar de plank.

![De leesmij van een App, getoond voordat de App start](../images/en/app-start.jpg)

**De instellingen van een App.** Veel Apps zijn geschreven voor één bepaalde controller, dus je kunt instellen hoe ze
de jouwe zien. Kies de App, open de pictogrammenrij en kies *Game*: de *Game-instellingen* van de App gaan open
(*Wijzig hoe dit programma wordt gestart*). *Controllermodus:* bepaalt welke controller de App denkt te hebben.
*Automatisch* gebruikt wat de App zelf vraagt; *PSC-controller* en *Xbox 360-controller* laten je controller zien als
die van de console of als een Xbox 360-controller, en *PSC-controller (systeem)* en *Xbox 360-controller (systeem)*
doen hetzelfde via het systeem zelf. Reageert een App niet goed op je controller, probeer dan een andere modus.
*D-pad als stick:* laat de d-pad de analoge stick bewegen, voor een App die alleen naar de stick luistert, en
*Stick als D-pad:* doet het omgekeerde.

Sommige Apps stellen je de eerste keer dat je ze start een vraag. De ene wil weten *Welke besturing heeft je
controller?*, om zijn besturing in te stellen: antwoord *Eén D-pad* voor een controller met alleen een d-pad, of
*Analoge sticks*. Een App die Windows draait, vraagt *Wat wil je doen?* en biedt aan om Windows te starten, het te
installeren, DOS te starten of Windows te verwijderen. Mag je in een App een toets instellen, dan vraagt hij
*Druk op een van de knoppen.*

![De game-instellingen van een App](../images/en/app-game-settings.jpg)

Een Windows-programma dat de PE-runner uitvoert (een PE-app, sectie 3.3), praat met je via de eigen schermen van
AutoBleem: een bericht dat het wil tonen, verschijnt als *Bericht*, en een vraag met keuzes als *Kies een optie*,
allebei met de naam van de App als titel.

![Een vraag van een PE-app, getoond als scherm van AutoBleem](../images/en/pe-dialog.jpg)

### 3.9a Een schijf in een USB-station

Je kunt een gewoon USB-cd/dvd-station aansluiten op de console, een Raspberry Pi of een pc die vanaf de
AutoBleem-stick is opgestart, en meteen spelen vanaf een originele PlayStation-schijf - zonder iets te kopiëren. Een
schijf die je erin legt, verschijnt in de launcher als gewoon nog een game. Op Windows werkt dit niet.

**Een schijf naar de stick kopiëren.** Wil je de game altijd bij de hand hebben, zonder de schijf, druk dan op
Square (*Schijf kopiëren*). AutoBleem vraagt eerst of de game gekopieerd moet worden en hoeveel ruimte dat kost, en
zet hem dan als één CHD-bestand in de map `Games` (een game op meerdere schijven krijgt er ook een `.m3u`-bestand bij,
zodat wisselen van schijf in de game werkt). Tijdens het kopiëren zie je de snelheid en de resterende tijd, en met
*Afbreken* stop je ermee. Is het klaar, dan staat de game op de plank zoals alle andere. AutoBleem kopieert geen game
die al in `Games` staat, en ook geen game waar geen ruimte voor is - dan zegt hij hoeveel ruimte hij nodig heeft.
Ook een bekraste schijf kan gekopieerd worden: de stukken die niet te lezen waren, worden met nullen gevuld, en
AutoBleem vertelt je hoeveel het er waren. Zo'n kopie werkt misschien wel, misschien niet.

Square biedt de kopie aan voor elke PlayStation-gameschijf in de schijfweergave, ook voor een schijf die de cover
databases niet kennen. Een game die de databases kennen, wordt onder zijn titel gekopieerd; kopieer bij een game op
meerdere schijven de schijven na elkaar, en de `.m3u` zet ze op volgorde, schijf 1 eerst. Een schijf die de databases
niet kennen, krijgt in plaats daarvan zijn serienummer als naam, wordt als losse schijf gekopieerd en heeft geen
hoesje op de plank. Het kopieervenster, *Schijf wordt gekopieerd*, blijft op het scherm tot de kopie klaar is of
gestopt - de launcher wacht zolang - en toont de snelheid als veelvoud van een gewoon cd-station. Mislukt de kopie,
dan vertelt AutoBleem je waarom.

![Een schijf kopiëren](../images/en/disc-copy.jpg)

**Spelen vanaf de schijf.** Leg je een schijf in het station, dan opent de **schijfweergave** vanzelf zodra de schijf
is ingelezen. Je ziet het hoesje van de schijf - uit de cover databases, of online opgehaald - met het serienummer en
de titel, en Cross start de game. Een PS1-game die je vanaf de schijf speelt, bewaart zijn hervattingspunten en saves
in een eigen map, zodat je net als bij een game op de stick kunt stoppen en later verder kunt gaan. Na de game, of
nadat je in de opties of de instellingen van een extensie bent geweest, kom je terug in de schijfweergave. Verlaat je
hem met Circle om door je andere games te bladeren, dan blijft de schijf in het station en brengt Circle op de plank
de weergave terug; op een lege plank opent R1 (*Schijf*) hem ook. Op een plank met games doet R1 gewoon zijn vaste
werk: springen tussen beginletters. Haal je de schijf eruit, dan sluit de schijfweergave.

![De schijfweergave](../images/en/disc-view.jpg)

**De stationschip** bovenaan het scherm laat zien wat het station aan het doen is, zodat je weet of je moet wachten.
Zonder aangesloten station zie je niets. Een station zonder schijf toont een gedimd schijfpictogram. Terwijl een
schijf wordt ingelezen, knippert het pictogram en staat er *Schijf wordt gelezen...*, en zodra hij klaar is, licht het
pictogram op met de titel van de schijf. Leg je een schijf in die geen PlayStation-game of audio-cd is, dan zegt de
chip *Dit is geen PlayStation-schijf*, en kan het station de schijf op dat moment niet lezen, dan staat er
*De schijf kan nu niet gelezen worden*.

![De stationschip](../images/en/disc-chip.jpg)

**Audio-cd's.** Het station speelt ook muziek-cd's af. Een audio-cd opent de **cd-speler** in plaats van de
schijfweergave. Die toont de schijf als *Audio-cd* met de lijst van nummers en de totale speelduur, en de regel
eronder noemt het gekozen nummer en zegt of herhalen en shuffle aan staan. Een schijf die de speler niet kan afspelen,
is gemarkeerd met *Deze schijf kan niet worden afgespeeld*. Dit zijn de knoppen:

| Knop | In de cd-speler |
|---|---|
| Cross | Speelt het gekozen nummer af. |
| Start | Pauzeert de muziek, en zet hem weer aan. |
| Square | Stopt de muziek. |
| L1 / R1 | Naar het vorige of het volgende nummer. |
| L2 / R2 | Spoelt terug of vooruit door het nummer, vijf seconden per keer. |
| Triangle | Verandert wat er herhaald wordt: niets, de hele schijf, of het huidige nummer. |
| Select | Zet shuffle aan of uit, zodat de nummers in willekeurige volgorde spelen. |
| Circle | Verlaat de cd-speler. |

![De cd-speler](../images/en/cd-player.jpg)

**LibCrypt-schijven.** Sommige PlayStation-games, de meeste uit Europa, hebben een kopieerbeveiliging die LibCrypt
heet. Om ze te draaien, heeft de emulator een klein `.sbi`-bestand met de gegevens van die beveiliging nodig.
AutoBleem haalt dat bestand zelf van de site voordat zo'n schijf speelt en als je hem kopieert, en het wordt samen
met de game gekopieerd. Daarvoor is een netwerk nodig: op een Raspberry Pi of een pc het netwerk dat hij al heeft,
op de console de wifi die je in PSC-Bios hebt ingesteld.

Voor een schijf in het station hebben sommige instellingen van een game geen zin; de game-editor maakt die regels dan
grijs (sectie 3.7).

### 3.10 Games toevoegen

AutoBleem vindt je games zelf, zolang ze op de juiste plek staan. In deze sectie lees je waar elke soort hoort, zodat
elke scan ze met naam en hoesje op de plank zet.

**PS1-games** horen in de map `Games`, **één map per game**, genoemd naar de game. Je kunt games ook in eigen mappen
groeperen; elke zo'n map wordt een groep in de setkiezer (sectie 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                a folder of games: a group of its own in the set picker
    Klonoa/                   Klonoa.pbp
```

AutoBleem leest de gangbare formaten voor schijfimages: `.cue` met de bijbehorende `.bin` (of `.img`), `.pbp`, `.chd`
(ook met zstd gecomprimeerd), `.iso` en `.ecm`, dat de scan voor je decodeert. Een gezipte game werkt ook: de
processor **Unzip** pakt hem uit voordat de scan hem leest (sectie 3.14).

Je hoeft niet netjes te zijn. Een game op meerdere schijven hoort in één map met al zijn schijven, maar kopieer je
mappen met namen als `Game (Disc 1)`, `Game (Disc 2)` enzovoort, dan voegt de scan ze samen tot één map `Game`.
Games die je als losse bestanden direct in `Games/` zet, krijgen van de scan ook elk een eigen map.

**Namen en hoesjes** komen vanzelf. De scan leest het serienummer van elke schijf en haalt de titel, de uitgever, het
jaar, het aantal spelers en de regio uit de PlayStation-database van RetroArch of uit de cover databases. Wil je een
eigen hoesje, zet dan een PNG of JPEG met dezelfde naam naast het image van de game. Zonder eigen hoesje komt het
artwork uit de cover databases of, met RetroArch geïnstalleerd, uit de thumbnailset van libretro; op een Raspberry Pi,
een pc of Windows wordt een ontbrekend hoesje online opgehaald (Opties → *Hoesjes online ophalen*). Doet de scan iets
verkeerd, verbeter het dan in de game-editor en zet *Gegevens vergrendelen* aan, zodat de volgende scan je wijziging
laat staan.

**Games van andere systemen** horen onder `RetroArch/roms/`, **één map per systeem, met de naam die de databases van
RetroArch ervoor gebruiken** - bijvoorbeeld `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo
Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` of `FBNeo - Arcade Games` (of
`Arcade`). De mappen worden voor je aangemaakt, en de ROM's mogen gezipt blijven. Op een Raspberry Pi, een pc of
Windows leest de scan ze zelf in en schrijft hij de afspeellijsten van RetroArch. Een consolestick kan dat niet in
zijn eentje; daar start je **UpdateRoms** op de pc (hoofdstuk 5).

**Apps** horen onder `Apps/<name>/`, elk met een `app.ini` - de naam, het pictogram en wat er gestart moet worden - en
een `run.sh`.

**Pakketten.** Sommige Apps zijn game-engines: ze hebben de gegevens nodig van een game die je zelf bezit voordat ze
die kunnen spelen. Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital,
DOS-games en meer werken zo. Zet de bestanden van de game in een map `Packages` op de stick, één map per game -
bijvoorbeeld `Packages/Doom/DOOM2.WAD` - en AutoBleem herkent ze aan de hand van een tabel die erbij zit
(`rc/packages.ini`). In een map die hij herkent, zijn losse gamebestanden elk een pakket op zich. AutoBleem leest je
bestanden alleen en verandert er nooit iets aan. Een pakket kan ook uit de Store komen (sectie 3.13).

Waar de launcher hem toont, staan in de regel *Pakketten* van het tabblad Apps (sectie 3.3) de gamegegevens die
gevonden zijn. Cross op een item opent zijn **Package info**: wat er in de gegevens zit, een beschrijving, waar de
bestanden staan en waar ze vandaan komen (je eigen bestanden, de Store, een mod, of bestanden die in een App
meekomen), of het shareware of gratis is, en welke geïnstalleerde App het draait. Kan niets wat je hebt
geïnstalleerd het draaien, dan zegt de info je dat.

Start je een engine-App, dan zoekt AutoBleem naar gamegegevens die hij kan draaien. Is er één set gegevens, dan start
de game meteen. Zijn het er meer, dan vraagt een lijst (*Kies gamedata*) welke je wilt spelen, en staat hij op de
set die je de vorige keer koos. Is er geen enkele, dan vertelt AutoBleem je welke gegevens de App nodig heeft en waar
je ze moet zetten, en start er niets.

**Je eigen games.** Herkent AutoBleem bepaalde gegevens niet, dan staat er in hun Package info *Niet herkend. Is dit
een game, zie dan de handleiding: Je eigen games.* De tabel kent alleen de games waarvoor hij gemaakt is. Voor een
andere game schrijf je er zelf een regel voor in een eigen `packages.ini` in de map `Packages`: AutoBleem leest de
jouwe eerst, dus jouw regels gaan voor.

![De pakketkiezer, waar je kiest met welke gamegegevens je start](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Eén deel scannen.** Heb je maar games aan één set of map toegevoegd, dan kan *Games opnieuw scannen* alleen dat
deel scannen. Dat gaat sneller dan alles scannen, en de bubbel verdwijnt zodra hij klaar is.

**Thema's** horen onder `Themes/<name>/`, met hun `theme.json` en hun afbeeldingen - of zet de zip van het thema zoals
hij is in `Themes/`.

### 3.11 De PS1-BIOS

De BIOS is het eigen opstartprogramma van de PlayStation, en met de echte speelt de emulator games het meest
getrouw. Op een **PlayStation Classic** hoef je niets te doen: de emulator gebruikt de BIOS van de console zelf. Op
een **Raspberry Pi, een pc en Windows** zet je je eigen PS1-BIOS-bestanden in `System/Bios/`: `romw.bin` (de
Amerikaanse/Europese SCPH-5501/5502) en `romJP.bin` (de Japanse SCPH-5500, voor Japanse games). De
installatieprogramma's vullen die aan uit de BIOS-pakketten van RetroArch, tenzij je eigen bestanden er al staan -
die vervangen ze nooit. Zonder die bestanden draait de emulator op zijn ingebouwde HLE-BIOS, een vervanger die veel
games accepteren en sommige niet. Start een game niet, kijk dan eerst of de BIOS ontbreekt.

### 3.12 Updates

AutoBleem houdt zichzelf up-to-date, zodat je nieuwe functies en verbeteringen krijgt zonder iets opnieuw te
installeren. Als de launcher start, en daarna eens per dag, kijkt hij op de site of er een nieuwe versie is op zijn
**kanaal**. Het kanaal kies je in Opties → *Updates*: `release`, `testing`, `nightly`, of `off` als hij helemaal niet
moet kijken. Wil je niet wachten op de dagelijkse controle, dan kijkt *Software-update* in het systeemmenu meteen.

Is er een nieuwe versie, dan vraagt AutoBleem wat je wilt doen. *Nu bijwerken* downloadt en installeert hem, wat een
paar minuten duurt. *Herinner me morgen* vraagt het over een dag opnieuw, en *Deze versie overslaan* vraagt niet meer
naar deze versie. Wat je ook kiest, je games, saves en instellingen blijven altijd bewaard; na een update scant de
launcher je games nog een keer. Het kanaallabel in de linkerbovenhoek (sectie 3.1) laat zien welke versie je hebt.

Hoe de update wordt geïnstalleerd, hangt af van het apparaat:

- Op een **Raspberry Pi** en de **pc-stick** draait na de download het installatieprogramma opnieuw, met hetzelfde
  voortgangsscherm als bij de eerste start, en het biedt ook een nieuwere RetroArch aan. Daarna is de launcher
  terug.
- Op **Windows** opent de gedownloade setup, die de nieuwe versie installeert en de nieuwe launcher start.
- Op een **PlayStation Classic** kan alleen een console met de **AutoBleem-kernel** (ABFlashKit, sectie 6.2) en een
  **wifinetwerk** dat in PSC-Bios is ingesteld (sectie 6.1) zichzelf bijwerken - een console in de originele staat
  heeft geen netwerk, dus daar kijkt de launcher niet. Na *Nu bijwerken* sluit de launcher, en de AutoBleem-afbeelding
  blijft op het scherm staan terwijl de stick wordt bijgewerkt, wat een paar minuten duurt; daarna start de nieuwe
  launcher. Zonder netwerk meldt *Software-update* *Niet verbonden*. Elke consolestick kun je ook vanaf een pc
  bijwerken met `AutoBleemInstaller.exe` (sectie 2.1).

### 3.13 Extensies en de AutoBleem Store

**Extensies** voegen nieuwe dingen toe aan de launcher - eigen schermen en functies - zonder AutoBleem zelf te
veranderen. De AutoBleem Store en PSC-Bios zijn extensies. Een extensie staat in `Extensions/<name>/` op de stick (op
een Raspberry Pi op zijn datapartitie, op Windows in de datamap); om er een te installeren, pak je zijn zip daar uit.

Om ze te bekijken, open je het systeemmenu (**L2 + R2**) en kies je *Extensies*. De extensies van het AutoBleem-team
staan bovenaan, en alle andere volgen onder *Extensies van derden*. Cross start de gekozen extensie, en Triangle zet
hem uit, of weer aan. PSC-Bios op de console is de uitzondering: daarmee stel je de wifi, de controllers en de klok
in, dus daar kan hij niet uit. Kan een extensie niet draaien, dan zegt haar regel waarom - ze heeft een netwerk nodig
en dat is er niet, ze is niet voor dit systeem gemaakt, ze is voor een andere versie van AutoBleem gemaakt en heeft
een update nodig, of ze kon niet geladen worden. Brengt een extensie ooit de launcher tot stilstand, dan schakelt
AutoBleem haar uit en meldt de lijst dat; je kunt haar hier weer aanzetten.

![De lijst met extensies](../images/en/extensions.jpg)

**De AutoBleem Store** is de eerste extensie: een plek om Apps en games te bekijken en ze met één druk op de knop te
installeren, op elk systeem waar AutoBleem op draait. Een PlayStation Classic heeft er de AutoBleem-kernel voor
nodig, want de wifi komt met de kernel mee. Je opent de Store vanuit het snelmenu (*Store*, sectie 3.4). Hij heeft
vier tabbladen, en met L1 en R1 wissel je ertussen.

De tabbladen **Apps** en **Games** tonen wat de bronnen aanbieden, elk item met zijn afbeelding, zijn versie, zijn
grootte en het kleine pictogram van de bron waar het vandaan komt. Op het tabblad Apps staan ook PE-apps, met hun
licentie en bron, en pakketten met gamegegevens (sectie 3.10). Wat je al hebt geïnstalleerd, heeft een badge
*Installed*. De hintbalk toont de knoppen die voor het gekozen item gelden:

| Knop | Op de tabbladen Apps en Games |
|---|---|
| Cross | Installeert het item - of werkt het bij, probeert het na een mislukking opnieuw, of annuleert een download die wacht of loopt. |
| Triangle | Verwijdert iets wat de Store heeft geïnstalleerd. |
| Square | Ververst de lijsten vanuit de bronnen. |
| L2 / R2 | Springen naar de vorige of volgende beginletter. |
| Select | Toont één bron tegelijk, als je wilt zien wat één bron aanbiedt. |
| Start | Zoekt in de titels. |

Afbeeldingen worden bewaard zodra ze geladen zijn, zodat de lijsten de volgende keer snel verschijnen, en een
afbeelding die niet laadde, kan opnieuw geprobeerd worden.

Het tabblad **Downloads** toont wat er gedownload wordt, wacht, mislukt of geïnstalleerd is, met een voortgangsbalk die
gelijkmatig vooruitgaat. Je hoeft er niet naar te blijven kijken: downloads lopen op de achtergrond door, ook als je
de Store verlaat, en als je ergens anders in de launcher bent, toont een bubbel de lopende download met zijn snelheid
en de resterende tijd (bijvoorbeeld `1.4 MB/s · 0:42`). Een game starten of het apparaat uitzetten pauzeert ze alleen,
en een gestopte download gaat verder waar hij gebleven was. Valt het netwerk weg, dan staat er bij het item *Waiting
for the network* en gaat het verder waar het was zodra het netwerk terug is; na 30 minuten zonder netwerk geeft het
op. Downloads van meer dan 2 GB werken op elk platform, ook op de 32-bits versies. Een game die je installeert,
verschijnt na de volgende scan op de plank, met de afbeelding uit de Store als hoesje.

Het tabblad **Sources** toont waar de lijsten vandaan komen, elk met zijn pictogram: de eigen catalogus van AutoBleem,
elke TSV-lijst die in `System/Extensions/store/sources/` is gezet, en de adressen die je zelf toevoegt met *Add a
source URL*. Cross op een bron die je zelf hebt toegevoegd, laat je hem een andere naam geven, zijn adres wijzigen,
hem tussen `http://` en `https://` laten wisselen of hem verwijderen.

![Het tabblad Apps van de Store](../images/en/store-apps.jpg)

![Het menu van een bron die je zelf hebt toegevoegd](../images/en/store-source-menu.jpg)

Wat de eigen catalogus van AutoBleem aanbiedt, staat ook op de downloadsite, op
`https://autobleem.retromenele.pl/store/`. Een bron die je zelf toevoegt, is een ander verhaal: **jij bent
verantwoordelijk voor wat er in de bronnen staat die je toevoegt.**

**Je eigen games op je eigen netwerk.** Staan je PS1-games op een andere computer in huis, dan kan `abstored`, de
LAN-server van de Store, ze via je netwerk aan de Store aanbieden, zodat je ze installeert zoals elk ander item. Hij
draait op elke Linux-machine - een Raspberry Pi, een thuisserver - en leest de map alleen, zonder er iets aan te
veranderen. Start hem met `abstored <games folder>` en open daarna `http://<that machine>:8124/` in een browser: de
pagina laat zien wat hij aanbiedt en welke problemen hij heeft gevonden. Voeg in de Store
`http://<that machine>:8124/store.tsv` toe als bron. Kant-en-klare programma's voor Linux en Windows staan op de
pagina van de Store, op het tabblad **LAN server**, en `INSTALL-linux.md` (`ext_store/server/` in de broncode) legt
uit hoe je hem als service instelt. **LAN Share** (sectie 5.2) zet games en schijven vanaf een pc op zo'n server.

### 3.14 Scanprocessors

Scanprocessors bereiden je games voor voordat AutoBleem ze inleest. Een processor is een klein programma dat elke scan
als eerste uitvoert. Hij kan een formaat dat AutoBleem niet leest, omzetten naar een formaat dat hij wel leest - een
gezipte game uitpakken, bijvoorbeeld - of de gegevens van een game veranderen, zoals een vertaalpatch toepassen.
Processors staan in `System/Processors/<name>/` op de stick (op een Raspberry Pi op zijn datapartitie, op Windows in de
datamap); om er een te installeren, pak je zijn map daar uit, en de volgende scan voert hem uit.

**Unzip zit bij AutoBleem.** Hij pakt gezipte PS1-games in `Games/` uit voordat de scan ze leest, en gezipte ROM's een
voor een; arcadesets blijven gezipt, want zo lezen de arcadecores ze. Werk je AutoBleem bij, dan wordt Unzip ook
bijgewerkt, en heb je hem uitgezet, dan blijft hij uit.

Een processor doet zijn werk één keer: heeft hij een game behandeld, dan wordt hij er pas weer op losgelaten als de
game verandert. Terwijl een processor bezig is, toont de bubbel rechtsboven wat hij doet, en een waarschuwing of een
fout verschijnt op de regel eronder; `processors.log` in de map met logbestanden heeft de details. Start je een game
of RetroArch, dan stopt een processor die bestanden verandert, zodat de game het apparaat voor zich alleen heeft; de
volgende scan maakt het werk af.

Om ze te beheren, open je het systeemmenu (**L2 + R2**) en kies je *Scanprocessors*. Je ziet ze in de volgorde waarin
ze draaien, met één tabblad voor de PS1-games en één voor de ROM's; met L1 en R1 wissel je van tabblad. De volgorde
doet ertoe: een processor die uitpakt, moet vóór een processor komen die het uitgepakte patcht.

| Knop | In Scanprocessors |
|---|---|
| Square | Pakt de gekozen processor op, zodat Omhoog en Omlaag hem naar zijn nieuwe plek verplaatsen; Square zet hem weer neer. |
| Cross | Zet de processor uit, of weer aan. |
| Triangle | Laat de processor bij de volgende scan opnieuw naar elke game kijken, ook naar de games die hij al heeft behandeld. |
| Circle | Gaat terug, en start een scan als je iets hebt veranderd. |

Een processor die voor een ander apparaat is gebouwd, blijft grijs in de lijst staan, zodat je ziet dat hij er is maar
hier niet draait.

![Scanprocessors](../images/en/processors.jpg)

Wil je zelf een processor schrijven, dan legt de pagina van Unzip, `https://github.com/autobleem2/proc_unzip`, alles
uit wat een processor moet doen, en `tools/proc_check.py` in de broncode van AutoBleem controleert de jouwe voordat je
hem deelt.

<!-- pagebreak -->

## 4. Schermen

### 4.1 Game Manager

In de Game Manager ruim je je PS1-verzameling op. Gebruik hem als je een game die je niet meer speelt wilt
verwijderen, de instellingen van een game wilt openen zonder hem eerst op de plank te zoeken, of AutoBleem alle
hoesjes opnieuw wilt laten ophalen. Je opent hem vanuit het systeemmenu (L2 + R2, *Game Manager*). Zolang er een
scan loopt, is hij grijs en wacht hij tot de scan klaar is.

Het scherm heet *Game manager - Selecteer game*. Links zie je al je PS1-games als een lijst met titels op
alfabetische volgorde; rechts het hoesje van de gekozen game met de uitgever, het jaar, het serienummer en de map
waar hij in staat. Rechtsboven staat hoeveel ruimte er nog vrij is op het station, zodat je ziet hoeveel ruimte een
verwijdering je oplevert. Omhoog en Omlaag lopen door de lijst, L2 / R2 bladeren een pagina verder en L1 / R1
springen naar de eerste of de laatste game.

- **Cross** opent de gekozen game in de game-editor - dezelfde editor als het pictogram Game op de plank
  (sectie 3.7). Verlaat je hem, dan sta je weer op dezelfde game in de lijst.
- **Square verwijdert de game.** AutoBleem vraagt het eerst en verwijdert dan de hele map van de game. Worden de
  savestates en de memory card van de game door geen enkele andere game gebruikt, dan stelt hij nog een tweede vraag:
  of die ook weg moeten. Zeg nee als je de game later misschien met je saves terug wilt.
- **Triangle verwijdert alle hoesjes** (PNG of JPEG) die naast je games staan, na een vraag. Handig als je hoesjes
  hebt verzameld die je niet mooi vindt: de volgende scan haalt de hoesjes dan weer uit de cover databases.

Aan het eind van de lijst, na de games, zie je misschien mappen met het label *Niet toegevoegd*. Dat zijn mappen in
`Games` die de scan wel heeft bekeken maar waar hij geen game van kon maken. Kies er een, en rechts lees je waar hij
staat en waarom hij niet is toegevoegd - een ontbrekend cue-bestand bijvoorbeeld (hoofdstuk 7). Square verwijdert zo'n
map na een vraag. Verlaat je het scherm met Circle nadat je iets hebt veranderd, dan scant AutoBleem de games opnieuw.

![De Game Manager: links de lijst met games, rechts het hoesje en de gegevens van de gekozen game](../images/en/game-manager.jpg)

### 4.2 Hardware-informatie

Hardware-informatie is de pagina waar je kijkt als je wilt weten wat je apparaat is en wat het ziet: hoeveel ruimte
er nog op de stick is, welk netwerkadres het heeft, welke beeld- en geluidsstuurprogramma's het gebruikt en welke
controllers er zijn aangesloten. Op elk platform is het dezelfde pagina, ook op de console. Je opent hem vanuit het
systeemmenu (L2 + R2, *Hardware-informatie*); met Circle ga je terug naar het systeemmenu.

De pagina toont het systeem, de hardware, de opslag met de vrije ruimte, de netwerkadressen, de beeld- en
geluidsstuurprogramma's en de aangesloten controllers. Hij leest alles elke seconde opnieuw in, dus je kunt hem open
laten staan terwijl je een controller of een kabel aansluit en de verandering zien verschijnen. Hij laat alleen dingen
zien - om het netwerk of een controller in te stellen, gebruik je *Netwerk & controllers* (PSC-Bios, hoofdstuk 6).

Het deel over controllers beantwoordt de vraag "welke controller is welke speler?". De eerste twee controllers staan
er als *Speler 1* en *Speler 2* - de poorten die de PS1-emulator ze geeft. Elke volgende controller staat er als
*wordt niet gebruikt door de PS1-emulator*. RetroArch verdeelt de poorten volgens zijn eigen instellingen, dus in een
RetroArch-game kan de volgorde anders zijn. Je hoeft deze pagina niet elke keer te openen: zodra er een controller
wordt aangesloten of losgehaald, laat de launcher even zien welke controller nu Speler 1 is en welke Speler 2.

![Hardware-informatie: de gegevens van het apparaat en de aangesloten controllers](../images/en/hardware-info.jpg)

### 4.3 Het knoppenoverzicht

Weet je ergens niet meer wat een knop doet, druk dan op **Triangle** op de plank. Het knoppenoverzicht toont alle
knoppen van alle schermen op één pagina, zodat je het kunt opzoeken zonder de launcher te verlaten. Is er een
USB-toetsenbord aangesloten, of is er een gebruikt, dan staat in een kolom *Toetsenbord* bij elke knop de bijbehorende
toets.

Het overzicht herinnert je ook aan het enige wat je bij elke game moet onthouden: hoe je eruit komt. Houd Select +
Start, of Home, 2 seconden ingedrukt om terug te gaan naar AutoBleem; kort drukken opent in plaats daarvan het menu
van de emulator.

![Het knoppenoverzicht: de knoppen van elk scherm, met de toetsen van het toetsenbord ernaast](../images/en/button-guide.jpg)

### 4.4 Het schermtoetsenbord

Moet je in AutoBleem iets typen - de naam van een set memory cards, de titel van een game, een wifiwachtwoord, het
adres van een bron in de Store - dan verschijnt steeds hetzelfde schermtoetsenbord, zodat je alleen met de controller
kunt typen. Het is ingedeeld zoals het toetsenbord van een telefoon. Naast de letters heeft het een pagina met
symbolen, met `/ \ : ? & = % @ #` en de rest van wat je voor een adres of een wachtwoord nodig hebt, en twee pagina's
met letters met accenten. In de onderste rij zitten Shift, de toets die van pagina wisselt, de spatie, Backspace en
Bevestigen.

Ga met de richtingsknoppen over de toetsen en druk op **Cross** om de toets onder de cursor te typen. **Triangle**
wist een letter en **Square** typt een spatie. **L1** is Shift; druk twee keer voor Caps Lock. **R1** gaat naar de
volgende pagina met toetsen, en **L2 / R2** verplaatsen de cursor in de tekst. **Start** bevestigt wat je hebt getypt
en **Circle** annuleert. Is er een USB-toetsenbord aangesloten, dan kun je daar altijd op typen: Enter bevestigt en
Esc annuleert.

![Het schermtoetsenbord](../images/en/keyboard.jpg)

### 4.5 Virtueel gamepad

Apps - de programma's in de set Apps, zoals Doom of Quake - lezen je controller niet zelf. Een klein hulpprogramma,
de daemon voor de virtuele gamepad, leest de echte controllers en geeft elke App een controller die hij begrijpt. Deze
pagina laat zien welke controllers dat hulpprogramma ziet en hoe het ze leest. Kijk hier als een App niet op je
controller reageert, of als de knoppen door elkaar zitten. Je opent hem vanuit het systeemmenu (L2 + R2,
*Virtueel gamepad*); met Circle ga je terug naar het systeemmenu.

Onder *Gamepads die de daemon ziet* staat elke controller met een nummer en zijn naam. Ernaast lees je drie dingen: of
het hulpprogramma de controller kon openen (*verbonden*) of niet (*niet leesbaar*); het stuurprogramma waarlangs de
controller binnenkwam; en waar zijn knopindeling vandaan komt - *uit de controllerdatabase* betekent dat de
controller bekend is en zijn knoppen zitten waar ze horen, *geraden door de daemon* betekent dat hij niet bekend is en
het hulpprogramma een zo goed mogelijke gok heeft gedaan. Voelen de knoppen in een App verkeerd aan, dan is een
geraden indeling de waarschijnlijke oorzaak.

Het hulpprogramma draait alleen zolang er een App draait; de pagina vraagt het daarom één keer, als hij opent. Sluit je
een controller aan terwijl de pagina open is, druk dan op **Cross** (*Opnieuw zoeken*) om het opnieuw te vragen. Op
Windows bestaat zo'n hulpprogramma niet, en daar zegt de pagina *Niet in deze build*.

![Virtueel gamepad: de controllers die het hulpprogramma van de Apps ziet](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. Op de pc

### 5.1 UpdateRoms - een consolestick verversen

Op een Raspberry Pi, een pc of Windows zet de scan van de launcher je RetroArch-games zelf in lijsten en haalt hij
hun hoesjes op. De PlayStation Classic kan dat niet, want die heeft geen eigen netwerk. **UpdateRoms** doet dat werk
in plaats daarvan op je Windows-pc: het gebruikt het netwerk van de pc maar schrijft alles met de paden die de
console verwacht. Steek je de stick terug, dan start de console en staat alles klaar. Start het telkens als je
RetroArch-games op een consolestick hebt toegevoegd of verwijderd.

1. Kopieer je ROM's naar de stick, onder `RetroArch/roms/<system>/` (sectie 3.10). De mapnamen moeten de namen uit de
   databases van RetroArch zijn; de gangbare heeft het installatieprogramma al aangemaakt.
2. Start **`UpdateRoms\UpdateRoms.exe` vanaf de stick** - het installatieprogramma heeft het daar neergezet. Het zoekt
   zelf uit op welke stick het staat. Terwijl het bezig is, zie je een regel die zegt wat het doet, een voortgangsbalk
   en een logboek.
   - Heeft de stick nog geen RetroArch-database, dan downloadt het eerst de databasebundel van RetroArch. Daarmee
     herkent het vervolgens elke ROM, zodat een game die de database kent zijn juiste naam krijgt.
   - Het schrijft per systeem één afspeellijst in `RetroArch/bin/playlists/`, met de paden van de console. Wat
     RetroArch zelf aan die lijsten heeft toegevoegd, blijft staan.
   - Voor elke ROM zonder hoesje haalt het er een op van de thumbnailservers van libretro, in
     `RetroArch/bin/thumbnails/`.
3. Werp de stick veilig uit en steek hem terug in de console. Het tabblad RetroArch van de setkiezer toont nu elk
   systeem waar games voor zijn.

Je kunt het zo vaak starten als je wilt: een map waarin niets veranderd is, wordt overgeslagen, dus een tweede keer
gaat snel. Gaat er iets mis, dan staat het logboek in `System/Logs/updateroms.log` op de stick. Een kaart van een
Raspberry Pi in een kaartlezer kun je op dezelfde manier verversen, met `UpdateRoms.exe <drive> --target rpi`, al doet
een Pi dat zelf als hij een netwerk heeft.

### 5.2 LAN Share - je games en schijven op de server in je netwerk

De Store kan games installeren vanaf een server in je eigen thuisnetwerk (sectie 3.13). **LAN Share** is het
Windows-programma waarmee je die server vanaf je pc vult: het zet de PS1-games die je op de pc hebt op de server, en
het kan een PS1-schijf in het cd/dvd-station van de pc inlezen en die er ook op zetten. De server is een `abstored`
die op een Raspberry Pi, een NAS of een andere pc draait. Staat een game er eenmaal op, dan kan de Store op de
console, de Pi of de pc hem daarvandaan installeren.

`LanShare.exe` vind je op de pagina van de Store, op het tabblad **LAN server**. Installeren hoeft niet: start het
gewoon, en het bewaart zijn instellingen in `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![Het venster van LAN Share: links de games op de server, rechts de games op deze pc](../images/en/lanshare.jpg)

1. **Verbind met de server.** Vul zijn adres in zoals de Store het kent, `http://<its address>:<port>`, en druk op
   **Connect**. Links verschijnen de games die al op de server staan, en de problemen die zijn eigen scan heeft
   gevonden. Om games op de server te zetten, heeft LAN Share een van twee manieren nodig om erbij te komen:
   - **Share** is de gamemap van de server zoals die in je netwerk gedeeld wordt (Samba), bijvoorbeeld
     `\\raspberrypi\games`. LAN Share kopieert de games erin en vraagt de server te scannen; de server zelf leest zijn
     map nog steeds alleen.
   - **Token** is voor een server die met `--allow-uploads` is gestart. Vul zijn token in - de server toont het bij het
     starten en bewaart het in `<state>/upload-token`. LAN Share uploadt dan via HTTP, en een upload die halverwege
     stopt, gaat verder waar hij gebleven was.
2. **Zet de games van je pc erop.** Kies de map waar je games in staan (één map per game), vink de games aan die je
   wilt en druk op **Publish the ticked games**. **On the server** vertelt je of de server een game al heeft - hij
   vergelijkt het serienummer, of de titel als er geen serienummer is - en een game die de server al heeft, wordt nooit
   twee keer verstuurd. **Tick those not on the server** vinkt alle andere voor je aan.
3. **Zet een schijf erop.** Leg een PS1-schijf in het station van de pc en druk op **Read a disc and publish it**. LAN
   Share leest de hele schijf in als `.bin` + `.cue`, genoemd naar de titel van de game. Bij een LibCrypt-game schrijft
   het ook het `.sbi`-bestand, als het station het subkanaal kan lezen. Heb je de databases gekozen (zie hieronder),
   dan controleert het de kopie aan de hand van de bekende goede dump. Daarna zet het de game op de server. Vink bij
   een game op meerdere schijven eerst **The game has more than one disc** aan: LAN Share vraagt je dan om elke
   volgende schijf en zet ze samen als één game op de server.
4. **Haal games van de server.** Selecteer ze en druk op **Remove from the server...**. Er wordt niets gewist: elke
   game gaat naar een map `.removed` naast de games van de server, en zet je hem terug, dan is hij er weer.

De **Databases** zijn optioneel. Wijs je LAN Share de map met hoesjes van AutoBleem (`coversU/P/J.db`) en
`Sony - PlayStation.rdb` van RetroArch aan, dan gebruikt het die om de games een naam te geven en om een ingelezen
schijf te controleren.

Wil je liever niets kopiëren, vink dan **Also share the games on this PC with the Store** aan (staat standaard uit):
LAN Share biedt de gamemap op je pc dan rechtstreeks aan de Store aan. De eerste keer dat je dat doet, vraagt Windows
iets over zijn firewall - sta alleen privénetwerken toe.

<!-- pagebreak -->

## 6. De consolehulpmiddelen (PlayStation Classic)

Bij een stick voor de PlayStation Classic horen twee hulpmiddelen waarmee je de console verder inricht dan hij uit de
doos kan. Allebei zien ze eruit als de rest van de launcher, in zijn thema en zijn taal, en je bedient ze met de
controller - in de gamepadwizard ook met de knoppen aan de voorkant van de console. **PSC-Bios** is een extensie die
bij het consolepakket hoort: het item *Netwerk & controllers* in het snelmenu en in het systeemmenu opent hem, en je
vindt hem ook in de lijst met extensies. **ABFlashKit** is een App, in de set Apps.

### 6.1 PSC-Bios

Met PSC-Bios verbind je het apparaat met de buitenwereld: je wifinetwerk, de tijdzone, Bluetooth-controllers, en de
knopindeling van een controller die AutoBleem niet kent. Het hoort bij het consolepakket en zit ook op een Raspberry
Pi en de pc-stick. Je opent het met *Netwerk & controllers* in het systeemmenu (of het snelmenu), of vanuit de lijst
met extensies. Is de extensie geïnstalleerd maar uitgeschakeld, dan is het item *Netwerk & controllers* grijs en
staat erbij dat hij *staat uit - zet hem aan bij Extensies*; druk er dan op Cross, en de lijst met extensies opent bij
PSC-Bios, zodat je hem weer kunt aanzetten.

Het eerste scherm geeft je een overzicht: de tijd en de tijdzone, de netwerkadapters (wifi, ethernet, Bluetooth) met
hun adressen, en elke aangesloten controller, met een opmerking of hij een knopindeling heeft. Op de console hebben
het netwerk- en het Bluetooth-deel de AutoBleem-kernel nodig (sectie 6.2); op een Raspberry Pi of de pc-stick
gebruiken ze de eigen hulpmiddelen van het systeem. De gamepadwizard werkt overal.

![PSC-Bios: het startscherm van Netwerk & controllers](../images/en/pscbios-main.jpg)

Vanuit het eerste scherm brengt één knop je naar elk onderdeel:

| Knop | Wat hij opent |
|---|---|
| Select | **Wi-Fi Network** verbindt je met je wifi (via de kernel, of via NetworkManager op een Pi of pc): typ de naam van het netwerk of kies het uit een zoekopdracht, vul het wachtwoord in, kies de stuurprogrammamodus en druk op *Apply / Restart Network*. Hier stel je ook de tijdzone in, en zodra je verbonden bent, zie je het IP-adres van de console. |
| Square | **Bluetooth Controllers** zoekt naar Bluetooth-controllers zoals de DualShock 4, zodat je een nieuwe kunt koppelen of er een kunt verwijderen die je niet meer gebruikt. |
| L1 | **DualShock 3 Pairing** verbindt je eerste DualShock 3, die daarvoor met USB aangesloten moet zijn, via de sixaxis-plug-in van de kernel. |
| R1 | **Controller Mapping** opent de gamepadwizard, die hieronder beschreven staat. |
| Triangle | **About** laat zien wat PSC-Bios is. |
| Circle | **Back** brengt je uit PSC-Bios, terug naar de launcher. |

**De gamepadwizard.** Gebruik hem als een controller in AutoBleem niets doet of zijn knoppen op de verkeerde plek
heeft. Hij toont de aangesloten controller zoals hij echt is - elke as, knop en hat als getal - en een afbeelding van
een DualShock die oplicht als je drukt. Omdat je de controller die je test nog niet kunt vertrouwen, bedien je de
wizard met de **knoppen aan de voorkant** van de console: **RESET** gaat naar de volgende controller, **OPEN** start
het toewijzen en **POWER** annuleert of verlaat de wizard. Tijdens het toewijzen vraagt de wizard om de ene knop na de
andere: druk op de knop die op de afbeelding oplicht, of op OPEN als je controller zo'n knop niet heeft. Een korte
druk wordt gewoon toegewezen.

Je kunt de wizard ook vanaf de controller verlaten: houd Circle 2 seconden ingedrukt - een balk loopt vol en onderaan
staat *Hold 2 s: Exit*. Zolang de controller nog geen knopindeling heeft, doet elke knop die je 2 seconden ingedrukt
houdt hetzelfde (*Hold any button 2 s: Exit*). Op een toetsenbord nemen Esc, de spatiebalk en Enter de plaats in van
POWER, RESET en OPEN.

Aan het eind wordt de nieuwe knopindeling in gebruik genomen, zodat je hem kunt uitproberen, en OPEN bewaart hem
onder een naam die je zelf kiest. Vanaf dan laadt de launcher hem elke keer.

![PSC-Bios: de wizard voor de knopindeling van controllers](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - de AutoBleem-kernel

De AutoBleem-kernel vervangt de eigen Linux-kernel van de console, en hij is optioneel. Je wilt hem als je meer uit
de console wilt halen: hij geeft hem een klok die werkt, laat USB-wifi- en Bluetooth-dongles werken (voor PSC-Bios en
Bluetooth-controllers), en voegt de ondersteuning voor de knoppen aan de voorkant toe die de emulator gebruikt voor
hervattingspunten. ABFlashKit is het hulpmiddel dat hem installeert. Het maakt eerst een back-up van de console, en
het kan de console ook terugzetten naar de originele staat via het eigen herstel van Sony.

> **Dit hulpmiddel schrijft naar het flashgeheugen van de console.** Wordt het schrijven onderbroken - de stroom valt
> weg, of de stick wordt eruit getrokken - dan start de console misschien niet meer, en door een eigen kernel te
> installeren vervalt de garantie. Houd de console aan de stroom en de stick erin tot de console uit zichzelf
> herstart. ABFlashKit opent met deze waarschuwing: *I understand* gaat verder, *Quit* stopt.

![Het menu van ABFlashKit](../images/en/abflashkit-menu.jpg)

ABFlashKit kan drie dingen:

- **Flash Kernel** installeert de kernel. Staat er nog geen back-up voor herstel op de stick, dan maakt het eerst een
  back-up van de partities van de console (`LBOOT.EPB`). Het controleert de back-up en het kernelimage, schrijft de
  kernel en de systeembestanden van AutoBleem, en herstart de console. Zegt het *All done - when the screen goes
  black replace power cord*, wacht dan tot het scherm zwart wordt, trek de stroomkabel van de console eruit en steek
  hem er weer in.
- **Full backup** bewaart alle vier de partities van de console in `LBOOT.EPB`, zodat je ze later kunt terugzetten.
  Is er al een back-up, dan vraagt het eerst voordat het die overschrijft.
- **Restore Mode** is de weg terug naar de originele firmware. Het controleert of de back-up op de stick een originele
  is, zet de herstelvlag en herstart in het herstel van Sony, dat de console terugzet vanuit `LBOOT.EPB`.

Onder elke stap laat een voortgangsbalk zien hoe ver het is. ABFlashKit flasht geen console waar andere eigen
firmware op draait, zoals BleemSync of Project Eris: zet zo'n console eerst terug naar de originele staat.

**Inloggen vanaf een pc.** Ken je Linux en wil je in de console kijken, dan kun je er vanaf een pc op inloggen via een
USB-kabel. Daarvoor heb je de AutoBleem-kernel nodig; op een console in de originele staat werkt het niet.

1. Verbind de micro-USB-poort van de console met een USB-kabel met de pc. De pc ziet de console als een nieuwe
   netwerkadapter, en het adres van de console vind je in de instellingen van die adapter op de pc.
2. Log in met `ssh root@<the console's address>`. Het standaardwachtwoord is `autobleem`.

In plaats van het wachtwoord kun je een sleutel gebruiken. Zet je publieke sleutel in het bestand
`System/ssh/authorized_keys` op de stick en herstart de console: bij de volgende start wordt hij aan het account root
toegevoegd. Bijwerken of opnieuw installeren van de launcher haalt hem niet weg.

> **Het standaardwachtwoord is op elke console hetzelfde**, dus iedereen die een kabel in de jouwe kan steken, kan als
> root inloggen. Gebruik waar het kan een sleutel, en laat een console met het standaardwachtwoord niet liggen waar
> anderen erbij kunnen.

<!-- pagebreak -->

## 7. Als er iets misgaat

De meeste problemen hebben een eenvoudige oorzaak. Hieronder begint elk probleem met wat je ziet, dan waarom het
gebeurt en daarna wat je eraan doet. Wil je om hulp vragen, dan zijn de logbestanden het eerste waar iedereen om
vraagt; daarom staan die vooraan.

**De logbestanden vinden.** AutoBleem houdt zijn logbestanden in het geheugen zolang hij draait, zodat er niet de hele
tijd naar de stick geschreven wordt. Ze komen pas in `System/Logs/` op de stick, de kaart of de datamap terecht als er
iets misging: crasht de launcher, een PS1-game of RetroArch, dan worden de logbestanden bewaard in
`System/Logs/crash-<n>/` (de laatste drie crashes worden bewaard), en de launcher meldt het één keer als hij terug is.
Zit je achter een probleem aan dat geen crash is, bewaar dan alle logbestanden: zet Opties → *Diagnose* →
*Logbestanden op de stick bewaren* aan (werkt vanaf de volgende start), of maak vanaf een pc een leeg bestand
`System/Logs/keep`. *Hardware-informatie* (sectie 4.2) laat ook zien waar de logbestanden staan, en Square bewaart daar
de huidige in `System/Logs/saved-<n>/`.

Dit zijn de bestanden die je vindt:

| Bestand | Wat het je vertelt |
|---|---|
| `autobleem.log` | Wat de launcher zelf heeft gedaan. |
| `launch.log`, `pcsx.log` | Hoe een PS1-game is gestart, en wat de emulator zei terwijl hij draaide. |
| `retroarch.log` | Wat RetroArch zei terwijl het draaide. |
| `update.log` | Hoe een online update is verlopen; wordt altijd op de stick bewaard. |
| `updateroms.log` | Hoe UpdateRoms op de pc is verlopen (hoofdstuk 5); wordt altijd op de stick bewaard. |

**Een afbeelding vraagt je de stick erin te steken, of de console is gaan slapen.** AutoBleem kan zijn stick niet
vinden: er zat er geen in toen de console startte, of hij is eruit gehaald. Steek hem in een willekeurige USB-poort
(het liefst een aan de voorkant, sectie 2.1) voordat de 5 minuten om zijn, of druk op Power. Is de stick niet netjes
verwijderd, dan controleert AutoBleem hem eerst - wacht tot de voortgangsbalk klaar is.

**RetroArch meldt *RetroArch heeft een nieuwere systeembibliotheek nodig dan deze console heeft - gebruik de
RetroArch die bij AutoBleem hoort*.** Die RetroArch is gebouwd voor een nieuwer systeem dan dat van de console, en
kan daar dus niet draaien. Gebruik de RetroArch die bij AutoBleem hoort.

**Een game meldt *Deze game is beveiligd met de PSN-licentie en kan niet worden gestart*.** Games die je in het
PlayStation Network hebt gekocht, zitten vast aan hun licentie, en AutoBleem kan ze niet draaien. Daar valt niets aan
te verhelpen.

**Een game staat niet op de plank.** Meestal is zijn map niet ingedeeld zoals de scan verwacht. Controleer of elke game
een eigen map heeft en in een van de formaten uit sectie 3.10 staat. De *Game Manager* (sectie 4.1) toont na de games
de mappen die de scan heeft geweigerd, gemarkeerd met *Niet toegevoegd*, en vertelt je waarom elke map is geweigerd;
Square verwijdert zo'n map. Heb je een map verbeterd, dan voert *Games opnieuw scannen* in het systeemmenu de scan
opnieuw uit.

**Games hebben geen hoesje.** Ofwel zijn de cover databases niet geïnstalleerd - start het installatieprogramma
opnieuw met die optie aangevinkt - ofwel is UpdateRoms, voor RetroArch-games op een console, nog niet op de pc
uitgevoerd (hoofdstuk 5).

**Een controller doet niets, of zijn knoppen zitten door elkaar.** AutoBleem kent de knopindeling van die controller
niet. Wijs op een console de knoppen toe met de gamepadwizard van PSC-Bios (sectie 6.1). Op een Pi of een pc laat de
pagina Hardware-informatie (sectie 4.2) zien wat het systeem van de controller ziet; zo weet je of hij überhaupt
herkend wordt.

**Het scherm blijft zwart na een game op de console.** Het beeld van de launcher kwam niet terug toen de game afliep.
AutoBleem bouwt zijn venster zelf opnieuw op, tot drie keer toe. Blijft het scherm daarna nog zwart, houd dan de
Power-knop ingedrukt en zet de console weer aan.

**Op een Raspberry Pi** kun je achter de launcher kijken als dat nodig is: `Alt+F2` geeft je een inlogprompt op de
tweede console, en SSH staat vanaf de eerste start aan. `sudo journalctl -u autobleem` laat zien wat de service van de
launcher heeft gedaan, en `sudo systemctl restart autobleem` herstart hem. Kon de eerste start niet afgemaakt worden
omdat er geen netwerk was, dan probeert hij het bij de volgende start opnieuw.

**Op Windows** verlaat je de launcher met `Esc`. Je datamap is de map die je tijdens de setup hebt gekozen
(`Documents\AutoBleem`, tenzij je dat hebt veranderd), en de logbestanden staan in de map `System\Logs` daarin.

**De console herstart steeds opnieuw na een online update (stick geformatteerd als ext4).** Sommige mensen
formatteren de stick als ext4, het bestandssysteem van Linux, in plaats van FAT32 of exFAT. Tot de volgende release van
AutoBleem pakt een online update op zo'n stick elk bestand uit zonder de toestemming waarmee het als programma mag
draaien. AutoBleem kan dan niet starten, en de console herstart steeds opnieuw. Sticks met FAT32 of exFAT hebben hier
geen last van. Je kunt het op twee manieren oplossen.

**Oplossing A** heeft een Linux-pc nodig. Steek de stick erin en maak de programma's van AutoBleem weer uitvoerbaar.
Vervang `/media/USER/STICK` door je eigen koppelpad; de laatste regel heb je alleen nodig als RetroArch geïnstalleerd
is:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Oplossing B**: installeer de nieuwste release van AutoBleem opnieuw op de stick, zoals in sectie 2.1. Het
installatieprogramma heeft een pc nodig die de stick kan lezen. Kan hij de jouwe niet lezen, dan moet de stick eerst
geformatteerd worden, en dan wordt alles erop gewist - kopieer je games er eerst af.

> Voorkom dit door **FAT32** te gebruiken (een console in de originele staat leest alleen FAT32; exFAT heeft de
> AutoBleem-kernel nodig, hoofdstuk 6). De volgende release bewaart de toestemmingen, en AutoBleem herstelt ze bij elke
> start.

AutoBleem is vrije software (GNU GPL v3 of later) en wordt geleverd zonder enige garantie. Voor hulp en nieuws kun je
terecht op de Discord-server waarnaar het scherm Over verwijst, of op https://autobleem.retromenele.pl/.
