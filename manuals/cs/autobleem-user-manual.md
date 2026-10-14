# Uživatelská příručka AutoBleem 2

AutoBleem 2 je spouštěč her pro **PlayStation Classic** a od druhé verze také pro **Raspberry Pi**, **PC
spuštěné z USB flashky** a **Windows**. Vaše hry z PS1 vám ukáže jako polici s obaly, u každé hry s obrázkem
krabičky a podrobnostmi, spustí je v přibaleném emulátoru PCSX, a když vedle něj nainstalujete RetroArch,
zahrajete si i hry z jiných systémů. Příručka vás provede instalací na každé platformě, běžným používáním
a nástroji, které k AutoBleemu patří.

> Všechno ke stažení najdete na **https://autobleem.retromenele.pl/**. Stránka je rozdělená podle platforem:
> panel *Install* u každé z nich obsahuje to, co si stahujete vy; *Build inputs* pod ním jsou soubory, které si
> instalátory stáhnou samy.

## 1. Co dostanete

S AutoBleemem se z PlayStation Classic - nebo z Raspberry Pi, starého PC či vašeho počítače s Windows - stane
malá herní konzole s pořádnou nabídkou pro vaše vlastní hry. Tohle všechno v něm najdete:

- **Spouštěč.** To je obrazovka, kterou uvidíte hned po zapnutí: police s obaly her, po které listujete, a vedle
  vybrané hry její podrobnosti. Odtud hry spouštíte, třídíte je do sad (PlayStation, RetroArch, Aplikace),
  měníte nastavení, staráte se o paměťové karty a uložené pozice a stahujete aplikace a hry z Obchodu. Na všech
  platformách vypadá i funguje stejně.
- **Dva emulátory PS1.** `pcsx-abnxt` je ten současný a výchozí, `pcsx-ab` je klasický emulátor, se kterým
  AutoBleem přichází odjakživa. Vybíráte mezi nimi v Možnostech. Oba sdílejí stejná nastavení i paměťové karty,
  takže je můžete kdykoli vyměnit a o nic nepřijdete.
- **RetroArch**, pokud chcete hrát i hry z jiných systémů - NES, SNES, Mega Drive, Game Boy, arkádové automaty
  a spoustu dalších. Na žádné platformě není povinný. Nakopírujete své ROMy a AutoBleem je roztřídí do seznamů
  a každou hru spustí se správným jádrem. V RetroArch můžete hrát i hry z PlayStationu; jeho jádro *PlayStation 1*
  je v seznamu jader úplně nahoře (oddíl 3.9). Hry jako Doom běží z vašich vlastních herních souborů ve složce
  `Packages` (oddíl 3.10).
- **Nástroje pro konzoli.** *PSC-Bios* - v nabídkách se jmenuje *Síť a ovladače* - nastavuje WiFi, hodiny,
  ovladače přes Bluetooth a mapování tlačítek, a to na konzoli i na Raspberry Pi a flashce pro PC. *ABFlashKit*
  instaluje do PlayStation Classic jádro AutoBleem (kapitola 6).
- **UpdateRoms** pro Windows. PlayStation Classic nemá vlastní síť, a tak tenhle program pro PC obnoví seznamy
  RetroArch a stáhne obaly pro flashku konzole, zatímco je zapojená v počítači.

![Spouštěč: police s obaly, podrobnosti vybrané hry a nápověda tlačítek](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Instalace

### 2.1 PlayStation Classic

AutoBleem běží celý z USB flashky. Uvnitř konzole se nic nemění: vytáhnete flashku a konzole funguje přesně
jako předtím. Potřebujete jen PC s Windows, flashku (USB 2.0, aspoň 8 GB) a samotnou konzoli.

Flashka nemusí být prázdná a **formátovat se nebude**, dokud o to sami nepožádáte. AutoBleem se nainstaluje
vedle všeho, co na ní už je, a flashku, kterou už používáte s AutoBleemem 1.0, rovnou aktualizuje (viz níže).
Pro konzoli v továrním stavu musí být flashka naformátovaná jako **FAT32**, protože původní jádro konzole exFAT
nepřečte. Jakmile nainstalujete jádro AutoBleem (ABFlashKit, kapitola 6), konzole naběhne i z flashky s exFAT
a vy se zbavíte limitu FAT32, který nedovolí soubor větší než 4 GB.

1. Z panelu PlayStation Classic na webu si stáhněte **AutoBleemInstaller-<verze>.zip** a rozbalte ho kamkoli.
   Uvnitř je `AutoBleemInstaller.exe` a jeho README. Samotný AutoBleem se stahuje až během instalace, takže
   počítač potřebuje připojení k internetu.
2. Zapojte flashku a spusťte `AutoBleemInstaller.exe`. Vyberte **kanál** - *Release* je odzkoušená verze
   a pro většinu lidí ta správná volba, *Testing* je příští verze ve chvíli, kdy se testuje, a *Nightly* je
   nejčerstvější vývojové sestavení, které nemusí fungovat - a potom písmeno jednotky flashky. Řádek pod tím
   vám řekne, jakou verzi AutoBleemu se chystáte nainstalovat a co je na flashce teď: buď *a fresh install*
   (ostatních souborů na flashce se instalace nedotkne), nebo *AutoBleem <verze> is on this stick: it will be
   updated* (hry, uložené pozice, paměťové karty i nastavení zůstanou).
   **Formátovat nemusíte.** Tlačítko **Format** vedle jednotky je jen pro úplně novou flashku bez souborového
   systému, pro flashku, kterou konzole nepřečte (třeba s NTFS), nebo pro takovou, kterou chcete vymazat do
   čista. Nejdřív se zeptá a pak smaže z flashky úplně všechno. Pokud konzole ještě nemá jádro AutoBleem,
   zvolte tam FAT32.
   Pak zaškrtněte, co chcete nainstalovat:
   - **Cover databases** - obaly a popisy celé knihovny her pro PS1, aby si vaše hry našly obaly samy
     (standardně zaškrtnuto; zhruba 300 MB).
   - **RetroArch** - RetroArch s jádry, doplňkovými aplikacemi (Doom, Quake, Amiga, ...) a grafikou z libretro,
     pro hry z jiných systémů. Standardně vypnuto; doinstalovat ho můžete kdykoli později dalším spuštěním
     instalátoru.
   - **BIOS files** - soubory BIOS, bez kterých se některá jádra RetroArch nespustí (jen spolu s RetroArch).
   - **Sample games** - pár volně šiřitelných homebrew her, aby police při prvním spuštění nezela prázdnotou.
3. Stiskněte **Install** a počkejte. Ukazatele průběhu a záznam ukazují každý krok. Na konci se flashka
   přejmenuje na `SONY` a dostane kopii programu `UpdateRoms` (viz kapitola 5).
4. Flashku bezpečně odeberte, zapojte ji do **druhého předního USB portu** konzole (toho pravého, pro hráče 2)
   - první zůstane volný pro ovladač - a konzoli zapněte. Místo původní nabídky naběhne AutoBleem. Druhý
   ovladač připojíte přes USB hub v předním portu, nebo použijte ovladač přes Bluetooth.

**Zapínání a vypínání.** Se zapojenou flashkou konzole naběhne, pár sekund bliká kontrolkou, než AutoBleem
zaregistruje, a ještě než se na obrazovce cokoli objeví, přejde do pohotovostního režimu. To je v pořádku:
AutoBleem startuje přes vlastní aktualizační mechanismus konzole a ten prostě funguje takhle. Stiskněte jednou
**Power** a spouštěč se objeví.

Když v systémové nabídce zvolíte *Vypnout* nebo stisknete na konzoli tlačítko Power, konzole přejde do
**pohotovostního režimu AutoBleemu**: AutoBleem nejdřív bezpečně odpojí flashku a potom kontrolka zoranžoví -
to je znamení, že všechno proběhlo, jak má. Dalším stiskem Power se spouštěč za pár sekund vrátí. **Dokud svítí
oranžově, můžete flashku vytáhnout** a zapojit do počítače; Windows ji nebudou chtít kontrolovat, protože byla
odpojená správně. Než znovu stisknete Power, vraťte ji zpátky. Pokud konzoli odpojíte ze zásuvky, při dalším
zapnutí projde znovu startovním pohotovostním režimem. **Červená** kontrolka znamená, že je konzole opravdu
vypnutá.

**Port vzadu.** Port micro-USB vzadu je napájecí konektor konzole. S jádrem AutoBleem do něj jde zapojit i USB
zařízení, ale flashka patří do předního portu.

**Když flashka chybí.** Pokud konzole naběhne bez flashky, nebo flashku vytáhnete za běhu AutoBleemu, objeví se
obrázek, který vás požádá, ať ji zasunete - do kteréhokoli USB portu. AutoBleem čeká 5 minut a pak konzoli uspí;
chcete-li, aby usnula hned, stiskněte Power.

![Obrázek, který žádá o vložení flashky](../images/en/insert-stick.jpg)

**Kdy se flashka kontroluje.** Pokud flashka nebyla odpojená správně - vytáhli jste ji za běhu AutoBleemu nebo
vypadl proud - AutoBleem ji před dalším použitím zkontroluje, jestli na ní nejsou chyby: při startu, po
probuzení nebo když ji znovu zapojíte. Ukazatel průběhu ukazuje, jak daleko kontrola je. Na velké flashce může
chvíli trvat; nechte ji doběhnout a konzoli mezitím nevypínejte.

![Kontrola flashky](../images/en/stick-check.jpg)

**Aktualizace.** Flashku aktualizujete tak, že na ni znovu pustíte instalátor - tlačítko teď místo instalace
nabízí *Update*. Nainstaluje nejnovější verzi zvoleného kanálu; hry, uložené pozice, nastavení i obsah
RetroArch zůstanou a vymění se jen vlastní soubory AutoBleemu. Konzole s jádrem AutoBleem a s WiFi se umí
aktualizovat i sama (oddíl 3.12).

**Přechod z AutoBleemu 1.0 (nebo AutoBleem-NG).** Použijete stejný instalátor na stejné flashce, bez
formátování:

1. Nejdřív si celou flashku pro jistotu zkopírujte do počítače jako zálohu.
2. Zapojte ji, spusťte `AutoBleemInstaller.exe` a vyberte kanál a jednotku. Tlačítko Format **nemačkejte**.
3. Stiskněte **Install**. Instalátor převede staré uspořádání na nové: RetroArch, ROMy a motivy přestěhuje tam,
   kde je AutoBleem 2 čeká, a staré složky s ROMy (`nes`, `snes`, ...) dostanou názvy systémů podle RetroArch.
   Hry, uložené pozice, paměťové karty, ROMy i uložené hry z RetroArch zůstanou, stejně jako `config.ini` - jen
   emulátor PS1 se v něm přepne na pcsx-abnxt.
4. Vraťte flashku do konzole. První skenování znovu sestaví seznam her i playlisty. Obaly pro hry z RetroArch
   získáte, když na PC spustíte UpdateRoms (kapitola 5).

> Konzole v továrním stavu nemá hodiny ani síť. Data se začnou zobrazovat až po instalaci jádra AutoBleem
> (kapitola 6) a obaly her pro RetroArch obstará UpdateRoms na PC (kapitola 5).

Hry z PS1 patří na flashce do složky `Games`, každá do vlastní složky - jak přesně, vysvětluje oddíl 3.10.

### 2.2 Raspberry Pi

S AutoBleemem se z Raspberry Pi stane malá konzole: naběhne rovnou do spouštěče, žádná plocha mezi tím. Na webu
jsou dva hotové obrazy karty, 32bitový a 64bitový, a k tomu balíček pro Raspberry Pi OS Lite, který už máte
nainstalovaný.

| Model | 32bitový obraz | 64bitový obraz | Poznámka |
|---|---|---|---|
| Raspberry Pi 5 | ano | ano | |
| Raspberry Pi 4 Model B, Pi 400 | ano | ano | |
| Raspberry Pi 3 Model B / B+ / A+ | ano | ano | na spouštěč a PS1 stačí |
| Raspberry Pi Zero 2 W | ano | ano | 512 MB RAM: PS1 běží, náročnější jádra RetroArch ne |
| Raspberry Pi 2 Model B | ano | jen v1.2 | na cokoli ve 3D je pomalé |
| Raspberry Pi 1, Zero, Zero W | ne | ne | ARMv6 - žádný z obrazů na nich neběží |

**Kvůli hrám z PS1 si vezměte 32bitový obraz.** Rychlý rekompilátor pro ARM má klasický `pcsx-ab` jen ve
32bitové verzi, takže na 64bitovém sestavení běží hry z PS1 pomaleji. 64bitový obraz zase nabízí víc jader
RetroArch - zvolte ho, pokud vám jde víc o ostatní systémy než o PS1.

**Pomocí Raspberry Pi Imager:**

1. Nainstalujte si Raspberry Pi Imager (raspberrypi.com/software). V *Choose OS* zvolte *Use custom* a stažený
   soubor `autobleem-<verze>-rpi-armhf.img.xz` (32 bitů) nebo `-arm64.img.xz` (64 bitů). Druhá možnost je
   přidat v nastavení aplikace adresu repozitáře a AutoBleem pak vybrat ze seznamu. Pro každý kanál je jedna:
   `https://autobleem.retromenele.pl/rpi-imager/os_list.json` pro poslední vydání,
   `.../os_list-testing.json` pro sestavení ve fázi testování a `.../os_list-nightly.json` pro nejnovější
   vývojové sestavení. Na stránce ke stažení je na kartě Raspberry Pi najdete všechny, které existují, každou
   s tlačítkem *Copy*.
2. Na obrazovce úprav v Imageru (ozubené kolečko, nebo dotaz po kliknutí na *Next*) nastavte **uživatelské jméno
   a heslo, síť WiFi a zemi a zapněte SSH**. AutoBleem potřebuje při prvním spuštění síť.
3. Zapište kartu, vložte ji do Pi s připojenou obrazovkou a klávesnicí nebo ovladačem a zapněte ho.

**První spuštění** trvá 5 až 25 minut a na obrazovce průběžně vidíte, co se děje. Pokud Pi není připojené
k síti, zeptá se na ni: ze seznamu vyberete svou WiFi a napíšete heslo. Potom se zeptá, jestli nainstalovat
RetroArch - když do minuty neodpovíte, nainstaluje ho. Pak zvětší systémový oddíl, ze zbytku karty udělá oddíl
`AUTOBLEEM` pro vaše hry, nainstaluje RetroArch s jádry, balíčky BIOS a ukázkové hry a restartuje se rovnou do
spouštěče.

Pokud nechcete při prvním spuštění na nic odpovídat, zapište odpovědi předem do souboru **`autobleem.txt`** na
zaváděcím oddílu karty - otevřete a upravíte ho na jakémkoli PC:

| Klíč | Výchozí hodnota | Význam |
|---|---|---|
| `root_gib` | 8 | Velikost systémového oddílu v GiB; ze zbytku se stane oddíl pro hry. |
| `hdmi_mode` | 1920x1080@60 | Režim obrazovky pro celý start (pro starší televizi `1280x720@60`). |
| `retroarch` | (asked) | `yes` / `no` - RetroArch a další systémy, nebo jen PS1. |
| `thumbnails` | none | `boxarts` stáhne celou sadu obalů, aby byly k dispozici i bez sítě (asi 9000 souborů). |
| `bios`, `downloads`, `samples` | yes | Hodnota `no` vynechá balíčky BIOS, veškeré stahování, nebo ukázkové hry. |

**Na Raspberry Pi OS Lite, který už máte** (Bookworm nebo Trixie): zkopírujte do Pi `autobleem-rpi.tar.gz`
(nebo verzi arm64), rozbalte ho a spusťte `sudo bash install.sh`. Položí vám stejné otázky, při dalším startu
zmenší systémový oddíl, aby uvolnil místo pro datový oddíl (`--shrink-root <GiB>`), a spouštěč umístí na první
konzoli.

Po instalaci naplníte **oddíl `AUTOBLEEM`** na kartě (exFAT) svými hrami: buď kartu vyndáte a otevřete na
jakémkoli PC, nebo kopírujete po síti (SSH je zapnuté). Hry z PS1 patří do `Games/`, ROMy ostatních systémů do
`RetroArch/roms/<systém>/`, BIOS pro PS1 do `System/Bios/` (oddíl 3.11) a motivy do `Themes/`.

### 2.3 Flashka pro PC

Totéž funguje na každém PC, které umí startovat z USB: flashka nastartuje počítač rovnou do AutoBleemu a jeho
vlastní disk nechá na pokoji. Jde o 32bitový systém, takže poslouží i starší stroje.

1. Zapište obraz na flashku s kapacitou aspoň 8 GB. **Ve Windows** na to použijte **AutoBleemFlasher** (panel
   PC na webu - rozbalte ho a spusťte `AutoBleemFlasher.exe`; vyžádá si práva správce, protože zapisuje celý
   disk): vyberte kanál a flashku, stiskněte *Write* a dvakrát potvrďte. Program obraz stáhne, ověří, zapíše
   a znovu přečte. Nabídne vám jen USB flashky a SD karty, nikdy disk, ze kterého běží Windows, a **všechno na
   vybrané flashce se smaže**. V Linuxu nebo macOS si z panelu PC stáhněte
   `autobleem-<verze>-pcusb-i386.img.xz` a zapište ho příkazem
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (nebo programem balenaEtcher).
2. Spusťte PC z flashky (klávesou pro výběr zaváděcího zařízení - podle počítače F12, F8, Esc...). Funguje
   start z BIOSu i z UEFI; **Secure Boot musí být vypnutý**.
3. První spuštění proběhne stejně jako na Pi: když není zapojený kabel, zeptá se na síť, zeptá se na RetroArch,
   všechno nainstaluje - s kabelovou sítí to trvá asi osm minut - a restartuje se do spouštěče.

Potom má flashka oddíl `AUTOBLEEM` pro vaše hry. Když ji zapojíte do běžícího PC s Windows 10 (verze 1903 nebo
novější), objeví se jako druhá jednotka a hry na ni můžete kopírovat. `autobleem.txt` je na prvním oddílu a má
stejné klíče jako na Pi (kromě `hdmi_mode` - PC vždy používá vlastní režim obrazovky).

### 2.4 Windows

Pokud chcete AutoBleem na svém počítači s Windows, běží i jako obyčejný program: na celé obrazovce, přičemž
emulátory a RetroArch se spouštějí jako samostatné programy.

1. Stáhněte **AutoBleemSetup-<verze>.exe** a spusťte ho. Instaluje se pro aktuálního uživatele, bez práv
   správce: program do `%LOCALAPPDATA%\Programs\AutoBleem`, data (hry, nastavení, motivy, RetroArch) do složky,
   kterou si zvolíte - výchozí je `Documents\AutoBleem`.
2. Zaškrtněte součásti - databáze obalů, RetroArch (oficiální sestavení pro Windows s jádry), soubory BIOS
   a ukázkové hry - a nechte pomocníka instalace, ať je stáhne.
3. AutoBleem spustíte z nabídky Start nebo z plochy. Na PC zastoupí ovladač klávesnice (oddíl 3.2).

Aktualizace je jednoduchá: přes starou verzi spusťte novější instalaci. Program se vymění a složka s daty
zůstane, jak je. Spouštěč navíc jednou denně zkontroluje web, a pokud je k dispozici nová verze, nabídne vám ji
(oddíl 3.12).

<!-- pagebreak -->

## 3. Používání AutoBleemu

### 3.1 Spouštěč

Ve spouštěči si vybíráte, co budete hrát. Hry v něm stojí jako obaly na polici, podobně jako krabičky na
skutečné poličce, a vy po ní posouváte, dokud nenarazíte na tu pravou. Všechno ostatní v AutoBleemu - nastavení,
paměťové karty, Obchod - se otevírá odsud, a když hru ukončíte, vrátíte se sem.

Vybraná hra stojí uprostřed police a pod ní je jemný odraz. Vedle ní je v malé mřížce vidět, kdo ji vydal, rok,
sériové číslo, oblast, pro kolik hráčů je a kdy jste ji naposledy hráli. Když AutoBleem některý údaj nezná,
řádek raději vynechá, než aby ukazoval prázdné místo. Vedle podrobností je tlačítko pro spuštění. Hra bez
obrázku obalu se ukáže jako disk ležící v černém lůžku prázdné krabičky, takže i ona má na polici své místo.

Vzhled spouštěče určuje téma. Výchozí je **ab2.0.0**: přepne se na něj čerstvá instalace a také aktualizace,
která ho přináší, ovšem jen jednou - když si pak vyberete jiné téma (oddíl 3.6), zůstane vám.

**Lišta nápovědy** dole na obrazovce vám říká, co tlačítka zrovna dělají. Má dva řádky po čtyřech polích. První
řádek se týká vybrané hry: spustit ji, spustit ji v RetroArch, otevřít řadu ikon pod ní, nebo otevřít Rychlou
nabídku. Druhý řádek se nemění: Select vybírá sadu, Start vybere náhodnou hru, Triangle ukáže průvodce tlačítky
a L2 + R2 otevře systémovou nabídku. Když tlačítko zrovna nemá co dělat, jeho nápověda je ztlumená.

**Nové hry si najde sám.** Při každém startu spouštěč na pozadí projde složku s hrami, takže hra, kterou jste
nakopírovali, zatímco byl stroj vypnutý, se objeví, aniž byste cokoli dělali. Během skenování ukazuje bublina
vpravo nahoře, jak daleko je, a nové hry přibývají na polici, jak je najde - můžete si mezitím v klidu listovat.

**Čerstvá instalace** ještě žádné hry nemá. Místo prázdné police uvidíte uvítací kartu *Ahoj a vítej
v AutoBleem!*, která vám poradí nahrát hry do složky `Games` a zvolit *Znovu skenovat hry*. Zmíní i místo
podle vaší platformy: na flashce (PlayStation Classic, flashka pro PC), na SD kartě (Raspberry Pi) nebo ve
složce AutoBleem (Windows). Jakmile skenování najde první hru, karta zmizí.

**Oznámení** jsou bubliny vpravo nahoře. Informují vás, aniž by překážely: o průběhu skenování, o názvu sady,
na kterou jste právě přepnuli (*Zobrazeno: ...*), o ovladači, kterému dochází baterie, o pádu programu,
o procesoru skenování, který právě pracuje, a o stahování z Obchodu. Bublina stahování ukazuje rychlost
a zbývající čas, například `1.4 MB/s · 0:42`. Jak dlouho informační bubliny zůstanou na obrazovce, si určíte
sami: Možnosti → *Doba zobrazení oznámení:*.

**Baterie ovladačů.** Na konzoli, Raspberry Pi a flashce pro PC (ve Windows ne) se každý bezdrátový ovladač,
který hlásí stav baterie, zobrazí jako malá ikona s procenty na vlastní destičce; destičky se řadí pod sebe od
levého horního rohu. Ovladač, kterým hraje hráč 1 nebo hráč 2, nese štítek P1 nebo P2 podle nastavení
*Prohodit hráče 1 / hráče 2 (emulátory PS1):* (oddíl 3.6); ovladač, který žádnému hráči nepatří, nebo třetí
ovladač štítek nemá. Když ovladači dochází baterie, oznámení vás na to jednou upozorní, s názvem ovladače
a procenty.

**Štítek kanálu.** Pokud používáte sestavení, které není finálním vydáním, připomene vám to malý štítek pod
destičkou s baterií ovladače v levém horním rohu. Je to čip s názvem kanálu a vedle něj krátké číslo verze:
`ALPHA`, `BETA` nebo `RC` u předběžného vydání, `TESTING` u jakéhokoli jiného předběžného vydání, `NIGHTLY`
u nočního sestavení a `DEV` u sestavení vytvořeného ručně (u `DEV` je místo verze commit, ze kterého vzniklo).
Finální vydání žádný štítek nemá.

![Výběr sady: tři karty a skupiny té aktuální s počty her](../images/en/set-picker.jpg)

### 3.2 Ovládání

AutoBleem se dá celý ovládat jen ovladačem a tlačítka znamenají na každé obrazovce totéž: Cross potvrzuje,
Circle vrací zpět, Triangle radí. Když zapomenete, co které tlačítko dělá, napoví vám lišta dole na obrazovce
a Triangle na polici otevře průvodce tlačítky se všemi tlačítky všech obrazovek (oddíl 4.3). Na polici fungují
takhle:

| Tlačítko | Na polici |
|---|---|
| Vlevo / Vpravo | Přesune vás na předchozí nebo další hru; když tlačítko podržíte, posouvá se dál. |
| L1 / R1 | Skočí na předchozí nebo další počáteční písmeno názvů, takže dlouhou polici rychle projdete. Na prázdné polici se zapojenou USB mechanikou otevře R1 *Disk* (oddíl 3.9a). |
| Cross | Spustí vybranou hru: hru z PS1 v emulátoru PS1, hru pro RetroArch v jejím jádře a aplikaci po přečtení jejího popisu. |
| Square | Spustí vybranou hru z PS1 místo toho v RetroArch. Když je vybraný disk v USB mechanice, disk zkopíruje (*Kopírovat disk*, oddíl 3.9a). |
| Circle | Vrátí vás do zobrazení disku, když je v mechanice disk (oddíl 3.9a). |
| Triangle | Otevře průvodce tlačítky. |
| Start | Vybere náhodnou hru z aktuální sady - pro chvíle, kdy se nemůžete rozhodnout. |
| Select | Otevře výběr sady, kde zvolíte, které hry police ukazuje (oddíl 3.3). |
| Nahoru | Otevře Rychlou nabídku (oddíl 3.4). |
| Dolů | Otevře řadu ikon pod hrou (*NASTAVENÍ*, *Hra*, *PAMĚŤOVÁ KARTA*, *OBNOVIT*); Nahoru ji zase zavře. |
| L2 + R2 | Otevře systémovou nabídku (oddíl 3.5). |

**Na klávesnici.** Na PC bez ovladače, nebo s USB klávesnicí na konzoli, Pi či flashce pro PC zastoupí tlačítka
klávesy. Šipky jsou směrový kříž, Enter je Cross, Esc nebo Backspace je Circle, Tab je Triangle a mezerník je
Square. F1 a F2 jsou Select a Start, Page Up a Page Down jsou L1 a R1, Home a End jsou L2 a R2 a F10 otevře
systémovou nabídku. Na vývojářském počítači Esc zavře program a mezerník je Start.

**Ve všech seznamech a nabídkách** platí stejné pohyby: Nahoru a Dolů posouvají kurzor, L2 a R2 listují po
stránkách, L1 a R1 skočí na první nebo poslední řádek, Cross vybírá a Circle vrací zpět. Tlačítko Uložit nikde
hledat nemusíte: obrazovka s nastavením se uloží sama, když ji opustíte tlačítkem Circle.

**Jak ze hry nebo aplikace odejít.** Podržte na 2 sekundy Start + Select, nebo Home, a jste zpátky
v AutoBleemu. Funguje to na každém ovladači - původním z konzole, na USB i přes Bluetooth. Krátký stisk stejných
tlačítek místo toho otevře nabídku emulátoru. Aplikace žádnou takovou nabídku nemá, takže u ní funguje jen dlouhé
podržení.

![Řada ikon pod vybranou hrou](../images/en/launcher-icons.jpg)

### 3.3 Sady

Velkou knihovnu se lépe prochází po částech. Sady vám dovolí zúžit polici na jeden druh her - jen oblíbené,
jen hry pro Super Nintendo, jen hry z jedné složky - abyste nemuseli kvůli jediné hře listovat stovkami obalů.

Stiskněte **Select** a otevře se výběr sady. Má tři karty, PlayStation, RetroArch a Aplikace: L1 a R1 mezi
nimi přepínají, Nahoru a Dolů procházejí skupinami na kartě (L2 a R2 po stránkách) a Cross zobrazí zvolenou
skupinu na polici. Circle (*Zpět*) výběr zavře a nic nezmění. Tyhle klávesy připomíná i zápatí. U každého
řádku vidíte, kolik položek obsahuje. Prázdná skupina se otevře na prázdné polici, kde řada ikon nabízí jen
*NASTAVENÍ*.

**Karta PlayStation.** Na PlayStation Classic začíná položkami *Všechny hry* a *Interní hry* (dvacet her
zabudovaných v konzoli), za nimi jsou *Hry na USB* - všechno ve složce `Games/` - a jedna skupina pro každou
složku, kterou jste v ní vytvořili, takže hra v podsložce patří do skupiny té složky. Pak následují *Oblíbené
hry*, *Historie her* a - jakmile alespoň jednu hru označíte jako hru pro světelnou pistoli - *Hry se světelnou
pistolí*. Raspberry Pi, flashka pro PC ani Windows žádné interní hry nemají, takže tam seznam začíná položkou
*Hry na USB*, což je celá vaše knihovna.

**Karta RetroArch** je jen tam, kde je RetroArch nainstalovaný. Má jednu skupinu pro každý systém, pro který
máte hry, a k tomu vlastní Oblíbené a Historii z RetroArch.

**Karta Aplikace** třídí aplikace podle druhu: *Všechny aplikace*, potom *Hry*, *Emulátory*, *Nástroje*,
*Média* a *Ostatní*. Do které skupiny aplikace patří, určuje její soubor `app.ini`. Na této kartě jsou i **PE
aplikace**, tedy programy pro Windows spouštěné přes PE runner; ta, kterou konzole spustit nedokáže, je označená
*nelze spustit na této konzoli*. Tam, kde ho spouštěč ukazuje, je v seznamu i řádek *Balíčky* (oddíl 3.10).

### 3.4 Rychlá nabídka

Rychlá nabídka je krátký seznam věcí, po kterých při procházení her saháte nejčastěji, abyste je nemuseli
hledat v celé systémové nabídce. Otevřete ji tlačítkem **Nahoru** na polici, nebo **ikonou ozubeného kolečka**
v řadě ikon (v té, kde jsou *NASTAVENÍ*, *Hra*, *PAMĚŤOVÁ KARTA* a *OBNOVIT*).

Nahoru a Dolů procházejí položky (z poslední skočí kurzor zase na první), Cross položku vybere a Circle nabídku
zavře. Řádek pod nabídkou popisuje vybranou položku. Najdete v ní:

- *Znovu skenovat hry* hned vyhledá nové, změněné nebo odebrané hry - hodí se, když jste zrovna nakopírovali
  hry a nechce se vám čekat.
- *Obchod* otevře Obchod AutoBleem, kde procházíte a instalujete hry, aplikace a rozšíření (oddíl 3.13).
- *Jádra RetroArch* (tam, kde je RetroArch nainstalovaný) vám dovolí vybrat, které jádro bude hrát který systém.
- *Síť a ovladače* otevře obrazovky pro WiFi, párování přes Bluetooth a mapování ovladačů (kapitola 6). Je tu
  jen tehdy, když je poskytuje některé nainstalované rozšíření - to dělá PSC-Bios na konzoli, Raspberry Pi
  a flashce pro PC. Pokud je takové rozšíření nainstalované, ale vypnuté, položka je zašedlá a její popis vám
  poradí zapnout ho v Rozšířeních; Cross pak otevře seznam Rozšíření přímo na něm.
- *Restartovat launcher* zavře AutoBleem a spustí ho znovu (jen na konzoli, Raspberry Pi a flashce pro PC).
- *Systémová nabídka...* otevře celou systémovou nabídku se vším ostatním - Možnostmi, Správcem her, vypnutím
  a dalším (oddíl 3.5).

Všechno kromě Obchodu, jader RetroArch a restartu spouštěče najdete i v systémové nabídce.

![Rychlá nabídka](../images/en/quick-menu.jpg)

### 3.5 Systémová nabídka

V systémové nabídce je všechno, co AutoBleem umí kromě samotného hraní: nastavení, nástroje pro knihovnu
a paměťové karty, informace o stroji a cesta k vypnutí. Stiskněte současně **L2 + R2** (v libovolném pořadí)
a nabídka se otevře přes polici. Položky jsou rozdělené pod nadpisy *Knihovna*, *Systém* a *Odchod* a ty dvě,
které budete používat nejčastěji, jsou úplně nahoře. Řádek dole popisuje vybranou položku, takže se můžete
v klidu rozhlédnout, než něco zvolíte.

| Oddíl | Položka | K čemu je |
|---|---|---|
| (nahoře) | *Znovu skenovat hry* | Hned vyhledá nové, změněné nebo odebrané hry. Skenování sleduje složku i samo, takže tohle potřebujete, jen když nechcete čekat. |
| | *Rozšíření* | Ukáže rozšíření na flashce, například Obchod AutoBleem, abyste je mohli spustit nebo vypnout (oddíl 3.13). |
| *Knihovna* | *Správce her* | Ukáže hry z PS1 jako seznam i se složkami; tady můžete hru smazat nebo vymazat obaly (oddíl 4.1). Během skenování ho otevřít nejde. |
| | *Paměťové karty* | Správa sdílených sad paměťových karet (oddíl 3.8). |
| | *Procesory skenování* | Určuje pořadí programů, které každé skenování spustí jako první, a zapíná nebo vypíná je (oddíl 3.14). Během skenování ho otevřít nejde. |
| *Systém* | *Možnosti* | Otevře nastavení AutoBleemu (oddíl 3.6). |
| | *Síť a ovladače* | Otevře obrazovky pro WiFi, párování ovladačů přes Bluetooth, nastavení DualShocku 3 a mapování ovladačů (kapitola 6). Je tu jen tehdy, když je poskytuje některé rozšíření - viz níže. |
| | *Informace o hardwaru* | Ukáže údaje o stroji - systém, procesor, úložiště, síťová rozhraní, časové pásmo, displej a ovladače s jejich mapováním - na všech platformách na stejné stránce (oddíl 4.2). Circle vás vrátí do systémové nabídky. |
| | *Virtuální gamepad* | Ukáže ovladače, které dostávají aplikace, a ovladače, které vidí démon; pomůže, když ovladač v aplikaci nefunguje (oddíl 4.5). Circle vás vrátí do systémové nabídky. |
| | *Aktualizace softwaru* | Hned zkontroluje na webu, jestli není novější AutoBleem nebo RetroArch, místo abyste čekali na denní kontrolu (oddíl 3.12). Když už spouštěč o nějaké ví, řádek hlásí *Aktualizace k dispozici*. Na PlayStation Classic to vyžaduje jádro AutoBleem a síť WiFi. |
| | *O programu* | Ukáže autory a licenci. |
| *Odchod* | *RetroArch* | Opustí spouštěč a otevře vlastní nabídku RetroArch s jeho nastavením a seznamy obsahu; když RetroArch zavřete, jste zpět ve spouštěči. Je tu jen tam, kde je RetroArch nainstalovaný. |
| | *Vypnout* | Vypne stroj, ale nejdřív se vás zeptá (viz níže). |

**Síť a ovladače** se objeví jen tam, kde nainstalované rozšíření poskytuje položku `network`; rozšíření to
oznamuje řádkem `Provides=network` ve svém souboru `extension.ini`. PSC-Bios to dělá na konzoli, Raspberry Pi
a flashce pro PC. Když je takové rozšíření nainstalované, ale vypnuté, položka v nabídce zůstane, jen zašedlá,
a její popis vám poradí zapnout ho v Rozšířeních; Cross na ní otevře seznam Rozšíření přímo na něm.

**Vypnout** udělá to, co se pro daný stroj hodí. Konzoli uvede do pohotovostního režimu AutoBleemu: flashka se
odpojí, kontrolka zoranžoví a Power vrátí spouštěč za pár sekund (oddíl 2.1). Raspberry Pi nebo PC se vypne.

![Systémová nabídka](../images/en/system-menu.jpg)

### 3.6 Možnosti

V Možnostech si AutoBleem přizpůsobíte: obraz na obrazovce, vzhled spouštěče, jazyk, zvuk, emulátor, ve kterém
poběží hry z PS1. Otevřete je ze systémové nabídky (*Možnosti*) nebo ikonou *NASTAVENÍ* pod hrou. Obrazovku
a jazyk obvykle nastavíte jednou a vrátíte se sem, až vám bude na nějaké televizi něco vadit nebo budete chtít
změnu.

Nastavení jsou rozdělená do skupin, každá pod svým nadpisem. Nahoru a Dolů přecházíte mezi řádky, Vlevo a Vpravo
měníte hodnotu řádku, na kterém stojíte: krátký stisk posune o jeden krok, podržení posouvá dál. L1 a R1 skočí
na první nebo poslední řádek, L2 a R2 listují po stránkách. Na řádku s výběrem témat, hudby nebo písem vybere
Start něco náhodně. Nastavení, které se dá jen zapnout nebo vypnout, ukazuje **ON** nebo **OFF**. Každou změnu
vidíte hned a Circle obrazovku opustí a všechno uloží - nic dalšího potvrzovat nemusíte. Jedinou výjimkou je
režim obrazovky, který se vyzkouší až ve chvíli, kdy Možnosti opouštíte (viz *Obraz:* níže).

Některé řádky se ukazují jen tam, kde dávají smysl: řádky pro CRT jen při obrazu 4:3, řádky pro RetroArch jen
tam, kde je RetroArch nainstalovaný, interní hry jen na PlayStation Classic.

| Skupina / nastavení | K čemu slouží |
|---|---|
| *Rozhraní*: *Obraz:* | Nastaví rozlišení obrazovky pro spouštěč i emulátor PS1. *Auto* použije vlastní režim obrazovky a ukáže, který to je, například *Auto (1920x1080)*; vybrat můžete i kterýkoli jiný režim, který obrazovka nabízí. Konzole nabízí 720p, 1080p a *CRT 4:3* (720x480), což je režim pro starou CRT televizi nebo pro zařízení na záznam obrazu ve 4:3. Změňte ho, když se obraz na televizi nevejde nebo je rozmazaný. Pokud AutoBleem běží v okně na vývojářském počítači, tenhle řádek tu není. |
| *Okraj CRT:* | Trochu všechno zmenší, od 0 do 10 % po 1 %, protože staré televize okraje obrazu oříznou. Zvyšujte ho, dokud není celá lišta nápovědy i rohy vidět. Ukazuje se jen při výstupu 4:3, projeví se okamžitě a platí dokonce už pro úvodní obrazovku při startu. |
| *Výška obrazu:* | Udělá obraz vyšší nebo nižší, od -40 do +40 po 2, na jakémkoli výstupu 4:3 - *CRT 4:3*, nebo režim 4:3 na výstupu VGA či PC. Použijte ho, když je obraz na staré televizi zmáčknutý nebo přetéká nahoře a dole. Projeví se okamžitě a obraz her v RetroArch se mu přizpůsobí. |
| *Škálování obrazu emulátoru:* | Rozhoduje, jak emulátor PS1 přizpůsobí obraz hry obrazovce. *1x1* ukáže původní pixely PlayStationu, malé a přesné; *2x (celočíselně)* a *4:3 (celočíselně)* zvětšují jen celými násobky, což dává nejostřejší obraz; *4:3* zachová původní tvar obrazu; *Celá obrazovka* obraz roztáhne přes celou obrazovku. Nahrazuje dřívější přepínač širokoúhlého obrazu. Klasický `pcsx-ab` a RetroArch umí jen celou obrazovku a 4:3. |
| *Halo obrazovky:* | Když je ON, prázdné pruhy vedle obrazu hry (tam, kde obraz obrazovku nevyplní) se místo černé vyplní jemnou září samotného obrazu. Funguje s `pcsx-abnxt`. |
| *AutoBleem téma:* | Změní vzhled spouštěče. Témata jsou ve složce `Themes/` a v seznamu se objeví i zip s tématem, který tam vložíte, pod svým názvem. Témata dodávaná s AutoBleemem se při každé aktualizaci obnoví, takže pokud si některé chcete upravit, nejdřív si ho zkopírujte pod novým názvem. Výchozí je **ab2.0.0**. |
| *Styl obalu:* | Vybere rámeček krabičky, který se kreslí kolem obalů her z PS1. |
| *Záblesk obalu:* | Nechá přes vybraný obal přeběhnout odlesk pokaždé, když se police zastaví. |
| *Jazyk:* | Nastaví jazyk spouštěče; jazyků je 17 a změna se projeví okamžitě. |
| *Doba zobrazení oznámení:* | Určuje, jak dlouho zůstanou informační bubliny (*Zobrazeno: ...*, shrnutí skenování), od 0 do 20 sekund; 0 se zobrazí jako *Vypnuto* a bubliny vypne. Chybová hlášení mají vlastní pevnou dobu, takže vám žádné neuteče. |
| *Úvodní obrazovka:* | Při startu spouštěče ukáže obrázek AutoBleem; když ji vypnete, půjdete rovnou na polici. |
| *Animace:* | Animuje přechod z jedné obrazovky na druhou; vypněte ji, pokud chcete, aby se každá obrazovka objevila okamžitě. |
| *Písma*: *Použít výchozí písmo:* | Když je ON, spouštěč používá vlastní písmo (Red Hat Text); vypnutím použijete písmo zvolené na dalším řádku. |
| *Písmo:* | Vybere vlastní písmo: jakýkoli soubor `.ttf` nebo `.otf` ve složce `resources/fonts`, `RetroArch/fonts` nebo ve složce tématu. Řádek ukazuje název písma, které se opravdu používá. |
| *Zvuk*: *Hudba:*, *Hudba na pozadí:* | *Hudba:* vybere skladbu, která hraje ve spouštěči - vlastní hudbu tématu, nebo soubor z `resources/music`. *Hudba na pozadí:* rozhoduje, jestli bude vůbec nějaká hudba hrát. |
| *Emulace*: *Emulátor PS1:* | Vybere emulátor, ve kterém se hry z PS1 spouštějí: výchozí `pcsx-abnxt` (současný PCSX-ReARMed s doplňky AutoBleemu), nebo klasický `pcsx-ab`. Když nějaká hra neběží dobře, zkuste ten druhý. Bod obnovení uložený jedním emulátorem můžete dohrát ve druhém, pokud hra neběžela bez souboru BIOS. |
| *Prohodit hráče 1 / hráče 2 (emulátory PS1):* | Prohodí, který z prvních dvou ovladačů je hráč 1 a který hráč 2, v obou emulátorech PS1 - praktické, když máte ovladače zapojené „obráceně“. Má smysl jen se dvěma a více ovladači; s jedním hrajete vždy jako hráč 1. RetroArch se to netýká. Pokud právě používaný emulátor PS1 prohození ještě neumí, AutoBleem vám to řekne. |
| *Hrát všechny PSX hry přes RA:*, *Aktualizovat konfiguraci RA:*, *Uchovat nastavení RetroArch:* | Tyhle tři jsou jen tam, kde je RetroArch nainstalovaný. První spouští všechny hry z PS1 v jádře RetroArch pro PS1 (*PlayStation 1*; na PC je to SwanStation). Druhé dovolí AutoBleemu zapsat svá nastavení do konfigurace RetroArch, když v něm spouští hru. Třetí zachová změny, které uděláte ve vlastní nabídce RetroArch, i po jeho ukončení. |
| *Knihovna*: *Zobrazit interní hry:* | Ukáže hry zabudované v konzoli v seznamech PlayStation (jen PlayStation Classic). |
| *Čisté názvy her:* | Když je ON (výchozí), seznamy her RetroArch ukazují úhledné názvy bez značek v závorkách, jako (USA), (Rev 1) nebo [!]; OFF ukazuje názvy souborů. Název souboru zůstane vidět v podrobnostech hry. Hry z PS1 se to netýká, jejich názvy pocházejí z databáze. |
| *Stahovat obaly online:* | Dovolí skenování stáhnout chybějící obaly ze serverů libretro (Raspberry Pi, PC, Windows). |
| *Aktualizace*: *Aktualizace:* | Vybere, jaké aktualizace bude spouštěč hledat (oddíl 3.12): `release` (odzkoušená verze), `testing` (příští verze ve fázi testování), `nightly` (nejnovější vývojové sestavení), nebo `off`. Výchozí hodnota odpovídá verzi, kterou jste nainstalovali. Na vývojářském počítači se neukazuje. |
| *Diagnostika*: *Uchovávat logy na flashce:* | Od dalšího startu ukládá na flashku všechny logy, nejen po pádu - zapněte ho, když se pídíte po nějakém problému (kapitola 7). |
| *Zobrazit výkon:* | V levém dolním rohu ukáže překryv se snímkovou frekvencí, vytížením procesoru, vlákny a pamětí; ve hře emulátor ukazuje také své FPS a vytížení procesoru. |

**Změna režimu obrazovky.** Když Možnosti opustíte s novým režimem v *Obraz:*, AutoBleem se na něj přepne
a zeptá se *Ponechat tento režim obrazu?*. Pokud je obraz v pořádku, potvrďte to. Pokud televize nic neukazuje,
počkejte: bez potvrzení se AutoBleem po odpočtu vrátí k předchozímu režimu.

**Témata na obrazovce 4:3.** V režimu *CRT 4:3* ukazuje seznam témat jen ta, která mají rozvržení pro 4:3. Pokud
ho vaše téma nemá, po potvrzení režimu (a při každém startu v tomto režimu) ho nahradí výchozí téma a oznámení
vám to řekne: *Téma změněno na výchozí (CRT 4:3)*.

![Možnosti rozdělené do skupin](../images/en/options.jpg)

![Skupina Obraz: Okraj CRT a Výška obrazu](../images/en/options-display.jpg)

![Oznámení po přepnutí na CRT 4:3 s tématem, které nemá rozvržení 4:3](../images/en/crt43-theme-notice.jpg)

### 3.7 Nastavení hry

Každá hra může mít svá vlastní nastavení. Většina her běží dobře tak, jak je, ale sem tam některá potřebuje
trochu pomoct - ostřejší nebo měkčí obraz, vynechaný snímek, aby běžela plynule, jinou paměťovou kartu - nebo ji
chcete označit jako oblíbenou. V editoru hry tohle změníte jen pro tu jednu hru, na ostatní nesáhnete.

Když máte hru vybranou, stiskněte **Dolů** a pod ní se otevře řada ikon. Jsou čtyři: *NASTAVENÍ* (Možnosti
z oddílu 3.6), *Hra* (vlastní nastavení této hry), *PAMĚŤOVÁ KARTA* (její paměťová karta) a *OBNOVIT* (její
uložené pozice). Přejděte na jednu z nich a otevřete ji tlačítkem Cross.

**Editor hry** (ikona *Hra*) ukazuje vpravo podrobnosti o hře - název, vydavatele, rok, počet hráčů, složku
a paměťovou kartu - a vlevo její nastavení. Nahoru a Dolů přecházíte mezi nastaveními, Vlevo a Vpravo je měníte,
stejně jako v Možnostech; podržené tlačítko pohyb opakuje. Až budete hotovi, Circle změny uloží a vrátí vás zpět.
Hra, která ve svých datech nemá název, se ukazuje pod názvem své složky.

Nastavení jsou ve čtyřech skupinách:

- **Hra** se týká toho, jak s hrou zachází AutoBleem. *Oblíbené:* ji zařadí do skupiny *Oblíbené hry* ve výběru
  sady. *Zamknout data:* řekne skeneru, ať název hry, sériové číslo a seznam disků nechá přesně tak, jak jste je
  nastavili, aby vaše úpravy příští skenování nepřepsalo. *Pokračování:* určuje, co se stane, když spustíte hru,
  která má body obnovení: *Zeptat se* ukáže výběr pozic, *Poslední pozice* rovnou pokračuje z nejnovější pozice
  a *Nikdy* spustí hru vždy od začátku. Tam, kde je nainstalovaný RetroArch, jsou tu ještě dva řádky. *Hra
  Lightgun:* je pro hry se světelnou pistolí: hra se zařadí do skupiny *Hry se světelnou pistolí* a vždy poběží
  v RetroArch, protože jeho jádro pro PS1 umí GunCon (zapnutím se zapne i další řádek). *Hrát pomocí RA:* spustí
  tuhle jednu hru v RetroArch místo v emulátoru PS1.
- **Obraz** se týká toho, jak obraz vypadá. *Rozlišení:* vykresluje hru v 1x nebo 2x (na vestavěném GPU)
  a *Odstranit švy:*, které funguje jen při 2x, skryje tenké čáry, jež se při této velikosti mohou mezi částmi
  obrazu objevit. *Dithering:* (*Vypnuto*, *Zapnuto*, *Vždy*) řídí jemný vzor teček, kterým PlayStation míchá
  barvy, a *Vyhlazování:* vybere jeden z vyhlazovacích filtrů emulátoru. *Filtr:* rozhoduje, jak se obraz
  přizpůsobí obrazovce: *Nejbližší* ukáže čisté pixely, *Lineární* je vyhladí, *Ostrý* a *Ostrý (jednoduchý)*
  udrží pixely ostré bez mihotání, a pak je tu *Quilez*. Filtry CRT *CRT (fast)*, *CRT (raster)* a *CRT-Pi*
  napodobují starou televizi a kreslí si vlastní řádky, takže řádky pro obrazové řádky zešednou, dokud je
  některý z nich vybraný. Jinak *Obrazové řádky:* přidají tmavé linky staré televize a *Jas obrazových řádků:*
  určuje, jak moc budou tmavé. *Rozlišení*, *Odstranit švy*, *Dithering*, *Vyhlazování* a filtry kromě
  *Lineární* a *Nejbližší* jsou pro `pcsx-abnxt`; klasický `pcsx-ab` a RetroArch ukazují každý jiný filtr jako
  *Nejbližší*.
- **Vykreslování** obsahuje *Plugin:* pro GPU a *Přeskočení snímků:* (*Auto*, *Vypnuto*, nebo 1 až 3 snímky).
  Vynechávání snímků pomůže hře, která běží příliš pomalu, udržet rychlost, za cenu méně plynulého obrazu.
- **Emulátor** obsahuje *SpeedHack:*, *CPU hodiny:*, *Interpolace zvuku:* (jak se vyhlazuje zvuk), *Logo při
  spuštění:* a s `pcsx-abnxt` také *Opravy Sony:*. Když vypnete *Logo při spuštění:*, přeskočíte úvodní obrazovku
  BIOSu - to potřebujete u homebrew disku, který se kvůli vlastnímu logu nespustí.

Tvar obrazu a rozlišení obrazovky se nenastavují pro každou hru zvlášť, ale pro všechny najednou v Možnostech
(*Škálování obrazu emulátoru:* a *Obraz:*).

**Další tlačítka v editoru.** Triangle hru přejmenuje pomocí klávesnice na obrazovce. Square dá hře jinou
paměťovou kartu (*Změnit paměťovou kartu*). Dokud hra používá svou vlastní kartu, Start z ní udělá novou sdílenou
sadu, aby ji mohly používat i jiné hry (*Sdílet paměťovou kartu*, oddíl 3.8). Tyhle dvě možnosti se u interních
her konzole nenabízejí. Podržením Vlevo / Vpravo nebo Nahoru / Dolů se pohyb opakuje - tady i v obrazovkách
s možnostmi her a jádry RetroArch.

Hra z mechaniky, která nemá soubor `pcsx.cfg`, si nastavení uložit neumí; když nějaké změníte, editor vám
oznámí *Neuloženo: hra nemá pcsx.cfg*.

U **disku v mechanice** (oddíl 3.9a) některá nastavení nedávají smysl, takže je editor zašedí, a když na takový
řádek přejdete, řádek dole napíše *Není k dispozici pro disk v mechanice*.

![Editor hry pro disk v mechanice](../images/en/game-editor-disc.jpg)

**Nastavení uložená v emulátoru.** Hru můžete doladit i během hraní: vlastní nabídka emulátoru má položku *Save
settings for this game* (oddíl 3.9). Jakmile má hra nastavení uložená tam, hraje se s nimi. Editor hry pak
ukazuje její řádky Obraz, Vykreslování a Emulátor zašedlé, s uloženými hodnotami, pod nadpisem *Uloženo
v emulátoru* - můžete si je přečíst, ale ne změnit. Pokud chcete znovu používat nastavení z editoru hry, zvolte
*Odemknout nastavení* a potvrďte to: nastavení uložená emulátorem se smažou a řádky půjde zase měnit. Oba
emulátory, `pcsx-ab` i `pcsx-abnxt`, čtou a zapisují stejná uložená nastavení, takže nezáleží na tom, který je
uložil.

![Editor hry](../images/en/game-editor.jpg)

### 3.8 Paměťové karty a uložené pozice

Na skutečném PlayStationu byste se o jednu nebo dvě paměťové karty dělili mezi všechny hry a dřív nebo později
by vám na nich došlo místo. V AutoBleemu má každá hra z PS1 standardně vlastní paměťovou kartu, takže nemusíte
řešit, kolik je na ní místa ani na které kartě je která pozice. Karta je uložená spolu s uloženými pozicemi hry
ve složce `Games/!SaveStates/<složka hry>/`.

**Sdílené sady paměťových karet.** Někdy potřebují hry vidět navzájem svá uložení - třeba pokračování, které
načte uloženou hru z prvního dílu, nebo díly série, které chcete mít na jedné kartě. Pro takový případ si
vytvoříte sdílenou sadu: jednu kartu, kterou používá víc her. Sady jsou ve složce `Games/!MemCards/` a spravujete
je položkou *Paměťové karty* v systémové nabídce. Square vytvoří novou sadu (název napíšete na klávesnici na
obrazovce), Cross vybranou sadu přejmenuje a Triangle ji smaže - ale nejdřív se zeptá. Hře přiřadíte sadu
tlačítkem *Změnit paměťovou kartu* v jejím editoru (oddíl 3.7), nebo přes její ikonu *PAMĚŤOVÁ KARTA*.

**Editor paměťových karet** se otevře z ikony *PAMĚŤOVÁ KARTA* u hry. Ukazuje kartu hry a druhou kartu vedle
sebe, u každé uložené hry její ikonu a název, podobně jako obrazovka paměťových karet na původní konzoli. Square
zkopíruje vybranou pozici na druhou kartu, Triangle ji smaže a Select kartu defragmentuje - stáhne volné bloky
k sobě, aby se tam zase vešla větší uložená hra. Start vám dovolí vybrat, která sada se ukáže vpravo, a Cross
obě karty znovu načte z flashky. Karta, na kterou hra ještě nic nezapsala - protože jste v ní ještě neukládali -,
je prázdná a vedle názvu má *zatím žádná karta*. Pokud jste něco změnili, AutoBleem se před opuštěním editoru,
novým načtením karet nebo zobrazením jiné sady zeptá *Chcete uložit data paměťových karet?*.

![Editor paměťových karet](../images/en/memory-card-editor.jpg)

**Body obnovení.** Spousta her pro PS1 dovoluje ukládat jen na určitých místech a ne vždycky k nějakému
dojdete, než musíte přestat. Na to jsou body obnovení: když hru z PS1 opustíte tlačítkem Reset na konzoli (nebo
přes nabídku emulátoru na Pi či PC), AutoBleem si uloží pozici přesně tam, kde jste byli. Zatímco ji při
odchodu ze hry zapisuje, emulátor ukazuje *Please wait...*. Příště budete pokračovat přesně od té chvíle.

Najdete je pod ikonou *OBNOVIT* u hry. Hra s bodem obnovení má na ikoně malý obrázek z něj; hra bez nich má
ikonu zašedlou. Výběr pozic má čtyři pozice, zobrazené jako karty v rámečku, každou s obrázkem dané chvíle,
číslem pozice a datem. Nejnovější je označená **NEJNOVĚJŠÍ** a nepoužitá pozice hlásí *Žádný bod obnovení*. Cross
pokračuje ve hře z vybrané pozice a Triangle ji smaže. Jestli se výběr při spuštění hry vůbec ukáže, záleží na
nastavení *Pokračování:* u hry (oddíl 3.7).

Body obnovení mají i hry z PS1, které hrajete v RetroArch. Každá pozice nese odznak - logo AutoBleem 2 nebo
logo RetroArch - takže je vidět, který emulátor ji zapsal.

![Výběr pozic pro pokračování](../images/en/resume-picker.jpg)

### 3.9 Spouštění her, RetroArch a aplikace

Spouštět hry budete nejčastěji, a proto na to stačí jedno tlačítko: vyberte hru na polici a stiskněte **Cross**.
Hra z PS1 se otevře na celé obrazovce v emulátoru PS1, který jste zvolili v Možnostech (oddíl 3.6), a běží,
dokud ji neopustíte. Pokud byste hru z PS1 radši hráli v RetroArch - protože tam běží lépe, nebo protože máte
rádi jeho možnosti - stiskněte místo toho **Square**.

**Jak hru opustit.** Na PlayStation Classic dělají tlačítka konzole přesně to, co čekáte. **Reset** vpředu vás
vrátí do spouštěče a uloží bod obnovení tam, kde jste byli, abyste mohli později pokračovat (oddíl 3.8); funguje
i ve chvíli, kdy je otevřená nabídka ve hře. **Power** konzoli vypne. Raspberry Pi ani PC taková tlačítka nemají,
takže tam hru opouštíte přes nabídku emulátoru ve hře, popsanou níže.

Existuje i cesta ven, která funguje stejně na každém ovladači - původním z konzole, na USB i přes Bluetooth:
**podržte na 2 sekundy Start + Select, nebo Home**, a jste zpátky v AutoBleemu. Krátký stisk stejných tlačítek
místo toho otevře nabídku emulátoru. Spouštěč vám obojí připomíná v nápovědě (*Podržte Select+Start nebo Home
2 sekundy: zpět do AutoBleem* a *Krátký stisk Select+Start nebo Home: nabídka emulátoru*). Aplikace nabídku
emulátoru nemají, takže u nich funguje jen dlouhé podržení. Na konzoli Reset ukončí vždy i aplikaci.

**Nabídka ve hře.** S `pcsx-abnxt` má emulátor vlastní nabídku na věci, které při hraní potřebujete: ukládání,
výměnu disků, úpravu obrazu, výběr ovladačů. Stiskněte tlačítko nabídky - Home na ovladači, který ho má,
**Select + Start** na ovladači bez něj, nebo **Esc** na klávesnici - a hra se za nabídkou pozastaví, s posledním
obrázkem v pozadí. Když tlačítko nabídky podržíte 2 sekundy, stane se totéž co po stisku Reset: hra skončí.
Nabídka má tři karty a L1 a R1 mezi nimi přepínají. Pamatuje si, kde jste byli, takže se příště otevře na stejné
kartě a stejném řádku.

- Karta **Game** se týká samotné hry. *Resume game* nabídku zavře a hrajete dál. Pod *Saves* je *Quick save*,
  které uloží chvíli, ve které jste, a *Quick load*, které ji vrátí. *Load autosave* vás vrátí do stavu hry až
  30 sekund nazpátek - emulátor si tuhle kopii během hraní drží v paměti a zachrání vás před chybou, kterou už
  nejde vzít zpět. Pod *CD disc* je *Change disc* pro hru na více discích, když chce další disk, a *Reset game*
  spustí hru znovu od začátku. *Save settings for this game* uloží nastavení, která jste pro tuhle jednu hru
  zvolili (oddíl 3.7). *PCSX menu* otevře vlastní stránky PCSX-ReARMed s jeho možnostmi, cheaty a informacemi
  o programu a *Exit* vás vrátí do AutoBleemu.
- Na kartě **Picture** měníte, jak hra vypadá, a změnu hned vidíte: *Display*, *Resolution* (1x nebo 2x),
  *Remove seams*, *Dithering*, *Scaling*, *Smoothing*, *Filter*, *Scanlines* a *Scanline brightness*. Jde
  o stejná nastavení jako v editoru hry (oddíl 3.7) a každý řádek má vpravo řádek nápovědy, který vysvětluje, co
  dělá. *Display* je rozlišení obrazovky; na konzoli ho volíte v Možnostech a tady je jen vidět. Filtr CRT-Pi je
  pro konzoli při 1080p příliš náročný. Řádek, který se nehodí, je zašedlý a jeho nápověda vysvětlí proč.
- Karta **Controllers** rozhoduje, co je zapojené do dvou portů PlayStationu, *Controller 1* a *Controller 2*:
  standardní (digitální) ovladač, analogový ovladač (DualShock), pistole, nebo nic. Některé hry fungují jen
  s jedním druhem ovladače. Změna se projeví, až se vrátíte do hry.

Nabídka je nakreslená ve vzhledu ab2.0.0 samotného spouštěče, takže nepůsobí jako jiný program, a ukazuje stav
baterií vašich ovladačů i obrázek z posledního rychlého uložení.

**Hry pro RetroArch.** Hra z jiného systému se spustí v RetroArch s jádrem, které spouštěč pro daný systém
vybral. Až dohrajete, vrátí vás do spouštěče *Close Content* nebo *Quit RetroArch* v nabídce RetroArch. Pokud
chcete změnit, které jádro hraje který systém, otevřete v Rychlé nabídce *Jádra RetroArch* (oddíl 3.4); seznam
se otevře s jádrem *PlayStation 1* nahoře. A pokud chcete vlastní nabídku RetroArch (XMB) s jeho nastavením
a seznamy obsahu, zvolte v systémové nabídce *RetroArch*: RetroArch se pak otevře bez načtené hry.

![Okno jader RetroArch s jádrem PlayStation 1 nahoře](../images/en/retroarch-cores.jpg)

**Aplikace.** Aplikace nejsou hry, ale programy: nástroje pro konzoli a na konzoli také doplňkové aplikace, které
přicházejí v balíčku RetroArch - Doom, Quake, Amiga a další. Najdete je v sadě Aplikace. Než se aplikace spustí,
AutoBleem ukáže její popis, abyste věděli, co to je a jak se ovládá. Cross ji spustí a Circle vás vrátí na
polici.

![Popis aplikace, který se ukáže před jejím spuštěním](../images/en/app-start.jpg)

**Nastavení aplikace.** Spousta aplikací vznikla pro jeden konkrétní ovladač, a tak můžete změnit, jak vidí ten
váš. Vyberte aplikaci, otevřete řadu ikon a zvolte *Hra*: otevře se *Nastavení hry* aplikace (*Změnit způsob spuštění tohoto programu*). *Režim ovladače:*
určuje, jaký ovladač aplikace podle svého dojmu má. *Automaticky* použije to, co si aplikace sama vyžádá;
*Ovladač PSC* a *Ovladač Xbox 360* vydávají váš ovladač za ovladač konzole nebo za ovladač Xbox 360 a *Ovladač
PSC (systémový)* a *Ovladač Xbox 360 (systémový)* dělají totéž přes samotný systém. Když aplikace na váš ovladač
nereaguje, jak by měla, zkuste jiný režim. *D-pad jako páčka:* nechá směrový kříž hýbat analogovou páčkou, pro
aplikaci, která poslouchá jen páčku, a *Páčka jako D-pad:* dělá opak.

Některé aplikace se vás při prvním spuštění na něco zeptají. Jedna chce vědět *Jaké ovládání má váš ovladač?*,
aby si podle toho nastavila ovládání: odpovězte *Jeden D-pad* u ovladače jen se směrovým křížem, nebo
*Analogové páčky*. Aplikace, která spouští Windows, se zeptá *Co chcete udělat?* a nabídne spuštění Windows,
jejich instalaci, spuštění DOSu nebo odinstalování Windows. Když vám aplikace dovolí nastavit klávesu, požádá
vás *Stiskněte jedno z tlačítek.*

![Nastavení hry u aplikace](../images/en/app-game-settings.jpg)

Program pro Windows spouštěný přes PE runner (PE aplikace, oddíl 3.3) s vámi mluví přes vlastní obrazovky
AutoBleemu: zpráva, kterou chce ukázat, se objeví jako *Zpráva* a otázka s možnostmi jako *Vyberte možnost*,
obojí s názvem aplikace v titulku.

![Otázka PE aplikace zobrazená jako obrazovka AutoBleemu](../images/en/pe-dialog.jpg)

### 3.9a Disk v USB mechanice

Ke konzoli, Raspberry Pi nebo PC spuštěnému z flashky AutoBleem můžete připojit obyčejnou USB mechaniku CD/DVD
a hrát přímo z originálního disku PlayStation - nic se přitom nekopíruje. Vložený disk se ve spouštěči objeví
jako další hra. Ve Windows to nefunguje.

**Kopírování disku na flashku.** Pokud chcete mít hru vždycky po ruce i bez disku, stiskněte Square
(*Kopírovat disk*). AutoBleem se nejdřív zeptá, jestli hru zkopírovat a kolik místa zabere, a pak ji uloží do
složky `Games` jako jediný soubor CHD (hra na více discích dostane navíc soubor `.m3u`, aby ve hře fungovala
výměna disků). Během kopírování vidíte rychlost a zbývající čas a *Přerušit* kopírování zastaví. Když je hotovo,
stojí hra na polici jako každá jiná. AutoBleem nezkopíruje hru, která už v `Games` je, ani takovou, pro kterou
není místo - v tom případě vám řekne, kolik místa potřebuje. Zkopírovat jde i poškrábaný disk: části, které se
nepodařilo přečíst, se vyplní nulami a AutoBleem vám řekne, kolik jich bylo. Taková kopie může, ale nemusí
fungovat.

Square nabízí kopii u každého herního disku PlayStation v zobrazení disku, i u takového, který databáze obalů
neznají. Hra, kterou databáze znají, se zkopíruje pod svým názvem; u hry na více discích zkopírujte disky jeden
po druhém a soubor `.m3u` je seřadí, disk 1 jako první. Disk, který databáze neznají, dostane místo názvu své
sériové číslo, zkopíruje se jako jediný disk a na polici nemá obal. Okno kopírování, *Kopírování disku*, zůstane
na obrazovce, dokud kopie neskončí nebo ji nezastavíte - spouštěč mezitím čeká - a rychlost ukazuje jako násobek
běžné mechaniky CD. Pokud se kopírování nepovede, AutoBleem vám řekne proč.

![Kopírování disku](../images/en/disc-copy.jpg)

**Hraní z disku.** Když disk vložíte, **zobrazení disku** se otevře samo, jakmile je disk načtený. Ukazuje obal
disku - z databází obalů, nebo stažený z internetu - s jeho sériovým číslem a názvem, a Cross hru spustí. Hra
z PS1 hraná z disku si body obnovení a uložené hry ukládá do vlastní složky, takže můžete přestat a později
pokračovat, stejně jako u hry na flashce. Po hře, nebo když jste byli v Možnostech či v nastavení rozšíření, se
vrátíte do zobrazení disku. Když ho opustíte tlačítkem Circle, abyste se podívali na ostatní hry, disk zůstane
v mechanice a Circle na polici zobrazení zase vrátí; na prázdné polici ho otevře i R1 (*Disk*). Na polici
s hrami si R1 ponechá svou obvyklou práci, skákání mezi počátečními písmeny. Když disk vyndáte, zobrazení disku
se zavře.

![Zobrazení disku](../images/en/disc-view.jpg)

**Čip mechaniky** nahoře na obrazovce vám říká, co mechanika právě dělá, abyste věděli, jestli máte čekat. Bez
připojené mechaniky neuvidíte nic. Mechanika bez disku ukazuje tlumenou ikonu disku. Během čtení disku ikona
bliká a hlásí *Čtu disk...*, a jakmile je disk připravený, ikona se rozsvítí i s jeho názvem. Pokud vložíte disk,
který není hra pro PlayStation ani hudební CD, čip napíše *Toto není disk PlayStation*, a když mechanika disk
zrovna přečíst nemůže, hlásí *Disk teď nelze přečíst*.

![Čip mechaniky](../images/en/disc-chip.jpg)

**Hudební CD.** Mechanika umí přehrávat i hudební CD. Hudební CD otevře místo zobrazení disku **CD přehrávač**.
Ten ukazuje disk jako *Audio CD* se seznamem skladeb a celkovou délkou a řádek pod ním uvádí vybranou skladbu
a jestli je zapnuté opakování a náhodné pořadí. Disk, který přehrávač přehrát neumí, je označený *Tento disk
nelze přehrát*. Tlačítka přehrávače:

| Tlačítko | V CD přehrávači |
|---|---|
| Cross | Přehraje vybranou skladbu. |
| Start | Pozastaví hudbu a znovu ji pustí. |
| Square | Zastaví hudbu. |
| L1 / R1 | Přejde na předchozí nebo další skladbu. |
| L2 / R2 | Převine skladbu zpět nebo dopředu, vždy o pět sekund. |
| Triangle | Mění, co se opakuje: nic, celý disk, nebo aktuální skladba. |
| Select | Zapne nebo vypne náhodné pořadí, takže skladby hrají napřeskáčku. |
| Circle | Opustí CD přehrávač. |

![CD přehrávač](../images/en/cd-player.jpg)

**Disky s LibCrypt.** Některé hry pro PlayStation, většinou evropské, mají ochranu proti kopírování jménem
LibCrypt. Aby běžely, potřebuje emulátor malý soubor `.sbi` s údaji o ochraně. AutoBleem si ho sám stáhne z webu
před spuštěním takového disku a při jeho kopírování a zkopíruje ho spolu se hrou. Potřebuje k tomu síť: na
Raspberry Pi nebo PC tu, kterou už má, na konzoli WiFi, kterou nastavíte v PSC-Bios.

U disku v mechanice některá nastavení hry nedávají smysl, a tak je jeho editor hry zašedí (oddíl 3.7).

### 3.10 Přidávání her

AutoBleem si vaše hry najde sám, pokud jsou na správném místě. Tady se dozvíte, kam patří který druh, aby je
každé skenování postavilo na polici s názvem a obalem.

**Hry z PS1** patří do složky `Games`, **každá do vlastní složky** pojmenované podle hry. Hry můžete seskupit
i do vlastních složek a z každé takové složky se ve výběru sady stane skupina (oddíl 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                složka s hrami: ve výběru sady vlastní skupina
    Klonoa/                   Klonoa.pbp
```

AutoBleem čte obvyklé formáty obrazů disků: `.cue` s `.bin` (nebo `.img`), `.pbp`, `.chd` (i komprimované
pomocí zstd), `.iso` a `.ecm`, které skenování samo dekóduje. Funguje i hra zabalená do zipu: procesor **Unzip**
ji rozbalí dřív, než ji skenování přečte (oddíl 3.14).

Pořádek mít nemusíte. Hra na více discích patří do jedné složky se všemi disky, ale když nakopírujete složky
pojmenované `Game (Disc 1)`, `Game (Disc 2)` a tak dále, skenování je sloučí do jedné složky `Game`. Hry
nahrané rovnou do `Games/` jako volné soubory skenování také samo roztřídí do vlastních složek.

**Názvy a obaly** přijdou samy. Skenování přečte sériové číslo každého disku a vezme název, vydavatele, rok, počet
hráčů a oblast z databáze PlayStation v RetroArch nebo z databází obalů. Pokud chcete vlastní obal, dejte vedle
obrazu hry soubor PNG nebo JPEG se stejným názvem. Bez něj přijde obal z databází obalů nebo, s nainstalovaným
RetroArch, ze sady náhledů libretro; na Raspberry Pi, PC nebo ve Windows se chybějící obal stáhne z internetu
(Možnosti → *Stahovat obaly online:*). Když skenování něco popletě, opravte to v editoru hry a zapněte *Zamknout
data:*, aby vaši změnu příští skenování nechalo být.

**Hry z ostatních systémů** patří do `RetroArch/roms/`, **pro každý systém jedna složka pojmenovaná tak, jak ho
jmenují databáze RetroArch** - například `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo
Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` nebo `FBNeo - Arcade Games`
(či `Arcade`). Složky se vytvoří samy a ROMy mohou zůstat zazipované. Na Raspberry Pi, PC nebo ve Windows je
skenování přečte samo a zapíše playlisty RetroArch. Flashka pro konzoli to sama nezvládne, takže tam spusťte na
PC **UpdateRoms** (kapitola 5).

**Aplikace** patří do `Apps/<název>/`, každá se souborem `app.ini` - název, ikona a co spustit - a souborem
`run.sh`.

**Balíčky.** Některé aplikace jsou herní enginy: než mohou hru hrát, potřebují data hry, kterou vlastníte. Takhle
fungují Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, hry pro
DOS a další. Soubory hry dejte na flashce do složky `Packages`, každou hru do vlastní složky - například
`Packages/Doom/DOOM2.WAD` - a AutoBleem je rozpozná podle tabulky, kterou s sebou má (`rc/packages.ini`).
Ve složce, kterou rozpozná, jsou volné herní soubory samostatnými balíčky. AutoBleem vaše soubory jen čte, nikdy
je nemění. Balíček může přijít i z Obchodu (oddíl 3.13).

Tam, kde ho spouštěč ukazuje, vypisuje řádek *Balíčky* na kartě Aplikace (oddíl 3.3) nalezená herní data. Cross
na položce otevře její **Package info**: co data obsahují, popis, kde soubory jsou a odkud přišly (vaše vlastní
soubory, Obchod, mod, nebo soubory dodané uvnitř aplikace), jestli jde o shareware nebo volně šiřitelnou hru
a která nainstalovaná aplikace je spustí. Pokud je nic z toho, co máte nainstalované, spustit neumí, informace
vám to řeknou.

Když spustíte aplikaci s enginem, AutoBleem hledá herní data, která umí spustit. S jednou sadou dat se hra spustí
hned. Když jich je víc, seznam (*Vyberte herní data*) se zeptá, kterou hrát, a nastaví se na tu, kterou jste
zvolili minule. Pokud žádná nejsou, AutoBleem vám řekne, jaká data aplikace potřebuje a kam je dát, a nic se
nespustí.

**Vaše vlastní hry.** Když AutoBleem nějaká data nerozpozná, jejich Package info hlásí *Nerozpoznáno. Pokud jde
o hru, viz příručka: Vaše vlastní hry.* Tabulka zná jen hry, pro které vznikla. Pro jinou hru si napište řádek do
vlastního souboru `packages.ini` ve složce `Packages`: AutoBleem čte nejdřív ten váš, takže vaše řádky mají
přednost.

![Výběr balíčku, kde zvolíte herní data, se kterými hra začne](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Skenování jen části.** Pokud jste přidali hry jen do jedné sady nebo složky, *Znovu skenovat hry* umí
naskenovat jen tu část, což je rychlejší než skenovat všechno, a jeho bublina po dokončení zmizí.

**Témata** patří do `Themes/<název>/` se souborem `theme.json` a obrázky - nebo do `Themes/` vložte zip
s tématem tak, jak je.

### 3.11 BIOS pro PS1

BIOS je vlastní startovací program PlayStationu a emulátor hraje hry nejvěrněji právě se skutečným BIOSem. Na
**PlayStation Classic** nemusíte nic dělat: emulátor použije BIOS konzole. Na **Raspberry Pi, PC a ve Windows**
dejte své vlastní soubory BIOS pro PS1 do `System/Bios/`: `romw.bin` (americký/evropský SCPH-5501/5502)
a `romJP.bin` (japonský SCPH-5500, pro japonské hry). Instalátory je doplní z balíčků BIOS pro RetroArch, pokud
tam už nejsou vaše vlastní - ty nikdy nepřepíšou. Bez nich běží emulátor na vestavěném HLE BIOSu, náhradě, kterou
mnoho her přijme a některé ne; když tedy hra nechce naběhnout, chybějící BIOS je první, co zkontrolovat.

### 3.12 Aktualizace

AutoBleem se udržuje aktuální sám, takže nové funkce a opravy dostanete bez přeinstalování. Když se spouštěč
spustí, a pak jednou denně, podívá se na web, jestli na jeho **kanálu** není nová verze. Kanál si vyberete
v Možnostech → *Aktualizace:*: `release`, `testing`, `nightly`, nebo `off`, pokud nechcete, aby se díval vůbec.
Pokud nechcete čekat na denní kontrolu, *Aktualizace softwaru* v systémové nabídce zkontroluje hned.

Když je k dispozici nová verze, AutoBleem se zeptá, co dělat. *Aktualizovat nyní* ji stáhne a nainstaluje, což
trvá pár minut. *Připomenout zítra* se zeptá znovu za den a *Přeskočit tuto verzi* se na tuhle verzi už ptát
nebude. Ať zvolíte cokoli, vaše hry, uložené pozice a nastavení vždycky zůstanou; po aktualizaci spouštěč hry
ještě jednou naskenuje. Štítek kanálu v levém horním rohu (oddíl 3.1) ukazuje, jaké sestavení máte.

Jak se aktualizace nainstaluje, záleží na stroji:

- Na **Raspberry Pi** a **flashce pro PC** se po stažení znovu spustí instalátor se stejnou obrazovkou průběhu
  jako při prvním spuštění a nabídne i novější RetroArch. Pak je spouštěč zpátky.
- Ve **Windows** se otevře stažený instalátor, nainstaluje novou verzi a spustí nový spouštěč.
- Na **PlayStation Classic** se umí aktualizovat sama jen konzole s **jádrem AutoBleem** (ABFlashKit, oddíl 6.2)
  a **sítí WiFi** nastavenou v PSC-Bios (oddíl 6.1) - konzole v továrním stavu síť nemá, takže spouštěč ani
  nehledá. Po *Aktualizovat nyní* se spouštěč zavře a na obrazovce zůstane obrázek AutoBleem, zatímco se flashka
  aktualizuje, což trvá pár minut; pak se spustí nový spouštěč. Bez sítě vám *Aktualizace softwaru* oznámí
  *Nepřipojeno*. Každou flashku pro konzoli můžete aktualizovat i z PC pomocí `AutoBleemInstaller.exe`
  (oddíl 2.1).

### 3.13 Rozšíření a Obchod AutoBleem

**Rozšíření** přidávají do spouštěče nové věci - vlastní obrazovky a funkce - aniž by měnila samotný AutoBleem.
Obchod AutoBleem i PSC-Bios jsou rozšíření. Rozšíření bydlí ve složce `Extensions/<název>/` na flashce (na
Raspberry Pi na jeho datovém oddílu, ve Windows ve složce s daty); nainstalujete ho tak, že tam rozbalíte jeho
zip.

Prohlédnout si je můžete v systémové nabídce (**L2 + R2**) pod položkou *Rozšíření*. Ta od týmu AutoBleem jsou
nahoře a ostatní následují pod nadpisem *Rozšíření třetích stran*. Cross vybrané rozšíření spustí a Triangle ho
vypne, nebo zase zapne. Výjimkou je PSC-Bios na konzoli: nastavujete jím WiFi, ovladače a hodiny, takže se tam
vypnout nedá. Když rozšíření spustit nejde, jeho řádek vám řekne proč - potřebuje síť a žádná není, není určené
pro tento systém, vzniklo pro jinou verzi AutoBleemu a potřebuje aktualizovat, nebo se ho nepodařilo načíst.
Pokud by některé rozšíření spouštěč někdy shodilo, AutoBleem ho vypne a seznam vám to oznámí; tady ho pak můžete
znovu zapnout.

![Seznam Rozšíření](../images/en/extensions.jpg)

**Obchod AutoBleem** je první rozšíření: místo, kde procházíte aplikace a hry a jedním stiskem je instalujete,
a to na každém systému, na kterém AutoBleem běží. PlayStation Classic k tomu potřebuje jádro AutoBleem, protože
WiFi přichází s ním. Otevřete ho z Rychlé nabídky (*Obchod*, oddíl 3.4). Má čtyři karty a L1 a R1 mezi nimi
přepínají.

Karty **Apps** a **Games** vypisují, co zdroje nabízejí, každou položku s obrázkem, verzí, velikostí a malou ikonou
zdroje, ze kterého pochází. Karta Apps uvádí také PE aplikace s jejich licencí a zdrojem a balíčky s herními daty
(oddíl 3.10). Co už máte nainstalované, nese odznak *Installed*. Lišta nápovědy ukazuje tlačítka, která pro
vybraný řádek platí:

| Tlačítko | Na kartách Apps a Games |
|---|---|
| Cross | Položku nainstaluje - nebo ji aktualizuje, po chybě to zkusí znovu, či zruší stahování, které čeká nebo běží. |
| Triangle | Odebere něco, co nainstaloval Obchod. |
| Square | Obnoví seznamy ze zdrojů. |
| L2 / R2 | Skočí na předchozí nebo další počáteční písmeno. |
| Select | Ukazuje zdroje po jednom, když chcete vidět, co nabízí jen jeden z nich. |
| Start | Hledá v názvech. |

Obrázky se po načtení uchovávají, takže se seznamy příště objeví rychle, a obrázek, který se nenačetl, můžete
zkusit načíst znovu.

Karta **Downloads** ukazuje, co se stahuje, co čeká, co selhalo a co je nainstalované, s ukazatelem průběhu, který
se posouvá plynule. Hlídat ji nemusíte: stahování pokračují na pozadí, i když Obchod opustíte, a zatímco jste
jinde ve spouštěči, bublina ukazuje běžící stahování s rychlostí a zbývajícím časem (například
`1.4 MB/s · 0:42`). Spuštění hry nebo vypnutí stahování jen pozastaví a přerušené stahování pokračuje tam, kde
skončilo. Když vypadne síť, položka hlásí *Waiting for the network* a po návratu sítě pokračuje od místa, kde
byla; po 30 minutách bez sítě to vzdá. Stahování větší než 2 GB fungují na každé platformě, i na 32bitových
sestaveních. Hra, kterou nainstalujete, se objeví na polici po dalším skenování a jako obal dostane obrázek
z Obchodu.

Karta **Sources** ukazuje, odkud seznamy pocházejí, každý zdroj s ikonou: vlastní katalog AutoBleemu, jakýkoli
seznam TSV vložený do `System/Extensions/store/sources/` a adresy, které si přidáte sami přes *Add a source URL*.
Cross na zdroji, který jste přidali, vám dovolí ho přejmenovat, změnit jeho adresu, přepnout ho mezi `http://`
a `https://` nebo ho odebrat.

![Karta Apps v Obchodě](../images/en/store-apps.jpg)

![Nabídka zdroje, který jste přidali](../images/en/store-source-menu.jpg)

Co nabízí vlastní katalog AutoBleemu, najdete také na stránce ke stažení na adrese
`https://autobleem.retromenele.pl/store/`. Se zdrojem, který si přidáte sami, je to jiné: **za obsah zdrojů,
které přidáte, odpovídáte vy.**

**Vlastní hry ve vaší síti.** Pokud máte hry pro PS1 doma na jiném počítači, `abstored`, server Obchodu pro
místní síť, je může Obchodu nabídnout po síti a vy je nainstalujete jako jakoukoli jinou položku. Běží na každém
linuxovém stroji - na Raspberry Pi, na domácím serveru - a složku jen čte, nikdy ji nemění. Spustíte ho příkazem
`abstored <složka s hrami>` a pak v prohlížeči otevřete `http://<ten stroj>:8124/`: stránka ukazuje, co server
nabízí, a případné problémy, na které narazil. V Obchodě pak přidejte jako zdroj `http://<ten stroj>:8124/store.tsv`.
Hotové programy pro Linux a Windows najdete na stránce Obchodu na kartě **LAN server** a `INSTALL-linux.md`
(ve zdrojovém kódu v `ext_store/server/`) vysvětluje, jak ho nastavit jako službu. **LAN Share** (oddíl 5.2)
nahraje na takový server hry a disky z PC.

### 3.14 Procesory skenování

Procesory skenování připraví vaše hry dřív, než je AutoBleem přečte. Procesor je malý program, který každé
skenování spustí jako první. Umí převést formát, který AutoBleem nečte, na takový, který čte - například rozbalit
zazipovanou hru -, nebo změnit data hry, třeba použít patch s překladem. Procesory bydlí ve složce
`System/Processors/<název>/` na flashce (na Raspberry Pi na jeho datovém oddílu, ve Windows ve složce s daty);
nainstalujete ho tak, že tam rozbalíte jeho složku, a příští skenování ho spustí.

**Unzip je součástí AutoBleemu.** Rozbaluje zazipované hry pro PS1 v `Games/` dřív, než je skenování přečte,
a zazipované ROMy po jedné; arkádové sady zůstanou zazipované, protože tak je arkádová jádra čtou. Aktualizace
AutoBleemu aktualizuje i Unzip, a pokud jste ho vypnuli, zůstane vypnutý.

Procesor udělá svou práci jen jednou: jakmile se hrou skončí, nespustí se na ni znovu, dokud se hra nezmění.
Zatímco procesor pracuje, bublina vpravo nahoře ukazuje, co dělá, a varování nebo chyba se objeví na řádku pod
ní; podrobnosti najdete v `processors.log` ve složce s logy. Spuštění hry nebo RetroArch zastaví procesor, který
mění soubory, aby měla hra stroj jen pro sebe, a příští skenování práci dokončí.

Spravovat je můžete v systémové nabídce (**L2 + R2**) pod položkou *Procesory skenování*. Vidíte je v pořadí, ve
kterém běží, s jednou kartou pro hry z PS1 a druhou pro ROMy; L1 a R1 mezi kartami přepínají. Na pořadí záleží:
procesor, který rozbaluje, musí běžet dřív než ten, který rozbalené soubory upravuje.

| Tlačítko | V Procesorech skenování |
|---|---|
| Square | Vybraný procesor „zvedne“, takže ho Nahoru a Dolů přesunete na nové místo; Square ho zase položí. |
| Cross | Procesor vypne, nebo zase zapne. |
| Triangle | Při příštím skenování nechá procesor projít znovu všechny hry, i ty, se kterými už skončil. |
| Circle | Vrátí vás zpět, a pokud jste něco změnili, spustí skenování. |

Procesor, který vznikl pro jiný stroj, zůstane v seznamu zašedlý, abyste viděli, že tam je, ale že tady neběží.

![Procesory skenování](../images/en/processors.jpg)

Pokud si chcete napsat vlastní procesor, stránka Unzipu `https://github.com/autobleem2/proc_unzip` vysvětluje
všechno, co procesor musí dělat, a `tools/proc_check.py` ve zdrojovém kódu AutoBleemu ten váš zkontroluje, než
ho budete sdílet.

<!-- pagebreak -->

## 4. Obrazovky

### 4.1 Správce her

Ve Správci her si děláte pořádek v knihovně her pro PS1. Použijete ho, když chcete odstranit hru, kterou už
nehrajete, otevřít nastavení hry, aniž byste ji museli hledat na polici, nebo když chcete, aby si AutoBleem znovu
stáhl všechny obaly. Otevřete ho ze systémové nabídky (L2 + R2, *Správce her*). Během skenování je zašedlý
a počká, až skenování skončí.

Obrazovka má nadpis *Správce her - vybrat hru*. Vlevo vidíte všechny své hry z PS1 jako seznam názvů v abecedním
pořadí, vpravo obal vybrané hry s vydavatelem, rokem, sériovým číslem a složkou, ve které je. Vpravo nahoře je
vidět, kolik místa na jednotce zbývá, takže poznáte, kolik vám smazání vrátí. Nahoru a Dolů procházíte seznam,
L2 / R2 listují po stránkách a L1 / R1 skočí na první nebo poslední hru.

- **Cross** otevře vybranou hru v editoru hry - stejném, jaký otevírá ikona *Hra* na polici (oddíl 3.7). Když
  ho opustíte, jste zpátky na stejné hře v seznamu.
- **Square hru smaže.** AutoBleem se nejdřív zeptá a pak odstraní celou složku hry. Pokud uložené pozice
  a paměťovou kartu hry nepoužívá žádná jiná hra, položí ještě druhou otázku: jestli smazat i je. Odpovězte ne,
  pokud byste hru možná někdy chtěli zpátky i s uloženými pozicemi.
- **Triangle smaže všechny obrázky obalů** (PNG nebo JPEG), které leží vedle vašich her, a to po dotazu. Hodí se
  to, když jste nasbírali obaly, které se vám nelíbí: příští skenování vezme obaly znovu z databází obalů.

Na konci seznamu, za hrami, můžete vidět složky označené *Nepřidáno*. To jsou složky v `Games`, které skenování
prošlo, ale nedokázalo z nich udělat hru. Když jednu vyberete, pravá strana vám řekne, kde je a proč nebyla
přidaná - třeba chybí soubor cue (kapitola 7). Square takovou složku po dotazu smaže. Když po nějaké změně
odejdete tlačítkem Circle, AutoBleem hry znovu naskenuje.

![Správce her: seznam her vlevo, obal a podrobnosti vybrané hry vpravo](../images/en/game-manager.jpg)

### 4.2 Informace o hardwaru

Na stránku Informace o hardwaru se podíváte, když chcete vědět, co je váš stroj zač a co vidí: kolik místa
zbývá na flashce, jakou má síťovou adresu, jaké ovladače displeje a zvuku používá a které herní ovladače jsou
připojené. Na všech platformách je to stejná stránka, konzoli nevyjímaje. Otevřete ji ze systémové nabídky
(L2 + R2, *Informace o hardwaru*); Circle vás vrátí do systémové nabídky.

Stránka ukazuje systém, hardware, úložiště s volným místem, síťové adresy, ovladače displeje a zvuku a připojené
herní ovladače. Každou sekundu všechno načte znovu, takže ji můžete nechat otevřenou, zapojit ovladač nebo kabel
a sledovat, jak se změna objeví. Jen ukazuje - síť nebo ovladač nastavíte v *Síť a ovladače* (PSC-Bios,
kapitola 6).

Část s ovladači odpovídá na otázku „který ovladač je který hráč?“. První dva ovladače se ukazují jako *Hráč 1*
a *Hráč 2* - porty, které jim přidělí emulátor PS1. Každý další ovladač se ukazuje jako *nepoužívá jej PS1
emulátor*. RetroArch přiděluje porty podle vlastního nastavení, takže ve hře v RetroArch může být pořadí jiné.
Tuhle stránku nemusíte otevírat pokaždé: kdykoli ovladač zapojíte nebo odpojíte, spouštěč krátce ukáže, který
ovladač je teď hráč 1 a který hráč 2.

![Informace o hardwaru: údaje o stroji a připojené ovladače](../images/en/hardware-info.jpg)

### 4.3 Průvodce tlačítky

Když zapomenete, co někde dělá které tlačítko, stiskněte na polici **Triangle**. Průvodce tlačítky ukáže všechna
tlačítka všech obrazovek na jedné stránce, takže si je najdete, aniž byste spouštěč opustili. Pokud je připojená
USB klávesnice, nebo byla použita, ukazuje sloupec *Klávesnice* vedle každého tlačítka ovladače odpovídající
klávesu.

Průvodce vám také připomene jedinou věc, kterou se vyplatí pamatovat u každé hry: jak z ní odejít. Podržením
Select + Start, nebo Home, na 2 sekundy se vrátíte do AutoBleemu; krátký stisk místo toho otevře nabídku
emulátoru.

![Průvodce tlačítky: tlačítka všech obrazovek a vedle nich klávesy klávesnice](../images/en/button-guide.jpg)

### 4.4 Klávesnice na obrazovce

Kdykoli po vás AutoBleem chce něco napsat - název sady paměťových karet, název hry, heslo k WiFi, adresu zdroje
v Obchodě - objeví se stejná klávesnice na obrazovce, takže píšete jen ovladačem. Je rozvržená jako klávesnice
v telefonu. Kromě písmen má stránku se symboly, s `/ \ : ? & = % @ #` a vším ostatním, co adresa nebo heslo
potřebuje, a dvě stránky písmen s diakritikou. Ve spodní řadě jsou Shift, klávesa pro změnu stránky, mezerník,
Backspace a potvrzení.

Po klávesách se pohybujete směry a **Cross** napíše tu pod kurzorem. **Triangle** smaže písmeno a **Square**
napíše mezeru. **L1** je Shift; dvojím stiskem zapnete velká písmena natrvalo. **R1** přejde na další stránku
kláves a **L2 / R2** posouvají kurzor v textu. **Start** napsané potvrdí a **Circle** zruší. Pokud je připojená
USB klávesnice, můžete kdykoli psát místo toho na ní: Enter potvrdí a Esc zruší.

![Klávesnice na obrazovce](../images/en/keyboard.jpg)

### 4.5 Virtuální gamepad

Aplikace - programy v sadě Aplikace, jako Doom nebo Quake - nečtou váš ovladač samy. Malý pomocný program,
démon virtuálního gamepadu, čte skutečné ovladače a každé aplikaci předá ovladač, kterému rozumí. Tahle stránka
vám ukáže, které ovladače pomocník vidí a jak je čte. Podívejte se sem, když aplikace na váš ovladač nereaguje,
nebo má přeházená tlačítka. Otevřete ji ze systémové nabídky (L2 + R2, *Virtuální gamepad*); Circle vás vrátí do
systémové nabídky.

Pod nadpisem *Ovladače viditelné pro démona* je každý ovladač uvedený s číslem a názvem. Vedle něj se dočtete tři
věci: jestli ho pomocník dokázal otevřít (*připojeno*), nebo ne (*nečitelné*); ovladač systému, přes který
ovladač přišel; a odkud pochází rozložení jeho tlačítek - *z databáze ovladačů* znamená, že je ovladač známý
a tlačítka má tam, kde mají být, *odhadnuto démonem* znamená, že známý není a pomocník jeho rozložení odhadl, jak
nejlépe uměl. Pokud se vám tlačítka v aplikaci zdají špatně, nejspíš za to může odhadnuté rozložení.

Pomocník běží jen tehdy, když běží aplikace, takže se ho stránka zeptá jednou při otevření. Pokud během otevřené
stránky zapojíte ovladač, stiskněte **Cross** (*Zkontrolovat znovu*) a stránka se zeptá znovu. Ve Windows žádný
takový pomocník není a stránka hlásí *Není v tomto sestavení*.

![Virtuální gamepad: ovladače, které vidí pomocník aplikací](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. Na PC

### 5.1 UpdateRoms - obnovení flashky pro konzoli

Na Raspberry Pi, PC nebo ve Windows roztřídí skenování spouštěče vaše hry pro RetroArch do seznamů a stáhne
jejich obaly samo. PlayStation Classic to nezvládne, protože nemá vlastní síť. **UpdateRoms** tuhle práci udělá
místo něj na vašem PC s Windows: použije síť počítače, ale všechno zapíše s cestami, které čeká konzole, takže
když flashku vrátíte, konzole naběhne a všechno najde na svém místě. Spusťte ho pokaždé, když na flashku pro
konzoli přidáte nebo z ní odeberete hry pro RetroArch.

1. Nakopírujte ROMy na flashku do `RetroArch/roms/<systém>/` (oddíl 3.10). Názvy složek musí odpovídat názvům
   v databázích RetroArch; ty běžné už vytvořil instalátor.
2. Spusťte **`UpdateRoms\UpdateRoms.exe` z flashky** - dal ho tam instalátor. Sám pozná, na které flashce je.
   Během práce vidíte řádek s tím, co právě dělá, ukazatel průběhu a záznam.
   - Pokud na flashce ještě není databáze RetroArch, nejdřív stáhne balík databází RetroArch. Pak podle něj
     rozpozná každý ROM, takže hra, kterou databáze zná, dostane správný název.
   - Pro každý systém zapíše jeden playlist do `RetroArch/bin/playlists/`, s cestami konzole. Cokoli, co do
     těch seznamů přidal sám RetroArch, zůstane.
   - Ke každému ROMu bez obalu stáhne obal ze serverů náhledů libretro do `RetroArch/bin/thumbnails/`.
3. Flashku bezpečně odeberte a vraťte do konzole. Karta RetroArch ve výběru sady teď uvádí každý systém, který
   má hry.

Spouštět ho můžete, jak často chcete: složka, ve které se nic nezměnilo, se přeskočí, takže druhý běh je rychlý.
Když se něco pokazí, log najdete na flashce v `System/Logs/updateroms.log`. Stejně tak lze obnovit kartu
Raspberry Pi ve čtečce karet, příkazem `UpdateRoms.exe <jednotka> --target rpi`, i když Pi to se sítí zvládne
samo.

### 5.2 LAN Share - vaše hry a disky na serveru ve vaší síti

Obchod umí instalovat hry ze serveru ve vaší domácí síti (oddíl 3.13). **LAN Share** je program pro Windows,
který takový server naplní z vašeho PC: nahraje na něj hry pro PS1, které máte v počítači, a umí také přečíst
disk PS1 v mechanice CD/DVD počítače a nahrát ho tam taky. Serverem je `abstored` běžící na Raspberry Pi, NAS
nebo jiném PC. Jakmile je hra na něm, Obchod na konzoli, Pi nebo PC ji odtud může nainstalovat.

`LanShare.exe` získáte na stránce Obchodu, na kartě **LAN server**. Nic se neinstaluje: spustíte ho a nastavení
si ukládá do `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![Okno LAN Share: hry na serveru vlevo, hry na tomto PC vpravo](../images/en/lanshare.jpg)

1. **Připojte se k serveru.** Zadejte jeho adresu tak, jak ji má Obchod, `http://<jeho adresa>:<port>`,
   a stiskněte **Connect**. Vlevo se objeví hry, které už na serveru jsou, a případné problémy, které našlo jeho
   vlastní skenování. Aby mohl LAN Share na server hry nahrávat, potřebuje jednu ze dvou cest dovnitř:
   - **Share** je složka s hrami serveru sdílená ve vaší síti (Samba), například `\\raspberrypi\games`. LAN Share
     do ní hry zkopíruje a požádá server o skenování; server sám svou složku stále jen čte.
   - **Token** je pro server spuštěný s `--allow-uploads`. Zadejte jeho token - server ho vypíše při startu
     a uchovává ho v `<state>/upload-token`. LAN Share pak nahrává přes HTTP a nahrávání, které se v půlce
     zastaví, pokračuje tam, kde skončilo.
2. **Zveřejněte hry ze svého PC.** Vyberte složku, ve které hry máte (každá hra ve vlastní složce), zaškrtněte
   ty, které chcete, a stiskněte **Publish the ticked games**. Sloupec **On the server** vám řekne, jestli už
   server hru má - porovnává sériové číslo, nebo název, když sériové číslo chybí - a hru, kterou server má,
   nikdy nepošle dvakrát. **Tick those not on the server** za vás zaškrtne všechny ostatní.
3. **Zveřejněte disk.** Vložte disk PS1 do mechaniky počítače a stiskněte **Read a disc and publish it**. LAN
   Share přečte celý disk do `.bin` + `.cue` pojmenovaných podle názvu hry. U hry s LibCrypt zapíše i soubor
   `.sbi`, pokud mechanika umí číst subkanál. Pokud jste vybrali databáze (níže), porovná kopii se známým
   správným obrazem. Pak hru zveřejní. U hry na více discích nejdřív zaškrtněte **The game has more than one
   disc**: LAN Share si postupně řekne o každý další disk a zveřejní je dohromady jako jednu hru.
4. **Odeberte hry ze serveru.** Vyberte je a stiskněte **Remove from the server...**. Nic se nesmaže: každá hra
   se přesune do složky `.removed` vedle her serveru a když ji přesunete zpátky, je zase na místě.

**Databases** jsou volitelné. Když LAN Share nasměrujete na složku s obaly AutoBleemu (`coversU/P/J.db`)
a na soubor `Sony - PlayStation.rdb` z RetroArch, použije je k pojmenování her a ke kontrole přečteného disku.

Pokud nechcete nic kopírovat, zaškrtněte **Also share the games on this PC with the Store** (standardně je
vypnuté): LAN Share pak bude Obchodu nabízet složku s hrami na vašem PC přímo. Když to uděláte poprvé, Windows se
zeptají na bránu firewall - povolte jen soukromé sítě.

<!-- pagebreak -->

## 6. Nástroje pro konzoli (PlayStation Classic)

S flashkou pro PlayStation Classic přicházejí dva nástroje, které vám pomůžou nastavit konzoli nad rámec toho,
co umí sama od výroby. Oba vypadají jako zbytek spouštěče, v jeho tématu a jazyce, a ovládáte je ovladačem -
v průvodci mapováním ovladače i předními tlačítky konzole. **PSC-Bios** je rozšíření, které přichází s balíčkem
pro konzoli: otevře ho položka *Síť a ovladače* v Rychlé nabídce i v systémové nabídce a najdete ho také
v seznamu Rozšíření. **ABFlashKit** je aplikace v sadě Aplikace.

### 6.1 PSC-Bios

V PSC-Bios propojíte stroj se světem: se sítí WiFi, časovým pásmem, ovladači přes Bluetooth a s rozložením
tlačítek ovladače, který AutoBleem nezná. Přichází s balíčkem pro konzoli a je k dispozici i na Raspberry Pi
a flashce pro PC. Otevřete ho položkou *Síť a ovladače* v systémové nabídce (nebo v Rychlé nabídce), nebo ze
seznamu Rozšíření. Pokud je rozšíření nainstalované, ale vypnuté, položka *Síť a ovladače* je zašedlá a hlásí,
že *je vypnuto - zapněte jej v Rozšířeních*; stiskněte na ní Cross a otevře se seznam Rozšíření na PSC-Bios,
abyste ho mohli znovu zapnout.

První obrazovka vám dá přehled: čas a časové pásmo, síťové adaptéry (WiFi, Ethernet, Bluetooth) s adresami
a každý připojený ovladač s poznámkou, jestli má mapování tlačítek. Na konzoli potřebují síť a Bluetooth jádro
AutoBleem (oddíl 6.2); na Raspberry Pi nebo flashce pro PC používají vlastní nástroje systému. Průvodce
mapováním ovladače funguje všude.

![PSC-Bios: rozcestník Network & Controllers](../images/en/pscbios-main.jpg)

Z první obrazovky vás do každé části dovede jedno tlačítko:

| Tlačítko | Co otevře |
|---|---|
| Select | **Wi-Fi Network** vás připojí k WiFi (přes jádro, na Pi nebo PC přes NetworkManager): napište název sítě nebo ji vyberte z vyhledaných, zadejte heslo, zvolte režim ovladače a stiskněte *Apply / Restart Network*. Tady nastavíte i časové pásmo a po připojení uvidíte IP adresu konzole. |
| Square | **Bluetooth Controllers** hledá ovladače přes Bluetooth, například DualShock 4, abyste mohli spárovat nový nebo odebrat ten, který už nepoužíváte. |
| L1 | **DualShock 3 Pairing** připojí váš první DualShock 3, který k tomu musí být zapojený přes USB, pomocí pluginu sixaxis v jádře. |
| R1 | **Controller Mapping** otevře průvodce mapováním ovladače, popsaný níže. |
| Triangle | **About** ukáže, co je PSC-Bios zač. |
| Circle | **Back** vás vyvede z PSC-Bios zpátky do spouštěče. |

**Průvodce mapováním ovladače.** Použijte ho, když ovladač v AutoBleemu nic nedělá, nebo má tlačítka na
špatných místech. Ukáže připojený ovladač takový, jaký skutečně je - každou osu, tlačítko a hat jako čísla -
a obrázek DualShocku, který se při stisku rozsvěcuje. Protože se na ovladač, který zkoušíte, zatím nedá
spolehnout, ovládáte průvodce **předními tlačítky** konzole: **RESET** přepne na další ovladač, **OPEN** spustí
mapování a **POWER** ruší nebo odchází. Během mapování se průvodce ptá na jedno tlačítko za druhým: stiskněte
tlačítko, které svítí na obrázku, nebo OPEN, pokud takové tlačítko váš ovladač nemá. Krátký stisk se namapuje
jako obvykle.

Odejít můžete i z ovladače: podržte 2 sekundy Circle - naplní se pruh a zápatí hlásí *Hold 2 s: Exit*. Dokud
ovladač nemá žádné mapování, stejně funguje podržení libovolného tlačítka na 2 sekundy (*Hold any button 2 s:
Exit*). Na klávesnici zastupují POWER, RESET a OPEN klávesy Esc, mezerník a Enter.

Na konci se nové mapování začne používat, abyste ho mohli vyzkoušet, a OPEN ho uloží pod názvem, který si
zvolíte. Od té doby ho spouštěč načte pokaždé.

![PSC-Bios: průvodce mapováním ovladače](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - jádro AutoBleem

Jádro AutoBleem nahrazuje původní linuxové jádro konzole a je volitelné. Budete ho chtít, pokud od konzole
čekáte víc: dá jí fungující hodiny, rozchodí USB adaptéry WiFi a Bluetooth (pro PSC-Bios a ovladače přes
Bluetooth) a přidá podporu předních tlačítek, kterou emulátor používá pro body obnovení. ABFlashKit je nástroj,
který ho nainstaluje. Nejdřív konzoli zazálohuje a umí ji také vrátit do továrního stavu přes vlastní obnovu
od Sony.

> **Tento nástroj zapisuje do flash paměti konzole.** Pokud se zápis přeruší - vypadne proud nebo vytáhnete
> flashku -, konzole už nemusí naběhnout, a instalace vlastního jádra ruší záruku. Nechte konzoli zapojenou
> a flashku v ní, dokud se konzole sama nerestartuje. ABFlashKit se otevře právě tímto varováním: *I understand*
> pokračuje, *Quit* odejde.

![Nabídka ABFlashKit](../images/en/abflashkit-menu.jpg)

ABFlashKit umí tři věci:

- **Flash Kernel** nainstaluje jádro. Pokud na flashce ještě není záloha pro obnovu, nejdřív zazálohuje oddíly
  konzole (`LBOOT.EPB`). Zkontroluje zálohu i obraz jádra, zapíše jádro a systémové soubory AutoBleemu
  a restartuje konzoli. Když napíše *All done - when the screen goes black replace power cord*, počkejte, až
  obrazovka zčerná, pak napájecí kabel konzole vytáhněte a zase zastrčte.
- **Full backup** uloží všechny čtyři oddíly konzole do `LBOOT.EPB`, abyste je mohli později obnovit. Pokud už
  záloha existuje, zeptá se, než ji přepíše.
- **Restore Mode** je cesta zpátky k továrnímu firmwaru. Zkontroluje, že záloha na flashce je tovární, nastaví
  příznak obnovy a restartuje se do obnovy od Sony, která konzoli obnoví z `LBOOT.EPB`.

Pod každým krokem ukazatel průběhu ukazuje, jak daleko je. ABFlashKit nebude flashovat konzoli, na které běží
jiný vlastní firmware, například BleemSync nebo Project Eris: takovou konzoli nejdřív vraťte do továrního stavu.

**Přihlášení z PC.** Pokud znáte Linux a chcete se podívat do konzole, můžete se do ní přihlásit z PC přes USB
kabel. Vyžaduje to jádro AutoBleem; na konzoli v továrním stavu to nefunguje.

1. Propojte port micro-USB konzole s PC kabelem USB. PC uvidí konzoli jako nový síťový adaptér a adresu konzole
   najdete v nastavení toho adaptéru v počítači.
2. Přihlaste se příkazem `ssh root@<adresa konzole>`. Výchozí heslo je `autobleem`.

Místo hesla můžete použít klíč. Svůj veřejný klíč dejte na flashce do souboru `System/ssh/authorized_keys`
a konzoli restartujte: při dalším startu se přidá k účtu root. Aktualizace ani přeinstalování spouštěče ho
neodstraní.

> **Výchozí heslo je na každé konzoli stejné**, takže kdokoli, kdo do té vaší zapojí kabel, se může přihlásit
> jako root. Kde to jde, používejte klíč, a konzoli s výchozím heslem nenechávejte tam, kam se dostanou ostatní.

<!-- pagebreak -->

## 7. Když něco nefunguje

Většina problémů má jednoduchou příčinu. Každý z nich níže začíná tím, co vidíte, pak vysvětlí, proč se to
děje, a nakonec, co dělat. Pokud budete potřebovat pomoc, logy jsou první, na co se vás kdokoli zeptá, a proto
jsou na řadě jako první.

**Kde najdete logy.** AutoBleem si za běhu drží logy v paměti, aby na flashku nezapisoval pořád. Do `System/Logs/`
na flashce, kartě nebo ve složce s daty se dostanou, jen když se něco pokazí: když spadne spouštěč, hra z PS1
nebo RetroArch, logy se uloží do `System/Logs/crash-<n>/` (uchovávají se poslední tři pády) a spouštěč vám to
po návratu jednou oznámí. Pokud se pídíte po problému, který není pád, uchovávejte všechny logy: zapněte Možnosti
→ *Diagnostika* → *Uchovávat logy na flashce:* (projeví se od dalšího startu), nebo z PC vytvořte prázdný soubor
`System/Logs/keep`. *Informace o hardwaru* (oddíl 4.2) také ukazují, kde logy jsou, a Square tam uloží ty
aktuální do `System/Logs/saved-<n>/`.

Najdete tyto soubory:

| Soubor | Co z něj vyčtete |
|---|---|
| `autobleem.log` | Co dělal samotný spouštěč. |
| `launch.log`, `pcsx.log` | Jak se hra z PS1 spustila a co emulátor hlásil za běhu. |
| `retroarch.log` | Co hlásil RetroArch za běhu. |
| `update.log` | Jak proběhla aktualizace přes internet; na flashce se uchovává vždy. |
| `updateroms.log` | Jak na PC proběhl UpdateRoms (kapitola 5); na flashce se uchovává vždy. |

**Obrázek vás žádá o vložení flashky, nebo konzole usnula.** AutoBleem nemůže najít svou flashku: buď v konzoli
při startu nebyla, nebo ji někdo vytáhl. Zasuňte ji do kteréhokoli USB portu (nejlépe do předního, oddíl 2.1),
než uběhne 5 minut, nebo stiskněte Power. Pokud flashka nebyla odpojená správně, AutoBleem ji nejdřív
zkontroluje - počkejte, až ukazatel průběhu doběhne.

**RetroArch hlásí, že *needs a newer system library than this console has*.** Tenhle RetroArch vznikl pro
novější systém, než má konzole, a proto na ní běžet nemůže. Použijte RetroArch, který přichází s AutoBleemem.

**Hra hlásí, že *is protected by its PSN license and cannot be started*.** Hry koupené v PlayStation Network
jsou vázané na licenci a AutoBleem je spustit neumí. Tady není co opravit.

**Hra není na polici.** Obvykle její složka není uspořádaná tak, jak skenování čeká. Zkontrolujte, že každá
hra má vlastní složku a je v jednom z formátů z oddílu 3.10. *Správce her* (oddíl 4.1) uvádí za hrami složky,
které skenování odmítlo, označené *Nepřidáno*, a u každé řekne proč; Square takovou složku smaže. Až složku
opravíte, *Znovu skenovat hry* v systémové nabídce spustí skenování znovu.

**Hry nemají obaly.** Buď nebyly nainstalované databáze obalů - spusťte instalátor znovu a zaškrtněte je -, nebo
u her pro RetroArch na konzoli ještě neproběhl UpdateRoms na PC (kapitola 5).

**Ovladač nic nedělá, nebo má přeházená tlačítka.** AutoBleem rozložení toho ovladače nezná. Na konzoli ho
namapujte průvodcem mapováním ovladače v PSC-Bios (oddíl 6.1). Na Pi nebo PC ukazuje stránka Informace
o hardwaru (oddíl 4.2), co systém z ovladače vidí, a pomůže vám poznat, jestli ho vůbec rozpoznal.

**Po hře na konzoli zůstane obrazovka černá.** Obraz spouštěče se po skončení hry nevrátil. AutoBleem své okno
sám obnoví, až třikrát. Pokud obrazovka zůstane černá i potom, podržte tlačítko Power a konzoli znovu zapněte.

**Na Raspberry Pi** se v případě potřeby dostanete za spouštěč: `Alt+F2` vám dá přihlašovací výzvu na druhé
konzoli a SSH je zapnuté od prvního spuštění. `sudo journalctl -u autobleem` ukáže, co dělala služba spouštěče,
a `sudo systemctl restart autobleem` ji restartuje. Pokud se první spuštění nedokončilo, protože nebyla síť,
zkusí to znovu při dalším startu.

**Ve Windows** spouštěč opustíte klávesou `Esc`. Vaše složka s daty je ta, kterou jste zvolili při instalaci
(`Documents\AutoBleem`, pokud jste ji nezměnili), a logy jsou v její složce `System\Logs`.

**Konzole se po aktualizaci přes internet pořád dokola restartuje (flashka naformátovaná jako ext4).** Někdo si
flashku naformátuje jako ext4, linuxový souborový systém, místo FAT32 nebo exFAT. Až do příštího vydání
AutoBleemu rozbalí aktualizace přes internet na takové flashce každý soubor bez oprávnění, které mu dovoluje běžet
jako program. AutoBleem se pak nemůže spustit a konzole se restartuje pořád dokola. Flashek s FAT32 a exFAT se to
netýká. Opravit to jde dvěma způsoby.

**Oprava A** potřebuje PC s Linuxem. Zapojte flashku a vraťte programům AutoBleemu možnost běžet. Místo
`/media/USER/STICK` dosaďte vlastní cestu, kam je flashka připojená; poslední řádek potřebujete, jen pokud máte
nainstalovaný RetroArch:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Oprava B**: nainstalujte na flashku znovu nejnovější vydání AutoBleemu, jak popisuje oddíl 2.1. Instalátor
potřebuje PC, které flashku přečte. Pokud tu vaši nepřečte, je třeba ji nejdřív naformátovat, a tím se z ní
všechno smaže - předtím si z ní hry zkopírujte.

> Abyste se tomu vyhnuli, používejte **FAT32** (konzole v továrním stavu čte jen FAT32; exFAT potřebuje jádro
> AutoBleem, kapitola 6). Příští vydání oprávnění zachová a AutoBleem je při každém startu opraví.

AutoBleem je svobodný software (GNU GPL v3 nebo novější) a nepřichází s žádnou zárukou. Pro podporu a novinky se
připojte na server Discord, na který odkazuje obrazovka O programu, nebo navštivte https://autobleem.retromenele.pl/.
