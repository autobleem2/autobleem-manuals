# Manuale utente di AutoBleem 2

AutoBleem 2 è un launcher di giochi nato per la **PlayStation Classic** che, dalla versione 2, funziona anche su
un **Raspberry Pi**, su un **PC avviato da una chiavetta USB** e su **Windows**. I tuoi giochi PS1 compaiono come
su uno scaffale, ognuno con la sua copertina e la sua scheda; partono nell'emulatore PCSX incluso e, se accanto
installi RetroArch, puoi giocare anche ai titoli di altri sistemi. Questo manuale spiega come installarlo su ogni
piattaforma, come usarlo tutti i giorni e a cosa servono gli strumenti che lo accompagnano.

> Tutti i download si trovano su **https://autobleem.retromenele.pl/**. La pagina è divisa per piattaforma: per
> ciascuna, il riquadro *Install* contiene ciò che devi scaricare, mentre i *Build inputs* che trovi sotto sono i
> file che gli installer vanno a prendersi da soli.

## 1. Cosa ottieni

Con AutoBleem la tua PlayStation Classic - oppure un Raspberry Pi, un vecchio PC o il tuo computer Windows -
diventa una piccola console con un vero menu per i tuoi giochi. Ecco cosa trovi:

- **Il launcher.** È quello che vedi all'accensione: uno scaffale di copertine da scorrere, con la scheda del gioco
  accanto. Da qui avvii i giochi, li dividi in set (PlayStation, RetroArch, App), cambi le impostazioni, gestisci
  memory card e salvataggi di stato e scarichi app e giochi dallo Store. Ha lo stesso aspetto e funziona allo
  stesso modo su ogni piattaforma.
- **Due emulatori PS1.** `pcsx-abnxt` è quello attuale e predefinito; `pcsx-ab` è l'emulatore classico che AutoBleem
  ha sempre incluso. Scegli tra i due nelle opzioni. Usano le stesse impostazioni e le stesse memory card, quindi puoi
  cambiare quando vuoi senza perdere nulla.
- **RetroArch**, se vuoi giocare anche con altri sistemi: NES, Super Nintendo, Mega Drive, Game Boy, cabinati arcade
  e molti altri. È facoltativo su ogni piattaforma. Copia le tue ROM e AutoBleem le ordina in elenchi e avvia ogni
  gioco con il core giusto. Anche i giochi PlayStation possono girare in RetroArch: il suo core *PlayStation 1* è in
  cima all'elenco dei core (sezione 3.9). Giochi come Doom funzionano invece con i tuoi file di gioco, messi in una
  cartella `Packages` (sezione 3.10).
- **Gli strumenti per la console.** *PSC-Bios* - nei menu si chiama *Rete e controller* - configura il Wi-Fi,
  l'orologio, i controller Bluetooth e la mappatura dei controller, sulla console come su un Raspberry Pi e sulla
  chiavetta PC. *ABFlashKit* installa il kernel di AutoBleem su una PlayStation Classic (capitolo 6).
- **UpdateRoms** per Windows. La PlayStation Classic non ha una rete propria, quindi questo programma per PC
  aggiorna gli elenchi di RetroArch e scarica le copertine mentre la chiavetta della console è collegata al PC.

![Il launcher: lo scaffale delle copertine, la scheda del gioco selezionato, i suggerimenti dei pulsanti](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Installazione

### 2.1 PlayStation Classic

AutoBleem gira interamente da una chiavetta USB. Dentro la console non cambia nulla: togli la chiavetta e la
console torna esattamente com'era. Ti servono un PC Windows, una chiavetta USB (USB 2.0, da 8 GB in su) e la
console.

La chiavetta non deve per forza essere vuota e **non viene formattata**, a meno che tu non lo chieda: AutoBleem si
installa accanto a quello che c'è già, e una chiavetta che usi già con AutoBleem 1.0 viene aggiornata così com'è
(vedi più avanti). Con una console originale la chiavetta deve essere in **FAT32**, perché il kernel della console
non legge l'exFAT. Una volta installato il kernel di AutoBleem (ABFlashKit, capitolo 6), la console si avvia anche da
una chiavetta exFAT, e sparisce così il limite di 4 GB per file del FAT32.

1. Scarica **AutoBleemInstaller-<version>.zip** dal riquadro PlayStation Classic del sito ed estrailo dove vuoi.
   Dentro ci sono `AutoBleemInstaller.exe` e il suo README. AutoBleem vero e proprio viene scaricato durante
   l'installazione, quindi il PC deve essere connesso a Internet.
2. Collega la chiavetta e avvia `AutoBleemInstaller.exe`. Scegli il **canale** - *Release* è la versione collaudata e
   va bene per quasi tutti, *Testing* è la prossima versione mentre la si collauda, *Nightly* è l'ultima build di
   sviluppo e potrebbe non funzionare - e poi l'unità della chiavetta. La riga sottostante ti dice quale versione di
   AutoBleem stai per installare e cosa c'è ora sulla chiavetta: *a fresh install* (una nuova installazione: gli altri
   file sulla chiavetta restano dove sono) oppure *AutoBleem <version> is on this stick: it will be updated* (la
   chiavetta verrà aggiornata, e giochi, salvataggi, memory card e impostazioni restano).
   **Non serve formattare.** Il pulsante **Format** accanto all'unità serve solo per una chiavetta nuova di zecca
   senza file system, per una che la console non riesce a leggere (in NTFS, per esempio) o per una che vuoi
   svuotare del tutto. Prima chiede conferma, poi cancella tutto il contenuto. Lì scegli FAT32, a meno che la console
   non abbia già il kernel di AutoBleem.
   Poi spunta cosa vuoi installare:
   - **Database delle copertine** - copertine e descrizioni dell'intero catalogo PS1, così i tuoi giochi trovano la
     loro copertina da soli (spuntato di serie; circa 300 MB).
   - **RetroArch** - RetroArch con i suoi core, applicazioni extra (Doom, Quake, Amiga, ...) e le risorse di
     libretro, per i giochi di altri sistemi. Non spuntato di serie; puoi aggiungerlo in seguito rilanciando
     l'installer.
   - **File BIOS** - i BIOS di cui alcuni core di RetroArch hanno bisogno per partire (solo con RetroArch).
   - **Giochi di esempio** - qualche gioco homebrew gratuito, perché al primo avvio lo scaffale non sia vuoto.
3. Premi **Install** e attendi. Le barre di avanzamento e il registro mostrano ogni passaggio. Alla fine la chiavetta
   si chiama `SONY` e contiene una copia di `UpdateRoms` (vedi il capitolo 5).
4. Rimuovi la chiavetta in modo sicuro, inseriscila nella **seconda porta USB frontale** della console (quella a
   destra, del giocatore 2) - la prima resta libera per il controller - e accendi la console. Al posto del menu
   originale parte AutoBleem. Per un secondo controller usa un hub USB sulla porta frontale oppure un controller
   Bluetooth.

**Accensione e spegnimento.** Con la chiavetta inserita la console si accende, fa lampeggiare la spia per qualche
secondo mentre riconosce AutoBleem e poi va in standby prima che sullo schermo compaia qualcosa. È normale: AutoBleem
parte attraverso il meccanismo di aggiornamento della console stessa, e quel meccanismo funziona così. Premi una volta
**Power** e compare il launcher.

Quando scegli *Spegni* nel menu di sistema, o premi il tasto Power della console, questa entra nello **standby di
AutoBleem**: prima AutoBleem scollega la chiavetta in modo sicuro, poi la spia diventa **arancione**, segno che è
andato tutto bene. Alla pressione successiva di Power il launcher torna in pochi secondi. **Finché la spia è
arancione puoi estrarre la chiavetta** e inserirla nel PC; Windows non ti chiederà di controllarla, perché è stata
scollegata correttamente. Rimettila al suo posto prima di premere Power. Se stacchi il cavo di alimentazione della
console, la volta successiva ripasserà dallo standby dell'avvio. Una spia **rossa** vuol dire che la console è spenta
davvero.

**La porta sul retro.** La porta micro-USB sul retro è la presa di alimentazione della console. Con il kernel di
AutoBleem accetta anche un dispositivo USB, ma il posto della chiavetta è in una porta frontale.

**Se manca la chiavetta.** Quando la console si avvia senza chiavetta, o quando la estrai mentre AutoBleem è in
funzione, un'immagine ti chiede di inserirla - va bene qualsiasi porta USB. AutoBleem aspetta 5 minuti e poi manda la
console in standby; premi Power se vuoi che ci vada subito.

![L'immagine che chiede di inserire la chiavetta](../images/en/insert-stick.jpg)

**Quando viene controllata la chiavetta.** Se la chiavetta non è stata scollegata correttamente - l'hai estratta
mentre AutoBleem era in funzione, oppure è mancata la corrente - AutoBleem la controlla alla ricerca di errori prima
di riutilizzarla: all'avvio, al risveglio o quando la ricolleghi. Una barra di avanzamento mostra a che punto è il
controllo. Su una chiavetta grande può volerci un po'; lascialo finire e non spegnere la console nel frattempo.

![Il controllo della chiavetta](../images/en/stick-check.jpg)

**Aggiornare.** Per aggiornare una chiavetta, rilancia l'installer su di essa: ora il pulsante dice *Update*. Installa
la versione più recente del canale che scegli; giochi, salvataggi, impostazioni e contenuti di RetroArch restano, e
vengono sostituiti solo i file di AutoBleem. Una console con il kernel di AutoBleem e il Wi-Fi può anche aggiornarsi
da sola (sezione 3.12).

**Passare da AutoBleem 1.0 (o AutoBleem-NG) ad AutoBleem 2.** Usi lo stesso installer sulla stessa chiavetta, senza
formattarla:

1. Per prima cosa copia l'intera chiavetta sul PC, come backup: non si sa mai.
2. Collegala, avvia `AutoBleemInstaller.exe` e scegli canale e unità. **Non** premere Format.
3. Premi **Install**. L'installer trasferisce la vecchia struttura in quella nuova: RetroArch, le ROM e i temi vanno
   dove se li aspetta AutoBleem 2, e le vecchie cartelle delle ROM (`nes`, `snes`, ...) prendono i nomi di sistema di
   RetroArch. Giochi, salvataggi di stato, memory card, ROM e salvataggi di RetroArch restano tutti, e resta anche
   `config.ini`: cambia solo il suo emulatore PS1, che passa a pcsx-abnxt.
4. Rimetti la chiavetta nella console. La prima scansione ricostruisce l'elenco dei giochi e le playlist. Per avere
   le copertine dei giochi RetroArch, avvia UpdateRoms sul PC (capitolo 5).

> La console originale non ha né orologio né rete. Le date compaiono solo dopo l'installazione del kernel di
> AutoBleem (capitolo 6), e le copertine dei giochi RetroArch arrivano da UpdateRoms sul PC (capitolo 5).

I tuoi giochi PS1 vanno nella cartella `Games` della chiavetta, una cartella per gioco: la sezione 3.10 spiega come
organizzarli.

### 2.2 Raspberry Pi

Con AutoBleem un Raspberry Pi diventa una piccola console: si avvia direttamente nel launcher, senza nessun desktop in
mezzo. Sul sito trovi due immagini già pronte per la scheda, a 32 e a 64 bit, e un pacchetto per un Raspberry Pi OS
Lite che hai già installato.

| Modello | Immagine 32 bit | Immagine 64 bit | Note |
|---|---|---|---|
| Raspberry Pi 5 | sì | sì | |
| Raspberry Pi 4 Model B, Pi 400 | sì | sì | |
| Raspberry Pi 3 Model B / B+ / A+ | sì | sì | va bene per il launcher e la PS1 |
| Raspberry Pi Zero 2 W | sì | sì | 512 MB di RAM: la PS1 gira, i core di RetroArch più pesanti no |
| Raspberry Pi 2 Model B | sì | solo v1.2 | lento con qualsiasi cosa in 3D |
| Raspberry Pi 1, Zero, Zero W | no | no | ARMv6 - nessuna delle due immagini funziona |

**Per i giochi PS1 scegli l'immagine a 32 bit.** Il ricompilatore ARM veloce del `pcsx-ab` classico esiste solo a 32
bit, quindi con la build a 64 bit i giochi PS1 vanno più lenti. L'immagine a 64 bit ha però più core di RetroArch:
sceglila se gli altri sistemi ti interessano più della PS1.

**Con Raspberry Pi Imager:**

1. Installa Raspberry Pi Imager (raspberrypi.com/software). In *Choose OS* scegli *Use custom* e il file
   `autobleem-<version>-rpi-armhf.img.xz` (32 bit) o `-arm64.img.xz` (64 bit) che hai scaricato - oppure aggiungi
   l'URL di un repository nelle impostazioni dell'app e scegli AutoBleem dall'elenco. Ce n'è uno per canale:
   `https://autobleem.retromenele.pl/rpi-imager/os_list.json` per l'ultima release,
   `.../os_list-testing.json` per la build in collaudo e `.../os_list-nightly.json` per l'ultima build di sviluppo.
   La scheda Raspberry Pi della pagina dei download elenca quelli disponibili, ognuno con un pulsante *Copy*.
2. Nella schermata di personalizzazione di Imager (l'ingranaggio, o la domanda che compare dopo *Next*) imposta **nome
   utente e password, rete Wi-Fi e paese, e attiva SSH**. Al primo avvio AutoBleem ha bisogno di una rete.
3. Scrivi la scheda, inseriscila nel Pi con uno schermo e una tastiera o un controller collegati e accendilo.

**Il primo avvio** richiede da 5 a 25 minuti, e lo schermo ti tiene aggiornato su quello che succede. Se non c'è
rete, te ne chiede una: scegli il tuo Wi-Fi dall'elenco e digita la password. Poi ti chiede se installare RetroArch -
se non rispondi entro un minuto, lo installa. Dopodiché allarga la partizione di sistema, trasforma il resto della
scheda nella partizione `AUTOBLEEM` per i tuoi giochi, installa RetroArch con i suoi core, i pacchetti di BIOS e i
giochi di esempio, e si riavvia nel launcher.

Se preferisci non rispondere a domande al primo avvio, scrivi prima le risposte in **`autobleem.txt`**, sulla
partizione di boot della scheda: qualsiasi PC può aprirlo e modificarlo.

| Chiave | Predefinito | Significato |
|---|---|---|
| `root_gib` | 8 | La dimensione della partizione di sistema in GiB; il resto diventa la partizione dei giochi. |
| `hdmi_mode` | 1920x1080@60 | La modalità video per tutto l'avvio (`1280x720@60` per un televisore più vecchio). |
| `retroarch` | (chiesto) | `yes` / `no` - RetroArch e gli altri sistemi, oppure solo PS1. |
| `thumbnails` | none | `boxarts` copia in locale l'intera raccolta di copertine, per averle anche offline (~9000 file). |
| `bios`, `downloads`, `samples` | yes | Metti `no` per saltare i pacchetti di BIOS, qualsiasi download o i giochi di esempio. |

**Su un Raspberry Pi OS Lite che hai già** (Bookworm o Trixie): copia `autobleem-rpi.tar.gz` (o quello arm64) sul Pi,
estrailo e lancia `sudo bash install.sh`. Fa le stesse domande, ricava lo spazio per la partizione dei dati
restringendo quella di sistema al riavvio successivo (`--shrink-root <GiB>`) e mette il launcher sulla prima console.

Finita l'installazione, riempi di giochi la **partizione `AUTOBLEEM`** della scheda (in exFAT): estrai la scheda e
aprila su un PC qualsiasi, oppure copia in rete (SSH è attivo). I giochi PS1 vanno in `Games/`, le ROM degli altri
sistemi in `RetroArch/roms/<sistema>/`, il BIOS PS1 in `System/Bios/` (sezione 3.11) e i temi in `Themes/`.

### 2.3 Chiavetta USB per PC

Lo stesso discorso vale per qualsiasi PC in grado di avviarsi da USB: la chiavetta avvia il PC direttamente in
AutoBleem e lascia stare il suo disco. È un sistema a 32 bit, quindi vanno bene anche le macchine vecchie.

1. Scrivi l'immagine su una chiavetta da 8 GB o più. **Su Windows** usa **AutoBleemFlasher** (riquadro PC del sito:
   estrailo e avvia `AutoBleemFlasher.exe`; chiede i diritti di amministratore, perché scrive un intero disco).
   Scegli il canale e la chiavetta, premi *Write* e conferma due volte: scarica l'immagine, la verifica, la scrive e la
   rilegge. Ti vengono proposte solo chiavette USB e schede SD, mai il disco da cui gira Windows, e **tutto il
   contenuto della chiavetta scelta viene cancellato**. Su Linux o macOS scarica
   `autobleem-<version>-pcusb-i386.img.xz` dal riquadro PC e scrivilo con
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (oppure con balenaEtcher).
2. Avvia il PC dalla chiavetta (con il tasto del menu di avvio del tuo PC - F12, F8, Esc...). Funziona sia l'avvio
   BIOS sia quello UEFI; **il Secure Boot deve essere disattivato**.
3. Il primo avvio funziona come sul Pi: chiede una rete se non c'è un cavo collegato, chiede di RetroArch, installa
   tutto - circa otto minuti con una rete via cavo - e si riavvia nel launcher.

Dopo, la chiavetta ha una partizione `AUTOBLEEM` per i tuoi giochi. Se la colleghi a un PC acceso con Windows 10
(versione 1903 o successiva), compare come una seconda unità su cui copiare i giochi. `autobleem.txt` si trova sulla
prima partizione, con le stesse chiavi del Pi (tranne `hdmi_mode`: un PC usa sempre la modalità nativa dello schermo).

### 2.4 Windows

Se vuoi AutoBleem sul tuo computer Windows, funziona anche come un normale programma: a schermo intero, con gli
emulatori e RetroArch avviati come programmi a sé.

1. Scarica **AutoBleemSetup-<version>.exe** ed eseguilo. Si installa per il solo utente, senza diritti di
   amministratore: il programma va in `%LOCALAPPDATA%\Programs\AutoBleem`, i dati (giochi, impostazioni, temi,
   RetroArch) in una cartella a tua scelta, che di serie è `Documents\AutoBleem`.
2. Spunta i componenti - i database delle copertine, RetroArch (la build ufficiale per Windows con i suoi core), i
   file BIOS, i giochi di esempio - e lascia che l'assistente di installazione li scarichi.
3. Avvia AutoBleem dal menu Start o dal desktop. Sul PC la tastiera fa da controller (sezione 3.2).

Per aggiornare, esegui sopra un setup più recente: il programma viene sostituito e la cartella dei dati resta
com'è. Il launcher controlla anche il sito una volta al giorno e ti propone l'aggiornamento quando ce n'è uno
(sezione 3.12).

<!-- pagebreak -->

## 3. Usare AutoBleem

### 3.1 Il launcher

Il launcher è il posto in cui scegli a cosa giocare. Mostra i tuoi giochi come una fila di copertine, come le
custodie su uno scaffale vero, e tu lo scorri finché non trovi quello che cerchi. Tutto il resto di AutoBleem - le
impostazioni, le memory card, lo Store - si apre da qui, ed è qui che torni quando esci da un gioco.

Il gioco selezionato sta al centro dello scaffale, con un leggero riflesso sotto. Accanto compare la sua scheda, in
una piccola griglia: editore, anno, numero di serie, regione, numero di giocatori e la data dell'ultima partita.
Quando AutoBleem non conosce uno di questi dati, la riga viene omessa invece di restare vuota. Accanto alla scheda
c'è un pulsante di avvio. Un gioco senza copertina viene mostrato come un disco appoggiato nel vassoio nero di una
custodia vuota, così ha comunque il suo posto sullo scaffale.

L'aspetto del launcher dipende dal tema. Quello predefinito è **ab2.0.0**: una nuova installazione lo adotta, e lo fa
anche un aggiornamento che lo porta con sé, ma una volta sola - se poi scegli un altro tema (sezione 3.6), quello
resta.

**La barra dei suggerimenti**, in fondo allo schermo, ti dice cosa fanno i pulsanti in quel momento. Ha due righe da
quattro posti. La prima riguarda il gioco selezionato: avviarlo, avviarlo in RetroArch, aprire la riga di icone che
sta sotto o aprire il menu rapido. La seconda non cambia mai: Select sceglie il set, Start pesca un gioco a caso,
Triangle mostra la guida dei pulsanti e L2 + R2 apre il menu di sistema. Un suggerimento appare attenuato quando il
suo pulsante non ha niente da fare.

**I giochi nuovi li trova da solo.** A ogni avvio il launcher scansiona la cartella dei giochi in background, così un
gioco che hai copiato a macchina spenta compare senza che tu debba fare nulla. Durante la scansione una bolla in alto
a destra ne mostra l'avanzamento, e i nuovi giochi arrivano sullo scaffale man mano che vengono trovati: nel frattempo
puoi continuare a sfogliare.

**Con un'installazione nuova** non ci sono ancora giochi. Al posto di uno scaffale vuoto vedi una scheda di
benvenuto, *Ciao e benvenuto in AutoBleem!*, che ti dice di mettere i giochi in `Games` e di premere *Riscansiona i
giochi*. Ti indica il posto giusto per la tua piattaforma: sulla chiavetta (PlayStation Classic, chiavetta PC), sulla
scheda SD (Raspberry Pi) o nella cartella di AutoBleem (Windows). La scheda sparisce non appena una scansione trova il
primo gioco.

**Le notifiche** sono le bolle in alto a destra. Ti tengono informato senza intralciarti: l'avanzamento della
scansione, il nome del set appena scelto (*Sto mostrando: ...*), un controller con la batteria quasi scarica, un
avviso dopo un crash, un processore di scansione al lavoro e un download dallo Store. La bolla di un download mostra
la velocità e il tempo rimanente, per esempio `1.4 MB/s · 0:42`. Per quanto tempo restano a schermo le bolle
informative lo decidi tu: Opzioni → *Durata avviso:*.

**Le batterie dei controller.** Sulla console, su un Raspberry Pi e sulla chiavetta PC (non su Windows), ogni
controller wireless che comunica lo stato della batteria compare come una piccola icona con la percentuale, su una
targhetta tutta sua; le targhette si impilano a partire dall'angolo in alto a sinistra. Un controller che gioca come
giocatore 1 o giocatore 2 porta l'etichetta P1 o P2, secondo l'opzione *Scambia giocatore 1 / giocatore 2*
(sezione 3.6); un controller non associato a nessun giocatore, o un terzo controller, non ha etichetta. Quando la
batteria di un controller si sta scaricando, una notifica te lo dice una volta, con il nome del controller e la
percentuale.

**L'etichetta del canale.** Se usi una build che non è una release definitiva, una piccola etichetta sotto le
targhette delle batterie, nell'angolo in alto a sinistra, te lo ricorda. È un chip con il canale e accanto la versione
abbreviata: `ALPHA`, `BETA` o `RC` per una pre-release, `TESTING` per qualsiasi altra pre-release, `NIGHTLY` per una
build notturna e `DEV` per una build compilata a mano (per `DEV` la versione è il commit da cui è stata compilata). Una
release non mostra alcuna etichetta.

![La scelta del set: tre schede e i gruppi di quella attuale con il numero di giochi](../images/en/set-picker.jpg)

### 3.2 I comandi

AutoBleem è fatto per essere usato solo con il controller, e i pulsanti hanno lo stesso significato in ogni
schermata: Cross conferma, Circle torna indietro, Triangle aiuta. Se non ricordi cosa fa un pulsante, te lo dice la
barra dei suggerimenti in fondo allo schermo, e Triangle sullo scaffale apre la guida con tutti i pulsanti di tutte le
schermate (sezione 4.3). Sullo scaffale i pulsanti funzionano così:

| Pulsante | Sullo scaffale |
|---|---|
| Sinistra / Destra | Passa al gioco precedente o successivo; tienilo premuto per continuare a scorrere. |
| L1 / R1 | Salta all'iniziale precedente o successiva dei titoli, per attraversare in fretta uno scaffale lungo. Su uno scaffale vuoto con un'unità USB collegata, R1 apre *Disco* (sezione 3.9a). |
| Cross | Avvia il gioco selezionato: un gioco PS1 nell'emulatore PS1, un gioco RetroArch nel suo core, un'app dopo il suo leggimi. |
| Square | Avvia invece il gioco PS1 selezionato in RetroArch. Se è selezionato un disco in un'unità USB, copia il disco (*Copia disco*, sezione 3.9a). |
| Circle | Ti riporta alla vista del disco quando c'è un disco nell'unità (sezione 3.9a). |
| Triangle | Apre la guida dei pulsanti. |
| Start | Pesca un gioco a caso dal set attuale, per quando non sai decidere. |
| Select | Apre la scelta del set, dove decidi quali giochi mostra lo scaffale (sezione 3.3). |
| Su | Apre il menu rapido (sezione 3.4). |
| Giù | Apre la riga di icone sotto il gioco (*IMPOSTAZIONI*, *Gioco*, *MEMORY CARD*, *RIPRENDI*); Su la richiude. |
| L2 + R2 | Apre il menu di sistema (sezione 3.5). |

**Con la tastiera.** Su un PC senza controller, o con una tastiera USB collegata alla console, a un Pi o alla
chiavetta PC, i tasti prendono il posto dei pulsanti. Le frecce sono la croce direzionale, Invio è Cross, Esc o
Backspace è Circle, Tab è Triangle e la barra spaziatrice è Square. F1 e F2 sono Select e Start, Pagina su e Pagina giù
sono L1 e R1, Home e Fine sono L2 e R2, e F10 apre il menu di sistema.

Su Windows alcuni tasti cambiano. Lì Esc chiude AutoBleem (capitolo 7), quindi Circle è solo Backspace, la barra
spaziatrice fa da Start e la S da Square. Le lettere possono inoltre sostituire l'intero controller, senza
bisogno delle frecce: X, O, S e T sono Cross, Circle, Square e Triangle, I, J, K e L la croce direzionale (su,
sinistra, giù, destra), B è Select, Q ed E sono L1 e R1, 1 e 2 sono L2 e R2.

**In tutti gli elenchi e i menu** ci si muove allo stesso modo: Su e Giù spostano il cursore, L2 e R2 girano pagina, L1
e R1 saltano alla prima o all'ultima riga, Cross seleziona e Circle torna indietro. Non devi mai cercare un pulsante
Salva: una schermata di impostazioni le salva quando la lasci con Circle.

**Uscire da un gioco o da un'app.** Tieni premuti Start + Select, oppure Home, per 2 secondi e sei di nuovo in
AutoBleem. Funziona con qualsiasi controller: quello della console, un controller USB o uno Bluetooth. Una pressione
breve degli stessi pulsanti apre invece il menu dell'emulatore. Un'app non ha questo menu, quindi lì conta solo la
pressione lunga.

![La riga di icone sotto il gioco selezionato](../images/en/launcher-icons.jpg)

### 3.3 I set

Una libreria grande si sfoglia meglio un pezzo alla volta. I set ti permettono di ridurre lo scaffale a un solo tipo
di giochi - solo i preferiti, solo i giochi Super Nintendo, solo quelli di una certa cartella - così non devi scorrere
centinaia di copertine per arrivare a quella che vuoi.

Premi **Select** e si apre la scelta del set. Ha tre schede, PlayStation, RetroArch e App: L1 e R1 passano dall'una
all'altra, Su e Giù scorrono i gruppi della scheda (L2 e R2 una pagina alla volta) e Cross mostra sullo scaffale il
gruppo scelto. Circle (*Indietro*) chiude la finestra senza cambiare nulla. Questi tasti sono ricordati anche nel piè
di pagina. Ogni riga dice quanti elementi contiene. Un gruppo vuoto si apre su uno scaffale vuoto, dove la riga di
icone offre solo *IMPOSTAZIONI*.

**La scheda PlayStation.** Su una PlayStation Classic comincia con *Tutti i giochi* e *Giochi interni* (i venti
giochi incorporati nella console), seguiti da *Giochi su USB* - tutto ciò che sta in `Games/` - e da un gruppo per ogni
cartella che hai creato lì dentro: un gioco in una sottocartella appartiene quindi al gruppo di quella cartella.
Seguono *Giochi preferiti*, *Cronologia giochi* e, non appena hai segnato almeno un gioco come gioco per pistola
ottica, *Giochi con pistola*. Un Raspberry Pi, una chiavetta PC e Windows non hanno giochi interni, quindi lì l'elenco
parte da *Giochi su USB*, che è tutta la tua libreria.

**La scheda RetroArch** c'è solo dove RetroArch è installato. Contiene un gruppo per ogni sistema di cui hai giochi,
più i Preferiti e la Cronologia di RetroArch.

**La scheda App** ordina le applicazioni per tipo: *Tutte le app*, poi *Giochi*, *Emulatori*, *Strumenti*, *Media* e
*Altro*. Il gruppo di un'app è indicato nel suo file `app.ini`. In questa scheda trovi anche le **app PE**, cioè
programmi Windows eseguiti dal runner PE; quelle che la console non può avviare sono segnate con *non può funzionare
su questa console*. Dove il launcher la mostra, nell'elenco c'è anche una riga *Pacchetti* (sezione 3.10).

### 3.4 Il menu rapido

Il menu rapido è un breve elenco delle cose che ti servono più spesso mentre sfogli i giochi, così non devi andarle a
cercare nel menu di sistema completo. Aprilo con **Su** sullo scaffale, oppure con l'**icona dell'ingranaggio** nella
riga di icone (quella con *IMPOSTAZIONI*, *Gioco*, *MEMORY CARD* e *RIPRENDI*).

Su e Giù scorrono le voci (dall'ultima il cursore torna alla prima), Cross ne sceglie una e Circle chiude il menu. Una
riga sotto il menu descrive la voce selezionata. Ecco le voci:

- *Riscansiona i giochi* cerca subito giochi nuovi, modificati o rimossi: comodo quando hai appena copiato dei giochi
  e non vuoi aspettare.
- *Store* apre lo Store di AutoBleem, dove sfogli e installi giochi, app ed estensioni (sezione 3.13).
- *Core di RetroArch*, dove RetroArch è installato, ti fa scegliere il core che fa girare ciascun sistema.
- *Rete e controller* apre le schermate del Wi-Fi, dell'abbinamento Bluetooth e della mappatura dei controller
  (capitolo 6). C'è solo quando un'estensione installata le fornisce: lo fa PSC-Bios, sulla console, su un Raspberry
  Pi e sulla chiavetta PC. Se quell'estensione è installata ma disattivata, la voce è in grigio e la sua descrizione ti
  dice di attivarla in Estensioni; Cross apre allora l'elenco delle estensioni proprio su di lei.
- *Riavvia il launcher* chiude AutoBleem e lo riavvia (solo sulla console, su un Raspberry Pi e sulla chiavetta PC).
- *Menu di sistema...* apre il menu di sistema completo con tutto il resto: Opzioni, Gestore del gioco, Spegni e
  altro (sezione 3.5).

Tutto ciò che è qui, tranne lo Store, i core di RetroArch e *Riavvia il launcher*, si trova anche nel menu di sistema.

![Il menu rapido](../images/en/quick-menu.jpg)

### 3.5 Il menu di sistema

Il menu di sistema raccoglie tutto ciò che AutoBleem sa fare oltre al gioco: le impostazioni, gli strumenti per la
libreria e le memory card, le informazioni sulla macchina e il modo per spegnerla. Premi insieme **L2 + R2** (in
qualsiasi ordine) e si apre sopra lo scaffale. Le voci sono raggruppate sotto i titoli *Libreria*, *Sistema* ed
*Esci*, con le due più usate in cima. Una riga in fondo al menu descrive la voce selezionata, così puoi guardarti
intorno prima di scegliere.

| Sezione | Voce | A cosa serve |
|---|---|---|
| (in cima) | *Riscansiona i giochi* | Cerca subito giochi nuovi, modificati o rimossi. La scansione tiene già d'occhio la cartella da sola, quindi ti serve solo quando non vuoi aspettare. |
| | *Estensioni* | Elenca le estensioni presenti sulla chiavetta, come lo Store di AutoBleem, per avviarle o disattivarle (sezione 3.13). |
| *Libreria* | *Gestore del gioco* | Mostra i giochi PS1 come elenco con le loro cartelle, dove puoi eliminare un gioco o cancellare le copertine (sezione 4.1). Non si apre durante una scansione. |
| | *Memory card* | Gestisce i tuoi set di memory card condivise (sezione 3.8). |
| | *Processori di scansione* | Stabilisce l'ordine dei programmi che ogni scansione esegue per primi, e li attiva o disattiva (sezione 3.14). Non si apre durante una scansione. |
| *Sistema* | *Opzioni* | Apre le impostazioni di AutoBleem (sezione 3.6). |
| | *Rete e controller* | Apre le schermate del Wi-Fi, dell'abbinamento dei controller Bluetooth, della configurazione del DualShock 3 e della mappatura dei controller (capitolo 6). C'è solo quando un'estensione le fornisce: vedi sotto. |
| | *Informazioni hardware* | Mostra i dati della macchina - sistema, CPU, memoria di archiviazione, interfacce di rete, fuso orario, schermo e i controller con le loro mappature - nella stessa pagina su ogni piattaforma (sezione 4.2). Circle ti riporta al menu di sistema. |
| | *Gamepad virtuale* | Mostra i controller che vengono passati alle app e quelli che vede il demone, utile quando un controller non funziona in un'app (sezione 4.5). Circle ti riporta al menu di sistema. |
| | *Aggiornamento software* | Cerca subito sul sito una versione più recente di AutoBleem o di RetroArch, senza aspettare il controllo giornaliero (sezione 3.12). Quando il launcher ne conosce già una, la riga dice *Aggiornamento disponibile*. Su una PlayStation Classic servono il kernel di AutoBleem e una rete Wi-Fi. |
| | *Informazioni su* | Mostra i riconoscimenti e la licenza. |
| *Esci* | *RetroArch* | Lascia il launcher per il menu di RetroArch vero e proprio, con le sue impostazioni e i suoi elenchi di contenuti; quando chiudi RetroArch torni nel launcher. C'è solo dove RetroArch è installato. |
| | *Spegni* | Spegne la macchina dopo averti chiesto conferma (vedi sotto). |

**Rete e controller** compare solo dove un'estensione installata fornisce la voce `network`, cosa che un'estensione
dichiara con `Provides=network` nel suo `extension.ini`. Lo fa PSC-Bios sulla console, su un Raspberry Pi e sulla
chiavetta PC. Se quell'estensione è installata ma disattivata, la voce resta nel menu, in grigio, e la sua
descrizione ti dice di attivarla in Estensioni; Cross su di essa apre l'elenco delle estensioni proprio su
quell'estensione.

**Spegni** fa ciò che è adatto alla macchina. Sulla console la mette nello standby di AutoBleem: la chiavetta viene
scollegata, la spia diventa arancione e Power riporta il launcher in pochi secondi (sezione 2.1). Su un Raspberry Pi o
un PC la macchina si spegne.

![Il menu di sistema](../images/en/system-menu.jpg)

### 3.6 Opzioni

Nelle opzioni rendi AutoBleem davvero tuo: l'immagine sullo schermo, l'aspetto del launcher, la lingua, l'audio,
l'emulatore PS1 che fa girare i giochi. Le apri dal menu di sistema (*Opzioni*) o con l'icona *IMPOSTAZIONI* sotto un
gioco. Di solito schermo e lingua si impostano una volta per tutte, e ci si torna quando qualcosa non va su un certo
televisore o quando si ha voglia di cambiare.

Le impostazioni sono divise in gruppi, ognuno con un titolo. Su e Giù passano da una riga all'altra, Sinistra e Destra
cambiano il valore della riga su cui sei: un tocco sposta di un passo, tenendo premuto si va avanti. L1 e R1 saltano
alla prima o all'ultima riga, L2 e R2 girano pagina. Sulle righe in cui scegli un tema, una musica o un carattere,
Start ne pesca uno a caso. Un'impostazione che si accende o si spegne mostra **ON** oppure **OFF**. Ogni modifica si
vede subito, e Circle lascia la schermata salvando tutto: non c'è altro da confermare. L'unica eccezione è la modalità
dello schermo, che viene provata quando esci dalle opzioni (vedi *Schermo* qui sotto).

Alcune righe compaiono solo dove hanno senso: quelle CRT solo con un'immagine 4:3, quelle di RetroArch solo dove
RetroArch è installato, i giochi interni solo su una PlayStation Classic.

| Gruppo / impostazione | A cosa serve |
|---|---|
| *Interfaccia*: *Schermo:* | Imposta la risoluzione dello schermo, per il launcher e per l'emulatore PS1. *Auto* usa la modalità nativa dello schermo e ti dice qual è, per esempio *Auto (1920x1080)*; puoi anche scegliere qualsiasi modalità elencata dallo schermo. La console offre 720p, 1080p e *CRT 4:3* (720x480), la modalità per un vecchio televisore a tubo catodico o per un dispositivo di acquisizione 4:3. Cambiala quando l'immagine non entra nel televisore o appare sfocata. Questa riga non c'è quando AutoBleem gira in una finestra su una macchina di sviluppo. |
| *Margine CRT:* | Rimpicciolisce un po' tutto, da 0 a 10 % a passi dell'1 %, perché i vecchi televisori tagliano i bordi dell'immagine. Alzalo finché la barra dei suggerimenti e gli angoli non si vedono per intero. Compare solo con un'uscita 4:3, ha effetto subito e viene applicato già prima della schermata iniziale. |
| *Altezza dell'immagine:* | Rende l'immagine più alta o più bassa, da -40 a +40 a passi di 2, su qualsiasi uscita 4:3 - *CRT 4:3*, oppure una modalità 4:3 su un'uscita VGA o PC. Usala quando su un vecchio televisore l'immagine appare schiacciata o esce sopra e sotto. Ha effetto subito, e l'immagine dei giochi in RetroArch la segue. |
| *Scala schermo emulatore:* | Decide come l'emulatore PS1 adatta l'immagine del gioco allo schermo. *1x1* mostra i pixel originali della PlayStation, piccoli e precisi; *2x (intera)* e *4:3 (intera)* ingrandiscono solo per multipli interi, e danno l'immagine più nitida; *4:3* mantiene le proporzioni originali; *Schermo intero* stira l'immagine su tutto lo schermo. Sostituisce il vecchio interruttore Widescreen. Il `pcsx-ab` classico e RetroArch conoscono solo schermo intero e 4:3. |
| *Alone dello schermo:* | Su ON, le fasce vuote ai lati dell'immagine del gioco (dove non riempie lo schermo) si riempiono di un morbido bagliore preso dall'immagine stessa invece di restare nere. Funziona con `pcsx-abnxt`. |
| *Tema di AutoBleem:* | Cambia l'aspetto del launcher. I temi stanno in `Themes/`, e anche un tema in formato zip messo lì compare con il suo nome. I temi forniti con AutoBleem vengono rinnovati a ogni aggiornamento, quindi se vuoi personalizzarne uno, prima copialo con un altro nome. Quello predefinito è **ab2.0.0**. |
| *Stile delle cover:* | Sceglie la custodia di plastica disegnata intorno alle copertine PS1. |
| *Riflesso della copertina:* | Fa passare un riflesso sulla copertina selezionata ogni volta che lo scaffale si ferma. |
| *Lingua:* | Imposta la lingua del launcher; ce ne sono 17, e il cambio è immediato. |
| *Durata avviso:* | Stabilisce per quanto restano a schermo le bolle informative (*Sto mostrando: ...*, il riepilogo della scansione), da 0 a 20 secondi; 0 mostra *Disattivato* e le spegne. I messaggi di errore hanno una durata fissa tutta loro, così non te ne perdi nessuno. |
| *Schermata iniziale:* | Mostra l'immagine di AutoBleem mentre il launcher si avvia; disattivala per arrivare dritto allo scaffale. |
| *Animazioni:* | Anima il passaggio da una schermata all'altra; disattivale se preferisci che ogni schermata compaia all'istante. |
| *Caratteri*: *Usa il carattere predefinito:* | Su ON il launcher usa il suo carattere (Red Hat Text); disattivalo per usare quello scelto nella riga successiva. |
| *Carattere:* | Sceglie un carattere tuo: qualsiasi file `.ttf` o `.otf` in `resources/fonts`, `RetroArch/fonts` o nella cartella del tema. La riga mostra il nome del carattere effettivamente in uso. |
| *Audio*: *Musica:*, *Musica di sottofondo:* | *Musica:* sceglie il brano che accompagna il launcher - quello del tema, o un file di `resources/music`. *Musica di sottofondo:* decide se suonare musica oppure no. |
| *Emulazione*: *Emulatore PS1:* | Sceglie l'emulatore in cui partono i giochi PS1: `pcsx-abnxt`, quello predefinito (l'attuale PCSX-ReARMed con le aggiunte di AutoBleem), oppure `pcsx-ab`, quello classico. Prova l'altro quando un gioco non gira bene. Un punto di ripristino salvato con uno continua nell'altro, a meno che il gioco non girasse senza file BIOS. |
| *Scambia giocatore 1 / giocatore 2 (emulatori PS1):* | Scambia, in entrambi gli emulatori PS1, quale dei primi due controller è il giocatore 1 e quale il giocatore 2: utile quando i controller sono collegati "al contrario". Conta solo con due o più controller collegati; con uno solo giochi sempre come giocatore 1. RetroArch non ne è toccato. Se l'emulatore PS1 in uso non sa ancora fare lo scambio, AutoBleem te lo dice. |
| *Gioca a tutti i giochi PSX con RA:*, *Aggiorna configurazione RA:*, *Mantieni la config di RetroArch:* | Queste tre righe ci sono solo dove RetroArch è installato. La prima avvia ogni gioco PS1 nel core PS1 di RetroArch (*PlayStation 1*; su PC è SwanStation). La seconda permette ad AutoBleem di scrivere le sue impostazioni nella configurazione di RetroArch quando vi avvia un gioco. La terza conserva, quando RetroArch si chiude, le modifiche fatte nel menu di RetroArch. |
| *Libreria*: *Mostra giochi interni:* | Mostra i giochi incorporati nella console negli elenchi PlayStation (solo PlayStation Classic). |
| *Nomi dei giochi puliti:* | Su ON (il valore predefinito) gli elenchi dei giochi RetroArch mostrano nomi ordinati, senza indicazioni tra parentesi come (USA), (Rev 1) o [!]; su OFF mostrano i nomi dei file. Il nome del file resta comunque nella scheda del gioco. I giochi PS1 non ne sono toccati, perché i loro titoli vengono dal database. |
| *Scarica copertine online:* | Permette alla scansione di scaricare le copertine mancanti dai server di libretro (Raspberry Pi, PC, Windows). |
| *Aggiornamenti*: *Aggiornamenti:* | Sceglie quali aggiornamenti cerca il launcher (sezione 3.12): `release` (la versione collaudata), `testing` (la prossima versione, in collaudo), `nightly` (l'ultima build di sviluppo) oppure `off`. Il valore predefinito segue la versione che hai installato. Non compare su una macchina di sviluppo. |
| *Diagnostica*: *Conserva i log sulla chiavetta:* | Dall'avvio successivo conserva tutti i log sulla chiavetta, non solo dopo un crash: attivalo quando stai dando la caccia a un problema (capitolo 7). |
| *Mostra prestazioni:* | Mostra nell'angolo in basso a sinistra un riquadro con i fotogrammi al secondo, il carico della CPU, i thread e la memoria; durante il gioco anche l'emulatore mostra i suoi FPS e la CPU. |

**Cambiare la modalità dello schermo.** Quando esci dalle opzioni dopo aver scelto una nuova modalità in *Schermo:*,
AutoBleem passa a quella modalità e chiede *Mantenere questa modalità schermo?*. Se l'immagine va bene, conferma. Se il
televisore non mostra niente, aspetta: senza conferma, allo scadere di un conto alla rovescia AutoBleem torna alla
modalità precedente.

**I temi su uno schermo 4:3.** In modalità *CRT 4:3* l'elenco dei temi mostra solo quelli con un layout 4:3. Se il tema
che usi non ce l'ha, dopo che hai confermato la modalità (e a ogni avvio in quella modalità) al suo posto subentra il
tema predefinito, e un avviso te lo comunica: *Tema cambiato con quello predefinito (CRT 4:3)*.

![Le opzioni, divise in gruppi](../images/en/options.jpg)

![Il gruppo Interfaccia: Margine CRT e Altezza dell'immagine](../images/en/options-display.jpg)

![L'avviso dopo il passaggio a CRT 4:3 con un tema senza layout 4:3](../images/en/crt43-theme-notice.jpg)

### 3.7 Le impostazioni di un gioco

Ogni gioco può avere impostazioni tutte sue. La maggior parte gira benissimo così com'è, ma ogni tanto un gioco ha
bisogno di una mano - un'immagine più nitida o più morbida, un fotogramma saltato per restare fluido, un'altra memory
card - oppure vuoi segnarlo come preferito. L'editor del gioco è il posto dove cambiare queste cose per quel solo
gioco, senza toccare gli altri.

Con un gioco selezionato premi **Giù** per aprire la riga di icone sottostante. Ha quattro icone: *IMPOSTAZIONI* (le
opzioni della sezione 3.6), *Gioco* (le impostazioni di questo gioco), *MEMORY CARD* (la sua memory card) e *RIPRENDI*
(i suoi salvataggi di stato). Spostati su una e premi Cross per aprirla.

**L'editor del gioco** (l'icona *Gioco*) mostra a destra la scheda del gioco - titolo, editore, anno, numero di
giocatori, cartella e memory card - e a sinistra le sue impostazioni. Su e Giù passano da un'impostazione all'altra,
Sinistra e Destra la cambiano, come nelle opzioni; tenendo premuto un pulsante il movimento si ripete. Quando hai
finito, Circle salva le modifiche e ti riporta indietro. Un gioco che nei suoi dati non ha un titolo viene mostrato
con il nome della sua cartella.

Le impostazioni sono divise in quattro gruppi:

- **Gioco** riguarda il modo in cui AutoBleem tratta il gioco. *Preferiti:* lo mette nel gruppo *Giochi preferiti*
  della scelta del set. *Blocca dati:* dice alla scansione di lasciare titolo, numero di serie ed elenco dei dischi
  esattamente come li hai impostati, così una scansione successiva non sovrascrive le tue modifiche. *Ripresa:*
  decide cosa succede quando avvii un gioco che ha punti di ripristino: *Chiedi* mostra la scelta dello slot, *Ultimo
  slot* riprende subito dallo slot più recente e *Mai* fa sempre partire il gioco dall'inizio. Dove RetroArch è
  installato ci sono altre due righe. *Gioco Lightgun:* è per i giochi con pistola ottica: il gioco entra nel gruppo
  *Giochi con pistola* e gira sempre in RetroArch, perché è il core PS1 di RetroArch a gestire il GunCon (attivarla
  attiva anche la riga successiva). *Gioca con RA:* fa girare questo solo gioco in RetroArch invece che
  nell'emulatore PS1.
- **Schermo** riguarda l'aspetto dell'immagine. *Risoluzione:* disegna il gioco a 1x o a 2x (con la GPU integrata), e
  *Rimuovi le giunture:*, che funziona solo a 2x, nasconde le linee sottili che a quella dimensione possono comparire
  tra le parti dell'immagine. *Dithering:* (*Disattivato*, *Attivato*, *Sempre*) controlla la trama fine di puntini
  che la PlayStation usa per sfumare i colori, e *Smussatura:* sceglie uno degli scaler di smussatura
  dell'emulatore. *Filtro:* decide come l'immagine viene adattata allo schermo: *Più vicino* mostra pixel puri,
  *Lineare* li ammorbidisce, *Nitido* e *Nitido (semplice)* mantengono i pixel netti senza sfarfallio, e c'è anche
  *Quilez*. I filtri CRT, *CRT (fast)*, *CRT (raster)* e *CRT-Pi*, imitano un vecchio televisore e disegnano le loro
  scanline, quindi le righe delle scanline diventano grigie quando ne è scelto uno. Altrimenti *Scanline:* aggiunge le
  righe scure di un vecchio televisore, e *Luminosità scanline:* ne regola l'intensità. *Risoluzione*, *Rimuovi le
  giunture*, *Dithering*, *Smussatura* e i filtri diversi da *Lineare* e *Più vicino* sono per `pcsx-abnxt`; il
  `pcsx-ab` classico e RetroArch trattano qualsiasi altro filtro come *Più vicino*.
- **Rendering** contiene il *Plugin:* della GPU e *Frameskip:* (*Auto*, *Disattivato*, o da 1 a 3 fotogrammi). Saltare
  fotogrammi aiuta un gioco troppo lento a mantenere la sua velocità, a prezzo di un'immagine meno fluida.
- **Emulatore** contiene *SpeedHack:*, la *Frequenza:* della CPU, *Interpolazione Spu:* (come viene smussato l'audio),
  *Logo di avvio:* e, con `pcsx-abnxt`, *Patch Sony:*. Disattiva *Logo di avvio:* per saltare la schermata del BIOS:
  ti serve per un disco homebrew il cui logo personalizzato gli impedisce di partire.

Le proporzioni dell'immagine e la risoluzione dello schermo non si impostano gioco per gioco ma per tutti insieme,
nelle opzioni (*Scala schermo emulatore:* e *Schermo:*).

**Gli altri pulsanti dell'editor.** Triangle rinomina il gioco con la tastiera a schermo. Square dà al gioco un'altra
memory card (*Cambia memory card*). Finché il gioco usa ancora la sua card personale, Start la trasforma in un nuovo
set condiviso, così possono usarla anche altri giochi (*Condividi memory card*, sezione 3.8). Questi due non sono
disponibili per i giochi interni della console. Qui, come nelle schermate delle opzioni di gioco e dei core di
RetroArch, tenere premuto Sinistra / Destra o Su / Giù ripete il movimento.

Ogni gioco tiene le sue impostazioni in un proprio file `pcsx.cfg`. Tutti i giochi sulla chiavetta ce l'hanno,
perché lo crea la scansione. Un disco originale in un lettore USB (sezione 3.9a), invece, riceve la sua cartella
con il `pcsx.cfg` solo la prima volta che lo avvii; fino ad allora una modifica fatta nell'editor non si può
conservare, e l'editor ti avverte: *Non salvato: questo gioco non ha pcsx.cfg*. Avvia quindi il disco una volta:
da lì in poi le sue impostazioni restano come per qualsiasi altro gioco. Un disco che appartiene a un gioco già
presente nella tua collezione usa fin dall'inizio la cartella e le impostazioni di quel gioco.

Per un **disco nell'unità** (sezione 3.9a) alcune impostazioni non hanno senso, quindi l'editor mette quelle righe in
grigio, e quando ti sposti su una di esse la riga in fondo dice *Non disponibile per un disco nell'unità*.

![L'editor del gioco per un disco nell'unità](../images/en/game-editor-disc.jpg)

**Impostazioni salvate nell'emulatore.** Puoi anche mettere a punto un gioco mentre ci giochi: il menu dell'emulatore
ha *Salva le impostazioni per questo gioco* (sezione 3.9). Quando un gioco ha impostazioni salvate lì, sono quelle a valere.
L'editor mostra allora le righe di Schermo, Rendering ed Emulatore in grigio, con i valori salvati, sotto il titolo
*Salvate nell'emulatore*: puoi leggerle ma non cambiarle. Se preferisci tornare alle impostazioni dell'editor,
scegli *Sblocca le impostazioni* e conferma: le impostazioni salvate dall'emulatore vengono eliminate e le righe
tornano modificabili. Entrambi gli emulatori, `pcsx-ab` e `pcsx-abnxt`, leggono e scrivono le stesse impostazioni
salvate, quindi non importa quale dei due le abbia salvate.

![L'editor del gioco](../images/en/game-editor.jpg)

### 3.8 Memory card e salvataggi di stato

Su una PlayStation vera condividi una o due memory card tra tutti i giochi, e prima o poi lo spazio finisce. In
AutoBleem ogni gioco PS1 ha di serie una memory card tutta sua, così non devi mai preoccuparti dello spazio né
ricordarti su quale card sta un salvataggio. La card è conservata insieme ai salvataggi di stato del gioco, in
`Games/!SaveStates/<cartella del gioco>/`.

**Set di memory card condivise.** A volte i giochi devono vedere i salvataggi l'uno dell'altro: un seguito che legge
il salvataggio del primo capitolo, per esempio, o i dischi di una serie che vuoi tenere su una sola card. Per questo
crei un set condiviso: una card unica usata da più giochi. I set sono conservati in `Games/!MemCards/` e li gestisci
con *Memory card* nel menu di sistema. Square crea un nuovo set (ne digiti il nome con la tastiera a schermo), Cross
rinomina quello selezionato e Triangle lo elimina, dopo averti chiesto conferma. Per assegnare un set a un gioco usa
*Cambia memory card* nel suo editor (sezione 3.7), oppure la sua icona *MEMORY CARD*.

**L'editor delle memory card** si apre dall'icona *MEMORY CARD* di un gioco. Mostra affiancate la card del gioco e una
seconda card, con l'icona e il titolo di ogni salvataggio, come la schermata delle memory card della console
originale. Square copia il salvataggio selezionato sull'altra card, Triangle lo elimina e Select deframmenta una card,
raccogliendone i blocchi liberi perché ci stia di nuovo un salvataggio grande. Start ti fa scegliere quale set
mostrare a destra, e Cross ricarica entrambe le card dalla chiavetta. Una card su cui il gioco non ha ancora scritto -
un gioco in cui non hai mai salvato - è vuota e accanto al nome riporta *ancora nessuna card*. Se hai fatto delle
modifiche, AutoBleem chiede *Vuoi salvare i dati delle memory card?* prima di uscire dall'editor, ricaricare le card o
mostrare un altro set.

![L'editor delle memory card](../images/en/memory-card-editor.jpg)

**Punti di ripristino.** Molti giochi PS1 ti fanno salvare solo in certi punti, e non sempre ci arrivi prima di dover
smettere. Ci pensano i punti di ripristino: quando lasci un gioco PS1 con il tasto Reset della console (o dal menu
dell'emulatore su un Pi o un PC), AutoBleem conserva un salvataggio di stato del punto esatto in cui eri. Mentre lo
scrive, uscendo dal gioco, l'emulatore mostra *Please wait...*. La volta successiva riprendi proprio da quel momento.

Li trovi sotto l'icona *RIPRENDI* del gioco. Un gioco con un punto di ripristino ne mostra una piccola immagine
sull'icona; un gioco che non ne ha ha l'icona in grigio. La scelta dello slot ha quattro slot, mostrati come schede
incorniciate, ognuna con un'immagine del momento, il numero dello slot e la data. Il più recente è segnato con
**RECENTE**, e uno slot mai usato dice *Nessun punto di ripristino*. Cross riprende il gioco dallo slot selezionato,
Triangle lo elimina. Se la scelta compaia o meno all'avvio del gioco lo decide l'impostazione *Ripresa:* del gioco
(sezione 3.7).

Anche i giochi PS1 che giochi in RetroArch hanno i loro slot di ripristino. Ogni slot porta un badge - il logo di
AutoBleem 2 o quello di RetroArch - così vedi quale emulatore l'ha scritto.

![La scelta dello slot di ripristino](../images/en/resume-picker.jpg)

### 3.9 Avviare i giochi, RetroArch e le app

Avviare un gioco è la cosa che farai più spesso, quindi basta un pulsante: seleziona il gioco sullo scaffale e premi
**Cross**. Un gioco PS1 si apre a schermo intero nell'emulatore PS1 scelto nelle opzioni (sezione 3.6) e va avanti
finché non esci. Se preferisci giocare un titolo PS1 in RetroArch - perché lì gira meglio, o perché ti piacciono le
opzioni di RetroArch - premi invece **Square**.

**Uscire da un gioco.** Sulla PlayStation Classic i tasti della console fanno quello che ti aspetti. **Reset**, sul
davanti, ti riporta al launcher e conserva un punto di ripristino di dove eri, così puoi continuare più tardi
(sezione 3.8); funziona anche con il menu di gioco aperto. **Power** spegne la console. Un Raspberry Pi o un PC non
hanno questi tasti, quindi lì esci dal menu di gioco dell'emulatore, descritto più avanti.

C'è poi un modo per uscire che funziona allo stesso modo su ogni controller - quello della console, uno USB o uno
Bluetooth: **tieni premuti Start + Select, oppure Home, per 2 secondi** e sei di nuovo in AutoBleem. Una pressione
breve degli stessi pulsanti apre invece il menu dell'emulatore. Il launcher ti ricorda entrambe le cose nei suoi
suggerimenti (*Tieni premuto Select+Start o Home per 2 secondi: torna ad AutoBleem* e *Pressione breve di Select+Start o
Home: il menu dell'emulatore*). Un'app non ha un menu dell'emulatore, quindi lì conta solo la pressione lunga. Sulla
console, Reset chiude sempre anche un'app.

**Il menu di gioco.** Con `pcsx-abnxt` l'emulatore ha un suo menu per ciò che ti serve mentre giochi: salvare,
cambiare disco, regolare l'immagine, scegliere i controller. Premi il pulsante del menu - Home su un controller che ce
l'ha, **Select + Start** su uno che non ce l'ha, o **Esc** sulla tastiera - e il gioco si mette in pausa dietro il
menu, con l'ultima immagine sullo sfondo. Tenere premuto il pulsante del menu per 2 secondi equivale a Reset: esci dal
gioco. Il menu ha tre schede, e L1 e R1 passano dall'una all'altra. Si ricorda dov'eri, così la volta dopo si riapre
sulla stessa scheda e sulla stessa riga.

- La scheda **Gioco** riguarda il gioco stesso. *Riprendi il gioco* chiude il menu e ti lascia continuare. Sotto
  *Salvataggi*, *Salvataggio rapido* fissa il momento in cui sei e *Caricamento rapido* ti ci riporta. *Carica il
  salvataggio automatico* ti riporta a com'era il gioco fino a 30 secondi prima - l'emulatore tiene questa copia in
  memoria mentre giochi, e ti salva da un errore irrimediabile. Sotto *Disco CD*, *Cambia disco* serve per un
  gioco su più dischi quando chiede il successivo, e *Riavvia il gioco* lo fa ricominciare da capo. *Salva le
  impostazioni per questo gioco* conserva le impostazioni che hai scelto per questo solo gioco (sezione 3.7). *Menu
  PCSX* apre le pagine di PCSX-ReARMed, con le sue opzioni, i trucchi e le informazioni, ed *Esci* ti riporta ad
  AutoBleem.
- La scheda **Immagine** ti fa cambiare l'aspetto del gioco mentre lo guardi: *Schermo*, *Risoluzione* (1x o 2x),
  *Rimuovi le giunture*, *Dithering*, *Scalatura*, *Alone dello schermo*, *Smussatura*, *Filtro*, *Maschera CRT*,
  *Scanline* e *Luminosità delle scanline*. Sono le stesse impostazioni dell'editor del gioco (sezione 3.7), e ogni
  riga ha sulla destra una riga di aiuto che spiega a cosa serve. *Schermo* è la risoluzione dello schermo; sulla
  console la scegli nelle opzioni, e qui viene solo mostrata. *Alone dello schermo* pensa alle bande scure che
  restano ai lati di un'immagine 4:3 su un televisore largo: le riempie con i bordi stessi dell'immagine,
  specchiati e scuriti, così il gioco sembra allargarsi dentro di esse invece di stare chiuso tra due barre nere.
  *Maschera CRT* stende sull'immagine il disegno dei fosfori di un vecchio tubo catodico - *Apertura* dà le sottili
  strisce di un Trinitron, *A fessura* e *Delta* i puntini di altri tubi; c'è solo con il filtro CRT (raster). Il
  filtro CRT-Pi è troppo pesante per la console a 1080p. Una riga che non si applica è in grigio, e la sua riga di
  aiuto ti dice perché.
- La scheda **Controller** decide cosa è collegato alle due porte della PlayStation, *Controller 1* e *Controller 2*:
  un controller standard (digitale), un controller analogico (DualShock), una pistola o niente. Alcuni giochi
  funzionano solo con un certo tipo di controller. La modifica ha effetto quando torni al gioco.

Il menu ha lo stesso stile ab2.0.0 del launcher, così non sembra un altro programma, e mostra le batterie dei
controller e l'immagine del tuo ultimo salvataggio rapido.

**Giochi RetroArch.** Un gioco di un altro sistema parte in RetroArch, con il core che il launcher ha scelto per quel
sistema. Quando hai finito, *Close Content* o *Quit RetroArch* nel menu di RetroArch ti riportano al launcher. Se vuoi
cambiare il core che fa girare un sistema, apri *Core di RetroArch* nel menu rapido (sezione 3.4); l'elenco si apre con
il core *PlayStation 1* in cima. E se vuoi il menu di RetroArch vero e proprio (l'XMB), per le sue impostazioni e i
suoi elenchi di contenuti, scegli *RetroArch* nel menu di sistema: RetroArch si apre senza nulla caricato.

![La finestra dei core di RetroArch, con il core PlayStation 1 in cima](../images/en/retroarch-cores.jpg)

**App.** Le app sono programmi più che giochi: gli strumenti della console e, sulla console, le applicazioni extra che
arrivano con il pacchetto di RetroArch - Doom, Quake, Amiga e altre. Le trovi nel set App. Prima che un'app parta,
AutoBleem ne mostra il leggimi, così sai cos'è e come si controlla. Cross la avvia, Circle ti riporta allo scaffale.

![Il leggimi di un'app, mostrato prima dell'avvio](../images/en/app-start.jpg)

**Le impostazioni di un'app.** Molte app sono state scritte per un controller ben preciso, quindi puoi cambiare il
modo in cui vedono il tuo. Seleziona l'app, apri la riga di icone e scegli *Gioco*: si aprono le *Impostazioni del
gioco* dell'app (*Change how this program is started*). *Modalità controller:* decide quale controller l'app crede di
avere. *Automatica* usa quello che l'app stessa chiede; *Controller PSC* e *Controller Xbox 360* presentano il tuo
controller come quello della console o come un controller Xbox 360, e *Controller PSC (sistema)* e *Controller Xbox
360 (sistema)* fanno lo stesso passando dal sistema. Prova un'altra modalità quando un'app non risponde come dovrebbe
al tuo controller. *Croce direzionale come levetta:* fa muovere la levetta analogica con la croce direzionale, per
un'app che ascolta solo la levetta, e *Levetta come croce direzionale:* fa il contrario.

Alcune app ti fanno una domanda al primo avvio. Una vuole sapere *Quali comandi ha il tuo controller?*, per impostare
i suoi comandi: rispondi *Una croce direzionale* per un controller che ha solo la croce, oppure *Stick analogici*.
Un'app che fa girare Windows chiede *Cosa vuoi fare?* e ti propone di avviare Windows, installarlo, avviare il DOS o
disinstallare Windows. Quando un'app ti fa assegnare un tasto, ti chiede *Premi uno dei pulsanti.*

![Le impostazioni di gioco di un'app](../images/en/app-game-settings.jpg)

Un programma Windows eseguito dal runner PE (un'app PE, sezione 3.3) parla con te attraverso le schermate di
AutoBleem: un messaggio che vuole mostrarti compare come *Messaggio*, una domanda con più scelte come *Scegli
un'opzione*, ognuno con il nome dell'app come titolo.

![Una domanda di un'app PE, mostrata come schermata di AutoBleem](../images/en/pe-dialog.jpg)

### 3.9a Un disco in un'unità USB

Puoi collegare un normale lettore CD/DVD USB alla console, a un Raspberry Pi o a un PC avviato dalla chiavetta di
AutoBleem e giocare direttamente da un disco PlayStation originale, senza copiare niente. Il disco che inserisci
compare nel launcher come un gioco in più. Su Windows non funziona.

**Copiare un disco sulla chiavetta.** Se vuoi avere il gioco sempre a portata di mano, senza il disco, premi Square
(*Copia disco*). AutoBleem ti chiede prima se copiare il gioco e quanto spazio occuperà, poi lo salva nella cartella
`Games` come un unico file CHD (un gioco su più dischi riceve anche un file `.m3u`, così il cambio disco funziona nel
gioco). Durante la copia vedi la velocità e il tempo rimanente, e *Interrompi* la ferma. Finita la copia, il gioco è
sullo scaffale come tutti gli altri. AutoBleem non copia un gioco che è già in `Games`, né uno per cui manca lo
spazio: in quel caso ti dice quanto spazio gli serve. Si può copiare anche un disco graffiato: le parti illeggibili
vengono riempite di zeri, e AutoBleem ti dice quante erano. Una copia del genere può funzionare come no.

Square propone la copia per qualsiasi disco di gioco PlayStation nella vista del disco, anche per uno che i database
delle copertine non conoscono. Un gioco che i database conoscono viene copiato con il suo titolo; per un gioco su più
dischi copia i dischi uno dopo l'altro, e il `.m3u` li elenca in ordine, a partire dal disco 1. Un disco che i
database non conoscono prende invece il nome dal numero di serie, viene copiato come disco singolo e sullo scaffale
non ha copertina. La finestra di copia, *Copia del disco in corso*, resta a schermo finché la copia non è finita o
interrotta - nel frattempo il launcher aspetta - e mostra la velocità come multiplo di quella di un normale lettore
CD. Se la copia non riesce, AutoBleem ti dice perché.

![La copia di un disco](../images/en/disc-copy.jpg)

**Giocare dal disco.** Quando inserisci un disco, la **vista del disco** si apre da sola non appena il disco è stato
letto. Mostra la copertina del disco - dai database delle copertine, o scaricata online - con il numero di serie e il
titolo, e Cross avvia il gioco. Un gioco PS1 giocato dal disco tiene i suoi punti di ripristino e i suoi salvataggi in
una cartella tutta sua, così puoi smettere e riprendere più tardi proprio come con un gioco sulla chiavetta. Dopo la
partita, o dopo essere passato dalle opzioni o dalle impostazioni di un'estensione, torni alla vista del disco. Se la
lasci con Circle per sfogliare gli altri giochi, il disco resta nell'unità e Circle sullo scaffale fa tornare la vista;
su uno scaffale vuoto la apre anche R1 (*Disco*). Su uno scaffale con dei giochi, R1 continua a fare il suo solito
lavoro di salto tra le iniziali. Quando estrai il disco, la vista del disco si chiude.

![La vista del disco](../images/en/disc-view.jpg)

**Il chip dell'unità**, in alto sullo schermo, ti dice cosa sta facendo l'unità, così sai se devi aspettare. Senza
unità collegata non vedi nulla. Un'unità senza disco mostra un'icona del disco attenuata. Mentre un disco viene letto,
l'icona lampeggia e dice *Lettura del disco...*, e quando è pronto l'icona si accende con il titolo del disco. Se
inserisci un disco che non è né un gioco PlayStation né un CD audio, il chip dice *Questo non è un disco PlayStation*,
e se l'unità al momento non riesce a leggere il disco, dice *Il disco non può essere letto ora*.

![Il chip dell'unità](../images/en/disc-chip.jpg)

**CD audio.** L'unità riproduce anche i CD musicali. Un CD audio apre il **lettore CD** invece della vista del disco.
Il lettore mostra il disco come *CD audio*, con l'elenco delle tracce e la durata totale, e la riga sottostante indica
la traccia selezionata e se ripetizione e riproduzione casuale sono attive. Un disco che il lettore non può
riprodurre viene segnato con *Questo disco non può essere riprodotto*. Questi sono i suoi pulsanti:

| Pulsante | Nel lettore CD |
|---|---|
| Cross | Riproduce la traccia selezionata. |
| Start | Mette in pausa la musica, e la fa ripartire. |
| Square | Ferma la musica. |
| L1 / R1 | Vanno alla traccia precedente o successiva. |
| L2 / R2 | Riavvolgono o mandano avanti la traccia, cinque secondi alla volta. |
| Triangle | Cambia cosa viene ripetuto: niente, tutto il disco o la traccia attuale. |
| Select | Attiva o disattiva la riproduzione casuale, per ascoltare le tracce in ordine sparso. |
| Circle | Esce dal lettore CD. |

![Il lettore CD](../images/en/cd-player.jpg)

**Dischi LibCrypt.** Alcuni giochi PlayStation, per lo più europei, hanno una protezione dalla copia chiamata LibCrypt.
Per farli girare, l'emulatore ha bisogno di un piccolo file `.sbi` con i dati della protezione. AutoBleem lo scarica da
solo dal sito prima di avviare un disco del genere e quando lo copi, e il file viene copiato insieme al gioco. Per
farlo gli serve una rete: su un Raspberry Pi o un PC quella che hanno già, sulla console il Wi-Fi che hai configurato
in PSC-Bios.

Per un disco nell'unità alcune impostazioni del gioco non hanno senso, quindi il suo editor mette quelle righe in
grigio (sezione 3.7).

### 3.10 Aggiungere giochi

AutoBleem trova i tuoi giochi da solo, purché siano nel posto giusto. Questa sezione ti dice dove va ogni tipo di
gioco, perché ogni scansione li metta sullo scaffale con il loro nome e la loro copertina.

**I giochi PS1** vanno nella cartella `Games`, **una cartella per gioco**, con il nome del gioco. Puoi anche
raggrupparli in cartelle tue, e ognuna di queste diventa un gruppo nella scelta del set (sezione 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                una cartella di giochi: un gruppo a sé nella scelta del set
    Klonoa/                   Klonoa.pbp
```

AutoBleem legge i formati di immagine disco più comuni: `.cue` con il suo `.bin` (o `.img`), `.pbp`, `.chd` (anche
quelli compressi zstd), `.iso` ed `.ecm`, che la scansione decodifica per te. Funziona anche un gioco zippato: il
processore **Unzip** lo estrae prima che la scansione lo legga (sezione 3.14).

Non devi essere ordinatissimo. Un gioco su più dischi va in un'unica cartella con tutti i suoi dischi, ma se copi
cartelle chiamate `Game (Disc 1)`, `Game (Disc 2)` e così via, la scansione le unisce in un'unica cartella `Game`. Anche
i giochi messi alla rinfusa direttamente in `Games/` vengono sistemati dalla scansione in cartelle proprie.

**Nomi e copertine** arrivano da soli. La scansione legge il numero di serie di ogni disco e prende titolo, editore,
anno, numero di giocatori e regione dal database PlayStation di RetroArch o dai database delle copertine. Se vuoi una
copertina tua, metti un PNG o un JPEG accanto all'immagine del gioco, con lo stesso nome. Altrimenti la copertina
arriva dai database delle copertine o, con RetroArch installato, dalla raccolta di miniature di libretro; su un
Raspberry Pi, un PC o Windows una copertina mancante viene scaricata online (Opzioni → *Scarica copertine online:*). Se
la scansione sbaglia qualcosa, correggilo nell'editor del gioco e attiva *Blocca dati:*, così la scansione successiva
mantiene la tua modifica.

**I giochi di altri sistemi** vanno in `RetroArch/roms/`, **una cartella per sistema, con il nome che gli danno i
database di RetroArch** - per esempio `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo
Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` o `FBNeo - Arcade Games` (oppure
`Arcade`). Le cartelle vengono create per te, e le ROM possono restare zippate. Su un Raspberry Pi, un PC o Windows la
scansione le legge da sola e scrive le playlist di RetroArch. Una chiavetta della console non può farlo da sola, quindi
lì avvii **UpdateRoms** sul PC (capitolo 5).

**Le app** vanno in `Apps/<nome>/`, ognuna con un `app.ini` - il suo nome, la sua icona e cosa avviare - e un `run.sh`.

**I pacchetti.** Alcune app sono motori di gioco: per giocare hanno bisogno dei dati di un gioco che possiedi.
Funzionano così Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, i
giochi DOS e altri ancora. Metti i file del gioco in una cartella `Packages` sulla chiavetta, una cartella per gioco -
per esempio `Packages/Doom/DOOM2.WAD` - e AutoBleem li riconosce grazie a una tabella che porta con sé
(`rc/packages.ini`). In una cartella che riconosce, i file di gioco sparsi sono pacchetti a sé. AutoBleem si limita a
leggere i tuoi file e non li modifica mai. Un pacchetto può arrivare anche dallo Store (sezione 3.13).

Dove il launcher la mostra, la riga *Pacchetti* della scheda App (sezione 3.3) elenca i dati di gioco trovati. Cross
su una voce apre il suo **Package info**: cosa contengono i dati, una descrizione, dove sono i file e da dove vengono
(file tuoi, lo Store, una mod o file inclusi in un'app), se si tratta di shareware o di un gioco libero e quale app
installata lo fa girare. Se nessuna delle app installate può farlo girare, la scheda te lo dice.

Quando avvii un'app motore di gioco, AutoBleem cerca dati di gioco che sappia far girare. Con un solo set di dati il
gioco parte subito. Con più set, un elenco (*Scegli i dati di gioco*) ti chiede quale giocare, partendo da quello che
hai scelto l'ultima volta. Se non ce n'è nessuno, AutoBleem ti dice di quali dati ha bisogno l'app e dove metterli, e
non parte niente.

**I tuoi giochi.** Quando AutoBleem non riconosce dei dati, il loro Package info dice *Non riconosciuto. Se è un gioco,
vedi il manuale: I tuoi giochi.* La tabella conosce solo i giochi per cui è stata fatta. Per un altro gioco, scrivi una
riga in un tuo `packages.ini` nella cartella `Packages`: AutoBleem legge prima il tuo, quindi le tue righe hanno la
meglio.

![La scelta dei pacchetti, dove scegli con quali dati di gioco partire](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Scansionare una parte sola.** Se hai aggiunto giochi a un solo set o a una sola cartella, *Riscansiona i giochi* può
scansionare solo quella parte, più in fretta che scansionare tutto, e la sua bolla sparisce a lavoro finito.

**I temi** vanno in `Themes/<nome>/`, con il loro `theme.json` e le loro immagini - oppure metti lo zip del tema così
com'è in `Themes/`.

### 3.11 Il BIOS PS1

Il BIOS è il programma di avvio della PlayStation, e con quello originale l'emulatore fa girare i giochi nel modo più
fedele. Su una **PlayStation Classic** non devi fare nulla: l'emulatore usa il BIOS della console. Su **Raspberry Pi,
PC e Windows** metti i tuoi file BIOS PS1 in `System/Bios/`: `romw.bin` (lo SCPH-5501/5502 americano/europeo) e
`romJP.bin` (lo SCPH-5500 giapponese, usato per i giochi giapponesi). Gli installer li ricavano dai pacchetti di BIOS
di RetroArch, a meno che i tuoi file non ci siano già: non sostituiscono mai i tuoi. Senza di essi l'emulatore usa il
suo BIOS HLE integrato, un sostituto che molti giochi accettano e alcuni no; quindi, se un gioco non parte, la prima
cosa da controllare è il BIOS mancante.

### 3.12 Aggiornamenti

AutoBleem si tiene aggiornato da solo, così hai nuove funzioni e correzioni senza reinstallare niente. Quando il
launcher si avvia, e poi una volta al giorno, controlla sul sito se c'è una nuova versione sul suo **canale**. Il
canale lo scegli in Opzioni → *Aggiornamenti*: `release`, `testing`, `nightly`, oppure `off` se non vuoi che controlli
affatto. Se non vuoi aspettare il controllo giornaliero, *Aggiornamento software* nel menu di sistema controlla
subito.

Quando c'è una nuova versione, AutoBleem ti chiede cosa fare. *Aggiorna ora* la scarica e la installa, e ci vogliono
alcuni minuti. *Ricordamelo domani* te lo richiede tra un giorno, e *Salta questa versione* non ti chiede più nulla per
questa versione. Qualunque cosa scegli, giochi, salvataggi e impostazioni restano sempre; dopo un aggiornamento il
launcher scansiona di nuovo i giochi. L'etichetta del canale nell'angolo in alto a sinistra (sezione 3.1) ti mostra
quale build hai.

Il modo in cui l'aggiornamento si installa dipende dalla macchina:

- Su un **Raspberry Pi** e sulla **chiavetta PC**, dopo il download riparte l'installer, con la stessa schermata di
  avanzamento del primo avvio, e propone anche un RetroArch più recente. Poi torna il launcher.
- Su **Windows** si apre il setup scaricato, che installa la nuova versione e avvia il nuovo launcher.
- Su una **PlayStation Classic** può aggiornarsi da sola solo una console con il **kernel di AutoBleem** (ABFlashKit,
  sezione 6.2) e una **rete Wi-Fi** configurata in PSC-Bios (sezione 6.1): una console originale non ha rete, quindi
  il launcher non controlla. Dopo *Aggiorna ora* il launcher si chiude e l'immagine di AutoBleem resta a schermo mentre
  la chiavetta viene aggiornata, il che richiede alcuni minuti; poi parte il nuovo launcher. Senza rete,
  *Aggiornamento software* ti risponde *Non connesso*. Qualsiasi chiavetta della console si può aggiornare anche da un
  PC con `AutoBleemInstaller.exe` (sezione 2.1).

### 3.13 Le estensioni e lo Store di AutoBleem

Le **estensioni** aggiungono cose nuove al launcher - schermate e funzioni proprie - senza cambiare AutoBleem. Lo
Store di AutoBleem e PSC-Bios sono estensioni. Un'estensione sta in `Extensions/<nome>/` sulla chiavetta (su un
Raspberry Pi nella sua partizione dei dati, su Windows nella cartella dei dati); per installarne una, estrai lì il suo
zip.

Per vederle, apri il menu di sistema (**L2 + R2**) e scegli *Estensioni*. Quelle del team di AutoBleem sono in cima, le
altre seguono sotto *Estensioni di terze parti*. Cross avvia quella selezionata, e Triangle la disattiva o la riattiva.
PSC-Bios sulla console fa eccezione: è con lei che configuri Wi-Fi, controller e orologio, quindi lì non si può
disattivare. Quando un'estensione non può funzionare, la sua riga ti dice perché: ha bisogno di una rete e non ce n'è,
non è fatta per questo sistema, è stata fatta per un'altra versione di AutoBleem e va aggiornata, oppure non è stato
possibile caricarla. Se un'estensione dovesse mai bloccare il launcher, AutoBleem la disattiva e l'elenco te lo
segnala; puoi riattivarla da qui.

![L'elenco delle estensioni](../images/en/extensions.jpg)

**Lo Store di AutoBleem** è la prima estensione: un posto in cui sfogliare app e giochi e installarli con una sola
pressione, su ogni sistema su cui gira AutoBleem. Una PlayStation Classic ha bisogno per questo del kernel di
AutoBleem, perché è il kernel a portare il Wi-Fi. Aprilo dal menu rapido (*Store*, sezione 3.4). Ha quattro schede, e
L1 e R1 passano dall'una all'altra.

Le schede **Apps** e **Games** elencano ciò che offrono le fonti, ogni elemento con la sua immagine, la versione, la
dimensione e la piccola icona della fonte da cui proviene. La scheda Apps elenca anche le app PE, con licenza e fonte,
e i pacchetti di dati di gioco (sezione 3.10). Ciò che hai già installato porta un badge *Installed*. La barra dei
suggerimenti mostra i pulsanti validi per la riga selezionata:

| Pulsante | Nelle schede Apps e Games |
|---|---|
| Cross | Installa l'elemento - oppure lo aggiorna, riprova dopo un errore, o annulla un download in attesa o in corso. |
| Triangle | Rimuove qualcosa che lo Store ha installato. |
| Square | Aggiorna gli elenchi dalle fonti. |
| L2 / R2 | Saltano all'iniziale precedente o successiva. |
| Select | Mostra una fonte alla volta, quando vuoi vedere cosa offre una sola fonte. |
| Start | Cerca nei titoli. |

Le immagini, una volta caricate, vengono conservate, così la volta dopo gli elenchi compaiono in fretta; un'immagine
che non si è caricata si può riprovare.

La scheda **Downloads** mostra cosa è in download, in attesa, fallito o installato, con una barra di avanzamento che
procede regolare. Non devi stare a guardarla: i download continuano in background, anche quando esci dallo Store, e
mentre sei altrove nel launcher una bolla mostra il download in corso con la velocità e il tempo rimanente (per esempio
`1.4 MB/s · 0:42`). Avviare un gioco o spegnere li mette solo in pausa, e un download interrotto riprende da dove si
era fermato. Se cade la rete, l'elemento dice *Waiting for the network* e, quando la rete torna, riprende da dov'era;
dopo 30 minuti senza rete rinuncia. I download oltre i 2 GB funzionano su ogni piattaforma, comprese le build a 32
bit. Un gioco che installi compare sullo scaffale dopo la scansione successiva, con l'immagine dello Store come
copertina.

La scheda **Sources** mostra da dove vengono gli elenchi, ognuno con la sua icona: il catalogo di AutoBleem, qualsiasi
elenco TSV messo in `System/Extensions/store/sources/` e gli indirizzi che aggiungi tu con *Add a source URL*. Cross su
una fonte che hai aggiunto ti permette di rinominarla, cambiarne l'indirizzo, passarla da `http://` a `https://` e
viceversa, oppure rimuoverla.

![La scheda Apps dello Store](../images/en/store-apps.jpg)

![Il menu di una fonte che hai aggiunto](../images/en/store-source-menu.jpg)

Ciò che offre il catalogo di AutoBleem è elencato anche sul sito dei download, all'indirizzo
`https://autobleem.retromenele.pl/store/`. Una fonte che aggiungi tu è un'altra faccenda: **del contenuto delle fonti
che aggiungi rispondi tu.**

**I tuoi giochi nella tua rete.** Se tieni i giochi PS1 su un altro computer di casa, `abstored`, il server LAN dello
Store, può offrirli allo Store attraverso la rete, così li installi come qualsiasi altro elemento. Gira su qualsiasi
macchina Linux - un Raspberry Pi, un server di casa - e si limita a leggere la cartella, senza mai modificarla. Avvialo
con `abstored <cartella dei giochi>`, poi apri `http://<quella macchina>:8124/` in un browser: la pagina mostra cosa
offre ed eventuali problemi trovati. Nello Store aggiungi `http://<quella macchina>:8124/store.tsv` come fonte. I
programmi pronti per Linux e Windows sono sulla pagina dello Store, nella scheda **LAN server**, e `INSTALL-linux.md`
(`ext_store/server/` nei sorgenti) spiega come configurarlo come servizio. **LAN Share** (sezione 5.2) mette su un
server del genere giochi e dischi da un PC.

### 3.14 Processori di scansione

I processori di scansione preparano i tuoi giochi prima che AutoBleem li legga. Un processore è un piccolo programma
che ogni scansione esegue per primo. Può trasformare un formato che AutoBleem non legge in uno che legge - estraendo un
gioco zippato, per esempio - oppure modificare i dati di un gioco, come applicare una patch di traduzione. I
processori stanno in `System/Processors/<nome>/` sulla chiavetta (su un Raspberry Pi nella sua partizione dei dati, su
Windows nella cartella dei dati); per installarne uno, estrai lì la sua cartella, e la scansione successiva lo esegue.

**Unzip è incluso in AutoBleem.** Estrae i giochi PS1 zippati in `Games/` prima che la scansione li legga, e le ROM
zippate una alla volta; i set arcade restano zippati, perché è così che li leggono i core arcade. Aggiornando AutoBleem
si aggiorna anche Unzip, e se l'avevi disattivato, resta disattivato.

Un processore fa il suo lavoro una volta sola: quando ha trattato un gioco, non ci torna finché il gioco non cambia.
Mentre un processore lavora, la bolla in alto a destra mostra cosa sta facendo, e un avviso o un errore compare sulla
riga sottostante; i dettagli sono in `processors.log` nella cartella dei log. Avviare un gioco o RetroArch ferma un
processore che modifica file, così il gioco ha la macchina tutta per sé, e la scansione successiva completa il lavoro.

Per gestirli, apri il menu di sistema (**L2 + R2**) e scegli *Processori di scansione*. Li vedi nell'ordine in cui
vengono eseguiti, con una scheda per i giochi PS1 e una per le ROM; L1 e R1 passano da una scheda all'altra. L'ordine
conta: un processore che estrae deve venire prima di uno che modifica ciò che è stato estratto.

| Pulsante | In Processori di scansione |
|---|---|
| Square | Prende il processore selezionato, così Su e Giù lo spostano nella nuova posizione; Square lo rimette giù. |
| Cross | Disattiva il processore, o lo riattiva. |
| Triangle | Fa riesaminare al processore tutti i giochi alla prossima scansione, anche quelli che ha già trattato. |
| Circle | Torna indietro, e avvia una scansione se hai cambiato qualcosa. |

Un processore fatto per un'altra macchina resta nell'elenco, in grigio: vedi che c'è, ma anche che qui non gira.

![Processori di scansione](../images/en/processors.jpg)

Se vuoi scrivere un processore tuo, la pagina di Unzip, `https://github.com/autobleem2/proc_unzip`, spiega tutto ciò
che un processore deve fare, e `tools/proc_check.py` nei sorgenti di AutoBleem controlla il tuo prima che tu lo
condivida.

<!-- pagebreak -->

## 4. Schermate

### 4.1 Gestore del gioco

Il gestore del gioco è il posto in cui fai ordine nella tua libreria PS1. Usalo quando vuoi togliere un gioco a cui
non giochi più, aprire le impostazioni di un gioco senza doverlo prima trovare sullo scaffale, o far scaricare di
nuovo ad AutoBleem tutte le copertine. Aprilo dal menu di sistema (L2 + R2, *Gestore del gioco*). Durante una
scansione è in grigio e aspetta che la scansione sia finita.

La schermata si intitola *Gestore del gioco - Scegli un gioco*. A sinistra vedi tutti i tuoi giochi PS1 come elenco di
titoli in ordine alfabetico; a destra la copertina del gioco selezionato con editore, anno, numero di serie e la
cartella in cui si trova. In alto a destra è indicato lo spazio libero rimasto sull'unità, così vedi quanto spazio ti
restituisce un'eliminazione. Su e Giù scorrono l'elenco, L2 / R2 girano pagina e L1 / R1 saltano al primo o all'ultimo
gioco.

- **Cross** apre il gioco selezionato nell'editor del gioco - lo stesso dell'icona Gioco sullo scaffale (sezione 3.7).
  Quando lo chiudi, torni sullo stesso gioco nell'elenco.
- **Square elimina il gioco.** AutoBleem prima chiede conferma, poi cancella l'intera cartella del gioco. Se i
  salvataggi di stato e la memory card del gioco non sono usati da nessun altro gioco, ti fa una seconda domanda: se
  eliminare anche quelli. Rispondi di no se un giorno potresti rivolere il gioco con i tuoi salvataggi.
- **Triangle elimina tutte le immagini di copertina** (PNG o JPEG) che stanno accanto ai tuoi giochi, dopo una
  domanda. È utile quando hai accumulato copertine che non ti piacciono: la scansione successiva riprende le copertine
  dai database.

In fondo all'elenco, dopo i giochi, potresti vedere delle cartelle segnate *Non aggiunto*. Sono cartelle in `Games`
che la scansione ha esaminato ma non è riuscita a trasformare in un gioco. Selezionane una e la parte destra ti dice
dove si trova e perché non è stata aggiunta - per esempio un file cue mancante (capitolo 7). Square elimina una
cartella del genere dopo una domanda. Quando esci con Circle dopo aver cambiato qualcosa, AutoBleem scansiona di nuovo
i giochi.

![Il gestore del gioco: l'elenco dei giochi a sinistra, la copertina e la scheda del gioco selezionato a destra](../images/en/game-manager.jpg)

### 4.2 Informazioni hardware

Informazioni hardware è la pagina da guardare quando vuoi sapere cos'è la tua macchina e cosa vede: quanto spazio
resta sulla chiavetta, che indirizzo di rete ha, quali driver video e audio usa, quali controller sono collegati. È la
stessa pagina su ogni piattaforma, console compresa. Aprila dal menu di sistema (L2 + R2, *Informazioni hardware*);
Circle ti riporta al menu di sistema.

La pagina mostra il sistema, l'hardware, la memoria di archiviazione con lo spazio libero, gli indirizzi di rete, i
driver video e audio e i controller collegati. Rilegge tutto ogni secondo, quindi puoi lasciarla aperta mentre
colleghi un controller o un cavo e vedere comparire il cambiamento. Si limita a mostrare: per configurare la rete o un
controller usa *Rete e controller* (PSC-Bios, capitolo 6).

La parte dei controller risponde alla domanda "quale controller è quale giocatore?". I primi due controller compaiono
come *Giocatore 1* e *Giocatore 2*, le porte che assegna loro l'emulatore PS1. Ogni controller in più viene indicato
come *non utilizzato dall'emulatore PS1*. RetroArch assegna le porte secondo le sue impostazioni, quindi in un gioco
RetroArch l'ordine può essere diverso. Non devi aprire questa pagina ogni volta: quando colleghi o scolleghi un
controller, il launcher mostra per un attimo quale controller è ora il giocatore 1 e quale il giocatore 2.

![Informazioni hardware: i dati della macchina e i controller collegati](../images/en/hardware-info.jpg)

### 4.3 La guida dei pulsanti

Se non ricordi cosa fa un pulsante in un certo punto, premi **Triangle** sullo scaffale. La guida dei pulsanti mostra
in una sola pagina tutti i pulsanti di tutte le schermate, così puoi controllare senza uscire dal launcher. Se è
collegata una tastiera USB, o è stata usata, una colonna *Tastiera* mostra accanto a ogni pulsante del controller il
tasto corrispondente.

La guida ti ricorda anche l'unica cosa che vale la pena ricordare per ogni gioco: come uscirne. Tieni premuti Select +
Start, oppure Home, per 2 secondi per tornare ad AutoBleem; una pressione breve apre invece il menu dell'emulatore.

![La guida dei pulsanti: i pulsanti di ogni schermata, con accanto i tasti della tastiera](../images/en/button-guide.jpg)

### 4.4 La tastiera a schermo

Ogni volta che AutoBleem ha bisogno che tu scriva qualcosa - il nome di un set di memory card, il titolo di un gioco,
una password Wi-Fi, l'indirizzo di una fonte dello Store - compare la stessa tastiera a schermo, così puoi scrivere
usando solo il controller. È disposta come quella di un telefono. Oltre alle lettere ha una pagina di simboli, con
`/ \ : ? & = % @ #` e tutto il resto che serve per un indirizzo o una password, e due pagine di lettere accentate. La
riga in basso contiene Maiuscolo, il tasto che cambia pagina, Spazio, Cancella e Conferma.

Muoviti tra i tasti con le direzioni e premi **Cross** per scrivere quello sotto il cursore. **Triangle** cancella una
lettera e **Square** inserisce uno spazio. **L1** è il Maiuscolo; premilo due volte per il blocco maiuscole. **R1**
passa alla pagina di tasti successiva, e **L2 / R2** spostano il cursore all'interno del testo. **Start** conferma ciò
che hai scritto e **Circle** annulla. Se è collegata una tastiera USB, puoi scrivere su quella in qualsiasi momento:
Invio conferma ed Esc annulla.

![La tastiera a schermo](../images/en/keyboard.jpg)

### 4.5 Gamepad virtuale

Le app - i programmi del set App, come Doom o Quake - non leggono direttamente il tuo controller. Un piccolo programma
di supporto, il demone del gamepad virtuale, legge i controller veri e passa a ogni app un controller che quell'app
capisce. Questa pagina ti mostra quali controller vede quel programma e come li legge. Guardala quando un'app non
risponde al tuo controller o quando i suoi pulsanti sono scambiati. Aprila dal menu di sistema (L2 + R2, *Gamepad
virtuale*); Circle ti riporta al menu di sistema.

Sotto *Gamepad visti dal demone* ogni controller è elencato con un numero e il suo nome. Accanto leggi tre cose: se il
demone è riuscito ad aprire il controller (*collegato*) oppure no (*non leggibile*); il driver da cui è arrivato; e da
dove viene la disposizione dei pulsanti - *dal database dei controller* vuol dire che il controller è conosciuto e i
suoi pulsanti sono dove devono essere, *indovinato dal demone* vuol dire che non è conosciuto e il demone ha tirato a
indovinare al meglio. Se in un'app i pulsanti sembrano sbagliati, la causa probabile è una disposizione indovinata.

Il demone gira solo mentre gira un'app, quindi la pagina lo interroga una volta all'apertura. Se colleghi un
controller con la pagina aperta, premi **Cross** (*Cerca di nuovo*) per chiedere di nuovo. Su Windows questo programma
non esiste, e la pagina dice *Non presente in questa versione*.

![Gamepad virtuale: i controller che vede il programma di supporto delle app](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. Sul PC

### 5.1 UpdateRoms - aggiornare una chiavetta della console

Su un Raspberry Pi, un PC o Windows la scansione del launcher ordina da sola i giochi RetroArch in elenchi e ne
scarica le copertine. La PlayStation Classic non può farlo, perché non ha una rete propria. **UpdateRoms** fa questo
lavoro sul tuo PC Windows: usa la rete del PC ma scrive tutto con i percorsi che la console si aspetta, così quando
rimetti la chiavetta la console si avvia e trova tutto al suo posto. Avvialo ogni volta che hai aggiunto o tolto
giochi RetroArch su una chiavetta della console.

1. Copia le tue ROM sulla chiavetta in `RetroArch/roms/<sistema>/` (sezione 3.10). I nomi delle cartelle devono essere
   quelli dei database di RetroArch; l'installer ha già creato quelli più comuni.
2. Avvia **`UpdateRoms\UpdateRoms.exe` dalla chiavetta**: ce l'ha messo l'installer. Capisce da solo su quale
   chiavetta si trova. Mentre lavora vedi una riga che dice cosa sta facendo, una barra di avanzamento e un registro.
   - Se sulla chiavetta non c'è ancora un database di RetroArch, scarica prima il pacchetto dei database di
     RetroArch. Poi identifica con esso ogni ROM, così un gioco che il database conosce riceve il suo nome giusto.
   - Scrive una playlist per sistema in `RetroArch/bin/playlists/`, con i percorsi della console. Tutto ciò che
     RetroArch ha aggiunto per conto suo a quelle playlist viene mantenuto.
   - Per ogni ROM senza copertina ne scarica una dai server di miniature di libretro in `RetroArch/bin/thumbnails/`.
3. Rimuovi la chiavetta in modo sicuro e rimettila nella console. La scheda RetroArch della scelta del set ora elenca
   ogni sistema che ha dei giochi.

Puoi avviarlo tutte le volte che vuoi: una cartella in cui non è cambiato nulla viene saltata, quindi un secondo
passaggio è veloce. Se qualcosa va storto, il registro è `System/Logs/updateroms.log` sulla chiavetta. Anche la scheda
di un Raspberry Pi inserita in un lettore di schede si può aggiornare allo stesso modo, con
`UpdateRoms.exe <unità> --target rpi`, anche se un Pi lo fa da solo quando ha una rete.

### 5.2 LAN Share - i tuoi giochi e dischi sul server della tua rete

Lo Store può installare giochi da un server nella tua rete di casa (sezione 3.13). **LAN Share** è il programma
Windows che riempie quel server dal tuo PC: ci mette i giochi PS1 che hai sul PC, e sa anche leggere un disco PS1
nell'unità CD/DVD del PC e mettere anche quello sul server. Il server è un `abstored` che gira su un Raspberry Pi, un
NAS o un altro PC. Una volta che un gioco è lì, lo Store della console, del Pi o del PC può installarlo da lì.

`LanShare.exe` lo trovi sulla pagina dello Store, nella scheda **LAN server**. Non c'è niente da installare: avvialo e
conserva le sue impostazioni in `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![La finestra di LAN Share: i giochi del server a sinistra, quelli di questo PC a destra](../images/en/lanshare.jpg)

1. **Collegati al server.** Inserisci il suo indirizzo come lo conosce lo Store, `http://<suo indirizzo>:<porta>`, e
   premi **Connect**. A sinistra compaiono i giochi già presenti sul server e gli eventuali problemi trovati dalla sua
   scansione. Per mettere giochi sul server, LAN Share ha bisogno di uno di questi due accessi:
   - **Share** è la cartella dei giochi del server così come è condivisa nella tua rete (Samba), per esempio
     `\\raspberrypi\games`. LAN Share ci copia i giochi e chiede al server di scansionare; il server continua comunque
     a limitarsi a leggere la sua cartella.
   - **Token** è per un server avviato con `--allow-uploads`. Inserisci il suo token: il server lo stampa all'avvio e
     lo conserva in `<state>/upload-token`. LAN Share allora carica via HTTP, e un caricamento interrotto a metà
     riprende da dove si era fermato.
2. **Pubblica i giochi del tuo PC.** Scegli la cartella in cui stanno i giochi (una cartella per gioco), spunta quelli
   che vuoi e premi **Publish the ticked games**. **On the server** ti dice se il server ha già un gioco - confronta il
   numero di serie, o il titolo quando il numero di serie manca - e un gioco che il server ha già non viene mai inviato
   due volte. **Tick those not on the server** spunta per te tutti gli altri.
3. **Pubblica un disco.** Metti un disco PS1 nell'unità del PC e premi **Read a disc and publish it**. LAN Share legge
   tutto il disco in un `.bin` + `.cue`, con il nome del titolo del gioco. Per un gioco LibCrypt scrive anche il file
   `.sbi`, se l'unità sa leggere il subcanale. Se hai indicato i database (vedi sotto), confronta la copia con il dump
   buono conosciuto. Poi pubblica il gioco. Per un gioco su più dischi spunta prima **The game has more than one
   disc**: LAN Share ti chiede ogni disco successivo e li pubblica insieme come un unico gioco.
4. **Togli giochi dal server.** Selezionali e premi **Remove from the server...**. Non si cancella niente: ogni gioco
   viene spostato in una cartella `.removed` accanto ai giochi del server, e riportandolo indietro torna al suo posto.

I **Databases** sono facoltativi. Se indichi a LAN Share la cartella delle copertine di AutoBleem (`coversU/P/J.db`) e
il file `Sony - PlayStation.rdb` di RetroArch, li usa per dare il nome ai giochi e per controllare un disco che ha
letto.

Se preferisci non copiare niente, spunta **Also share the games on this PC with the Store** (di serie è disattivato):
LAN Share offre allora direttamente allo Store la cartella dei giochi del tuo PC. La prima volta Windows ti chiede del
firewall: consenti solo le reti private.

<!-- pagebreak -->

## 6. Gli strumenti per la console (PlayStation Classic)

Con una chiavetta per PlayStation Classic arrivano due strumenti che ti aiutano a configurare la console oltre quello
che sa fare di fabbrica. Entrambi hanno l'aspetto del resto del launcher, con il suo tema e la sua lingua, e li usi
con il controller - nella procedura di mappatura anche con i tasti frontali della console. **PSC-Bios** è
un'estensione inclusa nel pacchetto della console: la apre la voce *Rete e controller* nel menu rapido e nel menu di
sistema, e la trovi anche nell'elenco delle estensioni. **ABFlashKit** è un'app, nel set App.

### 6.1 PSC-Bios

PSC-Bios è il posto in cui colleghi la macchina al mondo: la tua rete Wi-Fi, il fuso orario, i controller Bluetooth e
la disposizione dei pulsanti di un controller che AutoBleem non conosce. È incluso nel pacchetto della console e c'è
anche su un Raspberry Pi e sulla chiavetta PC. Aprilo con *Rete e controller* nel menu di sistema (o nel menu rapido),
oppure dall'elenco delle estensioni. Se l'estensione è installata ma disattivata, la voce *Rete e controller* è in
grigio e dice che *è disattivata - attivala in Estensioni*; premi Cross su di essa e l'elenco delle estensioni si apre
su PSC-Bios, così puoi riattivarla.

La prima schermata ti dà un quadro d'insieme: l'ora e il fuso orario, le schede di rete (Wi-Fi, Ethernet, Bluetooth)
con i loro indirizzi e ogni controller collegato, con l'indicazione se ha una mappatura dei pulsanti. Sulla console le
parti di rete e Bluetooth richiedono il kernel di AutoBleem (sezione 6.2); su un Raspberry Pi o sulla chiavetta PC
usano gli strumenti del sistema. La procedura di mappatura dei controller funziona ovunque.

![PSC-Bios: la schermata principale di Rete e controller](../images/en/pscbios-main.jpg)

Dalla prima schermata, un pulsante ti porta a ciascuna parte:

| Pulsante | Cosa apre |
|---|---|
| Select | **Wi-Fi Network** ti collega al Wi-Fi (attraverso il kernel, oppure NetworkManager su un Pi o un PC): digita il nome della rete o sceglila da una ricerca, inserisci la password, scegli la modalità del driver e premi *Apply / Restart Network*. Qui imposti anche il fuso orario, e una volta connesso vedi l'indirizzo IP della console. |
| Square | **Bluetooth Controllers** cerca controller Bluetooth come il DualShock 4, per abbinarne uno nuovo o rimuoverne uno che non usi più. |
| L1 | **DualShock 3 Pairing** collega il tuo primo DualShock 3, che per questo deve essere collegato via USB, attraverso il plugin sixaxis del kernel. |
| R1 | **Controller Mapping** apre la procedura di mappatura dei controller, descritta qui sotto. |
| Triangle | **About** mostra cos'è PSC-Bios. |
| Circle | **Back** ti fa uscire da PSC-Bios e ti riporta al launcher. |

**Il Wi-Fi e un controller Bluetooth insieme.** Sulla PlayStation Classic il Wi-Fi e il Bluetooth passano per
un'unica radio con un'unica antenna, e quella radio può fare una sola cosa alla volta. Finché un controller
Bluetooth è collegato e lo stai usando, la radio fa a turno - un attimo al controller, un attimo al Wi-Fi - e
così al Wi-Fi resta meno tempo e diventa più lento. Te ne accorgi soprattutto durante un download grande dallo
*Store* (sezione 3.13) o un aggiornamento (sezione 3.12), che allora richiedono molto più tempo. Prima di un
download grande, quindi, spegni il controller tenendo premuto il suo tasto PS per circa 10 secondi, oppure usa
per quel tempo un controller USB: il Wi-Fi ha così la radio tutta per sé. AutoBleem avvisa già il Wi-Fi quando
un controller è collegato, in modo che i due si dividano meglio la radio. Questo aiuta molto, ma non può
eliminare l'effetto, perché la radio resta una sola.

**La procedura di mappatura dei controller.** Usala quando un controller non fa niente in AutoBleem o ha i pulsanti
al posto sbagliato. Mostra il controller collegato com'è davvero - ogni asse, pulsante e hat sotto forma di numeri - e
un'immagine del DualShock che si illumina mentre premi. Visto che del controller che stai provando non ci si può
ancora fidare, la procedura si guida con i **tasti frontali** della console: **RESET** passa al controller successivo,
**OPEN** avvia la mappatura e **POWER** annulla o esce. Durante la mappatura la procedura ti chiede un pulsante dopo
l'altro: premi il pulsante illuminato sull'immagine, oppure OPEN se il tuo controller non ha quel pulsante. Una
pressione breve viene mappata normalmente.

Puoi uscire anche dal controller: tieni premuto Circle per 2 secondi - una barra si riempie e il piè di pagina dice
*Hold 2 s: Exit*. Finché il controller non ha ancora una mappatura, tenere premuto un pulsante qualsiasi per 2 secondi
fa lo stesso (*Hold any button 2 s: Exit*). Sulla tastiera Esc, Spazio e Invio fanno le veci di POWER, RESET e OPEN.

Alla fine la nuova mappatura viene messa in uso così puoi provarla, e OPEN la salva con un nome a tua scelta. Da quel
momento il launcher la carica ogni volta.

![PSC-Bios: la procedura di mappatura dei controller](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - il kernel di AutoBleem

Il kernel di AutoBleem sostituisce il kernel Linux della console, ed è facoltativo. Ti interessa se dalla console vuoi
di più: le dà un orologio funzionante, fa funzionare le chiavette Wi-Fi e Bluetooth USB (per PSC-Bios e i controller
Bluetooth) e aggiunge il supporto dei tasti frontali che l'emulatore usa per i punti di ripristino. ABFlashKit è lo
strumento che lo installa. Prima fa un backup della console, e sa anche riportarla allo stato originale attraverso il
ripristino di Sony.

> **Questo strumento scrive nella memoria flash della console.** Se la scrittura viene interrotta - salta la corrente o
> viene estratta la chiavetta - la console potrebbe non avviarsi più, e installare un kernel personalizzato fa decadere
> la garanzia. Tieni la console alimentata e la chiavetta inserita finché la console non si riavvia da sola.
> ABFlashKit si apre con questo avviso: *I understand* prosegue, *Quit* esce.

![Il menu di ABFlashKit](../images/en/abflashkit-menu.jpg)

ABFlashKit ha tre azioni:

- **Flash Kernel** installa il kernel. Se sulla chiavetta non c'è ancora un backup di ripristino, prima ne crea uno
  delle partizioni della console (`LBOOT.EPB`). Controlla il backup e l'immagine del kernel, scrive il kernel e i file
  di sistema di AutoBleem e riavvia la console. Quando dice *All done - when the screen goes black replace power
  cord*, aspetta che lo schermo diventi nero, poi stacca il cavo di alimentazione della console e ricollegalo.
- **Full backup** salva tutte e quattro le partizioni della console in `LBOOT.EPB`, così potrai ripristinarle in
  seguito. Se un backup c'è già, chiede prima di sovrascriverlo.
- **Restore Mode** è la strada per tornare al firmware originale. Controlla che il backup sulla chiavetta sia
  originale, imposta il flag di ripristino e riavvia nel ripristino di Sony, che riporta la console allo stato salvato
  in `LBOOT.EPB`.

Sotto ogni passaggio una barra di avanzamento mostra a che punto è. ABFlashKit non installa nulla su una console che
usa un altro firmware personalizzato, come BleemSync o Project Eris: prima riporta quella console allo stato
originale.

**Accedere da un PC.** Se conosci Linux e vuoi guardare dentro la console, puoi accedervi da un PC tramite un cavo USB.
Serve il kernel di AutoBleem; su una console originale non funziona.

1. Collega la porta micro-USB della console al PC con un cavo USB. Il PC vede la console come una nuova scheda di
   rete, e trovi l'indirizzo della console nelle impostazioni di quella scheda sul PC.
2. Accedi con `ssh root@<indirizzo della console>`. La password predefinita è `autobleem`.

Al posto della password puoi usare una chiave. Metti la tua chiave pubblica nel file `System/ssh/authorized_keys` sulla
chiavetta e riavvia la console: al prossimo avvio viene aggiunta all'account root. Aggiornare o reinstallare il
launcher non la rimuove.

> **La password predefinita è la stessa su tutte le console**, quindi chiunque possa collegare un cavo alla tua può
> accedere come root. Dove puoi usa una chiave, e non lasciare una console con la password predefinita dove altri
> possono raggiungerla.

<!-- pagebreak -->

## 7. Se qualcosa va storto

La maggior parte dei problemi ha una causa semplice. Qui sotto ognuno parte da ciò che vedi, spiega perché succede e
poi cosa fare. Se devi chiedere aiuto, la prima cosa che chiunque ti chiederà sono i log, quindi si comincia da lì.

**Trovare i log.** Mentre è in funzione, AutoBleem tiene i log in memoria, per non scrivere di continuo sulla
chiavetta. Finiscono in `System/Logs/` sulla chiavetta, sulla scheda o nella cartella dei dati solo quando qualcosa è
andato storto: quando il launcher, un gioco PS1 o RetroArch va in crash, i log vengono salvati in
`System/Logs/crash-<n>/` (si tengono gli ultimi tre crash), e il launcher te lo dice una volta quando torna. Se stai
dando la caccia a un problema che non è un crash, conserva tutti i log: attiva Opzioni → *Diagnostica* → *Conserva i
log sulla chiavetta:* (vale dall'avvio successivo), oppure crea da un PC un file vuoto `System/Logs/keep`. Anche
*Informazioni hardware* (sezione 4.2) mostra dove sono i log, e lì Square salva quelli attuali in
`System/Logs/saved-<n>/`.

Questi sono i file che trovi:

| File | Cosa ti dice |
|---|---|
| `autobleem.log` | Cosa ha fatto il launcher. |
| `launch.log`, `pcsx.log` | Come è stato avviato un gioco PS1, e cosa ha detto l'emulatore mentre girava. |
| `retroarch.log` | Cosa ha detto RetroArch mentre girava. |
| `update.log` | Com'è andato un aggiornamento online; resta sempre sulla chiavetta. |
| `updateroms.log` | Com'è andato UpdateRoms sul PC (capitolo 5); resta sempre sulla chiavetta. |

**Un'immagine ti chiede di inserire la chiavetta, oppure la console è andata in standby.** AutoBleem non trova la sua
chiavetta: non era inserita all'avvio della console, oppure è stata estratta. Inseriscila in una porta USB qualsiasi
(meglio una frontale, sezione 2.1) prima che passino i 5 minuti, oppure premi Power. Se la chiavetta non è stata
rimossa correttamente, AutoBleem prima la controlla: aspetta che la barra di avanzamento arrivi in fondo.

**RetroArch dice che *richiede una libreria di sistema più recente di quella di questa console*.** Quel RetroArch è
stato compilato per un sistema più recente di quello della console, quindi lì non può girare. Usa il RetroArch fornito
con AutoBleem.

**Un gioco dice che *è protetto dalla sua licenza PSN e non può essere avviato*.** I giochi comprati sul PlayStation
Network sono legati alla loro licenza, e AutoBleem non può farli girare. Non c'è niente da sistemare.

**Un gioco non è sullo scaffale.** Di solito la sua cartella non è organizzata come se l'aspetta la scansione.
Controlla che ogni gioco abbia una cartella tutta sua e sia in uno dei formati della sezione 3.10. Il *Gestore del
gioco* (sezione 4.1) elenca dopo i giochi le cartelle rifiutate dalla scansione, segnate *Non aggiunto*, e ti dice
perché ognuna è stata rifiutata; Square elimina una cartella del genere. Dopo aver sistemato una cartella,
*Riscansiona i giochi* nel menu di sistema esegue di nuovo la scansione.

**I giochi non hanno copertine.** O i database delle copertine non sono stati installati - rilancia l'installer con
quella voce spuntata - oppure, per i giochi RetroArch su una console, UpdateRoms non è ancora stato eseguito sul PC
(capitolo 5).

**Un controller non fa niente, o ha i pulsanti scambiati.** AutoBleem non conosce la disposizione di quel controller.
Su una console, mappalo con la procedura di mappatura di PSC-Bios (sezione 6.1). Su un Pi o un PC la pagina
Informazioni hardware (sezione 4.2) mostra cosa vede il sistema del controller, e ti aiuta a capire se viene
rilevato.

**Lo schermo resta nero dopo un gioco sulla console.** L'immagine del launcher non è tornata alla fine del gioco.
AutoBleem ricostruisce la sua finestra da solo, fino a tre volte. Se lo schermo resta ancora nero, tieni premuto il
tasto Power e riaccendi la console.

**Su un Raspberry Pi** puoi andare dietro le quinte del launcher quando serve: `Alt+F2` ti dà un prompt di accesso
sulla seconda console, e SSH è attivo fin dal primo avvio. `sudo journalctl -u autobleem` mostra cosa ha fatto il
servizio del launcher, e `sudo systemctl restart autobleem` lo riavvia. Se il primo avvio non è riuscito a finire
perché mancava la rete, ci riprova all'avvio successivo.

**Su Windows**, `Esc` chiude il launcher. La tua cartella dei dati è quella che hai scelto durante il setup
(`Documents\AutoBleem` se non l'hai cambiata), e i log sono nella sua cartella `System\Logs`.

**La console si riavvia in continuazione dopo un aggiornamento online (chiavetta formattata in ext4).** C'è chi formatta
la chiavetta in ext4, il file system di Linux, invece che in FAT32 o exFAT. Fino alla prossima release di AutoBleem, un
aggiornamento online su una chiavetta del genere estrae ogni file senza il permesso che gli consente di essere
eseguito come programma. AutoBleem allora non riesce ad avviarsi e la console si riavvia di continuo. Le chiavette FAT32
ed exFAT non hanno questo problema. Ci sono due modi per rimediare.

**Soluzione A**: serve un PC Linux. Collega la chiavetta e rendi di nuovo eseguibili i programmi di AutoBleem. Al posto
di `/media/USER/STICK` metti il tuo punto di montaggio; l'ultima riga serve solo se RetroArch è installato:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

Lo schema `bin/emu*/pcsx-ab` della seconda riga copre entrambi gli emulatori: il classico `pcsx-ab` e `pcsx-abnxt`,
che viene installato come `Autobleem/bin/emunxt/pcsx-ab`, quindi per il più recente non serve un comando a parte.

**Soluzione B**: reinstalla sulla chiavetta l'ultima release di AutoBleem, come nella sezione 2.1. L'installer ha
bisogno di un PC che legga la chiavetta. Se il tuo non la legge, la chiavetta va prima formattata, il che cancella
tutto ciò che contiene: copia altrove i tuoi giochi prima di farlo.

> Per evitare il problema usa **FAT32** (una console originale legge solo il FAT32; l'exFAT richiede il kernel di
> AutoBleem, capitolo 6). La prossima release mantiene i permessi e AutoBleem li ripara a ogni avvio.

AutoBleem è software libero (GNU GPL v3 o successiva) ed è fornito senza alcuna garanzia. Per assistenza e novità,
entra nel server Discord indicato nella schermata Informazioni su, oppure visita https://autobleem.retromenele.pl/.
