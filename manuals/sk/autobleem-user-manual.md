# Používateľská príručka AutoBleem 2

AutoBleem 2 je spúšťač hier pre **PlayStation Classic** a od druhej verzie aj pre **Raspberry Pi**, **PC
spustené z USB kľúča** a **Windows**. Vaše hry z PS1 vám ukáže ako policu s obalmi, pri každej hre s obrázkom
krabice a podrobnosťami, spustí ich v pribalenom emulátore PCSX, a ak k nemu nainštalujete RetroArch, zahráte si
aj hry z iných systémov. Príručka vás prevedie inštaláciou na každej platforme, bežným používaním aj nástrojmi,
ktoré k AutoBleemu patria.

> Všetko na stiahnutie nájdete na **https://autobleem.retromenele.pl/**. Stránka je rozdelená podľa platforiem:
> v paneli *Install* pri každej z nich je to, čo si stiahnete vy; *Build inputs* pod ním sú súbory, ktoré si
> inštalátory stiahnu samy.

## 1. Čo dostanete

S AutoBleemom sa z PlayStation Classic - alebo z Raspberry Pi, starého PC či vášho počítača s Windows - stane
malá herná konzola s poriadnou ponukou pre vaše vlastné hry. Toto všetko v ňom nájdete:

- **Spúšťač.** Je to obrazovka, ktorú uvidíte hneď po zapnutí: polica s obalmi hier, po ktorej listujete, a vedľa
  vybranej hry jej podrobnosti. Odtiaľto hry spúšťate, triedite ich do sád (PlayStation, RetroArch, Aplikácie),
  meníte nastavenia, staráte sa o pamäťové karty a uložené pozície a sťahujete aplikácie a hry z Obchodu. Na
  všetkých platformách vyzerá aj funguje rovnako.
- **Dva emulátory PS1.** `pcsx-abnxt` je ten súčasný a predvolený, `pcsx-ab` je klasický emulátor, s ktorým
  AutoBleem prichádza odjakživa. Vyberáte medzi nimi v Možnostiach. Oba používajú tie isté nastavenia aj pamäťové
  karty, takže ich môžete kedykoľvek vymeniť a o nič neprídete.
- **RetroArch**, ak chcete hrať aj hry z iných systémov - NES, SNES, Mega Drive, Game Boy, arkádové automaty a
  mnoho ďalších. Na žiadnej platforme nie je povinný. Nakopírujete svoje ROMky a AutoBleem ich roztriedi do
  zoznamov a každú hru spustí so správnym jadrom. V RetroArch si môžete zahrať aj hry z PlayStationu; jeho jadro
  *PlayStation 1* je v zozname jadier úplne hore (oddiel 3.9). Hry ako Doom bežia z vašich vlastných herných
  súborov v priečinku `Packages` (oddiel 3.10).
- **Nástroje pre konzolu.** *PSC-Bios* - v ponukách sa volá *Sieť a ovládače* - nastavuje WiFi, hodiny, ovládače
  cez Bluetooth a mapovanie tlačidiel, a to na konzole aj na Raspberry Pi a na PC kľúči. *ABFlashKit* inštaluje do
  PlayStation Classic jadro AutoBleem (kapitola 6).
- **UpdateRoms** pre Windows. PlayStation Classic nemá vlastnú sieť, a tak tento program pre PC obnoví zoznamy
  RetroArch a stiahne obaly pre kľúč konzoly, kým je zapojený v počítači.

![Spúšťač: polica s obalmi, podrobnosti vybranej hry a nápoveda tlačidiel](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Inštalácia

### 2.1 PlayStation Classic

AutoBleem beží celý z USB kľúča. Vo vnútri konzoly sa nič nemení: keď kľúč vytiahnete, konzola funguje presne tak
ako predtým. Potrebujete len PC s Windows, USB kľúč (USB 2.0, aspoň 8 GB) a samotnú konzolu.

Kľúč nemusí byť prázdny a **formátovať sa nebude**, kým o to sami nepožiadate. AutoBleem sa nainštaluje vedľa
všetkého, čo na ňom už je, a kľúč, ktorý už používate s AutoBleemom 1.0, rovno aktualizuje (pozri nižšie). Pre
konzolu v továrenskom stave musí byť kľúč naformátovaný ako **FAT32**, pretože pôvodné jadro konzoly exFAT
neprečíta. Keď nainštalujete jadro AutoBleem (ABFlashKit, kapitola 6), konzola nabehne aj z kľúča s exFAT a
zbavíte sa obmedzenia FAT32, ktoré nedovolí súbor väčší ako 4 GB.

1. Z panela PlayStation Classic na webe si stiahnite **AutoBleemInstaller-<verzia>.zip** a rozbaľte ho
   kamkoľvek. Vnútri je `AutoBleemInstaller.exe` a jeho README. Samotný AutoBleem sa sťahuje až počas
   inštalácie, takže počítač potrebuje pripojenie na internet.
2. Zapojte kľúč a spustite `AutoBleemInstaller.exe`. Vyberte **kanál** - *Release* je odskúšaná verzia a pre
   väčšinu ľudí tá správna voľba, *Testing* je nasledujúca verzia v čase, keď sa testuje, a *Nightly* je
   najčerstvejšie vývojové zostavenie, ktoré nemusí fungovať - a potom jednotku kľúča. Riadok pod tým vám
   povie, akú verziu AutoBleemu sa chystáte nainštalovať a čo je na kľúči teraz: buď *a fresh install*
   (ostatných súborov na kľúči sa inštalácia nedotkne), alebo *AutoBleem <verzia> is on this stick: it will be
   updated* (hry, uložené pozície, pamäťové karty aj nastavenia zostanú).
   **Formátovať nemusíte.** Tlačidlo **Format** vedľa jednotky je len pre úplne nový kľúč bez súborového
   systému, pre kľúč, ktorý konzola neprečíta (napríklad s NTFS), alebo pre taký, ktorý chcete vymazať do čista.
   Najprv sa opýta a potom z kľúča zmaže úplne všetko. Ak konzola ešte nemá jadro AutoBleem, zvoľte tam FAT32.
   Potom zaškrtnite, čo chcete nainštalovať:
   - **Cover databases** - obaly a popisy celej knižnice hier pre PS1, aby si vaše hry našli obaly samy
     (predvolene zaškrtnuté; zhruba 300 MB).
   - **RetroArch** - RetroArch s jadrami, doplnkovými aplikáciami (Doom, Quake, Amiga, ...) a grafikou
     z libretro, pre hry z iných systémov. Predvolene vypnuté; doinštalovať ho môžete kedykoľvek neskôr ďalším
     spustením inštalátora.
   - **BIOS files** - súbory BIOS, bez ktorých sa niektoré jadrá RetroArch nespustia (len spolu s RetroArch).
   - **Sample games** - pár voľne šíriteľných homebrew hier, aby polica pri prvom spustení nezívala prázdnotou.
3. Stlačte **Install** a počkajte. Ukazovatele priebehu a záznam ukazujú každý krok. Na konci sa kľúč premenuje
   na `SONY` a dostane kópiu programu `UpdateRoms` (pozri kapitolu 5).
4. Kľúč bezpečne odoberte, zapojte ho do **druhého predného USB portu** konzoly (toho pravého, pre hráča 2) -
   prvý zostane voľný pre ovládač - a konzolu zapnite. Namiesto pôvodnej ponuky nabehne AutoBleem. Druhý
   ovládač pripojíte cez USB hub v prednom porte, alebo použite ovládač cez Bluetooth.

**Zapínanie a vypínanie.** So zapojeným kľúčom konzola nabehne, pár sekúnd bliká kontrolkou, kým zaregistruje
AutoBleem, a ešte predtým, ako sa na obrazovke čokoľvek objaví, prejde do pohotovostného režimu. To je v poriadku:
AutoBleem štartuje cez vlastný aktualizačný mechanizmus konzoly a ten jednoducho funguje takto. Stlačte raz
**Power** a spúšťač sa objaví.

Keď v systémovej ponuke zvolíte *Vypnúť* alebo stlačíte na konzole tlačidlo Power, konzola prejde do
**pohotovostného režimu AutoBleemu**: AutoBleem najprv bezpečne odpojí kľúč a potom kontrolka zmení farbu na
**oranžovú** - to je znamenie, že všetko prebehlo, ako má. Ďalším stlačením Power sa spúšťač o pár sekúnd vráti.
**Kým svieti oranžovo, môžete kľúč vytiahnuť** a zapojiť do počítača; Windows ho nebudú chcieť kontrolovať, lebo
bol odpojený správne. Predtým, ako znova stlačíte Power, ho vráťte späť. Ak konzolu odpojíte zo zásuvky, pri
ďalšom zapnutí znova prejde štartovacím pohotovostným režimom. **Červená** kontrolka znamená, že konzola je
naozaj vypnutá.

**Port vzadu.** Port micro-USB vzadu je napájací konektor konzoly. S jadrom AutoBleem sa doň dá zapojiť aj USB
zariadenie, ale kľúč patrí do predného portu.

**Keď kľúč chýba.** Ak konzola nabehne bez kľúča, alebo kľúč vytiahnete počas behu AutoBleemu, objaví sa obrázok,
ktorý vás požiada, aby ste ho zasunuli - do ktoréhokoľvek USB portu. AutoBleem čaká 5 minút a potom konzolu
uspí; ak chcete, aby zaspala hneď, stlačte Power.

![Obrázok, ktorý žiada o vloženie kľúča](../images/en/insert-stick.jpg)

**Kedy sa kľúč kontroluje.** Ak kľúč nebol odpojený správne - vytiahli ste ho počas behu AutoBleemu alebo
vypadol prúd - AutoBleem ho pred ďalším použitím skontroluje, či na ňom nie sú chyby: pri štarte, po prebudení
alebo keď ho znova zapojíte. Ukazovateľ priebehu ukazuje, kam až sa kontrola dostala. Na veľkom kľúči môže chvíľu
trvať; nechajte ju dobehnúť a konzolu medzitým nevypínajte.

![Kontrola kľúča](../images/en/stick-check.jpg)

**Aktualizácia.** Kľúč aktualizujete tak, že naň znova pustíte inštalátor - tlačidlo teraz namiesto inštalácie
ponúka *Update*. Nainštaluje najnovšiu verziu zvoleného kanála; hry, uložené pozície, nastavenia aj obsah
RetroArch zostanú a vymenia sa len vlastné súbory AutoBleemu. Konzola s jadrom AutoBleem a s WiFi sa vie
aktualizovať aj sama (oddiel 3.12).

**Prechod z AutoBleemu 1.0 (alebo AutoBleem-NG).** Použijete ten istý inštalátor na tom istom kľúči, bez
formátovania:

1. Najprv si celý kľúč pre istotu skopírujte do počítača ako zálohu.
2. Zapojte ho, spustite `AutoBleemInstaller.exe` a vyberte kanál a jednotku. Tlačidlo Format **nestláčajte**.
3. Stlačte **Install**. Inštalátor prerobí staré usporiadanie na nové: RetroArch, ROMky a témy presťahuje tam,
   kde ich AutoBleem 2 čaká, a staré priečinky s ROMkami (`nes`, `snes`, ...) dostanú názvy systémov podľa
   RetroArch. Hry, uložené pozície, pamäťové karty, ROMky aj uložené hry z RetroArch zostanú, rovnako ako
   `config.ini` - iba emulátor PS1 sa v ňom prepne na pcsx-abnxt.
4. Vráťte kľúč do konzoly. Prvé skenovanie znova zostaví zoznam hier aj playlisty. Obaly pre hry z RetroArch
   získate, keď na PC spustíte UpdateRoms (kapitola 5).

> Konzola v továrenskom stave nemá hodiny ani sieť. Dátumy sa začnú zobrazovať až po inštalácii jadra AutoBleem
> (kapitola 6) a obaly hier pre RetroArch obstará UpdateRoms na PC (kapitola 5).

Hry z PS1 patria na kľúči do priečinka `Games`, každá do vlastného priečinka - ako presne, vysvetľuje oddiel 3.10.

### 2.2 Raspberry Pi

S AutoBleemom sa z Raspberry Pi stane malá konzola: nabehne rovno do spúšťača, bez akejkoľvek pracovnej plochy
medzi tým. Na webe sú dva hotové obrazy karty, 32-bitový a 64-bitový, a balík pre Raspberry Pi OS Lite, ktorý už
máte nainštalovaný.

| Model | 32-bitový obraz | 64-bitový obraz | Poznámky |
|---|---|---|---|
| Raspberry Pi 5 | áno | áno | |
| Raspberry Pi 4 Model B, Pi 400 | áno | áno | |
| Raspberry Pi 3 Model B / B+ / A+ | áno | áno | na spúšťač a PS1 bohato stačí |
| Raspberry Pi Zero 2 W | áno | áno | 512 MB RAM: PS1 pobeží, náročnejšie jadrá RetroArch nie |
| Raspberry Pi 2 Model B | áno | len v1.2 | na čokoľvek v 3D je pomalé |
| Raspberry Pi 1, Zero, Zero W | nie | nie | ARMv6 - nespustí sa ani jeden obraz |

**Na hry z PS1 si vezmite 32-bitový obraz.** Rýchly ARM rekompilátor klasického `pcsx-ab` existuje iba v 32-bitovej
verzii, takže v 64-bitovom zostavení bežia hry z PS1 pomalšie. 64-bitový obraz má zase viac jadier RetroArch;
siahnite poň, ak sú pre vás ostatné systémy dôležitejšie ako PS1.

**Pomocou Raspberry Pi Imager:**

1. Nainštalujte si Raspberry Pi Imager (raspberrypi.com/software). V *Choose OS* zvoľte *Use custom* a stiahnutý
   súbor `autobleem-<verzia>-rpi-armhf.img.xz` (32-bitový) alebo `-arm64.img.xz` (64-bitový) - prípadne
   v nastaveniach aplikácie pridajte URL repozitára a AutoBleem si vyberte zo zoznamu. Pre každý kanál je jedna:
   `https://autobleem.retromenele.pl/rpi-imager/os_list.json` pre najnovšie vydanie,
   `.../os_list-testing.json` pre zostavenie, ktoré sa práve testuje, a `.../os_list-nightly.json` pre najnovšie
   vývojové zostavenie. Na karte Raspberry Pi na stránke so stiahnutiami sú vypísané tie, ktoré existujú, každá
   s tlačidlom *Copy*.
2. Na obrazovke prispôsobenia v Imageri (ozubené koliesko alebo otázka po *Next*) nastavte **meno používateľa
   a heslo, sieť WiFi a krajinu a zapnite SSH**. Pri prvom štarte AutoBleem sieť potrebuje.
3. Zapíšte kartu, vložte ju do Pi, pripojte obrazovku a klávesnicu alebo ovládač a zapnite ho.

**Prvý štart** trvá 5 až 25 minút a na obrazovke vidíte, čo sa práve deje. Ak nie je k dispozícii sieť, opýta sa
na ňu: vyberte zo zoznamu svoju WiFi a zadajte heslo. Potom sa opýta, či má nainštalovať RetroArch - ak do minúty
neodpoviete, nainštaluje ho. Ďalej zväčší systémový oddiel, zo zvyšku karty urobí oddiel `AUTOBLEEM` pre vaše
hry, nainštaluje RetroArch s jadrami, balíky BIOS a ukážkové hry a reštartuje sa rovno do spúšťača.

Ak nechcete pri prvom štarte odpovedať na otázky, napíšte odpovede vopred do súboru **`autobleem.txt`** na
zavádzacom oddiele karty - otvoriť a upraviť ho dokáže ktorýkoľvek počítač:

| Kľúč | Predvolená hodnota | Význam |
|---|---|---|
| `root_gib` | 8 | Veľkosť systémového oddielu v GiB; zo zvyšku sa stane oddiel pre hry. |
| `hdmi_mode` | 1920x1080@60 | Režim obrazovky počas celého štartu (pre starší televízor `1280x720@60`). |
| `retroarch` | (opýta sa) | `yes` / `no` - RetroArch a ostatné systémy, alebo iba PS1. |
| `thumbnails` | none | `boxarts` stiahne celú sadu obalov, aby boli k dispozícii aj bez siete (~9000 súborov). |
| `bios`, `downloads`, `samples` | yes | Hodnota `no` vynechá balíky BIOS, všetko sťahovanie alebo ukážkové hry. |

**Na Raspberry Pi OS Lite, ktorý už máte** (Bookworm alebo Trixie): skopírujte do Pi `autobleem-rpi.tar.gz` (alebo
verziu arm64), rozbaľte ho a spustite `sudo bash install.sh`. Opýta sa na to isté, pri ďalšom štarte zmenší
systémový oddiel, aby uvoľnil miesto pre dátový oddiel (`--shrink-root <GiB>`), a spúšťač umiestni na prvú
konzolu.

Po inštalácii naplníte **oddiel `AUTOBLEEM`** na karte (exFAT) svojimi hrami: kartu vyberte a otvorte na
ktoromkoľvek PC, alebo kopírujte cez sieť (SSH je zapnuté). Hry z PS1 patria do `Games/`, ROMky iných systémov
do `RetroArch/roms/<systém>/`, BIOS z PS1 do `System/Bios/` (oddiel 3.11) a témy do `Themes/`.

### 2.3 USB kľúč pre PC

To isté pre akékoľvek PC, ktoré dokáže štartovať z USB: kľúč spustí počítač rovno do AutoBleemu a vlastného disku
PC sa nedotkne. Je to 32-bitový systém, takže si poradí aj so starými strojmi.

1. Zapíšte obraz na kľúč s kapacitou aspoň 8 GB. **Vo Windows** použite **AutoBleemFlasher** (panel PC na webe -
   rozbaľte ho a spustite `AutoBleemFlasher.exe`; vyžiada si práva správcu, pretože zapisuje celý disk):
   vyberte kanál a kľúč, stlačte *Write* a dvakrát potvrďte - obraz stiahne, overí, zapíše a ešte ho prečíta
   späť. Ponúka iba USB kľúče a SD karty, nikdy disk, z ktorého bežia Windows, a **všetko na vybranom kľúči sa
   zmaže**. V Linuxe alebo macOS si z panela PC stiahnite `autobleem-<verzia>-pcusb-i386.img.xz` a zapíšte ho
   príkazom `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (alebo cez balenaEtcher).
2. Spustite PC z kľúča (klávesom pre ponuku zavádzania - F12, F8, Esc...). Funguje štart cez BIOS aj UEFI;
   **Secure Boot musí byť vypnutý**.
3. Prvý štart prebieha ako na Pi: ak nie je zapojený kábel, opýta sa na sieť, opýta sa na RetroArch,
   nainštaluje všetko - s káblovou sieťou to trvá asi osem minút - a reštartuje sa do spúšťača.

Potom je na kľúči oddiel `AUTOBLEEM` pre vaše hry. Keď kľúč zapojíte do bežiaceho PC s Windows 10 (verzia 1903
alebo novšia), objaví sa ako druhá jednotka, na ktorú môžete kopírovať hry. Súbor `autobleem.txt` je na prvom
oddiele a má tie isté kľúče ako na Pi (okrem `hdmi_mode` - PC vždy používa vlastný režim obrazovky).

### 2.4 Windows

Ak chcete mať AutoBleem na svojom počítači s Windows, beží aj ako obyčajný program: na celej obrazovke, pričom
emulátory a RetroArch sa spúšťajú ako samostatné programy.

1. Stiahnite si **AutoBleemSetup-<verzia>.exe** a spustite ho. Inštaluje sa pre jedného používateľa, bez práv
   správcu: program do `%LOCALAPPDATA%\Programs\AutoBleem`, dáta (hry, nastavenia, témy, RetroArch) do priečinka,
   ktorý si zvolíte - predvolene `Documents\AutoBleem`.
2. Zaškrtnite súčasti - databázy obalov, RetroArch (oficiálne zostavenie pre Windows a jeho jadrá), súbory BIOS,
   ukážkové hry - a nechajte pomocníka inštalácie, aby ich stiahol.
3. AutoBleem spustite z ponuky Štart alebo z pracovnej plochy. Na PC slúži klávesnica ako ovládač (oddiel 3.2).

Pri aktualizácii spustite novší inštalátor cez existujúcu inštaláciu: program sa vymení a váš dátový priečinok
zostane, ako je. Spúšťač navyše raz denne skontroluje web a keď nájde novú verziu, ponúkne aktualizáciu (oddiel
3.12).

<!-- pagebreak -->

## 3. Používanie AutoBleemu

### 3.1 Spúšťač

V spúšťači si vyberáte, čo budete hrať. Hry vám ukáže ako policu s obalmi, tak ako by ste videli krabice na
skutočnej poličke, a vy po nej listujete, kým nenájdete tú, ktorú chcete. Všetko ostatné v AutoBleeme -
nastavenia, pamäťové karty, Obchod - sa otvára odtiaľto, a keď hru opustíte, vrátite sa sem.

Vybraná hra stojí uprostred police a pod ňou je jemný odraz. Vedľa nej v malej mriežke vidíte jej podrobnosti:
vydavateľa, rok, sériové číslo, región, pre koľko hráčov je a kedy ste ju naposledy hrali. Keď AutoBleem niektorý
z týchto údajov nepozná, riadok radšej vynechá, než aby ho nechal prázdny. Vedľa podrobností je tlačidlo na
spustenie. Hra, ktorá nemá obrázok obalu, sa zobrazí ako disk ležiaci v čiernom lôžku prázdnej krabičky, takže
aj ona má na polici svoje miesto.

Vzhľad spúšťača určuje jeho téma. Predvolená je **ab2.0.0**: prepne sa na ňu nová inštalácia aj aktualizácia,
ktorá ju prinesie, no iba raz - keď si potom vyberiete inú tému (oddiel 3.6), zostane vám.

**Lišta s nápovedou** v dolnej časti obrazovky vám hovorí, čo tlačidlá práve robia. Má dva riadky so štyrmi
miestami. Prvý riadok sa týka vybranej hry: spustiť ju, spustiť ju v RetroArch, otvoriť rad ikon pod ňou alebo
otvoriť Rýchlu ponuku. Druhý riadok sa nemení nikdy: Select vyberá sadu, Start vyberie náhodnú hru, Triangle
ukáže prehľad tlačidiel a L2 + R2 otvorí systémovú ponuku. Keď tlačidlo práve nemá čo robiť, jeho nápoveda
zošedne.

**Nové hry nájde sám.** Pri každom štarte spúšťač na pozadí prehľadá priečinok s hrami, takže hra, ktorú ste
nakopírovali, kým bol stroj vypnutý, sa objaví bez toho, aby ste čokoľvek robili. Počas skenovania ukazuje
bublina vpravo hore, ako ďaleko je, a nové hry pribúdajú na polici hneď, ako sa nájdu - medzitým môžete pokojne
listovať ďalej.

**Nová inštalácia** ešte nemá žiadne hry. Namiesto prázdnej police uvidíte uvítaciu kartu *Ahoj a vitaj
v AutoBleem!*, ktorá vám poradí, aby ste hry nahrali do `Games` a stlačili *Znova skenovať hry*. Pomenuje aj
miesto podľa vašej platformy: na kľúči (PlayStation Classic, PC kľúč), na SD karte (Raspberry Pi) alebo vo
vašom priečinku AutoBleem (Windows). Karta zmizne hneď, ako skenovanie nájde prvú hru.

**Oznámenia** sú bubliny vpravo hore. Informujú vás bez toho, aby zavadzali: o priebehu skenovania, o názve sady,
na ktorú ste práve prepli (*Zobrazujem: ...*), o ovládači so slabou batériou, o páde programu, o práci procesora
skenovania a o sťahovaní z Obchodu. Bublina sťahovania ukazuje rýchlosť a zostávajúci čas, napríklad
`1.4 MB/s · 0:42`. Ako dlho zostanú informačné bubliny na obrazovke, je na vás: Možnosti → *Doba zobrazenia
oznámenia:*.

**Batérie ovládačov.** Na konzole, Raspberry Pi a PC kľúči (nie vo Windows) sa každý bezdrôtový ovládač, ktorý
hlási stav batérie, zobrazí ako malá ikona s percentami na vlastnej doštičke; doštičky sa radia pod seba od
ľavého horného rohu. Ovládač, ktorý hrá za hráča 1 alebo hráča 2, má značku P1 alebo P2 podľa voľby *Vymeniť
hráča 1 / hráča 2* (oddiel 3.6); ovládač, ktorý nie je priradený žiadnemu hráčovi, alebo tretí ovládač značku
nemá. Keď batéria niektorého ovládača dochádza, upozorní vás na to raz oznámenie s menom ovládača a percentami.

**Značka kanála.** Ak používate zostavenie, ktoré nie je finálnym vydaním, pripomenie vám to malá značka pod
doštičkami batérií v ľavom hornom rohu. Je to štítok s kanálom a vedľa neho krátka verzia: `ALPHA`, `BETA` alebo
`RC` pre predbežné vydanie, `TESTING` pre akékoľvek iné predbežné vydanie, `NIGHTLY` pre nočné zostavenie a `DEV`
pre zostavenie vytvorené ručne (pri `DEV` je verziou commit, z ktorého vzniklo). Vydanie žiadnu značku nemá.

![Výber sady: tri karty a skupiny tej aktuálnej s počtom hier](../images/en/set-picker.jpg)

### 3.2 Ovládanie

AutoBleem je stavaný na ovládanie iba ovládačom a tlačidlá znamenajú na každej obrazovke to isté: Cross
potvrdzuje, Circle vracia späť, Triangle pomáha. Ak zabudnete, čo ktoré tlačidlo robí, povie vám to lišta
s nápovedou v dolnej časti obrazovky, a Triangle na polici otvorí prehľad tlačidiel so všetkými tlačidlami
všetkých obrazoviek (oddiel 4.3). Na polici robia tlačidlá toto:

| Tlačidlo | Na polici |
|---|---|
| Vľavo / Vpravo | Presunie sa na predchádzajúcu alebo nasledujúcu hru; keď tlačidlo podržíte, listuje ďalej. |
| L1 / R1 | Skočí na predchádzajúce alebo nasledujúce začiatočné písmeno názvov, takže sa dlhou policou dostanete rýchlo. Na prázdnej polici s pripojenou USB mechanikou otvorí R1 *Disk* (oddiel 3.9a). |
| Cross | Spustí vybranú hru: hru z PS1 v emulátore PS1, hru z RetroArch v jej jadre a aplikáciu po zobrazení jej popisu. |
| Square | Spustí vybranú hru z PS1 namiesto toho v RetroArch. Keď je vybraný disk v USB mechanike, disk namiesto toho skopíruje (*Kopírovať disk*, oddiel 3.9a). |
| Circle | Vráti vás do zobrazenia disku, keď je v mechanike disk (oddiel 3.9a). |
| Triangle | Otvorí prehľad tlačidiel. |
| Start | Vyberie náhodnú hru z aktuálnej sady - keď sa neviete rozhodnúť. |
| Select | Otvorí výber sady, kde si zvolíte, ktoré hry polica ukazuje (oddiel 3.3). |
| Hore | Otvorí Rýchlu ponuku (oddiel 3.4). |
| Dole | Otvorí rad ikon pod hrou (*NASTAVENIA*, *Hra*, *PAMÄŤOVÁ KARTA*, *OBNOVA*); tlačidlom Hore ho znova zatvoríte. |
| L2 + R2 | Otvorí systémovú ponuku (oddiel 3.5). |

**S klávesnicou.** Na PC bez ovládača, alebo s USB klávesnicou na konzole, Pi či PC kľúči, zastúpia tlačidlá
klávesy. Šípky sú smerový ovládač, Enter je Cross, Esc alebo Backspace je Circle, Tab je Triangle a medzerník je
Square. F1 a F2 sú Select a Start, Page Up a Page Down sú L1 a R1, Home a End sú L2 a R2 a F10 otvorí systémovú
ponuku.

Vo Windows fungujú niektoré klávesy inak. Esc tam zatvorí AutoBleem (kapitola 7), takže Circle je iba
Backspace, medzerník je Start a S je Square. Celý ovládač navyše zastúpia písmená, takže na šípky nemusíte
siahať: X, O, S a T sú Cross, Circle, Square a Triangle, I, J, K a L sú smerový kríž (hore, doľava, dole,
doprava), B je Select, Q a E sú L1 a R1 a 1 a 2 sú L2 a R2.

**V každom zozname a ponuke** platia tie isté pohyby: Hore a Dole posúvajú kurzor, L2 a R2 listujú po stranách,
L1 a R1 skočia na prvý alebo posledný riadok, Cross vyberá a Circle vracia späť. Tlačidlo Uložiť nikdy hľadať
nemusíte: obrazovka s nastaveniami ich uloží sama, keď z nej odídete cez Circle.

**Ako odísť z hry alebo aplikácie.** Podržte na 2 sekundy Start + Select alebo Home a ste späť v AutoBleeme.
Funguje to na každom ovládači - na pôvodnom z konzoly, na USB aj na Bluetooth ovládači. Krátke stlačenie tých
istých tlačidiel namiesto toho otvorí ponuku emulátora. Aplikácia takú ponuku nemá, takže v nej funguje iba dlhé
podržanie.

![Rad ikon pod vybranou hrou](../images/en/launcher-icons.jpg)

### 3.3 Sady

Veľká knižnica sa lepšie prechádza po častiach. Sady vám policu zúžia na jeden druh hier - iba obľúbené, iba hry
pre Super Nintendo, iba hry z jedného priečinka - aby ste nemuseli prechádzať stovky obalov, kým nájdete ten
pravý.

Stlačte **Select** a otvorí sa výber sady. Má tri karty, PlayStation, RetroArch a Aplikácie: L1 a R1 medzi nimi
prepínajú, Hore a Dole sa pohybujete po skupinách na karte (L2 a R2 po celých stranách) a Cross zobrazí vybranú
skupinu na polici. Circle (*Späť*) výber zatvorí bez akejkoľvek zmeny. Tieto klávesy ukazuje aj spodná lišta.
Pri každom riadku vidíte, koľko položiek obsahuje. Skupina, v ktorej nič nie je, sa otvorí na prázdnej polici,
kde rad ikon ponúka iba *NASTAVENIA*.

**Karta PlayStation.** Na PlayStation Classic začína skupinami *Všetky hry* a *Originálne hry* (dvadsať hier
zabudovaných v konzole), po nich nasledujú *USB hry* - všetko v `Games/` - a jedna skupina pre každý priečinok,
ktorý ste v ňom vytvorili, takže hra v podpriečinku patrí do skupiny daného priečinka. Potom prídu *Obľúbené hry*,
*História hry* a - keď aspoň jednu hru označíte ako hru pre svetelnú pištoľ - *Hry so svetelnou pištoľou*.
Raspberry Pi, PC kľúč a Windows zabudované hry nemajú, takže tam zoznam začína skupinou *USB hry*, ktorá obsahuje
celú vašu knižnicu.

**Karta RetroArch** je k dispozícii iba tam, kde je nainštalovaný RetroArch. Má jednu skupinu pre každý systém,
pre ktorý máte hry, a k tomu vlastné Obľúbené a Históriu RetroArch.

**Karta Aplikácie** triedi aplikácie podľa druhu: *Všetky aplikácie*, potom *Hry*, *Emulátory*, *Nástroje*,
*Médiá* a *Ostatné*. Do ktorej skupiny aplikácia patrí, určuje jej súbor `app.ini`. Na tejto karte sú aj
**PE aplikácie**, teda programy pre Windows, ktoré spúšťa PE runner; tá, ktorú konzola spustiť nevie, je
označená *nemožno spustiť na tejto konzole*. Tam, kde ho spúšťač zobrazuje, je v zozname aj riadok *Balíky*
(oddiel 3.10).

### 3.4 Rýchla ponuka

Rýchla ponuka je krátky zoznam vecí, po ktorých pri prehliadaní hier siahate najčastejšie, aby ste ich nemuseli
hľadať v celej systémovej ponuke. Otvoríte ju tlačidlom **Hore** na polici alebo **ikonou ozubeného kolieska**
v rade ikon (v tom, kde sú *NASTAVENIA*, *Hra*, *PAMÄŤOVÁ KARTA* a *OBNOVA*).

Hore a Dole sa pohybujete po položkách (z poslednej skočí kurzor dokola na prvú), Cross jednu vyberie a Circle
ponuku zatvorí. Riadok pod ponukou popisuje vybranú položku. Nájdete v nej:

- *Znova skenovať hry* hneď vyhľadá nové, zmenené alebo odstránené hry - hodí sa, keď ste práve nakopírovali hry
  a nechce sa vám čakať.
- *Obchod* otvorí AutoBleem Store, v ktorom si prezeráte a inštalujete hry, aplikácie a rozšírenia (oddiel
  3.13).
- *Jadrá RetroArch*, tam, kde je nainštalovaný RetroArch, vám dovolia vybrať jadro, ktoré hrá jednotlivé
  systémy.
- *Sieť a ovládače* otvorí obrazovky pre WiFi, párovanie cez Bluetooth a mapovanie ovládača (kapitola 6). Položka
  je tu iba vtedy, keď ich poskytuje niektoré nainštalované rozšírenie - PSC-Bios to robí na konzole, Raspberry
  Pi a PC kľúči. Ak je toto rozšírenie nainštalované, ale vypnuté, položka je sivá a jej popis vás vyzve, aby ste
  ho zapli v Rozšíreniach; Cross potom otvorí zoznam Rozšírení priamo na ňom.
- *Reštartovať launcher* zatvorí AutoBleem a znova ho spustí (iba na konzole, Raspberry Pi a PC kľúči).
- *Systémová ponuka...* otvorí celú systémovú ponuku so všetkým ostatným - Možnosťami, Správcom hier, vypnutím
  a ďalším (oddiel 3.5).

Všetko okrem Obchodu, jadier RetroArch a reštartu spúšťača nájdete aj v systémovej ponuke.

![Rýchla ponuka](../images/en/quick-menu.jpg)

### 3.5 Systémová ponuka

V systémovej ponuke je všetko, čo AutoBleem dokáže okrem samotného hrania: nastavenia, nástroje pre knižnicu
a pamäťové karty, informácie o stroji a vypnutie. Stlačte naraz **L2 + R2** (v ľubovoľnom poradí) a otvorí sa
nad policou. Položky sú zoskupené pod nadpismi *Knižnica*, *Systém* a *Odchod*, pričom dve najpoužívanejšie
sú úplne hore. Riadok v spodnej časti ponuky popisuje vybranú položku, takže sa môžete najprv porozhliadnuť a až
potom vybrať.

| Časť | Položka | Na čo slúži |
|---|---|---|
| (hore) | *Znova skenovať hry* | Hneď vyhľadá nové, zmenené alebo odstránené hry. Skenovanie sleduje priečinok aj samo, takže túto položku potrebujete, len keď nechcete čakať. |
| | *Rozšírenia* | Ukáže rozšírenia na kľúči, napríklad AutoBleem Store, aby ste ich mohli spustiť alebo vypnúť (oddiel 3.13). |
| *Knižnica* | *Správca hier* | Ukáže hry z PS1 ako zoznam s ich priečinkami; môžete v ňom hru zmazať alebo vyčistiť obaly (oddiel 4.1). Počas skenovania sa nedá otvoriť. |
| | *Pamäťové karty* | Správa vašich zdieľaných sád pamäťových kariet (oddiel 3.8). |
| | *Procesory skenovania* | Nastaví poradie programov, ktoré každé skenovanie spustí ako prvé, a zapína ich alebo vypína (oddiel 3.14). Počas skenovania sa nedá otvoriť. |
| *Systém* | *Možnosti* | Otvorí nastavenia AutoBleemu (oddiel 3.6). |
| | *Sieť a ovládače* | Otvorí obrazovky pre WiFi, párovanie ovládačov cez Bluetooth, nastavenie DualShock 3 a mapovanie ovládača (kapitola 6). Je tu iba vtedy, keď ich poskytuje niektoré rozšírenie - pozri nižšie. |
| | *Informácie o hardvéri* | Ukáže údaje o stroji - systém, procesor, úložisko, sieťové rozhrania, časové pásmo, obrazovku a ovládače s ich mapovaním - na tej istej stránke na každej platforme (oddiel 4.2). Circle vás vráti do systémovej ponuky. |
| | *Virtuálny gamepad* | Ukáže ovládače, ktoré dostávajú aplikácie, a ovládače, ktoré vidí démon; pomôže, keď ovládač v aplikácii nefunguje (oddiel 4.5). Circle vás vráti do systémovej ponuky. |
| | *Aktualizácia softvéru* | Hneď na webe skontroluje, či nie je novší AutoBleem alebo RetroArch, namiesto čakania na dennú kontrolu (oddiel 3.12). Keď už spúšťač o novej verzii vie, v riadku stojí *Dostupná aktualizácia*. Na PlayStation Classic to vyžaduje jadro AutoBleem a sieť WiFi. |
| | *O programe* | Ukáže poďakovania a licenciu. |
| *Odchod* | *RetroArch* | Opustí spúšťač a prejde do vlastnej ponuky RetroArch, k jeho nastaveniam a zoznamom obsahu; keď RetroArch zatvoríte, ste späť v spúšťači. Je tu iba tam, kde je nainštalovaný RetroArch. |
| | *Vypnúť* | Po potvrdení vypne stroj (pozri nižšie). |

**Sieť a ovládače** sa objaví iba tam, kde niektoré nainštalované rozšírenie poskytuje položku `network`;
rozšírenie to ohlási riadkom `Provides=network` vo svojom `extension.ini`. PSC-Bios to robí na konzole, Raspberry
Pi a PC kľúči. Ak je toto rozšírenie nainštalované, ale vypnuté, položka v ponuke zostane, sivá, a jej popis vás
vyzve, aby ste ho zapli v Rozšíreniach; Cross na nej otvorí zoznam Rozšírení priamo na danom rozšírení.

**Vypnúť** urobí to, čo sa pre daný stroj hodí. Konzolu uvedie do pohotovostného režimu AutoBleemu: kľúč sa
odpojí, kontrolka sa rozsvieti oranžovo a Power vráti spúšťač o pár sekúnd (oddiel 2.1). Raspberry Pi alebo PC sa
vypne.

![Systémová ponuka](../images/en/system-menu.jpg)

### 3.6 Možnosti

V Možnostiach si AutoBleem prispôsobíte: obraz na obrazovke, vzhľad spúšťača, jazyk, zvuk aj to, ktorý emulátor
PS1 bude hrať vaše hry. Otvoríte ich zo systémovej ponuky (*Možnosti*) alebo ikonou *NASTAVENIA* pod hrou.
Obrazovku a jazyk zvyčajne nastavíte raz a vrátite sa, až keď niečo na konkrétnom televízore nevyzerá dobre
alebo máte chuť na zmenu.

Nastavenia sú rozdelené do skupín, každá pod vlastným nadpisom. Hore a Dole sa presúvate z riadka na riadok,
Vľavo a Vpravo meníte hodnotu riadka, na ktorom stojíte: ťuknutie posunie o krok, podržanie pokračuje ďalej. L1
a R1 skočia na prvý alebo posledný riadok, L2 a R2 listujú po stranách. Na riadku s výberom tém, hudby alebo písma
vyberie Start jednu možnosť náhodne. Nastavenie, ktoré sa zapína a vypína, ukazuje **ZAP** alebo **VYP**. Každú
zmenu vidíte hneď a Circle obrazovku opustí a všetko uloží - nič ďalšie potvrdzovať netreba. Jedinou výnimkou je
režim obrazovky, ktorý sa vyskúša, až keď z Možností odídete (pozri *Obraz* nižšie).

Niektoré riadky sa objavia iba tam, kde majú zmysel: riadky pre CRT iba pri obraze 4:3, riadky pre RetroArch
iba tam, kde je RetroArch nainštalovaný, a zabudované hry iba na PlayStation Classic.

| Skupina / nastavenie | Na čo slúži |
|---|---|
| *Rozhranie*: *Obraz:* | Nastaví rozlíšenie obrazovky pre spúšťač aj emulátor PS1. *Auto* použije vlastný režim obrazovky a ukáže, ktorý to je, napríklad *Auto (1920x1080)*; vybrať môžete aj akýkoľvek režim, ktorý obrazovka ponúka. Konzola ponúka 720p, 1080p a *CRT 4:3* (720x480), režim pre starý CRT televízor alebo zachytávacie zariadenie 4:3. Zmeňte ho, keď obraz na televízor nesedí alebo je rozmazaný. Ak AutoBleem beží v okne na vývojárskom stroji, tento riadok tam nie je. |
| *Okraj CRT:* | Všetko trochu zmenší, od 0 do 10 % po 1 %, pretože staré televízory orezávajú okraje obrazu. Zvyšujte ho, kým nie je celá lišta s nápovedou aj rohy dobre vidieť. Zobrazí sa iba pri výstupe 4:3, prejaví sa hneď a platí už pred úvodnou obrazovkou pri štarte. |
| *Výška obrazu:* | Urobí obraz vyšším alebo nižším, od -40 do +40 po 2, pri akomkoľvek výstupe 4:3 - *CRT 4:3* alebo režime 4:3 na výstupe VGA či PC. Použite ho, keď je obraz na starom televízore stlačený alebo presahuje hore a dole. Prejaví sa hneď a riadi sa ním aj obraz hry v RetroArch. |
| *Škálovanie obrazu emulátora:* | Určuje, ako emulátor PS1 prispôsobí obraz hry vašej obrazovke. *1x1* ukáže vlastné pixely PlayStationu, malé a presné; *2x (celočíselne)* a *4:3 (celočíselne)* zväčšujú iba celými násobkami, čo dáva najostrejší obraz; *4:3* zachová pôvodný tvar obrazu; *Celá obrazovka* roztiahne obraz cez celú obrazovku. Nahrádza starý prepínač Widescreen. Klasický `pcsx-ab` a RetroArch poznajú iba celú obrazovku a 4:3. |
| *Halo obrazovky:* | Keď je ZAP, prázdne pásy vedľa obrazu hry (tam, kde obraz nevyplní celú obrazovku) sa namiesto čiernej vyplnia jemnou žiarou samotného obrazu. Funguje s `pcsx-abnxt`. |
| *Téma AutoBleemu:* | Zmení vzhľad spúšťača. Témy sú v `Themes/` a zobrazí sa tu podľa názvu aj téma, ktorej zip tam len nahráte. Témy, ktoré AutoBleem dodáva, sa pri každej aktualizácii obnovia, takže ak si nejakú chcete upraviť, skopírujte ju najprv pod novým menom. Predvolená je **ab2.0.0**. |
| *Štýl obalu:* | Vyberie rámik plastovej krabičky, ktorý sa kreslí okolo obalov hier z PS1. |
| *Záblesk obalu:* | Nechá cez vybraný obal prebehnúť záblesk zakaždým, keď sa polica zastaví. |
| *Jazyk:* | Nastaví jazyk spúšťača; jazykov je 17 a zmena platí okamžite. |
| *Doba zobrazenia oznámenia:* | Nastaví, ako dlho zostanú informačné bubliny (*Zobrazujem: ...*, súhrn skenovania) na obrazovke, od 0 do 20 sekúnd; pri 0 sa ukáže *Vypnutý* a bubliny sa vypnú. Chybové hlásenia majú vlastný pevný čas, takže vám žiadne neujde. |
| *Úvodná obrazovka:* | Počas štartu spúšťača ukáže obrázok AutoBleem; ak ho vypnete, prejdete rovno na policu. |
| *Animácie:* | Animuje prechod z jednej obrazovky na druhú; vypnite ich, ak chcete, aby sa každá obrazovka objavila okamžite. |
| *Písma*: *Použiť predvolené písmo:* | Keď je ZAP, spúšťač používa vlastné písmo (Red Hat Text); vypnite ho, ak chcete písmo zvolené v ďalšom riadku. |
| *Písmo:* | Vyberie vaše vlastné písmo: akýkoľvek súbor `.ttf` alebo `.otf` v `resources/fonts`, `RetroArch/fonts` alebo v priečinku témy. Riadok ukazuje názov písma, ktoré sa naozaj používa. |
| *Zvuk*: *Hudba:*, *Hudba na pozadí:* | *Hudba:* vyberie skladbu, ktorá hrá v spúšťači - vlastnú skladbu témy alebo súbor z `resources/music`. *Hudba na pozadí:* určuje, či bude hrať nejaká hudba vôbec. |
| *Emulácia*: *Emulátor PS1:* | Vyberie emulátor, v ktorom sa spúšťajú vaše hry z PS1: `pcsx-abnxt`, predvolený (súčasný PCSX-ReARMed s doplnkami AutoBleemu), alebo `pcsx-ab`, klasický. Keď niektorá hra nebeží dobre, skúste ten druhý. Bod obnovenia uložený jedným emulátorom môžete dohrať v druhom, pokiaľ hra nebežala bez súboru BIOS. |
| *Vymeniť hráča 1 / hráča 2 (emulátory PS1):* | V oboch emulátoroch PS1 vymení, ktorý z prvých dvoch ovládačov je hráč 1 a ktorý hráč 2 - šikovné, keď sú ovládače zapojené „naopak". Význam má iba pri dvoch a viacerých pripojených ovládačoch; s jedným ovládačom hráte vždy za hráča 1. RetroArch sa to netýka. Ak emulátor PS1, ktorý používate, výmenu ešte nevie, AutoBleem vám to povie. |
| *Hrať všetky PSX hry cez RA:*, *Aktualizovať konfiguráciu RA:*, *Uchovať nastavenia RetroArch:* | Tieto tri sú tu iba tam, kde je nainštalovaný RetroArch. Prvý spúšťa každú hru z PS1 v jadre PS1 v RetroArch (*PlayStation 1*; na PC je to SwanStation). Druhý dovolí AutoBleemu zapísať pri spúšťaní hry svoje nastavenia do konfigurácie RetroArch. Tretí zachová zmenu, ktorú urobíte vo vlastnej ponuke RetroArch, aj po jeho ukončení. |
| *Knižnica*: *Zobraziť originálne hry:* | Ukáže v zoznamoch PlayStation hry zabudované v konzole (iba PlayStation Classic). |
| *Čisté názvy hier:* | Keď je ZAP (predvolene), zoznamy hier RetroArch ukazujú upravené názvy bez značiek v zátvorkách ako (USA), (Rev 1) alebo [!]; VYP ukazuje názvy súborov. Názov súboru nájdete aj tak v podrobnostiach hry. Hier z PS1 sa to netýka, ich názvy pochádzajú z databázy. |
| *Sťahovať obaly online:* | Dovolí skenovaniu stiahnuť chýbajúce obaly zo serverov libretro (Raspberry Pi, PC, Windows). |
| *Aktualizácie*: *Aktualizácie:* | Vyberie, ktoré aktualizácie spúšťač hľadá (oddiel 3.12): `release` (odskúšaná verzia), `testing` (nasledujúca verzia, ktorá sa testuje), `nightly` (najnovšie vývojové zostavenie) alebo `off`. Predvolená hodnota sa riadi verziou, ktorú ste nainštalovali. Na vývojárskom stroji sa nezobrazuje. |
| *Diagnostika*: *Uchovávať logy na kľúči:* | Od ďalšieho štartu uchováva na kľúči všetky logy, nielen po páde - zapnite ho, keď pátrate po nejakom probléme (kapitola 7). |
| *Zobraziť výkon:* | V ľavom dolnom rohu ukáže prekrytie so snímkovou frekvenciou, zaťažením procesora, vláknami a pamäťou; v hre ukáže emulátor aj svoje FPS a procesor. |

**Zmena režimu obrazovky.** Keď z Možností odídete s novým režimom v *Obraz:*, AutoBleem naň prepne a opýta sa
*Ponechať tento režim obrazu?*. Ak je obraz v poriadku, potvrďte to. Ak televízor nič neukazuje, počkajte: bez
potvrdenia sa AutoBleem po odpočítaní vráti k predchádzajúcemu režimu.

**Témy na obrazovke 4:3.** V režime *CRT 4:3* ukazuje zoznam tém iba tie, ktoré majú rozloženie 4:3. Ak ho téma,
ktorú používate, nemá, po potvrdení režimu (a pri každom štarte v tomto režime) ju nahradí predvolená téma
a upozorní vás na to oznámenie *Téma zmenená na predvolenú (CRT 4:3)*.

![Možnosti rozdelené do skupín](../images/en/options.jpg)

![Skupina Rozhranie: Okraj CRT a Výška obrazu](../images/en/options-display.jpg)

![Oznámenie po prepnutí na CRT 4:3 s témou, ktorá nemá rozloženie 4:3](../images/en/crt43-theme-notice.jpg)

### 3.7 Nastavenia hry

Každá hra môže mať vlastné nastavenia. Väčšina hier hrá dobre tak, ako je, no občas niektorá potrebuje malú
pomoc - ostrejší alebo jemnejší obraz, vynechanú snímku, aby bežala plynulo, inú pamäťovú kartu - alebo ju chcete
označiť ako obľúbenú. Na to slúži editor hry: v ňom tieto veci zmeníte pre jednu jedinú hru a ostatných sa
nedotknete.

Keď máte hru vybranú, stlačte **Dole** a pod ňou sa otvorí rad ikon. Má štyri ikony: *NASTAVENIA* (možnosti
z oddielu 3.6), *Hra* (vlastné nastavenia tejto hry), *PAMÄŤOVÁ KARTA* (jej pamäťová karta) a *OBNOVA* (jej
uložené pozície). Presuňte sa na jednu z nich a otvorte ju tlačidlom Cross.

**Editor hry** (ikona *Hra*) ukazuje vpravo podrobnosti hry - názov, vydavateľa, rok, počet hráčov, priečinok
a pamäťovú kartu - a vľavo jej nastavenia. Hore a Dole sa presúvate medzi nastaveniami, Vľavo a Vpravo ich meníte,
rovnako ako v Možnostiach; keď tlačidlo podržíte, pohyb sa opakuje. Keď skončíte, Circle zmeny uloží a vráti vás
späť. Hra, ktorá vo svojich údajoch nemá názov, sa zobrazí pod názvom svojho priečinka.

Nastavenia sú v štyroch skupinách:

- **Hra** sa týka toho, ako AutoBleem s hrou zaobchádza. *Obľúbené:* ju zaradí do skupiny *Obľúbené hry* vo výbere
  sady. *Uzamknúť zmeny:* povie skeneru, aby názov, sériové číslo a zoznam diskov nechal presne tak, ako ste ich
  nastavili, a neskoršie skenovanie vaše zmeny neprepísalo. *Pokračovanie:* určuje, čo sa stane, keď spustíte hru,
  ktorá má body obnovenia: *Opýtať sa* ukáže výber pozícií, *Posledná pozícia* hneď pokračuje z najnovšej
  pozície a *Nikdy* spustí hru vždy od začiatku. Tam, kde je nainštalovaný RetroArch, sú tu ešte dva riadky.
  *Hra Lightgun:* je pre hru so svetelnou pištoľou: zaradí ju do skupiny *Hry so svetelnou pištoľou* a hra sa
  vždy spúšťa v RetroArch, pretože jadro PS1 v RetroArch má GunCon (zapnutím sa zapne aj ďalší riadok). *Hrať cez
  RA:* spúšťa práve túto hru v RetroArch namiesto emulátora PS1.
- **Obraz** sa týka toho, ako obraz vyzerá. *Rozlíšenie:* kreslí hru v 1x alebo 2x (na zabudovanom GPU)
  a *Odstrániť švy:*, ktoré funguje iba pri 2x, skryje tenké čiary, ktoré sa pri tejto veľkosti môžu objaviť medzi
  časťami obrazu. *Dithering:* (*Vypnutý*, *Zapnutý*, *Vždy*) ovláda jemný bodkový vzor, ktorým PlayStation
  prelína farby, a *Vyhladzovanie:* vyberie jeden z vyhladzovacích škálovačov emulátora. *Filter:* určuje, ako sa
  obraz prispôsobí obrazovke: *Najbližší* ukazuje holé pixely, *Lineárny* ich vyhladí, *Ostrý* a *Ostrý
  (jednoduchý)* nechajú pixely ostré bez mihotania a je tu aj *Quilez*. Filtre CRT *CRT (fast)*, *CRT (raster)*
  a *CRT-Pi* napodobňujú starý televízor a kreslia vlastné riadky, preto sú riadky pre obrazové riadky sivé, kým je
  niektorý z nich vybraný. Inak *Obrazové riadky:* pridá tmavé riadky starého televízora a *Jas obrazových
  riadkov:* nastaví, aké sú tmavé. *Rozlíšenie*, *Odstrániť švy*, *Dithering*, *Vyhladzovanie* a filtre okrem
  *Lineárny* a *Najbližší* sú pre `pcsx-abnxt`; klasický `pcsx-ab` a RetroArch ukážu každý iný filter ako
  *Najbližší*.
- **Vykresľovanie** obsahuje *Plugin:* pre GPU a *Preskočenie snímok:* (*Auto*, *Vypnutý* alebo 1 až 3 snímky).
  Preskakovanie snímok pomôže hre, ktorá beží príliš pomaly, udržať rýchlosť, za cenu menej plynulého obrazu.
- **Emulátor** obsahuje *SpeedHack:*, *CPU hodiny:* procesora, *Interpolácia zvuku:* (ako sa zvuk vyhladzuje),
  *Logo pri spustení:* a s `pcsx-abnxt` aj *Opravy Sony:*. Ak *Logo pri spustení:* vypnete, preskočí sa úvodná
  obrazovka BIOS - to potrebujete pre homebrew disk, ktorý sa pre vlastné logo nechce spustiť.

Tvar obrazu a rozlíšenie obrazovky sa nenastavujú pre každú hru zvlášť, ale pre všetky naraz, v Možnostiach
(*Škálovanie obrazu emulátora:* a *Obraz:*).

**Ďalšie tlačidlá v editore.** Triangle hru premenuje pomocou klávesnice na obrazovke. Square dá hre inú pamäťovú
kartu (*Zmeniť pamäťovú kartu*). Kým hra ešte používa vlastnú kartu, Start z nej urobí novú zdieľanú sadu, aby ju
mohli používať aj iné hry (*Zdieľať pamäťovú kartu*, oddiel 3.8). Tieto dve možnosti sa pri zabudovaných hrách
konzoly neponúkajú. Podržanie Vľavo / Vpravo alebo Hore / Dole tu opakuje pohyb, rovnako ako v nastaveniach hier
a jadier RetroArch.

Svoje nastavenia si hra drží vo vlastnom súbore `pcsx.cfg`. Každá hra na kľúči ho má, pretože ho vytvorí už
skenovanie. Originálny disk v USB mechanike (oddiel 3.9a) dostane vlastný priečinok so súborom `pcsx.cfg` až
vtedy, keď ho prvýkrát spustíte; dovtedy sa zmena v editore nedá uložiť a editor vám oznámi *Neuložené: hra
nemá pcsx.cfg*. Disk preto raz spustite - odvtedy si svoje nastavenia pamätá ako každá iná hra. Disk, ktorý
patrí k hre, ktorú už v zbierke máte, používa priečinok a nastavenia tej hry hneď od začiatku.

Pre **disk v mechanike** (oddiel 3.9a) niektoré nastavenia nemajú zmysel, a tak ich editor zošedí a keď sa na
taký riadok presuniete, v spodnom riadku sa ukáže *Nie je k dispozícii pre disk v mechanike*.

![Editor hry pre disk v mechanike](../images/en/game-editor-disc.jpg)

**Nastavenia uložené v emulátore.** Hru si môžete vyladiť aj priamo počas hrania: vlastná ponuka emulátora má
položku *Uložiť nastavenia pre túto hru* (oddiel 3.9). Keď má hra nastavenia uložené tam, hrá s nimi. Editor hry
potom ukazuje riadky skupín Obraz, Vykresľovanie a Emulátor sivé, s uloženými hodnotami, pod nadpisom *Uložené
v emulátore* - môžete si ich prečítať, ale nie zmeniť. Ak chcete znova používať nastavenia z editora, vyberte
*Odomknúť nastavenia* a potvrďte: nastavenia uložené emulátorom sa zmažú a riadky sa dajú opäť meniť. Oba
emulátory, `pcsx-ab` aj `pcsx-abnxt`, čítajú a zapisujú tie isté uložené nastavenia, takže je jedno, ktorý ich
uložil.

![Editor hry](../images/en/game-editor.jpg)

### 3.8 Pamäťové karty a uložené pozície

Na skutočnom PlayStatione ste mali jednu či dve pamäťové karty pre všetky hry a skôr či neskôr na nich došlo
miesto. V AutoBleeme má každá hra z PS1 predvolene vlastnú pamäťovú kartu, takže nikdy nemusíte riešiť miesto ani
to, na ktorej karte je ktoré uloženie. Karta je uložená spolu s uloženými pozíciami hry v
`Games/!SaveStates/<priečinok hry>/`.

**Zdieľané sady pamäťových kariet.** Niekedy hry potrebujú vidieť uloženia tých druhých - napríklad pokračovanie,
ktoré načíta uloženú hru z prvého dielu, alebo disky jednej série, ktoré chcete mať na jednej karte. Na to si
vytvoríte zdieľanú sadu: jednu kartu, ktorú používa viac hier. Sady sú uložené v `Games/!MemCards/` a spravujete
ich položkou *Pamäťové karty* v systémovej ponuke. Square vytvorí novú sadu (jej názov napíšete na klávesnici na
obrazovke), Cross vybranú sadu premenuje a Triangle ju po potvrdení zmaže. Hru na sadu presuniete cez *Zmeniť
pamäťovú kartu* v jej editore (oddiel 3.7) alebo cez jej ikonu *PAMÄŤOVÁ KARTA*.

**Editor pamäťových kariet** sa otvára ikonou *PAMÄŤOVÁ KARTA* pri hre. Ukazuje kartu hry a druhú kartu vedľa
seba, pri každom uložení jeho ikonu a názov, tak ako obrazovka pamäťových kariet na pôvodnej konzole. Square
skopíruje vybrané uloženie na druhú kartu, Triangle ho zmaže a Select kartu zdefragmentuje - zhromaždí jej voľné
bloky dokopy, aby sa na ňu zmestilo aj veľké uloženie. Start vám dovolí vybrať, ktorá sada sa ukazuje vpravo,
a Cross obe karty znova načíta z kľúča. Karta, na ktorú hra ešte nič nezapísala - v hre ste ešte neukladali - je
prázdna a pri jej názve stojí *zatiaľ žiadna karta*. Ak ste niečo zmenili, AutoBleem sa pred odchodom z editora,
opätovným načítaním kariet alebo zobrazením inej sady opýta *Chcete uložiť údaje z kariet?*.

![Editor pamäťových kariet](../images/en/memory-card-editor.jpg)

**Body obnovenia.** Mnohé hry z PS1 vás nechajú uložiť iba na určitých miestach a nie vždy sa k nejakému
dostanete, kým musíte prestať. Na to sú body obnovenia: keď hru z PS1 opustíte tlačidlom Reset na konzole (alebo
cez ponuku emulátora na Pi či PC), AutoBleem uloží stav presne tam, kde ste práve boli. Kým ho pri odchode z hry
zapisuje, ukazuje emulátor *Please wait...*. Nabudúce pokračujete presne od tej chvíle.

Nájdete ich pod ikonou *OBNOVA* pri hre. Hra s bodom obnovenia ukazuje na ikone jeho malý obrázok; hra bez neho
má ikonu sivú. Výber pozícií má štyri pozície zobrazené ako karty v rámčeku, každú s obrázkom danej chvíle,
číslom pozície a dátumom. Najnovšia je označená **NAJNOVŠIE** a nepoužitá pozícia hlási *Žiadny bod obnovenia*.
Cross pokračuje v hre z vybranej pozície, Triangle ju zmaže. Či sa výber pri spustení hry vôbec objaví, určuje
nastavenie *Pokračovanie:* danej hry (oddiel 3.7).

Aj hry z PS1, ktoré hráte v RetroArch, majú pozície na obnovenie. Každá pozícia nesie odznak - logo AutoBleem 2
alebo logo RetroArch - takže vidíte, ktorý emulátor ju zapísal.

![Výber pozícií na obnovenie](../images/en/resume-picker.jpg)

### 3.9 Spúšťanie hier, RetroArch a aplikácie

Spúšťanie hier budete robiť najčastejšie, preto naň stačí jedno tlačidlo: vyberte hru na polici a stlačte
**Cross**. Hra z PS1 sa otvorí na celej obrazovke v emulátore PS1, ktorý ste si zvolili v Možnostiach (oddiel
3.6), a beží, kým ju neopustíte. Ak by ste hru z PS1 radšej hrali v RetroArch - lebo tam beží lepšie alebo vám
vyhovujú jeho možnosti - stlačte namiesto toho **Square**.

**Ako odísť z hry.** Na PlayStation Classic robia vlastné tlačidlá konzoly to, čo by ste od nich čakali.
**Reset** vpredu vás vráti do spúšťača a uloží bod obnovenia tam, kde ste práve boli, takže môžete neskôr
pokračovať (oddiel 3.8); funguje aj vtedy, keď je otvorená ponuka v hre. **Power** konzolu vypne. Raspberry Pi ani
PC také tlačidlá nemajú, preto tam z hry odídete cez ponuku emulátora, ktorá je popísaná nižšie.

Existuje aj cesta von, ktorá funguje rovnako na každom ovládači - na pôvodnom z konzoly, na USB aj na Bluetooth
ovládači: **podržte Start + Select alebo Home na 2 sekundy** a ste späť v AutoBleeme. Krátke stlačenie tých istých
tlačidiel namiesto toho otvorí ponuku emulátora. Spúšťač vám obe pripomína v nápovede (*Podržte Select+Start
alebo Home 2 sekundy: späť do AutoBleem* a *Krátke stlačenie Select+Start alebo Home: ponuka emulátora*).
Aplikácia ponuku emulátora nemá, takže v nej funguje iba dlhé podržanie. Na konzole Reset vždy ukončí aj
aplikáciu.

**Ponuka v hre.** S `pcsx-abnxt` má emulátor vlastnú ponuku pre veci, ktoré počas hrania potrebujete: ukladanie,
výmenu diskov, úpravu obrazu, výber ovládačov. Stlačte tlačidlo ponuky - Home na ovládači, ktorý ho má, **Select
+ Start** na ovládači bez neho alebo **Esc** na klávesnici - a hra sa za ponukou zastaví, s posledným obrázkom na
pozadí. Ak tlačidlo ponuky podržíte 2 sekundy, urobí to isté ako Reset: hru opustí. Ponuka má tri karty a L1 a R1
medzi nimi prepínajú. Pamätá si, kde ste boli, takže sa nabudúce otvorí na tej istej karte a riadku.

- Karta **Hra** sa týka samotnej hry. *Pokračovať v hre* ponuku zatvorí a hráte ďalej. V časti *Uložené pozície*
  uloží *Rýchle uloženie* chvíľu, v ktorej práve ste, a *Rýchle načítanie* ju vráti. *Načítať automatické
  uloženie* vás vráti do stavu, v akom bola hra pred najviac 30 sekundami - túto kópiu si emulátor počas hrania
  drží v pamäti a zachráni vás pred chybou, ktorú sa inak vrátiť nedá. V časti *Disk CD* slúži *Vymeniť disk* hre
  na viacerých diskoch, keď si vypýta ďalší, a *Resetovať hru* spustí hru odznova. *Uložiť nastavenia pre túto
  hru* si zapamätá nastavenia, ktoré ste zvolili pre túto jednu hru (oddiel 3.7). *Menu PCSX* otvorí vlastné
  stránky PCSX-ReARMed s jeho možnosťami, cheatmi a informáciami (About) a *Ukončiť* vás vráti do AutoBleemu.
- Na karte **Obraz** meníte vzhľad hry a hneď vidíte výsledok: *Obrazovka*, *Rozlíšenie* (1x alebo 2x),
  *Odstrániť švy*, *Dithering*, *Škálovanie*, *Halo obrazovky*, *Vyhladzovanie*, *Filter*, *Maska CRT*,
  *Scanlines* a *Jas scanlines*. Sú to tie isté nastavenia ako v editore hry (oddiel 3.7) a pri každom riadku je
  vpravo pomocný text, ktorý vysvetľuje, na čo slúži. *Obrazovka* je rozlíšenie obrazovky; na konzole ho vyberáte
  v Možnostiach a tu sa iba zobrazuje. *Halo obrazovky* je pre tmavé pruhy po stranách obrazu 4:3 na širokouhlom
  televízore: vyplní ich okrajmi samotného obrazu, zrkadlenými a stmavenými, takže hra akoby do nich presvitala
  a nesedí medzi dvoma čiernymi pruhmi. *Maska CRT* položí na obraz vzor luminoforu starej obrazovky -
  *Apertúra* dáva jemné pruhy Trinitronu, *Štrbinová* a *Delta* body iných obrazoviek; ponúka sa iba s filtrom
  CRT (raster). Filter CRT-Pi je pre konzolu pri 1080p príliš náročný. Riadok, ktorý sa netýka danej situácie,
  je sivý a pomocný text povie prečo.
- Karta **Ovládače** určuje, čo je zapojené do dvoch portov PlayStationu, *Ovládač 1* a *Ovládač 2*:
  štandardný (digitálny) ovládač, analógový ovládač (DualShock), pištoľ alebo nič. Niektoré hry fungujú iba
  s jedným druhom ovládača. Zmena sa prejaví, keď sa vrátite do hry.

Ponuka je nakreslená vo vlastnom vzhľade spúšťača ab2.0.0, takže nepôsobí ako iný program, a ukazuje batérie
vašich ovládačov aj obrázok posledného rýchleho uloženia.

**Hry z RetroArch.** Hra z iného systému sa spustí v RetroArch s jadrom, ktoré spúšťač pre daný systém vybral. Keď
dohráte, *Close Content* alebo *Quit RetroArch* v ponuke RetroArch vás vráti do spúšťača. Ak chcete zmeniť, ktoré
jadro hrá niektorý systém, otvorte v Rýchlej ponuke *Jadrá RetroArch* (oddiel 3.4); zoznam sa otvorí s jadrom
*PlayStation 1* úplne hore. A ak chcete vlastnú ponuku RetroArch (XMB) s jeho nastaveniami a vlastnými zoznamami
obsahu, vyberte v systémovej ponuke *RetroArch*: RetroArch sa potom otvorí bez načítaného obsahu.

![Okno jadier RetroArch s jadrom PlayStation 1 hore](../images/en/retroarch-cores.jpg)

**Aplikácie.** Aplikácie sú skôr programy ako hry: nástroje konzoly a na konzole aj doplnkové aplikácie, ktoré
prichádzajú s balíkom RetroArch - Doom, Quake, Amiga a ďalšie. Nájdete ich v sade Aplikácie. Pred spustením
aplikácie vám AutoBleem ukáže jej popis, aby ste vedeli, čo to je a ako sa ovláda. Cross ju spustí, Circle vás
vráti na policu.

![Popis aplikácie, ktorý sa ukáže pred jej spustením](../images/en/app-start.jpg)

**Nastavenia aplikácie.** Mnohé aplikácie boli napísané pre jeden konkrétny ovládač, preto môžete zmeniť, ako
vidia ten váš. Vyberte aplikáciu, otvorte rad ikon a zvoľte *Hra*: otvoria sa *Nastavenia hry* aplikácie (*Zmeniť
spôsob spustenia tohto programu*). *Režim ovládača:* určuje, aký ovládač sa aplikácia dozvie, že má. *Automaticky*
použije to, čo si aplikácia sama vypýta; *Ovládač PSC* a *Ovládač Xbox 360* predstavia váš ovládač ako ovládač
konzoly alebo ako ovládač Xbox 360 a *Ovládač PSC (systémový)* a *Ovládač Xbox 360 (systémový)* urobia to isté
cez samotný systém. Keď aplikácia na váš ovládač nereaguje, ako by mala, skúste iný režim. *D-pad ako páčka:*
nechá smerový ovládač pohybovať analógovou páčkou, pre aplikáciu, ktorá počúva iba páčku, a *Páčka ako D-pad:*
robí opak.

Niektoré aplikácie sa vás pri prvom spustení na niečo opýtajú. Jedna chce vedieť *Aké ovládanie má váš
ovládač?*, aby si mohla nastaviť ovládanie: odpovedzte *Jeden D-pad* pri ovládači iba so smerovým ovládačom,
alebo *Analógové páčky*. Aplikácia, ktorá spúšťa Windows, sa opýta *Čo chcete urobiť?* a ponúkne spustenie
Windows, ich inštaláciu, spustenie DOS alebo odinštalovanie Windows. Keď vám aplikácia dovolí nastaviť kláves,
vyzve vás *Stlačte jedno z tlačidiel.*

![Nastavenia hry pri aplikácii](../images/en/app-game-settings.jpg)

Program pre Windows, ktorý spúšťa PE runner (PE aplikácia, oddiel 3.3), sa s vami rozpráva cez vlastné obrazovky
AutoBleemu: hlásenie, ktoré chce ukázať, sa objaví ako *Správa* a otázka s možnosťami ako *Vyberte možnosť*,
v oboch prípadoch s názvom aplikácie v nadpise.

![Otázka PE aplikácie zobrazená ako obrazovka AutoBleemu](../images/en/pe-dialog.jpg)

### 3.9a Disk v USB mechanike

Ku konzole, k Raspberry Pi alebo k PC spustenému z kľúča AutoBleem môžete pripojiť obyčajnú USB mechaniku CD/DVD
a hrať priamo z originálneho disku PlayStation - bez akéhokoľvek kopírovania. Disk, ktorý vložíte, sa v spúšťači
objaví ako ďalšia hra. Vo Windows to nefunguje.

**Skopírovanie disku na kľúč.** Ak chcete mať hru vždy po ruke, aj bez disku, stlačte Square (*Kopírovať disk*).
AutoBleem sa najprv opýta, či má hru skopírovať, a povie vám, koľko miesta zaberie; potom ju uloží do priečinka
`Games` ako jeden súbor CHD (hra na viacerých diskoch dostane aj súbor `.m3u`, aby výmena diskov v hre fungovala).
Počas kopírovania vidíte rýchlosť a zostávajúci čas a *Prerušiť* kopírovanie zastaví. Keď je hotovo, hra stojí na
polici ako každá iná. Hru, ktorá už v `Games` je, AutoBleem nekopíruje, a ani takú, pre ktorú nie je miesto - vtedy
vám povie, koľko miesta potrebuje. Skopírovať sa dá aj poškriabaný disk: časti, ktoré sa nedali prečítať, sa
vyplnia nulami a AutoBleem vám povie, koľko ich bolo. Taká kópia môže, ale nemusí fungovať.

Square ponúka kopírovanie pri každom hernom disku PlayStation v zobrazení disku, aj pri takom, ktorý databázy
obalov nepoznajú. Hra, ktorú databázy poznajú, sa skopíruje pod svojím názvom; pri hre na viacerých diskoch
kopírujte disky jeden po druhom a súbor `.m3u` ich zoradí, disk 1 ako prvý. Disk, ktorý databázy nepoznajú, dostane
namiesto názvu svoje sériové číslo, skopíruje sa ako jediný disk a na polici nemá obal. Okno kopírovania,
*Kopírovanie disku*, zostane na obrazovke, kým sa kopírovanie neskončí alebo nezastaví - spúšťač medzitým čaká -
a rýchlosť ukazuje ako násobok bežnej CD mechaniky. Ak kopírovanie zlyhá, AutoBleem vám povie prečo.

![Kopírovanie disku](../images/en/disc-copy.jpg)

**Hranie z disku.** Keď vložíte disk, **zobrazenie disku** sa otvorí samo hneď, ako sa disk načíta. Ukazuje obal
disku - z databáz obalov alebo stiahnutý online - so sériovým číslom a názvom a Cross hru spustí. Hra z PS1 hraná
z disku si body obnovenia a uložené hry ukladá do vlastného priečinka, takže môžete prestať a neskôr pokračovať
rovnako ako pri hre na kľúči. Po hre, alebo keď ste boli v možnostiach či v nastaveniach rozšírenia, sa vrátite do
zobrazenia disku. Ak ho opustíte cez Circle, aby ste si prezreli ostatné hry, disk zostane v mechanike a Circle na
polici zobrazenie vráti; na prázdnej polici ho otvorí aj R1 (*Disk*). Na polici s hrami má R1 svoju bežnú úlohu
a skáče medzi začiatočnými písmenami. Keď disk vyberiete, zobrazenie disku sa zatvorí.

![Zobrazenie disku](../images/en/disc-view.jpg)

**Štítok mechaniky** v hornej časti obrazovky vám hovorí, čo mechanika práve robí, aby ste vedeli, či máte čakať.
Bez pripojenej mechaniky nevidíte nič. Mechanika bez disku ukazuje tlmenú ikonu disku. Kým sa disk číta, ikona
bliká a hlási *Číta sa disk...*, a keď je pripravený, ikona sa rozsvieti spolu s názvom disku. Ak vložíte disk,
ktorý nie je hrou pre PlayStation ani zvukovým CD, štítok hlási *Toto nie je disk PlayStation*, a ak mechanika
disk práve nedokáže prečítať, hlási *Disk sa teraz nedá prečítať*.

![Štítok mechaniky](../images/en/disc-chip.jpg)

**Zvukové CD.** Mechanika prehrá aj hudobné CD. Zvukové CD namiesto zobrazenia disku otvorí **CD prehrávač**.
Ten ukáže disk ako *Audio CD* so zoznamom skladieb a celkovým časom a riadok pod ním pomenuje vybranú skladbu
a povie, či je zapnuté opakovanie a náhodné poradie. Disk, ktorý prehrávač prehrať nevie, je označený *Tento disk
sa nedá prehrať*. Tlačidlá prehrávača:

| Tlačidlo | V CD prehrávači |
|---|---|
| Cross | Prehrá vybranú skladbu. |
| Start | Pozastaví hudbu a znova ju spustí. |
| Square | Zastaví hudbu. |
| L1 / R1 | Prejdú na predchádzajúcu alebo nasledujúcu skladbu. |
| L2 / R2 | Pretáčajú skladbu dozadu alebo dopredu, vždy o päť sekúnd. |
| Triangle | Zmení, čo sa opakuje: nič, celý disk alebo aktuálna skladba. |
| Select | Zapne alebo vypne náhodné poradie, aby skladby hrali na preskáčku. |
| Circle | Opustí CD prehrávač. |

![CD prehrávač](../images/en/cd-player.jpg)

**Disky s LibCrypt.** Niektoré hry pre PlayStation, väčšinou európske, majú ochranu proti kopírovaniu zvanú
LibCrypt. Aby bežali, potrebuje emulátor malý súbor `.sbi` s údajmi ochrany. AutoBleem si ho sám stiahne z webu
predtým, ako sa taký disk spustí, aj keď ho kopírujete, a skopíruje ho spolu s hrou. Potrebuje na to sieť: na
Raspberry Pi alebo PC tú, ktorú už má, na konzole WiFi, ktorú ste nastavili v PSC-Bios.

Pri disku v mechanike niektoré nastavenia hry nemajú zmysel, preto ich editor hry zošedí (oddiel 3.7).

### 3.10 Pridávanie hier

AutoBleem si vaše hry nájde sám, pokiaľ sú na správnom mieste. Tento oddiel vám povie, kam ktorý druh patrí, aby
ich každé skenovanie postavilo na policu aj s názvami a obalmi.

**Hry z PS1** patria do priečinka `Games`, **každá do vlastného priečinka** pomenovaného podľa hry. Hry môžete
zoskupiť aj do vlastných priečinkov a každý taký priečinok sa vo výbere sady stane samostatnou skupinou (oddiel
3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                a folder of games: a group of its own in the set picker
    Klonoa/                   Klonoa.pbp
```

AutoBleem číta bežné formáty obrazov diskov: `.cue` s jeho `.bin` (alebo `.img`), `.pbp`, `.chd` (vrátane tých
komprimovaných cez zstd), `.iso` a `.ecm`, ktoré skenovanie za vás rozbalí. Funguje aj zazipovaná hra: procesor
**Unzip** ju rozbalí ešte predtým, ako ju skenovanie načíta (oddiel 3.14).

Nemusíte byť úzkostlivo poriadni. Hra na viacerých diskoch patrí do jedného priečinka so všetkými diskami, ale ak
nakopírujete priečinky s názvami `Game (Disc 1)`, `Game (Disc 2)` a tak ďalej, skenovanie ich zlúči do jedného
priečinka `Game`. Aj hry nahrané rovno do `Games/` ako voľné súbory skenovanie roztriedi do vlastných priečinkov.

**Názvy a obaly** prídu samy. Skenovanie prečíta sériové číslo každého disku a z databázy PlayStation v RetroArch
alebo z databáz obalov si vezme názov, vydavateľa, rok, počet hráčov a región. Ak chcete vlastný obal, dajte
vedľa obrazu hry súbor PNG alebo JPEG s rovnakým názvom. Bez neho príde obal z databáz obalov alebo, ak je
nainštalovaný RetroArch, zo sady náhľadov libretro; na Raspberry Pi, PC alebo vo Windows sa chýbajúci obal
stiahne online (Možnosti → *Sťahovať obaly online:*). Ak skenovanie niečo popletie, opravte to v editore hry
a zapnite *Uzamknúť zmeny:*, aby ďalšie skenovanie vašu zmenu zachovalo.

**Hry iných systémov** patria do `RetroArch/roms/`, **každý systém do vlastného priečinka pomenovaného tak, ako ho
pomenúvajú databázy RetroArch** - napríklad `Nintendo - Nintendo Entertainment System`, `Nintendo - Super
Nintendo Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` alebo `FBNeo -
Arcade Games` (prípadne `Arcade`). Priečinky sa vytvoria za vás a ROMky môžu zostať zazipované. Na Raspberry Pi,
PC alebo vo Windows ich skenovanie načíta samo a zapíše playlisty RetroArch. Kľúč konzoly to sám nezvládne, preto
tam na PC spustíte **UpdateRoms** (kapitola 5).

**Aplikácie** patria do `Apps/<názov>/`, každá s `app.ini` - jej názvom, ikonou a tým, čo sa má spustiť - a so
súborom `run.sh`.

**Balíky.** Niektoré aplikácie sú herné enginy: skôr ako hru spustia, potrebujú dáta hry, ktorú vlastníte. Takto
fungujú Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, hry pre DOS
a ďalšie. Súbory hry dajte do priečinka `Packages` na kľúči, každú hru do vlastného priečinka - napríklad
`Packages/Doom/DOOM2.WAD` - a AutoBleem ich rozpozná podľa tabuľky, ktorá s ním prichádza (`rc/packages.ini`).
V priečinku, ktorý rozpozná, sú voľné herné súbory samostatnými balíkmi. AutoBleem vaše súbory iba číta a nikdy
ich nemení. Balík môže prísť aj z Obchodu (oddiel 3.13).

Tam, kde ho spúšťač zobrazuje, ukazuje riadok *Balíky* na karte Aplikácie (oddiel 3.3) herné dáta, ktoré sa
našli. Cross na položke otvorí jej **Package info**: čo dáta obsahujú, popis, kde sú súbory a odkiaľ prišli (vaše
vlastné súbory, Obchod, mod alebo súbory, ktoré sú priamo v aplikácii), či ide o shareware alebo voľnú hru a ktorá
nainštalovaná aplikácia ich spúšťa. Ak ich nič z toho, čo máte nainštalované, spustiť nevie, informácie vám to
povedia.

Keď spustíte aplikáciu s enginom, AutoBleem hľadá herné dáta, ktoré vie spustiť. S jednou sadou dát sa hra spustí
hneď. Pri viacerých sa vás zoznam (*Vyberte herné dáta*) opýta, ktoré chcete hrať, a kurzor stojí na tých, ktoré ste
si vybrali naposledy. Ak nie sú žiadne, AutoBleem vám povie, aké dáta aplikácia potrebuje a kam ich dať, a nič sa
nespustí.

**Vaše vlastné hry.** Keď AutoBleem niektoré dáta nerozpozná, ich Package info hlási *Nerozpoznané. Ak ide o hru,
pozrite príručku: Vaše vlastné hry.* Tabuľka pozná iba hry, pre ktoré bola urobená. Pre inú hru si do priečinka
`Packages` napíšte vlastný `packages.ini` s riadkom pre ňu: AutoBleem číta ten váš ako prvý, takže vaše riadky
majú prednosť.

![Výber balíka, v ktorom zvolíte herné dáta na spustenie](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Skenovanie jednej časti.** Ak ste pridali hry iba do jednej sady alebo priečinka, *Znova skenovať hry* vie
prehľadať len túto časť, čo je rýchlejšie ako prehľadávať všetko, a jeho bublina po skončení zmizne.

**Témy** patria do `Themes/<názov>/` aj so svojím `theme.json` a obrázkami - alebo zip témy nahrajte do `Themes/`
tak, ako je.

### 3.11 BIOS pre PS1

BIOS je vlastný štartovací program PlayStationu a emulátor hrá hry najvernejšie so skutočným BIOSom. Na
**PlayStation Classic** nemusíte robiť nič: emulátor používa BIOS samotnej konzoly. Na **Raspberry Pi, PC
a vo Windows** dajte vlastné súbory BIOS pre PS1 do `System/Bios/`: `romw.bin` (americký/európsky SCPH-5501/5502)
a `romJP.bin` (japonský SCPH-5500, pre japonské hry). Inštalátory ich doplnia z balíkov BIOS pre RetroArch, pokiaľ
tam už nie sú vaše vlastné - tie nikdy nenahrádzajú. Bez nich emulátor beží na zabudovanom HLE BIOSe, náhradníkovi,
ktorý mnohé hry prijmú a niektoré nie; ak sa teda hra nechce spustiť, chýbajúci BIOS je prvá vec, ktorú treba
skontrolovať.

### 3.12 Aktualizácie

AutoBleem sa stará o to, aby bol aktuálny, takže nové funkcie a opravy dostanete bez preinštalovania. Pri štarte
spúšťača a potom raz denne sa na webe pozrie, či na jeho **kanáli** nie je nová verzia. Kanál si vyberiete
v Možnostiach → *Aktualizácie*: `release`, `testing`, `nightly`, alebo `off`, ak nechcete, aby sa pozeral vôbec.
Ak nechcete čakať na dennú kontrolu, *Aktualizácia softvéru* v systémovej ponuke skontroluje web hneď.

Keď je k dispozícii nová verzia, AutoBleem sa vás opýta, čo s ňou. *Aktualizovať teraz* ju stiahne a nainštaluje,
čo trvá pár minút. *Pripomenúť zajtra* sa opýta znova o deň a *Preskočiť túto verziu* sa už na túto verziu
nepýta. Nech zvolíte čokoľvek, vaše hry, uložené hry a nastavenia vždy zostanú; po aktualizácii spúšťač hry ešte
raz prehľadá. Značka kanála v ľavom hornom rohu (oddiel 3.1) ukazuje, aké zostavenie máte.

Ako sa aktualizácia nainštaluje, závisí od stroja:

- Na **Raspberry Pi** a **PC kľúči** sa po stiahnutí znova spustí inštalátor s tou istou obrazovkou priebehu ako
  pri prvom štarte a ponúkne aj novší RetroArch. Potom je spúšťač späť.
- Vo **Windows** sa otvorí stiahnutý inštalátor, nainštaluje novú verziu a spustí nový spúšťač.
- Na **PlayStation Classic** sa dokáže aktualizovať iba konzola s **jadrom AutoBleem** (ABFlashKit, oddiel 6.2)
  a **sieťou WiFi** nastavenou v PSC-Bios (oddiel 6.1) - konzola v továrenskom stave sieť nemá, takže spúšťač sa
  ani nepozerá. Po *Aktualizovať teraz* sa spúšťač zatvorí a na obrazovke zostane obrázok AutoBleem, kým sa kľúč
  aktualizuje, čo trvá pár minút; potom sa spustí nový spúšťač. Bez siete vám *Aktualizácia softvéru* oznámi
  *Nepripojené*. Každý kľúč konzoly sa dá aktualizovať aj z PC pomocou `AutoBleemInstaller.exe` (oddiel 2.1).

### 3.13 Rozšírenia a AutoBleem Store

**Rozšírenia** pridávajú do spúšťača nové veci - vlastné obrazovky a funkcie - bez toho, aby menili samotný
AutoBleem. AutoBleem Store aj PSC-Bios sú rozšírenia. Rozšírenie sídli v `Extensions/<názov>/` na kľúči (na
Raspberry Pi na jeho dátovom oddiele, vo Windows v dátovom priečinku); nainštalujete ho tak, že tam rozbalíte jeho
zip.

Ak ich chcete vidieť, otvorte systémovú ponuku (**L2 + R2**) a vyberte *Rozšírenia*. Tie od tímu AutoBleem sú
hore, všetky ostatné nasledujú pod nadpisom *Rozšírenia tretích strán*. Cross vybrané rozšírenie spustí
a Triangle ho vypne, prípadne znova zapne. Výnimkou je PSC-Bios na konzole: nastavujete ním WiFi, ovládače
a hodiny, preto sa tam vypnúť nedá. Keď sa rozšírenie nedá spustiť, jeho riadok vám povie prečo - potrebuje sieť
a žiadna nie je, nie je urobené pre tento systém, bolo urobené pre inú verziu AutoBleemu a potrebuje aktualizáciu,
alebo sa ho nepodarilo načítať. Ak by niektoré rozšírenie niekedy zastavilo spúšťač, AutoBleem ho vypne a zoznam
vám to povie; tu ho môžete znova zapnúť.

![Zoznam Rozšírení](../images/en/extensions.jpg)

**AutoBleem Store** je prvé rozšírenie: miesto, kde si prezriete aplikácie a hry a jedným stlačením ich
nainštalujete, na každom systéme, na ktorom AutoBleem beží. PlayStation Classic preň potrebuje jadro AutoBleem,
pretože WiFi prichádza s jadrom. Otvoríte ho z Rýchlej ponuky (*Obchod*, oddiel 3.4). Má štyri karty a L1 a R1
medzi nimi prepínajú.

Karty **Apps** a **Games** ukazujú, čo zdroje ponúkajú, pri každej položke jej obrázok, verziu, veľkosť a malú
ikonu zdroja, z ktorého pochádza. Na karte Apps sú aj PE aplikácie s licenciou a zdrojom a balíky s hernými dátami
(oddiel 3.10). To, čo už máte nainštalované, nesie odznak *Installed*. Lišta s nápovedou ukazuje tlačidlá, ktoré
platia pre vybraný riadok:

| Tlačidlo | Na kartách Apps a Games |
|---|---|
| Cross | Nainštaluje položku - alebo ju aktualizuje, skúsi to znova po neúspechu, prípadne zruší sťahovanie, ktoré čaká alebo beží. |
| Triangle | Odstráni niečo, čo nainštaloval Obchod. |
| Square | Obnoví zoznamy zo zdrojov. |
| L2 / R2 | Skočia na predchádzajúce alebo nasledujúce začiatočné písmeno. |
| Select | Ukazuje naraz iba jeden zdroj, keď chcete vidieť, čo ponúka práve on. |
| Start | Vyhľadáva v názvoch. |

Obrázky sa po načítaní uchovajú, takže sa zoznamy nabudúce objavia rýchlo, a obrázok, ktorý sa nenačítal, sa dá
skúsiť znova.

Karta **Downloads** ukazuje, čo sa sťahuje, čaká, zlyhalo alebo je nainštalované, s ukazovateľom priebehu, ktorý
sa posúva plynulo. Sledovať ho nemusíte: sťahovanie pokračuje na pozadí aj po odchode z Obchodu, a kým ste inde
v spúšťači, bublina ukazuje bežiace sťahovanie s rýchlosťou a zostávajúcim časom (napríklad `1.4 MB/s · 0:42`).
Spustenie hry alebo vypnutie sťahovanie iba pozastaví a zastavené sťahovanie pokračuje tam, kde prestalo. Ak
vypadne sieť, položka hlási *Waiting for the network* a po návrate siete pokračuje tam, kde bola; po 30 minútach
bez siete to vzdá. Sťahovanie väčšie ako 2 GB funguje na každej platforme vrátane 32-bitových zostavení. Hra,
ktorú nainštalujete, sa objaví na polici po ďalšom skenovaní a ako obal dostane obrázok z Obchodu.

Karta **Sources** ukazuje, odkiaľ zoznamy pochádzajú, každý so svojou ikonou: vlastný katalóg AutoBleemu, každý
zoznam TSV nahraný do `System/Extensions/store/sources/` a adresy, ktoré si pridáte sami cez *Add a source URL*.
Cross na zdroji, ktorý ste pridali, vám ho dovolí premenovať, zmeniť jeho adresu, prepnúť ho medzi `http://`
a `https://` alebo ho odstrániť.

![Karta Apps v Obchode](../images/en/store-apps.jpg)

![Ponuka zdroja, ktorý ste pridali](../images/en/store-source-menu.jpg)

To, čo ponúka vlastný katalóg AutoBleemu, je vypísané aj na webe so stiahnutiami, na adrese
`https://autobleem.retromenele.pl/store/`. Zdroj, ktorý si pridáte sami, je iná vec: **za obsah zdrojov, ktoré
pridáte, zodpovedáte vy.**

**Vlastné hry vo vašej sieti.** Ak máte hry z PS1 uložené na inom počítači doma, `abstored`, LAN server Obchodu,
ich môže ponúknuť Obchodu cez vašu sieť a vy ich nainštalujete ako ktorúkoľvek inú položku. Beží na akomkoľvek
stroji s Linuxom - na Raspberry Pi, na domácom serveri - a priečinok iba číta, nikdy ho nemení. Spustite ho
príkazom `abstored <priečinok s hrami>` a potom v prehliadači otvorte `http://<ten stroj>:8124/`: stránka ukáže,
čo poskytuje, a problémy, ktoré našiel. V Obchode pridajte ako zdroj `http://<ten stroj>:8124/store.tsv`. Hotové
programy pre Linux a Windows sú na stránke Obchodu, na jej karte **LAN server**, a `INSTALL-linux.md`
(`ext_store/server/` v zdrojovom kóde) vysvetľuje, ako ho nastaviť ako službu. **LAN Share** (oddiel 5.2) dáva
na taký server hry a disky z PC.

### 3.14 Procesory skenovania

Procesory skenovania pripravia vaše hry ešte predtým, ako ich AutoBleem načíta. Procesor je malý program, ktorý
každé skenovanie spustí ako prvý. Dokáže previesť formát, ktorý AutoBleem nečíta, na taký, ktorý číta - napríklad
rozbaliť zazipovanú hru - alebo zmeniť dáta hry, napríklad použiť prekladovú záplatu. Procesory sídlia
v `System/Processors/<názov>/` na kľúči (na Raspberry Pi na jeho dátovom oddiele, vo Windows v dátovom
priečinku); nainštalujete ho tak, že tam rozbalíte jeho priečinok, a ďalšie skenovanie ho spustí.

**Unzip prichádza s AutoBleemom.** Rozbalí zazipované hry z PS1 v `Games/` skôr, ako ich skenovanie načíta,
a zazipované ROMky po jednej; arkádové sady zostanú zazipované, pretože tak ich arkádové jadrá čítajú.
Aktualizácia AutoBleemu aktualizuje aj Unzip, a ak ste ho vypli, zostane vypnutý.

Procesor svoju prácu urobí raz: keď sa s hrou vysporiada, znova ju spracuje až vtedy, keď sa hra zmení. Kým
procesor pracuje, bublina vpravo hore ukazuje, čo robí, a varovanie alebo zlyhanie sa objaví v riadku pod ňou;
podrobnosti nájdete v `processors.log` v priečinku s logmi. Spustenie hry alebo RetroArch zastaví procesor, ktorý
mení súbory, aby mala hra stroj iba pre seba, a prácu dokončí ďalšie skenovanie.

Ak ich chcete spravovať, otvorte systémovú ponuku (**L2 + R2**) a vyberte *Procesory skenovania*. Vidíte ich
v poradí, v akom bežia, s jednou kartou pre hry z PS1 a jednou pre ROMky; L1 a R1 medzi kartami prepínajú. Na
poradí záleží: procesor, ktorý rozbaľuje, musí byť pred tým, ktorý záplatuje rozbalené.

| Tlačidlo | V Procesoroch skenovania |
|---|---|
| Square | Vybraný procesor zdvihne, takže ho Hore a Dole presuniete na nové miesto; Square ho znova položí. |
| Cross | Procesor vypne alebo znova zapne. |
| Triangle | Pri ďalšom skenovaní nechá procesor znova prejsť všetky hry, aj tie, ktoré už spracoval. |
| Circle | Vráti sa späť, a ak ste niečo zmenili, spustí skenovanie. |

Procesor, ktorý bol zostavený pre iný stroj, zostane v zozname sivý, aby ste videli, že tam je, ale že tu
nebeží.

![Procesory skenovania](../images/en/processors.jpg)

Ak chcete napísať vlastný procesor, stránka procesora Unzip, `https://github.com/autobleem2/proc_unzip`, vysvetľuje
všetko, čo procesor musí robiť, a `tools/proc_check.py` v zdrojovom kóde AutoBleemu ten váš skontroluje skôr, ako
ho budete zdieľať.

<!-- pagebreak -->

## 4. Obrazovky

### 4.1 Správca hier

V Správcovi hier si upratujete knižnicu hier z PS1. Použite ho, keď chcete odstrániť hru, ktorú už nehráte,
otvoriť nastavenia hry bez toho, aby ste ju najprv hľadali na polici, alebo prinútiť AutoBleem stiahnuť všetky
obaly znova. Otvoríte ho zo systémovej ponuky (L2 + R2, *Správca hier*). Počas skenovania je sivý a počká, kým
sa skenovanie skončí.

Obrazovka má nadpis *Správca hier - vybrať hru*. Vľavo vidíte všetky hry z PS1 ako zoznam názvov v abecednom
poradí, vpravo obal vybranej hry s vydavateľom, rokom, sériovým číslom a priečinkom, v ktorom je. Vpravo hore je
voľné miesto na jednotke, takže vidíte, koľko miesta vám zmazanie vráti. Hore a Dole sa pohybujete po zozname,
L2 / R2 listujú po stranách a L1 / R1 skočia na prvú alebo poslednú hru.

- **Cross** otvorí vybranú hru v editore hry - v tom istom editore ako ikona Hra na polici (oddiel 3.7). Keď z
  neho odídete, ste späť na tej istej hre v zozname.
- **Square hru zmaže.** AutoBleem sa najprv opýta a potom odstráni celý priečinok hry. Ak uložené pozície
  a pamäťovú kartu hry nepoužíva žiadna iná hra, položí ešte druhú otázku: či zmazať aj tie. Odpovedzte nie, ak by
  ste sa k hre možno neskôr chceli vrátiť aj s uloženými hrami.
- **Triangle zmaže všetky obrázky obalov** (PNG alebo JPEG), ktoré ležia vedľa vašich hier, po otázke. Hodí sa to,
  keď ste nazbierali obaly, ktoré sa vám nepáčia: ďalšie skenovanie si vezme obaly z databáz obalov znova.

Na konci zoznamu, za hrami, môžete vidieť priečinky označené *Nepridané*. Sú to priečinky v `Games`, ktoré si
skenovanie prezrelo, ale nedokázalo z nich urobiť hru. Vyberte jeden a pravá strana vám povie, kde je a prečo
nebol pridaný - napríklad chýba súbor cue (kapitola 7). Square taký priečinok po otázke zmaže. Keď po nejakej
zmene odídete cez Circle, AutoBleem hry znova prehľadá.

![Správca hier: zoznam hier vľavo, obal a podrobnosti vybranej hry vpravo](../images/en/game-manager.jpg)

### 4.2 Informácie o hardvéri

Informácie o hardvéri sú stránka, na ktorú sa pozriete, keď chcete vedieť, čo je váš stroj zač a čo vidí: koľko
miesta zostáva na kľúči, akú má sieťovú adresu, aké ovládače obrazu a zvuku používa a ktoré ovládače sú
pripojené. Na každej platforme vrátane konzoly je to tá istá stránka. Otvoríte ju zo systémovej ponuky (L2 + R2,
*Informácie o hardvéri*); Circle vás vráti do systémovej ponuky.

Stránka ukazuje systém, hardvér, úložisko s voľným miestom, sieťové adresy, ovládače obrazu a zvuku a pripojené
ovládače. Všetko znova načíta každú sekundu, takže ju môžete nechať otvorenú, zapojiť ovládač alebo kábel
a sledovať, ako sa zmena objaví. Iba zobrazuje - sieť alebo ovládač nastavíte v *Sieť a ovládače* (PSC-Bios,
kapitola 6).

Časť o ovládačoch odpovedá na otázku „ktorý ovládač je ktorý hráč?". Prvé dva ovládače sú uvedené ako *Hráč 1*
a *Hráč 2* - porty, ktoré im dá emulátor PS1. Každý ďalší ovládač je uvedený ako *nepoužíva ho PS1 emulátor*.
RetroArch rozdeľuje porty podľa vlastných nastavení, takže v hre z RetroArch môže byť poradie iné. Túto stránku
nemusíte otvárať zakaždým: kedykoľvek ovládač zapojíte alebo vytiahnete, spúšťač nakrátko ukáže, ktorý ovládač je
teraz hráč 1 a ktorý hráč 2.

![Informácie o hardvéri: údaje o stroji a pripojené ovládače](../images/en/hardware-info.jpg)

### 4.3 Prehľad tlačidiel

Ak niekde zabudnete, čo robí niektoré tlačidlo, stlačte na polici **Triangle**. Prehľad tlačidiel ukáže všetky
tlačidlá všetkých obrazoviek na jednej stránke, takže si ich pozriete bez toho, aby ste opustili spúšťač. Ak je
pripojená USB klávesnica, alebo bola použitá, stĺpec *Klávesnica* ukazuje pri každom tlačidle ovládača zodpovedajúci
kláves.

Prehľad vám pripomenie aj jedinú vec, ktorú sa oplatí pamätať pri každej hre: ako z nej odísť. Podržte Select +
Start alebo Home na 2 sekundy a vrátite sa do AutoBleemu; krátke stlačenie namiesto toho otvorí ponuku emulátora.

![Prehľad tlačidiel: tlačidlá všetkých obrazoviek a vedľa nich klávesy klávesnice](../images/en/button-guide.jpg)

### 4.4 Klávesnica na obrazovke

Kedykoľvek od vás AutoBleem potrebuje, aby ste niečo napísali - názov sady pamäťových kariet, názov hry, heslo
k WiFi, adresu zdroja v Obchode - objaví sa tá istá klávesnica na obrazovke, takže píšete iba ovládačom. Je
rozložená ako klávesnica v telefóne. Okrem písmen má stránku so symbolmi, s `/ \ : ? & = % @ #` a všetkým
ostatným, čo adresa alebo heslo potrebuje, a dve stránky písmen s diakritikou. V spodnom riadku sú Shift, kláves,
ktorý prepína stránky, medzera, Backspace a potvrdenie.

Po klávesoch sa pohybujete smermi a stlačením **Cross** napíšete ten pod kurzorom. **Triangle** zmaže písmeno
a **Square** napíše medzeru. **L1** je Shift; dvojitým stlačením zapnete veľké písmená natrvalo. **R1** prejde na
ďalšiu stránku klávesov a **L2 / R2** posúvajú kurzor v texte. **Start** potvrdí, čo ste napísali, a **Circle**
zruší. Ak je pripojená USB klávesnica, môžete kedykoľvek písať na nej: Enter potvrdí a Esc zruší.

![Klávesnica na obrazovke](../images/en/keyboard.jpg)

### 4.5 Virtuálny gamepad

Aplikácie - programy v sade Aplikácie, napríklad Doom alebo Quake - nečítajú váš ovládač samy. Malý pomocný
program, démon virtuálneho gamepadu, číta skutočné ovládače a každej aplikácii podá ovládač, ktorému rozumie. Táto
stránka vám ukáže, ktoré ovládače tento pomocník vidí a ako ich číta. Pozrite sa sem, keď aplikácia na váš ovládač
nereaguje alebo má poprehadzované tlačidlá. Otvoríte ju zo systémovej ponuky (L2 + R2, *Virtuálny gamepad*);
Circle vás vráti do systémovej ponuky.

Pod nadpisom *Ovládače viditeľné pre démona* je každý ovládač uvedený s číslom a menom. Vedľa neho si prečítate
tri veci: či ho pomocník dokázal otvoriť (*pripojené*) alebo nie (*nečitateľné*); ovládač systému, cez ktorý
prišiel; a odkiaľ pochádza rozloženie jeho tlačidiel - *z databázy ovládačov* znamená, že ovládač je známy
a tlačidlá má tam, kde majú byť, *odhadnuté démonom* znamená, že známy nie je a pomocník ho odhadol, ako najlepšie
vedel. Ak sa tlačidlá v aplikácii správajú zle, odhadnuté rozloženie je pravdepodobnou príčinou.

Pomocník beží iba vtedy, keď beží aplikácia, preto sa ho stránka pri otvorení opýta raz. Ak počas otvorenej
stránky zapojíte ovládač, stlačte **Cross** (*Skontrolovať znova*) a stránka sa opýta znova. Vo Windows taký
pomocník nie je a stránka hlási *Nie je v tomto zostavení*.

![Virtuálny gamepad: ovládače, ktoré vidí pomocník aplikácií](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. Na PC

### 5.1 UpdateRoms - obnovenie kľúča konzoly

Na Raspberry Pi, PC alebo vo Windows triedi skenovanie spúšťača hry z RetroArch do zoznamov a obaly k nim sťahuje
samo. PlayStation Classic to nedokáže, pretože nemá vlastnú sieť. **UpdateRoms** urobí túto prácu namiesto nej na
vašom PC s Windows: použije sieť počítača, ale všetko zapíše s cestami, ktoré čaká konzola, takže keď kľúč vrátite,
konzola nabehne a všetko nájde na svojom mieste. Spustite ho vždy, keď na kľúči konzoly pridáte alebo odstránite
hry z RetroArch.

1. Nakopírujte ROMky na kľúč do `RetroArch/roms/<systém>/` (oddiel 3.10). Názvy priečinkov musia byť názvy
   z databázy RetroArch; tie bežné už inštalátor vytvoril.
2. Spustite **`UpdateRoms\UpdateRoms.exe` priamo z kľúča** - umiestnil ho tam inštalátor. Sám zistí, na ktorom
   kľúči je. Počas práce vidíte riadok s tým, čo práve robí, ukazovateľ priebehu a záznam.
   - Ak na kľúči ešte nie je databáza RetroArch, najprv stiahne balík databáz RetroArch. Potom podľa neho
     identifikuje každú ROMku, takže hra, ktorú databáza pozná, dostane správny názov.
   - Do `RetroArch/bin/playlists/` zapíše jeden playlist pre každý systém, s cestami konzoly. Všetko, čo do týchto
     zoznamov pridal samotný RetroArch, zostane.
   - Pre každú ROMku bez obalu stiahne obal zo serverov náhľadov libretro do `RetroArch/bin/thumbnails/`.
3. Kľúč bezpečne odoberte a vráťte ho do konzoly. Karta RetroArch vo výbere sady teraz ukazuje každý systém,
   ktorý má hry.

Spúšťať ho môžete, koľkokrát chcete: priečinok, v ktorom sa nič nezmenilo, preskočí, takže druhé spustenie je
rýchle. Ak sa niečo pokazí, log je na kľúči v `System/Logs/updateroms.log`. Kartu z Raspberry Pi v čítačke kariet
obnovíte rovnako, príkazom `UpdateRoms.exe <jednotka> --target rpi`, hoci Pi to so sieťou zvládne aj samo.

### 5.2 LAN Share - vaše hry a disky na serveri vo vašej sieti

Obchod vie inštalovať hry zo servera vo vašej domácej sieti (oddiel 3.13). **LAN Share** je program pre Windows,
ktorý tento server plní z vášho PC: dá naň hry z PS1, ktoré máte na počítači, a dokáže prečítať aj disk PS1
v mechanike CD/DVD počítača a dať naň aj ten. Serverom je `abstored` bežiaci na Raspberry Pi, NAS alebo inom PC.
Keď je hra na ňom, Obchod na konzole, Pi alebo PC ju odtiaľ môže nainštalovať.

`LanShare.exe` získate na stránke Obchodu, na jej karte **LAN server**. Nič sa neinštaluje: spustite ho a svoje
nastavenia si uchováva v `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![Okno LAN Share: hry na serveri vľavo, hry na tomto PC vpravo](../images/en/lanshare.jpg)

1. **Pripojte sa k serveru.** Zadajte jeho adresu tak, ako ju má Obchod, `http://<jeho adresa>:<port>`, a stlačte
   **Connect**. Vľavo sa objavia hry, ktoré už na serveri sú, a problémy, ktoré našlo jeho vlastné skenovanie.
   Aby LAN Share mohol na server dávať hry, potrebuje jednu z dvoch ciest:
   - **Share** je priečinok s hrami servera zdieľaný vo vašej sieti (Samba), napríklad `\\raspberrypi\games`.
     LAN Share doň hry skopíruje a požiada server, aby ich prehľadal; samotný server svoj priečinok stále iba
     číta.
   - **Token** je pre server spustený s `--allow-uploads`. Zadajte jeho token - server ho pri štarte vypíše
     a uchováva ho v `<state>/upload-token`. LAN Share potom nahráva cez HTTP a nahrávanie, ktoré sa v polovici
     zastaví, pokračuje tam, kde prestalo.
2. **Zverejnite hry zo svojho PC.** Vyberte priečinok, v ktorom máte hry (každú vo vlastnom priečinku), zaškrtnite
   tie, ktoré chcete, a stlačte **Publish the ticked games**. Stĺpec **On the server** vám povie, či server hru už
   má - porovnáva sériové číslo, alebo názov, keď sériové číslo chýba - a hru, ktorú server má, nikdy nepošle
   dvakrát. **Tick those not on the server** za vás zaškrtne všetky ostatné.
3. **Zverejnite disk.** Vložte disk PS1 do mechaniky počítača a stlačte **Read a disc and publish it**. LAN Share
   prečíta celý disk do `.bin` + `.cue` pomenovaných podľa názvu hry. Pri hre s LibCrypt zapíše aj súbor `.sbi`,
   ak mechanika dokáže čítať subkanál. Ak ste zvolili databázy (nižšie), overí kópiu podľa známeho dobrého
   dumpu. Potom hru zverejní. Pri hre na viacerých diskoch najprv zaškrtnite **The game has more than one disc**:
   LAN Share si postupne vypýta každý ďalší disk a zverejní ich spolu ako jednu hru.
4. **Odoberte hry zo servera.** Vyberte ich a stlačte **Remove from the server...**. Nič sa nezmaže: každá hra sa
   presunie do priečinka `.removed` vedľa hier servera a keď ju presuniete späť, je tam znova.

**Databases** sú voliteľné. Ak LAN Share nasmerujete na priečinok s obalmi AutoBleemu (`coversU/P/J.db`) a na
`Sony - PlayStation.rdb` z RetroArch, použije ich na pomenovanie hier a na overenie disku, ktorý prečítal.

Ak by ste radšej nič nekopírovali, zaškrtnite **Also share the games on this PC with the Store** (predvolene je
vypnuté): LAN Share potom poskytne Obchodu priečinok s hrami na vašom PC priamo. Keď to urobíte prvýkrát, Windows
sa opýtajú na bránu firewall - povoľte iba súkromné siete.

<!-- pagebreak -->

## 6. Nástroje konzoly (PlayStation Classic)

S kľúčom pre PlayStation Classic prichádzajú dva nástroje, ktoré vám pomôžu nastaviť konzolu nad rámec toho, čo
vie hneď po vybalení. Oba vyzerajú ako zvyšok spúšťača, v jeho téme a jazyku, a ovládate ich ovládačom - v sprievodcovi
mapovaním ovládača aj prednými tlačidlami konzoly. **PSC-Bios** je rozšírenie, ktoré prichádza s balíkom pre
konzolu: otvára ho položka *Sieť a ovládače* v Rýchlej ponuke aj v systémovej ponuke a nájdete ho aj v zozname
Rozšírení. **ABFlashKit** je aplikácia, v sade Aplikácie.

### 6.1 PSC-Bios

V PSC-Bios pripájate stroj k svetu: k vašej sieti WiFi, k časovému pásmu, k ovládačom cez Bluetooth a nastavujete
v ňom rozloženie tlačidiel ovládača, ktorý AutoBleem nepozná. Prichádza s balíkom pre konzolu a je aj na Raspberry
Pi a PC kľúči. Otvoríte ho položkou *Sieť a ovládače* v systémovej ponuke (alebo v Rýchlej ponuke) alebo zo
zoznamu Rozšírení. Ak je rozšírenie nainštalované, ale vypnuté, položka *Sieť a ovládače* je sivá a hlási, že
*je vypnuté - zapnite ho v Rozšíreniach*; stlačte na nej Cross a zoznam Rozšírení sa otvorí priamo na PSC-Bios,
takže ho môžete znova zapnúť.

Prvá obrazovka vám dá prehľad: čas a časové pásmo, sieťové adaptéry (WiFi, Ethernet, Bluetooth) s ich adresami
a každý pripojený ovládač s poznámkou, či má mapovanie tlačidiel. Na konzole potrebujú časti pre sieť a Bluetooth
jadro AutoBleem (oddiel 6.2); na Raspberry Pi alebo PC kľúči používajú vlastné nástroje systému. Sprievodca
mapovaním ovládača funguje všade.

![PSC-Bios: rozcestník Sieť a ovládače](../images/en/pscbios-main.jpg)

Z prvej obrazovky vás do každej časti dostane jedno tlačidlo:

| Tlačidlo | Čo otvorí |
|---|---|
| Select | **Wi-Fi Network** vás pripojí k vašej WiFi (cez jadro, na Pi alebo PC cez NetworkManager): napíšte názov siete alebo ju vyberte z vyhľadaných, zadajte heslo, zvoľte režim ovládača a stlačte *Apply / Restart Network*. Nastavujete tu aj časové pásmo, a keď ste pripojení, vidíte IP adresu konzoly. |
| Square | **Bluetooth Controllers** vyhľadá ovládače cez Bluetooth, napríklad DualShock 4, aby ste mohli spárovať nový alebo odstrániť ten, ktorý už nepoužívate. |
| L1 | **DualShock 3 Pairing** pripojí váš prvý DualShock 3, ktorý na to musí byť zapojený cez USB, pomocou pluginu sixaxis v jadre. |
| R1 | **Controller Mapping** otvorí sprievodcu mapovaním ovládača, popísaného nižšie. |
| Triangle | **About** ukáže, čo je PSC-Bios. |
| Circle | **Back** vás vyvedie z PSC-Bios späť do spúšťača. |

**Sprievodca mapovaním ovládača.** Použite ho, keď ovládač v AutoBleeme nerobí nič alebo má tlačidlá na zlých
miestach. Ukáže pripojený ovládač taký, aký naozaj je - každú os, tlačidlo a smerový prepínač ako čísla - a obrázok
DualShocku, ktorý sa rozsvecuje, ako stláčate. Keďže testovanému ovládaču sa ešte nedá veriť, sprievodcu ovládate
**prednými tlačidlami** konzoly: **RESET** prepne na ďalší ovládač, **OPEN** spustí mapovanie a **POWER** zruší
alebo odíde. Počas mapovania si sprievodca pýta jedno tlačidlo za druhým: stlačte tlačidlo, ktoré svieti na
obrázku, alebo OPEN, ak váš ovládač také tlačidlo nemá. Krátke stlačenie sa namapuje ako obvykle.

Odísť môžete aj z ovládača: podržte Circle na 2 sekundy - naplní sa pruh a spodná lišta hlási *Hold 2 s: Exit*.
Kým ovládač ešte nemá mapovanie, to isté urobí podržanie ľubovoľného tlačidla na 2 sekundy (*Hold any button 2 s:
Exit*). Na klávesnici zastupujú POWER, RESET a OPEN klávesy Esc, medzerník a Enter.

Na konci sa nové mapovanie začne používať, aby ste si ho mohli vyskúšať, a OPEN ho uloží pod menom, ktoré si
zvolíte. Odvtedy ho spúšťač načíta zakaždým.

![PSC-Bios: sprievodca mapovaním ovládača](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - jadro AutoBleem

Jadro AutoBleem nahrádza vlastné linuxové jadro konzoly a je voliteľné. Oplatí sa, ak od konzoly chcete viac: dá
jej fungujúce hodiny, rozbehne USB adaptéry WiFi a Bluetooth (pre PSC-Bios a ovládače cez Bluetooth) a pridá
podporu predných tlačidiel, ktorú emulátor používa pre body obnovenia. ABFlashKit je nástroj, ktorý ho
nainštaluje. Najprv konzolu zálohuje a dokáže ju aj vrátiť do továrenského stavu cez vlastnú obnovu od Sony.

> **Tento nástroj zapisuje do flash pamäte konzoly.** Ak sa zápis preruší - vypadne prúd alebo vytiahnete kľúč -
> konzola sa už nemusí spustiť, a inštaláciou vlastného jadra prichádzate o záruku. Nechajte konzolu napájanú
> a kľúč zasunutý, kým sa konzola sama nereštartuje. ABFlashKit sa otvorí s týmto varovaním: *I understand*
> pokračuje, *Quit* odíde.

![Ponuka ABFlashKit](../images/en/abflashkit-menu.jpg)

ABFlashKit má tri akcie:

- **Flash Kernel** nainštaluje jadro. Ak na kľúči ešte nie je záloha na obnovu, najprv ju z oddielov konzoly
  vytvorí (`LBOOT.EPB`). Skontroluje zálohu a obraz jadra, zapíše jadro a systémové súbory AutoBleemu a konzolu
  reštartuje. Keď sa objaví *All done - when the screen goes black replace power cord*, počkajte, kým obrazovka
  sčernie, potom vytiahnite napájací kábel konzoly a znova ho zapojte.
- **Full backup** uloží všetky štyri oddiely konzoly do `LBOOT.EPB`, aby ste ich mohli neskôr obnoviť. Ak už záloha
  existuje, pred prepísaním sa opýta.
- **Restore Mode** je cesta späť k továrenskému firmvéru. Overí, že záloha na kľúči je továrenská, nastaví príznak
  obnovy a reštartuje konzolu do obnovy od Sony, ktorá konzolu obnoví z `LBOOT.EPB`.

Pod každým krokom ukazuje ukazovateľ priebehu, ako ďaleko je. ABFlashKit nenahrá jadro do konzoly, na ktorej beží
iný vlastný firmvér, napríklad BleemSync alebo Project Eris: takú konzolu najprv vráťte do továrenského stavu.

**Prihlásenie z PC.** Ak sa vyznáte v Linuxe a chcete sa pozrieť do vnútra konzoly, môžete sa na ňu prihlásiť z PC
cez USB kábel. Vyžaduje to jadro AutoBleem; na konzole v továrenskom stave to nefunguje.

1. Prepojte port micro-USB konzoly s PC USB káblom. PC uvidí konzolu ako nový sieťový adaptér a adresu konzoly
   nájdete v nastaveniach tohto adaptéra na PC.
2. Prihláste sa príkazom `ssh root@<adresa konzoly>`. Predvolené heslo je `autobleem`.

Namiesto hesla môžete použiť kľúč. Svoj verejný kľúč dajte do súboru `System/ssh/authorized_keys` na USB kľúči
a konzolu reštartujte: pri ďalšom štarte sa pridá k účtu root. Aktualizácia ani preinštalovanie spúšťača ho
neodstráni.

> **Predvolené heslo je na každej konzole rovnaké**, takže ktokoľvek, kto do vašej zapojí kábel, sa môže
> prihlásiť ako root. Kde sa dá, použite kľúč, a konzolu s predvoleným heslom nenechávajte tam, kde sa k nej
> dostanú iní.

<!-- pagebreak -->

## 7. Keď niečo nefunguje

Väčšina problémov má jednoduchú príčinu. Každý z nich nižšie začína tým, čo vidíte, vysvetlí, prečo sa to deje,
a potom, čo robiť. Ak budete potrebovať pomoc, ako prvé od vás budú chcieť logy, a preto sú tu na začiatku.

**Kde nájsť logy.** AutoBleem si počas behu drží logy v pamäti, aby sa na kľúč nezapisovalo neustále. Do
`System/Logs/` na kľúči, karte alebo v dátovom priečinku sa dostanú iba vtedy, keď sa niečo pokazilo: keď spadne
spúšťač, hra z PS1 alebo RetroArch, logy sa uložia do `System/Logs/crash-<n>/` (uchovávajú sa posledné tri pády)
a spúšťač vám to po návrate raz oznámi. Ak pátrate po probléme, ktorý nie je pádom, uchovávajte všetky logy:
zapnite Možnosti → *Diagnostika* → *Uchovávať logy na kľúči:* (platí od ďalšieho štartu), alebo z PC vytvorte
prázdny súbor `System/Logs/keep`. *Informácie o hardvéri* (oddiel 4.2) tiež ukazujú, kde logy sú, a Square tam
uloží aktuálne logy do `System/Logs/saved-<n>/`.

Nájdete tieto súbory:

| Súbor | Čo z neho zistíte |
|---|---|
| `autobleem.log` | Čo robil samotný spúšťač. |
| `launch.log`, `pcsx.log` | Ako sa hra z PS1 spúšťala a čo hlásil emulátor, kým bežal. |
| `retroarch.log` | Čo hlásil RetroArch, kým bežal. |
| `update.log` | Ako prebehla online aktualizácia; na kľúči sa uchováva vždy. |
| `updateroms.log` | Ako prebehol UpdateRoms na PC (kapitola 5); na kľúči sa uchováva vždy. |

**Obrázok vás žiada, aby ste vložili kľúč, alebo konzola zaspala.** AutoBleem nevie nájsť svoj kľúč: pri štarte
konzoly v nej žiadny nebol, alebo ho niekto vytiahol. Zasuňte ho do ktoréhokoľvek USB portu (najlepšie predného,
oddiel 2.1) skôr, ako uplynie 5 minút, alebo stlačte Power. Ak kľúč nebol vybraný čisto, AutoBleem ho najprv
skontroluje - počkajte, kým ukazovateľ priebehu dobehne.

**RetroArch hlási, že *needs a newer system library than this console has*.** Tento RetroArch bol zostavený pre
novší systém, než má konzola, takže na nej nepobeží. Použite RetroArch, ktorý prichádza s AutoBleemom.

**Hra hlási, že *is protected by its PSN license and cannot be started*.** Hry kúpené v PlayStation Network sú
viazané na svoju licenciu a AutoBleem ich spustiť nevie. Nedá sa s tým nič robiť.

**Hra nie je na polici.** Zvyčajne jej priečinok nie je usporiadaný tak, ako skenovanie čaká. Skontrolujte, či má
každá hra vlastný priečinok a je v niektorom z formátov z oddielu 3.10. *Správca hier* (oddiel 4.1) za hrami
ukazuje priečinky, ktoré skenovanie odmietlo, označené *Nepridané*, a pri každom povie prečo; Square taký priečinok
zmaže. Keď priečinok opravíte, *Znova skenovať hry* v systémovej ponuke spustí skenovanie znova.

**Hry nemajú obaly.** Buď sa nenainštalovali databázy obalov - spustite inštalátor znova a zaškrtnite ich - alebo,
pri hrách z RetroArch na konzole, ste ešte na PC nespustili UpdateRoms (kapitola 5).

**Ovládač nerobí nič alebo má poprehadzované tlačidlá.** AutoBleem nepozná rozloženie tohto ovládača. Na konzole
ho namapujte sprievodcom mapovaním ovládača v PSC-Bios (oddiel 6.1). Na Pi alebo PC ukáže stránka Informácie
o hardvéri (oddiel 4.2), čo systém z ovládača vidí, a pomôže vám zistiť, či ho vôbec rozpoznal.

**Po hre na konzole zostane obrazovka čierna.** Keď hra skončila, obraz spúšťača sa nevrátil. AutoBleem svoje okno
obnoví sám, až trikrát. Ak obrazovka aj potom zostane čierna, podržte tlačidlo Power a konzolu znova zapnite.

**Na Raspberry Pi** sa v prípade potreby dostanete za spúšťač: `Alt+F2` vám dá prihlasovaciu výzvu na druhej
konzole a SSH je zapnuté od prvého štartu. `sudo journalctl -u autobleem` ukáže, čo robila služba spúšťača,
a `sudo systemctl restart autobleem` ju reštartuje. Ak sa prvý štart nemohol dokončiť pre chýbajúcu sieť, skúsi to
znova pri ďalšom štarte.

**Vo Windows** spúšťač opustíte klávesom `Esc`. Váš dátový priečinok je ten, ktorý ste si zvolili pri inštalácii
(`Documents\AutoBleem`, ak ste ho nezmenili), a logy sú v jeho priečinku `System\Logs`.

**Konzola sa po online aktualizácii stále dokola reštartuje (kľúč naformátovaný ako ext4).** Niektorí ľudia
formátujú kľúč ako ext4, súborový systém Linuxu, namiesto FAT32 alebo exFAT. Až do ďalšieho vydania AutoBleemu
rozbalí online aktualizácia na takom kľúči každý súbor bez povolenia, ktoré mu dovoľuje bežať ako program.
AutoBleem sa potom nemôže spustiť a konzola sa reštartuje znova a znova. Kľúčov s FAT32 a exFAT sa to netýka.
Opraviť sa to dá dvoma spôsobmi.

**Oprava A** potrebuje PC s Linuxom. Zapojte kľúč a programom AutoBleemu vráťte povolenie na spustenie. Namiesto
`/media/USER/STICK` použite vlastnú cestu, kam je kľúč pripojený; posledný riadok potrebujete iba vtedy, ak je
nainštalovaný RetroArch:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Oprava B**: nainštalujte na kľúč znova najnovšie vydanie AutoBleemu, ako v oddiele 2.1. Inštalátor potrebuje PC,
ktoré kľúč dokáže prečítať. Ak ten váš prečítať nedokáže, kľúč treba najprv naformátovať, čo z neho zmaže všetko -
predtým si z neho skopírujte hry.

> Aby sa vám to nestalo, používajte **FAT32** (konzola v továrenskom stave číta iba FAT32; exFAT potrebuje jadro
> AutoBleem, kapitola 6). Ďalšie vydanie povolenia zachová a AutoBleem ich pri každom štarte opraví.

AutoBleem je slobodný softvér (GNU GPL v3 alebo novšia) a neposkytuje sa naň žiadna záruka. Podporu a novinky
nájdete na serveri Discord, na ktorý odkazuje obrazovka O programe, alebo na https://autobleem.retromenele.pl/.
