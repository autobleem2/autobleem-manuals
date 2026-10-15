# Manual de utilizare AutoBleem 2

AutoBleem 2 este un lansator de jocuri pentru **PlayStation Classic** și, începând cu versiunea 2, și pentru
**Raspberry Pi**, pentru un **PC pornit de pe un stick USB** și pentru **Windows**. Îți arată jocurile PS1 ca pe un
raft cu coperți, fiecare cu imaginea cutiei și detaliile ei, le pornește în emulatorul PCSX inclus și, dacă instalezi
RetroArch alături de el, rulează și jocuri de pe alte sisteme. În acest manual găsești instalarea pe fiecare
platformă, folosirea de zi cu zi și uneltele care vin împreună cu AutoBleem.

> Tot ce ai de descărcat se află pe **https://autobleem.retromenele.pl/**. Pagina e împărțită pe platforme: în
> panoul *Install* al fiecăreia e ceea ce descarci tu; *Build inputs*, de sub el, sunt fișierele pe care
> programele de instalare le iau singure.

## 1. Ce primești

AutoBleem transformă PlayStation Classic-ul tău - sau un Raspberry Pi, un PC mai vechi ori calculatorul cu Windows -
într-o mică consolă de jocuri, cu un meniu ca lumea pentru propriile tale jocuri. Iată ce conține:

- **Lansatorul.** Este ecranul pe care îl vezi imediat după pornire: un raft cu coperțile jocurilor, prin care
  derulezi, iar lângă jocul ales, detaliile lui. De aici pornești jocurile, le împarți în seturi (PlayStation,
  RetroArch, Aplicații), schimbi setările, te ocupi de cardurile de memorie și de salvările de stare și descarci
  aplicații și jocuri din Magazin. Arată și funcționează la fel pe toate platformele.
- **Două emulatoare PS1.** `pcsx-abnxt` este cel actual și cel implicit; `pcsx-ab` este emulatorul clasic, cel
  cu care AutoBleem a venit dintotdeauna. Alegi între ele în Opțiuni. Amândouă folosesc aceleași setări și
  aceleași carduri de memorie, așa că poți trece oricând de la unul la altul fără să pierzi nimic.
- **RetroArch**, dacă vrei și jocuri de pe alte sisteme - NES, SNES, Mega Drive, Game Boy, automate arcade și
  multe altele. Pe nicio platformă nu e obligatoriu. Copiezi ROM-urile, iar AutoBleem le pune în liste și pornește
  fiecare joc cu nucleul potrivit. Poți juca și jocuri PlayStation în RetroArch; nucleul lui *PlayStation 1* stă
  chiar în capul listei de nuclee (secțiunea 3.9). Jocuri precum Doom rulează din propriile tale fișiere de joc,
  aflate într-un folder `Packages` (secțiunea 3.10).
- **Uneltele pentru consolă.** *PSC-Bios* - în meniuri se numește *Rețea și controlere* - configurează WiFi-ul,
  ceasul, controlerele Bluetooth și maparea butoanelor, atât pe consolă, cât și pe un Raspberry Pi și pe stick-ul
  pentru PC. *ABFlashKit* instalează kernelul AutoBleem pe un PlayStation Classic (capitolul 6).
- **UpdateRoms** pentru Windows. PlayStation Classic nu are rețea proprie, așa că acest program pentru PC
  reîmprospătează listele RetroArch și aduce coperțile pentru stick-ul consolei cât timp stick-ul e conectat la PC.

![Lansatorul: raftul cu coperți, detaliile jocului selectat și indicațiile pentru butoane](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Instalare

### 2.1 PlayStation Classic

AutoBleem rulează în întregime de pe un stick USB. În consolă nu se schimbă nimic: scoți stick-ul și consola
merge exact ca înainte. Îți trebuie doar un PC cu Windows, un stick USB (USB 2.0, de cel puțin 8 GB) și consola.

Stick-ul nu trebuie să fie gol și **nu este formatat** decât dacă ceri tu asta: AutoBleem se instalează lângă ce
există deja pe el, iar un stick pe care îl folosești deja cu AutoBleem 1.0 este actualizat pe loc (vezi mai jos).
Pentru o consolă nemodificată, stick-ul trebuie să fie **FAT32**, pentru că kernelul original al consolei nu
citește exFAT. După ce instalezi kernelul AutoBleem (ABFlashKit, capitolul 6), consola pornește și de pe un stick
exFAT, iar așa scapi de limita FAT32 de 4 GB pe fișier.

1. Descarcă **AutoBleemInstaller-<versiune>.zip** din panoul PlayStation Classic al site-ului și dezarhivează-l
   unde vrei. Înăuntru găsești `AutoBleemInstaller.exe` și fișierul README. AutoBleem în sine se descarcă în timpul
   instalării, deci PC-ul are nevoie de conexiune la internet.
2. Conectează stick-ul și pornește `AutoBleemInstaller.exe`. Alege **canalul** - *Release* este versiunea testată
   și alegerea potrivită pentru cei mai mulți, *Testing* este următoarea versiune, cât timp e în testare, iar
   *Nightly* este cea mai nouă versiune de dezvoltare, care s-ar putea să nu meargă - și apoi unitatea stick-ului.
   Rândul de dedesubt îți spune ce versiune de AutoBleem urmează să instalezi și ce se află acum pe stick: *a fresh
   install* (celelalte fișiere de pe stick rămân neatinse) sau *AutoBleem <versiune> is on this stick: it will be
   updated* (jocurile, salvările, cardurile de memorie și setările rămân).
   **Nu e nevoie să formatezi.** Butonul **Format** de lângă unitate e doar pentru un stick nou-nouț, fără sistem
   de fișiere, pentru unul pe care consola nu-l poate citi (NTFS, de exemplu) sau pentru unul pe care vrei să-l
   ștergi complet. Întâi te întreabă, apoi șterge tot de pe stick. Alege acolo FAT32, cu excepția cazului în care
   consola are deja kernelul AutoBleem.
   Apoi bifează ce vrei să instalezi:
   - **Cover databases** - coperțile și descrierile întregii biblioteci PS1, ca jocurile tale să-și primească singure
     coperțile (bifat implicit; cam 300 MB).
   - **RetroArch** - RetroArch cu nucleele lui, aplicații suplimentare (Doom, Quake, Amiga, ...) și resursele
     grafice libretro, pentru jocurile de pe alte sisteme. Debifat implicit; îl poți adăuga mai târziu rulând din
     nou programul de instalare.
   - **BIOS files** - fișierele BIOS de care au nevoie unele nuclee RetroArch ca să pornească (doar împreună cu
     RetroArch).
   - **Sample games** - câteva jocuri homebrew gratuite, ca raftul să nu fie gol la prima pornire.
3. Apasă **Install** și așteaptă. Barele de progres și jurnalul arată fiecare pas. La sfârșit, stick-ul primește
   numele `SONY` și o copie a programului `UpdateRoms` (vezi capitolul 5).
4. Scoate stick-ul în siguranță, conectează-l în **al doilea port USB din față** al consolei (cel din dreapta, al
   jucătorului 2) - primul rămâne liber pentru controler - și pornește consola. În locul meniului original pornește
   AutoBleem. Pentru un al doilea controler folosește un hub USB în portul din față sau un controler Bluetooth.

**Pornirea și oprirea.** Cu stick-ul introdus, consola pornește, clipește din led câteva secunde până observă
AutoBleem și apoi intră în standby înainte să apară ceva pe ecran. E normal: AutoBleem pornește prin mecanismul de
actualizare al consolei, iar mecanismul acesta așa funcționează. Apasă o dată **Power** și apare lansatorul.

Când alegi *Oprire* în meniul sistem sau apeși butonul Power al consolei, consola intră în **standby-ul
AutoBleem**: AutoBleem deconectează întâi stick-ul în siguranță, apoi ledul devine **portocaliu** - semn că totul a
mers cum trebuie. La următoarea apăsare pe Power, lansatorul revine în câteva secunde. **Cât timp ledul e
portocaliu, poți scoate stick-ul** și îl poți pune în PC; Windows nu va cere să-l verifice, pentru că a fost
deconectat corect. Pune-l la loc înainte să apeși Power. Dacă scoți cablul de alimentare al consolei, data
viitoare trece din nou prin standby-ul de pornire. Un led **roșu** înseamnă că consola e oprită de-a binelea.

**Portul din spate.** Portul micro-USB din spate este mufa de alimentare a consolei. Cu kernelul AutoBleem
poate primi și un dispozitiv USB, dar locul stick-ului este într-un port din față.

**Dacă lipsește stick-ul.** Când consola pornește fără stick sau scoți stick-ul cât timp AutoBleem rulează, o
imagine îți cere să-l introduci - în orice port USB. AutoBleem așteaptă 5 minute și apoi pune consola în repaus;
apasă Power dacă vrei să adoarmă imediat.

![Imaginea care cere stick-ul](../images/en/insert-stick.jpg)

**Când este verificat stick-ul.** Dacă stick-ul n-a fost deconectat corect - l-ai scos cât rula AutoBleem sau s-a
luat curentul - AutoBleem îl verifică de erori înainte să-l folosească din nou: la pornire, după trezire sau când
îl reconectezi. O bară de progres arată cât a avansat verificarea. Pe un stick mare poate dura ceva; las-o să se
termine și nu opri consola între timp.

![Verificarea stick-ului](../images/en/stick-check.jpg)

**Actualizarea.** Ca să actualizezi un stick, rulează din nou programul de instalare pe el - butonul spune acum
*Update*. Instalează cea mai nouă versiune de pe canalul ales; jocurile, salvările, setările și conținutul
RetroArch rămân, iar înlocuite sunt doar fișierele proprii ale AutoBleem. O consolă cu kernelul AutoBleem și cu
WiFi se poate actualiza și singură (secțiunea 3.12).

**Trecerea de la AutoBleem 1.0 (sau AutoBleem-NG).** Folosești același program de instalare pe același stick, fără
să-l formatezi:

1. Mai întâi copiază tot stick-ul pe PC, ca rezervă - pentru orice eventualitate.
2. Conectează-l, pornește `AutoBleemInstaller.exe` și alege canalul și unitatea. **Nu** apăsa Format.
3. Apasă **Install**. Programul de instalare mută vechea organizare în cea nouă: RetroArch, ROM-urile și temele
   ajung acolo unde le așteaptă AutoBleem 2, iar vechile foldere de ROM-uri (`nes`, `snes`, ...) primesc numele de
   sisteme din RetroArch. Jocurile, salvările de stare, cardurile de memorie, ROM-urile și salvările RetroArch rămân
   toate, la fel și `config.ini` - doar emulatorul PS1 din el este schimbat pe pcsx-abnxt.
4. Pune stick-ul înapoi în consolă. Prima scanare reface lista de jocuri și playlist-urile. Pentru coperțile
   jocurilor RetroArch, rulează UpdateRoms pe PC (capitolul 5).

> Consola nemodificată nu are ceas și nici rețea. Datele apar abia după ce instalezi kernelul AutoBleem
> (capitolul 6), iar coperțile pentru jocurile RetroArch vin de la UpdateRoms, de pe PC (capitolul 5).

Jocurile PS1 se pun în folderul `Games` de pe stick, câte un folder pentru fiecare joc - secțiunea 3.10 explică
organizarea.

### 2.2 Raspberry Pi

Cu AutoBleem, un Raspberry Pi devine o mică consolă: pornește direct în lansator, fără niciun desktop la mijloc.
Pe site găsești două imagini gata făcute pentru card, pe 32 și pe 64 de biți, plus un pachet pentru un Raspberry Pi
OS Lite pe care îl ai deja.

| Model | Imagine pe 32 de biți | Imagine pe 64 de biți | Observații |
|---|---|---|---|
| Raspberry Pi 5 | da | da | |
| Raspberry Pi 4 Model B, Pi 400 | da | da | |
| Raspberry Pi 3 Model B / B+ / A+ | da | da | merge bine pentru lansator și PS1 |
| Raspberry Pi Zero 2 W | da | da | 512 MB RAM: PS1 merge, nucleele RetroArch mai grele nu |
| Raspberry Pi 2 Model B | da | doar v1.2 | lent pentru orice e 3D |
| Raspberry Pi 1, Zero, Zero W | nu | nu | ARMv6 - nu rulează niciuna dintre imagini |

**Pentru jocurile PS1, ia imaginea pe 32 de biți.** Recompilatorul ARM rapid al clasicului `pcsx-ab` există doar
pe 32 de biți, așa că pe varianta pe 64 de biți jocurile PS1 merg mai încet. Imaginea pe 64 de biți are în schimb
mai multe nuclee RetroArch, deci alege-o dacă celelalte sisteme contează mai mult pentru tine decât PS1.

**Cu Raspberry Pi Imager:**

1. Instalează Raspberry Pi Imager (raspberrypi.com/software). La *Choose OS* alege *Use custom* și fișierul
   descărcat `autobleem-<versiune>-rpi-armhf.img.xz` (32 de biți) sau `-arm64.img.xz` (64 de biți) - ori adaugă
   un URL de depozit în setările aplicației și alege AutoBleem din listă. Există câte unul pentru fiecare canal:
   `https://autobleem.retromenele.pl/rpi-imager/os_list.json` pentru ultima versiune stabilă,
   `.../os_list-testing.json` pentru versiunea aflată în testare și `.../os_list-nightly.json` pentru cea mai nouă
   versiune de dezvoltare. Fila Raspberry Pi de pe pagina de descărcări le enumeră pe cele care există, fiecare cu
   un buton *Copy*.
2. În ecranul de personalizare din Imager (rotița dințată sau întrebarea de după *Next*) setează **numele de
   utilizator și parola, rețeaua WiFi și țara și activează SSH**. La prima pornire AutoBleem are nevoie de rețea.
3. Scrie cardul, pune-l în Pi, conectează un ecran și o tastatură sau un controler și pornește-l.

**Prima pornire** durează între 5 și 25 de minute, iar ecranul îți arată ce se întâmplă. Dacă nu există rețea, ți-o
cere: alege-ți WiFi-ul din listă și scrie parola. Apoi te întreabă dacă să instaleze RetroArch - dacă nu răspunzi
într-un minut, îl instalează. După aceea mărește partiția de sistem, transformă restul cardului în partiția
`AUTOBLEEM` pentru jocurile tale, instalează RetroArch cu nucleele lui, pachetele BIOS și jocurile de exemplu și
repornește direct în lansator.

Dacă preferi să nu răspunzi la întrebări la prima pornire, scrie dinainte răspunsurile în **`autobleem.txt`** de
pe partiția de boot a cardului - orice PC îl poate deschide și edita:

| Cheie | Implicit | Ce înseamnă |
|---|---|---|
| `root_gib` | 8 | Mărimea partiției de sistem în GiB; restul devine partiția pentru jocuri. |
| `hdmi_mode` | 1920x1080@60 | Modul ecranului pe toată durata pornirii (`1280x720@60` pentru un televizor mai vechi). |
| `retroarch` | (întreabă) | `yes` / `no` - RetroArch și celelalte sisteme, sau doar PS1. |
| `thumbnails` | none | `boxarts` copiază tot setul de coperți, ca să ai coperți și fără rețea (~9000 de fișiere). |
| `bios`, `downloads`, `samples` | yes | Cu `no` sari peste pachetele BIOS, peste orice descărcare sau peste jocurile de exemplu. |

**Pe un Raspberry Pi OS Lite pe care îl ai deja** (Bookworm sau Trixie): copiază `autobleem-rpi.tar.gz` (sau
varianta arm64) pe Pi, dezarhivează-l și rulează `sudo bash install.sh`. Pune aceleași întrebări, face loc pentru
partiția de date micșorând partiția de sistem la următoarea pornire (`--shrink-root <GiB>`) și pune lansatorul pe
prima consolă.

După instalare umpli **partiția `AUTOBLEEM`** a cardului (exFAT) cu jocurile tale: scoate cardul și deschide-l pe
orice PC sau copiază prin rețea (SSH e activat). Jocurile PS1 merg în `Games/`, ROM-urile altor sisteme în
`RetroArch/roms/<sistem>/`, BIOS-ul PS1 în `System/Bios/` (secțiunea 3.11), iar temele în `Themes/`.

### 2.3 Stick USB pentru PC

Același lucru pentru orice PC care poate porni de pe USB: stick-ul pornește PC-ul direct în AutoBleem și nu se
atinge de discul calculatorului. Sistemul e pe 32 de biți, așa că merge și pe mașini vechi.

1. Scrie imaginea pe un stick de cel puțin 8 GB. **Pe Windows** folosește **AutoBleemFlasher** (panoul PC al
   site-ului - dezarhivează-l și rulează `AutoBleemFlasher.exe`; cere drepturi de administrator, pentru că scrie
   un disc întreg): alege canalul și stick-ul, apasă *Write* și confirmă de două ori - descarcă imaginea, o
   verifică, o scrie și o citește înapoi. Îți oferă doar stick-uri USB și carduri SD, niciodată discul de pe care
   rulează Windows, iar **tot ce se află pe stick-ul ales se șterge**. Pe Linux sau macOS descarcă
   `autobleem-<versiune>-pcusb-i386.img.xz` din panoul PC și scrie-o cu
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (sau cu balenaEtcher).
2. Pornește PC-ul de pe stick (cu tasta pentru meniul de boot a PC-ului tău - F12, F8, Esc...). Merge atât
   pornirea BIOS, cât și UEFI; **Secure Boot trebuie să fie dezactivat**.
3. Prima pornire decurge ca pe Pi: cere o rețea dacă nu e conectat niciun cablu, întreabă de RetroArch, instalează
   totul - cam opt minute cu rețea prin cablu - și repornește în lansator.

După aceea, stick-ul are o partiție `AUTOBLEEM` pentru jocurile tale. Conectează stick-ul la un PC pornit cu
Windows 10 (versiunea 1903 sau mai nouă) și apare ca a doua unitate, pe care poți copia jocuri. `autobleem.txt` se
află pe prima partiție, cu aceleași chei ca pe Pi (în afară de `hdmi_mode` - un PC folosește mereu modul propriu
al ecranului).

### 2.4 Windows

Dacă vrei AutoBleem pe calculatorul tău cu Windows, merge și ca program obișnuit: pe tot ecranul, cu emulatoarele
și RetroArch pornite ca programe separate.

1. Descarcă **AutoBleemSetup-<versiune>.exe** și rulează-l. Se instalează pentru utilizatorul curent, fără drepturi
   de administrator: programul în `%LOCALAPPDATA%\Programs\AutoBleem`, iar datele (jocuri, setări, teme,
   RetroArch) într-un folder ales de tine - implicit `Documents\AutoBleem`.
2. Bifează componentele - bazele de date cu coperți, RetroArch (versiunea oficială pentru Windows și nucleele ei),
   fișierele BIOS, jocurile de exemplu - și lasă asistentul de instalare să le descarce.
3. Pornește AutoBleem din meniul Start sau de pe Desktop. Pe un PC, tastatura ține locul controlerului
   (secțiunea 3.2).

Ca să actualizezi, rulează peste el un program de instalare mai nou: programul e înlocuit, iar folderul de date
rămâne cum era. Lansatorul verifică și el site-ul o dată pe zi și îți propune o actualizare când apare una
(secțiunea 3.12).

<!-- pagebreak -->

## 3. Folosirea AutoBleem

### 3.1 Lansatorul

În lansator alegi ce joci. Îți arată jocurile ca pe un raft cu coperți, așa cum ai vedea cutiile pe un raft
adevărat, iar tu derulezi de-a lungul lui până dai de cel pe care îl vrei. Tot restul din AutoBleem - setările,
cardurile de memorie, Magazinul - se deschide de aici, iar când ieși dintr-un joc, aici te întorci.

Jocul selectat stă în mijlocul raftului, cu o reflexie discretă sub el. Lângă el îi vezi detaliile, într-un mic
tabel: editorul, anul, numărul de serie, regiunea, pentru câți jucători e și când l-ai jucat ultima dată. Când
AutoBleem nu știe una dintre aceste informații, sare peste rândul respectiv în loc să-l lase gol. Lângă detalii
se află un buton de pornire. Un joc fără imagine de copertă apare ca un disc așezat în suportul negru al unei
cutii goale, ca să-și aibă și el locul pe raft.

Aspectul lansatorului vine de la temă. Cea implicită este **ab2.0.0**: o instalare nouă trece pe ea, la fel și o
actualizare care o aduce, dar o singură dată - dacă alegi apoi altă temă (secțiunea 3.6), aceea rămâne.

**Bara de indicații** din partea de jos a ecranului îți spune ce fac butoanele în momentul respectiv. Are două
rânduri cu câte patru locuri. Primul rând se referă la jocul selectat: îl pornești, îl pornești în RetroArch,
deschizi rândul de pictograme de sub el sau deschizi Meniul rapid. Al doilea rând nu se schimbă niciodată: Select
alege setul, Start alege un joc la întâmplare, Triangle arată ghidul butoanelor, iar L2 + R2 deschide meniul
sistem. O indicație apare estompată cât timp butonul ei nu are nimic de făcut.

**Găsește singur jocurile noi.** De fiecare dată când pornește, lansatorul scanează în fundal folderul cu jocuri,
așa că un joc copiat cât timp aparatul era oprit apare fără să faci nimic. Cât durează scanarea, o bulă din
dreapta sus arată cât a avansat, iar jocurile noi apar pe raft pe măsură ce sunt găsite - între timp poți
continua să răsfoiești.

**O instalare nouă** nu are încă jocuri. În locul unui raft gol vezi o carte de bun venit, *Salut și bun venit la
AutoBleem!*, care îți spune să pui jocurile în `Games` și să apeși *Rescaneaza jocurile*. Îți numește și locul,
după platformă: pe stick (PlayStation Classic, stick-ul pentru PC), pe cardul SD (Raspberry Pi) sau în folderul
AutoBleem (Windows). Cartea dispare de îndată ce o scanare găsește primul joc.

**Notificările** sunt bulele din dreapta sus. Te țin la curent fără să te încurce: progresul scanării, numele
setului pe care tocmai ai trecut (*Se arată: ...*), un controler cu bateria aproape descărcată, o notă după o
cădere a programului, un procesor de scanare la lucru și o descărcare din Magazin. Bula unei descărcări arată
viteza și timpul rămas, de exemplu `1.4 MB/s · 0:42`. Cât timp rămân pe ecran bulele informative hotărăști tu:
Opțiuni → *Durata anunțului*.

**Bateriile controlerelor.** Pe consolă, pe Raspberry Pi și pe stick-ul pentru PC (nu și pe Windows), fiecare
controler fără fir care își raportează bateria apare ca o mică pictogramă cu procentul, pe o plăcuță proprie;
plăcuțele se așază una sub alta, pornind din colțul din stânga sus. Un controler care joacă pe post de Jucător 1
sau Jucător 2 poartă eticheta P1 sau P2, după opțiunea *Schimbă jucătorul 1 / jucătorul 2* (secțiunea 3.6); un
controler care nu e asociat niciunui jucător, sau un al treilea controler, nu are etichetă. Când bateria unui
controler se descarcă, o notificare te anunță o singură dată, cu numele controlerului și procentul.

**Eticheta canalului.** Dacă folosești o versiune care nu e una finală, o mică etichetă sub plăcuțele bateriilor,
în colțul din stânga sus, îți amintește de asta. E un mic cartonaș cu canalul și, alături, versiunea scurtă:
`ALPHA`, `BETA` sau `RC` pentru o versiune preliminară, `TESTING` pentru orice altă versiune preliminară, `NIGHTLY`
pentru o versiune nightly și `DEV` pentru o versiune compilată de mână (la `DEV`, versiunea este commit-ul din care
a fost compilată). O versiune finală nu are etichetă.

![Alegerea setului: trei file și grupurile filei curente, cu numărul de jocuri](../images/en/set-picker.jpg)

### 3.2 Comenzile

AutoBleem e gândit să fie folosit doar cu controlerul, iar butoanele înseamnă același lucru pe fiecare ecran:
Cross confirmă, Circle te duce înapoi, Triangle te ajută. Dacă uiți ce face un buton, bara de indicații din josul
ecranului îți spune, iar Triangle pe raft deschide ghidul butoanelor, cu toate butoanele tuturor ecranelor
(secțiunea 4.3). Iată ce fac butoanele pe raft:

| Buton | Pe raft |
|---|---|
| Stânga / Dreapta | Trece la jocul anterior sau următor; ține butonul apăsat ca să derulezi în continuare. |
| L1 / R1 | Sare la inițiala anterioară sau următoare a titlurilor, ca să treci repede printr-un raft lung. Pe un raft gol, cu o unitate USB conectată, R1 deschide *Disc* (secțiunea 3.9a). |
| Cross | Pornește jocul selectat: un joc PS1 în emulatorul PS1, un joc RetroArch în nucleul lui, iar o aplicație după ce îi arată descrierea. |
| Square | Pornește jocul PS1 selectat în RetroArch. Când e selectat un disc dintr-o unitate USB, copiază în schimb discul (*Copiază discul*, secțiunea 3.9a). |
| Circle | Te întoarce la ecranul discului când în unitate e un disc (secțiunea 3.9a). |
| Triangle | Deschide ghidul butoanelor. |
| Start | Alege un joc la întâmplare din setul curent, pentru când nu te poți hotărî. |
| Select | Deschide alegerea setului, unde stabilești ce jocuri arată raftul (secțiunea 3.3). |
| Sus | Deschide Meniul rapid (secțiunea 3.4). |
| Jos | Deschide rândul de pictograme de sub joc (*SETĂRI*, *Joc*, *Card de memorie*, *RELUARE*); Sus îl închide la loc. |
| L2 + R2 | Deschide meniul sistem (secțiunea 3.5). |

**Cu tastatura.** Pe un PC fără controler, sau cu o tastatură USB conectată la consolă, la Pi ori la stick-ul
pentru PC, tastele țin locul butoanelor. Săgețile sunt crucea direcțională, Enter este Cross, Esc sau Backspace
este Circle, Tab este Triangle, iar Space este Square. F1 și F2 sunt Select și Start, Page Up și Page Down sunt L1
și R1, Home și End sunt L2 și R2, iar F10 deschide meniul sistem.

Pe Windows câteva taste se schimbă. Acolo Esc închide AutoBleem (capitolul 7), așa că Circle e doar Backspace,
Space este Start, iar S este Square. Pe deasupra, literele pot ține locul întregului controler, fără să mai ajungi
la săgeți: X, O, S și T sunt Cross, Circle, Square și Triangle, I, J, K și L sunt crucea direcțională (sus,
stânga, jos, dreapta), B este Select, Q și E sunt L1 și R1, iar 1 și 2 sunt L2 și R2.

**În orice listă și meniu** merg aceleași mișcări: Sus și Jos mută cursorul, L2 și R2 dau pagina, L1 și R1 sar la
primul sau la ultimul rând, Cross alege, iar Circle te duce înapoi. Nu trebuie să cauți niciodată un buton de
salvare: un ecran cu setări le salvează singur când îl părăsești cu Circle.

**Cum ieși dintr-un joc sau dintr-o aplicație.** Ține apăsat Start + Select, sau Home, timp de 2 secunde și ești
înapoi în AutoBleem. Merge cu orice controler - cel al consolei, unul USB sau unul Bluetooth. O apăsare scurtă pe
aceleași butoane deschide în schimb meniul emulatorului. O aplicație nu are un astfel de meniu, așa că acolo
contează doar apăsarea lungă.

![Rândul de pictograme de sub jocul selectat](../images/en/launcher-icons.jpg)

### 3.3 Seturile

O bibliotecă mare se răsfoiește mai ușor pe bucăți. Seturile îți restrâng raftul la un singur fel de jocuri - doar
favoritele, doar jocurile de Super Nintendo, doar jocurile dintr-un folder - ca să nu treci pe lângă sute de coperți
până găsești ce cauți.

Apasă **Select** și se deschide alegerea setului. Are trei file, PlayStation, RetroArch și Aplicații: L1 și R1
trec de la una la alta, Sus și Jos te plimbă prin grupurile filei (L2 și R2 câte o pagină), iar Cross pune pe raft
grupul ales. Circle (*Înapoi*) închide alegerea fără să schimbe nimic. Bara de jos arată și ea aceste taste.
Fiecare rând spune câte elemente conține. Un grup în care nu e nimic se deschide pe un raft gol, unde rândul de
pictograme oferă doar *SETĂRI*.

**Fila PlayStation.** Pe un PlayStation Classic începe cu *Toate jocurile* și *Jocuri interne* (cele douăzeci de
jocuri incluse în consolă), urmate de *Jocuri USB* - tot ce se află în `Games/` - și câte un grup pentru fiecare
folder creat de tine acolo, așa că un joc dintr-un subfolder ține de grupul folderului respectiv. Apoi vin *Jocuri
favorite*, *Istoric jocuri* și, după ce ai marcat cel puțin un joc ca joc cu pistol optic, *Jocuri Lightgun*. Un
Raspberry Pi, stick-ul pentru PC și Windows nu au jocuri interne, așa că acolo lista începe cu *Jocuri USB*, care
cuprinde întreaga ta bibliotecă.

**Fila RetroArch** există doar acolo unde e instalat RetroArch. Are câte un grup pentru fiecare sistem pentru care
ai jocuri, plus Favoritele și Istoricul proprii ale RetroArch.

**Fila Aplicații** împarte aplicațiile pe tipuri: *Toate aplicațiile*, apoi *Jocuri*, *Emulatoare*, *Instrumente*,
*Media* și *Altele*. Grupul din care face parte o aplicație e stabilit în fișierul ei `app.ini`. Tot aici apar și
**aplicațiile PE**, adică programe Windows rulate de PE runner; una pe care consola n-o poate porni e marcată
*nu poate rula pe această consolă*. Acolo unde lansatorul îl afișează, în listă există și un rând *Pachete*
(secțiunea 3.10).

### 3.4 Meniul rapid

Meniul rapid e o listă scurtă cu lucrurile de care ai nevoie cel mai des cât răsfoiești jocurile, ca să nu fie
nevoie să le cauți în tot meniul sistem. Îl deschizi cu **Sus** pe raft sau cu **pictograma rotiță** din rândul de
pictograme (rândul cu *SETĂRI*, *Joc*, *Card de memorie* și *RELUARE*).

Sus și Jos te mută între elemente (de la ultimul, cursorul o ia de la capăt), Cross alege unul, iar Circle închide
meniul. Un rând sub meniu descrie elementul selectat. Iată ce găsești în el:

- *Rescaneaza jocurile* caută pe loc jocurile noi, modificate sau șterse - util când tocmai ai copiat jocuri și nu
  vrei să aștepți.
- *Magazin* deschide AutoBleem Store, unde răsfoiești și instalezi jocuri, aplicații și extensii (secțiunea 3.13).
- *Nuclee RetroArch*, acolo unde e instalat RetroArch, îți permite să alegi nucleul care rulează fiecare sistem.
- *Rețea și controlere* deschide ecranele pentru Wi-Fi, asocierea prin Bluetooth și maparea controlerului
  (capitolul 6). Apare doar când le oferă o extensie instalată - PSC-Bios face asta pe consolă, pe Raspberry Pi și
  pe stick-ul pentru PC. Dacă extensia e instalată, dar oprită, elementul e gri, iar descrierea lui îți spune s-o
  pornești din Extensii; Cross deschide atunci lista Extensii exact la ea.
- *Repornește lansatorul* închide AutoBleem și îl pornește din nou (doar pe consolă, pe Raspberry Pi și pe
  stick-ul pentru PC).
- *Meniu sistem...* deschide meniul sistem complet, cu tot restul - Opțiuni, Manager jocuri, Oprire și altele
  (secțiunea 3.5).

Tot ce e aici, în afară de Magazin, nucleele RetroArch și repornirea lansatorului, găsești și în meniul sistem.

![Meniul rapid](../images/en/quick-menu.jpg)

### 3.5 Meniul sistem

Meniul sistem cuprinde tot ce poate face AutoBleem în afară de jocul propriu-zis: setările, uneltele pentru
bibliotecă și pentru cardurile de memorie, informații despre aparat și oprirea. Apasă împreună **L2 + R2** (în
orice ordine) și se deschide peste raft. Elementele sunt grupate sub titlurile *Bibliotecă*, *Sistem* și *Ieșire*,
iar cele două folosite cel mai des stau sus de tot. Un rând din josul meniului descrie elementul selectat, așa că
te poți uita în jur înainte să alegi.

| Secțiune | Element | Ce face |
|---|---|---|
| (sus) | *Rescaneaza jocurile* | Caută acum jocurile noi, modificate sau șterse. Scanarea urmărește oricum singură folderul, deci ai nevoie de asta doar când nu vrei să aștepți. |
| | *Extensii* | Arată extensiile de pe stick, de exemplu AutoBleem Store, ca să le poți porni sau opri (secțiunea 3.13). |
| *Bibliotecă* | *Manager jocuri* | Arată jocurile PS1 ca listă, cu folderele lor; aici poți șterge un joc sau poți curăța coperțile (secțiunea 4.1). Nu se poate deschide cât rulează o scanare. |
| | *Carduri de memorie* | Gestionează seturile tale de carduri de memorie comune (secțiunea 3.8). |
| | *Procesoare de scanare* | Stabilește ordinea programelor pe care fiecare scanare le rulează mai întâi și le pornește sau le oprește (secțiunea 3.14). Nu se poate deschide cât rulează o scanare. |
| *Sistem* | *Opțiuni* | Deschide setările AutoBleem (secțiunea 3.6). |
| | *Rețea și controlere* | Deschide ecranele pentru Wi-Fi, asocierea controlerelor Bluetooth, configurarea DualShock 3 și maparea controlerului (capitolul 6). Apare doar când le oferă o extensie - vezi mai jos. |
| | *Informatii hardware* | Arată datele aparatului - sistemul, procesorul, spațiul de stocare, interfețele de rețea, fusul orar, afișajul și controlerele cu mapările lor - pe aceeași pagină pe toate platformele (secțiunea 4.2). Circle te întoarce în meniul sistem. |
| | *Gamepad virtual* | Arată controlerele pe care le primesc aplicațiile și controlerele pe care le vede daemonul; te ajută când un controler nu merge într-o aplicație (secțiunea 4.5). Circle te întoarce în meniul sistem. |
| | *Actualizare software* | Verifică acum pe site dacă există un AutoBleem sau un RetroArch mai nou, în loc să aștepte verificarea zilnică (secțiunea 3.12). Când lansatorul știe deja de una, rândul spune *Actualizare disponibilă*. Pe un PlayStation Classic e nevoie de kernelul AutoBleem și de o rețea Wi-Fi. |
| | *Despre* | Arată mulțumirile și licența. |
| *Ieșire* | *RetroArch* | Părăsește lansatorul și trece în meniul propriu al RetroArch, la setările și listele lui de conținut; când închizi RetroArch, ești din nou în lansator. Există doar acolo unde e instalat RetroArch. |
| | *Oprire* | Oprește aparatul, după ce îți cere confirmarea (vezi mai jos). |

**Rețea și controlere** apare doar acolo unde o extensie instalată oferă intrarea `network`, pe care extensia o
declară prin `Provides=network` în fișierul ei `extension.ini`. PSC-Bios face asta pe consolă, pe Raspberry Pi și pe
stick-ul pentru PC. Dacă extensia e instalată, dar oprită, elementul rămâne în meniu, gri, iar descrierea lui îți
spune s-o pornești din Extensii; Cross pe el deschide lista Extensii chiar la extensia respectivă.

**Oprire** face ce i se potrivește aparatului. Consola o trece în standby-ul AutoBleem: stick-ul e deconectat,
ledul devine portocaliu, iar Power aduce lansatorul înapoi în câteva secunde (secțiunea 2.1). Un Raspberry Pi sau
un PC se închide.

![Meniul sistem](../images/en/system-menu.jpg)

### 3.6 Opțiuni

În Opțiuni faci AutoBleem pe gustul tău: imaginea de pe ecran, aspectul lansatorului, limba, sunetul, emulatorul
PS1 care îți rulează jocurile. Le deschizi din meniul sistem (*Opțiuni*) sau cu pictograma *SETĂRI* de sub un joc.
De obicei setezi ecranul și limba o singură dată și revii când ceva arată ciudat pe un anumit televizor sau când ai
chef de o schimbare.

Setările sunt împărțite în grupuri, fiecare sub un titlu. Sus și Jos te mută de la un rând la altul, iar Stânga și
Dreapta schimbă valoarea rândului pe care te afli: o apăsare scurtă mută un pas, ținerea apăsată continuă. L1 și R1
sar la primul sau la ultimul rând, L2 și R2 dau pagina. Pe un rând cu teme, muzică sau fonturi de ales, Start alege
una la întâmplare. O setare care poate fi doar pornită sau oprită arată **PORNIT** sau **OPRIT**. Fiecare
schimbare se vede pe loc, iar Circle închide ecranul și salvează tot - nu mai e nimic de confirmat. Singura
excepție e modul ecranului, care e încercat abia când ieși din Opțiuni (vezi *Afișaj* mai jos).

Unele rânduri apar doar acolo unde au sens: rândurile pentru CRT doar la o imagine 4:3, cele pentru RetroArch doar
unde e instalat RetroArch, iar jocurile interne doar pe un PlayStation Classic.

| Grup / setare | La ce folosește |
|---|---|
| *Interfață*: *Afișaj:* | Stabilește rezoluția ecranului, pentru lansator și pentru emulatorul PS1. *Auto* folosește modul propriu al ecranului și îți arată care este, de exemplu *Auto (1920x1080)*; poți alege și orice mod pe care ecranul îl oferă. Consola oferă 720p, 1080p și *CRT 4:3* (720x480), modul pentru un televizor CRT vechi sau pentru un dispozitiv de captură 4:3. Schimbă-l când imaginea nu se potrivește televizorului sau e neclară. Rândul lipsește când AutoBleem rulează într-o fereastră, pe o mașină de dezvoltare. |
| *Margine CRT:* | Micșorează puțin totul, de la 0 la 10 %, din 1 în 1 %, pentru că televizoarele vechi taie marginile imaginii. Crește valoarea până când bara de indicații și colțurile se văd în întregime. Apare doar la o ieșire 4:3, are efect imediat și se aplică încă dinainte de ecranul de pornire. |
| *Înălțimea imaginii:* | Face imaginea mai înaltă sau mai joasă, de la -40 la +40, din 2 în 2, la orice ieșire 4:3 - *CRT 4:3* sau un mod 4:3 pe o ieșire VGA ori PC. Folosește-o când imaginea de pe un televizor vechi e turtită sau iese în sus și în jos din ecran. Are efect imediat, iar imaginea jocului din RetroArch o urmează și ea. |
| *Scalarea ecranului emulatorului:* | Hotărăște cum potrivește emulatorul PS1 imaginea jocului pe ecranul tău. *1x1* arată pixelii PlayStation-ului așa cum sunt, mici și exacți; *2x (întreg)* și *4:3 (întreg)* măresc doar cu multipli întregi, ceea ce dă cea mai clară imagine; *4:3* păstrează forma originală a imaginii; *Ecran complet* întinde imaginea pe tot ecranul. Înlocuiește vechiul comutator Widescreen. Clasicul `pcsx-ab` și RetroArch cunosc doar ecranul complet și 4:3. |
| *Halou ecran:* | Când e PORNIT, benzile goale de lângă imaginea jocului (acolo unde imaginea nu umple ecranul) sunt umplute cu strălucirea discretă a imaginii însăși, în loc de negru. Merge cu `pcsx-abnxt`. |
| *Tema AutoBleem:* | Schimbă aspectul lansatorului. Temele stau în `Themes/`, iar o arhivă zip de temă pusă acolo apare și ea după nume. Temele livrate cu AutoBleem sunt reîmprospătate la fiecare actualizare, așa că, dacă vrei să modifici una, copiaz-o mai întâi sub alt nume. Implicită este **ab2.0.0**. |
| *Stil copertă:* | Alege rama de cutie de CD desenată în jurul coperților PS1. |
| *Strălucirea copertei:* | Face ca o strălucire să treacă peste coperta selectată de fiecare dată când raftul se oprește. |
| *Limba:* | Stabilește limba lansatorului; sunt 17, iar schimbarea are efect imediat. |
| *Durata anunțului:* | Stabilește cât rămân pe ecran bulele informative (*Se arată: ...*, rezumatul scanării), de la 0 la 20 de secunde; la 0 apare *Oprit* și bulele sunt dezactivate. Mesajele de eroare au timpul lor fix, ca să nu-ți scape niciunul. |
| *Ecran de pornire:* | Arată imaginea AutoBleem cât pornește lansatorul; oprește-l ca să ajungi direct la raft. |
| *Animații:* | Animează trecerea de la un ecran la altul; oprește-le dacă preferi ca fiecare ecran să apară instantaneu. |
| *Fonturi*: *Folosește fontul implicit:* | Când e PORNIT, lansatorul folosește fontul propriu (Red Hat Text); oprește-l ca să folosești fontul ales în rândul următor. |
| *Font:* | Alege un font al tău: orice fișier `.ttf` sau `.otf` din `resources/fonts`, `RetroArch/fonts` sau din folderul temei. Rândul arată numele fontului folosit de fapt. |
| *Sunet*: *Muzica:*, *Muzica de fundal:* | *Muzica:* alege piesa care se aude în lansator - cea a temei sau un fișier din `resources/music`. *Muzica de fundal:* hotărăște dacă se aude vreo muzică. |
| *Emulare*: *Emulator PS1:* | Alege emulatorul în care pornesc jocurile PS1: `pcsx-abnxt`, cel implicit (PCSX-ReARMed actual, cu adăugirile AutoBleem), sau `pcsx-ab`, cel clasic. Încearcă-l pe celălalt când un joc nu merge bine. Un punct de reluare salvat de unul poate fi continuat în celălalt, cu excepția cazului în care jocul a rulat fără fișier BIOS. |
| *Schimbă jucătorul 1 / jucătorul 2 (emulatoare PS1):* | Inversează, în ambele emulatoare PS1, care dintre primele două controlere e Jucătorul 1 și care Jucătorul 2 - util când controlerele sunt conectate „invers". Contează doar cu două sau mai multe controlere conectate; cu un singur controler joci mereu ca Jucătorul 1. RetroArch nu e afectat. Dacă emulatorul PS1 folosit nu poate încă face inversarea, AutoBleem îți spune. |
| *Joacă toate jocurile PSX cu RA:*, *Actualizează configurația RA:*, *Păstrează config. RetroArch:* | Aceste trei apar doar acolo unde e instalat RetroArch. Prima pornește fiecare joc PS1 în nucleul PS1 al RetroArch (*PlayStation 1*; pe PC acesta este SwanStation). A doua îi permite lui AutoBleem să-și scrie setările în configurația RetroArch când pornește un joc acolo. A treia păstrează o modificare făcută în meniul propriu al RetroArch după ce RetroArch se închide. |
| *Bibliotecă*: *Arată jocurile interne:* | Arată jocurile incluse în consolă în listele PlayStation (doar PlayStation Classic). |
| *Nume de jocuri curate:* | Când e PORNIT (implicit), listele de jocuri RetroArch arată nume îngrijite, fără etichete între paranteze precum (USA), (Rev 1) sau [!]; OPRIT arată numele fișierelor. Numele fișierului rămâne vizibil în detaliile jocului. Jocurile PS1 nu sunt afectate, pentru că titlurile lor vin din baza de date. |
| *Preia coperțile online:* | Permite scanării să descarce coperțile lipsă de pe serverele libretro (Raspberry Pi, PC, Windows). |
| *Actualizări*: *Actualizări:* | Alege ce actualizări caută lansatorul (secțiunea 3.12): `release` (versiunea testată), `testing` (următoarea versiune, aflată în testare), `nightly` (cea mai nouă versiune de dezvoltare) sau `off`. Valoarea implicită urmează versiunea pe care ai instalat-o. Nu apare pe o mașină de dezvoltare. |
| *Diagnosticare*: *Păstrează jurnalele pe stick:* | Păstrează pe stick, de la următoarea pornire, toate jurnalele, nu doar pe cele de după o cădere - pornește-o când urmărești o problemă (capitolul 7). |
| *Afișează performanța:* | Arată în colțul din stânga jos un strat cu numărul de cadre pe secundă, încărcarea procesorului, firele de execuție și memoria; într-un joc, emulatorul îți arată și el FPS-ul și procesorul. |

**Schimbarea modului ecranului.** Când ieși din Opțiuni cu un mod nou la *Afișaj:*, AutoBleem trece pe el și
întreabă *Păstrezi acest mod de afișare?*. Dacă imaginea e în regulă, confirmă. Dacă televizorul nu arată nimic,
așteaptă: fără confirmare, AutoBleem revine la modul anterior după o numărătoare inversă.

**Temele pe un ecran 4:3.** În modul *CRT 4:3*, lista de teme arată doar temele care au un aspect 4:3. Dacă tema pe
care o folosești nu are, tema implicită îi ia locul după ce confirmi modul (și la fiecare pornire în acel mod), iar
o notificare te anunță: *Tema a fost schimbată cu cea implicită (CRT 4:3)*.

![Opțiunile, pe grupuri](../images/en/options.jpg)

![Grupul Interfață: Margine CRT și Înălțimea imaginii](../images/en/options-display.jpg)

![Notificarea de după trecerea pe CRT 4:3 cu o temă fără aspect 4:3](../images/en/crt43-theme-notice.jpg)

### 3.7 Setările unui joc

Fiecare joc poate avea setările lui. Cele mai multe jocuri merg bine așa cum sunt, dar din când în când câte unul
are nevoie de un mic ajutor - o imagine mai clară sau mai fină, un cadru sărit ca să meargă fluent, alt card de
memorie - sau vrei să-l marchezi ca favorit. Editorul de joc e locul unde schimbi aceste lucruri doar pentru acel
joc, fără să te atingi de celelalte.

Cu un joc selectat, apasă **Jos** ca să deschizi rândul de pictograme de sub el. Are patru pictograme: *SETĂRI*
(opțiunile din secțiunea 3.6), *Joc* (setările acestui joc), *Card de memorie* (cardul lui de memorie) și
*RELUARE* (salvările lui de stare). Mergi pe una și apasă Cross ca s-o deschizi.

**Editorul de joc** (pictograma *Joc*) arată în dreapta detaliile jocului - titlul, editorul, anul, numărul de
jucători, folderul și cardul de memorie - iar în stânga setările lui. Sus și Jos te mută între setări, Stânga și
Dreapta le schimbă, ca în Opțiuni; dacă ții butonul apăsat, mișcarea se repetă. Când ai terminat, Circle îți
salvează modificările și te duce înapoi. Un joc fără titlu în datele lui apare sub numele folderului său.

Setările sunt împărțite în patru grupuri:

- **Joc** se referă la felul în care AutoBleem tratează jocul. *Favorit:* îl pune în grupul *Jocuri favorite* din
  alegerea setului. *Blochează datele:* îi spune scanerului să lase titlul, numărul de serie și lista de discuri
  ale jocului exact cum le-ai stabilit, ca o scanare ulterioară să nu-ți suprascrie modificările. *Reluare:*
  hotărăște ce se întâmplă când pornești un joc care are puncte de reluare: *Întreabă* arată alegerea slotului de
  reluare, *Ultimul slot* continuă imediat din cel mai nou slot, iar *Niciodată* pornește jocul mereu de la început.
  Acolo unde e instalat RetroArch mai sunt două rânduri. *Joc Lightgun:* e pentru un joc cu pistol optic: jocul
  intră în grupul *Jocuri Lightgun* și rulează mereu în RetroArch, pentru că nucleul PS1 al RetroArch are GunCon
  (pornirea lui pornește și rândul următor). *Joacă folosind RA:* rulează doar acest joc în RetroArch în loc de
  emulatorul PS1.
- **Afișaj** se referă la cum arată imaginea. *Rezoluție:* desenează jocul la 1x sau 2x (pe GPU-ul încorporat),
  iar *Elimină cusăturile:*, care merge doar la 2x, ascunde liniile subțiri care pot apărea între părțile imaginii
  la această mărime. *Dithering:* (*Oprit*, *Pornit*, *Mereu*) controlează modelul fin de puncte prin care
  PlayStation-ul amestecă culorile, iar *Netezire:* alege unul dintre filtrele de netezire ale emulatorului.
  *Filtru:* hotărăște cum e scalată imaginea pe ecran: *Cel mai apropiat* arată pixelii simpli, *Liniar* îi
  netezește, *Clar* și *Clar (simplu)* păstrează pixelii clari fără pâlpâire, și mai există *Quilez*. Filtrele CRT
  *CRT (rapid)*, *CRT (raster)* și *CRT-Pi* imită un televizor vechi și își desenează singure liniile de scanare,
  așa că rândurile pentru linii devin gri cât timp e ales unul dintre ele. Altfel, *Scanlines:* adaugă liniile
  întunecate ale unui televizor vechi, iar *Luminozitate scanlines:* stabilește cât de întunecate sunt.
  *Rezoluție*, *Elimină cusăturile*, *Dithering*, *Netezire* și filtrele în afară de *Liniar* și *Cel mai apropiat*
  sunt pentru `pcsx-abnxt`; clasicul `pcsx-ab` și RetroArch arată orice alt filtru ca *Cel mai apropiat*.
- **Randare** are *Plugin:* pentru GPU și *Frameskip:* (*Auto*, *Oprit* sau între 1 și 3 cadre). Săritul peste
  cadre ajută un joc care merge prea încet să-și păstreze viteza, cu prețul unei imagini mai puțin fluide.
- **Emulator** are *SpeedHack:*, *Ceas:* procesorului, *Interpolare SPU:* (cum e netezit sunetul), *Logo de
  pornire:* și, cu `pcsx-abnxt`, *Corecții Sony:*. Oprește *Logo de pornire:* ca să sari peste ecranul BIOS - ai
  nevoie de asta pentru un disc homebrew pe care logo-ul lui personalizat îl împiedică să pornească.

Forma imaginii și rezoluția ecranului nu se stabilesc pentru fiecare joc, ci pentru toate odată, în Opțiuni
(*Scalarea ecranului emulatorului:* și *Afișaj:*).

**Alte butoane în editor.** Triangle redenumește jocul, cu tastatura de pe ecran. Square îi dă jocului alt card de
memorie (*Schimbă cardul de memorie*). Cât timp jocul își folosește încă propriul card, Start transformă acel card
într-un set comun nou, ca să-l poată folosi și alte jocuri (*Partajează cardul de memorie*, secțiunea 3.8). Aceste
două nu sunt oferite pentru jocurile interne ale consolei. Ținerea apăsată a butoanelor Stânga / Dreapta sau
Sus / Jos repetă mișcarea aici, ca și în ecranele de opțiuni ale jocurilor și de nuclee din RetroArch.

Un joc își ține setările în propriul fișier `pcsx.cfg`. Orice joc de pe stick are unul, pentru că îl creează
scanarea. Un disc original într-o unitate USB (secțiunea 3.9a) primește însă un dosar propriu cu un `pcsx.cfg`
abia prima dată când îl pornești; până atunci o schimbare făcută în editor nu poate fi păstrată, iar editorul îți
spune *Nesalvat: acest joc nu are pcsx.cfg*. Așa că pornește discul o dată - de atunci încolo setările lui se
păstrează ca la orice alt joc. Un disc care aparține unui joc aflat deja în colecția ta folosește de la început
dosarul și setările acelui joc.

Pentru un **disc din unitate** (secțiunea 3.9a) unele setări n-au sens, așa că editorul face acele rânduri gri, iar
rândul de jos spune *Indisponibil pentru un disc din unitate* când ajungi pe unul dintre ele.

![Editorul de joc pentru un disc din unitate](../images/en/game-editor-disc.jpg)

**Setări salvate în emulator.** Poți regla un joc și în timp ce îl joci: meniul propriu al emulatorului are *Save
settings for this game* (secțiunea 3.9). Odată ce un joc are setări salvate acolo, cu ele se joacă. Editorul de joc
arată atunci rândurile Afișaj, Randare și Emulator în gri, cu valorile salvate, sub titlul *Salvat în emulator*,
ca să le poți citi, dar nu și schimba. Dacă vrei să folosești din nou setările din editorul de joc, alege
*Deblochează setările* și confirmă: setările salvate de emulator sunt șterse, iar rândurile pot fi schimbate din
nou. Ambele emulatoare, `pcsx-ab` și `pcsx-abnxt`, citesc și scriu aceleași setări salvate, așa că nu contează care
dintre ele le-a salvat.

![Editorul de joc](../images/en/game-editor.jpg)

### 3.8 Cardurile de memorie și salvările de stare

Pe un PlayStation adevărat împărțeai unul sau două carduri de memorie între toate jocurile și, mai devreme sau mai
târziu, rămâneai fără loc. În AutoBleem fiecare joc PS1 are implicit cardul lui de memorie, așa că nu trebuie să te
gândești niciodată la spațiu sau la cardul pe care se află o salvare. Cardul stă împreună cu salvările de stare ale
jocului, în `Games/!SaveStates/<folderul jocului>/`.

**Seturi comune de carduri de memorie.** Uneori jocurile trebuie să vadă salvările altor jocuri - o continuare care
citește salvarea primului joc, de exemplu, sau discurile unei serii pe care le vrei pe același card. Pentru asta
creezi un set comun: un card folosit de mai multe jocuri. Seturile stau în `Games/!MemCards/` și le gestionezi din
*Carduri de memorie*, în meniul sistem. Square creează un set nou (îi scrii numele cu tastatura de pe ecran), Cross
îl redenumește pe cel selectat, iar Triangle îl șterge, după ce te întreabă. Ca să pui un joc pe un set, folosește
*Schimbă cardul de memorie* din editorul lui de joc (secțiunea 3.7) sau pictograma lui *Card de memorie*.

**Editorul de carduri de memorie** se deschide din pictograma *Card de memorie* a unui joc. Arată cardul jocului și
un al doilea card unul lângă altul, cu pictograma și titlul fiecărei salvări, ca ecranul cardurilor de memorie de
pe consola originală. Square copiază salvarea selectată pe celălalt card, Triangle o șterge, iar Select
defragmentează un card, adunându-i blocurile libere la un loc, ca să încapă din nou o salvare mare. Start îți
permite să alegi ce set e afișat în dreapta, iar Cross reîncarcă ambele carduri de pe stick. Un card pe care jocul
n-a scris încă nimic - un joc în care n-ai salvat - e gol și are scris *niciun card încă* lângă nume. Dacă ai făcut
modificări, AutoBleem întreabă *Vrei să salvezi datele cardurilor de memorie?* înainte să părăsească editorul, să
reîncarce cardurile sau să arate alt set.

![Editorul de carduri de memorie](../images/en/memory-card-editor.jpg)

**Punctele de reluare.** Multe jocuri PS1 te lasă să salvezi doar în anumite locuri, iar nu ajungi mereu la unul
înainte să fii nevoit să te oprești. Punctele de reluare rezolvă asta: când ieși dintr-un joc PS1 cu butonul Reset
al consolei (sau prin meniul emulatorului, pe un Pi ori pe un PC), AutoBleem păstrează o salvare de stare exact din
locul unde erai. Cât o scrie, la ieșirea din joc, emulatorul arată *Please wait...*. Data viitoare continui din
acel moment.

Le găsești sub pictograma *RELUARE* a jocului. Un joc cu un punct de reluare arată pe pictogramă o mică imagine a
lui; la un joc fără niciunul, pictograma e gri. Alegerea slotului de reluare are patru sloturi, arătate ca niște
cartonașe înrămate, fiecare cu o imagine a momentului, numărul slotului și data. Cel mai nou e marcat **CEL MAI
NOU**, iar un slot nefolosit spune *Niciun punct de reluare*. Cross continuă jocul din slotul selectat, iar
Triangle îl șterge. Dacă alegerea apare sau nu când pornești jocul depinde de setarea *Reluare:* a jocului
(secțiunea 3.7).

Și jocurile PS1 pe care le joci în RetroArch au sloturi de reluare. Fiecare slot poartă o insignă - sigla AutoBleem
2 sau sigla RetroArch - ca să vezi ce emulator l-a scris.

![Alegerea slotului de reluare](../images/en/resume-picker.jpg)

### 3.9 Pornirea jocurilor, RetroArch și aplicațiile

Pornirea unui joc e ce vei face cel mai des, așa că e nevoie de un singur buton: alege jocul pe raft și apasă
**Cross**. Un joc PS1 se deschide pe tot ecranul în emulatorul PS1 ales în Opțiuni (secțiunea 3.6) și rulează până
când ieși din el. Dacă ai prefera să joci un joc PS1 în RetroArch - pentru că merge mai bine acolo sau pentru că îți
plac opțiunile RetroArch - apasă în schimb **Square**.

**Ieșirea dintr-un joc.** Pe PlayStation Classic, butoanele consolei fac ce te-ai aștepta. **Reset** din față te
duce înapoi în lansator și păstrează un punct de reluare din locul unde erai, ca să poți continua mai târziu
(secțiunea 3.8); merge chiar și cu meniul din joc deschis. **Power** oprește consola. Un Raspberry Pi sau un PC nu
are astfel de butoane, așa că acolo ieși prin meniul din joc al emulatorului, descris mai jos.

Mai există o cale de ieșire care merge la fel cu orice controler - cel al consolei, unul USB sau unul Bluetooth:
**ține apăsat Start + Select, sau Home, timp de 2 secunde** și ești înapoi în AutoBleem. O apăsare scurtă pe
aceleași butoane deschide în schimb meniul emulatorului. Lansatorul ți le amintește pe amândouă în indicații (*Ține
apăsat Select+Start sau Home 2 secunde: înapoi la AutoBleem* și *Apăsare scurtă Select+Start sau Home: meniul
emulatorului*). O aplicație nu are meniu de emulator, așa că acolo contează doar apăsarea lungă. Pe consolă, Reset
oprește întotdeauna și o aplicație.

**Meniul din joc.** Cu `pcsx-abnxt`, emulatorul are un meniu propriu pentru lucrurile de care ai nevoie în timp ce
joci: salvarea, schimbarea discurilor, reglarea imaginii, alegerea controlerelor. Apasă butonul de meniu - Home pe un
controler care îl are, **Select + Start** pe unul care nu-l are sau **Esc** pe tastatură - iar jocul se oprește în
spatele meniului, cu ultima lui imagine în fundal. Dacă ții butonul de meniu apăsat 2 secunde, faci același lucru
ca Reset: ieși din joc. Meniul are trei file, iar L1 și R1 trec de la una la alta. Își amintește unde ai rămas, așa
că data viitoare se deschide pe aceeași filă și pe același rând.

- Fila **Joc** se ocupă de jocul în sine. *Continuă jocul* închide meniul și te lasă să joci mai departe. La
  *Salvări*, *Salvare rapidă* păstrează momentul în care te afli, iar *Încărcare rapidă* te aduce înapoi la el.
  *Încarcă autozapis* te duce înapoi la starea jocului de acum cel mult 30 de secunde - emulatorul ține această
  copie în memorie cât joci și te scapă de o greșeală pe care altfel n-ai mai putea-o repara. La *Disc CD*,
  *Schimbă discul* e pentru un joc pe mai multe discuri, când îți cere discul următor, iar *Resetează jocul* îl
  pornește de la capăt. *Salvează setările pentru acest joc* păstrează setările alese doar pentru acest joc
  (secțiunea 3.7). *Meniu PCSX* deschide paginile proprii ale PCSX-ReARMed, cu opțiunile, cheat-urile și pagina
  About, iar *Ieși* te duce înapoi în AutoBleem.
- Fila **Imagine** îți permite să schimbi cum arată jocul și să vezi imediat rezultatul: *Afișaj*, *Rezoluție* (1x
  sau 2x), *Elimină cusăturile*, *Dithering*, *Scalare*, *Halou ecran*, *Netezire*, *Filtru*, *Mască CRT*,
  *Scanlines* și *Luminozitate scanlines*. Sunt aceleași setări ca în editorul de joc (secțiunea 3.7), iar fiecare
  rând are în dreapta un text de ajutor care spune la ce folosește. *Afișaj* este rezoluția ecranului; pe consolă
  o alegi în Opțiuni, iar aici e doar afișată. *Halou ecran* e pentru benzile întunecate de lângă o imagine 4:3 pe
  un televizor lat: le umple cu marginile imaginii înseși, în oglindă și întunecate, așa că jocul pare să se
  reverse în ele, în loc să stea înghesuit între două bare negre. *Mască CRT* pune peste imagine modelul de fosfor
  al unui tub vechi - *Apertură* dă dungile fine ale unui Trinitron, *Fantă* și *Delta* punctele altor tuburi; o
  găsești doar împreună cu filtrul CRT (raster). Filtrul CRT-Pi e prea greu pentru consolă la 1080p. Un rând care
  nu se aplică e gri, iar textul lui de ajutor îți spune de ce.
- Fila **Controlere** stabilește ce e conectat la cele două porturi ale PlayStation-ului, *Controler 1* și
  *Controler 2*: un controler standard (digital), un controler analogic (DualShock), un pistol sau nimic. Unele
  jocuri merg doar cu un anumit fel de controler. Schimbarea are efect când te întorci în joc.

Meniul e desenat în aspectul ab2.0.0 al lansatorului, așa că nu pare un alt program, și îți arată bateriile
controlerelor și imaginea ultimei salvări rapide.

**Jocurile RetroArch.** Un joc de pe alt sistem pornește în RetroArch, cu nucleul ales de lansator pentru sistemul
lui. Când ai terminat, *Close Content* sau *Quit RetroArch* din meniul RetroArch te aduce înapoi în lansator. Dacă
vrei să schimbi nucleul care rulează un sistem, deschide *Nuclee RetroArch* din Meniul rapid (secțiunea 3.4); lista
se deschide cu nucleul *PlayStation 1* în capul ei. Iar dacă vrei meniul propriu al RetroArch (XMB), pentru setările
și listele lui de conținut, alege *RetroArch* în meniul sistem: RetroArch se deschide atunci fără nimic încărcat.

![Fereastra Nuclee RetroArch, cu nucleul PlayStation 1 sus](../images/en/retroarch-cores.jpg)

**Aplicațiile.** Aplicațiile sunt mai degrabă programe decât jocuri: uneltele consolei și, pe consolă, aplicațiile
suplimentare care vin cu pachetul RetroArch - Doom, Quake, Amiga și altele. Le găsești în setul Aplicații. Înainte
să pornească o aplicație, AutoBleem îi arată descrierea, ca să știi ce este și cum se controlează. Cross o
pornește, iar Circle te duce înapoi la raft.

![Descrierea unei aplicații, arătată înainte să pornească](../images/en/app-start.jpg)

**Setările unei aplicații.** Multe aplicații au fost scrise pentru un anumit controler, așa că poți schimba felul în
care îl văd pe al tău. Selectează aplicația, deschide rândul de pictograme și alege *Joc*: se deschid *Setări joc*
ale aplicației (*Schimbă modul de pornire al acestui program*). *Mod controler:* hotărăște ce controler i se spune
aplicației că are. *Automat* folosește ce cere aplicația însăși; *Controler PSC* și *Controler Xbox 360* îți
prezintă controlerul ca pe cel al consolei sau ca pe un controler Xbox 360, iar *Controler PSC (sistem)* și
*Controler Xbox 360 (sistem)* fac același lucru prin sistemul însuși. Încearcă alt mod când o aplicație nu
reacționează la controler cum ar trebui. *D-pad ca stick:* lasă crucea direcțională să miște stick-ul analogic,
pentru o aplicație care ascultă doar de stick, iar *Stick ca D-pad:* face invers.

Unele aplicații îți pun o întrebare la prima pornire. Una vrea să știe *Ce comenzi are controlerul tău?*, ca să-și
poată configura comenzile: răspunde *Un D-pad* pentru un controler doar cu cruce direcțională sau *Stick-uri
analogice*. O aplicație care rulează Windows întreabă *Ce vrei să faci?* și îți oferă să rulezi Windows, să-l
instalezi, să rulezi DOS sau să dezinstalezi Windows. Când o aplicație te lasă să setezi o tastă, îți cere *Apasă
unul dintre butoane.*

![Setările de joc ale unei aplicații](../images/en/app-game-settings.jpg)

Un program Windows rulat de PE runner (o aplicație PE, secțiunea 3.3) îți vorbește prin ecranele AutoBleem: un mesaj
pe care vrea să-l arate apare ca *Mesaj*, iar o întrebare cu variante ca *Alege o opțiune*, fiecare având numele
aplicației drept titlu.

![O întrebare de la o aplicație PE, arătată ca ecran AutoBleem](../images/en/pe-dialog.jpg)

### 3.9a Un disc într-o unitate USB

Poți conecta o unitate CD/DVD USB obișnuită la consolă, la un Raspberry Pi sau la un PC pornit de pe stick-ul
AutoBleem și poți juca direct de pe un disc PlayStation original - fără să copiezi nimic. Discul pe care îl
introduci apare în lansator ca încă un joc. Pe Windows nu funcționează.

**Copierea unui disc pe stick.** Dacă vrei să ai jocul mereu la îndemână, fără disc, apasă Square (*Copiază
discul*). AutoBleem te întreabă mai întâi dacă să copieze jocul și cât loc va ocupa, apoi îl salvează în folderul
`Games` ca un singur fișier CHD (un joc pe mai multe discuri primește și un fișier `.m3u`, ca schimbarea discurilor
să meargă în joc). Cât copiază, vezi viteza și timpul rămas, iar *Întrerupe* oprește copierea. Când a terminat,
jocul stă pe raft ca oricare altul. AutoBleem nu copiază un joc care se află deja în `Games` și nici unul pentru
care nu e loc - atunci îți spune cât loc îi trebuie. Se poate copia și un disc zgâriat: părțile care n-au putut fi
citite sunt umplute cu zerouri, iar AutoBleem îți spune câte au fost. O astfel de copie poate să meargă sau nu.

Square oferă copierea pentru orice disc de joc PlayStation din ecranul discului, chiar și pentru unul pe care bazele
de date cu coperți nu-l cunosc. Un joc cunoscut de bazele de date e copiat sub titlul lui; la un joc pe mai multe
discuri, copiază discurile unul după altul, iar fișierul `.m3u` le pune în ordine, cu discul 1 primul. Un disc pe
care bazele de date nu-l cunosc primește în schimb numărul de serie drept nume, e copiat ca un singur disc și nu are
copertă pe raft. Fereastra de copiere, *Se copiază discul*, rămâne pe ecran până când copierea s-a terminat sau a
fost oprită - lansatorul așteaptă între timp - și arată viteza ca multiplu al unei unități CD obișnuite. Dacă
copierea eșuează, AutoBleem îți spune de ce.

![Copierea unui disc](../images/en/disc-copy.jpg)

**Jocul de pe disc.** Când introduci un disc, **ecranul discului** se deschide singur imediat ce discul a fost citit.
Arată coperta discului - din bazele de date cu coperți sau descărcată online - cu numărul de serie și titlul, iar
Cross pornește jocul. Un joc PS1 jucat de pe disc își păstrează punctele de reluare și salvările într-un folder
propriu, așa că te poți opri și poți continua mai târziu exact ca la un joc de pe stick. După joc, sau după ce ai
fost în opțiuni ori în setările unei extensii, te întorci la ecranul discului. Dacă îl părăsești cu Circle ca să
răsfoiești celelalte jocuri, discul rămâne în unitate, iar Circle pe raft aduce ecranul înapoi; pe un raft gol îl
deschide și R1 (*Disc*). Pe un raft cu jocuri, R1 își păstrează rolul obișnuit de a sări între inițiale. Când scoți
discul, ecranul discului se închide.

![Ecranul discului](../images/en/disc-view.jpg)

**Indicatorul unității**, din partea de sus a ecranului, îți spune ce face unitatea, ca să știi dacă trebuie să
aștepți. Fără nicio unitate conectată nu vezi nimic. O unitate fără disc arată o pictogramă de disc estompată. Cât
se citește un disc, pictograma clipește și scrie *Se citește discul...*, iar când e gata se aprinde, cu titlul
discului. Dacă introduci un disc care nu e nici joc PlayStation, nici CD audio, indicatorul spune *Acesta nu este
un disc PlayStation*, iar dacă unitatea nu poate citi discul în acel moment, spune *Discul nu poate fi citit acum*.

![Indicatorul unității](../images/en/disc-chip.jpg)

**CD-urile audio.** Unitatea redă și CD-uri cu muzică. Un CD audio deschide **playerul CD** în locul ecranului
discului. Acesta arată discul ca *CD audio*, cu lista pieselor și durata totală, iar rândul de dedesubt numește
piesa selectată și spune dacă repetarea și ordinea aleatorie sunt pornite. Un disc pe care playerul nu-l poate reda
e marcat *This disc cannot be played*. Iată butoanele lui:

| Buton | În playerul CD |
|---|---|
| Cross | Redă piesa selectată. |
| Start | Pune muzica pe pauză și o pornește din nou. |
| Square | Oprește muzica. |
| L1 / R1 | Trec la piesa anterioară sau următoare. |
| L2 / R2 | Derulează piesa înapoi sau înainte, câte cinci secunde. |
| Triangle | Schimbă ce se repetă: nimic, tot discul sau piesa curentă. |
| Select | Pornește sau oprește ordinea aleatorie, ca piesele să se audă amestecat. |
| Circle | Iese din playerul CD. |

![Playerul CD](../images/en/cd-player.jpg)

**Discurile cu LibCrypt.** Unele jocuri PlayStation, cele mai multe europene, au o protecție la copiere numită
LibCrypt. Ca să le ruleze, emulatorul are nevoie de un mic fișier `.sbi` cu datele protecției. AutoBleem descarcă
singur fișierul de pe site înainte să ruleze un astfel de disc și când îl copiezi, iar fișierul e copiat împreună cu
jocul. Pentru asta are nevoie de rețea: pe un Raspberry Pi sau pe un PC, de cea pe care o are deja, iar pe consolă,
de Wi-Fi-ul configurat în PSC-Bios.

Pentru un disc din unitate, unele dintre setările unui joc n-au sens, așa că editorul lui de joc face acele rânduri
gri (secțiunea 3.7).

### 3.10 Adăugarea jocurilor

AutoBleem își găsește singur jocurile, cu condiția să fie la locul potrivit. Secțiunea aceasta îți spune unde merge
fiecare fel de joc, ca fiecare scanare să le pună pe raft cu numele și coperțile lor.

**Jocurile PS1** merg în folderul `Games`, **câte un folder pentru fiecare joc**, cu numele jocului. Poți grupa
jocurile și în foldere proprii, iar fiecare astfel de folder devine un grup în alegerea setului (secțiunea 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                a folder of games: a group of its own in the set picker
    Klonoa/                   Klonoa.pbp
```

AutoBleem citește formatele obișnuite de imagini de disc: `.cue` cu `.bin`-ul lui (sau `.img`), `.pbp`, `.chd`
(inclusiv cele comprimate cu zstd), `.iso` și `.ecm`, pe care scanarea îl decodează pentru tine. Merge și un joc
arhivat zip: procesorul **Unzip** îl dezarhivează înainte ca scanarea să-l citească (secțiunea 3.14).

Nu trebuie să fii foarte ordonat. Un joc pe mai multe discuri ține într-un singur folder, cu toate discurile, dar
dacă copiezi foldere numite `Game (Disc 1)`, `Game (Disc 2)` și așa mai departe, scanarea le unește într-un singur
folder `Game`. Și jocurile puse direct în `Games/` ca fișiere libere sunt mutate de scanare în foldere proprii.

**Numele și coperțile** vin singure. Scanarea citește numărul de serie al fiecărui disc și ia titlul, editorul,
anul, numărul de jucători și regiunea din baza de date PlayStation a RetroArch sau din bazele de date cu coperți.
Dacă vrei o copertă a ta, pune un PNG sau un JPEG lângă imaginea jocului, cu același nume. Fără ea, coperta vine din
bazele de date cu coperți sau, cu RetroArch instalat, din setul de miniaturi libretro; pe un Raspberry Pi, pe un PC
sau pe Windows, o copertă lipsă e descărcată online (Opțiuni → *Preia coperțile online*). Dacă scanarea greșește
ceva, corectează în editorul de joc și pornește *Blochează datele*, ca următoarea scanare să-ți păstreze
modificarea.

**Jocurile altor sisteme** merg în `RetroArch/roms/`, **câte un folder pentru fiecare sistem, numit cum îl numesc
bazele de date RetroArch** - de exemplu `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo
Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` sau `FBNeo - Arcade Games` (ori
`Arcade`). Folderele sunt create pentru tine, iar ROM-urile pot rămâne arhivate zip. Pe un Raspberry Pi, pe un PC
sau pe Windows, scanarea le citește singură și scrie playlist-urile RetroArch. Stick-ul unei console nu poate face
asta singur, așa că acolo rulezi **UpdateRoms** pe PC (capitolul 5).

**Aplicațiile** merg în `Apps/<nume>/`, fiecare cu un `app.ini` - numele, pictograma și ce trebuie rulat - și cu un
`run.sh`.

**Pachetele.** Unele aplicații sunt motoare de joc: au nevoie de datele unui joc pe care îl deții înainte să-l poată
rula. Așa funcționează Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme
Hospital, jocurile DOS și altele. Pune fișierele jocului într-un folder `Packages` pe stick, câte un folder pentru
fiecare joc - de exemplu `Packages/Doom/DOOM2.WAD` - iar AutoBleem le recunoaște după un tabel care vine cu el
(`rc/packages.ini`). Într-un folder pe care îl recunoaște, fișierele de joc libere sunt pachete de sine stătătoare.
AutoBleem doar îți citește fișierele și nu le modifică niciodată. Un pachet poate veni și din Magazin (secțiunea
3.13).

Acolo unde lansatorul îl afișează, rândul *Pachete* din fila Aplicații (secțiunea 3.3) enumeră datele de joc găsite.
Cross pe o intrare îi deschide **Package info**: ce conțin datele, o descriere, unde se află fișierele și de unde
provin (fișierele tale, Magazinul, un mod sau fișiere care vin în interiorul unei aplicații), dacă sunt shareware
sau gratuite și ce aplicație instalată le rulează. Dacă nimic din ce ai instalat nu le poate rula, informațiile îți
spun asta.

Când pornești o aplicație-motor, AutoBleem caută date de joc pe care le poate rula. Cu un singur set de date, jocul
pornește imediat. Cu mai multe, o listă (*Alege datele jocului*) te întreabă pe care să-l joci, iar cursorul stă pe
cel ales data trecută. Dacă nu există niciunul, AutoBleem îți spune de ce date are nevoie aplicația și unde să le
pui, iar nimic nu pornește.

**Jocurile tale.** Când AutoBleem nu recunoaște niște date, Package info-ul lor spune *Nerecunoscut. Dacă este un
joc, vezi manualul: Jocurile tale.* Tabelul cunoaște doar jocurile pentru care a fost făcut. Pentru altul, scrie un
rând pentru el într-un `packages.ini` propriu, în folderul `Packages`: AutoBleem îl citește mai întâi pe al tău, așa
că rândurile tale au prioritate.

![Alegerea pachetului, unde alegi datele de joc cu care pornești](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Scanarea unei singure părți.** Dacă ai adăugat jocuri doar într-un set sau într-un folder, *Rescaneaza jocurile*
poate scana doar partea aceea, ceea ce e mai rapid decât să scaneze tot, iar bula ei dispare când a terminat.

**Temele** merg în `Themes/<nume>/`, cu `theme.json`-ul și imaginile lor - sau pune arhiva zip a temei în
`Themes/` așa cum e.

### 3.11 BIOS-ul PS1

BIOS-ul este programul de pornire al PlayStation-ului, iar emulatorul rulează jocurile cel mai fidel cu cel
adevărat. Pe un **PlayStation Classic** nu ai nimic de făcut: emulatorul folosește BIOS-ul consolei. Pe un
**Raspberry Pi, pe un PC și pe Windows** pune propriile fișiere BIOS PS1 în `System/Bios/`: `romw.bin` (cel
american/european, SCPH-5501/5502) și `romJP.bin` (cel japonez, SCPH-5500, folosit pentru jocurile japoneze).
Programele de instalare le completează din pachetele BIOS RetroArch, cu excepția cazului în care fișierele tale
sunt deja acolo - pe ale tale nu le înlocuiesc niciodată. Fără ele, emulatorul rulează pe BIOS-ul HLE încorporat,
un înlocuitor pe care multe jocuri îl acceptă, iar altele nu; așa că, dacă un joc nu pornește, un BIOS lipsă e
primul lucru de verificat.

### 3.12 Actualizările

AutoBleem se ține singur la zi, așa că primești funcții noi și reparații fără să reinstalezi nimic. Când pornește
lansatorul, și apoi o dată pe zi, verifică pe site dacă există o versiune nouă pe **canalul** lui. Canalul îl alegi
în Opțiuni → *Actualizări*: `release`, `testing`, `nightly` sau `off`, dacă nu vrei să caute deloc. Dacă nu vrei să
aștepți verificarea zilnică, *Actualizare software* din meniul sistem verifică pe loc.

Când există o versiune nouă, AutoBleem te întreabă ce să facă. *Actualizează acum* o descarcă și o instalează, ceea
ce durează câteva minute. *Amintește-mi mâine* întreabă din nou peste o zi, iar *Sari peste această versiune* nu
mai întreabă despre această versiune. Orice ai alege, jocurile, salvările și setările rămân mereu; după o
actualizare, lansatorul îți mai scanează o dată jocurile. Eticheta canalului din colțul din stânga sus (secțiunea
3.1) arată ce versiune ai.

Felul în care e instalată actualizarea depinde de aparat:

- Pe un **Raspberry Pi** și pe **stick-ul pentru PC**, după descărcare rulează din nou programul de instalare, cu
  același ecran de progres ca la prima pornire, și îți oferă și un RetroArch mai nou. Apoi lansatorul revine.
- Pe **Windows** se deschide programul de instalare descărcat, care instalează noua versiune și pornește noul
  lansator.
- Pe un **PlayStation Classic** se poate actualiza singură doar o consolă cu **kernelul AutoBleem** (ABFlashKit,
  secțiunea 6.2) și cu o **rețea Wi-Fi** configurată în PSC-Bios (secțiunea 6.1) - o consolă nemodificată nu are
  rețea, așa că lansatorul nici nu caută. După *Actualizează acum*, lansatorul se închide, iar imaginea AutoBleem
  rămâne pe ecran cât se actualizează stick-ul, ceea ce durează câteva minute; apoi pornește noul lansator. Fără
  rețea, *Actualizare software* îți spune *Neconectat*. Orice stick de consolă poate fi actualizat și de pe un PC,
  cu `AutoBleemInstaller.exe` (secțiunea 2.1).

### 3.13 Extensiile și AutoBleem Store

**Extensiile** adaugă lucruri noi lansatorului - ecrane și funcții proprii - fără să schimbe AutoBleem în sine.
AutoBleem Store și PSC-Bios sunt extensii. O extensie stă în `Extensions/<nume>/` pe stick (pe un Raspberry Pi, pe
partiția lui de date, pe Windows, în folderul de date); ca s-o instalezi, dezarhivează-i acolo arhiva zip.

Ca să le vezi, deschide meniul sistem (**L2 + R2**) și alege *Extensii*. Cele care vin de la echipa AutoBleem sunt
sus, iar celelalte urmează sub *Extensii terțe*. Cross o pornește pe cea selectată, iar Triangle o oprește sau o
pornește din nou. PSC-Bios pe consolă e excepția: cu el configurezi Wi-Fi-ul, controlerele și ceasul, așa că acolo
nu poate fi oprit. Când o extensie nu poate rula, rândul ei îți spune de ce - are nevoie de rețea și nu există, nu
e făcută pentru acest sistem, a fost făcută pentru altă versiune de AutoBleem și are nevoie de o actualizare, sau
n-a putut fi încărcată. Dacă vreodată o extensie oprește lansatorul, AutoBleem o oprește și lista îți spune asta;
o poți porni din nou de aici.

![Lista Extensii](../images/en/extensions.jpg)

**AutoBleem Store** este prima extensie: un loc în care răsfoiești aplicații și jocuri și le instalezi cu o singură
apăsare, pe orice sistem pe care rulează AutoBleem. Un PlayStation Classic are nevoie pentru el de kernelul
AutoBleem, pentru că Wi-Fi-ul vine odată cu kernelul. Îl deschizi din Meniul rapid (*Magazin*, secțiunea 3.4). Are
patru file, iar L1 și R1 trec de la una la alta.

Filele **Apps** și **Games** enumeră ce oferă sursele, fiecare element cu imaginea, versiunea, mărimea lui și mica
pictogramă a sursei din care vine. Fila Apps enumeră și aplicațiile PE, cu licența și sursa lor, precum și pachetele
cu date de joc (secțiunea 3.10). Ce ai instalat deja poartă insigna *Installed*. Bara de indicații arată butoanele
valabile pentru rândul selectat:

| Buton | În filele Apps și Games |
|---|---|
| Cross | Instalează elementul - sau îl actualizează, reîncearcă după un eșec ori anulează o descărcare care așteaptă sau rulează. |
| Triangle | Elimină ceva instalat de Magazin. |
| Square | Reîmprospătează listele din surse. |
| L2 / R2 | Sar la inițiala anterioară sau următoare. |
| Select | Arată câte o singură sursă, când vrei să vezi ce oferă doar ea. |
| Start | Caută în titluri. |

Imaginile sunt păstrate după ce s-au încărcat, așa că listele apar repede data viitoare, iar o imagine care nu s-a
încărcat poate fi reîncercată.

Fila **Downloads** arată ce se descarcă, ce așteaptă, ce a eșuat sau ce e instalat, cu o bară de progres care
înaintează constant. Nu trebuie s-o urmărești: descărcările continuă în fundal, și după ce ieși din Magazin, iar cât
ești în altă parte a lansatorului, o bulă arată descărcarea în curs, cu viteza și timpul rămas (de exemplu
`1.4 MB/s · 0:42`). Pornirea unui joc sau oprirea aparatului doar le pune pe pauză, iar o descărcare întreruptă
continuă de unde a rămas. Dacă pică rețeaua, elementul spune *Waiting for the network* și continuă de unde era când
rețeaua revine; după 30 de minute fără rețea, renunță. Descărcările de peste 2 GB merg pe toate platformele,
inclusiv pe versiunile pe 32 de biți. Un joc pe care îl instalezi apare pe raft după următoarea scanare, cu imaginea
din Magazin drept copertă.

Fila **Sources** arată de unde vin listele, fiecare cu pictograma ei: catalogul propriu al AutoBleem, orice listă TSV
pusă în `System/Extensions/store/sources/` și adresele pe care le adaugi tu cu *Add a source URL*. Cross pe o sursă
adăugată de tine îți permite s-o redenumești, să-i schimbi adresa, s-o treci între `http://` și `https://` sau s-o
elimini.

![Fila Apps a Magazinului](../images/en/store-apps.jpg)

![Meniul unei surse adăugate de tine](../images/en/store-source-menu.jpg)

Ce oferă catalogul propriu al AutoBleem e listat și pe site-ul de descărcări, la
`https://autobleem.retromenele.pl/store/`. O sursă adăugată de tine e altă poveste: **tu răspunzi de ce conțin
sursele pe care le adaugi.**

**Propriile jocuri în rețeaua ta.** Dacă îți ții jocurile PS1 pe alt calculator din casă, `abstored`, serverul LAN
al Magazinului, le poate oferi Magazinului prin rețea, iar tu le instalezi ca pe orice alt element. Rulează pe orice
mașină cu Linux - un Raspberry Pi, un server de acasă - și doar citește folderul, fără să-l modifice. Pornește-l cu
`abstored <folderul cu jocuri>`, apoi deschide `http://<acea mașină>:8124/` într-un browser: pagina arată ce oferă
și eventualele probleme găsite. În Magazin, adaugă `http://<acea mașină>:8124/store.tsv` ca sursă. Programe gata
făcute pentru Linux și Windows găsești pe pagina Magazinului, în fila **LAN server**, iar `INSTALL-linux.md`
(`ext_store/server/` în codul sursă) explică cum îl configurezi ca serviciu. **LAN Share** (secțiunea 5.2) pune pe
un astfel de server jocuri și discuri de pe un PC.

### 3.14 Procesoarele de scanare

Procesoarele de scanare îți pregătesc jocurile înainte ca AutoBleem să le citească. Un procesor e un mic program pe
care fiecare scanare îl rulează mai întâi. Poate transforma un format pe care AutoBleem nu-l citește într-unul pe
care îl citește - dezarhivând un joc zip, de exemplu - sau poate modifica datele unui joc, cum ar fi aplicarea unui
patch de traducere. Procesoarele stau în `System/Processors/<nume>/` pe stick (pe un Raspberry Pi, pe partiția lui
de date, pe Windows, în folderul de date); ca să instalezi unul, dezarhivează-i folderul acolo, iar următoarea
scanare îl rulează.

**Unzip vine cu AutoBleem.** Dezarhivează jocurile PS1 arhivate zip din `Games/` înainte ca scanarea să le citească,
iar ROM-urile arhivate pe rând, câte unul; seturile arcade rămân arhivate, pentru că așa le citesc nucleele arcade.
Actualizarea AutoBleem actualizează și Unzip, iar dacă l-ai oprit, rămâne oprit.

Un procesor își face treaba o singură dată: după ce s-a ocupat de un joc, nu mai e rulat pe el până când jocul se
schimbă. Cât lucrează un procesor, bula din dreapta sus arată ce face, iar un avertisment sau un eșec apare pe rândul
de sub ea; `processors.log` din folderul de jurnale are detaliile. Pornirea unui joc sau a RetroArch oprește un
procesor care modifică fișiere, ca jocul să aibă aparatul doar pentru el, iar următoarea scanare termină treaba.

Ca să le gestionezi, deschide meniul sistem (**L2 + R2**) și alege *Procesoare de scanare*. Le vezi în ordinea în
care rulează, cu o filă pentru jocurile PS1 și una pentru ROM-uri; L1 și R1 trec de la o filă la alta. Ordinea
contează: un procesor care dezarhivează trebuie să vină înaintea unuia care aplică patch-uri pe ce a fost
dezarhivat.

| Buton | În Procesoare de scanare |
|---|---|
| Square | Ridică procesorul selectat, ca Sus și Jos să-l mute pe noul loc; Square îl pune din nou jos. |
| Cross | Oprește procesorul sau îl pornește din nou. |
| Triangle | Pune procesorul să se uite din nou la fiecare joc la următoarea scanare, inclusiv la cele de care s-a ocupat deja. |
| Circle | Te duce înapoi și pornește o scanare dacă ai schimbat ceva. |

Un procesor construit pentru alt aparat rămâne în listă, gri, ca să vezi că e acolo, dar că aici nu rulează.

![Procesoare de scanare](../images/en/processors.jpg)

Dacă vrei să-ți scrii propriul procesor, pagina lui Unzip, `https://github.com/autobleem2/proc_unzip`, explică tot
ce trebuie să facă un procesor, iar `tools/proc_check.py` din codul sursă AutoBleem îl verifică pe al tău înainte
să-l împarți cu alții.

<!-- pagebreak -->

## 4. Ecranele

### 4.1 Manager jocuri

Managerul de jocuri e locul în care faci ordine în biblioteca PS1. Folosește-l când vrei să elimini un joc pe care
nu-l mai joci, să deschizi setările unui joc fără să-l cauți întâi pe raft sau să-l pui pe AutoBleem să aducă din
nou toate coperțile. Îl deschizi din meniul sistem (L2 + R2, *Manager jocuri*). Cât rulează o scanare, e gri și
așteaptă până se termină scanarea.

Ecranul are titlul *Manager jocuri - selectează jocul*. În stânga vezi toate jocurile PS1, ca listă de titluri în
ordine alfabetică; în dreapta, coperta jocului selectat cu editorul, anul, numărul de serie și folderul în care se
află. Spațiul liber rămas pe unitate e afișat în dreapta sus, ca să vezi cât loc îți eliberează o ștergere. Sus și
Jos te mută prin listă, L2 / R2 dau pagina, iar L1 / R1 sar la primul sau la ultimul joc.

- **Cross** deschide jocul selectat în editorul de joc - același editor ca la pictograma Joc de pe raft (secțiunea
  3.7). Când ieși din el, ești din nou pe același joc din listă.
- **Square șterge jocul.** AutoBleem te întreabă mai întâi, apoi elimină tot folderul jocului. Dacă salvările de
  stare și cardul de memorie ale jocului nu sunt folosite de niciun alt joc, îți pune o a doua întrebare: dacă să le
  șteargă și pe acelea. Răspunde nu dacă s-ar putea să vrei jocul înapoi mai târziu, cu salvările tale.
- **Triangle șterge toate imaginile de copertă** (PNG sau JPEG) aflate lângă jocurile tale, după o întrebare. E util
  când ai adunat coperți care nu-ți plac: următoarea scanare ia din nou coperțile din bazele de date cu coperți.

La sfârșitul listei, după jocuri, s-ar putea să vezi foldere marcate *Neadăugat*. Sunt foldere din `Games` la care
scanarea s-a uitat, dar din care n-a putut face un joc. Selectează unul, iar partea din dreapta îți spune unde se
află și de ce n-a fost adăugat - lipsește un fișier cue, de exemplu (capitolul 7). Square șterge un astfel de folder,
după o întrebare. Când ieși cu Circle după ce ai schimbat ceva, AutoBleem scanează din nou jocurile.

![Managerul de jocuri: lista jocurilor în stânga, coperta și detaliile jocului selectat în dreapta](../images/en/game-manager.jpg)

### 4.2 Informatii hardware

Informatii hardware e pagina la care te uiți când vrei să afli ce e aparatul tău și ce vede: cât loc mai e pe stick,
ce adresă de rețea are, ce drivere de afișaj și de sunet folosește și ce controlere sunt conectate. E aceeași pagină
pe toate platformele, inclusiv pe consolă. O deschizi din meniul sistem (L2 + R2, *Informatii hardware*); Circle te
întoarce în meniul sistem.

Pagina arată sistemul, componentele hardware, spațiul de stocare cu spațiul liber, adresele de rețea, driverele de
afișaj și de sunet și controlerele conectate. Recitește totul în fiecare secundă, așa că o poți lăsa deschisă cât
conectezi un controler sau un cablu și poți urmări cum apare schimbarea. Doar arată lucruri - ca să configurezi
rețeaua sau un controler, folosește *Rețea și controlere* (PSC-Bios, capitolul 6).

Partea despre controlere răspunde la întrebarea „care controler e care jucător?". Primele două controlere apar ca
*Jucător 1* și *Jucător 2* - porturile pe care li le dă emulatorul PS1. Orice alt controler apare ca *nefolosit de
emulatorul PS1*. RetroArch împarte porturile după propriile setări, așa că într-un joc RetroArch ordinea poate fi
alta. Nu trebuie să deschizi pagina de fiecare dată: oricând conectezi sau scoți un controler, lansatorul îți arată
pentru scurt timp care controler e acum Jucătorul 1 și care Jucătorul 2.

![Informatii hardware: datele aparatului și controlerele conectate](../images/en/hardware-info.jpg)

### 4.3 Ghidul butoanelor

Dacă uiți ce face un buton undeva, apasă **Triangle** pe raft. Ghidul butoanelor arată toate butoanele tuturor
ecranelor pe o singură pagină, ca să le poți căuta fără să ieși din lansator. Dacă e conectată o tastatură USB, sau a
fost folosită, o coloană *Tastatură* arată tasta corespunzătoare lângă fiecare buton al controlerului.

Ghidul îți amintește și singurul lucru care merită ținut minte pentru orice joc: cum ieși din el. Ține apăsat
Select + Start, sau Home, timp de 2 secunde ca să te întorci în AutoBleem; o apăsare scurtă deschide în schimb
meniul emulatorului.

![Ghidul butoanelor: butoanele fiecărui ecran, cu tastele de pe tastatură alături](../images/en/button-guide.jpg)

### 4.4 Tastatura de pe ecran

Ori de câte ori AutoBleem are nevoie să scrii ceva - numele unui set de carduri de memorie, titlul unui joc, o parolă
de WiFi, adresa unei surse din Magazin - apare aceeași tastatură pe ecran, ca să poți scrie doar cu controlerul. E
așezată ca tastatura unui telefon. Pe lângă litere are o pagină de simboluri, cu `/ \ : ? & = % @ #` și restul de
care are nevoie o adresă sau o parolă, și două pagini cu litere cu diacritice. Rândul de jos cuprinde Shift, tasta
care schimbă pagina, Space, Backspace și Confirmare.

Te miști printre taste cu direcțiile și apeși **Cross** ca să scrii tasta de sub cursor. **Triangle** șterge o
literă, iar **Square** scrie un spațiu. **L1** e Shift; apasă-l de două ori pentru Caps Lock. **R1** trece la
următoarea pagină de taste, iar **L2 / R2** mută cursorul în text. **Start** confirmă ce ai scris, iar **Circle**
anulează. Dacă e conectată o tastatură USB, poți scrie oricând pe ea în schimb: Enter confirmă, iar Esc anulează.

![Tastatura de pe ecran](../images/en/keyboard.jpg)

### 4.5 Gamepad virtual

Aplicațiile - programele din setul Aplicații, precum Doom sau Quake - nu-ți citesc singure controlerul. Un mic
program ajutător, daemonul de gamepad virtual, citește controlerele reale și îi dă fiecărei aplicații un controler
pe care îl înțelege. Pagina aceasta îți arată ce controlere vede ajutorul și cum le citește. Uită-te aici când o
aplicație nu reacționează la controlerul tău sau când are butoanele amestecate. O deschizi din meniul sistem (L2 +
R2, *Gamepad virtual*); Circle te întoarce în meniul sistem.

Sub *Controlerele văzute de daemon* e listat fiecare controler, cu un număr și numele lui. Alături citești trei
lucruri: dacă ajutorul a putut deschide controlerul (*conectat*) sau nu (*nu poate fi citit*); driverul prin care a
venit controlerul; și de unde vine așezarea butoanelor lui - *din baza de date a controlerelor* înseamnă că
controlerul e cunoscut și are butoanele unde trebuie, *ghicit de daemon* înseamnă că nu e cunoscut și ajutorul a
ghicit cât a putut de bine. Dacă butoanele dintr-o aplicație par greșite, cel mai probabil vina e a unei așezări
ghicite.

Ajutorul rulează doar cât rulează o aplicație, așa că pagina îl întreabă o dată, când se deschide. Dacă conectezi un
controler cât pagina e deschisă, apasă **Cross** (*Caută din nou*) ca să întrebe din nou. Pe Windows nu există un
astfel de ajutor, iar pagina spune *Nu există în această versiune*.

![Gamepad virtual: controlerele pe care le vede ajutorul aplicațiilor](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. Pe PC

### 5.1 UpdateRoms - reîmprospătarea stick-ului unei console

Pe un Raspberry Pi, pe un PC sau pe Windows, scanarea lansatorului îți pune singură jocurile RetroArch în liste și
le aduce coperțile. PlayStation Classic nu poate face asta, pentru că nu are rețea proprie. **UpdateRoms** face
această treabă în locul ei, pe PC-ul tău cu Windows: folosește rețeaua PC-ului, dar scrie totul cu căile la care se
așteaptă consola, așa că, atunci când pui stick-ul înapoi, consola pornește și găsește totul la locul lui. Rulează-l
ori de câte ori ai adăugat sau ai șters jocuri RetroArch de pe stick-ul unei console.

1. Copiază ROM-urile pe stick, în `RetroArch/roms/<sistem>/` (secțiunea 3.10). Numele folderelor trebuie să fie
   numele din bazele de date RetroArch; pe cele obișnuite le-a creat deja programul de instalare.
2. Pornește **`UpdateRoms\UpdateRoms.exe` de pe stick** - acolo l-a pus programul de instalare. Își dă seama singur
   pe ce stick se află. Cât lucrează, vezi un rând care spune ce face, o bară de progres și un jurnal.
   - Dacă stick-ul nu are încă o bază de date RetroArch, descarcă mai întâi pachetul de baze de date RetroArch.
     Apoi identifică fiecare ROM cu ajutorul lui, așa că un joc pe care baza de date îl cunoaște își primește
     numele corect.
   - Scrie câte un playlist pentru fiecare sistem în `RetroArch/bin/playlists/`, cu căile consolei. Tot ce a adăugat
     RetroArch însuși în aceste liste se păstrează.
   - Pentru fiecare ROM fără copertă, aduce o copertă de pe serverele de miniaturi libretro în
     `RetroArch/bin/thumbnails/`.
3. Scoate stick-ul în siguranță și pune-l înapoi în consolă. Fila RetroArch din alegerea setului enumeră acum
   fiecare sistem care are jocuri.

Îl poți rula ori de câte ori vrei: un folder în care nu s-a schimbat nimic e sărit, așa că a doua rulare e rapidă.
Dacă ceva nu merge, jurnalul e `System/Logs/updateroms.log` pe stick. Cardul unui Raspberry Pi pus într-un cititor
de carduri poate fi reîmprospătat la fel, cu `UpdateRoms.exe <unitate> --target rpi`, deși un Pi face asta singur
când are rețea.

### 5.2 LAN Share - jocurile și discurile tale pe serverul din rețeaua ta

Magazinul poate instala jocuri de pe un server din propria ta rețea de acasă (secțiunea 3.13). **LAN Share** este
programul Windows care umple acel server de pe PC-ul tău: pune pe server jocurile PS1 pe care le ai pe PC și poate
citi un disc PS1 din unitatea CD/DVD a PC-ului, ca să-l pună și pe el acolo. Serverul este un `abstored` care
rulează pe un Raspberry Pi, pe un NAS sau pe alt PC. Odată ce un joc e pe el, Magazinul de pe consolă, de pe Pi sau
de pe PC îl poate instala de acolo.

`LanShare.exe` îl iei de pe pagina Magazinului, din fila **LAN server**. Nu e nimic de instalat: îl pornești, iar el
își ține setările în `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![Fereastra LAN Share: jocurile serverului în stânga, jocurile de pe acest PC în dreapta](../images/en/lanshare.jpg)

1. **Conectează-te la server.** Scrie-i adresa așa cum o are Magazinul, `http://<adresa lui>:<port>`, și apasă
   **Connect**. În stânga apar jocurile aflate deja pe server și eventualele probleme găsite de scanarea lui proprie.
   Ca să pună jocuri pe server, LAN Share are nevoie de una dintre două căi de acces:
   - **Share** este folderul de jocuri al serverului, așa cum e partajat în rețeaua ta (Samba), de exemplu
     `\\raspberrypi\games`. LAN Share copiază jocurile în el și îi cere serverului să scaneze; serverul însuși doar
     își citește în continuare folderul.
   - **Token** e pentru un server pornit cu `--allow-uploads`. Scrie tokenul lui - serverul îl afișează când
     pornește și îl păstrează în `<state>/upload-token`. LAN Share încarcă atunci prin HTTP, iar o încărcare oprită
     la jumătate continuă de unde a rămas.
2. **Publică jocurile de pe PC.** Alege folderul în care ai jocurile (câte un folder pentru fiecare joc), bifează-le
   pe cele pe care le vrei și apasă **Publish the ticked games**. **On the server** îți spune dacă serverul are deja
   un joc - compară numărul de serie, sau titlul când nu există număr de serie - iar un joc pe care serverul îl are
   nu e trimis niciodată de două ori. **Tick those not on the server** le bifează pentru tine pe toate celelalte.
3. **Publică un disc.** Pune un disc PS1 în unitatea PC-ului și apasă **Read a disc and publish it**. LAN Share
   citește tot discul într-un `.bin` + `.cue`, numite după titlul jocului. La un joc cu LibCrypt scrie și fișierul
   `.sbi`, dacă unitatea poate citi subcanalul. Dacă ai ales bazele de date (mai jos), verifică copia cu dump-ul bun
   cunoscut. Apoi publică jocul. La un joc pe mai multe discuri, bifează mai întâi **The game has more than one
   disc**: LAN Share îți cere fiecare disc următor și le publică împreună, ca un singur joc.
4. **Scoate jocuri de pe server.** Selectează-le și apasă **Remove from the server...**. Nu se șterge nimic: fiecare
   joc e mutat într-un folder `.removed` lângă jocurile serverului, iar dacă îl muți înapoi, revine.

**Databases** sunt opționale. Dacă îi arăți lui LAN Share folderul cu coperți al AutoBleem (`coversU/P/J.db`) și
fișierul `Sony - PlayStation.rdb` al RetroArch, le folosește ca să numească jocurile și ca să verifice un disc citit.

Dacă preferi să nu copiezi nimic, bifează **Also share the games on this PC with the Store** (debifat implicit): LAN
Share oferă atunci Magazinului direct folderul de jocuri de pe PC. Prima dată când faci asta, Windows te întreabă de
firewall - permite doar rețelele private.

<!-- pagebreak -->

## 6. Uneltele consolei (PlayStation Classic)

Pe stick-ul pentru PlayStation Classic vin două unelte care te ajută să configurezi consola dincolo de ce știe să
facă din cutie. Amândouă arată ca restul lansatorului, în tema și limba lui, și le folosești cu controlerul - în
asistentul de mapare a controlerului și cu butoanele din fața consolei. **PSC-Bios** este o extensie care vine cu
pachetul pentru consolă: o deschide elementul *Rețea și controlere* din Meniul rapid și din meniul sistem și o găsești
și în lista Extensii. **ABFlashKit** este o aplicație, în setul Aplicații.

### 6.1 PSC-Bios

PSC-Bios e locul din care conectezi aparatul la lume: la rețeaua ta WiFi, la fusul orar, la controlerele Bluetooth
și tot aici stabilești așezarea butoanelor unui controler pe care AutoBleem nu-l cunoaște. Vine cu pachetul pentru
consolă și există și pe Raspberry Pi și pe stick-ul pentru PC. Îl deschizi cu *Rețea și controlere* din meniul
sistem (sau din Meniul rapid) ori din lista Extensii. Dacă extensia e instalată, dar oprită, elementul *Rețea și
controlere* e gri și spune că *este oprită - pornește-o din Extensii*; apasă Cross pe el și lista Extensii se
deschide la PSC-Bios, ca s-o poți porni din nou.

Primul ecran îți dă o privire de ansamblu: ora și fusul orar, adaptoarele de rețea (WiFi, Ethernet, Bluetooth) cu
adresele lor și fiecare controler conectat, cu o notă dacă are o mapare a butoanelor. Pe consolă, părțile de rețea
și Bluetooth au nevoie de kernelul AutoBleem (secțiunea 6.2); pe un Raspberry Pi sau pe stick-ul pentru PC folosesc
uneltele sistemului. Asistentul de mapare a controlerului merge peste tot.

![PSC-Bios: ecranul principal Rețea și controlere](../images/en/pscbios-main.jpg)

De pe primul ecran, câte un buton te duce în fiecare parte:

| Buton | Ce deschide |
|---|---|
| Select | **Wi-Fi Network** te conectează la WiFi-ul tău (prin kernel sau, pe un Pi ori pe un PC, prin NetworkManager): scrie numele rețelei sau alege-l dintr-o căutare, introdu parola, alege modul driverului și apasă *Apply / Restart Network*. Tot aici setezi fusul orar, iar după ce te-ai conectat vezi adresa IP a consolei. |
| Square | **Bluetooth Controllers** caută controlere Bluetooth, precum DualShock 4, ca să poți asocia unul nou sau să-l elimini pe unul pe care nu-l mai folosești. |
| L1 | **DualShock 3 Pairing** îți conectează primul DualShock 3, care trebuie să fie legat prin USB pentru asta, prin pluginul sixaxis al kernelului. |
| R1 | **Controller Mapping** deschide asistentul de mapare a controlerului, descris mai jos. |
| Triangle | **About** arată ce este PSC-Bios. |
| Circle | **Back** te scoate din PSC-Bios, înapoi în lansator. |

**Asistentul de mapare a controlerului.** Folosește-l când un controler nu face nimic în AutoBleem sau are butoanele
în locuri greșite. Îți arată controlerul conectat așa cum este de fapt - fiecare axă, buton și hat, ca numere - și o
imagine de DualShock care se aprinde pe măsură ce apeși. Pentru că controlerul pe care îl testezi nu e încă de
încredere, asistentul îl conduci cu **butoanele din fața** consolei: **RESET** trece la controlerul următor,
**OPEN** pornește maparea, iar **POWER** anulează sau iese. În timpul mapării, asistentul îți cere un buton după
altul: apasă butonul aprins pe imagine sau OPEN, dacă pe controlerul tău nu există un astfel de buton. O apăsare
scurtă se mapează ca de obicei.

Poți ieși și din controler: ține apăsat Circle 2 secunde - o bară se umple, iar bara de jos spune *Hold 2 s: Exit*.
Cât timp controlerul nu are încă mapare, același lucru îl face ținerea apăsată a oricărui buton timp de 2 secunde
(*Hold any button 2 s: Exit*). Pe tastatură, Esc, Space și Enter țin locul lui POWER, RESET și OPEN.

La sfârșit, maparea nouă e pusă în folosință, ca s-o poți încerca, iar OPEN o salvează sub un nume ales de tine. De
atunci, lansatorul o încarcă de fiecare dată.

![PSC-Bios: asistentul de mapare a controlerului](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - kernelul AutoBleem

Kernelul AutoBleem înlocuiește kernelul Linux original al consolei și este opțional. Îl vrei dacă vrei mai mult de la
consolă: îi dă un ceas care funcționează, face să meargă adaptoarele USB WiFi și Bluetooth (pentru PSC-Bios și
controlerele Bluetooth) și adaugă suportul pentru butoanele din față pe care emulatorul îl folosește la punctele de
reluare. ABFlashKit este unealta care îl instalează. Face mai întâi o copie de rezervă a consolei și poate aduce
consola înapoi la starea din fabrică prin recuperarea proprie Sony.

> **Această unealtă scrie în memoria flash a consolei.** Dacă scrierea e întreruptă - se ia curentul sau e scos
> stick-ul - s-ar putea ca consola să nu mai pornească, iar instalarea unui kernel personalizat îi anulează garanția.
> Ține consola alimentată și stick-ul introdus până când consola repornește singură. ABFlashKit se deschide cu acest
> avertisment: *I understand* merge mai departe, *Quit* iese.

![Meniul ABFlashKit](../images/en/abflashkit-menu.jpg)

ABFlashKit are trei acțiuni:

- **Flash Kernel** instalează kernelul. Dacă pe stick nu există încă o copie de rezervă pentru recuperare, face mai
  întâi una a partițiilor consolei (`LBOOT.EPB`). Verifică copia de rezervă și imaginea kernelului, scrie kernelul și
  fișierele de sistem ale AutoBleem și repornește consola. Când spune *All done - when the screen goes black replace
  power cord*, așteaptă ecranul negru, apoi scoate cablul de alimentare al consolei și pune-l la loc.
- **Full backup** salvează toate cele patru partiții ale consolei în `LBOOT.EPB`, ca să le poți restaura mai târziu.
  Dacă există deja o copie de rezervă, întreabă înainte s-o suprascrie.
- **Restore Mode** este drumul înapoi la firmware-ul original. Verifică dacă pe stick e o copie de rezervă a
  firmware-ului original, setează indicatorul de recuperare și repornește în recuperarea Sony, care restaurează
  consola din `LBOOT.EPB`.

O bară de progres sub fiecare pas arată cât a avansat. ABFlashKit nu scrie kernelul pe o consolă care rulează alt
firmware personalizat, precum BleemSync sau Project Eris: adu mai întâi acea consolă la starea din fabrică.

**Conectarea de pe un PC.** Dacă te pricepi la Linux și vrei să te uiți în interiorul consolei, te poți conecta la
ea de pe un PC, printr-un cablu USB. E nevoie de kernelul AutoBleem; pe o consolă nemodificată nu merge.

1. Leagă portul micro-USB al consolei de PC cu un cablu USB. PC-ul vede consola ca pe un adaptor de rețea nou, iar
   adresa consolei o găsești în setările acelui adaptor, pe PC.
2. Conectează-te cu `ssh root@<adresa consolei>`. Parola implicită este `autobleem`.

În locul parolei poți folosi o cheie. Pune cheia ta publică în fișierul `System/ssh/authorized_keys` de pe stick și
repornește consola: la următoarea pornire e adăugată la contul root. Actualizarea sau reinstalarea lansatorului nu o
elimină.

> **Parola implicită e aceeași pe toate consolele**, așa că oricine poate băga un cablu în a ta se poate conecta ca
> root. Folosește o cheie oriunde poți și nu lăsa o consolă cu parola implicită acolo unde alții au acces la ea.

<!-- pagebreak -->

## 7. Dacă ceva nu merge

Cele mai multe probleme au o cauză simplă. Mai jos, fiecare începe cu ce vezi, spune de ce se întâmplă și apoi ce
e de făcut. Dacă ai nevoie să ceri ajutor, jurnalele sunt primul lucru pe care ți-l va cere oricine, așa că ele vin
primele.

**Unde găsești jurnalele.** AutoBleem își ține jurnalele în memorie cât rulează, ca să nu scrie tot timpul pe stick.
Ajung în `System/Logs/` pe stick, pe card sau în folderul de date doar când ceva n-a mers: când lansatorul, un joc
PS1 sau RetroArch se blochează și se închide, jurnalele sunt salvate în `System/Logs/crash-<n>/` (se păstrează
ultimele trei căderi), iar lansatorul îți spune o dată, când revine. Dacă urmărești o problemă care nu e o cădere,
păstrează toate jurnalele: pornește Opțiuni → *Diagnosticare* → *Păstrează jurnalele pe stick* (are efect de la
următoarea pornire) sau creează de pe un PC un fișier gol `System/Logs/keep`. *Informatii hardware* (secțiunea 4.2)
arată și el unde sunt jurnalele, iar Square acolo salvează jurnalele curente în `System/Logs/saved-<n>/`.

Iată fișierele pe care le găsești:

| Fișier | Ce îți spune |
|---|---|
| `autobleem.log` | Ce a făcut lansatorul însuși. |
| `launch.log`, `pcsx.log` | Cum a fost pornit un joc PS1 și ce a spus emulatorul cât a rulat. |
| `retroarch.log` | Ce a spus RetroArch cât a rulat. |
| `update.log` | Cum a decurs o actualizare online; se păstrează mereu pe stick. |
| `updateroms.log` | Cum a decurs UpdateRoms pe PC (capitolul 5); se păstrează mereu pe stick. |

**O imagine îți cere să introduci stick-ul sau consola a intrat în repaus.** AutoBleem nu-și găsește stick-ul: nu
era introdus când a pornit consola sau a fost scos. Pune-l în orice port USB (cel mai bine într-unul din față,
secțiunea 2.1) înainte să treacă cele 5 minute, sau apasă Power. Dacă stick-ul n-a fost scos corect, AutoBleem îl
verifică mai întâi - așteaptă să se termine bara de progres.

**RetroArch spune că *needs a newer system library than this console has*.** Acel RetroArch a fost compilat pentru
un sistem mai nou decât cel al consolei, așa că nu poate rula pe ea. Folosește RetroArch-ul care vine cu AutoBleem.

**Un joc spune că *is protected by its PSN license and cannot be started*.** Jocurile cumpărate din PlayStation
Network sunt legate de licența lor, iar AutoBleem nu le poate rula. Nu e nimic de reparat.

**Un joc nu apare pe raft.** De obicei, folderul lui nu e organizat cum se așteaptă scanarea. Verifică dacă fiecare
joc are folderul lui și e într-unul dintre formatele din secțiunea 3.10. *Manager jocuri* (secțiunea 4.1) arată,
după jocuri, folderele refuzate de scanare, marcate *Neadăugat*, și îți spune de ce a fost refuzat fiecare; Square
șterge un astfel de folder. După ce ai reparat un folder, *Rescaneaza jocurile* din meniul sistem rulează din nou
scanarea.

**Jocurile n-au coperți.** Fie bazele de date cu coperți n-au fost instalate - rulează din nou programul de
instalare, cu ele bifate -, fie, pentru jocurile RetroArch de pe o consolă, UpdateRoms n-a fost încă rulat pe PC
(capitolul 5).

**Un controler nu face nimic sau are butoanele amestecate.** AutoBleem nu cunoaște așezarea butoanelor acelui
controler. Pe o consolă, mapează-l cu asistentul de mapare a controlerului din PSC-Bios (secțiunea 6.1). Pe un Pi
sau pe un PC, pagina Informatii hardware (secțiunea 4.2) arată ce vede sistemul din controler, ceea ce te ajută să
afli dacă e detectat măcar.

**Ecranul rămâne negru după un joc pe consolă.** Imaginea lansatorului nu a revenit când s-a terminat jocul.
AutoBleem își reface singur fereastra, de până la trei ori. Dacă ecranul tot rămâne negru, ține apăsat butonul Power
și pornește din nou consola.

**Pe un Raspberry Pi** poți ajunge în spatele lansatorului când ai nevoie: `Alt+F2` îți dă un prompt de autentificare
pe a doua consolă, iar SSH e activat de la prima pornire. `sudo journalctl -u autobleem` arată ce a făcut serviciul
lansatorului, iar `sudo systemctl restart autobleem` îl repornește. Dacă prima pornire nu s-a putut termina pentru că
nu exista rețea, încearcă din nou la următoarea pornire.

**Pe Windows**, `Esc` închide lansatorul. Folderul tău de date e cel ales la instalare (`Documents\AutoBleem`, dacă
nu l-ai schimbat), iar jurnalele sunt în folderul lui `System\Logs`.

**Consola repornește iar și iar după o actualizare online (stick formatat ext4).** Unii își formatează stick-ul ca
ext4, sistemul de fișiere Linux, în loc de FAT32 sau exFAT. Până la următoarea versiune AutoBleem, o actualizare
online pe un astfel de stick dezarhivează fiecare fișier fără permisiunea care îi dă voie să ruleze ca program.
AutoBleem nu mai poate porni atunci, iar consola repornește la nesfârșit. Stick-urile FAT32 și exFAT nu sunt
afectate. Există două feluri de a rezolva problema.

**Soluția A** are nevoie de un PC cu Linux. Conectează stick-ul și fă din nou executabile programele AutoBleem. Pune
calea ta de montare în locul lui `/media/USER/STICK`; ultimul rând îți trebuie doar dacă e instalat RetroArch:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Soluția B**: instalează din nou pe stick cea mai nouă versiune AutoBleem, ca în secțiunea 2.1. Programul de
instalare are nevoie de un PC care poate citi stick-ul. Dacă nu-l poate citi pe al tău, stick-ul trebuie formatat
mai întâi, ceea ce șterge tot de pe el - copiază-ți jocurile de pe el înainte.

> Ca să eviți asta, folosește **FAT32** (o consolă nemodificată citește doar FAT32; exFAT are nevoie de kernelul
> AutoBleem, capitolul 6). Următoarea versiune păstrează permisiunile, iar AutoBleem le repară la fiecare pornire.

AutoBleem este software liber (GNU GPL v3 sau o versiune ulterioară) și vine fără nicio garanție. Pentru ajutor și
noutăți, intră pe serverul Discord indicat în ecranul Despre sau vizitează https://autobleem.retromenele.pl/.
