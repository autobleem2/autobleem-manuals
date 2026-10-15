# Manual de l'utilizaire d'AutoBleem 2

AutoBleem 2 es un lançador de jòcs per la **PlayStation Classic** e, dempuèi la version 2, tanben per una
**Raspberry Pi**, un **PC aviat dempuèi una clau USB** e **Windows**. Vos presenta vòstres jòcs PS1 coma una
estatgièra de cobèrturas, amb l'imatge de la bóstia e las entresenhas de cada jòc, los aviá dins l'emulador PCSX
que i es inclús e, se RetroArch es installat al costat, vos fa jogar tanben als jòcs d'autras consòlas. Aqueste
manual explica cossí l'installar sus cada plataforma, cossí s'en servir cada jorn e de qué servisson los espleches
que l'acompanhan.

> Los telecargaments de totas las plataformas se tròban sus **https://autobleem.retromenele.pl/**. La pagina es
> ordenada per plataforma : çò que telecargatz es lo panèl *Install* de cadun ; los *Build inputs* que venon
> dessota, los installadors los van quèrre solets.

## 1. Çò que vos aporta

AutoBleem fa de vòstra PlayStation Classic, o d'una Raspberry Pi, d'un vièlh PC o de vòstre ordenador Windows,
una pichona consòla de jòc amb un menú vertadièr per vòstres pròpris jòcs. Vaquí çò que i trobatz :

- **Lo lançador.** Es çò que vesètz en alucant la maquina : una estatgièra de cobèrturas que fasètz desfilar, amb
  las entresenhas del jòc causit al costat. D'aquí aviatz los jòcs, los rengatz en colleccions (PlayStation,
  RetroArch, aplicacions), cambiatz los paramètres, gerissètz las cartas memòria e los estats salvats, e
  telecargatz d'aplicacions e de jòcs dempuèi la Botiga. Sus totas las plataformas a la meteissa cara e
  fonciona parièr.
- **Dos emuladors PS1.** `pcsx-abnxt` es lo modèrne, causit per defaut ; `pcsx-ab` es l'emulador classic
  qu'AutoBleem a totjorn provesit. Causissètz l'un o l'autre dins las opcions. Partejan los meteisses paramètres
  e las meteissas cartas memòria : podètz passar de l'un a l'autre quand volètz, sens res perdre.
- **RetroArch**, se volètz tanben los jòcs d'autras consòlas : NES, SNES, Mega Drive, Game Boy, bòrnas d'arcada e
  fòrça autras. Es facultatiu pertot. Copiatz-i vòstras ROM, e AutoBleem las ren en listas e aviá cada jòc amb lo
  bon core. Los jòcs PlayStation pòdon tanben virar dins RetroArch : son core *PlayStation 1* es en cima de la
  lista dels cores (seccion 3.9). Los jòcs coma Doom viran amb vòstres pròpris fichièrs de jòc, plaçats dins un
  dossièr `Packages` (seccion 3.10).
- **Los espleches de la consòla.** *PSC-Bios*, que dins los menús s'apèla *Ret e manetas*, configura la WiFi,
  l'ora, las manetas Bluetooth e l'assignacion dels botons, tant sus la consòla coma sus una Raspberry Pi o la clau
  PC. *ABFlashKit* installa lo nucli AutoBleem sus una PlayStation Classic (capítol 6).
- **UpdateRoms** per Windows. La PlayStation Classic a pas de ret pròpria : aqueste programa de PC refresca las
  listas RetroArch e va quèrre las cobèrturas per una clau de consòla, tre que la brancatz sus vòstre PC.

![Lo lançador : l'estatgièra de cobèrturas, las entresenhas del jòc causit, las ajudas dels botons](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Installacion

### 2.1 PlayStation Classic

AutoBleem vira entièrament dempuèi una clau USB. Dins la consòla, res es pas modificat : levatz la clau e la
consòla fonciona exactament coma abans. Vos cal pas qu'un PC Windows, una clau USB (USB 2.0, 8 GB o mai) e la
consòla.

La clau a pas besonh d'èsser voida, e **es pas formatada** se o demandatz pas : AutoBleem s'installa al costat de
çò que i a ja dessús, e una clau qu'utilizatz ja amb AutoBleem 1.0 es mesa a jorn sus plaça (vejatz mai bas). Per
una consòla d'origina, la clau deu èsser en **FAT32**, que lo nucli de la consòla sap pas legir l'exFAT. Un còp lo
nucli AutoBleem installat (ABFlashKit, capítol 6), la consòla s'avia tanben dempuèi una clau exFAT, e la limita de
4 GB per fichièr de FAT32 desaparéis.

1. Telecargatz **AutoBleemInstaller-<version>.zip** dins lo panèl PlayStation Classic del site e
   descompressatz-lo ont volètz. I trobaretz `AutoBleemInstaller.exe` e son README. AutoBleem el meteis es
   telecargat pendent l'installacion : lo PC deu doncas èsser connectat a internet.
2. Brancatz la clau e aviatz `AutoBleemInstaller.exe`. Causissètz lo **canal** : *Release* es la version
   ensajada, la que conven a la màger part del monde ; *Testing* es la version venenta, en cors d'ensag ;
   *Nightly* es la construccion de desvolopament mai recenta, que pòt quitament pas foncionar. Puèi causissètz
   lo lector de la clau. La linha dessota vos ditz quina version d'AutoBleem anatz installar e çò que i a ara sus
   la clau : *a fresh install* (installacion novèla, los autres fichièrs de la clau son pas tocats) o *AutoBleem
   <version> is on this stick: it will be updated* (la clau serà mesa a jorn ; vòstres jòcs, salvaments, cartas
   memòria e paramètres demòran).
   **Avètz pas besonh de formatar.** Lo boton **Format** al costat del lector es sonque per una clau novèla sens
   sistèma de fichièrs, per una clau que la consòla sap pas legir (en NTFS, per exemple) o per una clau que volètz
   escafar del tot. Vos o demanda abans, puèi escafa tot çò qu'es sus la clau. Causissètz-i FAT32, levat se la
   consòla a ja lo nucli AutoBleem.
   Puèi marcatz çò que volètz installar :
   - **Basas de cobèrturas** : las cobèrturas e las descripcions de tota la logitèca PS1, per que vòstres jòcs
     agan lor cobèrtura solets (marcat per defaut ; a l'entorn de 300 MB).
   - **RetroArch** : RetroArch amb sos cores, d'aplicacions en mai (Doom, Quake, Amiga...) e los elements de
     libretro, pels jòcs d'autras consòlas. Desactivat per defaut ; lo podètz apondre puèi en tornant aviar
     l'installador.
   - **Fichièrs BIOS** : los fichièrs BIOS que d'unes cores RetroArch demandan per s'aviar (sonque amb
     RetroArch).
   - **Jòcs d'exemple** : qualques jòcs amators gratuits, per que l'estatgièra siá pas voida a la primièra
     aviada.
3. Quichatz **Install** e esperatz. Las barras de progression e lo jornal mòstran cada etapa. A la fin, la clau
   pòrta lo nom `SONY` e recep una còpia d'`UpdateRoms` (vejatz lo capítol 5).
4. Levatz la clau amb seguretat, brancatz-la sul **segond pòrt USB de davant** de la consòla (lo de drecha, lo del
   jogaire 2) ; lo primièr demòra liure per la maneta. Alucatz la consòla : en plaça del menú d'origina, es
   AutoBleem que s'avia. Per una segonda maneta, prenètz un concentrador USB sul pòrt de davant o una maneta
   Bluetooth.

**Alucar e atudar.** Amb la clau dedins, la consòla s'avia, sa lum pampalheja qualques segondas pendent que
reconeis AutoBleem, puèi passa en velha abans que res aparesca a l'ecran. Es normal : AutoBleem s'avia pel
mecanisme de mesa a jorn de la consòla, e aquel mecanisme fonciona atal. Quichatz un còp **Power** e lo lançador
apareis.

Quand causissètz *Atudar* dins lo menú sistèma, o que quichatz lo boton Power de la consòla, aquesta passa en
**velha AutoBleem** : AutoBleem desconnècta d'en primièr la clau amb seguretat, puèi la lum ven **irange**, signe
que tot s'es plan passat. Lo còp que ven que quichatz Power, lo lançador torna en qualques segondas. **Tant que la
lum es irange, podètz levar la clau** e la metre dins vòstre PC ; Windows vos demandarà pas de la verificar, que
foguèt desconnectada coma cal. Tornatz-la metre abans de quichar Power. Se desbrancatz lo cable d'alimentacion de
la consòla, tornarà passar per la velha d'aviada lo còp que ven. Una lum **roja** vòl dire que la consòla es
vertadièrament atudada.

**Lo pòrt de darrièr.** Lo pòrt micro-USB de darrièr es lo de l'alimentacion de la consòla. Amb lo nucli
AutoBleem, pòt tanben recebre un periferic USB, mas la clau a sa plaça sus un pòrt de davant.

**Se la clau i es pas.** Quand la consòla s'avia sens clau, o que levatz la clau mentre qu'AutoBleem vira, un
imatge vos demanda de la metre : n'importa quin pòrt USB conven. AutoBleem espèra 5 minutas, puèi endormís la
consòla ; quichatz Power se la volètz endormir tot ara.

![L'imatge que demanda la clau](../images/en/insert-stick.jpg)

**Quand la clau es verificada.** Se la clau foguèt pas desconnectada coma cal (l'avètz levada mentre
qu'AutoBleem virava, o lo corrent se copèt), AutoBleem la verifica abans de la tornar utilizar : a l'aviada, al
reviscòl o quand la tornatz brancar. Una barra de progression mòstra ont ne es la verificacion. Sus una clau
bèla, aquò pòt durar un moment ; daissatz-la acabar e atudetz pas la consòla pendent aquel temps.

![La verificacion de la clau](../images/en/stick-check.jpg)

**Metre a jorn.** Per metre a jorn una clau, tornatz aviar l'installador dessús : ara lo boton ditz *Update*.
Installa la version mai recenta del canal que causissètz ; vòstres jòcs, salvaments, paramètres e lo contengut
RetroArch demòran, e sonque los fichièrs d'AutoBleem el meteis son remplaçats. Una consòla amb lo nucli AutoBleem
e la WiFi se pòt tanben metre a jorn soleta (seccion 3.12).

**Passar d'AutoBleem 1.0 (o d'AutoBleem-NG).** Utilizatz lo meteis installador sus la meteissa clau, sens la
formatar :

1. D'en primièr, copiatz tota la clau sus vòstre PC, coma salvagarda, per mai de seguretat.
2. Brancatz-la, aviatz `AutoBleemInstaller.exe` e causissètz lo canal e lo lector. Quichetz **pas** Format.
3. Quichatz **Install**. L'installador passa de l'ancian ordenament al novèl : RetroArch, las ROM e los tèmas van
   ont AutoBleem 2 los espèra, e los ancians dossièrs de ROM (`nes`, `snes`...) prenon los noms de sistèma de
   RetroArch. Vòstres jòcs, estats salvats, cartas memòria, ROM e salvaments RetroArch demòran totes, e
   `config.ini` tanben : sonque son emulador PS1 passa a pcsx-abnxt.
4. Tornatz metre la clau dins la consòla. Lo primièr escandalhatge refà la lista dels jòcs e las listas de lectura.
   Per aver las cobèrturas de vòstres jòcs RetroArch, aviatz UpdateRoms sul PC (capítol 5).

> La consòla d'origina a ni relòtge ni ret. Las datas apareisson sonque un còp lo nucli AutoBleem installat
> (capítol 6), e las cobèrturas dels jòcs RetroArch venon d'UpdateRoms sul PC (capítol 5).

Vòstres jòcs PS1 van dins lo dossièr `Games` de la clau, un dossièr per jòc ; la seccion 3.10 n'explica
l'ordenament.

### 2.2 Raspberry Pi

Amb AutoBleem, una Raspberry Pi ven una pichona consòla : s'avia dirèctament sul lançador, sens cap de burèu
entremièg. Lo site prepausa doas imatges de carta prèstas, 32 bits e 64 bits, e un paquet per un Raspberry Pi OS
Lite qu'avètz ja.

| Modèl | Imatge 32 bits | Imatge 64 bits | Nòtas |
|---|---|---|---|
| Raspberry Pi 5 | òc | òc | |
| Raspberry Pi 4 Model B, Pi 400 | òc | òc | |
| Raspberry Pi 3 Model B / B+ / A+ | òc | òc | va plan pel lançador e la PS1 |
| Raspberry Pi Zero 2 W | òc | òc | 512 MB de RAM : la PS1 vira, los cores RetroArch mai pesucs non |
| Raspberry Pi 2 Model B | òc | sonque v1.2 | lenta per tot çò qu'es en 3D |
| Raspberry Pi 1, Zero, Zero W | non | non | ARMv6 : cap dels dos imatges i vira pas |

**Pels jòcs PS1, prenètz l'imatge 32 bits.** Lo recompilador ARM rapid del `pcsx-ab` classic existís sonque en
32 bits : los jòcs PS1 viran doncas mai lentament sus la version 64 bits. L'imatge 64 bits a mai de cores
RetroArch ; prenètz-lo se las autras consòlas vos tenon mai a còr que la PS1.

**Amb Raspberry Pi Imager :**

1. Installatz Raspberry Pi Imager (raspberrypi.com/software). Dins *Choose OS*, causissètz *Use custom* e lo
   fichièr `autobleem-<version>-rpi-armhf.img.xz` (32 bits) o `-arm64.img.xz` (64 bits) qu'avètz telecargat ; o
   ben apondètz una adreça de depaus dins los paramètres de l'aplicacion e causissètz AutoBleem dins la lista.
   N'i a una per canal : `https://autobleem.retromenele.pl/rpi-imager/os_list.json` per la darrièra version
   publicada, `.../os_list-testing.json` per la version en cors d'ensag e `.../os_list-nightly.json` per la
   construccion de desvolopament mai recenta. L'onglet Raspberry Pi de la pagina de telecargament mòstra las que
   existisson, cadun amb son boton *Copy*.
2. Dins l'ecran de personalizacion d'Imager (l'engranatge, o la question après *Next*), definissètz **lo nom
   d'utilizaire e lo senhal, la ret WiFi e lo país, e activatz SSH**. AutoBleem a besonh d'una ret a sa primièra
   aviada.
3. Escrivètz la carta, metètz-la dins la Pi amb un ecran e un clavièr o una maneta, e alucatz.

**La primièra aviada** dura de 5 a 25 minutas, e l'ecran vos ditz çò que se passa. S'i a pas de ret, vos ne
demanda una : causissètz vòstra WiFi dins la lista e picatz lo senhal. Puèi vos demanda s'installa RetroArch ; se
respondètz pas dins la minuta, l'installa. Après aquò, agrandís la particion sistèma, fa del demai de la carta la
particion `AUTOBLEEM` per vòstres jòcs, installa RetroArch e sos cores, los paquets BIOS e los jòcs d'exemple, e
tòrna aviar sul lançador.

S'avètz mai d'enveja de respondre pas a cap de question a la primièra aviada, escrivètz las responsas d'avança
dins **`autobleem.txt`**, sus la particion d'aviada de la carta ; n'importa quin PC lo pòt dobrir e modificar :

| Clau | Per defaut | Significacion |
|---|---|---|
| `root_gib` | 8 | La talha de la particion sistèma en GiB ; lo demai ven la particion dels jòcs. |
| `hdmi_mode` | 1920x1080@60 | Lo mòde d'ecran per tota l'aviada (`1280x720@60` per una television mai anciana). |
| `retroarch` | (demandat) | `yes` / `no` : RetroArch e las autras consòlas, o sonque la PS1. |
| `thumbnails` | none | `boxarts` copia tot lo jòc de cobèrturas, per aver las cobèrturas sens ret (~9000 fichièrs). |
| `bios`, `downloads`, `samples` | yes | Metètz `no` per sautar los paquets BIOS, totes los telecargaments o los jòcs d'exemple. |

**Sus un Raspberry Pi OS Lite qu'avètz ja** (Bookworm o Trixie) : copiatz `autobleem-rpi.tar.gz` (o lo d'arm64)
sus la Pi, descompressatz-lo e aviatz `sudo bash install.sh`. Pausa las meteissas questions, fa de plaça per la
particion de donadas en reduson la particion sistèma a l'aviada seguenta (`--shrink-root <GiB>`), e mete lo
lançador sus la primièra consòla.

Un còp l'installacion facha, emplenatz la **particion `AUTOBLEEM`** de la carta (exFAT) amb vòstres jòcs :
levatz la carta e dobrissètz-la sus n'importa quin PC, o copiatz per la ret (SSH es activat). Los jòcs PS1 van
dins `Games/`, las ROM de las autras consòlas dins `RetroArch/roms/<system>/`, lo BIOS PS1 dins `System/Bios/`
(seccion 3.11) e los tèmas dins `Themes/`.

### 2.3 Clau USB per PC

Lo meteis principi per tot PC que se pòt aviar dempuèi l'USB : la clau aviá lo PC dirèctament sus AutoBleem e
tòca pas al disc del PC. Es un sistèma de 32 bits, doncas las maquinas vièlhas van tanben.

1. Escrivètz l'imatge sus una clau de 8 GB o mai. **Sus Windows**, utilizatz **AutoBleemFlasher** (panèl PC del
   site ; descompressatz-lo e aviatz `AutoBleemFlasher.exe` ; demanda los dreches d'administrator, que escriu
   un disc entièr) : causissètz lo canal e la clau, quichatz *Write* e confirmatz doas vegadas. Telecarga
   l'imatge, lo verifica, l'escriu e lo relegís. Vos prepausa sonque de claus USB e de cartas SD, jamai lo disc
   ont vira Windows, e **tot çò qu'es sus la clau causida es escafat**. Sus Linux o macOS, telecargatz
   `autobleem-<version>-pcusb-i386.img.xz` dins lo panèl PC e escrivètz-lo amb
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (o balenaEtcher).
2. Aviatz lo PC dempuèi la clau (amb la tòca del menú d'aviada de vòstre PC : F12, F8, Esc...). L'aviada BIOS e
   l'aviada UEFI foncionan totas doas ; **Secure Boot deu èsser desactivat**.
3. La primièra aviada se passa coma sus la Pi : demanda una ret se i a pas de cable brancat, vos demanda per
   RetroArch, installa tot (a l'entorn de uèit minutas amb una ret filara) e tòrna aviar sul lançador.

Après aquò, la clau a una particion `AUTOBLEEM` per vòstres jòcs. Brancatz la clau sus un PC Windows 10 en marcha
(version 1903 o mai recenta) : apareis coma un segond lector ont podètz copiar de jòcs. `autobleem.txt` es sus la
primièra particion, amb las meteissas claus que sus la Pi (levat `hdmi_mode` : un PC utiliza totjorn lo mòde
pròpri de l'ecran).

### 2.4 Windows

Se volètz AutoBleem sus vòstre ordenador Windows, vira tanben coma un programa ordinari : en ecran complet, amb
los emuladors e RetroArch aviats coma programas a despart.

1. Telecargatz **AutoBleemSetup-<version>.exe** e aviatz-lo. S'installa per utilizaire, sens dreches
   d'administrator : lo programa dins `%LOCALAPPDATA%\Programs\AutoBleem`, las donadas (jòcs, paramètres, tèmas,
   RetroArch) dins un dossièr que causissètz, `Documents\AutoBleem` per defaut.
2. Marcatz los components (las basas de cobèrturas, RetroArch amb la version Windows oficiala e sos cores, los
   fichièrs BIOS, los jòcs d'exemple) e daissatz l'assistent d'installacion los telecargar.
3. Aviatz AutoBleem dempuèi lo menú Aviar o lo Burèu. Sus un PC, lo clavièr fa de maneta (seccion 3.2).

Per metre a jorn, aviatz un installador mai recent per dessús : lo programa es remplaçat e vòstre dossièr de
donadas demòra coma es. Lo lançador verifica tanben lo site un còp per jorn e vos prepausa una mesa a jorn quand
n'i a una (seccion 3.12).

<!-- pagebreak -->

## 3. Utilizar AutoBleem

### 3.1 Lo lançador

Lo lançador es l'endrech ont causissètz a qué jogar. Vos mòstra vòstres jòcs coma una estatgièra de cobèrturas,
tal coma veiriatz las bóstias sus una estatgièra vertadièra, e la percorrètz fins que trobetz lo que volètz. Tot
lo demai d'AutoBleem (los paramètres, las cartas memòria, la Botiga) se dobrís d'aquí, e i tornatz quand quitatz
un jòc.

Lo jòc causit es al mitan de l'estatgièra, amb un rebat doç dessota. Al costat, vesètz sas entresenhas dins una
pichona grasilha : l'editor, l'annada, lo numèro de seria, la region, lo nombre de jogaires e la darrièra
partida. Quand AutoBleem coneis pas una d'aquelas entresenhas, daissa tombar la linha puslèu que de l'afichar
voida. Un boton de lectura es al costat de las entresenhas. Un jòc sens imatge de cobèrtura es mostrat coma un
disc pausat dins lo suport negre d'una bóstia voida : atal, a totjorn sa plaça sus l'estatgièra.

L'aparéncia del lançador ven de son tèma. Lo tèma per defaut es **ab2.0.0** : una installacion novèla i passa, e
una mesa a jorn que l'aporta tanben, mas un sol còp ; se causissètz un autre tèma puèi (seccion 3.6), aquel
demòra.

**La barra d'ajuda**, en bas de l'ecran, vos ditz çò que fan los botons a aquel moment. A doas linhas de quatre
cases. La primièra tòca lo jòc causit : lo jogar, lo jogar dins RetroArch, dobrir la rengada d'icònas dessota, o
dobrir lo Menú rapid. La segonda cambia pas jamai : Select causís la colleccion, Start tira un jòc a l'azard,
Triangle mòstra la guida dels botons e L2 + R2 dobrís lo menú sistèma. Una ajuda es atenuada quand son boton a
pas res a far.

**Trobar solet los jòcs novèls.** Cada còp que lo lançador s'avia, escandalha vòstre dossièr de jòcs en rèire
plan : un jòc que i avètz copiat mentre que la maquina èra atudada apareis sens que fagatz res. Pendent
l'escandalhatge, una anóncia en naut a drecha mòstra ont ne es, e los jòcs novèls apareisson sus l'estatgièra a
mesura que son trobats ; podètz contunhar de percórrer pendent aquel temps.

**Una installacion novèla** a pas encara de jòcs. En plaça d'una estatgièra voida, vesètz una carta
d'aculhença, *Bonjorn e benvenguda a AutoBleem !*, que vos ditz de metre vòstres jòcs dins `Games` e de causir
*Tornar escandalhar los jòcs*. Nomena l'endrech segon vòstra plataforma : sus vòstra clau (PlayStation Classic,
clau PC), sus vòstra carta SD (Raspberry Pi) o dins vòstre dossièr AutoBleem (Windows). La carta s'escafa tre
qu'un escandalhatge tròba lo primièr jòc.

**Las anóncias** son las bulas en naut a drecha. Vos tenon al fial sens vos destorbar : l'avançament de
l'escandalhatge, lo nom de la colleccion que venètz de causir (*Afichatge : ...*), una maneta qu'a gaire de
batariá, un avís après un plantatge, un processor d'escandalhatge al trabalh, e un telecargament de la Botiga. La
bula d'un telecargament mòstra sa velocitat e lo temps que demòra, per exemple `1.4 MB/s · 0:42`. Quant de temps
demòran las bulas d'informacion, aquò depend de vos : Opcions → *Durada de l'anóncia:*.

**Las batariás de las manetas.** Sus la consòla, una Raspberry Pi e la clau PC (pas sus Windows), cada maneta
sens fial que dona son nivèl de batariá apareis coma una pichona icòna amb son percentatge, sus sa pròpria placa,
e las placas s'apilan a partir del canton en naut a esquèrra. Una maneta que jòga coma jogaire 1 o jogaire 2
pòrta l'etiqueta P1 o P2, segon l'opcion *Escambiar jogaire 1 / jogaire 2 (emuladors PS1):* (seccion 3.6) ; una
maneta qu'es pas associada a cap de jogaire, o una tresena maneta, a pas d'etiqueta. Quand la batariá d'una maneta
baissa, una anóncia vos o ditz un còp, amb lo nom de la maneta e lo percentatge.

**L'etiqueta de canal.** Se fasètz virar una version qu'es pas una version finala, una pichona etiqueta dessota
la placa de batariá, en naut a esquèrra, vos o rapèla. Es una pastilha amb lo canal e la version corta al
costat : `ALPHA`, `BETA` o `RC` per una preversion, `TESTING` per tota autra preversion, `NIGHTLY` per una
construccion nocturna, e `DEV` per una version compilada a la man (per `DEV`, la version es lo commit que ne
sortiguèt). Una version publicada mòstra pas cap d'etiqueta.

![Lo causidor de colleccions : tres onglets, e los grops de l'onglet actual amb lor nombre de jòcs](../images/en/set-picker.jpg)

### 3.2 Las comandas

AutoBleem es fach per s'utilizar sonque amb la maneta, e los botons vòlon dire la meteissa causa sus totes los
ecrans : Cross confirma, Circle tòrna en rèire, Triangle ajuda. S'oblidatz çò que fa un boton, la barra d'ajuda en
bas de l'ecran vos o ditz, e Triangle sus l'estatgièra dobrís la guida dels botons, amb totes los botons de totes
los ecrans (seccion 4.3). Vaquí çò que fan los botons sus l'estatgièra :

| Boton | Sus l'estatgièra |
|---|---|
| Esquèrra / Drecha | Passa al jòc precedent o seguent ; tenètz lo boton quichat per contunhar de desfilar. |
| L1 / R1 | Saura a la primièra letra precedenta o seguenta dels títols, per traversar lèu una estatgièra longa. Sus una estatgièra voida amb un lector USB brancat, R1 dobrís *Disc* (seccion 3.9a). |
| Cross | Aviá lo jòc causit : un jòc PS1 dins l'emulador PS1, un jòc RetroArch dins son core, e una aplicacion après son legissetz-me. |
| Square | Aviá lo jòc PS1 causit dins RetroArch puslèu. Quand un disc dins un lector USB es causit, copia lo disc (*Copiar lo disc*, seccion 3.9a). |
| Circle | Vos torna menar a la vista del disc quand un disc es dins lo lector (seccion 3.9a). |
| Triangle | Dobrís la guida dels botons. |
| Start | Tira un jòc a l'azard dins la colleccion actuala, per quand vos podètz pas decidir. |
| Select | Dobrís lo causidor de colleccions, ont causissètz quins jòcs mòstra l'estatgièra (seccion 3.3). |
| Amont | Dobrís lo Menú rapid (seccion 3.4). |
| Avall | Dobrís la rengada d'icònas dessota lo jòc (*PARAMÈTRES*, *Jòc*, *CARTA MEMÒRIA*, *REPRENDRE*) ; Amont la tòrna barrar. |
| L2 + R2 | Dobrís lo menú sistèma (seccion 3.5). |

**Amb un clavièr.** Sus un PC sens maneta, o amb un clavièr USB sus la consòla, una Pi o la clau PC, las tòcas
remplaçan los botons. Las sagetas fan la crotz direccionala, Entrada es Cross, Esc o Retorn arrièr es Circle, Tab
es Triangle e Espaci es Square. F1 e F2 son Select e Start, Pagina amont e Pagina avall son L1 e R1, Origina e Fin
son L2 e R2, e F10 dobrís lo menú sistèma.

Sus Windows, qualques tòcas cambian. Esc i tampa AutoBleem (capítol 7) ; Circle es doncas sonque Retorn arrièr,
Espaci es Start e S es Square. Las letras pòdon tanben remplaçar tota la maneta, sens passar per las sagetas : X,
O, S e T son Cross, Circle, Square e Triangle, I, J, K e L la crotz direccionala (amont, esquèrra, aval, drecha),
B es Select, Q e E son L1 e R1, 1 e 2 son L2 e R2.

**Dins totas las listas e totes los menús**, los meteisses gestes foncionan : Amont e Avall desplaçan lo cursor,
L2 e R2 viran una pagina, L1 e R1 sautan a la primièra o a la darrièra linha, Cross causís e Circle tòrna en
rèire. Avètz pas jamai de cercar un boton per enregistrar : un ecran de paramètres los enregistra quand lo
quitatz amb Circle.

**Sortir d'un jòc o d'una aplicacion.** Tenètz Start + Select, o Home, quichats 2 segondas, e sètz tornats dins
AutoBleem. Aquò fonciona sus totas las manetas : la de la consòla, una maneta USB o una maneta Bluetooth. Una
quichada corta sus los meteisses botons dobrís puslèu lo menú de l'emulador. Una aplicacion a pas aquel menú :
aquí, sonque la quichada longa fa quicòm.

![La rengada d'icònas dessota lo jòc causit](../images/en/launcher-icons.jpg)

### 3.3 Las colleccions

Una granda logitèca se percor mai aisidament per tròces. Las colleccions vos daissan reduire l'estatgièra a una
sola mena de jòcs (sonque vòstres favorits, sonque los jòcs Super Nintendo, sonque los jòcs d'un dossièr), per
pas aver de passar davant de centenats de cobèrturas per trobar la que volètz.

Quichatz **Select** e lo causidor de colleccions se dobrís. A tres onglets, PlayStation, RetroArch e aplicacions :
L1 e R1 passan d'un a l'autre, Amont e Avall percorron los grops de l'onglet (L2 e R2 una pagina a la vegada), e
Cross mòstra sus l'estatgièra lo grop qu'avètz causit. Circle (*Tornar*) barra lo causidor sens res cambiar. Lo
pè de pagina mòstra tanben aquelas tòcas. Cada linha indica quant d'elements conten. Un grop void dobrís una
estatgièra voida, ont la rengada d'icònas prepausa sonque *PARAMÈTRES*.

**L'onglet PlayStation.** Sus una PlayStation Classic, comença per *Totes los jòcs* e *Jòcs intèrnes* (los vint
jòcs integrats a la consòla), seguits de *Jòcs USB*, es a dire tot çò qu'es dins `Games/`, e d'un grop per cada
dossièr qu'i avètz creat : un jòc dins un sosdossièr fa partida del grop d'aquel dossièr. Puèi venon *Jòcs
favorits*, *Istoric dels jòcs* e, tre qu'avètz marcat al mens un jòc coma jòc al pistolet, *Jòcs al pistolet*. Una
Raspberry Pi, una clau PC e Windows an pas de jòcs intèrnes : aquí la lista comença a *Jòcs USB*, qu'es tota
vòstra logitèca.

**L'onglet RetroArch** i es sonque ont RetroArch es installat. A un grop per cada consòla que n'avètz de jòcs, e
tanben los Favorits e l'Istoric de RetroArch.

**L'onglet de las aplicacions** las rengueja per tipe : *Totas las aplicacions*, puèi *Jòcs*, *Emuladors*,
*Espleches*, *Mèdia* e *Autre*. Lo grop d'una aplicacion es definit dins son fichièr `app.ini`. Aqueste onglet
lista tanben las **aplicacions PE**, de programas Windows aviats per l'executador PE ; la que la consòla pòt pas
aviar es marcada *pòt pas foncionar sus aquesta consòla*. Ont lo lançador l'aficha, una linha *Paquets* es tanben
dins la lista (seccion 3.10).

### 3.4 Lo Menú rapid

Lo Menú rapid es una lista corta de las causas que vos servisson mai sovent quand percorrètz vòstres jòcs, per
vos estalviar de las anar cercar dins lo menú sistèma complet. Lo dobrissètz amb **Amont** sus l'estatgièra, o
amb l'**icòna d'engranatge** de la rengada d'icònas (la de *PARAMÈTRES*, *Jòc*, *CARTA MEMÒRIA* e *REPRENDRE*).

Amont e Avall percorron los elements (après lo darrièr, lo cursor torna al primièr), Cross ne causís un e Circle
barra lo menú. Una linha dessota lo menú descriu l'element causit. Vaquí los elements :

- *Tornar escandalhar los jòcs* cèrca sul pic los jòcs novèls, modificats o suprimits ; practic quand venètz de
  copiar de jòcs e volètz pas esperar.
- *Botiga* dobrís la Botiga AutoBleem, ont percorrètz e installatz de jòcs, d'aplicacions e d'extensions (seccion
  3.13).
- *Cores RetroArch*, ont RetroArch es installat, vos daissa causir lo core que fa virar cada consòla.
- *Ret e manetas* dobrís los ecrans de la WiFi, de l'associacion Bluetooth e de l'assignacion de las manetas
  (capítol 6). I es sonque quand una extension installada los provesís : PSC-Bios o fa, sus la consòla, una
  Raspberry Pi e la clau PC. S'aquela extension es installada mas desactivada, l'element es grisat e sa
  descripcion ditz de l'activar dins Extensions ; Cross dobrís alara la lista de las extensions just sus ela.
- *Tornar aviar lo launcher* tampa AutoBleem e lo torna aviar (sonque sus la consòla, una Raspberry Pi e la clau
  PC).
- *Menú sistèma...* dobrís lo menú sistèma complet amb tot lo demai : Opcions, Gestionari de jòcs, Atudar e mai
  (seccion 3.5).

Tot çò qu'es aquí, levat la Botiga, los cores RetroArch e lo reaviament del lançador, es tanben dins lo menú
sistèma.

![Lo Menú rapid](../images/en/quick-menu.jpg)

### 3.5 Lo menú sistèma

Lo menú sistèma recampa tot çò qu'AutoBleem sap far en defòra del jòc : los paramètres, los espleches per vòstra
logitèca e vòstras cartas memòria, las entresenhas sus la maquina, e lo biais d'atudar. Quichatz **L2 + R2**
ensems (dins l'òrdre que volètz) e se dobrís per dessús l'estatgièra. Sos elements son recampats jos los títols
*Bibliotèca*, *Sistèma* e *Quitar*, amb los dos que vos servisson mai en cima. Una linha en bas del menú descriu
l'element causit : podètz doncas far lo torn abans de causir.

| Seccion | Element | Çò que fa |
|---|---|---|
| (cima) | *Tornar escandalhar los jòcs* | Cèrca ara los jòcs novèls, modificats o suprimits. L'escandalhatge susvelha tanben lo dossièr tot solet : n'avètz besonh sonque quand volètz pas esperar. |
| | *Extensions* | Lista las extensions de la clau, coma la Botiga AutoBleem, per las aviar o las desactivar (seccion 3.13). |
| *Bibliotèca* | *Gestionari de jòcs* | Mòstra los jòcs PS1 en lista amb lors dossièrs ; i podètz suprimir un jòc o voidar las cobèrturas (seccion 4.1). Se pòt pas dobrir pendent un escandalhatge. |
| | *Cartas memòria* | Gerís vòstres jòcs de cartas memòria partejadas (seccion 3.8). |
| | *Processors d'escandalhatge* | Definís l'òrdre dels programas que cada escandalhatge fa virar d'en primièr, e los activa o desactiva (seccion 3.14). Se pòt pas dobrir pendent un escandalhatge. |
| *Sistèma* | *Opcions* | Dobrís los paramètres d'AutoBleem (seccion 3.6). |
| | *Ret e manetas* | Dobrís los ecrans de la WiFi, de l'associacion de manetas Bluetooth, de la configuracion de la DualShock 3 e de l'assignacion de las manetas (capítol 6). I es sonque quand una extension los provesís : vejatz mai bas. |
| | *Entresenhas de material* | Mòstra las entresenhas de la maquina (sistèma, CPU, emmagazinatge, interfàcias de ret, fus orari, afichatge, e las manetas amb lors assignacions) sus la meteissa pagina sus totas las plataformas (seccion 4.2). Circle vos torna menar al menú sistèma. |
| | *Virtual gamepad* | Mòstra las manetas balhadas a las aplicacions e las que lo servici vei ; ajuda quand una maneta fonciona pas dins una aplicacion (seccion 4.5). Circle vos torna menar al menú sistèma. |
| | *Mesa a jorn logiciala* | Verifica ara sul site s'i a un AutoBleem o un RetroArch mai recent, sens esperar la verificacion quotidiana (seccion 3.12). Quand lo lançador ne coneis ja una, la linha ditz *Mesa a jorn disponibla*. Sus una PlayStation Classic, cal lo nucli AutoBleem e una ret WiFi. |
| | *A prepaus* | Mòstra los mercejaments e la licéncia. |
| *Quitar* | *RetroArch* | Quita lo lançador pel menú pròpri de RetroArch, per sos paramètres e sas listas de contenguts ; quand tampatz RetroArch, tornatz al lançador. I es sonque ont RetroArch es installat. |
| | *Atudar* | Atuda la maquina après vos aver demandat confirmacion (vejatz mai bas). |

**Ret e manetas** apareis sonque ont una extension installada provesís l'entrada `network`, qu'una extension
declara amb `Provides=network` dins son `extension.ini`. PSC-Bios o fa sus la consòla, una Raspberry Pi e la clau
PC. S'aquela extension es installada mas desactivada, l'element demòra dins lo menú, grisat, e sa descripcion vos
ditz de l'activar dins Extensions ; Cross dessús dobrís la lista de las extensions just sus aquela extension.

**Atudar** fa çò que conven a la maquina. Sus la consòla, la mete en velha AutoBleem : la clau es desconnectada, la
lum ven irange, e Power torna menar lo lançador en qualques segondas (seccion 2.1). Sus una Raspberry Pi o un PC,
la maquina s'atuda.

![Lo menú sistèma](../images/en/system-menu.jpg)

### 3.6 Opcions

Las opcions son l'endrech ont fasètz d'AutoBleem lo vòstre : l'imatge sus vòstre ecran, l'aparéncia del lançador,
la lenga, lo son, l'emulador PS1 que fa virar vòstres jòcs. Las dobrissètz dempuèi lo menú sistèma (*Opcions*) o
amb l'icòna *PARAMÈTRES* dessota un jòc. Lo mai sovent, reglatz l'ecran e la lenga un còp per totas, e i tornatz
quand quicòm sembla pas just sus una television o quand avètz enveja de cambiar.

Los paramètres son rengats en grops, cadun jos un títol. Amont e Avall passan d'una linha a l'autra, Esquèrra e
Drecha cambian la valor de la linha ont sètz : una quichada corta avança d'un pas, un boton tengut contunha. L1 e
R1 sautan a la primièra o a la darrièra linha, e L2 e R2 viran una pagina. Sus una linha que prepausa de tèmas, de
musicas o de poliças, Start ne tira una a l'azard. Un paramètre que s'activa o se desactiva aficha
**ACTIVAT** o **DESACTIVAT**. Vesètz cada cambiament sul pic, e Circle quita l'ecran e enregistra tot ; i a pas res
mai de confirmar. L'unica excepcion es lo mòde d'ecran, qu'es ensajat quand quitatz las opcions (vejatz
*Afichatge :* mai bas).

D'unas linhas apareisson sonque quand an un sens : las linhas CRT sonque amb un imatge 4:3, las linhas RetroArch
sonque ont RetroArch es installat, los jòcs intèrnes sonque sus una PlayStation Classic.

| Grop / paramètre | A qué servís |
|---|---|
| *Interfàcia* : *Afichatge :* | Definís la definicion de l'ecran, pel lançador e per l'emulador PS1. *Auto* utiliza lo mòde pròpri de l'ecran e mòstra lo qual, per exemple *Auto (1920x1080)* ; podètz tanben causir n'importa quin mòde que l'ecran prepausa. La consòla prepausa 720p, 1080p e *CRT 4:3* (720x480), lo mòde per una vièlha television a tub o un aparelh de captura 4:3. Cambiatz-lo quand l'imatge s'adapta pas a vòstra television o sembla borrós. Aquesta linha i es pas quand AutoBleem vira dins una fenèstra sus una maquina de desvolopament. |
| *Marge CRT :* | Las vièlhas televisions copan los bòrds de l'imatge : aqueste paramètre reduch doncas tot un pauc, de 0 a 10 % per pas d'1 %. Aumentatz-lo fins que la barra d'ajuda e los cantons se vejan en entièr. Apareis sonque amb una sortida 4:3, pren efièch sul pic, e s'aplica quitament abans l'ecran d'aviada. |
| *Nautor de l'imatge :* | Fa l'imatge mai naut o mai bas, de -40 a +40 per pas de 2, sus tota sortida 4:3 : *CRT 4:3*, o un mòde 4:3 sus una sortida VGA o PC. Servissètz-vos-en quand l'imatge sus una vièlha television es espotit o depassa en naut e en bas. Pren efièch sul pic, e l'imatge dels jòcs RetroArch lo seguís. |
| *Escalatge de l'ecran de l'emulador :* | Decidís cossí l'emulador PS1 adapta l'imatge d'un jòc a vòstre ecran. *1x1* mòstra los pixèls pròpris de la PlayStation, pichons e exactes ; *2x (entièr)* e *4:3 (entièr)* agrandisson sonque per multiples entièrs, çò que dona l'imatge mai net ; *4:3* garda la forma d'origina de l'imatge ; *Ecran complet* espandís l'imatge sus tot l'ecran. Remplaça l'ancian comutador Widescreen. Lo `pcsx-ab` classic e RetroArch coneisson sonque l'ecran complet e lo 4:3. |
| *Halo d'ecran :* | Quand es *ACTIVAT*, las bandas voidas al costat de l'imatge d'un jòc (ont l'imatge emplena pas l'ecran) son emplenadas amb la lusor doça de l'imatge el meteis puslèu qu'amb de negre. Fonciona amb `pcsx-abnxt`. |
| *Tèma AutoBleem :* | Cambia l'aparéncia del lançador. Los tèmas son dins `Themes/`, e un zip de tèma pausat aquí es tanben listat per son nom. Los tèmas que provesís AutoBleem son refrescats a cada mesa a jorn : se ne volètz personalizar un, copiatz-lo d'en primièr jos un nom novèl. Lo tèma per defaut es **ab2.0.0**. |
| *Estil cobèrtura :* | Causís lo quadre de bóstia de CD dessenhat a l'entorn de las cobèrturas PS1. |
| *Lusor de la cobèrtura :* | Fa passar un rebat sus la cobèrtura causida cada còp que l'estatgièra s'arrèsta. |
| *Lenga :* | Definís la lenga del lançador ; n'i a 17, e lo cambiament es immediat. |
| *Durada de l'anóncia:* | Definís quant de temps demòran las bulas d'informacion (*Afichatge : ...*, lo resumit de l'escandalhatge), de 0 a 20 segondas ; 0 aficha *Desactivat* e las suprimís. Los messatges d'error gardan lor pròpria durada fixa : ne mancaretz pas cap. |
| *Ecran d'aviada:* | Mòstra l'imatge d'AutoBleem pendent que lo lançador s'avia ; desactivatz-lo per anar dirèctament a l'estatgièra. |
| *Animacions:* | Anima lo passatge d'un ecran a l'autre ; desactivatz-lo s'amatz mai que cada ecran aparesca tot d'un còp. |
| *Poliças* : *Utilizar la poliça per defaut:* | Quand es *ACTIVAT*, lo lançador utiliza sa pròpria poliça (Red Hat Text) ; desactivatz-lo per utilizar la poliça causida a la linha seguenta. |
| *Polissa:* | Causís una poliça vòstra : tot fichièr `.ttf` o `.otf` de `resources/fonts`, `RetroArch/fonts` o del dossièr del tèma. La linha mòstra lo nom de la poliça vertadièrament utilizada. |
| *Son* : *Musica :*, *Musica de fons :* | *Musica :* causís lo tròç que jòga jos lo lançador : lo del tèma, o un fichièr de `resources/music`. *Musica de fons :* decidís se i a de musica o pas. |
| *Emulacion* : *Emulador PS1 :* | Causís l'emulador que vòstres jòcs PS1 s'i avian : `pcsx-abnxt`, per defaut (lo PCSX-ReARMed actual amb los apondons d'AutoBleem), o `pcsx-ab`, lo classic. Ensajatz l'autre quand un jòc vira pas plan. Un punt de represa enregistrat per l'un contunha dins l'autre, levat se lo jòc virava sens fichièr BIOS. |
| *Escambiar jogaire 1 / jogaire 2 (emuladors PS1):* | Inverte, dins los dos emuladors PS1, quina de las doas primièras manetas es lo jogaire 1 e quina es lo jogaire 2 : practic quand las manetas son brancadas « al revèrs ». Compta sonque amb doas manetas o mai ; amb una sola, sètz totjorn lo jogaire 1. RetroArch es pas tocat. Se l'emulador PS1 utilizat sap pas encara far l'escambi, AutoBleem vos o ditz. |
| *Jogar a totes los jòcs PSX amb RA :*, *Metre a jorn la configuracion RA :*, *Gardar la config RetroArch :* | Aquestas tres i son sonque ont RetroArch es installat. La primièra aviá totes los jòcs PS1 dins lo core PS1 de RetroArch (*PlayStation 1* ; sus un PC es SwanStation). La segonda permet a AutoBleem d'escriure sos paramètres dins la configuracion de RetroArch quand i aviá un jòc. La tresena garda un cambiament fach dins lo menú pròpri de RetroArch quand RetroArch se tampa. |
| *Bibliotèca* : *Afichar los jòcs intèrnes :* | Mòstra los jòcs integrats de la consòla dins las listas PlayStation (sonque PlayStation Classic). |
| *Noms de jòcs netejats:* | Quand es *ACTIVAT* (per defaut), las listas de jòcs RetroArch mòstran de noms nets, sens las etiquetas entre parentèsis coma (USA), (Rev 1) o [!] ; *DESACTIVAT* mòstra los noms de fichièr. Lo nom de fichièr es totjorn dins las entresenhas del jòc. Los jòcs PS1 son pas tocats, que lors títols venon de la basa de donadas. |
| *Recuperar las cobèrturas en linha :* | Permet a l'escandalhatge de telecargar las cobèrturas mancantas dels servidors de libretro (Raspberry Pi, PC, Windows). |
| *Mesas a jorn* : *Mesas a jorn:* | Causís quinas mesas a jorn lo lançador cèrca (seccion 3.12) : `release` (la version ensajada), `testing` (la version venenta, en cors d'ensag), `nightly` (la construccion de desvolopament mai recenta) o `off`. Per defaut, seguís la version qu'avètz installada. Es pas mostrat sus una maquina de desvolopament. |
| *Diagnostic* : *Gardar los jornals sus la clau :* | Garda totes los jornals sus la clau a partir de l'aviada seguenta, e pas sonque après un plantatge : activatz-lo quand cercatz l'origina d'un problèma (capítol 7). |
| *Afichar las performàncias :* | Aficha en bas a esquèrra la cadéncia d'imatges, la carga del CPU, los fials d'execucion e la memòria ; en jòc, l'emulador mòstra tanben sos FPS e son CPU. |

**Cambiar lo mòde d'ecran.** Quand quitatz las opcions amb un mòde *Afichatge :* novèl, AutoBleem i passa e vos
demanda *Gardar aqueste mòde d'afichatge ?*. Se l'imatge es corrècte, confirmatz. Se vòstra television mòstra pas
res, esperatz : sens confirmacion, AutoBleem torna al mòde precedent al cap d'un comptatge a l'invèrs.

**Los tèmas sus un ecran 4:3.** En mòde *CRT 4:3*, la lista dels tèmas mòstra sonque los que an una disposicion
4:3. Se lo tèma qu'utilizatz n'a pas, lo tèma per defaut pren sa plaça après qu'avètz confirmat lo mòde (e a cada
aviada dins aquel mòde), e un avís vos o ditz : *Tèma remplaçat pel tèma per defaut (CRT 4:3)*.

![Las opcions, per grops](../images/en/options.jpg)

![Lo grop Interfàcia : marge CRT e nautor de l'imatge](../images/en/options-display.jpg)

![L'avís après lo passatge en CRT 4:3 amb un tèma sens disposicion 4:3](../images/en/crt43-theme-notice.jpg)

### 3.7 Los paramètres d'un jòc

Cada jòc pòt aver sos pròpris paramètres. La màger part dels jòcs viran plan coma son, mas de còps un a besonh
d'un pauc d'ajuda (un imatge mai net o mai doç, un imatge sautat per demorar fluid, una autra carta memòria), o
ben lo volètz marcar coma favorit. L'editor de jòc es l'endrech ont cambiatz aquelas causas per aquel jòc sol,
sens tocar als autres.

Amb un jòc causit, quichatz **Avall** per dobrir la rengada d'icònas dessota. A quatre icònas : *PARAMÈTRES* (las
opcions de la seccion 3.6), *Jòc* (los paramètres pròpris d'aqueste jòc), *CARTA MEMÒRIA* (sa carta memòria) e
*REPRENDRE* (sos estats salvats). Anatz sus una e quichatz Cross per la dobrir.

**L'editor de jòc** (l'icòna *Jòc*) mòstra a drecha las entresenhas del jòc (lo títol, l'editor, l'annada, lo
nombre de jogaires, lo dossièr e la carta memòria) e a esquèrra sos paramètres. Amont e Avall passan d'un
paramètre a l'autre e Esquèrra e Drecha los cambian, coma dins las opcions ; un boton tengut repetís lo movement.
Quand avètz acabat, Circle enregistra vòstres cambiaments e vos torna menar en rèire. Un jòc sens títol dins sas
donadas es mostrat jos lo nom de son dossièr.

Los paramètres son en quatre grops :

- **Jòc** tòca la manièra qu'AutoBleem tracta lo jòc. *Favorits :* lo mete dins lo grop *Jòcs favorits* del
  causidor de colleccions. *Verrolhar las donadas :* ditz a l'escandalhatge de daissar lo títol, lo numèro de
  seria e la lista dels discs exactament coma los avètz definits : un escandalhatge ulterior escafarà pas vòstres
  cambiaments. *Represa :* decidís çò que se passa quand aviatz un jòc qu'a de punts de represa : *Demandar*
  mòstra lo causidor de punts de represa, *Darrièr emplaçament* contunha sul pic a partir del mai recent, e *Jamai*
  aviá totjorn lo jòc dempuèi lo començament. Ont RetroArch es installat, i a doas linhas de mai. *Jòc Lightgun:*
  es per un jòc al pistolet : lo jòc dintra dins lo grop *Jòcs al pistolet* e vira totjorn dins RetroArch, que lo
  core PS1 de RetroArch a la GunCon (l'activar activa tanben la linha seguenta). *Jogar amb RA :* fa virar aqueste
  jòc sol dins RetroArch puslèu que dins l'emulador PS1.
- **Afichatge** tòca l'aspècte de l'imatge. *Definicion :* dessenha lo jòc en 1x o en 2x (amb lo GPU integrat), e
  *Levar las juntas :*, que fonciona sonque en 2x, amaga las linhetas finas que pòdon aparéisser entre las
  partidas de l'imatge a aquela talha. *Dithering :* (*Desactivat*, *Activat*, *Totjorn*) regla lo fin motiu de
  punts que la PlayStation utiliza per mesclar las colors, e *Lissatge:* causís un dels escalaires de lissatge de
  l'emulador. *Filtre :* decidís cossí l'imatge es adaptat a l'ecran : *Lo mai pròche* mòstra de pixèls bruts,
  *Linear* los adocís, *Net* e *Net (simple)* gardan los pixèls nets sens fernigament, e i a tanben *Quilez*. Los
  filtres CRT *CRT (fast)*, *CRT (raster)* e *CRT-Pi* imitan una vièlha television e dessenhan lors pròprias
  linhas d'escansion : las linhas de reglatge de las linhas d'escansion venon doncas grisas quand n'es causit un.
  Autrament, *Linhas d'escansion :* apond las linhas escuras d'una vièlha television, e *Luminositat de las linhas
  d'escansion :* regla lor escuresa. *Definicion*, *Levar las juntas*, *Dithering*, *Lissatge* e los filtres
  autres que *Linear* e *Lo mai pròche* son per `pcsx-abnxt` ; lo `pcsx-ab` classic e RetroArch mòstran tot autre
  filtre coma *Lo mai pròche*.
- **Rendut** a l'*Extension :* GPU e *Frameskip :* (*Auto*, *Desactivat*, o d'1 a 3 imatges). Sautar d'imatges
  ajuda un jòc que vira tròp lentament a gardar sa velocitat, al prètz d'un imatge mens fluid.
- **Emulador** a *Hack velocitat :*, la *Frequéncia :* del CPU, *Interpolacion Spu :* (cossí lo son es lissat),
  *Lògo d'aviada:* e, amb `pcsx-abnxt`, *Correctius Sony:*. Desactivatz *Lògo d'aviada:* per sautar l'interfàcia
  del BIOS : n'avètz besonh per un disc amator que son lògo personalizat l'empacha de s'aviar.

La forma de l'imatge e la definicion de l'ecran se reglan pas jòc per jòc mas per totes, dins las opcions
(*Escalatge de l'ecran de l'emulador :* e *Afichatge :*).

**Los autres botons de l'editor.** Triangle renomena lo jòc, amb lo clavièr a l'ecran. Square balha al jòc una
autra carta memòria (*Cambiar la carta memòria*). Tant que lo jòc utiliza encara sa pròpria carta, Start fa
d'aquela carta un jòc de cartas partejadas novèl, que d'autres jòcs pòdon utilizar tanben (*Partejar la carta
memòria*, seccion 3.8). Aquestes dos son pas prepausats pels jòcs intèrnes de la consòla. Tenir quichat
Esquèrra / Drecha o Amont / Avall repetís lo movement aquí, e tanben dins los ecrans d'opcions de jòc e de cores
de RetroArch.

Un jòc garda sos paramètres dins son pròpri fichièr `pcsx.cfg`. Totes los jòcs de la clau n'an un, que l'escan
lo crea. Un disc original dins un lector USB (seccion 3.9a), el, recep son dorsièr e son `pcsx.cfg` sonque al
primièr aviada ; fins alara, un cambiament fach dins l'editor se pòt pas gardar, e l'editor vos ditz *Pas
enregistrat : aqueste jòc a pas de pcsx.cfg*. Aviatz doncas lo disc un còp - puèi, sos paramètres son gardats
coma los de quin autre jòc que siá. Un disc que fa partida d'un jòc ja present dins vòstra colleccion utiliza
tre la debuta lo dorsièr e los paramètres d'aquel jòc.

Per un **disc dins lo lector** (seccion 3.9a), d'unes paramètres an pas de sens : l'editor grisa aquelas linhas, e
la linha d'en bas ditz *Pas disponible per un disc dins lo lector* quand i anatz.

![L'editor de jòc per un disc dins lo lector](../images/en/game-editor-disc.jpg)

**Los paramètres enregistrats dins l'emulador.** Podètz tanben reglar un jòc en i jogant : lo menú pròpri de
l'emulador a *Enregistrar los paramètres per aqueste jòc* (seccion 3.9). Tre qu'un jòc a de paramètres
enregistrats aquí, son aqueles que comptan quand i jogatz. L'editor de jòc mòstra alara sas linhas Afichatge,
Rendut e Emulador grisadas, amb las valors enregistradas, jos lo títol *Enregistrat dins l'emulador* : las podètz
legir mas pas cambiar. S'amatz mai tornar utilizar los paramètres de l'editor de jòc, causissètz *Desblocar los
paramètres* e confirmatz : aquò suprimís los paramètres enregistrats per l'emulador, e las linhas se pòdon tornar
cambiar. Los dos emuladors, `pcsx-ab` e `pcsx-abnxt`, legisson e escrivon los meteisses paramètres enregistrats :
impòrta pas doncas quin los a enregistrats.

![L'editor de jòc](../images/en/game-editor.jpg)

### 3.8 Cartas memòria e estats salvats

Sus una PlayStation vertadièra, partejavatz una o doas cartas memòria entre totes vòstres jòcs, e un jorn o
l'autre i aviá pas pus de plaça. Dins AutoBleem, cada jòc PS1 a per defaut sa pròpria carta memòria : avètz pas
jamai de pensar a la plaça o a la carta ont es un salvament. La carta es gardada amb los estats salvats del jòc
dins `Games/!SaveStates/<game folder>/`.

**Los jòcs de cartas partejadas.** De còps, de jòcs an besonh de veire los salvaments dels autres : una seguida
que legís lo salvament del primièr jòc, per exemple, o los discs d'una seria que volètz sus una sola carta. Per
aquò, fasètz un jòc de cartas partejadas : una carta que mantun jòc utiliza. Aqueles jòcs de cartas son gardats
dins `Games/!MemCards/`, e los gerissètz amb *Cartas memòria* dins lo menú sistèma. Square ne crèa un novèl
(picatz son nom amb lo clavièr a l'ecran), Cross renomena lo que es causit e Triangle lo suprimís, après vos o
aver demandat. Per metre un jòc sus un jòc de cartas, utilizatz *Cambiar la carta memòria* dins son editor de jòc
(seccion 3.7), o son icòna *CARTA MEMÒRIA*.

**L'editor de cartas memòria** se dobrís amb l'icòna *CARTA MEMÒRIA* d'un jòc. Mòstra la carta del jòc e una
segonda carta costat a costat, amb l'icòna e lo títol de cada salvament, coma l'ecran de las cartas memòria de la
consòla d'origina. Square copia lo salvament causit sus l'autra carta, Triangle lo suprimís, e Select desfragmenta
una carta en recampant sos blòts liures, per que i càpia tornarmai un salvament bèl. Start vos daissa causir lo jòc
de cartas mostrat a drecha, e Cross torna cargar las doas cartas a partir de la clau. Una carta que lo jòc i a pas
encara escrich (un jòc que i avètz pas encara salvat) es voida e ditz *pas encara de carta* al costat de son nom.
S'avètz fach de cambiaments, AutoBleem vos demanda *Volètz enregistrar las donadas de las cartas memòria ?* abans
de quitar l'editor, de tornar cargar las cartas o de mostrar un autre jòc de cartas.

![L'editor de cartas memòria](../images/en/memory-card-editor.jpg)

**Los punts de represa.** Fòrça jòcs PS1 vos daissan salvar sonque a d'endreches precises, e i arribatz pas
totjorn abans de vos dever arrestar. Los punts de represa son aquí per aquò : quand quitatz un jòc PS1 amb lo
boton Reset de la consòla (o pel menú de l'emulador sus una Pi o un PC), AutoBleem garda un estat salvat
exactament ont èretz. Pendent que l'escriu, en sortent del jòc, l'emulador aficha *Esperatz...*. Lo còp que ven,
reprenètz a aquel moment.

Los trobatz jos l'icòna *REPRENDRE* del jòc. Un jòc amb un punt de represa ne mòstra un pichon imatge sus l'icòna ;
un jòc sens cap a l'icòna grisada. Lo causidor de punts de represa a quatre emplaçaments, mostrats coma de cartas
encadradas, cadun amb un imatge del moment, son numèro e sa data. Lo mai recent es marcat **MAI RECENT**, e un
emplaçament pas encara utilizat ditz *Cap de punt de represa*. Cross reprend lo jòc a partir de l'emplaçament
causit, e Triangle lo suprimís. Que lo causidor aparesca o pas quand aviatz lo jòc, aquò depend del paramètre
*Represa :* del jòc (seccion 3.7).

Los jòcs PS1 que jogatz dins RetroArch an tanben d'emplaçaments de represa. Cada emplaçament pòrta un badge, lo
lògo d'AutoBleem 2 o lo de RetroArch, per que vejatz quin emulador l'escriguèt.

![Lo causidor de punts de represa](../images/en/resume-picker.jpg)

### 3.9 Aviar los jòcs, RetroArch e las aplicacions

Aviar un jòc es çò que faretz mai sovent : es doncas un sol boton. Causissètz lo jòc sus l'estatgièra e quichatz
**Cross**. Un jòc PS1 se dobrís en ecran complet dins l'emulador PS1 qu'avètz causit dins las opcions (seccion
3.6) e vira fins que lo quitetz. S'amatz mai jogar un jòc PS1 dins RetroArch (perque i vira melhor, o que vos
agradan las opcions de RetroArch), quichatz **Square** puslèu.

**Quitar un jòc.** Sus la PlayStation Classic, los botons de la consòla fan çò qu'esperatz. **Reset**, sus la cara
de davant, vos torna menar al lançador e garda un punt de represa ont èretz, per que posquètz contunhar puèi
(seccion 3.8) ; fonciona quitament quand lo menú en jòc es dobèrt. **Power** atuda la consòla. Una Raspberry Pi o
un PC an pas d'aqueles botons : aquí quitatz pel menú en jòc de l'emulador, descrich mai bas.

I a tanben una sortida que fonciona parièr sus totas las manetas, la de la consòla, una maneta USB o una maneta
Bluetooth : **tenètz Start + Select, o Home, quichats 2 segondas**, e sètz tornats dins AutoBleem. Una quichada
corta sus los meteisses botons dobrís puslèu lo menú de l'emulador. Lo lançador vos rapèla los dos dins sas ajudas
(*Hold Select+Start or Home for 2 seconds: back to AutoBleem* e *Quicha cuerta de Select+Start o Home : lo menú de
l'emulador*). Una aplicacion a pas de menú d'emulador : aquí, sonque la quichada longa fa quicòm. Sus la consòla,
Reset arrèsta tanben totjorn una aplicacion.

**Lo menú en jòc.** Amb `pcsx-abnxt`, l'emulador a son pròpri menú per las causas que volètz pendent que jogatz :
salvar, cambiar de disc, reglar l'imatge, causir las manetas. Quichatz lo boton de menú (Home sus una maneta que
n'a un, **Select + Start** sus una maneta sens, o **Esc** sus un clavièr) e lo jòc se met en pausa darrièr lo
menú, amb son darrièr imatge en fons. Tenir lo boton de menú quichat 2 segondas fa coma Reset : quita lo jòc. Lo
menú a tres onglets, e L1 e R1 passan d'un a l'autre. Se rapèla ont èretz : lo còp que ven, se dobrís sul meteis
onglet e la meteissa linha.

- L'onglet **Jòc** tòca lo jòc el meteis. *Reprendre lo jòc* barra lo menú e vos daissa contunhar. Jos
  *Salvaments*, *Salvament rapid* garda lo moment ont sètz e *Cargament rapid* vos i torna menar. *Cargar
  l'autosalvament* torna metre lo jòc coma èra fa 30 segondas al maximum : l'emulador garda aquela còpia en memòria
  pendent que jogatz, e vos tira d'una error qu'auriatz pas pogut desfar. Jos *Disc CD*, *Cambiar de disc* es per
  un jòc sus mantun disc quand demanda lo seguent, e *Reïnicializar lo jòc* lo fa tornar començar. *Enregistrar los
  paramètres per aqueste jòc* garda los paramètres qu'avètz causits per aquel jòc sol (seccion 3.7). *Menú PCSX*
  dobrís las paginas pròprias de PCSX-ReARMed, amb sas opcions, sos còdis de trica e son A prepaus, e *Sortir* vos
  torna menar a AutoBleem.
- L'onglet **Imatge** vos daissa cambiar l'aspècte del jòc en l'agachant : *Afichatge*, *Definicion* (1x o 2x),
  *Levar las juntas*, *Dithering*, *Escalada*, *Halo d'ecran*, *Doçor*, *Filtre*, *Masca CRT*, *Scanlines* e
  *Luminositat de las scanlines*. Son los meteisses paramètres que dins l'editor de jòc (seccion 3.7), e cada
  linha a a drecha una linha d'ajuda que ditz a qué servís. *Afichatge* es la definicion de l'ecran ; sus la
  consòla, la causissètz dins las opcions, e aquí es sonque mostrada. *Halo d'ecran* es per las bandas escuras
  que demòran als costats d'un imatge 4:3 sus un ecran larg : las emplena amb los bòrds meteisses de l'imatge, en
  miralh e enfosquits, çò que fa que lo jòc sembla s'espandir dins elas allòc de demorar estrechat entre doas
  barras negras. *Masca CRT* pausa sus l'imatge lo motiu dels luminofòrs d'un vièlh tub - *Grasilha* dona las
  bendas finas d'un Trinitron, *Fendas* e *Delta* los punts d'autres tubs ; es pas prepausada qu'amb lo filtre
  CRT (raster). Lo filtre CRT-Pi es tròp pesuc per la consòla en 1080p. Una linha que s'aplica pas es grisada, e
  sa linha d'ajuda vos ditz perqué.
- L'onglet **Manètas** decidís çò qu'es brancat suls dos pòrts de la PlayStation, *Maneta 1* e *Maneta 2* : una
  maneta estandard (numerica), una maneta analogica (DualShock), un pistolet, o res. D'unes jòcs foncionan sonque
  amb una mena de maneta. Lo cambiament pren efièch quand tornatz al jòc.

Lo menú es dessenhat amb l'aparéncia ab2.0.0 del lançador : sembla pas un autre programa. Mòstra tanben las
batariás de vòstras manetas e l'imatge de vòstre darrièr salvament rapid.

**Los jòcs RetroArch.** Un jòc d'una autra consòla s'avia dins RetroArch, amb lo core que lo lançador a causit
per aquela consòla. Quand avètz acabat, *Close Content* o *Quit RetroArch* dins lo menú de RetroArch vos torna
menar al lançador. Se volètz cambiar lo core que fa virar una consòla, dobrissètz *Cores RetroArch* dins lo Menú
rapid (seccion 3.4) ; la lista se dobrís amb lo core *PlayStation 1* en cima. E se volètz lo menú pròpri de
RetroArch (l'XMB) per sos paramètres e sas pròprias listas de contenguts, causissètz *RetroArch* dins lo menú
sistèma : RetroArch se dobrís alara sens res cargat.

![La fenèstra dels cores RetroArch, amb lo core PlayStation 1 en cima](../images/en/retroarch-cores.jpg)

**Las aplicacions.** Las aplicacions son de programas puslèu que de jòcs : los espleches de la consòla e, sus la
consòla, las aplicacions en mai que venon amb lo paquet de RetroArch (Doom, Quake, Amiga e d'autras). Las trobatz
dins la colleccion de las aplicacions. Abans qu'una aplicacion s'avie, AutoBleem mòstra son legissetz-me, per que
sapiatz çò qu'es e cossí se comanda. Cross l'aviá, e Circle vos torna menar a l'estatgièra.

![Lo legissetz-me d'una aplicacion, mostrat abans que s'avie](../images/en/app-start.jpg)

**Los paramètres d'una aplicacion.** Fòrça aplicacions foguèron escrichas per una maneta precisa : podètz doncas
cambiar la manièra que vesètz la vòstra. Causissètz l'aplicacion, dobrissètz la rengada d'icònas e causissètz
*Jòc* : los *Paramètres del jòc* de l'aplicacion se dobrisson (*Cambiar la manièra de lançar aquel programa*).
*Mòde manèta :* decidís quina maneta l'aplicacion crei aver. *Automatic* utiliza çò que l'aplicacion demanda ela
meteissa ; *Manèta PSC* e *Manèta Xbox 360* presentan vòstra maneta coma la de la consòla o coma una maneta
Xbox 360, e *Manèta PSC (sistèma)* e *Manèta Xbox 360 (sistèma)* fan parièr pel sistèma el meteis. Ensajatz un
autre mòde quand una aplicacion reagís pas a vòstra maneta coma caldriá. *Crotz coma stick :* fa menar lo stick
analogic per la crotz direccionala, per una aplicacion qu'escota sonque lo stick, e *Stick coma crotz :* fa lo
contrari.

D'unas aplicacions vos pausan una question lo primièr còp que las aviatz. Una vòl saber *Quines comandas a vòstra
manèta ?*, per configurar sas comandas : respondètz *Una crotz direccionala* per una maneta qu'a sonque la crotz,
o *Sticks analogics*. Una aplicacion que fa virar Windows demanda *Qué volètz far ?* e prepausa d'aviar Windows,
de l'installar, d'aviar DOS o de desinstallar Windows. Quand una aplicacion vos daissa definir una tòca, vos
demanda *Quichatz un dels botons.*

![Los paramètres de jòc d'una aplicacion](../images/en/app-game-settings.jpg)

Un programa Windows aviat per l'executador PE (una aplicacion PE, seccion 3.3) vos parla pels ecrans pròpris
d'AutoBleem : un messatge que vòl mostrar apareis coma *Messatge*, e una question amb de causidas coma *Causir una
opcion*, cadun amb lo nom de l'aplicacion coma títol.

![Una question d'una aplicacion PE, mostrada coma un ecran AutoBleem](../images/en/pe-dialog.jpg)

### 3.9a Un disc dins un lector USB

Podètz brancar un lector CD/DVD USB ordinari sus la consòla, una Raspberry Pi o un PC aviat dempuèi la clau
AutoBleem, e jogar dirèctament a partir d'un disc PlayStation original, sens res copiar. Un disc que metètz
apareis dins lo lançador coma un jòc de mai. Aquò fonciona pas sus Windows.

**Copiar un disc sus la clau.** Se volètz lo jòc totjorn a man, sens lo disc, quichatz Square (*Copiar lo
disc*). AutoBleem vos demanda d'en primièr se cal copiar lo jòc e quanta plaça prendrà, puèi l'enregistra dins lo
dossièr `Games` coma un sol fichièr CHD (un jòc sus mantun disc recep tanben un fichièr `.m3u`, per que lo
cambiament de disc foncione dins lo jòc). Pendent la còpia, vesètz la velocitat e lo temps que demòra, e
*Interrompre* l'arrèsta. Quand es acabat, lo jòc es sus l'estatgièra coma los autres. AutoBleem copiarà pas un jòc
qu'es ja dins `Games`, ni un jòc que i a pas de plaça per el : vos ditz alara quanta plaça li cal. Un disc
rascat se pòt copiar tanben : las partidas que se podián pas legir son emplenadas de zèros, e AutoBleem vos ditz
quantas n'i aviá. Una tala còpia pòt foncionar o pas.

Square prepausa la còpia per cada disc de jòc PlayStation dins la vista del disc, quitament per un disc que las
basas de cobèrturas coneisson pas. Un jòc que las basas coneisson es copiat jos son títol ; per un jòc sus mantun
disc, copiatz los discs l'un après l'autre, e lo `.m3u` los lista dins l'òrdre, lo disc 1 en primièr. Un disc que
las basas coneisson pas es nomenat per son numèro de seria, es copiat coma un disc sol, e a pas de cobèrtura sus
l'estatgièra. La fenèstra de còpia, *Còpia del disc*, demòra a l'ecran fins que la còpia es acabada o arrestada
(lo lançador espèra pendent aquel temps), e mòstra la velocitat coma un multiple d'un lector CD ordinari. Se la
còpia fracassa, AutoBleem vos ditz perqué.

![La còpia d'un disc](../images/en/disc-copy.jpg)

**Jogar a partir del disc.** Quand metètz un disc, la **vista del disc** se dobrís soleta tre que lo disc es
legit. Mòstra la cobèrtura del disc (de las basas de cobèrturas, o recuperada en linha) amb son numèro de seria e
son títol, e Cross aviá lo jòc. Un jòc PS1 jogat a partir del disc garda sos punts de represa e sos salvaments
dins un dossièr pròpri : podètz doncas arrestar e contunhar puèi coma amb un jòc sus la clau. Après lo jòc, o
après èsser passat per las opcions o pels paramètres d'una extension, tornatz a la vista del disc. Se la quitatz
amb Circle per percórrer vòstres autres jòcs, lo disc demòra dins lo lector e Circle sus l'estatgièra torna menar
la vista ; sus una estatgièra voida, R1 (*Disc*) la dobrís tanben. Sus una estatgièra amb de jòcs, R1 garda son
trabalh abitual de sautar d'una primièra letra a l'autra. Quand levatz lo disc, la vista del disc se barra.

![La vista del disc](../images/en/disc-view.jpg)

**La pastilha del lector**, en naut de l'ecran, vos ditz çò que fa lo lector, per que sapiatz se cal esperar. Sens
lector brancat, vesètz pas res. Un lector sens disc mòstra una icòna de disc palla. Pendent que un disc es legit,
l'icòna pampalheja e ditz *Lectura del disc...*, e un còp prèst l'icòna s'aluca amb lo títol del disc. Se metètz
un disc qu'es ni un jòc PlayStation ni un CD àudio, la pastilha ditz *Aquò es pas un disc PlayStation*, e se lo
lector pòt pas legir lo disc a aquel moment, ditz *Lo disc pòt pas èsser legit ara*.

![La pastilha del lector](../images/en/disc-chip.jpg)

**Los CD àudio.** Lo lector jòga tanben los CD de musica. Un CD àudio dobrís lo **lector de CD** en plaça de la
vista del disc. Mòstra lo disc coma un *CD àudio* amb sa lista de pistas e sa durada totala, e la linha dessota
nomena la pista causida e ditz se la repeticion e l'azard son activats. Un disc que lo lector pòt pas jogar es
marcat *Aqueste disc se pòt pas legir*. Vaquí sos botons :

| Boton | Dins lo lector de CD |
|---|---|
| Cross | Jòga la pista causida. |
| Start | Met la musica en pausa, e la torna aviar. |
| Square | Arrèsta la musica. |
| L1 / R1 | Passan a la pista precedenta o seguenta. |
| L2 / R2 | Fan recular o avançar dins la pista, cinc segondas a la vegada. |
| Triangle | Cambia çò que se repetís : res, tot lo disc, o la pista actuala. |
| Select | Activa o desactiva l'azard, per que las pistas jògan dins un òrdre aleatòri. |
| Circle | Quita lo lector de CD. |

![Lo lector de CD](../images/en/cd-player.jpg)

**Los discs LibCrypt.** D'unes jòcs PlayStation, europèus per la màger part, an una proteccion contra la còpia
nomenada LibCrypt. Per los far virar, l'emulador a besonh d'un pichon fichièr `.sbi` amb las donadas de la
proteccion. AutoBleem va quèrre aquel fichièr sul site solet, abans qu'un tal disc jògue e quand lo copiatz, e es
copiat amb lo jòc. Per aquò, li cal una ret : sus una Raspberry Pi o un PC, la qu'a ja ; sus la consòla, la WiFi
qu'avètz configurada dins PSC-Bios.

Per un disc dins lo lector, d'unes paramètres d'un jòc an pas de sens : son editor de jòc grisa doncas aquelas
linhas (seccion 3.7).

### 3.10 Apondre de jòcs

AutoBleem tròba vòstres jòcs solet, a condicion que sián a la bona plaça. Aquesta seccion vos ditz ont va cada
mena de jòc, per que cada escandalhatge los mete sus l'estatgièra amb lors noms e lors cobèrturas.

**Los jòcs PS1** van dins lo dossièr `Games`, **un dossièr per jòc**, nomenat coma lo jòc. Podètz tanben recampar
de jòcs dins de dossièrs vòstres, e cada dossièr d'aquela mena ven un grop dins lo causidor de colleccions (seccion
3.3) :

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                un dossièr de jòcs : un grop a despart dins lo causidor de colleccions
    Klonoa/                   Klonoa.pbp
```

AutoBleem legís los formats d'imatge de disc abituals : `.cue` amb son `.bin` (o `.img`), `.pbp`, `.chd` (los
compressats en zstd tanben), `.iso`, e `.ecm`, que l'escandalhatge desencòda per vos. Un jòc en zip fonciona
tanben : lo processor **Unzip** lo descompressa abans que l'escandalhatge lo legisca (seccion 3.14).

Avètz pas besonh d'èsser ordenat. Un jòc sus mantun disc deu èsser dins un sol dossièr amb totes sos discs, mas se
i copiatz de dossièrs nomenats `Game (Disc 1)`, `Game (Disc 2)` e atal de seguida, l'escandalhatge los recampa dins
un sol dossièr `Game`. Los jòcs pausats en fichièrs desparièrs dirèctament dins `Games/` son tanben rengats per
l'escandalhatge dins de dossièrs pròpris.

**Los noms e las cobèrturas** venon solets. L'escandalhatge legís lo numèro de seria de cada disc e pren lo títol,
l'editor, l'annada, lo nombre de jogaires e la region dins la basa de donadas PlayStation de RetroArch o dins las
basas de cobèrturas. Se volètz vòstra pròpria cobèrtura, metètz un PNG o un JPEG al costat de l'imatge del jòc,
amb lo meteis nom. Sens aquò, la cobèrtura ven de las basas de cobèrturas o, amb RetroArch installat, de la
colleccion de vinhetas de libretro ; sus una Raspberry Pi, un PC o Windows, una cobèrtura mancanta es recuperada
en linha (Opcions → *Recuperar las cobèrturas en linha :*). Se l'escandalhatge se trompa, corregissètz dins
l'editor de jòc e activatz *Verrolhar las donadas :*, per que l'escandalhatge seguent garde vòstre cambiament.

**Los jòcs de las autras consòlas** van jos `RetroArch/roms/`, **un dossièr per consòla, nomenat coma lo nomenan
las basas de donadas de RetroArch** : per exemple `Nintendo - Nintendo Entertainment System`, `Nintendo - Super
Nintendo Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` o `FBNeo - Arcade
Games` (o `Arcade`). Los dossièrs son creats per vos, e las ROM pòdon demorar en zip. Sus una Raspberry Pi, un PC
o Windows, l'escandalhatge las legís solet e escriu las listas de lectura de RetroArch. Una clau de consòla o pòt
pas far soleta : aquí, aviatz **UpdateRoms** sul PC (capítol 5).

**Las aplicacions** van jos `Apps/<name>/`, cadun amb un `app.ini` (son nom, son icòna e çò que cal aviar) e un
`run.sh`.

**Los paquets.** D'unas aplicacions son de motors de jòc : an besonh de las donadas d'un jòc qu'avètz per lo poder
far virar. Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, los jòcs
DOS e d'autres foncionan atal. Metètz los fichièrs del jòc dins un dossièr `Packages` sus la clau, un dossièr per
jòc (per exemple `Packages/Doom/DOOM2.WAD`), e AutoBleem los reconeis gràcias a una taula que ven amb el
(`rc/packages.ini`). Dins un dossièr que reconeis, los fichièrs de jòc desparièrs son cadun un paquet. AutoBleem
legís sonque vòstres fichièrs e los cambia pas jamai. Un paquet pòt tanben venir de la Botiga (seccion 3.13).

Ont lo lançador l'aficha, la linha *Paquets* de l'onglet de las aplicacions (seccion 3.3) lista las donadas de
jòc trobadas. Cross sus una entrada dobrís sas **entresenhas de paquet** : çò que contenon las donadas, una
descripcion, ont son los fichièrs e d'ont venon (vòstres pròpris fichièrs, la Botiga, un mod, o de fichièrs que
venon dins una aplicacion), se son en shareware o liures, e quina aplicacion installada las fa virar. Se res de
çò qu'avètz installat las pòt far virar, las entresenhas vos o dison.

Quand aviatz una aplicacion de motor, AutoBleem cèrca de donadas de jòc que pòt far virar. Amb un sol jòc de
donadas, lo jòc s'avia sul pic. Amb mantun, una lista (*Causir las donadas de jòc*) vos demanda a quin jogar, e se
plaça sus lo qu'avètz causit lo darrièr còp. Se n'i a pas cap, AutoBleem vos ditz quinas donadas l'aplicacion
demanda e ont las metre, e res s'avia pas.

**Vòstres pròpris jòcs.** Quand AutoBleem reconeis pas qualques donadas, sas entresenhas de paquet dison *Pas
reconegut. S'es un jòc, vejatz lo manual : Vòstres pròpris jòcs.* La taula coneis sonque los jòcs per que foguèt
facha. Per un autre, escrivètz-li una linha dins un `packages.ini` vòstre, dins lo dossièr `Packages` : AutoBleem
legís lo vòstre d'en primièr, doncas vòstras linhas ganhan.

![Lo causidor de paquets, ont causissètz las donadas de jòc d'aviar](../images/en/packages-picker.jpg)

![Las entresenhas de paquet](../images/en/package-info.jpg)

**Escandalhar sonque una partida.** S'avètz apondut de jòcs sonque dins una colleccion o un dossièr, *Tornar
escandalhar los jòcs* pòt escandalhar sonque aquela partida, qu'es mai rapid que de tot escandalhar, e sa bula
s'escafa quand a acabat.

**Los tèmas** van jos `Themes/<name>/`, amb lor `theme.json` e lors imatges ; o pausatz lo zip del tèma dins
`Themes/` tal coma es.

### 3.11 Lo BIOS PS1

Lo BIOS es lo programa d'aviada pròpri de la PlayStation, e l'emulador fa virar los jòcs amb mai de fidelitat amb
lo vertadièr. Sus una **PlayStation Classic**, avètz pas res a far : l'emulador utiliza lo BIOS de la consòla. Sus
una **Raspberry Pi, un PC e Windows**, metètz vòstres pròpris fichièrs BIOS PS1 dins `System/Bios/` : `romw.bin`
(la SCPH-5501/5502 american e europèa) e `romJP.bin` (la SCPH-5500 japonesa, per los jòcs japoneses). Los
installadors los provesisson a partir dels paquets BIOS de RetroArch, levat se vòstres pròpris fichièrs i son ja :
remplaçan pas jamai los vòstres. Sens eles, l'emulador vira amb son BIOS HLE integrat, un remplaçant que fòrça
jòcs acceptan e d'unes non : se un jòc vòl pas s'aviar, un BIOS mancant es la primièra causa de verificar.

### 3.12 Las mesas a jorn

AutoBleem se ten a jorn solet : avètz las foncions novèlas e las correccions sens res tornar installar. Quand lo
lançador s'avia, e puèi un còp per jorn, verifica sul site s'i a una version novèla sus son **canal**. Causissètz
lo canal dins Opcions → *Mesas a jorn:* : `release`, `testing`, `nightly`, o `off` se volètz pas que i agache
briga. Se volètz pas esperar la verificacion quotidiana, *Mesa a jorn logiciala* dins lo menú sistèma verifica
ara.

Quand i a una version novèla, AutoBleem vos demanda çò que cal far. *Metre a jorn ara* la telecarga e l'installa,
çò que pren qualques minutas. *Me lo rapelar deman* vos o tòrna demandar l'endeman, e *Ignorar aquesta version*
vos parla pas pus d'aquesta version. Que que causiscatz, vòstres jòcs, salvaments e paramètres demòran totjorn ;
après una mesa a jorn, lo lançador escandalha vòstres jòcs tornarmai. L'etiqueta de canal en naut a esquèrra
(seccion 3.1) mòstra quina version avètz.

La mesa a jorn s'installa segon la maquina :

- Sus una **Raspberry Pi** e la **clau PC**, l'installador torna virar après lo telecargament, amb lo meteis ecran
  de progression qu'a la primièra aviada, e prepausa tanben un RetroArch mai recent. Puèi lo lançador torna.
- Sus **Windows**, l'installador telecargat se dobrís, installa la version novèla e aviá lo lançador novèl.
- Sus una **PlayStation Classic**, sonque una consòla amb lo **nucli AutoBleem** (ABFlashKit, seccion 6.2) e una
  **ret WiFi** configurada dins PSC-Bios (seccion 6.1) se pòt metre a jorn soleta : una consòla d'origina a pas
  de ret, e lo lançador agacha pas. Après *Metre a jorn ara*, lo lançador se tampa e l'imatge d'AutoBleem demòra
  a l'ecran pendent que la clau es mesa a jorn, çò que pren qualques minutas ; puèi lo lançador novèl s'avia.
  Sens ret, *Mesa a jorn logiciala* vos ditz *Pas connectat*. Tota clau de consòla se pòt tanben metre a jorn
  dempuèi un PC amb `AutoBleemInstaller.exe` (seccion 2.1).

### 3.13 Las extensions e la Botiga AutoBleem

**Las extensions** apondon de causas novèlas al lançador (lors pròpris ecrans e lors foncions) sens modificar
AutoBleem el meteis. La Botiga AutoBleem e PSC-Bios son d'extensions. Una extension viu dins
`Extensions/<name>/` sus la clau (sus una Raspberry Pi, sus sa particion de donadas ; sus Windows, dins lo dossièr
de donadas) ; per n'installar una, descompressatz son zip aquí.

Per las veire, dobrissètz lo menú sistèma (**L2 + R2**) e causissètz *Extensions*. Las que venon de l'equipa
AutoBleem son en cima, e las autras seguisson jos *Extensions tèrças*. Cross aviá la qu'es causida, e Triangle la
desactiva o la torna activar. PSC-Bios sus la consòla es l'excepcion : es amb ela que configuratz la WiFi, las
manetas e l'ora, e doncas se pòt pas desactivar aquí. Quand una extension pòt pas virar, sa linha vos ditz
perqué : a besonh d'una ret e n'i a pas, es pas facha per aqueste sistèma, foguèt facha per una autra version
d'AutoBleem e a besonh d'una mesa a jorn, o se podiá pas cargar. Se jamai una extension arrèsta lo lançador,
AutoBleem la desactiva e la lista vos o ditz ; la podètz tornar activar aquí.

![La lista de las extensions](../images/en/extensions.jpg)

**La Botiga AutoBleem** es la primièra extension : un endrech per percórrer d'aplicacions e de jòcs e los
installar d'una sola quichada, sus totes los sistèmas ont vira AutoBleem. Una PlayStation Classic a besonh del
nucli AutoBleem per aquò, que la WiFi ven amb lo nucli. Dobrissètz-la dempuèi lo Menú rapid (*Botiga*, seccion
3.4). A quatre onglets, e L1 e R1 passan d'un a l'autre.

Los onglets **Apps** (aplicacions) e **Games** (jòcs) listan çò que las fonts prepausan, cada element amb son
imatge, sa version, sa talha e la pichona icòna de la font d'ont ven. L'onglet de las aplicacions lista tanben las
aplicacions PE, amb lor licéncia e lor font, e los paquets de donadas de jòc (seccion 3.10). Çò qu'avètz ja
installat pòrta un badge *Installed*. La barra d'ajuda mòstra los botons que s'aplican a la linha causida :

| Boton | Dins los onglets d'aplicacions e de jòcs |
|---|---|
| Cross | Installa l'element ; o lo met a jorn, tòrna ensajar après un fracàs, o anulla un telecargament qu'espèra o qu'es en cors. |
| Triangle | Suprimís quicòm que la Botiga installèt. |
| Square | Refresca las listas a partir de las fonts. |
| L2 / R2 | Sautan a la primièra letra precedenta o seguenta. |
| Select | Mòstra una font a la vegada, quand volètz veire çò que prepausa una sola font. |
| Start | Cèrca dins los títols. |

Los imatges son gardats un còp cargats : las listas apareisson doncas lèu lo còp que ven, e un imatge que s'es pas
cargat se pòt tornar ensajar.

L'onglet **Downloads** (telecargaments) mòstra çò que se telecarga, çò qu'espèra, çò qu'a fracassat o qu'es
installat, amb una barra de progression qu'avança regularament. Avètz pas besonh de l'agachar : los telecargaments
contunhan en rèire plan, quitament après que quitatz la Botiga, e mentre que sètz endacòm mai dins lo lançador,
una bula mòstra lo telecargament en cors amb sa velocitat e lo temps que demòra (per exemple `1.4 MB/s · 0:42`).
Aviar un jòc o atudar los met sonque en pausa, e un telecargament arrestat repren ont s'èra arrestat. Se la ret
tomba, l'element ditz *Waiting for the network* e repren ont èra quand la ret torna ; après 30 minutas sens ret,
abandona. Los telecargaments de mai de 2 GB foncionan sus totas las plataformas, las versions 32 bits compresas.
Un jòc qu'installatz apareis sus l'estatgièra après l'escandalhatge seguent, amb l'imatge de la Botiga coma
cobèrtura.

L'onglet **Sources** (fonts) mòstra d'ont venon las listas, cadun amb son icòna : lo catalòg pròpri d'AutoBleem,
tota lista TSV pausada dins `System/Extensions/store/sources/`, e las adreças qu'apondètz vos meteisses amb *Add a
source URL*. Cross sus una font qu'avètz aponduda vos daissa la renomenar, cambiar son adreça, la far passar de
`http://` a `https://` o al contrari, o la suprimir.

![L'onglet de las aplicacions de la Botiga](../images/en/store-apps.jpg)

![Lo menú d'una font qu'avètz aponduda](../images/en/store-source-menu.jpg)

Çò que prepausa lo catalòg pròpri d'AutoBleem es tanben listat sul site de telecargament, a
`https://autobleem.retromenele.pl/store/`. Una font qu'apondètz vos meteisses es un autre afar : **sètz
responsable de çò que contenon las fonts qu'apondètz.**

**Vòstres pròpris jòcs sus vòstra ret.** Se gardatz vòstres jòcs PS1 sus un autre ordenador a l'ostal, `abstored`,
lo servidor de ret locala de la Botiga, los pòt prepausar a la Botiga per vòstra ret : los installatz alara coma
tot autre element. Vira sus tota maquina Linux (una Raspberry Pi, un servidor d'ostal) e legís sonque lo dossièr,
sens jamai lo cambiar. Aviatz-lo amb `abstored <games folder>`, puèi dobrissètz `http://<that machine>:8124/` dins
un navigador : la pagina mòstra çò que servís e los problèmas que trobèt. Dins la Botiga, apondètz
`http://<that machine>:8124/store.tsv` coma font. De programas prèstes per Linux e Windows son sus la pagina de la
Botiga, dins son onglet **LAN server**, e `INSTALL-linux.md` (`ext_store/server/` dins lo còdi font) explica cossí
lo configurar coma servici. **LAN Share** (seccion 5.2) mete de jòcs e de discs d'un PC sus un tal servidor.

### 3.14 Los processors d'escandalhatge

Los processors d'escandalhatge prèparan vòstres jòcs abans qu'AutoBleem los legisca. Un processor es un pichon
programa que cada escandalhatge fa virar d'en primièr. Pòt transformar un format qu'AutoBleem legís pas en un
format que legís (descompressar un jòc en zip, per exemple) o cambiar las donadas d'un jòc, coma aplicar un pedaç
de traduccion. Los processors son dins `System/Processors/<name>/` sus la clau (sus una Raspberry Pi, sus sa
particion de donadas ; sus Windows, dins lo dossièr de donadas) ; per n'installar un, descompressatz son dossièr
aquí, e l'escandalhatge seguent lo fa virar.

**Unzip ven amb AutoBleem.** Descompressa los jòcs PS1 en zip de `Games/` abans que l'escandalhatge los legisca, e
las ROM en zip una a una ; los jòcs d'arcada demòran en zip, que es atal que los cores d'arcada los legisson.
Metre a jorn AutoBleem met tanben a jorn Unzip, e se l'avètz desactivat, demòra desactivat.

Un processor fa son trabalh un còp : quand a tractat un jòc, lo torna pas tractar tant que lo jòc cambia pas.
Pendent qu'un processor trabalha, la bula en naut a drecha mòstra çò que fa, e un avertiment o un fracàs apareis
sus la linha dessota ; `processors.log` dins lo dossièr dels jornals ne dona lo detalh. Aviar un jòc o RetroArch
arrèsta un processor que modifica de fichièrs, per que lo jòc aja la maquina per el sol, e l'escandalhatge seguent
acaba lo trabalh.

Per los gerir, dobrissètz lo menú sistèma (**L2 + R2**) e causissètz *Processors d'escandalhatge*. Los vesètz dins
l'òrdre que viran, amb un onglet pels jòcs PS1 e un per las ROM ; L1 e R1 passan d'un onglet a l'autre. L'òrdre
compta : un processor que descompressa deu venir abans un processor que pedaça çò que foguèt descompressat.

| Boton | Dins los processors d'escandalhatge |
|---|---|
| Square | Pren lo processor causit, per que Amont e Avall lo desplacen a sa plaça novèla ; Square lo torna pausar. |
| Cross | Desactiva lo processor, o lo torna activar. |
| Triangle | Fa tornar examinar al processor totes los jòcs a l'escandalhatge seguent, quitament los qu'a ja tractats. |
| Circle | Tòrna en rèire, e aviá un escandalhatge s'avètz cambiat quicòm. |

Un processor bastit per una autra maquina demòra dins la lista, grisat : vesètz qu'es aquí, mas que vira pas
aquí.

![Los processors d'escandalhatge](../images/en/processors.jpg)

Se volètz escriure un processor vòstre, la pagina d'Unzip, `https://github.com/autobleem2/proc_unzip`, explica
tot çò que deu far un processor, e `tools/proc_check.py` dins lo còdi font d'AutoBleem verifica lo vòstre abans que
lo partejetz.

<!-- pagebreak -->

## 4. Los ecrans

### 4.1 Gestionari de jòcs

Lo Gestionari de jòcs es l'endrech ont botatz d'òrdre dins vòstra logitèca PS1. Servissètz-vos-en quand volètz
levar un jòc que i jogatz pas pus, dobrir los paramètres d'un jòc sens lo cercar d'en primièr sus l'estatgièra, o
far tornar quèrre totas las cobèrturas a AutoBleem. Lo dobrissètz dempuèi lo menú sistèma (L2 + R2, *Gestionari
de jòcs*). Pendent un escandalhatge es grisat, e espèra que l'escandalhatge aja acabat.

L'ecran a per títol *Gestionari de jòcs - causir un jòc*. A esquèrra, vesètz totes vòstres jòcs PS1 en lista de
títols per òrdre alfabetic ; a drecha, la cobèrtura del jòc causit amb son editor, son annada, son numèro de seria
e lo dossièr ont es. La plaça liura que demòra sul lector es mostrada en naut a drecha : vesètz atal quanta plaça
vos torna una supression. Amont e Avall percorron la lista, L2 / R2 viran una pagina e L1 / R1 sautan al primièr
o al darrièr jòc.

- **Cross** dobrís lo jòc causit dins l'editor de jòc, lo meteis editor que l'icòna Jòc de l'estatgièra (seccion
  3.7). Quand lo quitatz, tornatz sul meteis jòc dins la lista.
- **Square suprimís lo jòc.** AutoBleem vos o demanda d'en primièr, puèi suprimís tot lo dossièr del jòc. Se los
  estats salvats e la carta memòria del jòc son pas utilizats per cap d'autre jòc, pausa una segonda question :
  se los cal suprimir tanben. Respondètz non se poiriatz voler tornar trobar lo jòc puèi amb vòstres salvaments.
- **Triangle suprimís totes los imatges de cobèrtura** (PNG o JPEG) que son al costat de vòstres jòcs, après una
  question. Es util quand avètz amassat de cobèrturas que vos agradan pas : l'escandalhatge seguent torna prendre
  las cobèrturas dins las basas de cobèrturas.

A la fin de la lista, après los jòcs, podètz veire de dossièrs marcats *Pas apondut*. Son de dossièrs de `Games`
que l'escandalhatge a examinats mas qu'a pas poscut transformar en jòc. Causissètz-ne un e la partida drecha vos
ditz ont es e perqué es pas estat apondut : un fichièr cue mancant, per exemple (capítol 7). Square suprimís un
tal dossièr après una question. Quand quitatz amb Circle après aver cambiat quicòm, AutoBleem torna escandalhar
los jòcs.

![Lo Gestionari de jòcs : la lista dels jòcs a esquèrra, la cobèrtura e las entresenhas del jòc causit a drecha](../images/en/game-manager.jpg)

### 4.2 Entresenhas de material

Las Entresenhas de material son la pagina d'agachar quand volètz saber çò qu'es vòstra maquina e çò que vei :
quanta plaça demòra sus la clau, quina adreça de ret a, quins pilòts d'afichatge e d'àudio utiliza, e quinas
manetas son brancadas. Es la meteissa pagina sus totas las plataformas, la consòla compresa. La dobrissètz dempuèi
lo menú sistèma (L2 + R2, *Entresenhas de material*) ; Circle vos torna menar al menú sistèma.

La pagina mòstra lo sistèma, lo material, l'emmagazinatge amb sa plaça liura, las adreças de ret, los pilòts
d'afichatge e d'àudio e las manetas brancadas. Torna legir tot cada segonda : la podètz daissar dobèrta mentre que
brancatz una maneta o un cable, e veire lo cambiament aparéisser. Fa pas que mostrar : per configurar la ret o una
maneta, utilizatz *Ret e manetas* (PSC-Bios, capítol 6).

La partida de las manetas respond a la question « quina maneta es quin jogaire ? ». Las doas primièras manetas son
mostradas coma *Jogaire 1* e *Jogaire 2*, los pòrts que l'emulador PS1 lor balha. Tota maneta de mai es mostrada
coma *pas utilizat per l'emulador PS1*. RetroArch distribuís los pòrts segon sos pròpris paramètres : dins un jòc
RetroArch, l'òrdre pòt doncas èsser diferent. Avètz pas besonh de dobrir aquesta pagina cada còp : quand una
maneta es brancada o desbrancada, lo lançador mòstra un moment quina maneta es ara lo jogaire 1 e quina lo
jogaire 2.

![Entresenhas de material : las entresenhas de la maquina e las manetas brancadas](../images/en/hardware-info.jpg)

### 4.3 La guida dels botons

S'oblidatz çò que fa un boton endacòm, quichatz **Triangle** sus l'estatgièra. La guida dels botons mòstra totes
los botons de totes los ecrans sus una sola pagina : los podètz verificar sens quitar lo lançador. S'un clavièr USB
es brancat, o es estat utilizat, una colomna *Clavièr* mòstra la tòca correspondenta al costat de cada boton de la
maneta.

La guida vos rapèla tanben la sola causa que val la pena de reténer per cada jòc : cossí ne sortir. Tenètz Select
+ Start, o Home, quichats 2 segondas per tornar a AutoBleem ; una quichada corta dobrís puslèu lo menú de
l'emulador.

![La guida dels botons : los botons de cada ecran, amb las tòcas del clavièr al costat](../images/en/button-guide.jpg)

### 4.4 Lo clavièr a l'ecran

Cada còp qu'AutoBleem vos demanda de picar quicòm (lo nom d'un jòc de cartas memòria, lo títol d'un jòc, un
senhal WiFi, l'adreça d'una font de la Botiga), lo meteis clavièr a l'ecran apareis, per que poscatz picar sonque
amb la maneta. Es dispausat coma lo clavièr d'un telefonet. En mai de las letras, a una pagina de simbòls, amb
`/ \ : ? & = % @ #` e lo demai de çò que cal per una adreça o un senhal, e doas paginas de letras accentuadas. La
linha d'en bas ten Shift, la tòca que cambia de pagina, Espaci, Retorn arrièr e Confirmar.

Desplaçatz-vos sus las tòcas amb las direccions e quichatz **Cross** per picar la qu'es jos lo cursor.
**Triangle** escafa una letra e **Square** pica un espaci. **L1** es Shift ; quichatz-lo doas vegadas pel
verrolhatge de las majusculas. **R1** passa a la pagina de tòcas seguenta, e **L2 / R2** desplaçan lo cursor dins
lo tèxte. **Start** confirma çò qu'avètz picat e **Circle** anulla. S'un clavièr USB es brancat, podètz picar
dessús quand volètz : Entrada confirma e Esc anulla.

![Lo clavièr a l'ecran](../images/en/keyboard.jpg)

### 4.5 Virtual gamepad

Las aplicacions, los programas de la colleccion de las aplicacions coma Doom o Quake, legisson pas vòstra maneta
elas meteissas. Un pichon programa ajudaire, lo servici de maneta virtuala, legís las manetas vertadièras e balha
a cada aplicacion una maneta que compren. Aquesta pagina vos mòstra quinas manetas vei aquel ajudaire e cossí las
legís. Agachatz aquí quand una aplicacion reagís pas a vòstra maneta, o quand sos botons son mesclats. La
dobrissètz dempuèi lo menú sistèma (L2 + R2, *Virtual gamepad*) ; Circle vos torna menar al menú sistèma.

Jos *Pads the daemon sees*, cada maneta es listada amb un numèro e son nom. Al costat, legissètz tres causas : se
l'ajudaire a poscut dobrir la maneta (*connected*) o non (*not readable*) ; lo pilòt que la maneta ne ven ; e d'ont
ven la disposicion de sos botons : *from the controller database* vòl dire que la maneta es coneguda e que sos
botons son ont devon èsser, *guessed by the daemon* vòl dire qu'es pas coneguda e que l'ajudaire a fach de son
melhor per devinar. Se los botons dins una aplicacion semblan pas justes, una disposicion devinada n'es
probablament la rason.

L'ajudaire vira sonque pendent qu'una aplicacion vira : la pagina li pausa doncas la question un còp, quand se
dobrís. Se brancatz una maneta mentre que la pagina es dobèrta, quichatz **Cross** (*Look again*) per tornar
demandar. Sus Windows i a pas d'ajudaire d'aquela mena, e la pagina ditz *Not in this build*.

![Virtual gamepad : las manetas que vei l'ajudaire de las aplicacions](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. Sul PC

### 5.1 UpdateRoms : refrescar una clau de consòla

Sus una Raspberry Pi, un PC o Windows, l'escandalhatge del lançador renga vòstres jòcs RetroArch en listas e va
quèrre lors cobèrturas solet. La PlayStation Classic o pòt pas far, que a pas de ret pròpria. **UpdateRoms** fa
aquel trabalh a sa plaça sus vòstre PC Windows : utiliza la ret del PC mas escriu tot amb los camins que la
consòla espèra, e quand tornatz metre la clau, la consòla s'avia e tròba tot a sa plaça. Aviatz-lo cada còp
qu'avètz apondut o levat de jòcs RetroArch sus una clau de consòla.

1. Copiatz vòstras ROM sus la clau jos `RetroArch/roms/<system>/` (seccion 3.10). Los noms dels dossièrs devon
   èsser los noms de las basas de donadas de RetroArch ; l'installador a ja creat los mai corrents.
2. Aviatz **`UpdateRoms\UpdateRoms.exe` dempuèi la clau** (l'installador l'i a mes). Tròba solet sus quina clau es.
   Pendent que trabalha, vesètz una linha que ditz çò que fa, una barra de progression e un jornal.
   - Se la clau a pas encara de basa de donadas RetroArch, telecarga d'en primièr lo paquet de basas de donadas de
     RetroArch. Puèi identifica cada ROM amb el : un jòc que la basa coneis recep son nom vertadièr.
   - Escriu una lista de lectura per consòla dins `RetroArch/bin/playlists/`, amb los camins de la consòla. Tot
     çò que RetroArch el meteis apondèt a aquelas listas es gardat.
   - Per cada ROM sens cobèrtura, va quèrre una cobèrtura suls servidors de vinhetas de libretro e la mete dins
     `RetroArch/bin/thumbnails/`.
3. Levatz la clau amb seguretat e tornatz-la metre dins la consòla. L'onglet RetroArch del causidor de colleccions
   lista ara cada consòla qu'a de jòcs.

Lo podètz aviar tan sovent que volètz : un dossièr ont res a pas cambiat es sautat, doncas un segond passatge es
rapid. Se quicòm va pas, lo jornal es `System/Logs/updateroms.log` sus la clau. Una carta de Raspberry Pi dins un
lector de cartas se pòt refrescar parièr, amb `UpdateRoms.exe <drive> --target rpi`, mas una Pi o fa soleta quand
a una ret.

### 5.2 LAN Share : vòstres jòcs e vòstres discs sul servidor de vòstra ret

La Botiga pòt installar de jòcs a partir d'un servidor sus vòstra pròpria ret d'ostal (seccion 3.13). **LAN
Share** es lo programa Windows qu'emplena aquel servidor dempuèi vòstre PC : i mete los jòcs PS1 qu'avètz sul PC,
e pòt legir un disc PS1 dins lo lector CD/DVD del PC e l'i metre tanben. Lo servidor es un `abstored` que vira sus
una Raspberry Pi, un NAS o un autre PC. Un còp un jòc dessús, la Botiga de la consòla, de la Pi o del PC lo pòt
installar d'aquí.

Trobatz `LanShare.exe` sus la pagina de la Botiga, dins son onglet **LAN server**. I a pas res d'installar :
aviatz-lo, e garda sos paramètres dins `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![La fenèstra de LAN Share : los jòcs del servidor a esquèrra, los jòcs d'aqueste PC a drecha](../images/en/lanshare.jpg)

1. **Se connectar al servidor.** Picatz son adreça coma la Botiga l'a, `http://<its address>:<port>`, e quichatz
   **Connect**. Los jòcs ja presents sul servidor, e los problèmas que son pròpri escandalhatge trobèt,
   apareisson a esquèrra. Per metre de jòcs sul servidor, LAN Share a besonh d'una de doas intradas :
   - **Share** es lo dossièr de jòcs del servidor tal coma es partejat sus vòstra ret (Samba), per exemple
     `\\raspberrypi\games`. LAN Share i copia los jòcs e demanda al servidor d'escandalhar ; lo servidor el
     meteis legís totjorn sonque son dossièr.
   - **Token** es per un servidor aviat amb `--allow-uploads`. Picatz son geton : lo servidor l'aficha quand
     s'avia e lo garda dins `<state>/upload-token`. LAN Share manda alara per HTTP, e un mandadís que s'arrèsta
     a mièg camin repren ont s'èra arrestat.
2. **Publicar los jòcs de vòstre PC.** Causissètz lo dossièr ont son vòstres jòcs (un dossièr per jòc), marcatz los
   que volètz e quichatz **Publish the ticked games**. **On the server** vos ditz se lo servidor a ja un jòc (compara
   lo numèro de seria, o lo títol quand i a pas de numèro de seria), e un jòc que lo servidor a es pas jamai mandat
   doas vegadas. **Tick those not on the server** marca totes los autres per vos.
3. **Publicar un disc.** Metètz un disc PS1 dins lo lector del PC e quichatz **Read a disc and publish it**. LAN
   Share legís tot lo disc dins un `.bin` + `.cue`, nomenat segon lo títol del jòc. Per un jòc LibCrypt, escriu
   tanben lo fichièr `.sbi`, quand lo lector pòt legir lo sosvia. S'avètz causit las basas de donadas (vejatz mai
   bas), verifica la còpia amb lo bon imatge conegut. Puèi publica lo jòc. Per un jòc sus mantun disc, marcatz
   d'en primièr **The game has more than one disc** : LAN Share vos demanda cada disc seguent e los publica
   ensems coma un sol jòc.
4. **Levar de jòcs del servidor.** Causissètz-los e quichatz **Remove from the server...**. Res es pas suprimit :
   cada jòc es desplaçat dins un dossièr `.removed` al costat dels jòcs del servidor, e lo tornar desplaçar lo
   torna metre.

Las **Databases** (basas de donadas) son facultativas. Se mostratz a LAN Share lo dossièr de cobèrturas
d'AutoBleem (`coversU/P/J.db`) e lo `Sony - PlayStation.rdb` de RetroArch, las utiliza per nomenar los jòcs e per
verificar un disc qu'a legit.

Se volètz pas res copiar, marcatz **Also share the games on this PC with the Store** (desactivat per defaut) : LAN
Share servís alara dirèctament a la Botiga lo dossièr de jòcs de vòstre PC. Lo primièr còp que o fasètz, Windows
vos pausa una question sus son parafuòc : autorizatz sonque las rets privadas.

<!-- pagebreak -->

## 6. Los espleches de la consòla (PlayStation Classic)

Dos espleches venon amb una clau de PlayStation Classic e vos ajudan a configurar la consòla al delà de çò que sap
far en sortent de la bóstia. Totes dos semblan al demai del lançador, amb son tèma e sa lenga, e los comandatz amb
la maneta (dins l'assistent de manetas, tanben amb los botons de davant de la consòla). **PSC-Bios** es una
extension que ven amb lo paquet de la consòla : l'element *Ret e manetas* del Menú rapid e del menú sistèma la
dobrís, e la trobatz tanben dins la lista de las extensions. **ABFlashKit** es una aplicacion, dins la colleccion
de las aplicacions.

### 6.1 PSC-Bios

PSC-Bios es l'endrech ont connectatz la maquina al mond : vòstra ret WiFi, lo fus orari, las manetas Bluetooth, e
la disposicion dels botons d'una maneta qu'AutoBleem coneis pas. Ven amb lo paquet de la consòla e i es tanben sus
una Raspberry Pi e la clau PC. La dobrissètz amb *Ret e manetas* dins lo menú sistèma (o lo Menú rapid), o dempuèi
la lista de las extensions. Se l'extension es installada mas desactivada, l'element *Ret e manetas* es grisat e
ditz qu'*es desactivada - activatz-la dins Extensions* ; quichatz Cross dessús e la lista de las extensions se
dobrís sus PSC-Bios, per que la poscatz tornar activar.

Lo primièr ecran vos dona una vista d'ensemble : l'ora e lo fus orari, los adaptadors de ret (WiFi, Ethernet,
Bluetooth) amb lors adreças, e cada maneta brancada, amb una nòta que ditz s'a una assignacion de botons. Sus la
consòla, las partidas ret e Bluetooth demandan lo nucli AutoBleem (seccion 6.2) ; sus una Raspberry Pi o la clau
PC, utilizan los espleches del sistèma. L'assistent de manetas fonciona pertot.

![PSC-Bios : l'ecran principal Ret e manetas](../images/en/pscbios-main.jpg)

Dempuèi lo primièr ecran, un boton vos mena a cada partida :

| Boton | Çò que dobrís |
|---|---|
| Select | **Wi-Fi Network** (ret WiFi) vos connècta a vòstra WiFi (pel nucli, o per NetworkManager sus una Pi o un PC) : picatz lo nom de la ret o causissètz-la après una recèrca, picatz lo senhal, causissètz lo mòde del pilòt e quichatz *Apply / Restart Network*. Aquí reglatz tanben lo fus orari, e un còp connectat vesètz l'adreça IP de la consòla. |
| Square | **Bluetooth Controllers** (manetas Bluetooth) cèrca las manetas Bluetooth coma la DualShock 4, per n'associar una novèla o ne levar una que vos servís pas pus. |
| L1 | **DualShock 3 Pairing** (associacion DualShock 3) connècta vòstra primièra DualShock 3, que deu èsser brancada en USB per aquò, pel plugin sixaxis del nucli. |
| R1 | **Controller Mapping** (assignacion de las manetas) dobrís l'assistent de manetas, descrich mai bas. |
| Triangle | **About** (a prepaus) mòstra çò qu'es PSC-Bios. |
| Circle | **Back** (tornar) vos fa sortir de PSC-Bios e vos torna menar al lançador. |

**Lo WiFi e una maneta Bluetooth a l'encòp.** Sus la PlayStation Classic, lo WiFi e lo Bluetooth passan per una
sola e meteissa ràdio, amb una sola antena, e aquela ràdio pòt pas far qu'una causa a la fois. Tant qu'una
maneta Bluetooth es connectada e que l'utilizatz, la ràdio alterna - un moment per la maneta, un moment pel
WiFi -, e atal lo WiFi n'a mens per el e ven mai lent. Es subretot pendent un grand telecargament dempuèi la
*Botiga* (seccion 3.13) o una mesa a jorn (seccion 3.12) que o remarcatz: prenon alara fòrça mai de temps. Abans
un grand telecargament, amortatz doncas la maneta en tenent son boton PS quichat una desena de segondas, o
prenètz una maneta USB pendent aquel temps; lo WiFi a alara la ràdio per el sol. AutoBleem avisa ja lo WiFi
quand una maneta es connectada, per que los dos se partejan melhor la ràdio. Aquò ajuda fòrça, mas pòt pas far
desaparéisser l'efièch, perque i a totjorn pas qu'una ràdio.

**L'assistent de manetas.** Servissètz-vos-en quand una maneta fa pas res dins AutoBleem o qu'a sos botons a la
marrida plaça. Mòstra la maneta brancada tal coma es vertadièrament (cada axe, boton e capèl en nombres) e un
imatge de DualShock que s'aluca a mesura que quichatz. Coma la maneta qu'ensajatz es pas encara de fisança,
comandatz l'assistent amb los **botons de davant** de la consòla : **RESET** passa a la maneta seguenta, **OPEN**
comença l'assignacion, e **POWER** anulla o quita. Pendent l'assignacion, l'assistent vos demanda un boton après
l'autre : quichatz lo boton alucat sus l'imatge, o OPEN se vòstra maneta a pas aquel boton. Una quichada corta es
assignada coma de costuma.

Podètz tanben quitar a partir de la maneta : tenètz Circle quichat 2 segondas ; una barra s'emplena e lo pè de
pagina ditz *Hold 2 s: Exit*. Tant que la maneta a pas encara d'assignacion, tenir quin boton que siá 2 segondas
fa parièr (*Hold any button 2 s: Exit*). Sus un clavièr, Esc, Espaci e Entrada remplaçan POWER, RESET e OPEN.

A la fin, l'assignacion novèla es mesa en servici per que la poscatz ensajar, e OPEN l'enregistra jos un nom que
causissètz. A partir d'aquí, lo lançador la carga cada còp.

![PSC-Bios : l'assistent d'assignacion de las manetas](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit : lo nucli AutoBleem

Lo nucli AutoBleem remplaça lo nucli Linux de la consòla, e es facultatiu. Lo volètz se volètz mai de la consòla :
li balha un relòtge que fonciona, fa foncionar las claus WiFi e Bluetooth USB (per PSC-Bios e las manetas
Bluetooth), e apond la presa en carga dels botons de davant que l'emulador utiliza pels punts de represa.
ABFlashKit es l'esplech que l'installa. Salva d'en primièr la consòla, e la pòt tanben tornar metre a l'estat
d'origina pel sistèma de recuperacion de Sony el meteis.

> **Aqueste esplech escriu dins la memòria flash de la consòla.** Se l'escritura es interrompuda (lo corrent es
> copat, o la clau es levada), la consòla se poiriá pas pus aviar, e installar un nucli personalizat anulla sa
> garantida. Daissatz la consòla alimentada e la clau dedins fins que la consòla torne aviar soleta. ABFlashKit se
> dobrís sus aqueste avertiment : *I understand* contunha, *Quit* quita.

![Lo menú d'ABFlashKit](../images/en/abflashkit-menu.jpg)

ABFlashKit a tres accions :

- **Flash Kernel** installa lo nucli. S'i a pas encara de salvagarda de recuperacion sus la clau, ne fa d'en
  primièr una de las particions de la consòla (`LBOOT.EPB`). Verifica la salvagarda e l'imatge del nucli, escriu
  lo nucli e los fichièrs sistèma d'AutoBleem, e torna aviar la consòla. Quand ditz *All done - when the screen
  goes black replace power cord*, esperatz l'ecran negre, puèi desbrancatz lo cable d'alimentacion de la consòla
  e tornatz-lo brancar.
- **Full backup** salva las quatre particions de la consòla dins `LBOOT.EPB`, per las poder restablir puèi. S'i a
  ja una salvagarda, demanda abans de l'espotir.
- **Restore Mode** es lo camin de retorn cap al micrologicial d'origina. Verifica que la salvagarda de la clau es
  d'origina, plaça l'indicador de recuperacion e torna aviar sul sistèma de recuperacion de Sony, que restablís la
  consòla a partir de `LBOOT.EPB`.

Una barra de progression dessota cada etapa mòstra ont ne es. ABFlashKit flasharà pas una consòla que fa virar un
autre micrologicial personalizat, coma BleemSync o Project Eris : tornatz d'en primièr aquela consòla a l'estat
d'origina.

**Se connectar dempuèi un PC.** Se coneissètz Linux e volètz agachar dins la consòla, vos i podètz connectar
dempuèi un PC per un cable USB. Aquò demanda lo nucli AutoBleem ; fonciona pas sus una consòla d'origina.

1. Brancatz lo pòrt micro-USB de la consòla al PC amb un cable USB. Lo PC vei la consòla coma un adaptador de ret
   novèl, e trobatz l'adreça de la consòla dins los paramètres d'aquel adaptador sul PC.
2. Connectatz-vos amb `ssh root@<the console's address>`. Lo senhal per defaut es `autobleem`.

En plaça del senhal, podètz utilizar una clau. Metètz vòstra clau publica dins lo fichièr
`System/ssh/authorized_keys` sus la clau USB e tornatz aviar la consòla : a l'aviada seguenta, es aponduda al
compte root. Metre a jorn o tornar installar lo lançador la leva pas.

> **Lo senhal per defaut es lo meteis sus totas las consòlas** : qual que siá que pòt brancar un cable sus la
> vòstra se pòt connectar coma root. Utilizatz una clau quand podètz, e daissetz pas una consòla amb lo senhal per
> defaut ont d'autres i pòdon arribar.

<!-- pagebreak -->

## 7. Se quicòm va pas

La màger part dels problèmas an una causa simpla. Çai-jos, cadun comença per çò que vesètz, ditz perqué arriba, e
puèi çò que cal far. S'avètz besonh de demandar d'ajuda, los jornals son la primièra causa que vos demandaràn :
doncas venon en primièr.

**Trobar los jornals.** AutoBleem garda sos jornals en memòria pendent que vira, per pas escriure sus la clau tot
lo temps. Arriban dins `System/Logs/` sus la clau, la carta o lo dossièr de donadas sonque quand quicòm a mal
virat : quand lo lançador, un jòc PS1 o RetroArch se planta, los jornals son salvats dins `System/Logs/crash-<n>/`
(los tres darrièrs plantatges son gardats), e lo lançador vos o ditz un còp quand torna. Se cercatz un problèma
qu'es pas un plantatge, gardatz totes los jornals : activatz Opcions → *Diagnostic* → *Gardar los jornals sus la
clau :* (fonciona a partir de l'aviada seguenta), o creatz un fichièr void `System/Logs/keep` dempuèi un PC.
*Entresenhas de material* (seccion 4.2) mòstra tanben ont son los jornals, e Square aquí salva los actuals dins
`System/Logs/saved-<n>/`.

Vaquí los fichièrs que i trobaretz :

| Fichièr | Çò que vos ditz |
|---|---|
| `autobleem.log` | Çò que lo lançador el meteis a fach. |
| `launch.log`, `pcsx.log` | Cossí un jòc PS1 foguèt aviat, e çò que l'emulador diguèt pendent que virava. |
| `retroarch.log` | Çò que RetroArch diguèt pendent que virava. |
| `update.log` | Cossí s'es passada una mesa a jorn en linha ; es totjorn gardat sus la clau. |
| `updateroms.log` | Cossí s'es passat UpdateRoms sul PC (capítol 5) ; es totjorn gardat sus la clau. |

**Un imatge vos demanda de metre la clau, o la consòla s'es endormida.** AutoBleem tròba pas sa clau : n'i aviá
pas quand la consòla s'avièt, o es estada levada. Metètz-la dins quin pòrt USB que siá (un de davant es melhor,
seccion 2.1) abans la fin de las 5 minutas, o quichatz Power. Se la clau es pas estada levada coma cal, AutoBleem
la verifica d'en primièr : esperatz que la barra de progression acabe.

**RetroArch ditz qu'*a besonh d'una bibliotèca sistèma mai recenta que la d'aquesta consòla*.** Aquel RetroArch
foguèt bastit per un sistèma mai recent que lo de la consòla : i pòt doncas pas virar. Utilizatz lo RetroArch que
ven amb AutoBleem.

**Un jòc ditz qu'*es protegit per sa licéncia PSN e se pòt pas aviar*.** Los jòcs crompats sul PlayStation
Network son verrolhats a lor licéncia, e AutoBleem los pòt pas far virar. I a pas res de reparar.

**Un jòc es pas sus l'estatgièra.** Sovent, son dossièr es pas organizat coma l'escandalhatge s'i espèra.
Verificatz que cada jòc a son pròpri dossièr e es dins un dels formats de la seccion 3.10. Lo *Gestionari de
jòcs* (seccion 4.1) lista, après los jòcs, los dossièrs que l'escandalhatge a refusats, marcats *Pas apondut*, e
vos ditz perqué cadun foguèt refusat ; Square suprimís un tal dossièr. Après aver corregit un dossièr, *Tornar
escandalhar los jòcs* dins lo menú sistèma torna aviar l'escandalhatge.

**Los jòcs an pas de cobèrtura.** O ben las basas de cobèrturas son pas estadas installadas (tornatz aviar
l'installador amb elas marcadas), o ben, pels jòcs RetroArch sus una consòla, UpdateRoms es pas encara estat aviat
sul PC (capítol 5).

**Una maneta fa pas res, o sos botons son mesclats.** AutoBleem coneis pas la disposicion d'aquela maneta. Sus una
consòla, assignatz-la amb l'assistent de manetas de PSC-Bios (seccion 6.1). Sus una Pi o un PC, la pagina
Entresenhas de material (seccion 4.2) mòstra çò que lo sistèma vei de la maneta, çò que vos ajuda a saber se es
detectada o pas.

**L'ecran demòra negre après un jòc sus la consòla.** L'imatge del lançador es pas tornat quand lo jòc s'es
acabat. AutoBleem reconstruís sa fenèstra solet, fins a tres còps. Se l'ecran demòra encara negre, tenètz lo boton
Power quichat e tornatz alucar la consòla.

**Sus una Raspberry Pi**, podètz passar darrièr lo lançador quand n'avètz besonh : `Alt+F2` vos balha una invitacion
de connexion sus la segonda consòla, e SSH es activat dempuèi la primièra aviada. `sudo journalctl -u autobleem`
mòstra çò qu'a fach lo servici del lançador, e `sudo systemctl restart autobleem` lo torna aviar. Se la primièra
aviada a pas pogut acabar perque i aviá pas de ret, tòrna ensajar a l'aviada seguenta.

**Sus Windows**, `Esc` quita lo lançador. Vòstre dossièr de donadas es lo qu'avètz causit pendent l'installacion
(`Documents\AutoBleem` se l'avètz pas cambiat), e los jornals son dins son dossièr `System\Logs`.

**La consòla se torna aviar sens fin après una mesa a jorn en linha (clau formatada en ext4).** D'unas personas
formatan la clau en ext4, lo sistèma de fichièrs de Linux, en plaça de FAT32 o d'exFAT. Fins a la version
d'AutoBleem venenta, una mesa a jorn en linha sus una tala clau descompressa cada fichièr sens la permission que
li permet de s'executar coma programa. AutoBleem se pòt alara pas aviar, e la consòla se torna aviar sens fin.
Las claus FAT32 e exFAT son pas tocadas. I a doas manièras de o reparar.

**La correccion A** demanda un PC Linux. Brancatz la clau e tornatz far executables los programas d'AutoBleem.
Metètz vòstre pròpri camin de montatge en plaça de `/media/USER/STICK` ; la darrièra linha vos cal sonque se
RetroArch es installat :

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

Lo motiu `bin/emu*/pcsx-ab` de la segonda linha cobrís los dos emuladors : lo `pcsx-ab` classic e `pcsx-abnxt`,
installat jol nom `Autobleem/bin/emunxt/pcsx-ab` ; lo pus recent a doncas pas besonh d'una comanda a part.

**La correccion B** : tornatz installar la darrièra version d'AutoBleem sus la clau, coma a la seccion 2.1.
L'installador a besonh d'un PC que pòsca legir la clau. Se pòt pas legir la vòstra, la clau deu èsser formatada
d'en primièr, çò qu'escafa tot çò qu'es dessús : copiatz-ne vòstres jòcs abans de o far.

> Per evitar aquò, utilizatz **FAT32** (una consòla d'origina legís sonque FAT32 ; exFAT demanda lo nucli
> AutoBleem, capítol 6). La version venenta garda las permissions e AutoBleem las repara a cada aviada.

AutoBleem es un logicial liure (GNU GPL v3 o version ulteriora) e ven sens cap de garantida. Per l'ajuda e las
novèlas, rejonhètz lo servidor Discord ligat sus l'ecran A prepaus, o visitatz https://autobleem.retromenele.pl/.
