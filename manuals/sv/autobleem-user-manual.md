# AutoBleem 2 - användarhandbok

AutoBleem 2 är en spelmeny för **PlayStation Classic** och, från och med version 2, även för **Raspberry Pi**,
**en PC som startar från ett USB-minne** och **Windows**. Dina PS1-spel står som omslag på en hylla, med
omslagsbild och fakta om varje spel, och startas i den medföljande PCSX-emulatorn. Installerar du RetroArch
bredvid kan du dessutom spela spel från andra system. Den här handboken går igenom installationen på varje
plattform, hur du använder AutoBleem till vardags och vilka verktyg som följer med.

> Allt du behöver ladda ner finns på **https://autobleem.retromenele.pl/**. Sidan är uppdelad per plattform:
> det du laddar ner står i panelen *Install* för din plattform, och *Build inputs* under den är sådant som
> installationsprogrammen hämtar på egen hand.

## 1. Det här får du

Med AutoBleem blir din PlayStation Classic - eller en Raspberry Pi, en gammal PC eller din Windows-dator - en
liten spelkonsol med en riktig meny för dina egna spel. Det här ingår:

- **Launchern.** Det är den du möts av när du slår på: en hylla med spelomslag som du bläddrar längs, med
  fakta om varje spel bredvid. Härifrån startar du spel, delar in dem i samlingar (PlayStation, RetroArch,
  Appar), ändrar inställningar, sköter minneskort och sparlägen och laddar ner appar och spel från Store.
  Den ser likadan ut och fungerar likadant på alla plattformar.
- **Två PS1-emulatorer.** `pcsx-abnxt` är den nya och används som standard; `pcsx-ab` är den klassiska
  emulatorn som AutoBleem alltid har haft med. Du väljer mellan dem i alternativen. Båda delar inställningar
  och minneskort, så du kan byta när du vill utan att förlora något.
- **RetroArch**, om du vill spela spel från andra system också - NES, SNES, Mega Drive, Game Boy,
  arkadmaskiner och mycket mer. Det är valfritt på alla plattformar. Kopiera in dina ROM-filer, så sorterar
  AutoBleem dem i listor och startar varje spel med rätt core. PlayStation-spel kan också köras i RetroArch;
  dess core *PlayStation 1* står överst i core-listan (avsnitt 3.9). Spel som Doom körs från dina egna
  spelfiler i en mapp som heter `Packages` (avsnitt 3.10).
- **Konsolverktygen.** *PSC-Bios* - i menyerna heter det *Nätverk och handkontroller* - ställer in WiFi,
  klockan, Bluetooth-handkontroller och knappmappning, både på konsolen och på en Raspberry Pi och
  PC-minnet. *ABFlashKit* installerar AutoBleem-kerneln på en PlayStation Classic (kapitel 6).
- **UpdateRoms** för Windows. PlayStation Classic har inget eget nätverk, så det här PC-programmet uppdaterar
  RetroArch-listorna och hämtar omslagsbilder till ett konsol-USB-minne medan det sitter i din dator.

![Launchern: hyllan med omslag, fakta om det valda spelet och knapptipsen](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Installation

### 2.1 PlayStation Classic

AutoBleem körs helt och hållet från ett USB-minne. Ingenting inne i konsolen ändras: tar du ut minnet fungerar
konsolen precis som förut. Allt du behöver är en Windows-dator, ett USB-minne (USB 2.0, 8 GB eller mer) och
konsolen.

Minnet behöver inte vara tomt, och det **formateras inte** om du inte själv ber om det. AutoBleem installeras
bredvid det som redan finns där, och ett minne som du redan använder med AutoBleem 1.0 uppgraderas på plats (se
nedan). För en omodifierad konsol måste minnet vara **FAT32**, eftersom konsolens egen kernel inte kan läsa
exFAT. När AutoBleem-kerneln väl är installerad (ABFlashKit, kapitel 6) startar konsolen även från ett
exFAT-minne, och då försvinner FAT32:s gräns på 4 GB per fil.

1. Ladda ner **AutoBleemInstaller-<version>.zip** från PlayStation Classic-panelen på webbplatsen och packa upp
   den var du vill. Där finns `AutoBleemInstaller.exe` och en README. Själva AutoBleem laddas ner under
   installationen, så datorn måste vara ansluten till internet.
2. Sätt i minnet och starta `AutoBleemInstaller.exe`. Välj **kanal** - *Release* är den testade versionen och
   det rätta valet för de flesta, *Testing* är nästa version medan den testas, och *Nightly* är det senaste
   utvecklingsbygget, som kanske inte fungerar - och välj sedan vilken enhet minnet har. Raden under visar
   vilken version av AutoBleem du är på väg att installera och vad som finns på minnet just nu: *a fresh
   install* (de andra filerna på minnet lämnas i fred) eller *AutoBleem <version> is on this stick: it will be
   updated* (dina spel, sparningar, minneskort och inställningar finns kvar).
   **Du behöver inte formatera.** Knappen **Format** bredvid enheten är bara till för ett helt nytt minne utan
   filsystem, ett minne som konsolen inte kan läsa (till exempel NTFS) eller ett som du vill tömma helt. Den
   frågar först och raderar sedan allt på minnet. Välj FAT32 där, om inte konsolen redan har AutoBleem-kerneln.
   Kryssa sedan i det du vill installera:
   - **Omslagsdatabaser** - omslag och beskrivningar för hela PS1-biblioteket, så att dina spel får sina omslag
     av sig själva (förvalt; ungefär 300 MB).
   - **RetroArch** - RetroArch med sina cores, extra program (Doom, Quake, Amiga, ...) och libretros
     grafikfiler, för spel från andra system. Inte förvalt; du kan lägga till det senare genom att köra
     installationsprogrammet igen.
   - **BIOS-filer** - BIOS-filerna som vissa RetroArch-cores behöver för att starta (bara tillsammans med
     RetroArch).
   - **Exempelspel** - några fria homebrew-spel, så att hyllan inte är tom första gången du startar.
3. Tryck på **Install** och vänta. Förloppsstaplarna och loggen visar varje steg. När det är klart heter minnet
   `SONY`, och en kopia av `UpdateRoms` har lagts på det (se kapitel 5).
4. Mata ut minnet på ett säkert sätt och sätt i det i konsolens **andra USB-port på framsidan** (den högra, för
   spelare 2) - den första behöver du till handkontrollen - och slå på konsolen. I stället för den vanliga
   menyn startar AutoBleem. Vill du ha en andra handkontroll använder du en USB-hubb i porten på framsidan
   eller en Bluetooth-handkontroll.

**Slå på och stänga av.** Med minnet isatt startar konsolen, blinkar med lampan några sekunder medan den
upptäcker AutoBleem och går sedan i viloläge innan något syns på skärmen. Det är helt normalt: AutoBleem
startar via konsolens egen uppdateringsfunktion, och det är så den fungerar. Tryck en gång på **Power**, så
dyker launchern upp.

Väljer du *Stäng av* i systemmenyn, eller trycker på konsolens Power-knapp, går konsolen in i **AutoBleems
viloläge**. Först kopplar AutoBleem bort minnet på ett säkert sätt, sedan lyser lampan **orange** - ett tecken
på att allt gick som det skulle. Nästa tryck på Power tar tillbaka launchern på några sekunder. **Medan lampan
lyser orange kan du dra ut minnet** och sätta det i datorn; Windows vill inte kontrollera det, eftersom det
kopplades bort korrekt. Sätt tillbaka det innan du trycker på Power. Drar du ur konsolens strömkabel går den
igenom startvilan igen nästa gång. Lyser lampan **röd** är konsolen helt avstängd.

**Porten på baksidan.** Micro-USB-porten på baksidan är konsolens strömingång. Med AutoBleem-kerneln klarar den
också en USB-enhet, men minnet hör hemma i en port på framsidan.

**Om minnet saknas.** Startar konsolen utan minne, eller drar du ut minnet medan AutoBleem körs, ber en bild dig
att sätta i det - vilken USB-port som helst går bra. AutoBleem väntar i 5 minuter och låter sedan konsolen gå i
viloläge; tryck på Power om du vill att den ska somna direkt.

![Bilden som ber dig sätta i minnet](../images/en/insert-stick.jpg)

**När minnet kontrolleras.** Om minnet inte kopplades bort korrekt - du drog ut det medan AutoBleem körde, eller
strömmen gick - kontrollerar AutoBleem det efter fel innan det används igen: vid start, när konsolen vaknar
eller när du sätter tillbaka minnet. En förloppsstapel visar hur långt kontrollen har kommit. På ett stort
minne kan det ta en stund; låt den bli klar och stäng inte av konsolen under tiden.

![Kontrollen av minnet](../images/en/stick-check.jpg)

**Uppdatera.** Vill du uppdatera ett minne kör du bara installationsprogrammet på det igen - knappen heter nu
*Update*. Den installerar den senaste versionen i den kanal du väljer. Dina spel, sparningar, inställningar och
ditt RetroArch-innehåll finns kvar; bara AutoBleems egna filer byts ut. En konsol med AutoBleem-kerneln och WiFi
kan också uppdatera sig själv (avsnitt 3.12).

**Uppgradera från AutoBleem 1.0 (eller AutoBleem-NG).** Du använder samma installationsprogram på samma minne,
utan att formatera:

1. Kopiera först hela minnet till datorn som säkerhetskopia - för säkerhets skull.
2. Sätt i det, starta `AutoBleemInstaller.exe` och välj kanal och enhet. Tryck **inte** på Format.
3. Tryck på **Install**. Installationsprogrammet flyttar över allt från den gamla strukturen till den nya:
   RetroArch, ROM-filerna och temana hamnar där AutoBleem 2 letar efter dem, och de gamla ROM-mapparna (`nes`,
   `snes`, ...) får RetroArchs systemnamn. Dina spel, sparlägen, minneskort, ROM-filer och RetroArch-sparningar
   finns kvar, liksom `config.ini` - där byts bara PS1-emulatorn till pcsx-abnxt.
4. Sätt tillbaka minnet i konsolen. Den första skanningen bygger upp spellistan och spellistorna på nytt. För
   att få omslagsbilder till dina RetroArch-spel kör du UpdateRoms på datorn (kapitel 5).

> En omodifierad konsol har varken klocka eller nätverk. Datum visas först när AutoBleem-kerneln är installerad
> (kapitel 6), och omslagsbilder till RetroArch-spel får du via UpdateRoms på datorn (kapitel 5).

Dina PS1-spel lägger du i mappen `Games` på minnet, en mapp per spel - avsnitt 3.10 förklarar hur.

### 2.2 Raspberry Pi

Med AutoBleem blir en Raspberry Pi en liten konsol: den startar direkt i launchern, utan något skrivbord
emellan. På webbplatsen finns två färdiga kortavbilder, en för 32 bitar och en för 64 bitar, och dessutom ett
paket för ett Raspberry Pi OS Lite som du redan har.

| Modell | 32-bitarsavbild | 64-bitarsavbild | Anmärkning |
|---|---|---|---|
| Raspberry Pi 5 | ja | ja | |
| Raspberry Pi 4 Model B, Pi 400 | ja | ja | |
| Raspberry Pi 3 Model B / B+ / A+ | ja | ja | räcker gott för launchern och PS1 |
| Raspberry Pi Zero 2 W | ja | ja | 512 MB RAM: PS1 går, de tyngre RetroArch-cores gör det inte |
| Raspberry Pi 2 Model B | ja | bara v1.2 | långsam med allt i 3D |
| Raspberry Pi 1, Zero, Zero W | nej | nej | ARMv6 - ingen av avbilderna fungerar |

**Ta 32-bitarsavbilden för PS1-spel.** Den klassiska `pcsx-ab` har sin snabba ARM-omkompilator bara i
32-bitarsversionen, så PS1-spel går långsammare på 64-bitarsbygget. 64-bitarsavbilden har däremot fler
RetroArch-cores, så välj den om de andra systemen betyder mer för dig än PS1.

**Med Raspberry Pi Imager:**

1. Installera Raspberry Pi Imager (raspberrypi.com/software). Under *Choose OS* väljer du *Use custom* och den
   `autobleem-<version>-rpi-armhf.img.xz` (32 bitar) eller `-arm64.img.xz` (64 bitar) som du har laddat ner. Du
   kan också lägga till en repository-URL i programmets inställningar och välja AutoBleem i listan. Det finns en
   per kanal: `https://autobleem.retromenele.pl/rpi-imager/os_list.json` för den senaste releasen,
   `.../os_list-testing.json` för bygget som testas och `.../os_list-nightly.json` för det senaste
   utvecklingsbygget. Fliken Raspberry Pi på nedladdningssidan listar de som finns, var och en med en
   *Copy*-knapp.
2. I Imagers anpassningsskärm (kugghjulet, eller frågan efter *Next*) anger du **användarnamn och lösenord,
   WiFi-nätverk och land, och slår på SSH**. AutoBleem behöver ett nätverk första gången den startar.
3. Skriv kortet, sätt det i din Pi med skärm och tangentbord eller handkontroll anslutna, och slå på strömmen.

**Den första starten** tar mellan 5 och 25 minuter, och skärmen berättar vad som händer. Finns det inget
nätverk frågar den efter ett: välj ditt WiFi i listan och skriv lösenordet. Sedan frågar den om RetroArch ska
installeras - svarar du inte inom en minut gör den det. Därefter förstoras systempartitionen, resten av kortet
blir partitionen `AUTOBLEEM` för dina spel, RetroArch installeras med sina cores, BIOS-paketen och exempelspelen,
och till sist startar den om direkt till launchern.

Vill du slippa svara på frågor vid första starten kan du skriva in svaren i förväg i **`autobleem.txt`** på
kortets startpartition - den kan öppnas och redigeras på vilken dator som helst:

| Nyckel | Standard | Betydelse |
|---|---|---|
| `root_gib` | 8 | Systempartitionens storlek i GiB; resten blir spelpartitionen. |
| `hdmi_mode` | 1920x1080@60 | Skärmläget under hela starten (`1280x720@60` för en äldre TV). |
| `retroarch` | (frågas) | `yes` / `no` - RetroArch och de andra systemen, eller bara PS1. |
| `thumbnails` | none | `boxarts` speglar hela samlingen av omslagsbilder, så att omslagen finns offline (~9000 filer). |
| `bios`, `downloads`, `samples` | yes | Sätt till `no` för att hoppa över BIOS-paketen, alla nedladdningar eller exempelspelen. |

**På ett Raspberry Pi OS Lite som du redan har** (Bookworm eller Trixie): kopiera `autobleem-rpi.tar.gz`
(eller arm64-varianten) till din Pi, packa upp den och kör `sudo bash install.sh`. Den ställer samma frågor,
gör plats för datapartitionen genom att krympa systempartitionen vid nästa start (`--shrink-root <GiB>`) och
lägger launchern på den första konsolen.

Efter installationen fyller du kortets **partition `AUTOBLEEM`** (exFAT) med dina spel: ta ut kortet och öppna
det på valfri dator, eller kopiera över nätverket (SSH är påslaget). PS1-spel hamnar i `Games/`, ROM-filer för
andra system i `RetroArch/roms/<system>/`, PS1-BIOS i `System/Bios/` (avsnitt 3.11) och teman i `Themes/`.

### 2.3 USB-minne för PC

Samma sak fungerar på alla datorer som kan starta från USB: minnet startar datorn direkt i AutoBleem och rör
inte datorns egen hårddisk. Systemet är 32-bitars, så även gamla datorer fungerar.

1. Skriv avbilden till ett USB-minne på 8 GB eller mer. **I Windows** använder du **AutoBleemFlasher**
   (PC-panelen på webbplatsen - packa upp den och kör `AutoBleemFlasher.exe`; den ber om administratörsrättigheter
   eftersom den skriver en hel disk). Välj kanal och minne, tryck på *Write* och bekräfta två gånger - programmet
   laddar ner avbilden, kontrollerar den, skriver den och läser tillbaka den. Bara USB-minnen och SD-kort visas,
   aldrig disken som Windows körs från, och **allt på det valda minnet raderas**. I Linux eller macOS laddar du
   ner `autobleem-<version>-pcusb-i386.img.xz` från PC-panelen och skriver den med
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (eller balenaEtcher).
2. Starta datorn från minnet (med datorns tangent för startmenyn - F12, F8, Esc ...). Både BIOS- och
   UEFI-start fungerar; **Secure Boot måste vara avstängt**.
3. Första starten går till som på en Pi: den frågar efter ett nätverk om ingen kabel är ansluten, frågar om
   RetroArch, installerar allt - ungefär åtta minuter med trådbundet nätverk - och startar om till launchern.

Efteråt har minnet en partition `AUTOBLEEM` för dina spel. Sätter du minnet i en Windows 10-dator som är igång
(version 1903 eller senare) dyker den upp som en extra enhet som du kan kopiera spel till. `autobleem.txt`
ligger på den första partitionen, med samma nycklar som på en Pi (utom `hdmi_mode` - en PC använder alltid
skärmens eget läge).

### 2.4 Windows

Vill du ha AutoBleem på din Windows-dator går det också att köra som ett vanligt program: i helskärm, där
emulatorerna och RetroArch startas som egna program.

1. Ladda ner **AutoBleemSetup-<version>.exe** och kör den. Den installerar för din användare, utan
   administratörsrättigheter: själva programmet under `%LOCALAPPDATA%\Programs\AutoBleem`, och datan (spel,
   inställningar, teman, RetroArch) i en mapp som du väljer - `Documents\AutoBleem` om du inte ändrar det.
2. Kryssa i komponenterna - omslagsdatabaserna, RetroArch (det officiella Windows-bygget med sina cores),
   BIOS-filerna, exempelspelen - och låt installationshjälpen ladda ner dem.
3. Starta AutoBleem från Start-menyn eller skrivbordet. På en PC fungerar tangentbordet som handkontroll
   (avsnitt 3.2).

För att uppdatera kör du en nyare installation ovanpå den gamla: programmet byts ut och din datamapp lämnas
som den är. Launchern kollar dessutom webbplatsen en gång om dagen och erbjuder en uppdatering när det finns
en (avsnitt 3.12).

<!-- pagebreak -->

## 3. Använda AutoBleem

### 3.1 Launchern

I launchern väljer du vad du vill spela. Dina spel står som omslag på en hylla, ungefär som fodralen skulle
stå i en riktig bokhylla, och du bläddrar längs den tills du hittar det du är ute efter. Allt annat i
AutoBleem - inställningarna, minneskorten, Store - öppnas härifrån, och hit kommer du tillbaka när du lämnar
ett spel.

Det valda spelet står mitt på hyllan, med en mjuk spegling under sig. Bredvid ser du fakta om spelet i ett
litet rutnät: utgivare, år, serienummer, region, hur många spelare det är för och när du senast spelade det.
När AutoBleem inte känner till en av uppgifterna hoppar den över raden i stället för att visa den tom. Bredvid
uppgifterna finns en spelaknapp. Ett spel som saknar omslagsbild visas som en skiva i det svarta facket i ett
tomt fodral, så att det ändå har sin plats på hyllan.

Hur launchern ser ut bestäms av temat. Standardtemat heter **ab2.0.0**. En ny installation byter till det, och
det gör även en uppdatering som har det med, men bara en gång - väljer du ett annat tema efteråt (avsnitt 3.6)
så får det vara kvar.

**Knapptipsraden** längst ner på skärmen visar vad knapparna gör just nu. Den har två rader med fyra platser
var. Den första raden gäller det valda spelet: spela det, spela det i RetroArch, öppna ikonraden under det
eller öppna snabbmenyn. Den andra raden är alltid densamma: Select väljer samling, Start tar ett slumpmässigt
spel, Triangle visar knappguiden och L2 + R2 öppnar systemmenyn. Ett tips är nedtonat så länge knappen inte
har något att göra.

**Nya spel hittas av sig själva.** Varje gång launchern startar skannar den din spelmapp i bakgrunden, så ett
spel som du kopierade in medan maskinen var avstängd dyker upp utan att du behöver göra något. Under
skanningen visar en bubbla uppe till höger hur långt den har kommit, och nya spel ställs på hyllan allteftersom
de hittas - du kan fortsätta bläddra under tiden.

**En ny installation** har ännu inga spel. I stället för en tom hylla ser du ett välkomstkort, *Hej och
välkommen till AutoBleem!*, som säger åt dig att lägga dina spel i `Games` och välja *Skanna om spel*. Kortet
nämner rätt ställe för din plattform: på ditt USB-minne (PlayStation Classic, PC-minne), på ditt SD-kort
(Raspberry Pi) eller i din AutoBleem-mapp (Windows). Kortet försvinner så fort en skanning hittar det första
spelet.

**Meddelanden** är bubblorna uppe till höger. De håller dig informerad utan att vara i vägen: skanningens
förlopp, namnet på samlingen du just bytte till (*Visar: ...*), en handkontroll med svagt batteri, en notis
efter en krasch, en skanningsprocessor som arbetar och en nedladdning från Store. Bubblan för en nedladdning
visar hastigheten och tiden som återstår, till exempel `1.4 MB/s · 0:42`. Hur länge informationsbubblorna
stannar bestämmer du själv: Alternativ → *Visningstid för meddelande*.

**Batterier i handkontrollerna.** På konsolen, en Raspberry Pi och PC-minnet (inte i Windows) visas varje
trådlös handkontroll som rapporterar sitt batteri som en liten ikon med procenttal, på en egen platta, staplade
nedåt från det övre vänstra hörnet. En handkontroll som spelar som spelare 1 eller spelare 2 har en etikett P1
eller P2, enligt alternativet *Byt spelare 1 / spelare 2* (avsnitt 3.6); en handkontroll som inte hör till någon
spelare, eller en tredje handkontroll, har ingen etikett. När batteriet börjar ta slut säger ett meddelande till
en gång, med handkontrollens namn och procenttalet.

**Kanaletiketten.** Kör du ett bygge som inte är en slutlig release påminner en liten etikett om det, under
batteriplattorna i det övre vänstra hörnet. Det är en bricka med kanalen och den korta versionen bredvid:
`ALPHA`, `BETA` eller `RC` för en förhandsversion, `TESTING` för andra förhandsversioner, `NIGHTLY` för ett
nattligt bygge och `DEV` för ett bygge som någon har gjort för hand (för `DEV` är versionen den commit det
byggdes från). En release har ingen etikett.

![Samlingsväljaren: tre flikar, och grupperna i den aktuella fliken med antalet spel](../images/en/set-picker.jpg)

### 3.2 Styrning

AutoBleem är gjort för att styras med bara handkontrollen, och knapparna betyder samma sak på alla skärmar:
Cross bekräftar, Circle går tillbaka, Triangle hjälper. Glömmer du vad en knapp gör står det på knapptipsraden
längst ner, och Triangle på hyllan öppnar knappguiden med alla knappar på alla skärmar (avsnitt 4.3). Så här
fungerar knapparna på hyllan:

| Knapp | På hyllan |
|---|---|
| Vänster / Höger | Går till förra eller nästa spel; håll in knappen för att fortsätta bläddra. |
| L1 / R1 | Hoppar till förra eller nästa begynnelsebokstav, så att du snabbt kommer igenom en lång hylla. På en tom hylla med en USB-enhet ansluten öppnar R1 *Skiva* (avsnitt 3.9a). |
| Cross | Startar det valda spelet: ett PS1-spel i PS1-emulatorn, ett RetroArch-spel i sin core och en app efter dess läs-mig-text. |
| Square | Startar det valda PS1-spelet i RetroArch i stället. Är en skiva i en USB-enhet vald kopierar den skivan i stället (*Kopiera skiva*, avsnitt 3.9a). |
| Circle | Tar dig tillbaka till skivvyn när det ligger en skiva i enheten (avsnitt 3.9a). |
| Triangle | Öppnar knappguiden. |
| Start | Väljer ett slumpmässigt spel ur den aktuella samlingen, för när du inte kan bestämma dig. |
| Select | Öppnar samlingsväljaren, där du väljer vilka spel hyllan visar (avsnitt 3.3). |
| Upp | Öppnar snabbmenyn (avsnitt 3.4). |
| Ner | Öppnar ikonraden under spelet (*INSTÄLLNINGAR*, *Spel*, *MINNESKORT*, *FORTSÄTT*); Upp stänger den igen. |
| L2 + R2 | Öppnar systemmenyn (avsnitt 3.5). |

**Med tangentbord.** På en PC utan handkontroll, eller med ett USB-tangentbord på konsolen, en Pi eller
PC-minnet, gör tangenterna knapparnas jobb. Piltangenterna är styrkorset, Enter är Cross, Esc eller Backspace
är Circle, Tab är Triangle och mellanslag är Square. F1 och F2 är Select och Start, Page Up och Page Down är L1
och R1, Home och End är L2 och R2, och F10 öppnar systemmenyn. På en utvecklingsdator stänger Esc programmet,
och mellanslag är Start.

**I alla listor och menyer** fungerar samma grepp: Upp och Ner flyttar markören, L2 och R2 bläddrar en sida,
L1 och R1 hoppar till första eller sista raden, Cross väljer och Circle går tillbaka. Du behöver aldrig leta
efter en Spara-knapp: en skärm med inställningar sparar dem när du lämnar den med Circle.

**Ut ur ett spel eller en app.** Håll in Start + Select, eller Home, i 2 sekunder, så är du tillbaka i
AutoBleem. Det fungerar med alla handkontroller - konsolens egen, en USB-handkontroll eller en
Bluetooth-handkontroll. Ett kort tryck på samma knappar öppnar i stället emulatorns meny. En app har ingen
sådan meny, så där är det bara den långa tryckningen som gör något.

![Ikonraden under det valda spelet](../images/en/launcher-icons.jpg)

### 3.3 Samlingarna

Ett stort bibliotek är lättare att bläddra i bit för bit. Med samlingarna kan du begränsa hyllan till en sorts
spel - bara dina favoriter, bara Super Nintendo-spelen, bara spelen i en viss mapp - så att du slipper bläddra
förbi hundratals omslag för att hitta det du vill spela.

Tryck på **Select**, så öppnas samlingsväljaren. Den har tre flikar, PlayStation, RetroArch och Appar. L1 och R1
byter flik, Upp och Ner går genom flikens grupper (L2 och R2 en sida i taget), och Cross visar den grupp du har
valt på hyllan. Circle (*Tillbaka*) stänger väljaren utan att ändra något. Längst ner står de här knapparna
också. Varje rad visar hur många objekt den innehåller. En tom grupp öppnas på en tom hylla, där ikonraden bara
har *INSTÄLLNINGAR*.

**Fliken PlayStation.** På en PlayStation Classic börjar den med *Alla spel* och *Interna spel* (de tjugo spel
som är inbyggda i konsolen), följt av *USB-spel* - allt i `Games/` - och en grupp för varje mapp som du har
skapat där, så att ett spel i en undermapp hör till den mappens grupp. Sedan kommer *Favoritspel*,
*Spelhistorik* och, när du har markerat minst ett spel som lightgun-spel, *Lightgun-spel*. En Raspberry Pi,
ett PC-minne och Windows har inga interna spel, så där börjar listan med *USB-spel*, som är hela ditt bibliotek.

**Fliken RetroArch** finns bara där RetroArch är installerat. Den har en grupp för varje system som du har spel
till, plus RetroArchs egna Favorites och History.

**Fliken Appar** sorterar programmen efter typ: *Alla appar*, sedan *Spel*, *Emulatorer*, *Verktyg*, *Media*
och *Övrigt*. Vilken grupp en app hör till står i dess fil `app.ini`. Här listas också **PE-apparna**, som är
Windows-program som körs av PE-köraren; en som konsolen inte kan starta är märkt *kan inte köras på den här
konsolen*. Där launchern visar den finns även en rad *Paket* i listan (avsnitt 3.10).

### 3.4 Snabbmenyn

Snabbmenyn är en kort lista med det du oftast behöver medan du bläddrar bland dina spel, så att du slipper
gräva i hela systemmenyn. Du öppnar den med **Upp** på hyllan, eller med **kugghjulsikonen** i ikonraden (raden
med *INSTÄLLNINGAR*, *Spel*, *MINNESKORT* och *FORTSÄTT*).

Upp och Ner flyttar mellan punkterna (från den sista hoppar markören runt till den första), Cross väljer en och
Circle stänger menyn. En rad under menyn beskriver den valda punkten. Det här finns i menyn:

- *Skanna om spel* letar direkt efter nya, ändrade eller borttagna spel - praktiskt när du just har kopierat in
  spel och inte vill vänta.
- *Store* öppnar AutoBleem Store, där du bläddrar bland och installerar spel, appar och tillägg (avsnitt 3.13).
- *RetroArch-cores*, där RetroArch är installerat, låter dig välja vilken core som spelar varje system.
- *Nätverk och handkontroller* öppnar skärmarna för Wi-Fi, Bluetooth-parkoppling och knappmappning (kapitel 6).
  Punkten finns bara när ett installerat tillägg tillhandahåller dem - PSC-Bios gör det på konsolen, en
  Raspberry Pi och PC-minnet. Är tillägget installerat men avstängt är punkten nedtonad, och beskrivningen säger
  att du ska slå på det under Tillägg; Cross öppnar då listan Tillägg precis vid det tillägget.
- *Starta om launchern* stänger AutoBleem och startar det igen (bara på konsolen, en Raspberry Pi och
  PC-minnet).
- *Systemmeny...* öppnar hela systemmenyn med allt det andra - Alternativ, Spelbibliotek, Stäng av och mer
  (avsnitt 3.5).

Allt här utom Store, RetroArch-cores och Starta om launchern finns även i systemmenyn.

![Snabbmenyn](../images/en/quick-menu.jpg)

### 3.5 Systemmenyn

I systemmenyn finns allt som AutoBleem kan göra utöver att spela: inställningarna, verktygen för ditt
bibliotek och dina minneskort, information om maskinen och sättet att stänga av. Tryck på **L2 + R2**
samtidigt (i vilken ordning som helst), så öppnas den ovanpå hyllan. Punkterna är grupperade under rubrikerna
*Bibliotek*, *System* och *Lämna*, med de två du använder mest överst. En rad längst ner i menyn beskriver den
valda punkten, så att du kan se dig omkring innan du väljer.

| Del | Punkt | Vad den gör |
|---|---|---|
| (överst) | *Skanna om spel* | Letar efter nya, ändrade eller borttagna spel nu. Skanningen håller dessutom själv ett öga på mappen, så den här behöver du bara när du inte vill vänta. |
| | *Tillägg* | Listar tilläggen på minnet, till exempel AutoBleem Store, så att du kan köra dem eller stänga av dem (avsnitt 3.13). |
| *Bibliotek* | *Spelbibliotek* | Visar PS1-spelen som en lista med sina mappar, där du kan ta bort ett spel eller rensa omslagen (avsnitt 4.1). Kan inte öppnas medan en skanning pågår. |
| | *Minneskort* | Hanterar dina delade minneskortsuppsättningar (avsnitt 3.8). |
| | *Skanningsprocessorer* | Bestämmer i vilken ordning programmen körs som varje skanning börjar med, och slår på eller av dem (avsnitt 3.14). Kan inte öppnas medan en skanning pågår. |
| *System* | *Alternativ* | Öppnar AutoBleems inställningar (avsnitt 3.6). |
| | *Nätverk och handkontroller* | Öppnar skärmarna för Wi-Fi, parkoppling av Bluetooth-handkontroller, inställning av DualShock 3 och knappmappning (kapitel 6). Finns bara när ett tillägg tillhandahåller dem - se nedan. |
| | *Hårdvaruinformation* | Visar fakta om maskinen - system, processor, lagring, nätverksgränssnitt, tidszon, skärm och handkontrollerna med sina mappningar - på samma sida på alla plattformar (avsnitt 4.2). Circle tar dig tillbaka till systemmenyn. |
| | *Virtuell handkontroll* | Visar vilka handkontroller apparna får och vilka handkontroller daemonen ser, vilket hjälper när en handkontroll inte fungerar i en app (avsnitt 4.5). Circle tar dig tillbaka till systemmenyn. |
| | *Programuppdatering* | Kollar på webbplatsen efter en nyare AutoBleem eller RetroArch nu, i stället för att vänta på den dagliga kontrollen (avsnitt 3.12). Känner launchern redan till en står det *Uppdatering tillgänglig* på raden. På en PlayStation Classic krävs AutoBleem-kerneln och ett Wi-Fi-nätverk. |
| | *Om* | Visar medverkande och licensen. |
| *Lämna* | *RetroArch* | Lämnar launchern för RetroArchs egen meny, med dess inställningar och innehållslistor; när du stänger RetroArch är du tillbaka i launchern. Finns bara där RetroArch är installerat. |
| | *Stäng av* | Stänger av maskinen efter att du har bekräftat (se nedan). |

**Nätverk och handkontroller** visas bara där ett installerat tillägg tillhandahåller posten `network`, vilket
ett tillägg anger med `Provides=network` i sin `extension.ini`. PSC-Bios gör det på konsolen, en Raspberry Pi och
PC-minnet. Är tillägget installerat men avstängt står punkten kvar i menyn, nedtonad, och beskrivningen säger
att du ska slå på det under Tillägg; Cross på punkten öppnar listan Tillägg direkt vid det tillägget.

**Stäng av** gör det som passar maskinen. På konsolen går den in i AutoBleems viloläge: minnet kopplas bort,
lampan lyser orange, och Power tar tillbaka launchern på några sekunder (avsnitt 2.1). En Raspberry Pi eller
en PC stängs av helt.

![Systemmenyn](../images/en/system-menu.jpg)

### 3.6 Alternativ

I Alternativ gör du AutoBleem till ditt eget: bilden på skärmen, hur launchern ser ut, språket, ljudet, vilken
PS1-emulator som kör dina spel. Du öppnar det från systemmenyn (*Alternativ*) eller med ikonen *INSTÄLLNINGAR*
under ett spel. Skärmen och språket ställer du oftast in en gång, och sedan kommer du tillbaka när något ser
konstigt ut på en viss TV eller när du vill ha omväxling.

Inställningarna är sorterade i grupper, var och en under en rubrik. Upp och Ner går från rad till rad, och
Vänster och Höger ändrar värdet på raden du står på: ett tryck flyttar ett steg, håller du in knappen fortsätter
det. L1 och R1 hoppar till första eller sista raden, och L2 och R2 bläddrar en sida. På en rad där du väljer
tema, musik eller teckensnitt tar Start ett på måfå. En inställning som är på eller av visar **PÅ** eller
**AV**. Varje ändring syns direkt, och Circle lämnar skärmen och sparar allt - det finns inget mer att bekräfta.
Det enda undantaget är skärmläget, som provas när du lämnar Alternativ (se *Bild:* nedan).

Vissa rader visas bara där de är meningsfulla: CRT-raderna bara med 4:3-bild, RetroArch-raderna bara där
RetroArch är installerat, de interna spelen bara på en PlayStation Classic.

| Grupp / inställning | Vad den är till för |
|---|---|
| *Gränssnitt*: *Bild:* | Ställer in skärmens upplösning, för launchern och PS1-emulatorn. *Auto* använder skärmens eget läge och visar vilket det är, till exempel *Auto (1920x1080)*; du kan också välja vilket läge som helst som skärmen anger. Konsolen erbjuder 720p, 1080p och *CRT 4:3* (720x480), läget för en gammal bildrörs-TV eller en inspelningsenhet för 4:3. Ändra den när bilden inte passar din TV eller ser suddig ut. Raden finns inte när AutoBleem körs i ett fönster på en utvecklingsdator. |
| *CRT-marginal:* | Krymper allt en aning, från 0 till 10 % i steg om 1 %, eftersom gamla TV-apparater skär av bildens kanter. Höj den tills knapptipsraden och hörnen syns helt. Visas bara med 4:3-utgång, gäller direkt och används redan före startbilden. |
| *Bildhöjd:* | Gör bilden högre eller lägre, från -40 till +40 i steg om 2, på alla 4:3-utgångar - *CRT 4:3*, eller ett 4:3-läge på en VGA- eller PC-utgång. Använd den när bilden på en gammal TV är hoptryckt eller går utanför över- och nederkanten. Den gäller direkt, och RetroArchs spelbild följer med. |
| *Emulatorns skärmskalning:* | Bestämmer hur PS1-emulatorn anpassar spelets bild till din skärm. *1x1* visar PlayStationens egna pixlar, små och exakta; *2x (heltal)* och *4:3 (heltal)* skalar bara i hela multiplar, vilket ger skarpast bild; *4:3* behåller bildens ursprungliga form; *Helskärm* drar ut bilden över hela skärmen. Den ersätter den gamla Widescreen-växeln. Den klassiska `pcsx-ab` och RetroArch kan bara helskärm och 4:3. |
| *Skärmgloria:* | När den står på PÅ fylls de tomma fälten bredvid spelets bild (där bilden inte täcker skärmen) med bildens eget mjuka sken i stället för svart. Fungerar med `pcsx-abnxt`. |
| *AutoBleem-tema:* | Ändrar launcherns utseende. Teman ligger i `Themes/`, och en tema-zip som du lägger där listas också med sitt namn. Temana som följer med AutoBleem skrivs över vid varje uppdatering, så vill du anpassa ett av dem bör du först kopiera det under ett nytt namn. Standard är **ab2.0.0**. |
| *Omslagsstil:* | Väljer vilket CD-fodral som ritas runt PS1-omslagen. |
| *Glans på omslaget:* | Låter ett blänk svepa över det valda omslaget varje gång hyllan stannar. |
| *Språk:* | Ställer in launcherns språk; det finns 17, och bytet sker direkt. |
| *Visningstid för meddelande:* | Bestämmer hur länge informationsbubblorna (*Visar: ...*, skanningens sammanfattning) stannar, från 0 till 20 sekunder; 0 visar *Av* och stänger av dem. Felmeddelanden har sin egen fasta tid, så att du aldrig missar något. |
| *Startskärm:* | Visar AutoBleem-bilden medan launchern startar; stäng av den för att gå direkt till hyllan. |
| *Animationer:* | Animerar bytet från en skärm till nästa; stäng av det om du hellre vill att varje skärm dyker upp direkt. |
| *Teckensnitt*: *Använd standardteckensnitt:* | När den står på PÅ använder launchern sitt eget teckensnitt (Red Hat Text); stäng av den för att använda teckensnittet som du väljer på nästa rad. |
| *Teckensnitt:* | Väljer ett eget teckensnitt: vilken `.ttf`- eller `.otf`-fil som helst i `resources/fonts`, `RetroArch/fonts` eller temats mapp. Raden visar namnet på teckensnittet som faktiskt används. |
| *Ljud*: *Musik:*, *Bakgrundsmusik:* | *Musik:* väljer låten som spelas i launchern - temats egen eller en fil från `resources/music`. *Bakgrundsmusik:* bestämmer om någon musik alls ska spelas. |
| *Emulering*: *PS1-emulator:* | Väljer emulatorn som dina PS1-spel startar i: `pcsx-abnxt`, standard (den aktuella PCSX-ReARMed med AutoBleems tillägg), eller `pcsx-ab`, den klassiska. Prova den andra när ett spel inte går bra. En sparpunkt som den ena har sparat kan du fortsätta från i den andra, om inte spelet kördes utan BIOS-fil. |
| *Byt spelare 1 / spelare 2 (PS1-emulatorer):* | Byter vilken av de två första handkontrollerna som är spelare 1 och vilken som är spelare 2, i båda PS1-emulatorerna - praktiskt när handkontrollerna sitter "fel" väg. Det spelar bara roll med två eller fler handkontroller anslutna; med en handkontroll spelar du alltid som spelare 1. RetroArch påverkas inte. Kan PS1-emulatorn som används inte byta ännu säger AutoBleem till. |
| *Spela alla PSX-spel med RA:*, *Uppdatera RA-konfiguration:*, *Behåll RetroArch-inställningar:* | De här tre finns bara där RetroArch är installerat. Den första startar alla PS1-spel i RetroArchs PS1-core (*PlayStation 1*; på en PC är det SwanStation). Den andra låter AutoBleem skriva sina inställningar i RetroArchs konfiguration när den startar ett spel där. Den tredje behåller en ändring som du gör i RetroArchs egen meny när RetroArch avslutas. |
| *Bibliotek*: *Visa interna spel:* | Visar konsolens inbyggda spel i PlayStation-listorna (bara PlayStation Classic). |
| *Rena spelnamn:* | När den står på PÅ (standard) visar RetroArch-spellistorna prydliga namn, utan taggar inom parentes som (USA), (Rev 1) eller [!]; AV visar filnamnen. Filnamnet finns kvar bland spelets uppgifter. PS1-spel påverkas inte, eftersom deras titlar kommer från databasen. |
| *Hämta omslag online:* | Låter skanningen ladda ner omslag som saknas från libretros servrar (Raspberry Pi, PC, Windows). |
| *Uppdateringar*: *Uppdateringar:* | Väljer vilka uppdateringar launchern letar efter (avsnitt 3.12): `release` (den testade versionen), `testing` (nästa version, som testas), `nightly` (det senaste utvecklingsbygget) eller `off`. Standard följer versionen du installerade. Visas inte på en utvecklingsdator. |
| *Diagnostik*: *Behåll loggar på USB-minnet:* | Sparar alla loggar på minnet från och med nästa start, inte bara efter en krasch - slå på den när du jagar ett problem (kapitel 7). |
| *Visa prestanda:* | Visar en ruta i nedre vänstra hörnet med bildfrekvens, processorbelastning, trådar och minne; i ett spel visar emulatorn också sin FPS och processorlast. |

**Byta skärmläge.** När du lämnar Alternativ med ett nytt läge under *Bild:* byter AutoBleem till det och frågar
*Behålla det här bildläget?*. Ser bilden bra ut bekräftar du. Visar TV:n ingenting, vänta bara: utan
bekräftelse går AutoBleem tillbaka till det förra läget efter en nedräkning.

**Teman på en 4:3-skärm.** I läget *CRT 4:3* visar temalistan bara teman som har en 4:3-layout. Har temat du
använder ingen sådan tar standardtemat dess plats när du har bekräftat läget (och vid varje start i det läget),
och ett meddelande talar om det: *Tema ändrat till standardtemat (CRT 4:3)*.

![Alternativen, i grupper](../images/en/options.jpg)

![Gruppen Bild: CRT-marginal och Bildhöjd](../images/en/options-display.jpg)

![Meddelandet efter bytet till CRT 4:3 med ett tema som saknar 4:3-layout](../images/en/crt43-theme-notice.jpg)

### 3.7 Inställningar för ett enskilt spel

Varje spel kan ha egna inställningar. De flesta spel fungerar fint som de är, men ibland behöver ett spel lite
hjälp - en skarpare eller mjukare bild, en överhoppad bildruta för att det ska flyta, ett annat minneskort - eller
så vill du markera det som favorit. I spelredigeraren ändrar du sådant för just det spelet, utan att röra något
annat.

Med ett spel markerat trycker du på **Ner** för att öppna ikonraden under det. Den har fyra ikoner:
*INSTÄLLNINGAR* (alternativen i avsnitt 3.6), *Spel* (spelets egna inställningar), *MINNESKORT* (dess
minneskort) och *FORTSÄTT* (dess sparlägen). Gå till en av dem och tryck på Cross för att öppna den.

**Spelredigeraren** (ikonen *Spel*) visar spelets uppgifter till höger - titel, utgivare, år, antal spelare,
mapp och minneskort - och dess inställningar till vänster. Upp och Ner flyttar mellan inställningarna och Vänster
och Höger ändrar dem, precis som i Alternativ; håller du in en knapp upprepas rörelsen. När du är klar sparar
Circle dina ändringar och tar dig tillbaka. Ett spel som saknar titel i sina data visas med namnet på sin mapp.

Inställningarna är indelade i fyra grupper:

- **Spel** handlar om hur AutoBleem behandlar spelet. *Favorit:* lägger det i gruppen *Favoritspel* i
  samlingsväljaren. *Lås data:* säger åt skanningen att lämna spelets titel, serienummer och skivlista precis
  som du har ställt in dem, så att en senare skanning inte skriver över dina ändringar. *Återuppta:* bestämmer
  vad som händer när du startar ett spel som har sparpunkter: *Fråga* visar väljaren för sparplatser, *Senaste
  platsen* fortsätter direkt från den nyaste platsen, och *Aldrig* startar alltid spelet från början. Där
  RetroArch är installerat finns två rader till. *Lightgun-spel:* är för ett ljuspistolspel: det hamnar i
  gruppen *Lightgun-spel* och körs alltid i RetroArch, eftersom RetroArchs PS1-core har GunCon (slår du på den
  slås även nästa rad på). *Spela med RA:* kör just det här spelet i RetroArch i stället för i PS1-emulatorn.
- **Bild** handlar om hur bilden ser ut. *Upplösning:* ritar spelet i 1x eller 2x (med den inbyggda
  grafikprocessorn), och *Ta bort sömmar:*, som bara fungerar med 2x, döljer de tunna linjer som kan synas
  mellan bildens delar i den storleken. *Dithering:* (*Av*, *På*, *Alltid*) styr det fina punktmönster som
  PlayStation använder för att blanda färger, och *Utjämning:* väljer en av emulatorns utjämnande skalare.
  *Filter:* bestämmer hur bilden skalas till skärmen: *Närmaste* visar rena pixlar, *Linjär* jämnar ut dem,
  *Skarp* och *Skarp (enkel)* håller pixlarna skarpa utan flimmer, och så finns *Quilez*. CRT-filtren
  *CRT (fast)*, *CRT (raster)* och *CRT-Pi* efterliknar en gammal TV och ritar sina egna scanlines, så
  scanline-raderna tonas ner medan något av dem är valt. Annars lägger *Scanlines:* till de mörka linjerna från
  en gammal TV, och *Ljusstyrka för scanlines:* bestämmer hur mörka de är. *Upplösning*, *Ta bort sömmar*,
  *Dithering*, *Utjämning* och alla filter utom *Linjär* och *Närmaste* är till för `pcsx-abnxt`; den klassiska
  `pcsx-ab` och RetroArch visar alla andra filter som *Närmaste*.
- **Rendering** har grafikens *Plugin:* och *Frameskip:* (*Auto*, *Av* eller 1 till 3 bildrutor). Att hoppa
  över bildrutor hjälper ett spel som går för långsamt att hålla farten, till priset av en mindre flytande bild.
- **Emulator** har *SpeedHack:*, processorns *Klocka:*, *SPU-interpolation:* (hur ljudet jämnas ut),
  *Startlogotyp:* och, med `pcsx-abnxt`, *Sony-hack:*. Stäng av *Startlogotyp:* för att hoppa över BIOS-skalet -
  det behövs för en homebrew-skiva som inte startar på grund av sin egen logotyp.

Bildens form och skärmens upplösning ställs inte in per spel utan för alla spel på en gång, i Alternativ
(*Emulatorns skärmskalning:* och *Bild:*).

**Fler knappar i redigeraren.** Triangle byter namn på spelet med skärmtangentbordet. Square ger spelet ett
annat minneskort (*Byt minneskort*). Så länge spelet fortfarande har sitt eget kort gör Start om det kortet till
en ny delad uppsättning, så att andra spel också kan använda det (*Dela minneskort*, avsnitt 3.8). De här två
finns inte för konsolens interna spel. Håller du in Vänster / Höger eller Upp / Ner upprepas rörelsen här, och
likaså i RetroArchs spelalternativ och core-skärmar.

Ett spel på en enhet som saknar filen `pcsx.cfg` kan inte spara sina inställningar; ändrar du en av dem säger
redigeraren *Inte sparat: spelet saknar pcsx.cfg*.

För en **skiva i enheten** (avsnitt 3.9a) är vissa inställningar meningslösa, så redigeraren tonar ner de
raderna, och raden längst ner säger *Inte tillgängligt för en skiva i enheten* när du går till en av dem.

![Spelredigeraren för en skiva i enheten](../images/en/game-editor-disc.jpg)

**Inställningar sparade i emulatorn.** Du kan också finjustera ett spel medan du spelar: emulatorns egen meny har
*Save settings for this game* (avsnitt 3.9). När ett spel har inställningar sparade där är det dem det spelas
med. Spelredigeraren visar då raderna under Bild, Rendering och Emulator nedtonade, med de sparade värdena,
under rubriken *Sparat i emulatorn*, så att du kan läsa dem men inte ändra dem. Vill du hellre använda
spelredigerarens inställningar igen väljer du *Lås upp inställningarna* och bekräftar: då raderas
inställningarna som emulatorn sparade, och raderna går att ändra igen. Båda emulatorerna, `pcsx-ab` och
`pcsx-abnxt`, läser och skriver samma sparade inställningar, så det spelar ingen roll vilken av dem som sparade.

![Spelredigeraren](../images/en/game-editor.jpg)

### 3.8 Minneskort och sparlägen

På en riktig PlayStation delade du ett eller två minneskort mellan alla dina spel och fick förr eller senare
slut på plats. I AutoBleem har varje PS1-spel sitt eget minneskort från början, så du behöver aldrig tänka på
utrymme eller på vilket kort en sparning ligger på. Kortet förvaras tillsammans med spelets sparlägen i
`Games/!SaveStates/<spelets mapp>/`.

**Delade minneskortsuppsättningar.** Ibland behöver spel se varandras sparningar - en uppföljare som läser in
sparningen från det första spelet, till exempel, eller skivorna i en serie som du vill ha på samma kort. Då gör
du en delad uppsättning: ett kort som flera spel använder. Uppsättningarna ligger i `Games/!MemCards/`, och du
hanterar dem med *Minneskort* i systemmenyn. Square skapar en ny uppsättning (du skriver namnet med
skärmtangentbordet), Cross byter namn på den valda och Triangle tar bort den, efter att ha frågat först. För att
lägga ett spel på en uppsättning använder du *Byt minneskort* i dess spelredigerare (avsnitt 3.7) eller dess
ikon *MINNESKORT*.

**Minneskortsredigeraren** öppnas från ett spels ikon *MINNESKORT*. Den visar spelets kort och ett andra kort
sida vid sida, med varje sparnings ikon och titel, precis som minneskortsskärmen på originalkonsolen. Square
kopierar den valda sparningen till det andra kortet, Triangle raderar den, och Select defragmenterar ett kort så
att de lediga blocken samlas och en stor sparning får plats igen. Med Start väljer du vilken uppsättning som
visas till höger, och Cross läser in båda korten från minnet igen. Ett kort som spelet inte har skrivit till än -
ett spel som du inte har sparat i - är tomt och visar *inget kort än* bredvid namnet. Har du ändrat något frågar
AutoBleem *Vill du spara minneskortsdata?* innan den lämnar redigeraren, läser in korten igen eller visar en
annan uppsättning.

![Minneskortsredigeraren](../images/en/memory-card-editor.jpg)

**Sparpunkter.** Många PS1-spel låter dig bara spara på vissa ställen, och du hinner inte alltid fram till ett
innan du måste sluta. Det löser sparpunkterna: när du lämnar ett PS1-spel med konsolens Reset-knapp (eller via
emulatorns meny på en Pi eller en PC) sparar AutoBleem ett sparläge precis där du var. Medan det skrivs, på väg
ut ur spelet, visar emulatorn *Please wait...*. Nästa gång fortsätter du från just det ögonblicket.

Du hittar dem under spelets ikon *FORTSÄTT*. Ett spel med en sparpunkt visar en liten bild av den på ikonen; ett
spel utan sparpunkter har ikonen nedtonad. Väljaren för sparplatser har fyra platser, som visas som inramade
kort, var och en med en bild av ögonblicket, platsens nummer och datum. Den nyaste är märkt **NYAST**, och en
plats som inte har använts visar *Ingen sparpunkt*. Cross fortsätter spelet från den valda platsen, och Triangle
raderar den. Om väljaren alls visas när du startar spelet bestäms av spelets inställning *Återuppta:*
(avsnitt 3.7).

PS1-spel som du spelar i RetroArch har också sparplatser. Varje plats har ett märke - AutoBleem 2-logotypen
eller RetroArch-logotypen - så att du ser vilken emulator som skrev den.

![Väljaren för sparplatser](../images/en/resume-picker.jpg)

### 3.9 Starta spel, RetroArch och appar

Att starta spel är det du kommer att göra mest, så det räcker med en knapp: välj spelet på hyllan och tryck på
**Cross**. Ett PS1-spel öppnas i helskärm i den PS1-emulator som du valt i Alternativ (avsnitt 3.6) och körs
tills du lämnar det. Vill du hellre spela ett PS1-spel i RetroArch - för att det går bättre där, eller för att du
gillar RetroArchs alternativ - trycker du på **Square** i stället.

**Lämna ett spel.** På PlayStation Classic gör konsolens egna knappar det du väntar dig. **Reset** på framsidan
tar dig tillbaka till launchern och sparar en sparpunkt där du var, så att du kan fortsätta senare (avsnitt
3.8); det fungerar även när menyn i spelet är öppen. **Power** stänger av konsolen. En Raspberry Pi eller en PC
har inga sådana knappar, så där lämnar du spelet via emulatorns meny, som beskrivs nedan.

Det finns också en väg ut som fungerar likadant med alla handkontroller - konsolens egen, en USB-handkontroll
eller en Bluetooth-handkontroll: **håll in Start + Select, eller Home, i 2 sekunder**, så är du tillbaka i
AutoBleem. Ett kort tryck på samma knappar öppnar i stället emulatorns meny. Launchern påminner om båda i sina
tips (*Håll Select+Start eller Home i 2 sekunder: tillbaka till AutoBleem* och *Kort tryck på Select+Start eller
Home: emulatorns meny*). En app har ingen emulatormeny, så där är det bara den långa tryckningen som gör något.
På konsolen stoppar Reset alltid även en app.

**Menyn i spelet.** Med `pcsx-abnxt` har emulatorn en egen meny för det du behöver medan du spelar: spara, byta
skiva, justera bilden, välja handkontroller. Tryck på menyknappen - Home på en handkontroll som har en sådan,
**Select + Start** på en utan, eller **Esc** på ett tangentbord - så pausas spelet bakom menyn, med den senaste
bilden i bakgrunden. Håller du in menyknappen i 2 sekunder blir det samma sak som Reset: du lämnar spelet. Menyn
har tre flikar, och L1 och R1 byter mellan dem. Den kommer ihåg var du var, så nästa gång öppnas den på samma
flik och rad.

- Fliken **Spel** handlar om själva spelet. *Resume game* stänger menyn och låter dig spela vidare. Under
  *Saves* sparar *Quick save* ögonblicket du är i och *Quick load* tar tillbaka det. *Load autosave* tar dig
  tillbaka till hur spelet såg ut för upp till 30 sekunder sedan - emulatorn håller den kopian i minnet medan du
  spelar, och den räddar dig från ett misstag som inte går att ångra. Under *CD disc* är *Change disc* till för
  spel på flera skivor när de ber om nästa, och *Reset game* startar om spelet. *Save settings for this game*
  sparar inställningarna som du har valt för just det här spelet (avsnitt 3.7). *PCSX menu* öppnar
  PCSX-ReARMeds egna sidor, med dess alternativ, fusk och About, och *Exit* tar dig tillbaka till AutoBleem.
- På fliken **Bild** ändrar du hur spelet ser ut medan du tittar på det: *Bild*, *Upplösning* (1x eller 2x),
  *Ta bort sömmar*, *Dithering*, *Scaling*, *Utjämning*, *Filter*, *Scanlines* och *Ljusstyrka för scanlines*.
  Det är samma inställningar som i spelredigeraren (avsnitt 3.7), och varje rad har en hjälptext till höger som
  säger vad den gör. *Bild* är skärmens upplösning; på konsolen väljer du den i Alternativ, och här visas den
  bara. Filtret CRT-Pi är för tungt för konsolen i 1080p. En rad som inte gäller är nedtonad, och hjälptexten
  förklarar varför.
- Fliken **Handkontroller** bestämmer vad som sitter i PlayStationens två portar, *Controller 1* och
  *Controller 2*: en vanlig (digital) handkontroll, en analog handkontroll (DualShock), en pistol eller
  ingenting. Vissa spel fungerar bara med en viss sorts handkontroll. Ändringen gäller när du går tillbaka till
  spelet.

Menyn är ritad i launcherns egen ab2.0.0-stil, så den känns inte som ett annat program, och den visar batteriet
i dina handkontroller och bilden från din senaste snabbsparning.

**RetroArch-spel.** Ett spel från ett annat system startar i RetroArch, med den core som launchern har valt för
det systemet. När du är klar tar *Close Content* eller *Quit RetroArch* i RetroArchs meny dig tillbaka till
launchern. Vill du ändra vilken core som spelar ett system öppnar du *RetroArch-cores* i snabbmenyn (avsnitt
3.4); listan öppnas med coren *PlayStation 1* överst. Och vill du komma åt RetroArchs egen meny (XMB) för dess
inställningar och egna innehållslistor väljer du *RetroArch* i systemmenyn: RetroArch öppnas då utan något
inläst.

![Fönstret RetroArch-cores, med coren PlayStation 1 överst](../images/en/retroarch-cores.jpg)

**Appar.** Appar är program snarare än spel: konsolverktygen och, på konsolen, de extra program som följer med
RetroArch-paketet - Doom, Quake, Amiga och fler. Du hittar dem i samlingen Appar. Innan en app startar visar
AutoBleem dess läs-mig-text, så att du vet vad det är och hur den styrs. Cross startar den, och Circle tar dig
tillbaka till hyllan.

![En apps läs-mig-text, som visas innan appen startar](../images/en/app-start.jpg)

**En apps inställningar.** Många appar är skrivna för en viss handkontroll, så du kan ändra hur de ser din.
Välj appen, öppna ikonraden och välj *Spel*: appens *Spelinställningar* öppnas (*Ändra hur det här programmet
startas*). *Handkontrollsläge:* bestämmer vilken handkontroll appen får veta att den har. *Automatiskt* använder
det som appen själv ber om; *PSC-handkontroll* och *Xbox 360-handkontroll* presenterar din handkontroll som
konsolens egen eller som en Xbox 360-handkontroll, och *PSC-handkontroll (system)* och *Xbox 360-handkontroll
(system)* gör samma sak via själva systemet. Prova ett annat läge när en app inte reagerar på din handkontroll
som den ska. *Styrkors som spak:* låter styrkorset styra den analoga spaken, för en app som bara lyssnar på
spaken, och *Spak som styrkors:* gör tvärtom.

Vissa appar ställer en fråga första gången du startar dem. En vill veta *Vilka kontroller har din
handkontroll?*, så att den kan ställa in styrningen: svara *Ett styrkors* för en handkontroll med bara
styrkors, eller *Analoga spakar*. En app som kör Windows frågar *Vad vill du göra?* och erbjuder att köra
Windows, installera det, köra DOS eller avinstallera Windows. När en app låter dig välja en knapp ber den dig
att *Tryck på en av knapparna.*

![En apps spelinställningar](../images/en/app-game-settings.jpg)

Ett Windows-program som körs av PE-köraren (en PE-app, avsnitt 3.3) pratar med dig via AutoBleems egna
skärmar: ett meddelande som den vill visa dyker upp som *Meddelande*, och en fråga med svarsalternativ som
*Välj ett alternativ*, båda med appens namn som rubrik.

![En fråga från en PE-app, visad som en AutoBleem-skärm](../images/en/pe-dialog.jpg)

### 3.9a En skiva i en USB-enhet

Du kan koppla en vanlig CD/DVD-enhet med USB till konsolen, en Raspberry Pi eller en PC som har startat från
AutoBleem-minnet och spela direkt från en original-skiva till PlayStation - utan att kopiera något. En skiva som
du lägger i dyker upp i launchern som ett spel till. Det fungerar inte i Windows.

**Kopiera en skiva till minnet.** Vill du alltid ha spelet till hands, utan skivan, trycker du på Square
(*Kopiera skiva*). AutoBleem frågar först om spelet ska kopieras och hur mycket plats det tar, och sparar det
sedan i mappen `Games` som en enda CHD-fil (ett spel på flera skivor får dessutom en `.m3u`-fil, så att
skivbytet fungerar i spelet). Under kopieringen ser du hastigheten och tiden som återstår, och *Avbryt* stoppar
den. När den är klar står spelet på hyllan precis som alla andra. AutoBleem kopierar inte ett spel som redan
finns i `Games`, och inte heller ett som det inte finns plats för - då talar den om hur mycket plats som
behövs. En repad skiva går också att kopiera: de delar som inte gick att läsa fylls med nollor, och AutoBleem
säger hur många de var. En sådan kopia kanske fungerar, kanske inte.

Square erbjuder kopiering för alla PlayStation-spelskivor i skivvyn, även för en som omslagsdatabaserna inte
känner till. Ett spel som databaserna känner till kopieras under sin titel; för ett spel på flera skivor
kopierar du skivorna en efter en, och `.m3u`-filen listar dem i ordning, skiva 1 först. En skiva som
databaserna inte känner till får sitt serienummer som namn i stället, kopieras som en enda skiva och har inget
omslag på hyllan. Kopieringsfönstret, *Kopierar skivan*, står kvar på skärmen tills kopieringen är klar eller
avbruten - launchern väntar så länge - och visar hastigheten som en multipel av en vanlig CD-enhet. Misslyckas
kopieringen säger AutoBleem varför.

![Kopiera en skiva](../images/en/disc-copy.jpg)

**Spela från skivan.** När du lägger i en skiva öppnas **skivvyn** av sig själv så fort skivan är inläst. Den
visar skivans omslag - från omslagsdatabaserna eller hämtat online - med serienummer och titel, och Cross startar
spelet. Ett PS1-spel som spelas från skivan har sina sparpunkter och sparningar i en egen mapp, så du kan sluta
och fortsätta senare precis som med ett spel på minnet. Efter spelet, eller när du har varit i alternativen
eller i ett tilläggs inställningar, kommer du tillbaka till skivvyn. Lämnar du den med Circle för att bläddra
bland dina andra spel ligger skivan kvar i enheten, och Circle på hyllan tar fram vyn igen; på en tom hylla
öppnar även R1 (*Skiva*) den. På en hylla med spel gör R1 som vanligt och hoppar mellan begynnelsebokstäver.
När du tar ut skivan stängs skivvyn.

![Skivvyn](../images/en/disc-view.jpg)

**Enhetsbrickan** högst upp på skärmen visar vad enheten håller på med, så att du vet om du ska vänta. Utan
ansluten enhet syns ingenting. En enhet utan skiva visar en svag skivikon. Medan en skiva läses in blinkar
ikonen och det står *Läser skivan...*, och när den är klar lyser ikonen upp med skivans titel. Lägger du i en
skiva som varken är ett PlayStation-spel eller en ljud-cd säger brickan *Det här är inte en PlayStation-skiva*,
och kan enheten inte läsa skivan just då står det *Skivan kan inte läsas just nu*.

![Enhetsbrickan](../images/en/disc-chip.jpg)

**Ljud-cd.** Enheten spelar också musik-cd. En ljud-cd öppnar **CD-spelaren** i stället för skivvyn. Den visar
skivan som *Ljud-cd* med låtlistan och den totala speltiden, och raden under säger vilket spår som är valt och
om upprepning och blandning är påslagna. En skiva som spelaren inte kan spela är märkt *Den här skivan kan inte
spelas*. Så här fungerar knapparna:

| Knapp | I CD-spelaren |
|---|---|
| Cross | Spelar det valda spåret. |
| Start | Pausar musiken och startar den igen. |
| Square | Stoppar musiken. |
| L1 / R1 | Går till förra eller nästa spår. |
| L2 / R2 | Spolar bakåt eller framåt i spåret, fem sekunder i taget. |
| Triangle | Ändrar vad som upprepas: ingenting, hela skivan eller det aktuella spåret. |
| Select | Slår på eller av blandning, så att spåren spelas i slumpvis ordning. |
| Circle | Lämnar CD-spelaren. |

![CD-spelaren](../images/en/cd-player.jpg)

**LibCrypt-skivor.** Vissa PlayStation-spel, de flesta europeiska, har ett kopieringsskydd som heter LibCrypt.
För att kunna köra dem behöver emulatorn en liten `.sbi`-fil med skyddets data. AutoBleem hämtar den filen från
webbplatsen av sig själv innan en sådan skiva spelas och när du kopierar den, och filen kopieras med spelet. För
det behövs ett nätverk: på en Raspberry Pi eller en PC det som redan finns, på konsolen det Wi-Fi som du har
ställt in i PSC-Bios.

För en skiva i enheten är vissa av spelets inställningar meningslösa, så spelredigeraren tonar ner de raderna
(avsnitt 3.7).

### 3.10 Lägga till spel

AutoBleem hittar dina spel av sig själv, så länge de ligger på rätt ställe. Här får du veta var varje sorts spel
ska ligga, så att varje skanning ställer dem på hyllan med namn och omslag.

**PS1-spel** lägger du i mappen `Games`, **en mapp per spel**, med spelets namn. Du kan också samla spel i egna
mappar, och varje sådan mapp blir en grupp i samlingsväljaren (avsnitt 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                en mapp med spel: en egen grupp i samlingsväljaren
    Klonoa/                   Klonoa.pbp
```

AutoBleem läser de vanliga formaten för skivavbilder: `.cue` med sin `.bin` (eller `.img`), `.pbp`, `.chd`
(även zstd-komprimerade), `.iso` och `.ecm`, som skanningen avkodar åt dig. Ett zippat spel fungerar också:
processorn **Unzip** packar upp det innan skanningen läser det (avsnitt 3.14).

Du behöver inte vara noggrann. Ett spel på flera skivor hör hemma i en mapp med alla sina skivor, men kopierar du
in mappar som heter `Game (Disc 1)`, `Game (Disc 2)` och så vidare slår skanningen ihop dem till en mapp `Game`.
Spel som du lägger som lösa filer direkt i `Games/` sorterar skanningen också in i egna mappar.

**Namn och omslag** kommer av sig själva. Skanningen läser varje skivas serienummer och hämtar titel, utgivare,
år, antal spelare och region från RetroArchs PlayStation-databas eller från omslagsdatabaserna. Vill du ha ett
eget omslag lägger du en PNG- eller JPEG-bild bredvid spelets avbild, med samma namn. Annars kommer omslaget
från omslagsdatabaserna eller, med RetroArch installerat, från libretros samling av miniatyrbilder; på en
Raspberry Pi, en PC eller i Windows hämtas ett omslag som saknas online (Alternativ → *Hämta omslag online*). Blir
något fel i skanningen rättar du det i spelredigeraren och slår på *Lås data*, så att nästa skanning behåller
din ändring.

**Spel för andra system** hamnar under `RetroArch/roms/`, **en mapp per system, med samma namn som i RetroArchs
databaser** - till exempel `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo Entertainment
System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` eller `FBNeo - Arcade Games` (eller `Arcade`).
Mapparna skapas åt dig, och ROM-filerna får ligga kvar zippade. På en Raspberry Pi, en PC eller i Windows läser
skanningen dem själv och skriver RetroArchs spellistor. Ett konsolminne klarar inte det på egen hand, så där kör
du **UpdateRoms** på datorn (kapitel 5).

**Appar** lägger du under `Apps/<namn>/`, var och en med en `app.ini` - namn, ikon och vad som ska köras - och en
`run.sh`.

**Paket.** Vissa appar är spelmotorer: de behöver data från ett spel som du äger innan de kan spela det. Doom,
Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, DOS-spel och fler
fungerar så. Lägg spelets filer i en mapp `Packages` på minnet, en mapp per spel - till exempel
`Packages/Doom/DOOM2.WAD` - så känner AutoBleem igen dem med hjälp av en tabell som följer med
(`rc/packages.ini`). I en mapp som den känner igen räknas lösa spelfiler som egna paket. AutoBleem läser bara
dina filer och ändrar dem aldrig. Ett paket kan också komma från Store (avsnitt 3.13).

Där launchern visar den listar raden *Paket* på fliken Appar (avsnitt 3.3) de speldata som har hittats. Cross på
en post öppnar dess **Package info**: vad datan innehåller, en beskrivning, var filerna ligger och var de kommer
ifrån (dina egna filer, Store, en mod eller filer som följer med en app), om det är shareware eller fritt och
vilken installerad app som kör den. Kan ingenting som du har installerat köra den säger informationen det.

När du startar en motor-app letar AutoBleem efter speldata som den kan köra. Finns det en uppsättning startar
spelet direkt. Finns det flera frågar en lista (*Välj speldata*) vilken du vill spela, och den står på den du
valde sist. Finns det ingen talar AutoBleem om vilka data appen behöver och var de ska ligga, och ingenting
startar.

**Dina egna spel.** När AutoBleem inte känner igen vissa data står det i deras Package info *Inte igenkänt. Om
det är ett spel, se manualen: Dina egna spel.* Tabellen känner bara till de spel den gjordes för. För ett annat
spel skriver du en rad för det i en egen `packages.ini` i mappen `Packages`: AutoBleem läser din fil först, så
dina rader vinner.

![Paketväljaren, där du väljer vilka speldata du vill starta med](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Skanna en del.** Har du bara lagt till spel i en samling eller mapp kan *Skanna om spel* skanna just den
delen, vilket går fortare än att skanna allt, och bubblan försvinner när skanningen är klar.

**Teman** lägger du under `Themes/<namn>/`, med sin `theme.json` och sina bilder - eller så lägger du temats zip
som den är i `Themes/`.

### 3.11 PS1-BIOS

BIOS är PlayStationens eget startprogram, och emulatorn kör spelen mest troget med det riktiga. På en
**PlayStation Classic** behöver du inte göra något: emulatorn använder konsolens eget BIOS. På en **Raspberry
Pi, en PC och i Windows** lägger du dina egna PS1-BIOS-filer i `System/Bios/`: `romw.bin` (den amerikanska och
europeiska SCPH-5501/5502) och `romJP.bin` (den japanska SCPH-5500, som används för japanska spel).
Installationsprogrammen fyller i dem från RetroArchs BIOS-paket, om inte dina egna filer redan finns där - dina
ersätts aldrig. Utan dem kör emulatorn sitt inbyggda HLE-BIOS, en ersättare som många spel godtar och vissa
inte, så om ett spel inte vill starta är ett saknat BIOS det första du ska kontrollera.

### 3.12 Uppdateringar

AutoBleem håller sig själv uppdaterat, så du får nya funktioner och rättningar utan att installera om något.
När launchern startar, och sedan en gång om dagen, kollar den på webbplatsen om det finns en ny version i dess
**kanal**. Kanalen väljer du i Alternativ → *Uppdateringar*: `release`, `testing`, `nightly`, eller `off` om du
inte vill att den ska leta alls. Vill du inte vänta på den dagliga kontrollen kollar *Programuppdatering* i
systemmenyn direkt.

När det finns en ny version frågar AutoBleem vad du vill göra. *Uppdatera nu* laddar ner och installerar den,
vilket tar några minuter. *Påminn mig i morgon* frågar igen om ett dygn, och *Hoppa över den här versionen*
frågar inte mer om just den versionen. Vad du än väljer finns dina spel, sparningar och inställningar alltid
kvar; efter en uppdatering skannar launchern dina spel en gång till. Kanaletiketten i det övre vänstra hörnet
(avsnitt 3.1) visar vilket bygge du har.

Hur uppdateringen installeras beror på maskinen:

- På en **Raspberry Pi** och **PC-minnet** körs installationsprogrammet igen efter nedladdningen, med samma
  förloppsskärm som vid första starten, och erbjuder även en nyare RetroArch. Sedan är launchern tillbaka.
- I **Windows** öppnas den nedladdade installationen, installerar den nya versionen och startar den nya
  launchern.
- På en **PlayStation Classic** kan bara en konsol med **AutoBleem-kerneln** (ABFlashKit, avsnitt 6.2) och ett
  **Wi-Fi-nätverk** inställt i PSC-Bios (avsnitt 6.1) uppdatera sig själv - en omodifierad konsol har inget
  nätverk, så där letar launchern inte. Efter *Uppdatera nu* stängs launchern, och AutoBleem-bilden står kvar på
  skärmen medan minnet uppdateras, vilket tar några minuter; sedan startar den nya launchern. Utan nätverk säger
  *Programuppdatering* *Inte ansluten*. Alla konsolminnen kan också uppdateras från en dator med
  `AutoBleemInstaller.exe` (avsnitt 2.1).

### 3.13 Tillägg och AutoBleem Store

**Tillägg** ger launchern nya saker - egna skärmar och funktioner - utan att AutoBleem självt ändras. AutoBleem
Store och PSC-Bios är tillägg. Ett tillägg ligger i `Extensions/<namn>/` på minnet (på en Raspberry Pi på dess
datapartition, i Windows i datamappen); för att installera ett packar du upp dess zip där.

För att se dem öppnar du systemmenyn (**L2 + R2**) och väljer *Tillägg*. De som kommer från AutoBleem-teamet
står överst, och eventuella andra följer under *Tillägg från tredje part*. Cross kör det valda tillägget, och
Triangle stänger av det, eller slår på det igen. PSC-Bios på konsolen är undantaget: med det ställer du in
Wi-Fi, handkontrollerna och klockan, så där går det inte att stänga av. När ett tillägg inte kan köras står det
på raden varför - det behöver ett nätverk och det finns inget, det är inte gjort för det här systemet, det
gjordes för en annan version av AutoBleem och behöver uppdateras, eller det gick inte att läsa in. Om ett
tillägg någon gång stoppar launchern stänger AutoBleem av det, och listan talar om det; du kan slå på det igen
här.

![Listan Tillägg](../images/en/extensions.jpg)

**AutoBleem Store** är det första tillägget: ett ställe där du bläddrar bland appar och spel och installerar dem
med ett tryck, på alla system som AutoBleem körs på. En PlayStation Classic behöver AutoBleem-kerneln för det,
eftersom Wi-Fi följer med kerneln. Du öppnar Store från snabbmenyn (*Store*, avsnitt 3.4). Det har fyra flikar,
och L1 och R1 byter mellan dem.

Flikarna **Apps** och **Games** listar vad källorna erbjuder, varje objekt med bild, version, storlek och den
lilla ikonen för källan det kommer från. Fliken Apps listar också PE-appar, med licens och källa, och
speldatapaket (avsnitt 3.10). Det som du redan har installerat har märket *Installed*. Knapptipsraden visar
knapparna som gäller för den valda raden:

| Knapp | På flikarna Apps och Games |
|---|---|
| Cross | Installerar objektet - eller uppdaterar det, försöker igen efter ett fel eller avbryter en nedladdning som väntar eller pågår. |
| Triangle | Tar bort något som Store har installerat. |
| Square | Läser in listorna från källorna på nytt. |
| L2 / R2 | Hoppar till förra eller nästa begynnelsebokstav. |
| Select | Visar en källa i taget, när du vill se vad en enskild källa erbjuder. |
| Start | Söker bland titlarna. |

Bilderna sparas när de har laddats, så listorna kommer upp snabbt nästa gång, och en bild som inte gick att
ladda kan du försöka med igen.

Fliken **Downloads** visar vad som laddas ner, väntar, har misslyckats eller är installerat, med en
förloppsstapel som rör sig jämnt. Du behöver inte sitta och titta på den: nedladdningarna fortsätter i
bakgrunden, även när du har lämnat Store, och medan du är någon annanstans i launchern visar en bubbla den
pågående nedladdningen med hastighet och återstående tid (till exempel `1.4 MB/s · 0:42`). Att starta ett spel
eller stänga av pausar dem bara, och en stoppad nedladdning fortsätter där den slutade. Försvinner nätverket står
det *Waiting for the network* vid objektet, och nedladdningen fortsätter där den var när nätverket är tillbaka;
efter 30 minuter utan nätverk ger den upp. Nedladdningar över 2 GB fungerar på alla plattformar, även i
32-bitarsbyggena. Ett spel som du installerar dyker upp på hyllan efter nästa skanning, med bilden från Store som
omslag.

Fliken **Sources** visar var listorna kommer ifrån, var och en med sin ikon: AutoBleems egen katalog, alla
TSV-listor som ligger i `System/Extensions/store/sources/` och adresserna som du själv lägger till med *Add a
source URL*. Cross på en källa som du har lagt till låter dig byta namn på den, ändra dess adress, växla den
mellan `http://` och `https://` eller ta bort den.

![Fliken Apps i Store](../images/en/store-apps.jpg)

![Menyn för en källa som du har lagt till](../images/en/store-source-menu.jpg)

Vad AutoBleems egen katalog erbjuder listas också på nedladdningssidan, på
`https://autobleem.retromenele.pl/store/`. En källa som du själv lägger till är en annan sak: **du ansvarar
själv för vad källorna som du lägger till innehåller.**

**Dina egna spel i ditt nätverk.** Har du dina PS1-spel på en annan dator hemma kan `abstored`, Stores
LAN-server, erbjuda dem till Store över nätverket, så att du installerar dem som vilket objekt som helst. Den
körs på alla Linux-maskiner - en Raspberry Pi, en hemserver - och läser bara mappen, utan att någonsin ändra
den. Starta den med `abstored <spelmapp>` och öppna sedan `http://<den maskinen>:8124/` i en webbläsare: sidan
visar vad den delar ut och eventuella problem som den har hittat. I Store lägger du sedan till
`http://<den maskinen>:8124/store.tsv` som källa. Färdiga program för Linux och Windows finns på Stores sida,
under fliken **LAN server**, och `INSTALL-linux.md` (`ext_store/server/` i källkoden) förklarar hur du sätter
upp den som en tjänst. **LAN Share** (avsnitt 5.2) lägger spel och skivor från en PC på en sådan server.

### 3.14 Skanningsprocessorer

Skanningsprocessorer förbereder dina spel innan AutoBleem läser dem. En processor är ett litet program som varje
skanning kör först. Den kan göra om ett format som AutoBleem inte läser till ett som den läser - packa upp ett
zippat spel, till exempel - eller ändra ett spels data, som att lägga på en översättningspatch. Processorer
ligger i `System/Processors/<namn>/` på minnet (på en Raspberry Pi på dess datapartition, i Windows i
datamappen); för att installera en packar du upp dess mapp där, så kör nästa skanning den.

**Unzip följer med AutoBleem.** Den packar upp zippade PS1-spel i `Games/` innan skanningen läser dem, och
zippade ROM-filer en i taget; arkadset förblir zippade, eftersom arkad-cores läser dem så. När AutoBleem
uppdateras uppdateras även Unzip, och har du stängt av den förblir den avstängd.

En processor gör sitt jobb en gång: när den har tagit hand om ett spel körs den inte på det igen förrän spelet
ändras. Medan en processor arbetar visar bubblan uppe till höger vad den gör, och en varning eller ett fel syns
på raden under; `processors.log` i loggmappen har detaljerna. Startar du ett spel eller RetroArch stoppas en
processor som ändrar filer, så att spelet får maskinen för sig själv, och nästa skanning gör klart jobbet.

För att hantera dem öppnar du systemmenyn (**L2 + R2**) och väljer *Skanningsprocessorer*. Du ser dem i den
ordning de körs, med en flik för PS1-spelen och en för ROM-filerna; L1 och R1 byter flik. Ordningen spelar roll:
en processor som packar upp måste komma före en som patchar det uppackade.

| Knapp | I Skanningsprocessorer |
|---|---|
| Square | Plockar upp den valda processorn, så att Upp och Ner flyttar den till sin nya plats; Square släpper den igen. |
| Cross | Stänger av processorn, eller slår på den igen. |
| Triangle | Låter processorn titta på alla spel igen vid nästa skanning, även de som den redan har tagit hand om. |
| Circle | Går tillbaka, och startar en skanning om du har ändrat något. |

En processor som är byggd för en annan maskin står kvar i listan, nedtonad, så att du ser att den finns men att
den inte körs här.

![Skanningsprocessorer](../images/en/processors.jpg)

Vill du skriva en egen processor förklarar Unzips sida, `https://github.com/autobleem2/proc_unzip`, allt som en
processor måste göra, och `tools/proc_check.py` i AutoBleems källkod kontrollerar din innan du delar den.

<!-- pagebreak -->

## 4. Skärmar

### 4.1 Spelbibliotek

I Spelbibliotek städar du i ditt PS1-bibliotek. Använd det när du vill ta bort ett spel som du inte spelar
längre, öppna ett spels inställningar utan att först leta upp det på hyllan, eller låta AutoBleem hämta alla
omslag på nytt. Du öppnar det från systemmenyn (L2 + R2, *Spelbibliotek*). Medan en skanning pågår är det
nedtonat och väntar tills skanningen är klar.

Skärmen har rubriken *Spelbibliotek - välj spel*. Till vänster ser du alla dina PS1-spel som en lista med titlar
i bokstavsordning; till höger det valda spelets omslag med utgivare, år, serienummer och mappen det ligger i.
Det lediga utrymmet på enheten visas uppe till höger, så att du ser hur mycket plats du får tillbaka när du tar
bort något. Upp och Ner går genom listan, L2 / R2 bläddrar en sida och L1 / R1 hoppar till första eller sista
spelet.

- **Cross** öppnar det valda spelet i spelredigeraren - samma redigerare som ikonen *Spel* på hyllan (avsnitt
  3.7). När du lämnar den är du tillbaka på samma spel i listan.
- **Square tar bort spelet.** AutoBleem frågar först och tar sedan bort spelets hela mapp. Om spelets sparlägen
  och minneskort inte används av något annat spel ställer den en fråga till: om de också ska tas bort. Svara nej
  om du kanske vill ha tillbaka spelet senare med dina sparningar.
- **Triangle tar bort alla omslagsbilder** (PNG eller JPEG) som ligger bredvid dina spel, efter en fråga. Det är
  praktiskt när du har samlat på dig omslag som du inte gillar: nästa skanning hämtar omslagen från
  omslagsdatabaserna igen.

Längst ner i listan, efter spelen, kan du se mappar märkta *Inte tillagt*. Det är mappar i `Games` som skanningen
tittade på men inte kunde göra till ett spel. Välj en, så står det till höger var den ligger och varför den inte
lades till - en cue-fil som saknas, till exempel (kapitel 7). Square tar bort en sådan mapp efter en fråga. När
du lämnar med Circle efter att ha ändrat något skannar AutoBleem spelen igen.

![Spelbibliotek: listan med spel till vänster, det valda spelets omslag och uppgifter till höger](../images/en/game-manager.jpg)

### 4.2 Hårdvaruinformation

Hårdvaruinformation är sidan du tittar på när du vill veta vad din maskin är och vad den ser: hur mycket plats
som är kvar på minnet, vilken nätverksadress den har, vilka drivrutiner för bild och ljud den använder och vilka
handkontroller som är anslutna. Det är samma sida på alla plattformar, konsolen inräknad. Du öppnar den från
systemmenyn (L2 + R2, *Hårdvaruinformation*); Circle tar dig tillbaka till systemmenyn.

Sidan visar systemet, hårdvaran, lagringen med ledigt utrymme, nätverksadresserna, drivrutinerna för bild och
ljud och de anslutna handkontrollerna. Den läser in allt på nytt varje sekund, så du kan ha den öppen medan du
kopplar in en handkontroll eller en kabel och se ändringen dyka upp. Den visar bara saker - för att ställa in
nätverket eller en handkontroll använder du *Nätverk och handkontroller* (PSC-Bios, kapitel 6).

Delen om handkontrollerna svarar på frågan "vilken handkontroll är vilken spelare?". De två första visas som
*Spelare 1* och *Spelare 2* - de portar som PS1-emulatorn ger dem. Alla fler handkontroller visas som *används
inte av PS1-emulatorn*. RetroArch delar ut portarna enligt sina egna inställningar, så i ett RetroArch-spel kan
ordningen vara en annan. Du behöver inte öppna sidan varje gång: så fort en handkontroll kopplas in eller dras
ur visar launchern en kort stund vilken handkontroll som nu är spelare 1 och vilken som är spelare 2.

![Hårdvaruinformation: fakta om maskinen och de anslutna handkontrollerna](../images/en/hardware-info.jpg)

### 4.3 Knappguiden

Glömmer du vad en knapp gör någonstans trycker du på **Triangle** på hyllan. Knappguiden visar alla knappar på
alla skärmar på en sida, så att du kan slå upp dem utan att lämna launchern. Är ett USB-tangentbord anslutet,
eller har ett använts, visar en kolumn *Tangentbord* motsvarande tangent bredvid varje knapp.

Guiden påminner också om det enda som är värt att komma ihåg för varje spel: hur du kommer ut ur det. Håll in
Select + Start, eller Home, i 2 sekunder för att gå tillbaka till AutoBleem; ett kort tryck öppnar i stället
emulatorns meny.

![Knappguiden: knapparna på alla skärmar, med tangenterna bredvid](../images/en/button-guide.jpg)

### 4.4 Skärmtangentbordet

Varje gång AutoBleem behöver att du skriver något - namnet på en minneskortsuppsättning, ett spels titel, ett
WiFi-lösenord, adressen till en källa i Store - dyker samma skärmtangentbord upp, så att du kan skriva med bara
handkontrollen. Det är upplagt som tangentbordet på en mobiltelefon. Förutom bokstäverna har det en sida med
symboler, med `/ \ : ? & = % @ #` och resten av det som en adress eller ett lösenord behöver, och två sidor med
bokstäver med accenter. Den nedersta raden har Shift, tangenten som byter sida, mellanslag, Backspace och
Bekräfta.

Flytta mellan tangenterna med riktningsknapparna och tryck på **Cross** för att skriva den som markören står på.
**Triangle** raderar en bokstav och **Square** skriver ett mellanslag. **L1** är Shift; tryck två gånger för
Caps Lock. **R1** går till nästa sida med tangenter, och **L2 / R2** flyttar markören i texten. **Start**
bekräftar det du har skrivit och **Circle** avbryter. Är ett USB-tangentbord anslutet kan du när som helst skriva
på det i stället: Enter bekräftar och Esc avbryter.

![Skärmtangentbordet](../images/en/keyboard.jpg)

### 4.5 Virtuell handkontroll

Appar - programmen i samlingen Appar, som Doom eller Quake - läser inte din handkontroll själva. Ett litet
hjälpprogram, daemonen för den virtuella handkontrollen, läser de riktiga handkontrollerna och ger varje app en
handkontroll som den förstår. Den här sidan visar vilka handkontroller hjälpprogrammet ser och hur det läser
dem. Titta här när en app inte reagerar på din handkontroll, eller när knapparna är omkastade. Du öppnar den från
systemmenyn (L2 + R2, *Virtuell handkontroll*); Circle tar dig tillbaka till systemmenyn.

Under *Handkontroller som daemonen ser* står varje handkontroll med ett nummer och sitt namn. Bredvid kan du läsa
tre saker: om hjälpprogrammet kunde öppna handkontrollen (*ansluten*) eller inte (*inte läsbar*); vilken
drivrutin handkontrollen kom via; och var knapplayouten kommer ifrån - *från handkontrolldatabasen* betyder att
handkontrollen är känd och att knapparna sitter där de ska, *gissad av daemonen* betyder att den inte är känd
och att hjälpprogrammet har gissat så gott det kan. Känns knapparna fel i en app är en gissad layout den
troligaste orsaken.

Hjälpprogrammet körs bara medan en app körs, så sidan frågar det en gång när den öppnas. Kopplar du in en
handkontroll medan sidan är öppen trycker du på **Cross** (*Sök igen*) för att fråga igen. I Windows finns inget
sådant hjälpprogram, och sidan säger *Inte i det här bygget*.

![Virtuell handkontroll: handkontrollerna som apparnas hjälpprogram ser](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. På datorn

### 5.1 UpdateRoms - uppdatera ett konsolminne

På en Raspberry Pi, en PC eller i Windows sorterar launcherns skanning själv dina RetroArch-spel i listor och
hämtar deras omslagsbilder. PlayStation Classic kan inte göra det, eftersom den saknar eget nätverk.
**UpdateRoms** gör jobbet på din Windows-dator i stället: det använder datorns nätverk men skriver allt med de
sökvägar som konsolen förväntar sig, så när du sätter tillbaka minnet startar konsolen och hittar allt på plats.
Kör det varje gång du har lagt till eller tagit bort RetroArch-spel på ett konsolminne.

1. Kopiera dina ROM-filer till minnet under `RetroArch/roms/<system>/` (avsnitt 3.10). Mappnamnen måste vara
   RetroArchs databasnamn; installationsprogrammet har redan skapat de vanligaste.
2. Starta **`UpdateRoms\UpdateRoms.exe` från minnet** - installationsprogrammet lade det där. Det räknar själv
   ut vilket minne det ligger på. Medan det arbetar ser du en rad som säger vad det gör, en förloppsstapel och
   en logg.
   - Har minnet ingen RetroArch-databas än laddar det först ner RetroArchs databaspaket. Sedan identifierar det
     varje ROM-fil med det, så att ett spel som databasen känner till får sitt riktiga namn.
   - Det skriver en spellista per system i `RetroArch/bin/playlists/`, med konsolens sökvägar. Det som
     RetroArch själv har lagt till i de listorna behålls.
   - För varje ROM-fil utan omslagsbild hämtar det ett omslag från libretros servrar för miniatyrbilder till
     `RetroArch/bin/thumbnails/`.
3. Mata ut minnet på ett säkert sätt och sätt tillbaka det i konsolen. Fliken RetroArch i samlingsväljaren
   listar nu alla system som har spel.

Du kan köra det så ofta du vill: en mapp där ingenting har ändrats hoppas över, så en andra körning går fort.
Går något fel finns loggen i `System/Logs/updateroms.log` på minnet. Ett kort för Raspberry Pi i en kortläsare
kan uppdateras på samma sätt, med `UpdateRoms.exe <enhet> --target rpi`, även om en Pi gör det själv när den
har nätverk.

### 5.2 LAN Share - dina spel och skivor på servern i ditt nätverk

Store kan installera spel från en server i ditt eget hemnätverk (avsnitt 3.13). **LAN Share** är
Windows-programmet som fyller den servern från din dator: det lägger PS1-spelen som du har på datorn på servern,
och det kan läsa en PS1-skiva i datorns CD/DVD-enhet och lägga den där också. Servern är en `abstored` som körs
på en Raspberry Pi, en NAS eller en annan dator. När ett spel väl ligger där kan Store på konsolen, din Pi eller
datorn installera det därifrån.

Du hämtar `LanShare.exe` på Stores sida, under fliken **LAN server**. Det finns inget att installera: starta
programmet, så sparar det sina inställningar i `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![Fönstret LAN Share: serverns spel till vänster, spelen på den här datorn till höger](../images/en/lanshare.jpg)

1. **Anslut till servern.** Skriv in dess adress så som Store har den, `http://<dess adress>:<port>`, och tryck
   på **Connect**. Spelen som redan finns på servern, och eventuella problem som dess egen skanning har hittat,
   visas till vänster. För att kunna lägga spel på servern behöver LAN Share en av två vägar in:
   - **Share** är serverns spelmapp så som den delas i ditt nätverk (Samba), till exempel
     `\\raspberrypi\games`. LAN Share kopierar spelen dit och ber servern att skanna; servern själv läser
     fortfarande bara sin mapp.
   - **Token** är för en server som har startats med `--allow-uploads`. Skriv in dess token - servern skriver ut
     den när den startar och sparar den i `<state>/upload-token`. LAN Share laddar då upp via HTTP, och en
     uppladdning som avbryts halvvägs fortsätter där den slutade.
2. **Publicera spelen på din dator.** Välj mappen där dina spel ligger (en mapp per spel), kryssa i de du vill ha
   och tryck på **Publish the ticked games**. **On the server** visar om servern redan har ett spel - den jämför
   serienumret, eller titeln när det inte finns något serienummer - och ett spel som servern redan har skickas
   aldrig två gånger. **Tick those not on the server** kryssar i alla de andra åt dig.
3. **Publicera en skiva.** Lägg en PS1-skiva i datorns enhet och tryck på **Read a disc and publish it**. LAN
   Share läser hela skivan till en `.bin` + `.cue`, med spelets titel som namn. För ett LibCrypt-spel skriver
   det också `.sbi`-filen, om enheten kan läsa subkanalen. Har du valt databaserna (se nedan) jämför det kopian
   med den kända korrekta dumpen. Sedan publiceras spelet. För ett spel på flera skivor kryssar du först i
   **The game has more than one disc**: LAN Share ber dig om varje nästa skiva och publicerar dem tillsammans som
   ett spel.
4. **Ta bort spel från servern.** Markera dem och tryck på **Remove from the server...**. Ingenting raderas:
   varje spel flyttas till en mapp `.removed` bredvid serverns spel, och flyttar du tillbaka det är det tillbaka.

**Databases** är valfria. Pekar du LAN Share på AutoBleems omslagsmapp (`coversU/P/J.db`) och RetroArchs
`Sony - PlayStation.rdb` använder det dem för att namnge spelen och för att kontrollera en skiva som det har
läst.

Vill du hellre inte kopiera något kryssar du i **Also share the games on this PC with the Store** (det är
avstängt från början): LAN Share delar då ut spelmappen på din dator direkt till Store. Första gången du gör det
frågar Windows om sin brandvägg - tillåt bara privata nätverk.

<!-- pagebreak -->

## 6. Konsolverktygen (PlayStation Classic)

Två verktyg följer med ett minne för PlayStation Classic och hjälper dig att få ut mer av konsolen än den klarar
från fabrik. Båda ser ut som resten av launchern, med dess tema och språk, och du styr dem med handkontrollen -
i guiden för handkontroller även med konsolens knappar på framsidan. **PSC-Bios** är ett tillägg som följer med
konsolpaketet: punkten *Nätverk och handkontroller* i snabbmenyn och i systemmenyn öppnar det, och du hittar det
också i listan Tillägg. **ABFlashKit** är en app, i samlingen Appar.

### 6.1 PSC-Bios

Med PSC-Bios kopplar du maskinen till omvärlden: ditt WiFi-nätverk, tidszonen, Bluetooth-handkontroller och
knapplayouten för en handkontroll som AutoBleem inte känner till. Det följer med konsolpaketet och finns även på
en Raspberry Pi och PC-minnet. Du öppnar det med *Nätverk och handkontroller* i systemmenyn (eller snabbmenyn),
eller från listan Tillägg. Är tillägget installerat men avstängt är punkten *Nätverk och handkontroller*
nedtonad, och det står att det *är avstängt - slå på det under Tillägg*; tryck på Cross på punkten, så öppnas
listan Tillägg vid PSC-Bios och du kan slå på det igen.

Den första skärmen ger dig en överblick: tiden och tidszonen, nätverkskorten (WiFi, Ethernet, Bluetooth) med
sina adresser, och alla anslutna handkontroller, med en notering om de har en knappmappning. På konsolen kräver
delarna för nätverk och Bluetooth AutoBleem-kerneln (avsnitt 6.2); på en Raspberry Pi eller PC-minnet används
systemets egna verktyg. Guiden för handkontroller fungerar överallt.

![PSC-Bios: startsidan för Nätverk och handkontroller](../images/en/pscbios-main.jpg)

Från den första skärmen tar en knapp dig till varje del:

| Knapp | Vad den öppnar |
|---|---|
| Select | **Wi-Fi Network** ansluter dig till ditt WiFi (via kerneln, eller NetworkManager på en Pi eller PC): skriv nätverkets namn eller välj det ur en sökning, ange lösenordet, välj drivrutinsläge och tryck på *Apply / Restart Network*. Här ställer du också in tidszonen, och när du är ansluten ser du konsolens IP-adress. |
| Square | **Bluetooth Controllers** söker efter Bluetooth-handkontroller som DualShock 4, så att du kan parkoppla en ny eller ta bort en som du inte använder längre. |
| L1 | **DualShock 3 Pairing** ansluter din första DualShock 3, som då måste sitta i via USB, med hjälp av kernelns sixaxis-plugin. |
| R1 | **Controller Mapping** öppnar guiden för handkontroller, som beskrivs nedan. |
| Triangle | **About** visar vad PSC-Bios är. |
| Circle | **Back** tar dig ut ur PSC-Bios, tillbaka till launchern. |

**Guiden för handkontroller.** Använd den när en handkontroll inte gör något i AutoBleem eller har knapparna på
fel ställen. Den visar den anslutna handkontrollen precis som den är - alla axlar, knappar och hattar som siffror
- och en bild av en DualShock som lyser upp när du trycker. Eftersom handkontrollen du testar inte går att lita
på än styr du guiden med konsolens **knappar på framsidan**: **RESET** byter till nästa handkontroll, **OPEN**
startar mappningen och **POWER** avbryter eller avslutar. Under mappningen ber guiden om en knapp i taget: tryck
på knappen som lyser på bilden, eller på OPEN om din handkontroll saknar den knappen. Ett kort tryck mappas som
vanligt.

Du kan också avsluta från handkontrollen: håll in Circle i 2 sekunder - en stapel fylls och längst ner står det
*Hold 2 s: Exit*. Så länge handkontrollen saknar mappning gör det samma sak att hålla in vilken knapp som helst i
2 sekunder (*Hold any button 2 s: Exit*). På ett tangentbord gör Esc, mellanslag och Enter jobbet för POWER,
RESET och OPEN.

När du är klar tas den nya mappningen i bruk så att du kan prova den, och OPEN sparar den under ett namn som du
väljer. Från och med då läser launchern in den varje gång.

![PSC-Bios: guiden för knappmappning](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - AutoBleem-kerneln

AutoBleem-kerneln ersätter konsolens egen Linux-kernel, och den är valfri. Du vill ha den om du vill få ut mer
av konsolen: den ger den en fungerande klocka, får WiFi- och Bluetooth-adaptrar med USB att fungera (för PSC-Bios
och Bluetooth-handkontroller) och lägger till stödet för knapparna på framsidan som emulatorn använder för
sparpunkter. ABFlashKit är verktyget som installerar den. Det säkerhetskopierar konsolen först, och det kan
också återställa konsolen till fabriksskick med Sonys egen återställning.

> **Det här verktyget skriver till konsolens flashminne.** Avbryts skrivningen - strömmen bryts, eller minnet
> dras ut - kan det hända att konsolen inte startar längre, och en egen kernel gör att garantin upphör. Låt
> konsolen ha ström och minnet sitta kvar tills konsolen startar om av sig själv. ABFlashKit öppnas med den här
> varningen: *I understand* går vidare, *Quit* avslutar.

![ABFlashKits meny](../images/en/abflashkit-menu.jpg)

ABFlashKit kan göra tre saker:

- **Flash Kernel** installerar kerneln. Finns det ingen återställningskopia på minnet än gör den först en av
  konsolens partitioner (`LBOOT.EPB`). Den kontrollerar säkerhetskopian och kernelavbilden, skriver kerneln och
  AutoBleems systemfiler och startar om konsolen. När det står *All done - when the screen goes black replace
  power cord* väntar du tills skärmen blir svart, drar sedan ur konsolens strömkabel och sätter i den igen.
- **Full backup** sparar alla fyra av konsolens partitioner i `LBOOT.EPB`, så att du kan återställa dem senare.
  Finns det redan en säkerhetskopia frågar den innan den skriver över den.
- **Restore Mode** är vägen tillbaka till originalfirmwaren. Den kontrollerar att säkerhetskopian på minnet
  kommer från en omodifierad konsol, sätter återställningsflaggan och startar om till Sonys återställning, som
  återställer konsolen från `LBOOT.EPB`.

En förloppsstapel under varje steg visar hur långt det har kommit. ABFlashKit flashar inte en konsol som kör en
annan egen firmware, som BleemSync eller Project Eris: återställ den konsolen till fabriksskick först.

**Logga in från en dator.** Kan du Linux och vill titta in i konsolen kan du logga in på den från en dator via
en USB-kabel. Det kräver AutoBleem-kerneln; på en omodifierad konsol fungerar det inte.

1. Koppla konsolens micro-USB-port till datorn med en USB-kabel. Datorn ser konsolen som ett nytt nätverkskort,
   och konsolens adress hittar du i det nätverkskortets inställningar på datorn.
2. Logga in med `ssh root@<konsolens adress>`. Standardlösenordet är `autobleem`.

I stället för lösenordet kan du använda en nyckel. Lägg din publika nyckel i filen `System/ssh/authorized_keys`
på minnet och starta om konsolen: vid nästa start läggs den till för root-kontot. Att uppdatera eller installera
om launchern tar inte bort den.

> **Standardlösenordet är detsamma på alla konsoler**, så vem som helst som kan sätta en kabel i din konsol kan
> logga in som root. Använd en nyckel där du kan, och lämna inte en konsol med standardlösenordet där andra kan
> komma åt den.

<!-- pagebreak -->

## 7. Om något går fel

De flesta problem har en enkel orsak. Varje problem nedan börjar med vad du ser, förklarar varför det händer och
säger sedan vad du ska göra. Behöver du be om hjälp är loggarna det första någon kommer att fråga efter, så de
kommer först.

**Hitta loggarna.** AutoBleem håller sina loggar i minnet medan det körs, så att minnet inte skrivs till hela
tiden. De hamnar i `System/Logs/` på minnet, kortet eller i datamappen bara när något har gått fel: när
launchern, ett PS1-spel eller RetroArch kraschar sparas loggarna i `System/Logs/crash-<n>/` (de tre senaste
krascherna sparas), och launchern säger till en gång när den är tillbaka. Jagar du ett problem som inte är en
krasch kan du behålla alla loggar: slå på Alternativ → *Diagnostik* → *Behåll loggar på USB-minnet* (det gäller
från nästa start), eller skapa en tom fil `System/Logs/keep` från en dator. *Hårdvaruinformation* (avsnitt 4.2)
visar också var loggarna ligger, och Square där sparar de aktuella i `System/Logs/saved-<n>/`.

Det här är filerna du hittar:

| Fil | Vad den berättar |
|---|---|
| `autobleem.log` | Vad launchern själv gjorde. |
| `launch.log`, `pcsx.log` | Hur ett PS1-spel startades och vad emulatorn sa medan den körde. |
| `retroarch.log` | Vad RetroArch sa medan det körde. |
| `update.log` | Hur en uppdatering online gick; den sparas alltid på minnet. |
| `updateroms.log` | Hur UpdateRoms gick på datorn (kapitel 5); den sparas alltid på minnet. |

**En bild ber dig sätta i minnet, eller konsolen har somnat.** AutoBleem hittar inte sitt minne: det satt inte i
när konsolen startade, eller så drogs det ut. Sätt i det i valfri USB-port (helst en på framsidan, avsnitt 2.1)
innan de 5 minuterna har gått, eller tryck på Power. Togs minnet inte bort korrekt kontrollerar AutoBleem det
först - vänta tills förloppsstapeln är klar.

**RetroArch säger *RetroArch kräver ett nyare systembibliotek än den här konsolen har - använd den RetroArch som
följer med AutoBleem*.** Det RetroArch-bygget gjordes för ett nyare system än konsolens, så det kan inte köras
där. Använd den RetroArch som följer med AutoBleem.

**Ett spel säger *Det här spelet skyddas av sin PSN-licens och kan inte startas*.** Spel som är köpta på
PlayStation Network är låsta till sin licens, och AutoBleem kan inte köra dem. Det finns inget att åtgärda.

**Ett spel syns inte på hyllan.** Oftast är mappen inte ordnad så som skanningen förväntar sig. Kontrollera att
varje spel har en egen mapp och är i något av formaten i avsnitt 3.10. *Spelbibliotek* (avsnitt 4.1) listar
mapparna som skanningen avvisade efter spelen, märkta *Inte tillagt*, och berättar varför var och en avvisades;
Square tar bort en sådan mapp. När du har rättat en mapp kör *Skanna om spel* i systemmenyn skanningen igen.

**Spelen har inga omslag.** Antingen installerades inte omslagsdatabaserna - kör installationsprogrammet igen
med dem ikryssade - eller så har UpdateRoms inte körts på datorn än, när det gäller RetroArch-spel på en konsol
(kapitel 5).

**En handkontroll gör ingenting, eller knapparna är omkastade.** AutoBleem känner inte till handkontrollens
layout. På en konsol mappar du den med guiden för handkontroller i PSC-Bios (avsnitt 6.1). På en Pi eller en PC
visar sidan Hårdvaruinformation (avsnitt 4.2) vad systemet ser av handkontrollen, så att du kan avgöra om den
alls upptäcks.

**Skärmen förblir svart efter ett spel på konsolen.** Launcherns bild kom inte tillbaka när spelet tog slut.
AutoBleem bygger upp sitt fönster igen av sig själv, upp till tre gånger. Är skärmen fortfarande svart håller du
in Power-knappen och slår på konsolen igen.

**På en Raspberry Pi** kan du ta dig bakom launchern när du behöver: `Alt+F2` ger dig en inloggning på den andra
konsolen, och SSH är påslaget från första starten. `sudo journalctl -u autobleem` visar vad launcherns tjänst
gjorde, och `sudo systemctl restart autobleem` startar om den. Kunde första starten inte slutföras för att det
inte fanns något nätverk försöker den igen vid nästa start.

**I Windows** lämnar du launchern med `Esc`. Din datamapp är den som du valde under installationen
(`Documents\AutoBleem` om du inte ändrade det), och loggarna ligger i dess mapp `System\Logs`.

**Konsolen startar om gång på gång efter en uppdatering online (minnet formaterat som ext4).** En del formaterar
minnet som ext4, Linux-filsystemet, i stället för FAT32 eller exFAT. Fram till nästa AutoBleem-release packar en
uppdatering online upp alla filer på ett sådant minne utan behörigheten som låter dem köras som program.
AutoBleem kan då inte starta, och konsolen startar om om och om igen. Minnen med FAT32 och exFAT påverkas inte.
Det finns två sätt att rätta till det.

**Lösning A** kräver en Linux-dator. Sätt i minnet och gör AutoBleems program körbara igen. Byt ut
`/media/USER/STICK` mot din egen monteringssökväg; den sista raden behöver du bara om RetroArch är installerat:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Lösning B**: installera den senaste AutoBleem-releasen på minnet igen, som i avsnitt 2.1.
Installationsprogrammet behöver en dator som kan läsa minnet. Kan den inte läsa ditt måste minnet formateras
först, vilket raderar allt på det - kopiera av dina spel innan du gör det.

> Undvik problemet genom att använda **FAT32** (en omodifierad konsol läser bara FAT32; exFAT kräver
> AutoBleem-kerneln, kapitel 6). Nästa release behåller behörigheterna, och AutoBleem reparerar dem vid varje
> start.

AutoBleem är fri programvara (GNU GPL v3 eller senare) och levereras utan garanti. För support och nyheter kan
du gå med i Discord-servern som det finns en länk till på skärmen *Om*, eller besöka
https://autobleem.retromenele.pl/.
