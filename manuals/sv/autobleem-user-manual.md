# AutoBleem 2 Användarmanual

AutoBleem 2 är en spelstartare för **PlayStation Classic** - och sedan version 2 även för en
**Raspberry Pi**, en **PC som startar från USB-sticka** och **Windows**. Den visar dina PS1-spel som en
hylla med omslag med deras skisskonst och detaljer, startar dem i den medföljande PCSX-emulatorn och
kan, när RetroArch är installerat bredvid den, även spela spel från andra system. Den här manualen
täcker installation på varje plattform, daglig användning och de verktyg som medföljer.

> Nedladdningarna för varje plattform finns på **https://autobleem.retromenele.pl/**. Sidan är
> organiserad per plattform: panelen *Install* för var och en är vad du laddar ner; *Build inputs*
> under den är vad installationsprogrammen själva hämtar.

## 1. Vad du får

- **Startaren** - hyllan med omslag, uppsättningarna (PlayStation, RetroArch, Apps), speldetaljer,
  snabbmenyn och systemmenyn, inställningarna, minneskortverktyget och sparpunktverktygen samt Butiken för
  nedladdning av appar och spel. Samma program på varje plattform.
- **Två PS1-emulatorer** - `pcsx-abnxt`, den nuvarande (standard) och `pcsx-ab`, den klassiska
  emulatorn som AutoBleem alltid har medfört. Du väljer en i inställningarna; båda använder samma
  inställningar och minneskort.
- **RetroArch** (valfritt på varje plattform) för andra system: NES, SNES, Mega Drive, Game Boy,
  arkad och mycket mer. AutoBleem bygger sina RetroArch-listor från ROM-filer som du kopierar in och
  startar varje spel med rätt kärna. Kärnlistan börjar med *PlayStation 1* (avsnitt 3.8). Doom-liknande spel körs
  från dina egna speldata i en mapp som heter *Paket* (avsnitt 3.9).
- **Konsolverktygen**: *PSC-Bios* (visas i menyerna som *Nätverk och handkontroller*) för WiFi, klockan, Bluetooth
  och styrpadutsättning - på konsolen, och även på en Raspberry Pi och PC-stickan - och *ABFlashKit* för installation
  av AutoBleem-kerneln (endast PlayStation Classic).
- **UpdateRoms** för Windows: uppdaterar RetroArch-listorna och skisskonst för en konsolsticka på en PC,
  eftersom själva konsolen inte har ett nätverk.

![Startaren: hyllan med omslag, det valda spelets detaljer, knapphints](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Installation

### 2.1 PlayStation Classic

Du behöver en Windows-PC, en USB-sticka (USB 2.0, 8 GB eller mer) och originalkonsolen. Stickan behöver
inte vara tom och **formateras inte** om du inte ber om det: AutoBleem installeras bredvid det som redan finns
på den, och en sticka du redan använder med AutoBleem 1.0 uppgraderas på plats (nedan). AutoBleem körs från stickan utan några ändringar av konsolen.
Stickan måste vara **FAT32** för en originalkonsol - dess kernel kan inte läsa exFAT. Endast en konsol
med AutoBleem-kerneln installerad (ABFlashKit, kapitel 6) kan också starta från en exFAT-sticka, vilket
tar bort FAT32:s 4 GB-begränsning.

1. Ladda ner **AutoBleemInstaller-<version>.zip** från PlayStation Classic-panelen på webbplatsen och
   packa upp den någonstans. Den innehåller `AutoBleemInstaller.exe` och AutoBleem-paketet som den
   installerar.
2. Sätt in stickan och starta `AutoBleemInstaller.exe`. Välj enheten överst. Raden under säger vad som finns
   på stickan nu: *en ny installation* (stickans övriga filer lämnas orörda) eller *AutoBleem <version> finns
   på den här stickan: den uppdateras* (spel, sparningar, minneskort och inställningar stannar).
   **Formatering är valfri**: knappen **Format** bredvid enheten är bara för en ny sticka utan filsystem, en
   sticka konsolen inte kan läsa (till exempel NTFS) eller en du vill tömma - den frågar först och raderar
   sedan allt på stickan. Välj FAT32 där om inte konsolen har AutoBleem-kerneln. Markera vad du vill ha:
   - **Skisskonst-databaser** - omslag och detaljer för PS1-biblioteket (markerat som standard; cirka
     300 MB).
   - **RetroArch** - RetroArch med kärnor, extra program (Doom, Quake, Amiga, ...) och libretro-resurser
     för spel från andra system. Av som standard; kan läggas till senare genom att köra
     installationsprogrammet igen.
   - **BIOS-filer** - BIOS-filerna som RetroArch-kärnorna behöver (kräver RetroArch).
   - **Exempelspel** - några gratis homebrew-spel så att hyllan inte är tom.
3. Klicka på **Install** och vänta. Framstegsstaplarna och loggen visar varje steg; stickan heter
   `SONY` i slutet, och `UpdateRoms` placeras på den (se kapitel 5).
4. Ta bort stickan på ett säkert sätt, sätt in den i konsolens **andra främre USB-port** (höger, spelare 2) - den
   första är till handkontrollen - och slå på konsolen. AutoBleem startar istället för originalmenyn. En andra
   handkontroll behöver en USB-hubb på den främre porten eller en Bluetooth-handkontroll. Håll stickan borta från
   micro-USB-porten på baksidan (se nedan).

**Starta och stänga av.** Med stickan i startar konsolen, blinkar sin ljus några sekunder (AutoBleem
hämtas) och går sedan i beredskap innan något visas - det är konsolens eget sätt att organisera en
uppdatering, som är hur AutoBleem får att köras. Tryck på **Power** en gång och startaren dyker upp.
*Stäng av* i systemmenyn, eller konsolens Power-knapp, sätter konsolen i **AutoBleem-beredskap**: stickan
tas bort först, sedan blir ljuset **orange** - tecknet på att AutoBleem fungerar som det ska - och nästa
Power-tryck tar startaren tillbaka på några sekunder. **Medan ljuset är orange kan du dra ut stickan** och
sätta in den i en PC utan att Windows vill kontrollera den; sätt tillbaka den innan du trycker på Power.
Att dra ur konsolens ström går genom uppstartsberedskapen igen nästa gång. Ett ljus som är **rött** betyder att
konsolen verkligen har stängts av.

**Använd en främre USB-port för stickan.** Micro-USB-porten på baksidan (en värd där fungerar bara med
AutoBleem-kerneln) håller konsolen vaken: med en sticka eller en hubb på den stängs konsolen av i stället för att
gå i beredskap, och Power startar en kallstart.

**Ingen sticka.** Utan sticka i konsolen visar en bild att du ska sätta in en - i vilken USB-port som helst. Efter
5 minuter, eller direkt vid Power, går konsolen i viloläge. Samma bild visas om stickan dras ur medan AutoBleem
körs.

![Bilden som ber om stickan](../images/en/insert-stick.jpg)

**Stickkontroll.** En sticka som inte togs bort på rätt sätt kontrolleras vid start, vid uppvaknande och efter en
urdragning, med en förloppsstapel. På en stor sticka kan det ta en stund; avbryt inte.

![Stickkontrollen](../images/en/stick-check.jpg)

Om du vill **uppdatera** en sticka kör du ett nyare installationsprogram över den: dina spel, sparningar,
inställningar och RetroArch-innehål stannar; bara AutoBleem:s egna filer ersätts.

**Uppgradera från AutoBleem 1.0 (eller AutoBleem-NG).** Samma installationsprogram, samma sticka - ingen
formatering:

1. Kopiera först hela stickan till datorn, som säkerhetskopia.
2. Sätt in den, starta `AutoBleemInstaller.exe`, välj kanal och enhet. Tryck **inte** på Format.
3. Klicka på **Install**. Installationsprogrammet uppdaterar den gamla layouten: RetroArch, ROM-filerna och
   temana flyttas dit AutoBleem 2 letar efter dem, och de gamla ROM-mapparna (`nes`, `snes`, ...) får
   RetroArchs systemnamn. Spel, sparade lägen, minneskort, ROM-filer och RetroArchs sparningar stannar;
   `config.ini` behålls också, med PS1-emulatorn satt till pcsx-abnxt.
4. Sätt tillbaka stickan i konsolen. Den första skanningen bygger om spellistan och spellistorna i RetroArch
   (UpdateRoms på datorn hämtar omslag till RetroArch-spelen, kapitel 5).

> Originalkonsoolen har ingen klocka och inget nätverk: datum visas bara efter att AutoBleem-kerneln
> är installerad (kapitel 6), och skisskonst för RetroArch-spel kommer från UpdateRoms på PC
> (kapitel 5).

Spel går in i `Games`-mappen på stickan, en mapp per spel - se avsnitt 3.9 för layouten.

### 2.2 Raspberry Pi

AutoBleem gör en Pi till en liten konsol: den startar direkt in i startaren, utan skrivbord. Två färdiga
avbildningar finns på webbplatsen - 32-bitars och 64-bitars - plus en tarball för ett befintligt
Raspberry Pi OS Lite.

| Modell | 32-bitars avbild | 64-bitars avbild | Anmärkningar |
|---|---|---|---|
| Raspberry Pi 5 | ja | ja | |
| Raspberry Pi 4 Model B, Pi 400 | ja | ja | |
| Raspberry Pi 3 Model B / B+ / A+ | ja | ja | bra för startare och PS1 |
| Raspberry Pi Zero 2 W | ja | ja | 512 MB RAM: PS1 fungerar, tyngre RetroArch-kärnor gör det inte |
| Raspberry Pi 2 Model B | ja | bara v1.2 | långsam för något 3D |
| Raspberry Pi 1, Zero, Zero W | nej | nej | ARMv6 - ingen avbild stöds |

**32-bitarsavbildningen rekommenderas** för PS1-spel: `pcsx-ab`:s snabba ARM-omkompilator är endast
32-bitars, så 64-bitsversionen kör PS1-spel långsammare. 64-bitsavbildningen har en större uppsättning
RetroArch-kärnor.

**Med Raspberry Pi Imager:**

1. Installera Raspberry Pi Imager (raspberrypi.com/software). I *Choose OS* väljer du *Use custom* och
   den `autobleem-<version>-rpi-armhf.img.xz` (32-bitars) eller `-arm64.img.xz` (64-bitars) som du
   laddade ner - eller lägg till repositoriums-URL:en `https://autobleem.retromenele.pl/rpi-imager/os_list.json`
   i appens inställningar och välj AutoBleem från listan.
2. Använd Imagers anpassningsskärm (kugghjulet, eller frågan efter *Next*) för att ställa in
   **användarnamn och lösenord, WiFi-nätverk och land och aktivera SSH**. AutoBleem behöver ett nätverk
   vid första start.
3. Skriv kortet, sätt in det i Pi med en skärm och tangentbord eller styrenhet ansluten, och slå på den.

**Första starten** tar 5 till 25 minuter och visar vad den gör på skärmen. Utan nätverk ber det om ett
nätverk (WiFi-lista, lösenord), sedan om RetroArch ska installeras (en minut utan svar betyder ja),
växer systempartitionen, skapar `AUTOBLEEM`-datapartitionen från resten av kortet, installerar RetroArch
och kärnor, BIOS-paket och exempelspel, och startar om i startaren.

Svar kan ges i förväg i **`autobleem.txt`** på kortets startpartition (redigerbar på vilken PC som helst
före första start):

| Nyckel | Standard | Betydelse |
|---|---|---|
| `root_gib` | 8 | Systempartitionens storlek i GiB; resten blir spelpartitionen. |
| `hdmi_mode` | 1920x1080@60 | Skärmläge för hela startningen (`1280x720@60` för äldre TV). |
| `retroarch` | (frågad) | `yes` / `no` - RetroArch och andra system, eller bara PS1. |
| `thumbnails` | ingen | `boxarts` speglar hela box-art-uppsättningen offline (~9000 filer). |
| `bios`, `downloads`, `samples` | ja | Ställ in på `no` för att hoppa över BIOS-paket, alla nedladdningar eller exempelspel. |

**På befintligt Raspberry Pi OS Lite** (Bookworm eller Trixie): kopiera `autobleem-rpi.tar.gz` (eller
arm64-versionen) till Pi, packa upp den och kör `sudo bash install.sh`. Det ställer samma frågor,
skapar datapartitionen genom att krympa root vid nästa start (`--shrink-root <GiB>`), och placerar
startaren på den första konsolen.

Efter installation är **`AUTOBLEEM`-partitionen** på kortet (exFAT) vad du fyller: ta ur kortet och öppna
det på vilken PC som helst, eller kopiera över nätverket (SSH är aktiverat). `Games/` för PS1-spel,
`RetroArch/roms/<system>/` för spel från andra system, `System/Bios/` för PS1-BIOS (avsnitt 3.10),
`Themes/` för teman.

### 2.3 PC USB-sticka

Samma apparat för vilken PC som helst som startar från USB - ett 32-bitarssystem, så även gamla
maskiner fungerar:

1. Ladda ner `autobleem-<version>-pcusb-i386.img.xz` från PC-panelen och skriv den till en sticka på
   8 GB eller mer med Raspberry Pi Imager (*Use custom*), balenaEtcher eller Rufus (DD-läge).
2. Starta PC:n från stickan (boot-menyknappen för din PC - F12, F8, Esc...). Både BIOS och UEFI-start
   fungerar; **Secure Boot måste vara av**.
3. Första starten är Pi:s: en nätverksfråga om det inte finns någon kabel, RetroArch-frågan, sedan
   installation - cirka åtta minuter med kabelnat - och omstart i startaren.

Stickan har sedan en `AUTOBLEEM`-partition för dina spel, synlig på Windows 10 (1903 och senare) som en
andra enhet när du sätter in stickan i en PC som körs. `autobleem.txt` finns på första partitionen, med
samma nycklar som på Pi (ingen `hdmi_mode` - PC:n använder skärmens inbyggda läge).

### 2.4 Windows

AutoBleem som Windows-program: fullskärm, emulatorer och RetroArch startade som program.

1. Ladda ner **AutoBleemSetup-<version>.exe** och kör det. Den installeras per användare, utan
   administratörsrättigheter: programmet under `%LOCALAPPDATA%\Programs\AutoBleem`, data (spel,
   inställningar, teman, RetroArch) i en mapp du väljer - `Documents\AutoBleem` som standard.
2. Markera komponenter - skisskonst-databaser, RetroArch (Windowsversionen och kärnor), BIOS-filer,
   exempelspel - och låt inställningshjälparen ladda ner dem.
3. Starta AutoBleem från Start-menyn eller skrivbordet. På en PC fungerar tangentbordet som en
   styrenhet (avsnitt 3.2).

Att köra ett nyare installationsprogram över det uppdaterar programmet och behåller datamappen.
Startaren kontrollerar också webbplatsen en gång om dagen och erbjuder en uppdatering när det finns
en (avsnitt 3.11).

<!-- pagebreak -->

## 3. Använda AutoBleem

### 3.1 Startaren

Startaren öppnas på hyllan: omslaget från aktuell uppsättning, det som är valt i mitten med en mjuk reflektion
under sig, dess detaljer bredvid i ett kompakt rutnät - förlag, år, serienummer, region, spelare, när det senast
spelades (en uppgift som ett spel inte har utelämnas) - och en uppspelningsknapp. Standardutseendet är temat
**ab2.0.0**; en ny installation och en uppdatering som tar med det byter till det en gång. Tipsfältet längst ner har
två rader med fyra platser. Den första säger vad knapparna gör för det valda spelet (spela, spela i RetroArch, öppna
ikonraden, snabbmenyn); den andra visar alltid Select (uppsättningen), Start (ett slumpmässigt spel), Triangle
(guiden) och L2 + R2 (systemmenyn), nedtonade när någon av dem inte gör något. Ett spel utan omslag visar en skiva som ligger i fodralets svarta fack. En skanning av spelmappen körs i
bakgrunden vid varje start; medan den körs visar en bubbla längst upp till höger framstegen, och nya spel dyker upp
på hyllan när de hittas.

**En ny installation** har inga spel än: i stället för en tom hylla visar startaren ett välkomstkort - *Hej och
välkommen till AutoBleem!* - som ber dig lägga spel i mappen `Games` och välja *Skanna om spel*, och som anger
platsen för din plattform: på ditt minne (PlayStation Classic, PC-stickan), på ditt SD-kort (Raspberry Pi) eller i din
AutoBleem-mapp (Windows). Kortet försvinner så fort en skanning hittar det första spelet.

**Notiser** visas som bubblor längst upp till höger: skanningens framsteg, namnet på uppsättningen du bytte till
(*Visar: ...*, så länge Alternativ → *Visningstid för meddelande* anger), lågt batteri i en handkontroll, en notis
efter en krasch, en skanningsprocessor som arbetar och Butikens pågående nedladdning. Nedladdningens bubbla visar
dess hastighet och återstående tid, t.ex. `1.4 MB/s · 0:42`.

**Kanalmärket.** Ett bygge som inte är en slutlig utgåva visar ett litet märke under handkontrollens batteriplatta i
övre vänstra hörnet: en bricka med kanalen - `ALPHA`, `BETA` eller `RC` för en förhandsversion, `TESTING` för vilken
annan förhandsversion som helst, `NIGHTLY` för ett nattligt bygge, `DEV` för ett handgjort bygge - och den korta
versionen bredvid (för `DEV` den commit det byggdes från). En utgåva visar inget märke.

En trådlös kontroll med känt batteriläge - på konsolen, en Pi eller PC-stickan, inte i Windows - visas som en liten ikon med sin procentandel, staplad från övre vänstra hörnet på sin egen platta. En kontroll matchad till Spelare 1 eller Spelare 2 (enligt inställningen Byt spelare 1 / spelare 2) märks P1/P2; en omatchad kontroll, eller en tredje, får ingen märkning. När en kontrolls batteri blir lågt rapporterar en notisrad det en gång, med namn och procent.

![Set-väljaren: tre flikar och grupperna av den nuvarande fliken med deras antal](../images/en/set-picker.jpg)

### 3.2 Kontroller

| Knapp | På hyllan |
|---|---|
| Vänster / Höger | Föregående / nästa spel. Hålla inned scrollar. |
| L1 / R1 | Hoppa till föregående / nästa första bokstav i titlar. På en tom hylla med en skivenhet öppnar R1 *Skiva* (avsnitt 3.8a). |
| Cross | Starta det valda spelet (PS1-spel i PS1-emulator; RetroArch-spel i dess kärna; App efter readme). |
| Square | Starta det valda PS1-spelet i RetroArch istället. På en skiva i en USB-enhet: *Kopiera skiva* (avsnitt 3.8a). |
| Circle | Tillbaka till skivvyn, när en skiva finns i enheten (avsnitt 3.8a). |
| Triangle | Knappguiden. |
| Start | Ett slumpmässigt spel från aktuell uppsättning. |
| Select | Set-väljaren: PlayStation / RetroArch / Apps-flikar (L1 / R1), grupper av fliken (Upp / Ner,
L2 / R2 sida), Cross väljer. |
| Upp | Snabbmenyn (avsnitt 3.4). |
| Ner | Öppna ikonstaden under spelet (Inställningar, Spel, Minneskort, Återuppta). Upp stänger den. |
| L2 + R2 | Systemmenyn (avsnitt 3.5). |

**Med tangentbord** (PC utan styrenhet, eller USB-tangentbord på konsol, Pi eller PC-sticka): tangenterna
står in: **Piltangenter** = d-pad, **Enter** = Cross, **Esc eller Backspace** = Circle, **Tab** = Triangle,
**Mellanslag** = Square, **F1 / F2** = Select / Start, **Page Up / Page Down** = L1 / R1, **Home / End** =
L2 / R2, **F10** = systemmenyn. På en utvecklingsmaskin stänger Esc programmet och mellanslag är Start.

I varje lista och meny: Upp / Ner flytta, **L2 / R2 vänd sidor**, L1 / R1 hoppa till första / sista rad,
**Cross väljer, Circle går tillbaka**. En skärm med inställningar sparar dem när du lämnar den med Circle.

**I ett spel eller en app**: håll **Start + Select, eller Home, i 2 sekunder** för att gå tillbaka till AutoBleem.
Det fungerar på varje handkontroll - konsolens, en USB-handkontroll, en Bluetooth-handkontroll. Ett kort tryck
öppnar emulatorns meny; en app har ingen sådan meny, bara det långa trycket fungerar.

![Ikonstaden under det valda spelet](../images/en/launcher-icons.jpg)

### 3.3 Uppsättningarna

**Select** öppnar set-väljaren. PlayStation-fliken listar på PlayStation Classic *Alla spel* och *Interna spel* (de
tjugo inbyggda), sedan *USB-spel* (allt i `Games/`) och varje mapp du skapade under den (ett spel i en undermapp hör
till denna grupp), sedan *Favoritspel*, *Spelhistorik* och, när något spel är flaggat som sådant, *Lightgun-spel*. På
en Raspberry Pi, en PC-sticka och Windows finns inga interna spel, så listan börjar med *USB-spel*, som är hela
biblioteket. RetroArch-fliken (endast där RetroArch är installerat) listar en grupp per system som har spel, plus
RetroArch:s egna favoriter och historik. Apps-fliken grupperar applikationer efter typ: *Alla appar*, sedan *Spel*,
*Emulatorer*, *Verktyg*, *Media* och *Övrigt* (kategorin ställs in i varje apps `app.ini`-fil). Apps-fliken visar också **PE-appar** - Windows-program som körs
av PE-runnern; en som konsolen inte kan starta märks *kan inte köras på den här konsolen*. Där startaren visar den
finns även en *Paket*-rad i listan (avsnitt 3.9). Varje rad visar hur
många objekt den innehåller; en grupp utan objekt öppnas på en tom hylla med endast inställningar i ikonstaden.
Sidfoten anger tangenterna: L1 / R1 flikar, L2 / R2 en sida, Cross väljer, Circle *Tillbaka*.

### 3.4 Snabbmenyn

**Upp** i startaren, eller **kugghjulsikonen** i ikonstaden (där inställningar / spel / minneskort /
Återuppta är): snabbmenyn för åtgärder du vill nå snabbt. En kort lista: *Skanna om spel* (startar en
skanning nu), *Butik* (bläddra bland och installera spel, appar och tillägg), *Nätverk och handkontroller* (bara där
ett installerat tillägg ger `network`-posten - PSC-Bios på konsol, Pi och PC-sticka: WiFi, Bluetooth-parning,
styrenhetskarteringsguide - se kapitel 6; grå med "slå på det under Tillägg" när det tillägget är
inaktiverat - Cross öppnar listan över tillägg), *Starta om launchern* (stänger AutoBleem och startar det igen;
endast på konsol, Pi och PC-sticka) och *Systemmeny...* (allt annat: Alternativ, Spelbibliotek, Stäng av och mer -
hela menyn nedan). Upp / Ner flytta (radbrytning), Cross väljer, Circle går tillbaka. Varje objekt har en
enradsbeskrivning på sin rad. Förutom Butiken och *Starta om launchern* finns varje objekt också i systemmenyn.

![Snabbmenyn](../images/en/quick-menu.jpg)

### 3.5 Systemmenyn

**L2 + R2** (tillsammans, i valfri ordning) öppnar systemmenyn över hyllan. Varje rad har en enradsbeskrivning, och
menyn är organiserad i avsnitt:

| Avsnitt | Objekt | Vad det gör |
|---|---|---|
| (överst) | Skanna om spel | Söker nu efter nya, ändrade eller borttagna spel (skanningen övervakar även mappen själv). |
| | Tillägg | Tilläggen på stickan - AutoBleem Store och andra (avsnitt 3.12). |
| **Bibliotek** | Spelbibliotek | PS1-spel som en lista med sina mappar: ta bort ett spel, töm skisskonsten. Inaktiverad medan skanning körs. |
| | Minneskort | Dina minneskortuppsättningar (avsnitt 3.7). |
| | Skanningsprocessorer | Program som varje skanning kör först - deras ordning, på eller av (avsnitt 3.13). Inaktiverad medan skanning körs. |
| **System** | Alternativ | AutoBleem:s inställningar (avsnitt 3.6). |
| | Nätverk och handkontroller | Bara där ett installerat tillägg ger `network`-posten (`Provides=network` i dess `extension.ini` - PSC-Bios på konsol, Pi och PC-sticka) - WiFi, Bluetooth-styrenhetsparning, DualShock 3-installation och styrenhetskarteringsguide - se kapitel 6. När tillägget är installerat men inaktiverat, förblir detta objekt grått med "slå på det under Tillägg" - Cross öppnar listan över tillägg till det. |
| | Hårdvaruinformation | Maskinens fakta: system, CPU, lagring, nätverksgränssnitt, tidszon, display, styrenheter och deras mappningar - samma sida på varje plattform (avsnitt 4.2). Circle går tillbaka till systemmenyn. |
| | Virtuell handkontroll | Handkontrollerna som appar får och de som daemonen ser (avsnitt 4.5). Circle går tillbaka till systemmenyn. |
| | Programuppdatering | (Raspberry Pi och PC) Kontrollera webbplatsen nu för nyare AutoBleem eller RetroArch; raden säger *Uppdatering tillgänglig* när startaren redan känner till en. |
| | Om | Krediter och licens. |
| **Lämna** | RetroArch | (Endast där RetroArch är installerat.) Lämnar startaren för RetroArch:s egen meny. Att stänga RetroArch kommer tillbaka. |
| | Stäng av | Efter bekräftelse: på konsol AutoBleem-beredskap - stickan borttagen, ljuset orange, Power tar startaren tillbaka (avsnitt 2.1); på Pi eller PC stängs maskinen av. |

![Systemmenyn](../images/en/system-menu.jpg)

### 3.6 Inställningar

Inställningarna är i grupper, var och en under en rubrik; Upp / Ner flyttas mellan raderna, Vänster / Höger ändrar ett
värde (ett tryck är ett steg, att hålla inne rullar vidare), L1 / R1 hoppar till första / sista raden, L2 / R2 bläddrar,
Circle lämnar och sparar. Varje förändring tillämpas omedelbart. På/av-värden läses **PÅ** / **AV**.

| Grupp / Inställning | Vad det gör |
|---|---|
| **Gränssnitt**: Bild | Skärmens upplösning, för startaren och PS1-emulatorn: *Auto* (skärmens eget läge, visat som *Auto (1920x1080)*) eller vilket läge skärmen listar; konsolen erbjuder 720p, 1080p och *CRT 4:3* (720x480, för en CRT-TV eller en 4:3-inspelningsenhet). Ett nytt läge bekräftas: *Behålla det här bildläget?* - bekräftar du inte går det tillbaka efter en nedräkning. Inte i ett utvecklingsfönster. |
| CRT-marginal: | Säkerhetsmarginalen på en 4:3-utgång, 0 till 10 % i steg om 1 %. Tillämpas direkt och läses före startbilden. |
| Bildhöjd: | Bildens höjd på vilken 4:3-utgång som helst (*CRT 4:3*, eller ett 4:3-fönster på en VGA- / PC-utgång), -40 till +40 i steg om 2, tillämpas direkt. RetroArch:s spelbild följer med. |
| Emulatorns skärmskalning | Hur PS1-emulatorn anpassar ett spels bild till skärmen: *1x1* (PlayStations egna pixlar), *2x (heltal)*, *4:3*, *4:3 (heltal)* eller *Helskärm*. Heltalsskalning använder bara hela multipler (skarpast). Den ersätter den gamla Widescreen-växeln; klassiska `pcsx-ab` och RetroArch känner bara helskärm och 4:3. |
| Skärmgloria: | PÅ fyller banden vid sidan av ett spels bild (där den inte fyller skärmen) med bildens egen glöd (`pcsx-abnxt`). |
| AutoBleem-tema | Utseendet. Teman finns i `Themes/`; en tema-zip som släpps där packas upp vid nästa besök. AutoBleem:s teman uppdateras vid varje uppdatering - för att anpassa en, kopiera den först under ett nytt namn. Standard är **ab2.0.0**. På *CRT 4:3* visar listan bara teman som har en 4:3-layout; har temat som används ingen, ersätter standardtemat det efter bekräftelsen (även vid start) och en notis säger *Tema ändrat till standardtemat (CRT 4:3)*. |
| Omslagsstil | Den prydnadsstil som ritats omkring PS1-omslag. |
| Glans på omslaget | En glans som går över det valda omslaget när hyllan kommit till ro. |
| Språk | Starlarens språk, tillämpad omedelbar (17 språk). |
| Visningstid för meddelande | Hur länge infobubblorna ("Visar: ...", skanningens sammanfattning) blir kvar, 0 till 20 sekunder; 0 visar *Av*. Fel har sin egen fasta tid. |
| Startskärm | AutoBleem-bilden när startaren startar; av går direkt till hyllan. |
| Animationer | Rörelsen mellan skärmar; av gör varje skärmbyte omedelbart. |
| **Typsnitt**: Använd standardteckensnitt | Startaren använder sitt standardteckensnitt (Red Hat Text) eller - avstängt - teckensnittet som valts nedan. |
| Teckensnitt | Någon `.ttf`/`.otf` från `resources/fonts`, `RetroArch/fonts` eller temamappen; raden anger teckensnittet som används. |
| **Ljud**: Musik, Bakgrundsmusik | Vilken spår som spelar under startaren (temats, eller en fil från `resources/music`), och om en spelar alls. |
| **Emulering**: PS1-emulator | `pcsx-abnxt` (standard: nuvarande PCSX-ReARMed med AutoBleem:s tillägg) eller `pcsx-ab` (klassisk). En sparad återställningspunkt fortsätter i den andra, om inte spelet kördes utan BIOS-fil. |
| Byt spelare 1 / spelare 2 (PS1-emulatorer) | Byter vilken av de två första kontrollerna som är Spelare 1 och vilken som är Spelare 2, i båda PS1-emulatorerna (pcsx-abnxt och klassiska pcsx-ab). Det får bara effekt med två eller fler kontroller anslutna; med en kontroller är det alltid Spelare 1. RetroArch påverkas inte. En PS1-emulator som ännu inte kan byta visar *Den här PS1-emulatorn stöder ännu inte att byta handkontroller*. |
| Spela alla PSX-spel med RA, Uppdatera RA-konfiguration, Behåll RetroArch-inställningar | (Endast där RetroArch är installerat.) Varje PS1-spel startar i RetroArch:s PS1-kärna (*PlayStation 1*; på en PC är det SwanStation); AutoBleem skriver sina inställningar in i RetroArch:s config när det startar ett spel där; en ändring gjord i RetroArch:s egen meny behålls när RetroArch avslutas. |
| **Bibliotek**: Visa interna spel | Konsolens inbyggda spel i PlayStation-listerna (endast PlayStation Classic). |
| Rena spelnamn: | PÅ (standard): RetroArch-spellistor visar namn utan taggar inom parentes som (USA), (Rev 1) eller [!]. AV visar filnamnen. Filnamnet finns kvar i spelets detaljer. PS1-spel påverkas inte - deras titlar kommer från databasen. |
| Hämta omslag online | Skanningen hämtar saknade omslag från libretro:s servrar (Raspberry Pi, PC, Windows). |
| **Uppdateringar** | Uppdateringskanalen: `release` (den testade versionen), `testing` (nästa version, under test), `nightly` (det senaste utvecklingsbygget) eller `off`. Standard följer den installerade versionen. Visas inte på en utvecklingsvärd. |
| **Diagnostik**: Behåll loggar på minnet | Behåller alla loggar på stickan från nästa start, inte bara efter en krasch (kapitel 7). |
| Visa prestanda | Ett överlägg i nedre vänstra hörnet: bildfrekvens, CPU-belastning, trådar och minne; emulatorn visar också sin FPS och CPU i spelet. |

![Inställningar i grupper](../images/en/options.jpg)

![Bildgruppen: CRT-marginal och Bildhöjd](../images/en/options-display.jpg)

![Notisen efter byte till CRT 4:3 med ett tema utan 4:3-layout](../images/en/crt43-theme-notice.jpg)

### 3.7 Ett spelets inställningar

Med ett spel valt, **Ner** öppnar dess ikonstäder: **Inställningar** (ovan), **Spel** (dess egna
inställningar), **Minneskort** (dess minneskort) och **Återuppta** (dess sparpunkter). Cross öppnar
den under markören.

**Spelets redigerare** visar spelets detaljer på höger sida (titel, förlag, år, spelare, mapp, minneskort) och dess inställningar på vänster sida, i fyra grupper:

- **Spel**: *Favorit* (i Favoritspel-gruppen), *Lightgun-spel* och *Spela med RA* (endast där RetroArch är
  installerat: ett lightgun-spel ansluter sig till Lightgun-gruppen och körs alltid i RetroArch, vars PS1-kärna har
  GunCon; *Spela med RA* kör detta spel i RetroArch), *Lås data* (skannern behåller spelets titel, serienummer och
  skivlista som du ställt in) och *Återuppta:* - vad som händer när ett spel med sparpunkter startar: *Fråga* visar
  platsväljaren, *Senaste platsen* fortsätter direkt från den nyaste platsen, *Aldrig* startar spelet från början.
- **Bild**: *Upplösning* (1x eller 2x, på den inbyggda GPU:n), *Ta bort sömmar* (endast med 2x), *Dithering* (Av, På,
  Alltid), *Utjämning*, *Filter* - hur bilden skalas: Närmaste (rena pixlar), Linjär (mjuk), Skarp eller Skarp (enkel)
  (skarpa pixlar utan skimmer), Quilez, eller CRT-filtren CRT (fast), CRT (raster) och CRT-Pi (de ritar egna scanlines, så
  scanlinjeraderna blir gråa) - och *Scanlines* med deras *Scanlines ljusstyrka*. Upplösning, ta bort sömmar,
  dithering, utjämning och andra filter än Linjär och Närmaste är för `pcsx-abnxt`; klassiska `pcsx-ab` och RetroArch
  visar resten som Närmaste.
- **Rendering**: GPU-*Plugin* och *Frameskip* (Auto, Av, 1 till 3).
- **Emulator**: SpeedHack, CPU-klocka, SPU-interpolation, startlogga (av hoppar över BIOS-skal - för en
  homebrew-skiva vars anpassad logga bryter starten) och med `pcsx-abnxt` *Sony-hack*-växeln.

Bildens form och skärmens upplösning är globala (Alternativ → *Emulatorns skärmskalning* och *Bild*). Ett spel utan
titel i sina data visas under namnet på sin mapp.

Triangle byter namn på spelet, Square byter dess minneskort, Start delar ett nytt. Circle sparar och
lämnar. Att hålla Vänster / Höger eller Upp / Ner upprepar förflyttningen, i redigeraren och även i RetroArch:s
spelalternativ och kärnskärmar. Ett spel på enheten som saknar `pcsx.cfg` kan inte spara: redigeraren säger
*Inte sparat: spelet saknar pcsx.cfg*.

För en **skiva i skivenheten** (avsnitt 3.8a) tonar redigeraren ner raderna som skivan inte kan använda och säger
*Inte tillgängligt för en skiva i enheten*.

![Spelets redigerare för en skiva i enheten](../images/en/game-editor-disc.jpg)

**Inställningar sparade i emulatorn.** Emulatorns egen meny har *Spara inställningar för det här spelet*.
När ett spel har sparade inställningar där, är de de som det spelar med, och spelets redigerare visar
raderna Bild, Rendering och Emulator gråa med dessa värden, under rubriken *Sparat i emulatorn*. För att gå tillbaka
till speleditor-inställningarna väljer du **Lås upp inställningarna** och bekräftar: detta raderar de av
emulatorn sparade inställningarna, och dessa rader kan ändras igen. Båda emulatorerna, `pcsx-ab` och
`pcsx-abnxt`, läser och skriver samma sparade inställningar.

![Spelets redigerare](../images/en/game-editor.jpg)

### 3.7 Minneskort och sparpunkter

Varje PS1-spel har sitt eget minneskort som standard (hållet med sparpunkter i `Games/!SaveStates/<game
folder>/`). **Minneskort** i systemmenyn hanterar **delade uppsättningar** - ett kort som flera spel
använder, hållet i `Games/!MemCards/`: skapa ett (Square, med på-skärm-tangentbord), byt namn (Cross),
ta bort (Triangle). Ett spel placeras på en uppsättning med *Ändra minneskort* i dess redigerare, eller
från dess Minneskort-ikon. En uppsättning
utan kort än säger *inget kort än*, och vid sparande frågar den *Vill du spara minneskortsdata?*

**Minneskortredigeraren** (Minneskort-ikonen) visar spelets kort och ett andra kort sida vid sida, med
varje sparnings ikon och titel: kopiera en sparning mellan de två (Square), ta bort en (Triangle),
defragmentera ett kort (Select). Start byter ut kortet på höger sida mot en annan uppsättning.

![Minneskortredigeraren](../images/en/memory-card-editor.jpg)

**Återställningspunkter**: när du lämnar ett PS1-spel med konsolens framkantknapp **Reset** (eller emulatorns
meny på Pi eller PC), sparar AutoBleem ett sparpunkt från där du var och erbjuder det under **Återuppta**-ikonen
- fyra platser, visade som inramade kort, varje med en bild från stunden, platsens nummer och datum; det nyaste
är märkt **NYAST** och en oanvänd plats säger *Ingen återupptagspunkt*. Cross fortsätter från platsen, Triangle
raderar den. Ett spel med en återställningspunkt visar en liten bild på dess Återuppta-ikon; ett spel utan har
Återuppta-ikonen nedtonad. Medan återställningspunkten skrivs på väg ut ur ett spel visar emulatorn *Vänta...*.
PS1-spel som spelas i RetroArch har också återupptagsplatser. En plats har ett märke - AutoBleem 2- eller
RetroArch-loggan - så att du ser vilken emulator som skrev den.

![Platsväljaren för återupptagning](../images/en/resume-picker.jpg)

### 3.8 Starta spel, RetroArch och appar

**Cross** startar det valda spelet. Ett PS1-spel körs i den valda PS1-emulatorn (avsnitt 3.6), fullskärm,
tills du lämnar det - på konsolen med framkanten **Reset**-knapp (tillbaka till startaren med en
återställningspunkt; fungerar även inifrån in-game-menyn) eller **Power** (konsolen stängs av); på Pi eller PC via
emulatorns in-game-meny (nedan). **Square** startar ett PS1-spel i RetroArch istället.

**Vägen ut ur ett spel** är densamma på varje handkontroll - konsolens, en USB-handkontroll, en
Bluetooth-handkontroll: **håll Start + Select, eller Home, i 2 sekunder** (*Håll Select+Start eller Home i 2
sekunder: tillbaka till AutoBleem*). Ett kort tryck på Select + Start eller Home öppnar emulatorns meny (*Kort
tryck på Select+Start eller Home: emulatorns meny*); en app har ingen sådan meny, bara det långa trycket fungerar.
På konsolen stoppar **Reset** alltid även en app.

**In-game-menyn** (`pcsx-abnxt`). Tryck på menyknappen - handkontrollens Home, **Select + Start** på en handkontroll
utan, eller **Esc** på ett tangentbord - och spelet stannar bakom en meny med spelets senaste bild. **Att hålla
menyknappen i 2 sekunder** är detsamma som Reset: det lämnar spelet. L1 / R1 växlar mellan dess tre flikar, och
menyn öppnas på den flik och rad där den lämnades:

- **Spel**: *Fortsätt spelet*; under *Sparningar*: *Snabbspara*, *Snabbladda* och *Läs in autosparning* (spelet som
  det var för upp till 30 sekunder sedan - emulatorn sparar det i minnet av sig själv medan du spelar); under
  *Cd-skiva*: *Byt skiva* och *Återställ spelet* (startar det om från början); *Spara inställningar för det här
  spelet* (se avsnitt 3.7), *PCSX-meny* (PCSX-ReARMeds egna sidor: alternativ, fusk, Om) och *Avsluta* (tillbaka till
  AutoBleem).
- **Bild**: *Bild* (skärmens upplösning - på konsolen väljs den i Alternativ och visas här bara), *Upplösning* (1x
  eller 2x), *Ta bort sömmar*, *Dithering*, *Skalning*, *Utjämning*, *Filter*, *Scanlines* och *Scanlines
  ljusstyrka*. Varje rad har en hjälprad till höger. CRT-Pi är för tungt för konsolen vid 1080p. En rad som inte
  gäller är nedtonad, och dess hjälp säger varför.
- **Handkontroller**: *Handkontroll 1* och *Handkontroll 2*: standard (digital), analog (DualShock), en pistol eller
  ingen; träder i kraft när spelet fortsätter.

Menyn är ritad i startarens ab2.0.0-utseende, med handkontrollernas batterier och bilden från den senaste
snabbsparningen.

Ett **RetroArch**-spel startar i RetroArch med kärnan som startaren valde för sitt system; *Close Content*
eller *Quit RetroArch* i dess meny kommer tillbaka till startaren. RetroArch-objektet i systemmenyn öppnar
RetroArch:s egen meny (XMB) utan något inladdat, för dess inställningar och dess egna innehållslistor. Kärnfönstret öppnas med *PlayStation 1* först.

![RetroArch-kärnfönstret](../images/en/retroarch-cores.jpg)

En **app** (Apps-uppsättningen: konsolverktygen, och på en konsol de extra program som RetroArch:s paket
medbringer - Doom, Quake, Amiga, ...) visar sitt readme först; Cross startar det, Circle går tillbaka.

![En apps readme innan den startar](../images/en/app-start.jpg)

**En apps inställningar.** *Spelinställningar* ("Ändra hur det här programmet startas") har *Handkontrollsläge:*
(*Automatiskt*, *PSC-handkontroll*, *Xbox 360-handkontroll*, *PSC-handkontroll (system)*, *Xbox
360-handkontroll (system)*), *Styrkors som spak:* och *Spak som styrkors:*. Vissa appar frågar en gång, vid första
starten, *Vilka kontroller har din handkontroll?* (*Ett styrkors* eller *Analoga spakar*); en app av Windows-typ
frågar *Vad vill du göra?* (*Kör Windows*, *Installera Windows*, *Kör DOS*, *Avinstallera Windows*). För att
koppla en tangent säger skärmen *Tryck på en av knapparna.*

![En apps spelinställningar](../images/en/app-game-settings.jpg)

Texterna och frågorna som ett Windows-program (en PE-app) ställer visas som AutoBleem-skärmar (*Meddelande*,
*Välj ett alternativ*), med appens namn som rubrik.

![En fråga från en PE-app](../images/en/pe-dialog.jpg)

### 3.8a En skiva i en USB-enhet

En USB-cd/dvd-enhet med en PlayStation- eller ljudskiva i lägger skivan på hyllan som ett spel. Inte i Windows,
som saknar stöd för enheter.

- **Skivvyn** öppnas av sig själv när en skiva upptäcks; R1 *Skiva* öppnar den från hyllan. Den visar skivans
  omslag (från omslagsdatabaserna, eller hämtat online), dess serienummer och dess titel. Cross spelar skivan. Ett
  PS1-spel som spelas från skivan återupptar och sparar i skivans mapp. Efter ett spel, alternativen eller ett
  tilläggs inställningar är du tillbaka i skivvyn; Circle på hyllan tar fram den igen, och där är R1 åter
  första-bokstav-hoppet.
- **Enhetsbrickan** visar enhetens tillstånd: dold utan enhet, dämpad med enhet och utan skiva, blinkande *Läser
  skivan...* medan den läser, sedan skivans titel. Andra meddelanden är *Det här är inte en PlayStation-skiva* och
  *Skivan kan inte läsas just nu*.

![Skivvyn](../images/en/disc-view.jpg)

![Enhetsbrickan](../images/en/disc-chip.jpg)

- **En ljud-cd** öppnar **cd-spelaren** (*CD-SPELARE*, *Ljud-cd*, med *SPÅR* och *TOTALTID*). Dess tangenter är
  *Spela spår*, *Stopp*, *Föregående/nästa*, *Sök*, *Paus*, *Upprepa:* (av eller på) och *Blanda:*, och *Vald:*
  anger spåret. En skiva som inte spelas säger *Den här skivan kan inte spelas*.

![Cd-spelaren](../images/en/cd-player.jpg)

- **Kopiera skiva** (Square) kopierar en PlayStation-skiva till `Games` som en **CHD**, med en `.m3u`-fil för ett
  spel på flera skivor (skiva 1 först). Den frågar först: *Kopiera "%1" till %2? Det tar upp %3 av %4 ledigt
  utrymme.* Ett förloppsfönster, *Kopierar skivan*, visar *Hastighet* och *Återstående tid* och blockerar
  startaren; *Avbryt* avbryter (*Avbryter...*, sedan *Avbrutet*). Till slut står det *Skivan har kopierats till
  Games.* Den vägrar med *Finns redan i Games: %1*, *Inte tillräckligt med utrymme i Games: kopian behöver %1, %2
  är ledigt.* eller *Kopieringen misslyckades: %1*. Sektorer som inte kan läsas skrivs som nollor, och meddelandet
  *%1 sektorer kunde inte läsas och skrevs som nollor.* talar om hur många (*Oläsbara sektorer*). En skiva som
  databaserna inte känner till får sitt serienummer som namn.

![Kopiering av en skiva](../images/en/disc-copy.jpg)

- **LibCrypt-skivor**: `.sbi`-filen för ett LibCrypt-spel hämtas från webbplatsen innan skivan spelas och när den
  kopieras. Det kräver ett nätverk: på en Raspberry Pi eller PC det den redan har, på konsolen det WiFi som ställts
  in i PSC-Bios.
- Spelets redigerare för en skiva tonar ner raderna den inte kan använda (avsnitt 3.7).

### 3.9 Lägga till spel

**PS1-spel** går in i `Games`-mappen, **en mapp per spel**, uppkallad efter spelet:

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                en mapp av spel: en egen grupp i set-väljaren
    Klonoa/                   Klonoa.pbp
```

- Format: `.cue` + `.bin` (eller `.img`), `.pbp`, `.chd` (zstd också), `.ecm` (avkodad av skanningen),
  `.iso`. Ett zipat spel fungerar också: **Unzip**-processorn packar upp det innan skanningen (avsnitt
  3.13).
- Ett flerskiv-spel är en mapp med varje skiva i den; mappar uppkallade `Game (Disc 1)`, `Game (Disc 2)`
  ... slås samman till en `Game`-mapp av skanningen.
- Spel släppt direkt i `Games/` (lösa filer) sorteras in i mappar av skanningen.
- En **omslag** är en PNG eller JPEG bredvid spelets bild, uppkallad efter den. Utan en tas skisskonsten från
  omslags-databaserna, eller - när RetroArch är installerat - från libretro:s miniatyrsamling; på Pi,
  PC eller Windows hämtas en saknad online (Inställningar → *Hämta box art online*).
- Skanningen läser varje skivs serienummer och tar titel, förlag, år, spelare och region från
  RetroArch:s PlayStation-databas eller omslags-databaserna. Ändra något i speleditor:n och markera
  *Lås data* för att behålla det.

**Andra system** går under `RetroArch/roms/`, **en mapp per system, uppkallad som RetroArch:s databaser**
(mappen görs för dig): `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo Entertainment
System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance`, `FBNeo - Arcade Games` (eller `Arcade`),
... ROM-filer kan förbli zippade. På Pi, PC eller Windows läser skanningen dem själva och skriver
RetroArch:s spellista; på en konsol-sticka, kör **UpdateRoms** på PC:n (kapitel 5).

**Appar** går under `Apps/<name>/` med en `app.ini` (namn, ikon, vad som ska köras) och en `run.sh`.

**Paket.** Speldata för motorer - Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior,
Theme Hospital, DOS-spel och mer - läggs i en `Packages`-mapp på stickan, till exempel `Packages/Doom/DOOM2.WAD`.
AutoBleem känner igen datan med hjälp av en tabell som följer med (`rc/packages.ini`); de lösa spelfilerna i en
igenkänd mapp är var för sig ett paket. Dina egna filer bara läses, de ändras aldrig. Ett paket kan också komma
från Butiken. **Paketväljaren** listar det som hittades. **Paketinfo** visar ett pakets *Innehåll*,
*Beskrivning*, *Plats*, *Källa*, *Körs med*, *Mod*, *Shareware*, *I den här appen* och *Dina filer*, och *Välj
speldata* väljer datan att starta med. Meddelandena är *Ingen speldata hittades*, *Okända data*, *Ingen
installerad app kan köra detta*, *%1 behöver speldata som den kan köra: %2.* och *Inte igenkänt. Om det är ett
spel, se manualen: Dina egna spel.*

![Paketväljaren](../images/en/packages-picker.jpg)

![Paketinfo](../images/en/package-info.jpg)

**Skanna en enda del.** *Skanna om spel* kan skanna bara en del - en uppsättning eller en mapp - och tar ner sin
bubbla när den är klar.

**Teman** går under `Themes/<name>/` (`theme.json` och bilderna) - eller släpp tema-zipen i `Themes/`.

### 3.10 PS1-BIOS

På en **PlayStation Classic** använder emulatorn konsolens egen BIOS. På en **Raspberry Pi, PC och
Windows** lägg in din egen PS1-BIOS i `System/Bios/`: `romw.bin` (US/European SCPH-5501/5502) och
`romJP.bin` (Japanese SCPH-5500). Installationsprogrammen fyller dem från RetroArch-BIOS-paketen om dina
egna filer inte redan finns där. Utan dem körs emulatorn på sin inbyggda HLE-BIOS, som många spel tolererar
och några inte.

### 3.11 Uppdateringar

- **Raspberry Pi, PC-sticka, Windows**: startaren kontrollerar webbplatsen vid start och en gång om dagen
  (Inställningar → *Uppdateringar* är kanalen; *Programuppdatering* i systemmenyn kontrollerar nu). När
  det finns en nyare AutoBleem eller RetroArch frågat det: *Uppdatera nu* laddar ner allt och kör
  installationsprogrammet igen med förstartningsframstegsskärmen; *Påminn mig imorgon* och *Hoppa över
  denna version* är de andra svaren. Dina spel och inställningar stannar; startaren skannar om en gång
  efter en uppdatering. Kanalmärket i övre vänstra hörnet (avsnitt 3.1) visar vad som är installerat.
- **PlayStation Classic**: kör ett nyare `AutoBleemInstaller.exe` över stickan (avsnitt 2.1).

### 3.12 Tillägg och AutoBleem Store

**Tillägg** lägger till sina egna skärmar till startaren. De bor i `Extensions/<name>/` på stickan (på Pi
dess data-partition, på Windows datamappen); för att installera en, packar du upp dess zip där. **L2 + R2
→ Tillägg** listar dem: Cross kör en, Triangle stänger av eller på den igen. Ett tillägg som behöver
nätverket startas inte utan ett, och ett som stannade startaren stängs av - listan säger detta.

![Listan över tillägg](../images/en/extensions.jpg)

**AutoBleem Store** är det första tillägget: appar och spel att installera med ett tryck, på varje system
som AutoBleem körs på (en PlayStation Classic behöver AutoBleem-kernels WiFi). Dess fyra flikar, L1 / R1
mellan dem:

- **Appar** och **Spel**: vad källorna erbjuder (Apps-fliken listar också PE-appar, med deras licens och källa, och speldatapaket, avsnitt 3.9), varje med bild, version, storlek och källikon. Installerade
  objekt bär ett *Installerad*-märke. Cross installerar (eller uppdaterar, eller provar igen efter fel, eller
  avbryter en köad eller pågående nedladdning), Triangle tar bort vad Store installerade, Square uppdaterar
  listorna. L2 / R2 hoppar efter bokstav, **Select** visar en källa åt gången, **Start** söker titlar. Sidfoten
  visar tangenterna för den valda raden. Objektbilder cachas och kan försökas igen om de inte laddar.
- **Nedladdningar**: vad som laddar ner, väntar, misslyckas eller är installerat. Framstegsstrecken
  uppdateras stadigt, och medan du är någon annanstans i startaren visar en bubbla den pågående nedladdningen med
  dess hastighet och återstående tid (`1.4 MB/s · 0:42`). Nedladdningar går vidare i bakgrunden, även efter att du
  lämnar Store; att starta ett spel eller stänga av pausar dem bara, och en stoppad nedladdning går vidare där den
  stannade. Om nätverket försvinner säger objektet *Väntar på nätverket* och går vidare där det stannade när
  nätverket är tillbaka (det ger upp efter 30 minuter). Ett installerat spel dyker upp på hyllan efter nästa
  skanning, med Store:s bild som omslag. Nedladdningar över 2 GB fungerar på alla plattformar, inklusive 32-bitars
  versioner.
- **Källor**: varifrån listorna kommer - AutoBleem:s egen katalog, en TSV-lista som släpps in i
  `System/Extensions/store/sources/`, och adresser du lägger till med **Add a source URL**. Varje källa visar
  sin ikon i listan. Cross på en du lade till byter namn på den, ändrar dess adress, växlar mellan `http://`
  och `https://`, eller tar bort den.

![Store:s Apps-flik](../images/en/store-apps.jpg)

![En källas meny](../images/en/store-source-menu.jpg)

Det som AutoBleem:s katalog erbjuder listas också på nedladdningswebbplatsen, `https://autobleem.retromenele.pl/store/`.
**Du är ansvarig för vad källorna du lägger till innehåller.**

**Dina egna spel på ditt nätverk**: `abstored`, Store:s LAN-server, serverar en mapp av PS1-spel till
Store på samma nätverk. Den körs på vilken Linux-maskin som helst - en Raspberry Pi, en hemserver - och läser
bara mappen. Starta den med `abstored <games folder>`, öppna `http://<that machine>:8124/` i en webbläsare
för att se vad den serverar och eventuella problem, och lägg till `http://<that machine>:8124/store.tsv`
som källa. Färdiga program för Linux och Windows finns på Store-sidan, i dess **LAN server**-flik; att
ställa in det som en tjänst är `INSTALL-linux.md` (`ext_store/server/` i källan). **LAN Share** (avsnitt 5.2)
lägger spel och skivor från en PC på sådan server.

### 3.13 Skannrar processorer

**Skannrar processorer** är små program som varje skanning kör innan den läser dina spel. En kan förvandla
ett format som AutoBleem inte läser till ett som den gör - ett zipat spel till exempel - eller ändra ett
spelets data, såsom en översättningslapp. De bor i `System/Processors/<name>/` på stickan (på Pi dess
data-partition, på Windows datamappen); för att installera en, packar du upp dess mapp där. Nästa skanning
kör den.

- **Unzip medföljer AutoBleem**: den packar upp zippade PS1-spel i `Games/` innan skanningen läser dem, och
  zippade ROM-filer en i taget (arkad-uppsättningar stannar zippade). Att uppdatera AutoBleem uppdaterar den
  också, och lämnar den av om du gjorde det.
- En processor som redan har använts på ett spel körs inte på det igen förrän spelet ändras.
- Medan en processor fungerar visar bubblan längst upp till höger vad den gör; en varning eller misslyckande
  dyker upp på raden under den. `processors.log` i loggmappen har detaljerna.
- Att starta ett spel eller RetroArch stoppar en processor som ändrar filer; nästa skanning slutför dess arbete.

**L2 + R2 → Skannrar processorer** visar dem i den ordning de körs, en flik för PS1-spel och en för ROM-filer
(L1 / R1). **Square** plockar upp en processor och Upp / Ner flytta den - ordningen spelar roll: en processor
som packar upp måste komma före en som lägger lappar på vad som packades upp. **Cross** slår en av eller på,
**Triangle** låter den titta på varje spel igen vid nästa skanning, **Circle** går tillbaka och startar en
skanning om du ändrade något. En processor byggd för en annan maskin stannar på listan, grå.

![Skannrar processorer](../images/en/processors.jpg)

Att skriva din egen: Unzip:s sida, `https://github.com/autobleem2/proc_unzip`, förklarar allt en processor
måste göra, och `tools/proc_check.py` i AutoBleem:s källa kontrollerar en innan du delar den.

<!-- pagebreak -->

## 4. Skärmar

### 4.1 Spelhanterare

Skärmen heter *Spelbibliotek - välj spel*. PS1-spelen som en lista med bara titlar (spelets mapp finns i dess detaljer) och valda spelets omslag. Cross öppnar speleditor:n,
**Square raderar spelet** (dess mapp och, efter en andra fråga, dess sparpunkter), Triangle raderar varje
omslagsbild (PNG eller JPEG) bredvid spelen (skanningen tar dem från databaserna igen), L2 / R2 sida. Det lediga utrymmet på
enheten finns längst upp till höger. Spelhanterare väntar medan en skanning körs.

![Spelhanterare](../images/en/game-manager.jpg)

### 4.2 Hårdvaruinformation

Maskinens fakta - system, hårdvara, lagring med fritt utrymme, nätverksadresser, skärm- och
ljudstyrprogrammen, anslutna styrenheter - omläst varje sekund. Det är samma sida på varje plattform, konsolen
inräknad; skärmarna för nätverks- och handkontrollsinställningar är **Nätverk och handkontroller** (PSC-Bios, kapitel 6).

De två första enheterna visas som Spelare 1 och Spelare 2 – de portar som PS1-emulatorn tilldelar dem.
Alla ytterligare enheter visas som oanvända av PS1-emulatorn. RetroArch tilldelar enheter enligt egna
inställningar och kan ordna dem annorlunda. När en enhet ansluts eller kopplas från visar startaren kort
vilken pad som är Spelare 1 och Spelare 2. Circle går tillbaka till systemmenyn.

![Hårdvaruinformation](../images/en/hardware-info.jpg)

### 4.3 Knappguiden

Triangle på hyllan: varje knapp från varje skärm på en sida. När ett USB-tangentbord är ansluten eller
har använts visar en Tangentbords-kolumn tangenterna bredvid styrenhetsknapparna. Två rader förklarar vägen ut ur
ett spel: *Håll Select+Start eller Home i 2 sekunder: tillbaka till AutoBleem* och *Kort tryck på Select+Start
eller Home: emulatorns meny*.

![Knappguiden](../images/en/button-guide.jpg)

### 4.4 Tangentbordet på skärmen

Överallt där text skrivs - ett minneskort-namn, ett spelets titel, WiFi-lösenord, en källas adress - samma
tangentbord, utlagd som en telefons: bokstäver, en sida symboli (`/ \ : ? & = % @ #` och resten vad en adress
eller ett lösenord behöver) och två sidor med accenttecken, med Shift, sidtangenten, Mellanslag, Backspace
och Bekräfta på den nedersta raden. Riktningarna flyttar, Cross skriver, Triangle raderar, Square är ett
mellanslag, **L1** är Shift (två gånger för caps lock), **R1** nästa sida, **L2 / R2** flytta markören, Start
bekräftar, Circle avbryter. Ett USB-tangentbord skriver när som helst: Enter bekräftar, Esc avbryter.

![Tangentbordet på skärmen](../images/en/keyboard.jpg)

### 4.5 Virtuell handkontroll

*Virtuell handkontroll* i systemmenyn visar handkontrollerna så som programmet som betjänar dem ser dem. Den har
tre delar: *Handkontrollerna som appar får*, *Handkontroller som daemonen ser* och *Daemon*. En handkontroll kan ha
märkena *ansluten*, *inte läsbar*, *från handkontrolldatabasen*, *gissad av daemonen* eller *okänd drivrutin*, och
*Sök igen* läser av handkontrollerna en gång till. En del som bygget saknar säger *Inte i det här bygget*. Circle
går tillbaka till systemmenyn.

![Virtuell handkontroll](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. På PC:n

### 5.1 UpdateRoms - uppdatera en konsol-sticka

PlayStation Classic har inget nätverk, så RetroArch-listerna och skisskonsten på dess sticka görs på PC:n:
**UpdateRoms** gör på PC:n vad starlarens skanning gör på Pi, med PC:ns nätverk och konsolens vägar, så
konsolen startar och hittar allt på plats.

1. Kopiera dina ROM-filer på stickan under `RetroArch/roms/<system>/` (avsnitt 3.9). Mappnamnen måste vara
   RetroArch:s databasnamn; installationsprogrammet gör de vanliga.
2. Starta **`UpdateRoms\UpdateRoms.exe` från stickan** (installationsprogrammet satte den där). Den hittar
   stickan från var den sitter, visar en etapp-linje, framstegsstrecke och logg, och:
   - laddar ner RetroArch:s databasbunt när stickan inte har någon, och identifierar varje ROM med det - ett
     spel som databasen känner får sitt rätta namn;
   - skriver en spellista per system in i `RetroArch/bin/playlists/` med konsolens vägar, behåller vad
     RetroArch själv lade där;
   - hämtar skisskonsten för varje ROM som inte har någon från libretro:s miniatyrservrar in i
     `RetroArch/bin/thumbnails/`.
3. Ta bort stickan på ett säkert sätt och sätt in den i konsolen igen. RetroArch-fliken i set-väljaren
   listar varje system som har spel.

Kör det igen efter varje förändring av ROM-mapparna; en mapp som inget förändrades i hoppas över, så en
omkörning är snabb. Loggen är `System/Logs/updateroms.log`. Ett Raspberry Pi-kort i en kortläsare kan uppdateras
på samma sätt (`UpdateRoms.exe <drive> --target rpi`), även om Pi gör det själv när det har ett nätverk.

### 5.2 LAN Share - dina spel och skivor på servern på ditt nätverk

**LAN Share** (`LanShare.exe`, på Store-sidan i dess **LAN server**-flik) lägger dina PS1-spel på
Store:s server på ditt hemmanätverk - en `abstored` på Raspberry Pi, ett NAS eller en annan PC - och
läser en PS1-skiva i PC:ns CD/DVD-station för den. Store på konsolen, Pi eller PC installerar dem
sedan därifrån. Inget att installera; inställningarna hålls i `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![LAN Share-fönstret](../images/en/lanshare.jpg)

1. **Servern**: ange dess adress (`http://<its address>:<port>`, som Store har det) och tryck **Connect**.
   Dess spel och eventuella problem dess skanning hittade listas på vänster sida. För att lägga spel på den,
   ge en av:
   - **Share** - serverns spelmapp som den är delad på nätverket (Samba), t.ex. `\\raspberrypi\games`:
     LAN Share kopierar spelen där och ber servern att skanna. Själva servern förblir skrivskyddad.
   - **Token** - när servern startades med `--allow-uploads`: dess token (servern skriver ut den vid start
     och håller den i `<state>/upload-token`). LAN Share laddar upp över HTTP, och en stoppad nedladdning
     går vidare där den stannade.
2. **Spel på denna PC**: välj en mapp med spel (en mapp per spel), markera spel och tryck **Publish the
   ticked games**. **On the server** säger om servern redan har ett spel (efter serienummer, annars efter
   titel); sådant spel skickas aldrig två gånger. **Tick those not on the server** markerar resten.
3. **En skiva**: lägg en PS1-skiva i enheten och tryck **Read a disc and publish it**. Skivan läses helt in
   i en `.bin` + `.cue` (och en `.sbi` för ett LibCrypt-spel, när enheten ger delkanalen), uppkallad efter
   sin titel, kontrollerad mot den kända bra dumpen (när databaser väljs) och publicerad. För ett spel på
   flera skivor markera **The game has more than one disc**: LAN Share frågar om varje nästa skiva och
   publicerar dem tillsammans som ett spel.
4. **Remove from the server...** tar de valda spelen från servern. Ingenting raderas: varje flyttas in i en
   `.removed`-mapp bredvid serverns spel, och att flytta det tillbaka sätter det tillbaka.

**Databaserna** - AutoBleem:s omslag-mapp (`coversU/P/J.db`) och RetroArch:s `Sony - PlayStation.rdb` -
ge titlerna och kontrollen av en läst skiva; båda är valfria. **Also share the games on this PC with the
Store** (av som standard) serverar mappen på denna PC till Store direkt. Första gången frågar Windows om
dess brandvägg: tillåt bara privata nätverk.

<!-- pagebreak -->

## 6. Konsolverktygen (PlayStation Classic)

Två verktyg för en PlayStation Classic-sticka. Båda ritar sig själva i starlarens tema och språk, och båda
drivs av styrenheten - och, i styrenhetsguiden, av konsolens framknapparna. **PSC-Bios** är ett tillägg som
medföljer consolpaketet: posten *Nätverk och handkontroller* i snabbmenyn och systemmenyn öppnar det, och det är i listan över tillägg.
**ABFlashKit** är en app i Apps-uppsättningen.

### 6.1 PSC-Bios

Ett tillägg som medföljer consolpaketet, också tillgängligt på Raspberry Pi och PC-stickan. Den öppnas från
systemmenyn:s *Nätverk och styrenheter*-post (eller från listan över tillägg). När det tillägget är
installerat men inaktiverat, är *Nätverk och styrenheter*-posten i snabbmenyn och systemmenyn grå med
anmärkning "enable it in Extensions" - Cross där öppnar listan över tillägg till den.

Öppningsskärmen visar maskinens fakta: tid, tidszon, WiFi/Ethernet/Bluetooth-nätverkskort med sina
adresser, och varje ansluten styrenhet med om den har en knappkartläggning. Nätverk- och
Bluetooth-delarna behöver AutoBleem-kerneln på konsolen (avsnitt 6.2) eller systemverktygen på
Raspberry Pi / PC-stickan; styrenhetsguiden fungerar på vilket system som helst.

![PSC-Bios: Nätverk och styrenheter-hubben](../images/en/pscbios-main.jpg)

- **Select - Wi-Fi Network** (kernel eller NetworkManager): nätverksnamnet (skrivet, eller valt från scan),
  lösenord, drivrutinsläge, och *Apply / Restart Network*. Tidszonen ställs här också. Konsolens IP-adress
  visas när den är ansluten.
- **Square - Bluetooth Controllers**: en scan för Bluetooth-styrenheter (DualShock 4, osv.), för att para
  eller ta bort.
- **L1 - DualShock 3 Pairing**: USB-enbart samband för den första DualShock 3, genom kernelns sixaxis-plugin.
- **R1 - Controller Mapping**: kartläggningsguiden (nedan).
- **Triangle - About**, **Circle - back** till startaren.

**Styrenhetsguiden** visar den anslutna styrenheten rå - varje axel, knapp och hatt som siffror, och en
DualShock-bild som lyser upp när du trycker. Eftersom styrenheten under test inte kan litas på, drivs
guiden av konsolens **framknapparna**: **RESET** växlar till nästa styrenhet, **OPEN** startar kartläggningen
(besvarar då varje fråga - tryck knappen som lyser upp på bilden, eller OPEN när styrenheten inte har denna
knapp), **POWER** avbryter eller lämnar. Circle tryckt 2 sekunder på styrenheten lämnar guiden (en stapel
fylls och sidfoten säger "Hold 2 s: Exit"). Medan styrenheten inte har någon kartläggning ännu, gör vilken
knapp som helst tryckt 2 sekunder det ("Hold any button 2 s: Exit"). Ett kort tryck kartläggs normalt. På
tangentbord, Esc / Mellanslag / Enter står för POWER / RESET / OPEN. I slutet läggs den nya kartläggningen
in för ett test och OPEN sparar den under ett namn du väljer; startaren laddar den därifrån då.

![PSC-Bios: styrenhetskarleringsguiden](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - AutoBleem-kerneln

AutoBleem-kerneln är en valfri ersättare av konsolens Linux-kernel: den tar med en arbetande klocka,
USB-WiFi och Bluetooth-dongles (för PSC-Bios och Bluetooth-styrenheter) och framknappsstöd som emulatorn
använder för återställningspunkter. ABFlashKit installerar den, säkerhetskopierar konsolen först, och kan
sätta konsolen tillbaka till stock genom Sony:s egen recovery.

> **Detta verktyg skriver till konsolens flashminne.** En flash som blir avbruten - strömmen kapas,
> stickan dras ut - kan lämna konsolen oboot, och att installera en anpassad kernel gör garantin ogiltig.
> Håll konsolen på och stickan i den tills den startar om av sig själv. ABFlashKit öppnar denna varning;
> *I understand* går vidare, *Quit* lämnar.

![ABFlashKit-menyn](../images/en/abflashkit-menu.jpg)

- **Flash Kernel**: gör en recovery-backup av konsolens partitioner på stickan (`LBOOT.EPB`) om det inte
  finns någon än, kontrollerar det och kernel-avbildningen, skriver kerneln och AutoBleem:s systemfiler,
  och startar om. *All done - when the screen goes black replace power cord*: dra ut konsolens ström och
  sätt in den igen.
- **Full backup**: alla fyra partitioner till `LBOOT.EPB`, för senare återställning (föregående backup
  skrivs över efter en fråga).
- **Restore Mode**: kontrollerar att backupen är en original, ställer recovery-flaggan och startar om i
  Sony:s recovery, som återställer konsolen från `LBOOT.EPB` på stickan - vägen tillbaka till original
  firmware.

En framstegsstrecke under varje steg visar hur långt åtgärden är. Verktyget vägrar att flasha en konsol
som kör annan anpassad firmware (BleemSync, Project Eris): återställ den till stock först.

**Logga in från en PC.** Med AutoBleem-kerneln installerad (inte på en originalkonsol) kan du logga in på konsolen
över en USB-kabel:

1. Anslut konsolens micro-USB-port till PC:n med en USB-kabel. PC:n visar konsolen som en ny nätverksadapter;
   konsolens adress står i den adapterns inställningar på PC:n.
2. Logga in med `ssh root@<konsolens adress>`. Standardlösenordet är `autobleem`.

I stället för lösenordet kan du använda en nyckel: lägg din publika nyckel i filen `System/ssh/authorized_keys` på
stickan och starta om konsolen. Vid nästa uppstart läggs den till i root-kontot. Att uppdatera eller installera om
startaren tar inte bort den.

> **Standardlösenordet är detsamma på varje konsol**: den som kan sätta in en kabel i den kan logga in som root.
> Använd en nyckel där du kan, och lämna inte en konsol med standardlösenordet där andra kan komma åt den.

<!-- pagebreak -->

## 7. Om något går fel

- **Loggar**: AutoBleem håller loggar i minnet, så stickan inte skrivs till ständigt - de når `System/Logs/`
  på stickan, kortet eller datamappen bara när något går fel: en krasch av startaren, ett PS1-spel eller
  RetroArch sparar dem till `System/Logs/crash-<n>/` (de tre senaste hålls), och startaren säger det en gång
  när den kommer tillbaka. För att hålla varje logg, slå på *Options -> Diagnostics -> Keep logs on the stick*
  (från nästa start), eller gör en tom fil `System/Logs/keep` på en PC. På Pi eller PC visar
  *Hårdvaruinformation* var loggar är och Square sparar dem till `System/Logs/saved-<n>/`. Filerna: `autobleem.log`
  (startaren), `launch.log` och `pcsx.log` (PS1-start och emulator-utmatning), `retroarch.log`, och - alltid
  på stickan - `update.log` (online-uppdatering) och `updateroms.log` (UpdateRoms).
- **Bilden ber om en sticka, eller konsolen gick i viloläge**: det finns ingen sticka i konsolen, eller den drogs
  ur. Sätt in den (i vilken USB-port som helst; en framtill är bäst, avsnitt 2.1) innan de 5 minuterna har gått,
  eller tryck på Power. En sticka som inte togs bort på rätt sätt kontrolleras först - vänta tills
  förloppsstapeln är klar.
- **RetroArch säger att det behöver ett nyare systembibliotek än konsolen har**: konsolens eget bibliotek är för
  gammalt för den RetroArch. Använd den RetroArch som följer med AutoBleem.
- **Ett PSN-spel säger att det skyddas av sin PSN-licens och inte kan startas**: det spelet kan inte köras på
  AutoBleem.
- **Spel inte på hyllan**: kontrollera mappstrukturen (en mapp per spel, bildformaten i avsnitt 3.9).
  *Spelhanterare* listar de mappar som skanningen vägrade efter spelen, märkta *Not added*, med anledningen;
  Square tar bort sådan mapp. *Skanna om spel* i systemmenyn kör skanningen igen.
- **Ingen skisskonst**: skisskonst-databaserna installerades inte (kör installationsprogrammet igen med dem
  markerade), eller, för RetroArch-spel på en konsol, UpdateRoms har inte körts på PC:n.
- **Styrenhet gör ingenting eller har blandade knappar**: PSC-Bios:s styrenhetsguide (konsol) kartlägger
  den; på Pi eller PC visar Hårdvaruinformation-sidan vad SDL ser.
- **Konsol visar svart skärm efter spel**: AutoBleem bygger sitt fönster om av sig själv (upp till tre gånger);
  om det förblir svart, håll in Power-knappen och slå på konsolen igen.
- **Raspberry Pi**: `Alt+F2` ger en login-prompt på andra konsolen; SSH är aktiverat från första starten.
  `sudo journalctl -u autobleem` visar starlarens service; `sudo systemctl restart autobleem` startar om den.
  En första start som inte kunde slutföras (inget nätverk) provar igen vid nästa start.
- **Windows**: `Esc` lämnar startaren; datamappen är den som valdes i inställningen (`Documents\AutoBleem`
  som standard), loggar är i dess `System\Logs`.

**Konsolen startar om om och om efter en onlineuppdatering (minne formaterat som ext4).** Vissa användare formaterar minnet som ext4 (Linux) i stället för FAT32 eller exFAT. Fram till nästa AutoBleem-version packade onlineuppdateringen på ett sådant minne upp alla filer utan körbehörighet, så AutoBleem startar inte och konsolen startar om hela tiden. Minnen med FAT32 och exFAT påverkas inte.

**Åtgärd A** (kräver en Linux-dator): sätt i minnet och gör AutoBleems program körbara igen. Använd din egen monteringssökväg i stället för `/media/USER/STICK` (sista raden bara om RetroArch är installerat):

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Åtgärd B**: installera den senaste AutoBleem-versionen på minnet igen, som i avsnitt 2.1 (installationsprogrammet kräver en dator som kan läsa minnet; ett minne som den inte kan läsa måste formateras först, vilket raderar det - kopiera bort dina spel först).

> Använd **FAT32** (en vanlig konsol läser bara FAT32; exFAT kräver AutoBleem-kärnan, kapitel 6) - nästa version behåller behörigheterna och AutoBleem reparerar dem vid varje start.

AutoBleem är fri programvara (GNU GPL v3 eller senare), utan garanti. Support och nyheter: Discord-servern
länkad på About-skärmen, och https://autobleem.retromenele.pl/.
