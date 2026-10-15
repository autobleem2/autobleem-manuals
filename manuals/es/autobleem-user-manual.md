# Manual de usuario de AutoBleem 2

AutoBleem 2 es un lanzador de juegos pensado para la **PlayStation Classic** que, desde la versión 2, funciona
también en una **Raspberry Pi**, en un **PC arrancado desde una memoria USB** y en **Windows**. Te presenta tus
juegos de PS1 como una estantería de carátulas, con la portada y los datos de cada uno, los arranca en el
emulador PCSX que lleva incluido y, si instalas RetroArch a su lado, también te deja jugar a los de otros
sistemas. En este manual encontrarás cómo instalarlo en cada plataforma, cómo usarlo en el día a día y para qué
sirven las herramientas que lo acompañan.

> Todas las descargas están en **https://autobleem.retromenele.pl/**, ordenadas por plataforma. Lo que tienes
> que descargar es el panel *Install* de cada una; los *Build inputs* que aparecen debajo son los archivos que
> los instaladores ya se descargan por su cuenta.

## 1. Qué te ofrece

Con AutoBleem, tu PlayStation Classic (o una Raspberry Pi, un PC viejo o tu ordenador con Windows) se convierte
en una pequeña consola con un menú de verdad para tus propios juegos. Esto es lo que incluye:

- **El lanzador.** Es lo primero que ves al encender: una estantería de carátulas que vas recorriendo, con los
  datos de cada juego al lado. Desde ahí arrancas los juegos, los ordenas en conjuntos (PlayStation, RetroArch,
  Aplicaciones), cambias los ajustes, gestionas las tarjetas de memoria y los estados guardados, y descargas
  aplicaciones y juegos de la Tienda. Tiene el mismo aspecto y funciona igual en todas las plataformas.
- **Dos emuladores de PS1.** `pcsx-abnxt` es el actual y el que se usa por defecto; `pcsx-ab` es el emulador
  clásico que AutoBleem ha traído desde siempre. Puedes elegir uno u otro en las opciones. Los dos comparten
  ajustes y tarjetas de memoria, así que puedes cambiar cuando quieras sin perder nada.
- **RetroArch**, por si también quieres jugar a otros sistemas: NES, SNES, Mega Drive, Game Boy, recreativas y
  muchos más. Es opcional en todas las plataformas. Copias tus ROM y AutoBleem se encarga de ordenarlas en
  listas y de arrancar cada juego con el núcleo adecuado. Los juegos de PlayStation también pueden ir en
  RetroArch: su núcleo *PlayStation 1* aparece el primero en la lista de núcleos (sección 3.9). Juegos como Doom
  funcionan con tus propios archivos del juego, guardados en una carpeta `Packages` (sección 3.10).
- **Las herramientas de la consola.** *PSC-Bios*, que en los menús se llama *Red y mandos*, sirve para configurar
  el WiFi, el reloj, los mandos Bluetooth y la asignación de botones, tanto en la consola como en una Raspberry Pi
  o en la memoria USB para PC. *ABFlashKit* instala el kernel de AutoBleem en una PlayStation Classic
  (capítulo 6).
- **UpdateRoms** para Windows. La PlayStation Classic no tiene red propia, así que este programa de PC se encarga
  de actualizar las listas de RetroArch y de descargar las carátulas de la memoria USB de la consola mientras la
  tienes conectada al ordenador.

![El lanzador: la estantería de carátulas, los datos del juego seleccionado y las ayudas de botones](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Instalación

### 2.1 PlayStation Classic

AutoBleem funciona por completo desde una memoria USB y no modifica nada dentro de la consola: si quitas la
memoria, la consola vuelve a ser exactamente la de antes. Solo necesitas un PC con Windows, una memoria USB
(USB 2.0, de 8 GB o más) y la consola.

La memoria no tiene por qué estar vacía, y **no se formatea** a menos que tú lo pidas. AutoBleem se instala junto
a lo que ya haya en ella, y si ya la usabas con AutoBleem 1.0, se actualiza sin más (lo verás más abajo). Con
una consola de serie, la memoria tiene que estar en **FAT32**, porque el kernel original de la consola no sabe
leer exFAT. Una vez instalado el kernel de AutoBleem (ABFlashKit, capítulo 6), la consola arranca también desde
una memoria en exFAT, y así te libras del límite de FAT32 de 4 GB por archivo.

1. Descarga **AutoBleemInstaller-<version>.zip** del panel PlayStation Classic de la web y descomprímelo donde
   quieras. Dentro encontrarás `AutoBleemInstaller.exe` y su README. AutoBleem se descarga durante la
   instalación, así que el PC tiene que estar conectado a internet.
2. Conecta la memoria y abre `AutoBleemInstaller.exe`. Elige el **canal**: *Release* es la versión probada y la
   adecuada para casi todo el mundo, *Testing* es la próxima versión mientras se está probando, y *Nightly* es la
   compilación de desarrollo más reciente, que puede no funcionar. Luego elige la unidad de la memoria. La línea
   de debajo te indica qué versión de AutoBleem vas a instalar y qué hay ahora en la memoria: *a fresh install*
   (una instalación nueva; los demás archivos de la memoria no se tocan) o *AutoBleem <version> is on this
   stick: it will be updated* (la versión que ya tienes se actualizará, y tus juegos, partidas, tarjetas de
   memoria y ajustes se quedan como están).
   **No hace falta formatear.** El botón **Format** que hay junto a la unidad solo sirve para una memoria
   nueva que aún no tiene sistema de archivos, para una que la consola no puede leer (en NTFS, por ejemplo) o
   para una que quieras dejar limpia. Antes de nada te pide confirmación y después borra todo lo que hay en la
   memoria. Elige ahí FAT32, salvo que la consola ya tenga el kernel de AutoBleem.
   Después marca lo que quieres instalar:
   - **Cover databases**: las carátulas y descripciones de toda la biblioteca de PS1, para que tus juegos
     tengan su portada sin que hagas nada (viene marcado; ocupa unos 300 MB).
   - **RetroArch**: RetroArch con sus núcleos, aplicaciones extra (Doom, Quake, Amiga...) y los recursos de
     libretro, para jugar a otros sistemas. Viene desmarcado; puedes añadirlo más adelante volviendo a abrir el
     instalador.
   - **BIOS files**: los archivos BIOS que algunos núcleos de RetroArch necesitan para arrancar (solo junto con
     RetroArch).
   - **Sample games**: unos cuantos juegos homebrew gratuitos, para que la estantería no esté vacía la primera
     vez que arranques.
3. Pulsa **Install** y espera. Las barras de progreso y el registro te muestran cada paso. Al terminar, la
   memoria se llama `SONY` y lleva una copia de `UpdateRoms` (ver capítulo 5).
4. Extrae la memoria de forma segura y conéctala al **segundo puerto USB frontal** de la consola (el de la
   derecha, el del jugador 2); el primero queda libre para tu mando. Enciende la consola y, en lugar del menú
   original, arrancará AutoBleem. Para un segundo mando, usa un hub USB en el puerto frontal o un mando
   Bluetooth.

**Encender y apagar.** Con la memoria puesta, la consola se enciende, hace parpadear su luz durante unos segundos
mientras detecta AutoBleem y pasa a reposo antes de que salga nada en pantalla. Es normal: AutoBleem arranca
aprovechando el sistema de actualización de la propia consola, y ese sistema funciona así. Pulsa **Power** una
vez y aparecerá el lanzador.

Cuando eliges *Apagar* en el menú del sistema, o pulsas el botón Power de la consola, esta entra en el **reposo
de AutoBleem**: primero AutoBleem desconecta la memoria de forma segura y luego la luz se pone **naranja**, la
señal de que todo ha ido bien. La próxima vez que pulses Power, el lanzador vuelve en unos segundos. **Mientras
la luz esté naranja puedes sacar la memoria** y conectarla al PC; Windows no te pedirá repararla, porque se
desconectó como es debido. Vuelve a ponerla antes de pulsar Power. Si desenchufas el cable de alimentación de la
consola, la próxima vez pasará otra vez por el reposo del arranque. Si la luz está **roja**, la consola está
apagada del todo.

**El puerto de atrás.** El puerto micro-USB de atrás es la toma de alimentación de la consola. Con el kernel de
AutoBleem también admite un dispositivo USB, pero el sitio de la memoria es un puerto frontal.

**Si falta la memoria.** Si la consola arranca sin memoria, o la sacas mientras AutoBleem está en marcha, aparece
una imagen que te pide que la conectes; vale cualquier puerto USB. AutoBleem espera 5 minutos y después pone la
consola en reposo; si quieres que lo haga ya, pulsa Power.

![La imagen que te pide que conectes la memoria](../images/en/insert-stick.jpg)

**Cuándo se comprueba la memoria.** Si la memoria no se desconectó como es debido (la sacaste con AutoBleem en
marcha o se fue la luz), AutoBleem la revisa en busca de errores antes de volver a usarla: al arrancar, al salir
del reposo o al conectarla de nuevo. Una barra de progreso te muestra cómo va la comprobación. En una memoria
grande puede tardar un rato; deja que termine y no apagues la consola mientras tanto.

![La comprobación de la memoria](../images/en/stick-check.jpg)

**Actualizar.** Para actualizar una memoria, vuelve a pasarle el instalador; esta vez el botón dice *Update*.
Instala la versión más reciente del canal que elijas: tus juegos, partidas, ajustes y contenido de RetroArch se
quedan, y solo se sustituyen los archivos del propio AutoBleem. Una consola con el kernel de AutoBleem y WiFi
también puede actualizarse sola (sección 3.12).

**Pasar de AutoBleem 1.0 (o AutoBleem-NG).** Se usa el mismo instalador sobre la misma memoria, sin formatearla:

1. Antes de nada, copia toda la memoria al PC como copia de seguridad, por si acaso.
2. Conéctala, abre `AutoBleemInstaller.exe` y elige el canal y la unidad. **No** pulses Format.
3. Pulsa **Install**. El instalador pasa la organización antigua a la nueva: RetroArch, las ROM y los temas
   van a donde AutoBleem 2 los espera, y las carpetas de ROM antiguas (`nes`, `snes`...) reciben los nombres de
   sistema de RetroArch. Se conservan tus juegos, estados guardados, tarjetas de memoria, ROM y partidas de
   RetroArch, y también `config.ini`; lo único que cambia en él es el emulador de PS1, que pasa a ser
   pcsx-abnxt.
4. Vuelve a conectar la memoria a la consola. El primer escaneo reconstruye la lista de juegos y las listas de
   reproducción. Para tener las carátulas de tus juegos de RetroArch, pasa UpdateRoms en el PC (capítulo 5).

> La consola de serie no tiene reloj ni red. Las fechas solo aparecen una vez instalado el kernel de AutoBleem
> (capítulo 6), y las carátulas de los juegos de RetroArch las pone UpdateRoms desde el PC (capítulo 5).

Tus juegos de PS1 van en la carpeta `Games` de la memoria, cada uno en su propia carpeta; en la sección 3.10
te explicamos cómo organizarlos.

### 2.2 Raspberry Pi

Con AutoBleem, una Raspberry Pi se convierte en una pequeña consola: arranca directamente en el lanzador, sin
pasar por ningún escritorio. En la web tienes dos imágenes de tarjeta listas para usar, una de 32 bits y otra de
64 bits, y además un paquete para instalarlo sobre un Raspberry Pi OS Lite que ya tengas.

| Modelo | Imagen de 32 bits | Imagen de 64 bits | Observaciones |
|---|---|---|---|
| Raspberry Pi 5 | sí | sí | |
| Raspberry Pi 4 Model B, Pi 400 | sí | sí | |
| Raspberry Pi 3 Model B / B+ / A+ | sí | sí | va bien para el lanzador y la PS1 |
| Raspberry Pi Zero 2 W | sí | sí | 512 MB de RAM: la PS1 funciona, los núcleos de RetroArch más pesados no |
| Raspberry Pi 2 Model B | sí | solo la v1.2 | se queda corta para todo lo que sea 3D |
| Raspberry Pi 1, Zero, Zero W | no | no | ARMv6: no funciona ninguna de las dos imágenes |

**Para los juegos de PS1, elige la imagen de 32 bits.** El recompilador ARM rápido del clásico `pcsx-ab` solo
existe en 32 bits, así que en la versión de 64 bits los juegos de PS1 van más lentos. La imagen de 64 bits trae
más núcleos de RetroArch; elígela si los otros sistemas te importan más que la PS1.

**Con Raspberry Pi Imager:**

1. Instala Raspberry Pi Imager (raspberrypi.com/software). En *Choose OS*, elige *Use custom* y el archivo
   `autobleem-<version>-rpi-armhf.img.xz` (32 bits) o `-arm64.img.xz` (64 bits) que has descargado. También
   puedes añadir la URL de un repositorio en los ajustes del programa y elegir AutoBleem de la lista. Hay una
   por canal: `https://autobleem.retromenele.pl/rpi-imager/os_list.json` para la última versión publicada,
   `.../os_list-testing.json` para la que se está probando y `.../os_list-nightly.json` para la compilación de
   desarrollo más reciente. En la pestaña Raspberry Pi de la página de descargas tienes las que existen, cada
   una con su botón *Copy*.
2. En la pantalla de personalización de Imager (el engranaje, o la pregunta que aparece tras *Next*), configura
   **el nombre de usuario y la contraseña, la red WiFi y el país, y activa SSH**. AutoBleem necesita red la
   primera vez que arranca.
3. Graba la tarjeta, métela en la Pi con una pantalla y un teclado o un mando conectados, y enciéndela.

**El primer arranque** tarda entre 5 y 25 minutos, y la pantalla te va contando lo que hace. Si no hay red, te la
pide: elige tu WiFi de la lista y escribe la contraseña. Luego te pregunta si quieres instalar RetroArch; si no
contestas en un minuto, lo instala. Después amplía la partición del sistema, convierte el resto de la tarjeta en
la partición `AUTOBLEEM` para tus juegos, instala RetroArch con sus núcleos, los paquetes de BIOS y los juegos de
muestra, y se reinicia directamente en el lanzador.

Si prefieres que el primer arranque no te pregunte nada, deja las respuestas de antemano en **`autobleem.txt`**,
en la partición de arranque de la tarjeta; se puede abrir y editar desde cualquier PC:

| Clave | Por defecto | Significado |
|---|---|---|
| `root_gib` | 8 | El tamaño de la partición del sistema en GiB; el resto se convierte en la partición de juegos. |
| `hdmi_mode` | 1920x1080@60 | El modo de pantalla de todo el arranque (`1280x720@60` para una tele más antigua). |
| `retroarch` | (se pregunta) | `yes` / `no`: RetroArch y los demás sistemas, o solo PS1. |
| `thumbnails` | none | Con `boxarts` se descarga el juego completo de carátulas para tenerlas sin conexión (unos 9000 archivos). |
| `bios`, `downloads`, `samples` | yes | Pon `no` para saltarte los paquetes de BIOS, todas las descargas o los juegos de muestra. |

**Sobre un Raspberry Pi OS Lite que ya tengas** (Bookworm o Trixie): copia `autobleem-rpi.tar.gz` (o el de arm64)
a la Pi, descomprímelo y ejecuta `sudo bash install.sh`. Te hace las mismas preguntas, deja sitio para la
partición de datos reduciendo la del sistema en el siguiente arranque (`--shrink-root <GiB>`) y pone el lanzador
en la primera consola.

Una vez instalado, llena la **partición `AUTOBLEEM`** de la tarjeta (en exFAT) con tus juegos: saca la tarjeta y
ábrela en cualquier PC, o copia los archivos por la red (SSH viene activado). Los juegos de PS1 van en `Games/`,
las ROM de otros sistemas en `RetroArch/roms/<sistema>/`, la BIOS de PS1 en `System/Bios/` (sección 3.11) y los
temas en `Themes/`.

### 2.3 Memoria USB para PC

Lo mismo, pero para cualquier PC que pueda arrancar desde USB: la memoria arranca el PC directamente en AutoBleem
y no toca el disco del ordenador. Es un sistema de 32 bits, así que también funciona en equipos antiguos.

1. Graba la imagen en una memoria de 8 GB o más. **En Windows**, usa **AutoBleemFlasher** (en el panel PC de la
   web): descomprímelo y abre `AutoBleemFlasher.exe`. Te pedirá permisos de administrador, porque escribe un
   disco entero. Elige el canal y la memoria, pulsa *Write* y confirma dos veces: descarga la imagen, la
   comprueba, la graba y la vuelve a leer para verificarla. Solo te ofrece memorias USB y tarjetas SD, nunca el
   disco desde el que funciona Windows, y **se borra todo lo que haya en la memoria elegida**. En Linux o macOS,
   descarga `autobleem-<version>-pcusb-i386.img.xz` del panel PC y grábala con
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (o con balenaEtcher).
2. Arranca el PC desde la memoria (con la tecla del menú de arranque de tu PC: F12, F8, Esc...). Funciona tanto
   con BIOS como con UEFI; **el arranque seguro (Secure Boot) tiene que estar desactivado**.
3. El primer arranque va como en la Pi: te pide una red si no hay cable conectado, te pregunta por RetroArch, lo
   instala todo (unos ocho minutos con red por cable) y se reinicia en el lanzador.

Después, la memoria tiene una partición `AUTOBLEEM` para tus juegos. Si la conectas a un PC con Windows 10
(versión 1903 o posterior) ya encendido, aparece como una segunda unidad a la que puedes copiar juegos.
`autobleem.txt` está en la primera partición, con las mismas claves que en la Pi (menos `hdmi_mode`: un PC usa
siempre el modo propio de la pantalla).

### 2.4 Windows

Si quieres AutoBleem en tu ordenador con Windows, también funciona como un programa normal: a pantalla completa,
y con los emuladores y RetroArch abriéndose como programas aparte.

1. Descarga **AutoBleemSetup-<version>.exe** y ábrelo. Se instala para tu usuario, sin permisos de
   administrador: el programa va en `%LOCALAPPDATA%\Programs\AutoBleem`, y los datos (juegos, ajustes, temas,
   RetroArch) en la carpeta que elijas, que por defecto es `Documents\AutoBleem`.
2. Marca los componentes que quieras (las bases de datos de carátulas, RetroArch con la versión oficial para
   Windows y sus núcleos, los archivos BIOS y los juegos de muestra) y deja que el asistente los descargue.
3. Abre AutoBleem desde el menú Inicio o desde el escritorio. En un PC, el teclado hace de mando (sección 3.2).

Para actualizar, instala una versión más nueva encima: se sustituye el programa y tu carpeta de datos se queda
como está. Además, el lanzador consulta la web una vez al día y te ofrece la actualización cuando la hay
(sección 3.12).

<!-- pagebreak -->

## 3. Cómo se usa AutoBleem

### 3.1 El lanzador

El lanzador es donde eliges a qué vas a jugar. Te enseña tus juegos como una estantería de carátulas, igual que
verías las cajas en una estantería de verdad, y la vas recorriendo hasta dar con el que buscas. Todo lo demás de
AutoBleem (los ajustes, las tarjetas de memoria, la Tienda) se abre desde aquí, y aquí vuelves cuando sales de
un juego.

El juego seleccionado queda en el centro de la estantería, con un reflejo suave debajo. A su lado ves sus datos
en una pequeña cuadrícula: la editorial, el año, el número de serie, la región, para cuántos jugadores es y
cuándo jugaste por última vez. Si AutoBleem no conoce alguno de estos datos, prefiere quitar esa línea antes que
dejarla vacía. Junto a los datos hay un botón para jugar. Un juego sin carátula aparece como un disco dentro de
la bandeja negra de una caja vacía, para que también tenga su sitio en la estantería.

El aspecto del lanzador depende del tema. El tema por defecto es **ab2.0.0**: una instalación nueva lo pone, y
una actualización que lo trae también, pero solo una vez; si después eliges otro tema (sección 3.6), ese es el
que se queda.

**La barra de ayuda**, abajo del todo, te dice qué hace cada botón en ese momento. Tiene dos líneas de cuatro
huecos cada una. La primera se refiere al juego seleccionado: jugarlo, jugarlo en RetroArch, abrir la fila de
iconos de debajo o abrir el menú rápido. La segunda no cambia nunca: Select elige el conjunto, Start escoge un
juego al azar, Triangle muestra la guía de botones y L2 + R2 abre el menú del sistema. Cuando un botón no tiene
nada que hacer, su ayuda aparece atenuada.

**Encuentra los juegos nuevos solo.** Cada vez que arranca, el lanzador revisa tu carpeta de juegos en segundo
plano, así que un juego que copiaste con la máquina apagada aparece sin que tengas que hacer nada. Mientras dura
el escaneo, una burbuja arriba a la derecha te muestra cómo va, y los juegos nuevos van apareciendo en la
estantería a medida que se encuentran. Mientras tanto, puedes seguir navegando.

**Una instalación nueva** todavía no tiene juegos. En lugar de una estantería vacía, ves una tarjeta de
bienvenida, *¡Hola y bienvenido a AutoBleem!*, que te dice que copies tus juegos en `Games` y pulses
*Reescanear juegos*. Te indica el sitio según tu plataforma: en tu memoria USB (PlayStation Classic, memoria USB
para PC), en tu tarjeta SD (Raspberry Pi) o en tu carpeta de AutoBleem (Windows). La tarjeta desaparece en cuanto
un escaneo encuentra el primer juego.

**Las notificaciones** son las burbujas de arriba a la derecha. Te mantienen al tanto sin estorbar: el avance del
escaneo, el nombre del conjunto al que acabas de cambiar (*Mostrando: ...*), un mando con poca batería, un aviso
después de un cierre inesperado, un procesador de escaneo trabajando o una descarga de la Tienda. La burbuja de
una descarga muestra la velocidad y el tiempo que falta, por ejemplo `1.4 MB/s · 0:42`. Cuánto tiempo se quedan
en pantalla las burbujas informativas lo decides tú, en Opciones → *Duración del aviso:*.

**La batería de los mandos.** En la consola, en una Raspberry Pi y en la memoria USB para PC (no en Windows), cada
mando inalámbrico que informa de su batería aparece como un pequeño icono con su porcentaje, en su propia
placa, apiladas hacia abajo desde la esquina superior izquierda. Un mando que juega como jugador 1 o jugador 2
lleva una etiqueta P1 o P2, según la opción *Intercambiar jugador 1 / jugador 2 (emuladores PS1):* (sección
3.6); un mando que no está asignado a ningún jugador, o un tercer mando, no lleva etiqueta. Cuando a un mando le
queda poca batería, una notificación te avisa una vez, con el nombre del mando y el porcentaje.

**La etiqueta del canal.** Si usas una versión que no es definitiva, una pequeña etiqueta bajo la placa de las
baterías, en la esquina superior izquierda, te lo recuerda. Es una pastilla con el canal y, al lado, la versión
abreviada: `ALPHA`, `BETA` o `RC` para una versión preliminar, `TESTING` para cualquier otra versión preliminar,
`NIGHTLY` para una compilación nocturna y `DEV` para una compilación hecha a mano (en el caso de `DEV`, la
versión es el commit del que se compiló). Una versión publicada no lleva etiqueta.

![El selector de conjuntos: tres pestañas, y los grupos de la pestaña actual con su número de juegos](../images/en/set-picker.jpg)

### 3.2 Los controles

AutoBleem está pensado para manejarse solo con el mando, y los botones significan lo mismo en todas las
pantallas: Cross confirma, Circle vuelve atrás y Triangle ayuda. Si no recuerdas para qué sirve un botón, la
barra de ayuda de abajo te lo dice, y Triangle en la estantería abre la guía de botones, con todos los botones de
todas las pantallas (sección 4.3). En la estantería, los botones hacen esto:

| Botón | En la estantería |
|---|---|
| Izquierda / Derecha | Pasa al juego anterior o al siguiente; si lo mantienes pulsado, sigue avanzando. |
| L1 / R1 | Salta a la inicial anterior o siguiente de los títulos, para recorrer rápido una estantería larga. En una estantería vacía y con una unidad USB conectada, R1 abre *Disco* (sección 3.9a). |
| Cross | Arranca el juego seleccionado: un juego de PS1 en el emulador de PS1, uno de RetroArch en su núcleo, y una aplicación después de mostrar su ficha de información. |
| Square | Arranca el juego de PS1 seleccionado en RetroArch. Si lo seleccionado es un disco en una unidad USB, lo que hace es copiarlo (*Copiar disco*, sección 3.9a). |
| Circle | Te devuelve a la vista del disco cuando hay un disco en la unidad (sección 3.9a). |
| Triangle | Abre la guía de botones. |
| Start | Escoge un juego al azar del conjunto actual, para cuando no te decides. |
| Select | Abre el selector de conjuntos, donde eliges qué juegos muestra la estantería (sección 3.3). |
| Arriba | Abre el menú rápido (sección 3.4). |
| Abajo | Abre la fila de iconos bajo el juego (*AJUSTES*, *Juego*, *MEMORY CARD*, *REANUDAR*); Arriba la vuelve a cerrar. |
| L2 + R2 | Abre el menú del sistema (sección 3.5). |

**Con teclado.** En un PC sin mando, o con un teclado USB en la consola, en una Pi o en la memoria USB para PC,
las teclas hacen de botones. Las flechas son la cruceta, Intro es Cross, Esc o Retroceso es Circle, Tab es
Triangle y la barra espaciadora es Square. F1 y F2 son Select y Start, Re Pág y Av Pág son L1 y R1, Inicio y Fin
son L2 y R2, y F10 abre el menú del sistema. En una máquina de desarrollo, Esc cierra el programa y la barra
espaciadora es Start.

**En todas las listas y menús** se usan los mismos movimientos: Arriba y Abajo mueven el cursor, L2 y R2 pasan
página, L1 y R1 saltan a la primera o a la última fila, Cross selecciona y Circle vuelve atrás. Nunca tienes que
buscar un botón de guardar: una pantalla de ajustes los guarda al salir de ella con Circle.

**Salir de un juego o de una aplicación.** Mantén Start + Select, o Home, durante 2 segundos y vuelves a
AutoBleem. Funciona con cualquier mando: el de la consola, uno USB o uno Bluetooth. Una pulsación corta de esos
mismos botones abre, en cambio, el menú del emulador. Las aplicaciones no tienen ese menú, así que en ellas solo
sirve mantenerlos pulsados.

![La fila de iconos bajo el juego seleccionado](../images/en/launcher-icons.jpg)

### 3.3 Los conjuntos

Una biblioteca grande se recorre mejor por partes. Los conjuntos te permiten dejar en la estantería un solo tipo
de juego (solo tus favoritos, solo los de Super Nintendo, solo los de una carpeta), para no tener que pasar por
delante de cientos de carátulas hasta dar con la que quieres.

Pulsa **Select** y se abre el selector de conjuntos. Tiene tres pestañas, PlayStation, RetroArch y Aplicaciones:
L1 y R1 cambian de pestaña, Arriba y Abajo recorren los grupos de la pestaña (L2 y R2, página a página) y Cross
lleva a la estantería el grupo que has elegido. Circle (*Atrás*) cierra el selector sin cambiar nada. El pie de
la pantalla también te recuerda estas teclas. Cada fila indica cuántos elementos contiene. Un grupo vacío se abre
en una estantería vacía, donde la fila de iconos solo ofrece *AJUSTES*.

**La pestaña PlayStation.** En una PlayStation Classic empieza por *Todos los juegos* y *Juegos internos* (los
veinte juegos que trae la consola), seguidos de *Juegos USB*, que es todo lo que hay en `Games/`, y de un grupo
por cada carpeta que hayas creado dentro, de modo que un juego que está en una subcarpeta pertenece al grupo de
esa carpeta. Después vienen *Juegos favoritos*, *Historial de juego* y, en cuanto hayas marcado al menos un juego
como juego de pistola, *Juegos de pistola*. Una Raspberry Pi, una memoria USB para PC y Windows no tienen juegos
internos, así que ahí la lista empieza en *Juegos USB*, que es toda tu biblioteca.

**La pestaña RetroArch** solo aparece donde RetroArch está instalado. Tiene un grupo por cada sistema del que
tengas juegos, más los Favoritos y el Historial propios de RetroArch.

**La pestaña Aplicaciones** ordena las aplicaciones por tipo: *Todas las aplicaciones*, y después *Juegos*,
*Emuladores*, *Herramientas*, *Multimedia* y *Otros*. El grupo de cada aplicación se indica en su archivo
`app.ini`. En esta pestaña también aparecen las **aplicaciones PE**, programas de Windows que ejecuta el PE
runner; si la consola no puede arrancar alguna, la verás marcada como *no puede ejecutarse en esta consola*. Donde
el lanzador la muestra, también hay una fila *Paquetes* en la lista (sección 3.10).

### 3.4 El menú rápido

El menú rápido es una lista corta con lo que más usas mientras navegas por tus juegos, para que no tengas que
rebuscar en el menú del sistema completo. Se abre con **Arriba** en la estantería o con el **icono del engranaje**
de la fila de iconos (la que tiene *AJUSTES*, *Juego*, *MEMORY CARD* y *REANUDAR*).

Arriba y Abajo recorren las opciones (desde la última, el cursor vuelve a la primera), Cross elige una y Circle
cierra el menú. Debajo del menú, una línea describe la opción seleccionada. Estas son las opciones:

- *Reescanear juegos* busca en el momento juegos nuevos, cambiados o eliminados; viene bien cuando acabas de
  copiar juegos y no quieres esperar.
- *Tienda* abre la Tienda de AutoBleem, donde puedes explorar e instalar juegos, aplicaciones y extensiones
  (sección 3.13).
- *Núcleos de RetroArch*, donde RetroArch está instalado, te deja elegir qué núcleo se encarga de cada sistema.
- *Red y mandos* abre las pantallas de WiFi, de emparejamiento Bluetooth y de asignación de botones del mando
  (capítulo 6). Solo aparece si una extensión instalada las proporciona, como hace PSC-Bios en la consola, en una
  Raspberry Pi y en la memoria USB para PC. Si esa extensión está instalada pero desactivada, la opción aparece
  en gris y su descripción te dice que la actives en Extensiones; Cross abre entonces la lista de Extensiones
  justo en ella.
- *Reiniciar el lanzador* cierra AutoBleem y lo vuelve a abrir (solo en la consola, en una Raspberry Pi y en la
  memoria USB para PC).
- *Menú del sistema...* abre el menú del sistema completo con todo lo demás: Opciones, Administrador de Juegos,
  Apagar y más (sección 3.5).

Todo lo que hay aquí, salvo la Tienda, los núcleos de RetroArch y Reiniciar el lanzador, está también en el menú
del sistema.

![El menú rápido](../images/en/quick-menu.jpg)

### 3.5 El menú del sistema

En el menú del sistema está todo lo que AutoBleem sabe hacer además de jugar: los ajustes, las herramientas para
tu biblioteca y tus tarjetas de memoria, la información de la máquina y la forma de apagarla. Pulsa **L2 + R2** a
la vez (da igual el orden) y se abre encima de la estantería. Sus opciones están agrupadas bajo los títulos
*Biblioteca*, *Sistema* y *Salir*, con las dos que más se usan arriba del todo. Abajo, una línea describe la opción
seleccionada, así que puedes echar un vistazo antes de elegir.

| Apartado | Opción | Para qué sirve |
|---|---|---|
| (arriba) | *Reescanear juegos* | Busca ahora mismo juegos nuevos, cambiados o eliminados. El escaneo ya vigila la carpeta por su cuenta, así que solo lo necesitas cuando no quieres esperar. |
| | *Extensiones* | Muestra las extensiones que hay en la memoria, como la Tienda de AutoBleem, para que puedas abrirlas o desactivarlas (sección 3.13). |
| *Biblioteca* | *Administrador de Juegos* | Muestra los juegos de PS1 como una lista con sus carpetas; desde ahí puedes borrar un juego o eliminar las carátulas (sección 4.1). No se puede abrir mientras hay un escaneo en marcha. |
| | *Memory cards* | Gestiona tus conjuntos de tarjetas de memoria compartidas (sección 3.8). |
| | *Procesadores de escaneo* | Establece el orden de los programas que cada escaneo ejecuta primero, y los activa o desactiva (sección 3.14). No se puede abrir mientras hay un escaneo en marcha. |
| *Sistema* | *Opciones* | Abre los ajustes de AutoBleem (sección 3.6). |
| | *Red y mandos* | Abre las pantallas de WiFi, de emparejamiento de mandos Bluetooth, de configuración del DualShock 3 y de asignación de botones (capítulo 6). Solo aparece si una extensión las proporciona; lo verás más abajo. |
| | *Información de hardware* | Muestra los datos de la máquina (sistema, CPU, almacenamiento, interfaces de red, zona horaria, pantalla, y los mandos con su asignación), en la misma página en todas las plataformas (sección 4.2). Circle te devuelve al menú del sistema. |
| | *Mando virtual* | Muestra los mandos que reciben las aplicaciones y los que ve el demonio; te ayuda cuando un mando no funciona en una aplicación (sección 4.5). Circle te devuelve al menú del sistema. |
| | *Actualización de software* | Busca ya en la web una versión más nueva de AutoBleem o de RetroArch, sin esperar a la comprobación diaria (sección 3.12). Si el lanzador ya sabe que hay una, la fila dice *Actualización disponible*. En una PlayStation Classic hace falta el kernel de AutoBleem y una red WiFi. |
| | *Sobre* | Muestra los créditos y la licencia. |
| *Salir* | *RetroArch* | Deja el lanzador y abre el menú propio de RetroArch, para sus ajustes y sus listas de contenido; al cerrar RetroArch vuelves al lanzador. Solo aparece donde RetroArch está instalado. |
| | *Apagar* | Apaga la máquina, después de pedirte confirmación (lo verás más abajo). |

**Red y mandos** solo aparece si una extensión instalada proporciona la entrada `network`, algo que la extensión
declara con `Provides=network` en su `extension.ini`. PSC-Bios lo hace en la consola, en una Raspberry Pi y en la
memoria USB para PC. Si esa extensión está instalada pero desactivada, la opción sigue en el menú, en gris, y su
descripción te dice que la actives en Extensiones; si pulsas Cross sobre ella, la lista de Extensiones se abre
justo en esa extensión.

**Apagar** hace lo que le conviene a cada máquina. En la consola la deja en el reposo de AutoBleem: la memoria se
desconecta, la luz se pone naranja y Power devuelve el lanzador en unos segundos (sección 2.1). En una Raspberry
Pi o en un PC, la máquina se apaga.

![El menú del sistema](../images/en/system-menu.jpg)

### 3.6 Opciones

En Opciones es donde haces tuyo AutoBleem: la imagen en tu pantalla, el aspecto del lanzador, el idioma, el
sonido o el emulador de PS1 con el que juegas. Se abre desde el menú del sistema (*Opciones*) o con el icono
*AJUSTES* que hay bajo cada juego. Lo normal es ajustar la pantalla y el idioma una vez y volver solo cuando algo
se ve mal en una tele concreta o te apetece un cambio.

Los ajustes están ordenados en grupos, cada uno con su título. Arriba y Abajo pasan de una fila a otra, e
Izquierda y Derecha cambian el valor de la fila en la que estás: una pulsación avanza un paso, y si mantienes el
botón sigue avanzando. L1 y R1 saltan a la primera o a la última fila, y L2 y R2 pasan página. En una fila con
una lista de temas, músicas o fuentes, Start elige uno al azar. Un ajuste que se activa o desactiva muestra **ON**
u **OFF**. Cada cambio se ve en el momento, y Circle sale de la pantalla y lo guarda todo; no hay nada más que
confirmar. La única excepción es el modo de pantalla, que se prueba al salir de Opciones (lo verás en
*Pantalla:* más abajo).

Algunas filas solo aparecen cuando tienen sentido: las de CRT solo con una imagen 4:3, las de RetroArch solo
donde RetroArch está instalado y las de los juegos internos solo en una PlayStation Classic.

| Grupo / ajuste | Para qué sirve |
|---|---|
| *Interfaz*: *Pantalla:* | Fija la resolución de la pantalla para el lanzador y para el emulador de PS1. *Auto* usa el modo propio de la pantalla y te dice cuál es, por ejemplo *Auto (1920x1080)*; también puedes elegir cualquier modo de los que ofrece la pantalla. La consola ofrece 720p, 1080p y *CRT 4:3* (720x480), el modo para una tele CRT antigua o una capturadora 4:3. Cámbialo si la imagen no encaja en tu tele o se ve borrosa. Esta fila no aparece cuando AutoBleem funciona en una ventana en una máquina de desarrollo. |
| *Margen CRT:* | Encoge un poco todo, de 0 a 10 % en pasos de 1 %, porque las teles antiguas recortan los bordes de la imagen. Súbelo hasta que la barra de ayuda y las esquinas se vean enteras. Solo aparece con una salida 4:3, se aplica en el momento y funciona incluso antes de la pantalla de inicio. |
| *Altura de la imagen:* | Hace la imagen más alta o más baja, de -40 a +40 en pasos de 2, en cualquier salida 4:3: *CRT 4:3*, o un modo 4:3 en una salida VGA o de PC. Úsalo cuando en una tele antigua la imagen se ve aplastada o se sale por arriba y por abajo. Se aplica en el momento, y la imagen de los juegos en RetroArch también lo sigue. |
| *Escalado de pantalla del emulador:* | Decide cómo ajusta el emulador de PS1 la imagen del juego a tu pantalla. *1x1* muestra los píxeles tal cual los da la PlayStation, pequeños y exactos; *2x (entero)* y *4:3 (entero)* solo escalan en múltiplos enteros, lo que da la imagen más nítida; *4:3* conserva la forma original de la imagen; *Pantalla completa* la estira por toda la pantalla. Sustituye al antiguo interruptor de pantalla panorámica. El clásico `pcsx-ab` y RetroArch solo conocen pantalla completa y 4:3. |
| *Halo de pantalla:* | Con ON, las franjas vacías a los lados de la imagen del juego (donde la imagen no llena la pantalla) se rellenan con un resplandor suave de la propia imagen en vez de con negro. Funciona con `pcsx-abnxt`. |
| *Tema AutoBleem:* | Cambia el aspecto del lanzador. Los temas están en `Themes/`, y un zip de tema que dejes ahí también aparece con su nombre. Los temas que trae AutoBleem se renuevan con cada actualización, así que si quieres retocar uno, cópialo antes con otro nombre. El tema por defecto es **ab2.0.0**. |
| *Estilo de carátulas:* | Elige el marco de caja de CD que se dibuja alrededor de las carátulas de PS1. |
| *Destello de la carátula:* | Hace que un destello cruce la carátula seleccionada cada vez que la estantería se detiene. |
| *Idioma:* | Fija el idioma del lanzador; hay 17, y el cambio es inmediato. |
| *Duración del aviso:* | Fija cuánto tiempo se quedan las burbujas informativas (*Mostrando: ...*, el resumen del escaneo), de 0 a 20 segundos; con 0 aparece *Desactivado* y no se muestran. Los mensajes de error tienen su propio tiempo fijo, para que no se te escape ninguno. |
| *Pantalla de inicio:* | Muestra la imagen de AutoBleem mientras arranca el lanzador; desactívala para ir directamente a la estantería. |
| *Animaciones:* | Anima el paso de una pantalla a otra; desactívalo si prefieres que cada pantalla aparezca al instante. |
| *Fuentes*: *Usar la fuente predeterminada:* | Con ON, el lanzador usa su propia fuente (Red Hat Text); desactívalo para usar la fuente que elijas en la fila siguiente. |
| *Fuente:* | Elige una fuente tuya: cualquier archivo `.ttf` u `.otf` de `resources/fonts`, de `RetroArch/fonts` o de la carpeta del tema. La fila muestra el nombre de la fuente que de verdad se está usando. |
| *Sonido*: *Música:*, *Música de fondo:* | *Música:* elige la pista que suena con el lanzador: la del tema o un archivo de `resources/music`. *Música de fondo:* decide si suena música o no. |
| *Emulación*: *Emulador PS1:* | Elige el emulador en el que arrancan tus juegos de PS1: `pcsx-abnxt`, el predeterminado (el PCSX-ReARMed actual con los añadidos de AutoBleem), o `pcsx-ab`, el clásico. Prueba con el otro cuando un juego no va bien. Un punto de reanudación guardado con uno se puede continuar con el otro, salvo que el juego funcionara sin archivo BIOS. |
| *Intercambiar jugador 1 / jugador 2 (emuladores PS1):* | Intercambia cuál de los dos primeros mandos es el jugador 1 y cuál el jugador 2, en los dos emuladores de PS1; muy práctico cuando los mandos están conectados "al revés". Solo importa con dos o más mandos conectados; con uno solo siempre juegas como jugador 1. No afecta a RetroArch. Si el emulador de PS1 que usas todavía no sabe intercambiarlos, AutoBleem te lo dice. |
| *Jugar todos los juegos PSX con RA:*, *Actualizar config. de RA:*, *Conservar config. de RetroArch:* | Estas tres solo aparecen donde RetroArch está instalado. La primera arranca todos los juegos de PS1 en el núcleo de PS1 de RetroArch (*PlayStation 1*; en un PC es SwanStation). La segunda deja que AutoBleem escriba sus ajustes en la configuración de RetroArch cuando arranca un juego en él. La tercera conserva los cambios que hagas en el menú de RetroArch al cerrarlo. |
| *Biblioteca*: *Mostrar juegos internos:* | Muestra los juegos que trae la consola en las listas de PlayStation (solo en PlayStation Classic). |
| *Nombres de juegos limpios:* | Con ON (lo predeterminado), las listas de juegos de RetroArch muestran nombres limpios, sin etiquetas entre paréntesis o corchetes como (USA), (Rev 1) o [!]; con OFF se ven los nombres de archivo. El nombre del archivo sigue apareciendo en los datos del juego. No afecta a los juegos de PS1, porque sus títulos salen de la base de datos. |
| *Obtener carátulas en línea:* | Deja que el escaneo descargue las carátulas que faltan de los servidores de libretro (Raspberry Pi, PC, Windows). |
| *Actualizaciones*: *Actualizaciones:* | Elige qué actualizaciones busca el lanzador (sección 3.12): `release` (la versión probada), `testing` (la próxima versión, en pruebas), `nightly` (la compilación de desarrollo más reciente) u `off`. Por defecto sigue la versión que instalaste. No aparece en una máquina de desarrollo. |
| *Diagnóstico*: *Conservar los registros en el USB:* | A partir del siguiente arranque guarda todos los registros en la memoria, y no solo tras un cierre inesperado; actívalo cuando estés persiguiendo un problema (capítulo 7). |
| *Mostrar rendimiento:* | Muestra en la esquina inferior izquierda un panel con la tasa de fotogramas, la carga de la CPU, los hilos y la memoria; dentro de un juego, el emulador muestra también sus FPS y su CPU. |

**Cambiar el modo de pantalla.** Cuando sales de Opciones con un modo nuevo en *Pantalla:*, AutoBleem cambia a
ese modo y te pregunta *¿Mantener este modo de pantalla?*. Si la imagen se ve bien, confírmalo. Si la tele se
queda en negro, espera: si no confirmas, AutoBleem vuelve al modo anterior al acabar una cuenta atrás.

**Temas en una pantalla 4:3.** En el modo *CRT 4:3*, la lista de temas solo muestra los que tienen un diseño 4:3.
Si el tema que usas no lo tiene, el tema predeterminado ocupa su lugar en cuanto confirmas el modo (y en cada
arranque en ese modo), y un aviso te lo dice: *Tema cambiado al predeterminado (CRT 4:3)*.

![Las opciones, por grupos](../images/en/options.jpg)

![El grupo Pantalla: Margen CRT y Altura de la imagen](../images/en/options-display.jpg)

![El aviso tras cambiar a CRT 4:3 con un tema sin diseño 4:3](../images/en/crt43-theme-notice.jpg)

### 3.7 Los ajustes de cada juego

Cada juego puede tener sus propios ajustes. La mayoría van bien tal cual, pero de vez en cuando alguno necesita
una pequeña ayuda (una imagen más nítida o más suave, saltarse un fotograma para que vaya fluido, otra tarjeta de
memoria), o quieres marcarlo como favorito. El editor de juego es el sitio donde cambias estas cosas solo para
ese juego, sin tocar los demás.

Con un juego seleccionado, pulsa **Abajo** para abrir la fila de iconos que tiene debajo. Hay cuatro iconos:
*AJUSTES* (las opciones de la sección 3.6), *Juego* (los ajustes propios de este juego), *MEMORY CARD* (su tarjeta
de memoria) y *REANUDAR* (sus estados guardados). Ve a uno y pulsa Cross para abrirlo.

**El editor de juego** (el icono *Juego*) muestra a la derecha los datos del juego (el título, la editorial, el
año, el número de jugadores, la carpeta y la tarjeta de memoria) y a la izquierda sus ajustes. Arriba y Abajo
pasan de un ajuste a otro e Izquierda y Derecha los cambian, igual que en Opciones; si mantienes un botón, el
movimiento se repite. Cuando termines, Circle guarda los cambios y te devuelve atrás. Un juego que no tiene
título en sus datos aparece con el nombre de su carpeta.

Los ajustes están repartidos en cuatro grupos:

- **Juego** trata de cómo maneja AutoBleem el juego. *Favorito:* lo añade al grupo *Juegos favoritos* del
  selector de conjuntos. *Bloquear datos:* le dice al escaneo que deje el título, el número de serie y la lista
  de discos tal como los has puesto, para que un escaneo posterior no machaque tus cambios. *Reanudar:* decide qué
  pasa cuando arrancas un juego que tiene puntos de reanudación: *Preguntar* muestra el selector de ranuras,
  *Última ranura* continúa al momento desde la ranura más reciente, y *Nunca* empieza siempre el juego desde el
  principio. Donde RetroArch está instalado hay dos filas más. *Juego de pistola:* es para los juegos de pistola
  de luz: el juego pasa al grupo *Juegos de pistola* y siempre se ejecuta en RetroArch, porque el núcleo de PS1 de
  RetroArch tiene la GunCon (al activarlo se activa también la fila siguiente). *Jugar usando RA:* ejecuta este
  juego concreto en RetroArch en lugar de en el emulador de PS1.
- **Pantalla** trata del aspecto de la imagen. *Resolución:* dibuja el juego a 1x o a 2x (con la GPU integrada),
  y *Eliminar costuras:*, que solo funciona a 2x, oculta las líneas finas que pueden aparecer entre partes de la
  imagen a ese tamaño. *Tramado:* (*Desactivado*, *Activado*, *Siempre*) controla el fino patrón de puntos que usa
  la PlayStation para mezclar colores, y *Suavizado:* elige uno de los escaladores de suavizado del emulador.
  *Filtro:* decide cómo se escala la imagen a la pantalla: *Más cercano* muestra los píxeles tal cual, *Lineal*
  los suaviza, *Nítido* y *Nítido (simple)* mantienen los píxeles definidos sin que parpadeen, y además está
  *Quilez*. Los filtros CRT *CRT (fast)*, *CRT (raster)* y *CRT-Pi* imitan una tele antigua y dibujan sus propias
  scanlines, así que las filas de scanlines se quedan en gris mientras tienes uno de ellos elegido. Si no,
  *Scanlines:* añade las líneas oscuras de una tele antigua, y *Brillo de las scanlines:* fija lo oscuras que son.
  *Resolución*, *Eliminar costuras*, *Tramado*, *Suavizado* y los filtros que no son *Lineal* ni *Más cercano*
  son para `pcsx-abnxt`; el clásico `pcsx-ab` y RetroArch muestran cualquier otro filtro como *Más cercano*.
- **Renderizado** tiene el *Plugin:* de GPU y el *Frameskip:* (*Auto*, *Desactivado*, o de 1 a 3 fotogramas).
  Saltarse fotogramas ayuda a que un juego que va demasiado lento mantenga su velocidad, a cambio de una imagen
  menos fluida.
- **Emulador** tiene *SpeedHack:*, la *Frecuencia:* de la CPU, *Interpolación SPU:* (cómo se suaviza el sonido),
  *Logo de arranque:* y, con `pcsx-abnxt`, *Parches de Sony:*. Desactiva *Logo de arranque:* para saltarte la
  pantalla de la BIOS; lo necesitas con un disco homebrew cuyo logo personalizado le impide arrancar.

La forma de la imagen y la resolución de la pantalla no se ajustan por juego, sino para todos a la vez, en
Opciones (*Escalado de pantalla del emulador:* y *Pantalla:*).

**Otros botones del editor.** Triangle cambia el nombre del juego con el teclado en pantalla. Square le asigna
otra tarjeta de memoria (*Cambiar memory card*). Mientras el juego siga usando su propia tarjeta, Start la
convierte en un nuevo conjunto compartido para que otros juegos también puedan usarla (*Compartir memory card*,
sección 3.8). Estas dos opciones no están disponibles para los juegos internos de la consola. Mantener pulsado
Izquierda / Derecha o Arriba / Abajo repite el movimiento aquí, y también en las pantallas de opciones de juego y
de núcleos de RetroArch.

Un juego de la unidad que no tiene archivo `pcsx.cfg` no puede guardar sus ajustes; si cambias uno, el editor te
avisa con *No guardado: este juego no tiene pcsx.cfg*.

Para un **disco en la unidad** (sección 3.9a) algunos ajustes no tienen sentido, así que el editor pone esas filas
en gris, y cuando pasas por una la línea de abajo dice *No disponible para un disco en la unidad*.

![El editor de juego para un disco en la unidad](../images/en/game-editor-disc.jpg)

**Ajustes guardados en el emulador.** También puedes afinar un juego mientras juegas: el menú del propio emulador
tiene *Save settings for this game* (sección 3.9). Cuando un juego tiene ajustes guardados ahí, son esos los que
usa. El editor de juego muestra entonces sus filas de Pantalla, Renderizado y Emulador en gris, con los valores
guardados, bajo el título *Guardado en el emulador*: puedes leerlos, pero no cambiarlos. Si prefieres volver a los
ajustes del editor, elige *Desbloquear los ajustes* y confirma: se borran los ajustes que guardó el emulador y las
filas se pueden cambiar de nuevo. Los dos emuladores, `pcsx-ab` y `pcsx-abnxt`, leen y escriben los mismos
ajustes guardados, así que da igual cuál de ellos los guardara.

![El editor de juego](../images/en/game-editor.jpg)

### 3.8 Tarjetas de memoria y estados guardados

En una PlayStation de verdad compartías una o dos tarjetas de memoria entre todos tus juegos, y tarde o temprano
te quedabas sin espacio. En AutoBleem, cada juego de PS1 tiene de entrada su propia tarjeta de memoria, así que
nunca tienes que preocuparte por el espacio ni por en qué tarjeta está cada partida. La tarjeta se guarda junto a
los estados guardados del juego, en `Games/!SaveStates/<carpeta del juego>/`.

**Conjuntos de tarjetas compartidas.** A veces los juegos necesitan ver las partidas de otros: una secuela que
lee la partida del primer juego, por ejemplo, o los títulos de una saga que quieres tener en una sola tarjeta.
Para eso creas un conjunto compartido, una tarjeta que usan varios juegos. Los conjuntos se guardan en
`Games/!MemCards/`, y los gestionas con *Memory cards* en el menú del sistema. Square crea un conjunto nuevo (el
nombre lo escribes con el teclado en pantalla), Cross cambia el nombre del seleccionado y Triangle lo borra,
después de preguntarte. Para poner un juego en un conjunto, usa *Cambiar memory card* en su editor de juego
(sección 3.7) o su icono *MEMORY CARD*.

**El editor de tarjetas de memoria** se abre desde el icono *MEMORY CARD* de un juego. Muestra la tarjeta del
juego y una segunda tarjeta una al lado de la otra, con el icono y el título de cada partida, como la pantalla de
tarjetas de memoria de la consola original. Square copia la partida seleccionada a la otra tarjeta, Triangle la
borra, y Select desfragmenta una tarjeta, juntando sus bloques libres para que vuelva a caber una partida grande.
Start te deja elegir qué conjunto aparece a la derecha, y Cross vuelve a cargar las dos tarjetas desde la
memoria USB. Una tarjeta en la que el juego aún no ha escrito (porque todavía no has guardado en él) está vacía y
pone *aún no hay tarjeta* junto a su nombre. Si has hecho cambios, AutoBleem te pregunta *¿Quieres guardar los
datos de las memory cards?* antes de salir del editor, de recargar las tarjetas o de mostrar otro conjunto.

![El editor de tarjetas de memoria](../images/en/memory-card-editor.jpg)

**Puntos de reanudación.** Muchos juegos de PS1 solo te dejan guardar en sitios concretos, y no siempre llegas a
uno antes de tener que parar. Los puntos de reanudación lo resuelven: cuando sales de un juego de PS1 con el botón
Reset de la consola (o desde el menú del emulador en una Pi o en un PC), AutoBleem guarda un estado justo en el
punto en el que estabas. Mientras lo escribe, al salir del juego, el emulador muestra *Please wait...*. La
próxima vez, sigues desde ese mismo momento.

Los encontrarás en el icono *REANUDAR* del juego. Si el juego tiene un punto de reanudación, el icono muestra una
pequeña imagen de él; si no tiene ninguno, el icono aparece en gris. El selector de ranuras tiene cuatro, que se
muestran como tarjetas enmarcadas, cada una con una imagen del momento, su número de ranura y su fecha. La más
reciente lleva la marca **MÁS RECIENTE**, y una ranura sin usar pone *Sin punto de reanudación*. Cross continúa el
juego desde la ranura seleccionada y Triangle la borra. Que el selector aparezca o no al arrancar el juego lo
decide el ajuste *Reanudar:* del juego (sección 3.7).

Los juegos de PS1 a los que juegas en RetroArch también tienen ranuras de reanudación. Cada ranura lleva una
insignia, el logo de AutoBleem 2 o el de RetroArch, para que sepas qué emulador la escribió.

![El selector de ranuras de reanudación](../images/en/resume-picker.jpg)

### 3.9 Arrancar juegos, RetroArch y aplicaciones

Arrancar un juego es lo que más vas a hacer, así que basta con un botón: selecciona el juego en la estantería y
pulsa **Cross**. Un juego de PS1 se abre a pantalla completa en el emulador de PS1 que elegiste en Opciones
(sección 3.6) y sigue en marcha hasta que salgas. Si prefieres jugar a un juego de PS1 en RetroArch (porque va
mejor ahí o porque te gustan sus opciones), pulsa **Square**.

**Salir de un juego.** En la PlayStation Classic, los botones de la propia consola hacen lo que esperas. **Reset**,
en la parte delantera, te devuelve al lanzador y guarda un punto de reanudación de donde estabas, para que puedas
seguir más tarde (sección 3.8); funciona incluso con el menú del juego abierto. **Power** apaga la consola. Una
Raspberry Pi o un PC no tienen esos botones, así que ahí se sale desde el menú del emulador, que te explicamos más
abajo.

Hay además una forma de salir que funciona igual con cualquier mando, sea el de la consola, uno USB o uno
Bluetooth: **mantén Start + Select, o Home, durante 2 segundos** y vuelves a AutoBleem. Una pulsación corta de
esos mismos botones abre, en cambio, el menú del emulador. El lanzador te recuerda las dos cosas en sus ayudas
(*Mantén Select+Start o Home 2 segundos: volver a AutoBleem* y *Pulsación corta de Select+Start o Home: el menú
del emulador*). Una aplicación no tiene menú de emulador, así que en ella solo sirve mantener pulsado. En la
consola, Reset siempre cierra también una aplicación.

**El menú del juego.** Con `pcsx-abnxt`, el emulador tiene un menú propio para lo que necesitas mientras juegas:
guardar, cambiar de disco, ajustar la imagen o elegir los mandos. Pulsa el botón de menú (Home en un mando que lo
tenga, **Select + Start** en uno que no, o **Esc** en un teclado) y el juego se pausa detrás del menú, con su
última imagen de fondo. Mantener el botón de menú pulsado 2 segundos hace lo mismo que Reset: sale del juego. El
menú tiene tres pestañas, y L1 y R1 pasan de una a otra. Recuerda dónde estabas, así que la próxima vez se abre en
la misma pestaña y la misma fila.

- La pestaña **Juego** trata del juego en sí. *Continuar el juego* cierra el menú y te deja seguir jugando. En
  *Partidas guardadas*, *Guardado rápido* guarda el momento en el que estás y *Carga rápida* te devuelve a él.
  *Cargar autoguardado* te lleva a cómo estaba el juego hasta 30 segundos antes: el emulador guarda esa copia en
  memoria mientras juegas, y te salva de un error que ya no tiene remedio. En *Disco CD*, *Cambiar de disco* sirve
  para un juego de varios discos cuando te pide el siguiente, y *Reiniciar el juego* lo empieza de nuevo.
  *Guardar ajustes para este juego* conserva los ajustes que has elegido para este juego concreto (sección 3.7).
  *Menú PCSX* abre las páginas propias de PCSX-ReARMed, con sus opciones, sus trucos y su información, y *Salir*
  te devuelve a AutoBleem.
- La pestaña **Imagen** te deja cambiar el aspecto del juego mientras lo ves: *Pantalla*, *Resolución* (1x o 2x),
  *Eliminar costuras*, *Tramado*, *Escalado*, *Halo de pantalla*, *Suavizado*, *Filtro*, *Máscara CRT*,
  *Scanlines* y *Brillo de las scanlines*. Son los mismos ajustes que en el editor de juego (sección 3.7), y cada
  fila tiene a la derecha una línea de ayuda que explica para qué sirve. *Pantalla* es la resolución de la
  pantalla; en la consola se elige en Opciones, y aquí solo se muestra. *Halo de pantalla* es para las franjas
  oscuras que quedan a los lados de una imagen 4:3 en una tele panorámica: las rellena con los propios bordes de
  la imagen, reflejados y oscurecidos, de modo que el juego parece desbordarse hacia ellas en lugar de quedar
  encajonado entre dos barras negras. *Máscara CRT* pone sobre la imagen el dibujo de los fósforos de un tubo
  antiguo: *Apertura* da las finas franjas de un Trinitron, y *Ranura* y *Delta*, los puntos de otros tubos. Solo
  está disponible con el filtro CRT (raster). El filtro CRT-Pi es demasiado pesado para la consola a 1080p. Una
  fila que no se aplica aparece en gris, y su línea de ayuda te explica por qué.
- La pestaña **Mandos** decide qué hay conectado a los dos puertos de la PlayStation, *Mando 1* y
  *Mando 2*: un mando estándar (digital), un mando analógico (DualShock), una pistola o nada. Algunos juegos
  solo funcionan con un tipo de mando concreto. El cambio se aplica al volver al juego.

El menú usa el mismo aspecto ab2.0.0 del lanzador, para que no parezca otro programa, y muestra la batería de tus
mandos y la imagen de tu último guardado rápido.

**Juegos de RetroArch.** Un juego de otro sistema arranca en RetroArch, con el núcleo que el lanzador ha elegido
para ese sistema. Cuando termines, *Close Content* o *Quit RetroArch* en el menú de RetroArch te devuelven al
lanzador. Si quieres cambiar el núcleo que usa un sistema, abre *Núcleos de RetroArch* en el menú rápido (sección
3.4); la lista se abre con el núcleo *PlayStation 1* arriba del todo. Y si quieres el menú propio de RetroArch (el
XMB) para sus ajustes y sus listas de contenido, elige *RetroArch* en el menú del sistema: RetroArch se abre
entonces sin nada cargado.

![La ventana de núcleos de RetroArch, con el núcleo PlayStation 1 arriba del todo](../images/en/retroarch-cores.jpg)

**Aplicaciones.** Las aplicaciones son programas, no juegos: las herramientas de la consola y, en la consola, las
aplicaciones extra que vienen con el paquete de RetroArch, como Doom, Quake, Amiga y otras. Las encontrarás en el
conjunto Aplicaciones. Antes de arrancar una aplicación, AutoBleem te muestra su ficha de información, para que
sepas qué es y cómo se maneja. Cross la arranca y Circle te devuelve a la estantería.

![La ficha de información de una aplicación, que aparece antes de arrancarla](../images/en/app-start.jpg)

**Los ajustes de una aplicación.** Muchas aplicaciones se escribieron para un mando concreto, así que puedes
cambiar cómo ven el tuyo. Selecciona la aplicación, abre la fila de iconos y elige *Juego*: se abren los *Ajustes
del juego* de la aplicación (*Change how this program is started*). *Modo de mando:* decide qué mando cree tener
la aplicación. *Automático* usa el que pide la propia aplicación; *Mando PSC* y *Mando Xbox 360* presentan tu mando
como el de la consola o como uno de Xbox 360, y *Mando PSC (sistema)* y *Mando Xbox 360 (sistema)* hacen lo mismo
a través del propio sistema. Prueba otro modo cuando una aplicación no responde a tu mando como debería.
*Cruceta como stick:* deja que la cruceta mueva el stick analógico, para una aplicación que solo hace caso al
stick, y *Stick como cruceta:* hace lo contrario.

Algunas aplicaciones te hacen una pregunta la primera vez que las abres. Una quiere saber *¿Qué controles tiene
tu mando?* para configurar sus controles: contesta *Una cruceta* si tu mando solo tiene la cruceta, o *Sticks
analógicos*. Una aplicación que ejecuta Windows pregunta *¿Qué quieres hacer?* y te ofrece ejecutar Windows,
instalarlo, ejecutar DOS o desinstalar Windows. Cuando una aplicación te deja configurar una tecla, te pide
*Pulsa uno de los botones.*

![Los ajustes de juego de una aplicación](../images/en/app-game-settings.jpg)

Un programa de Windows que ejecuta el PE runner (una aplicación PE, sección 3.3) se comunica contigo a través de
las pantallas de AutoBleem: un mensaje que quiere enseñarte aparece como *Mensaje*, y una pregunta con varias
respuestas como *Elige una opción*, cada una con el nombre de la aplicación como título.

![Una pregunta de una aplicación PE, mostrada como una pantalla de AutoBleem](../images/en/pe-dialog.jpg)

### 3.9a Un disco en una unidad USB

Puedes conectar una unidad de CD/DVD USB normal y corriente a la consola, a una Raspberry Pi o a un PC arrancado
desde la memoria de AutoBleem, y jugar directamente con un disco original de PlayStation, sin copiar nada. El
disco que metas aparece en el lanzador como un juego más. Esto no funciona en Windows.

**Copiar un disco a la memoria.** Si quieres tener el juego siempre a mano, sin el disco, pulsa Square (*Copiar
disco*). AutoBleem te pregunta primero si quieres copiar el juego y cuánto espacio va a ocupar, y luego lo guarda
en la carpeta `Games` como un único archivo CHD (un juego de varios discos lleva además un archivo `.m3u`, para
que el cambio de disco funcione dentro del juego). Mientras copia ves la velocidad y el tiempo que falta, y
*Abortar* detiene la copia. Cuando acaba, el juego está en la estantería como cualquier otro. AutoBleem no copia
un juego que ya está en `Games`, ni uno para el que no hay sitio; en ese caso te dice cuánto espacio necesita.
También se puede copiar un disco rayado: las partes que no se han podido leer se rellenan con ceros, y AutoBleem
te dice cuántas había. Una copia así puede funcionar o no.

Square te ofrece la copia para cualquier disco de juego de PlayStation en la vista del disco, aunque las bases de
datos de carátulas no lo conozcan. Un juego que las bases de datos conocen se copia con su título; si el juego
tiene varios discos, cópialos uno detrás de otro, y el `.m3u` los ordena empezando por el disco 1. Un disco que
las bases de datos no conocen recibe como nombre su número de serie, se copia como un solo disco y no tiene
carátula en la estantería. La ventana de copia, *Copiando el disco*, se queda en pantalla hasta que la copia
termina o se detiene (el lanzador espera mientras tanto) y muestra la velocidad como un múltiplo de una unidad de
CD normal. Si la copia falla, AutoBleem te dice por qué.

![Copiando un disco](../images/en/disc-copy.jpg)

**Jugar desde el disco.** Cuando metes un disco, la **vista del disco** se abre sola en cuanto se ha leído.
Muestra la carátula del disco (de las bases de datos de carátulas o descargada de internet) con su número de
serie y su título, y Cross arranca el juego. Un juego de PS1 que juegas desde el disco guarda sus puntos de
reanudación y sus partidas en una carpeta propia, así que puedes parar y seguir más tarde igual que con un juego
de la memoria. Después de jugar, o después de pasar por las opciones o por los ajustes de una extensión, vuelves a
la vista del disco. Si sales de ella con Circle para ver tus otros juegos, el disco sigue en la unidad y Circle en
la estantería te devuelve a la vista; en una estantería vacía, también la abre R1 (*Disco*). En una estantería
con juegos, R1 sigue haciendo lo de siempre: saltar de una inicial a otra. Cuando sacas el disco, la vista del
disco se cierra.

![La vista del disco](../images/en/disc-view.jpg)

**El indicador de la unidad**, arriba en la pantalla, te dice qué está haciendo la unidad, para que sepas si
tienes que esperar. Si no hay ninguna unidad conectada, no ves nada. Una unidad sin disco muestra un icono de
disco atenuado. Mientras se lee un disco, el icono parpadea y dice *Leyendo el disco...*, y cuando está listo se
ilumina con el título del disco. Si metes un disco que no es ni un juego de PlayStation ni un CD de audio, el
indicador dice *Este no es un disco de PlayStation*, y si la unidad no puede leer el disco en ese momento, dice
*No se puede leer el disco ahora*.

![El indicador de la unidad](../images/en/disc-chip.jpg)

**CD de audio.** La unidad también reproduce CD de música. Un CD de audio abre el **reproductor de CD** en lugar
de la vista del disco. Muestra el disco como *CD de audio*, con su lista de pistas y su duración total, y la línea
de debajo indica la pista seleccionada y si la repetición y el modo aleatorio están activados. Un disco que el
reproductor no puede reproducir aparece marcado como *Este disco no se puede reproducir*. Estos son sus botones:

| Botón | En el reproductor de CD |
|---|---|
| Cross | Reproduce la pista seleccionada. |
| Start | Pone la música en pausa y la reanuda. |
| Square | Detiene la música. |
| L1 / R1 | Pasa a la pista anterior o a la siguiente. |
| L2 / R2 | Retrocede o avanza dentro de la pista, de cinco en cinco segundos. |
| Triangle | Cambia lo que se repite: nada, el disco entero o la pista actual. |
| Select | Activa o desactiva el modo aleatorio, para que las pistas suenen en orden al azar. |
| Circle | Sale del reproductor de CD. |

![El reproductor de CD](../images/en/cd-player.jpg)

**Discos con LibCrypt.** Algunos juegos de PlayStation, sobre todo europeos, llevan una protección anticopia
llamada LibCrypt. Para ejecutarlos, el emulador necesita un pequeño archivo `.sbi` con los datos de esa
protección. AutoBleem descarga ese archivo de la web por su cuenta antes de jugar con uno de esos discos y cuando
lo copias, y el archivo se copia junto con el juego. Para eso necesita red: en una Raspberry Pi o en un PC, la
que ya tiene; en la consola, el WiFi que hayas configurado en PSC-Bios.

Para un disco en la unidad, algunos ajustes del juego no tienen sentido, así que su editor de juego pone esas
filas en gris (sección 3.7).

### 3.10 Añadir juegos

AutoBleem encuentra tus juegos solo, siempre que estén en el sitio correcto. En esta sección te contamos dónde va
cada tipo, para que cada escaneo los ponga en la estantería con su nombre y su carátula.

**Los juegos de PS1** van en la carpeta `Games`, **cada uno en su propia carpeta**, con el nombre del juego.
También puedes agrupar juegos en carpetas tuyas, y cada una de ellas se convierte en un grupo del selector de
conjuntos (sección 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                una carpeta de juegos: su propio grupo en el selector de conjuntos
    Klonoa/                   Klonoa.pbp
```

AutoBleem lee los formatos de imagen de disco habituales: `.cue` con su `.bin` (o `.img`), `.pbp`, `.chd`
(también los comprimidos con zstd), `.iso` y `.ecm`, que el escaneo descodifica por ti. Un juego en zip también
sirve: el procesador **Unzip** lo descomprime antes de que el escaneo lo lea (sección 3.14).

No hace falta ser ordenado. Un juego de varios discos va en una sola carpeta con todos sus discos, pero si copias
carpetas llamadas `Game (Disc 1)`, `Game (Disc 2)` y así sucesivamente, el escaneo las junta en una sola carpeta
`Game`. Los juegos que dejes sueltos directamente en `Games/` también los reparte el escaneo en carpetas propias.

**Los nombres y las carátulas** llegan solos. El escaneo lee el número de serie de cada disco y saca el título, la
editorial, el año, el número de jugadores y la región de la base de datos de PlayStation de RetroArch o de las
bases de datos de carátulas. Si quieres una carátula tuya, pon un PNG o un JPEG junto a la imagen del juego, con
el mismo nombre. Si no, la carátula sale de las bases de datos de carátulas o, con RetroArch instalado, de las
miniaturas de libretro; en una Raspberry Pi, un PC o Windows, una carátula que falta se descarga de internet
(Opciones → *Obtener carátulas en línea*). Si el escaneo se equivoca en algo, corrígelo en el editor de juego y
activa *Bloquear datos*, para que el siguiente escaneo respete tu cambio.

**Los juegos de otros sistemas** van en `RetroArch/roms/`, **una carpeta por sistema, con el nombre que le dan
las bases de datos de RetroArch**: por ejemplo `Nintendo - Nintendo Entertainment System`, `Nintendo - Super
Nintendo Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` o `FBNeo - Arcade
Games` (o `Arcade`). Las carpetas ya vienen creadas, y las ROM pueden quedarse en zip. En una Raspberry Pi, un PC
o Windows, el escaneo las lee por su cuenta y escribe las listas de reproducción de RetroArch. La memoria de una
consola no puede hacerlo sola, así que ahí tienes que pasar **UpdateRoms** en el PC (capítulo 5).

**Las aplicaciones** van en `Apps/<nombre>/`, cada una con un `app.ini` (su nombre, su icono y qué ejecutar) y un
`run.sh`.

**Paquetes.** Algunas aplicaciones son motores de juego: necesitan los datos de un juego que tengas para poder
jugarlo. Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, juegos de
DOS y otros funcionan así. Pon los archivos del juego en una carpeta `Packages` de la memoria, una carpeta por
juego (por ejemplo `Packages/Doom/DOOM2.WAD`), y AutoBleem los reconoce gracias a una tabla que trae incluida
(`rc/packages.ini`). En una carpeta que reconoce, cada archivo de juego suelto es un paquete por sí mismo.
AutoBleem solo lee tus archivos y nunca los modifica. Un paquete también puede venir de la Tienda (sección 3.13).

Donde el lanzador la muestra, la fila *Paquetes* de la pestaña Aplicaciones (sección 3.3) recoge los datos de
juego encontrados. Cross sobre una entrada abre su **Package info**: qué contienen los datos, una descripción,
dónde están los archivos y de dónde vienen (tus propios archivos, la Tienda, un mod o archivos incluidos en una
aplicación), si son shareware o libres, y qué aplicación instalada los ejecuta. Si no tienes instalado nada que
pueda ejecutarlos, la ficha te lo dice.

Cuando arrancas una aplicación de motor, AutoBleem busca datos de juego que pueda ejecutar. Si solo hay un
conjunto de datos, el juego arranca al momento. Si hay varios, una lista (*Elegir los datos del juego*) te
pregunta a cuál quieres jugar, y se abre en el que elegiste la última vez. Si no hay ninguno, AutoBleem te dice
qué datos necesita la aplicación y dónde ponerlos, y no arranca nada.

**Tus propios juegos.** Cuando AutoBleem no reconoce unos datos, su Package info dice *No reconocido. Si es un
juego, consulta el manual: Tus propios juegos.* La tabla solo conoce los juegos para los que se hizo. Para otro
distinto, escribe una fila para él en un `packages.ini` tuyo dentro de la carpeta `Packages`: AutoBleem lee el
tuyo primero, así que tus filas mandan.

![El selector de paquetes, donde eliges con qué datos de juego empezar](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Escanear solo una parte.** Si solo has añadido juegos a un conjunto o a una carpeta, *Reescanear juegos* puede
escanear únicamente esa parte, lo que es más rápido que escanearlo todo, y su burbuja desaparece al terminar.

**Los temas** van en `Themes/<nombre>/`, con su `theme.json` y sus imágenes; también puedes dejar el zip del tema
en `Themes/` tal cual.

### 3.11 La BIOS de PS1

La BIOS es el programa de arranque propio de la PlayStation, y el emulador reproduce los juegos con más
fidelidad con la BIOS auténtica. En una **PlayStation Classic** no tienes que hacer nada: el emulador usa la BIOS
de la propia consola. En una **Raspberry Pi, un PC o Windows**, pon tus propios archivos de BIOS de PS1 en
`System/Bios/`: `romw.bin` (la SCPH-5501/5502 de EE. UU./Europa) y `romJP.bin` (la SCPH-5500 japonesa, que se usa
para los juegos japoneses). Los instaladores los rellenan con los paquetes de BIOS de RetroArch, salvo que ya
estén ahí tus propios archivos: nunca sustituyen los tuyos. Sin ellos, el emulador funciona con su BIOS HLE
integrada, un sustituto que muchos juegos aceptan y otros no; así que, si un juego no arranca, lo primero que
debes comprobar es si falta la BIOS.

### 3.12 Actualizaciones

AutoBleem se mantiene al día por su cuenta, así que tienes las novedades y las correcciones sin reinstalar nada.
Al arrancar el lanzador, y después una vez al día, consulta en la web si hay una versión nueva en su **canal**. El
canal se elige en Opciones → *Actualizaciones*: `release`, `testing`, `nightly`, u `off` si no quieres que busque
nada. Si no quieres esperar a la comprobación diaria, *Actualización de software* en el menú del sistema lo
comprueba en el momento.

Cuando hay una versión nueva, AutoBleem te pregunta qué hacer. *Actualizar ahora* la descarga y la instala, lo que
lleva unos minutos. *Recordar mañana* te lo vuelve a preguntar al día siguiente, y *Omitir esta versión* no vuelve
a preguntarte por esa versión. Elijas lo que elijas, tus juegos, partidas y ajustes se quedan siempre; después de
una actualización, el lanzador vuelve a escanear tus juegos. La etiqueta del canal en la esquina superior
izquierda (sección 3.1) te dice qué versión tienes.

Cómo se instala la actualización depende de la máquina:

- En una **Raspberry Pi** y en la **memoria USB para PC**, después de la descarga vuelve a ejecutarse el
  instalador, con la misma pantalla de progreso que en el primer arranque, y te ofrece también un RetroArch más
  nuevo. Después vuelve el lanzador.
- En **Windows** se abre el instalador descargado, instala la versión nueva y arranca el nuevo lanzador.
- En una **PlayStation Classic**, solo se puede actualizar sola una consola con el **kernel de AutoBleem**
  (ABFlashKit, sección 6.2) y una **red WiFi** configurada en PSC-Bios (sección 6.1); una consola de serie no
  tiene red, así que el lanzador ni siquiera busca. Después de *Actualizar ahora*, el lanzador se cierra y la
  imagen de AutoBleem se queda en pantalla mientras se actualiza la memoria, lo que lleva unos minutos; luego
  arranca el nuevo lanzador. Sin red, *Actualización de software* te dice *No conectado*. Cualquier memoria de
  consola se puede actualizar también desde un PC con `AutoBleemInstaller.exe` (sección 2.1).

### 3.13 Extensiones y la Tienda de AutoBleem

**Las extensiones** añaden cosas nuevas al lanzador, con sus propias pantallas y funciones, sin modificar el
propio AutoBleem. La Tienda de AutoBleem y PSC-Bios son extensiones. Cada extensión vive en `Extensions/<nombre>/`
en la memoria (en una Raspberry Pi, en su partición de datos; en Windows, en la carpeta de datos); para instalar
una, descomprime su zip ahí.

Para verlas, abre el menú del sistema (**L2 + R2**) y elige *Extensiones*. Las que vienen del equipo de AutoBleem
están arriba, y las demás aparecen debajo, bajo *Extensiones de terceros*. Cross abre la seleccionada y Triangle
la desactiva o la vuelve a activar. PSC-Bios en la consola es la excepción: con ella configuras el WiFi, los
mandos y el reloj, así que ahí no se puede desactivar. Cuando una extensión no puede funcionar, su fila te dice
por qué: necesita red y no la hay, no está hecha para este sistema, se hizo para otra versión de AutoBleem y
necesita una actualización, o no se ha podido cargar. Si alguna vez una extensión hace que el lanzador se cierre,
AutoBleem la desactiva y la lista te lo indica; puedes volver a activarla desde aquí.

![La lista de extensiones](../images/en/extensions.jpg)

**La Tienda de AutoBleem** es la primera extensión: un sitio donde ver aplicaciones y juegos e instalarlos con
una sola pulsación, en todos los sistemas en los que funciona AutoBleem. Una PlayStation Classic necesita para
ello el kernel de AutoBleem, porque el WiFi llega con el kernel. Se abre desde el menú rápido (*Tienda*, sección
3.4). Tiene cuatro pestañas, y L1 y R1 pasan de una a otra.

Las pestañas **Apps** y **Games** muestran lo que ofrecen las fuentes, cada elemento con su imagen, su versión, su
tamaño y el pequeño icono de la fuente de la que viene. La pestaña Apps muestra también las aplicaciones PE, con
su licencia y su origen, y los paquetes de datos de juego (sección 3.10). Lo que ya tienes instalado lleva la
insignia *Installed*. La barra de ayuda muestra los botones que sirven para la fila seleccionada:

| Botón | En las pestañas Apps y Games |
|---|---|
| Cross | Instala el elemento; o lo actualiza, lo vuelve a intentar tras un fallo, o cancela una descarga que está esperando o en curso. |
| Triangle | Quita algo que instaló la Tienda. |
| Square | Actualiza las listas desde las fuentes. |
| L2 / R2 | Saltan a la inicial anterior o siguiente. |
| Select | Muestra una sola fuente cada vez, cuando quieres ver lo que ofrece solo esa fuente. |
| Start | Busca en los títulos. |

Las imágenes se guardan una vez cargadas, así que la próxima vez las listas aparecen rápido, y una imagen que no
se cargó se puede volver a intentar.

La pestaña **Downloads** muestra lo que se está descargando, lo que espera, lo que ha fallado y lo que ya está
instalado, con una barra de progreso que avanza de forma continua. No tienes que estar pendiente: las descargas
siguen en segundo plano, también cuando sales de la Tienda, y mientras estás en otra parte del lanzador una
burbuja muestra la descarga en curso con su velocidad y el tiempo que falta (por ejemplo `1.4 MB/s · 0:42`).
Arrancar un juego o apagar solo las pone en pausa, y una descarga interrumpida sigue donde se quedó. Si se cae la
red, el elemento dice *Waiting for the network* y continúa desde donde iba cuando vuelve la red; tras 30 minutos
sin red, se da por vencido. Las descargas de más de 2 GB funcionan en todas las plataformas, también en las
versiones de 32 bits. Un juego que instales aparece en la estantería después del siguiente escaneo, con la imagen
de la Tienda como carátula.

La pestaña **Sources** muestra de dónde vienen las listas, cada una con su icono: el catálogo propio de AutoBleem,
cualquier lista TSV que dejes en `System/Extensions/store/sources/` y las direcciones que añadas tú mismo con
*Add a source URL*. Cross sobre una fuente que hayas añadido te deja cambiarle el nombre o la dirección, pasarla
de `http://` a `https://` o al revés, o quitarla.

![La pestaña Apps de la Tienda](../images/en/store-apps.jpg)

![El menú de una fuente que has añadido](../images/en/store-source-menu.jpg)

Lo que ofrece el catálogo propio de AutoBleem aparece también en la web de descargas, en
`https://autobleem.retromenele.pl/store/`. Una fuente que añadas tú es otra cosa: **tú eres responsable de lo que
contienen las fuentes que añades.**

**Tus propios juegos en tu red.** Si guardas tus juegos de PS1 en otro ordenador de casa, `abstored`, el servidor
de red local de la Tienda, puede ofrecérselos a la Tienda a través de tu red, para que los instales como
cualquier otro elemento. Funciona en cualquier máquina Linux (una Raspberry Pi, un servidor doméstico) y solo lee
la carpeta, sin modificarla nunca. Arráncalo con `abstored <carpeta de juegos>` y abre
`http://<esa máquina>:8124/` en un navegador: la página muestra lo que sirve y cualquier problema que haya
encontrado. En la Tienda, añade `http://<esa máquina>:8124/store.tsv` como fuente. En la página de la Tienda, en
su pestaña **LAN server**, tienes programas listos para Linux y Windows, y `INSTALL-linux.md`
(`ext_store/server/` en el código fuente) explica cómo configurarlo como servicio. **LAN Share** (sección 5.2)
lleva a ese servidor juegos y discos desde un PC.

### 3.14 Procesadores de escaneo

Los procesadores de escaneo preparan tus juegos antes de que AutoBleem los lea. Un procesador es un pequeño
programa que cada escaneo ejecuta primero. Puede convertir un formato que AutoBleem no lee en otro que sí (por
ejemplo, descomprimir un juego en zip) o cambiar los datos de un juego, como aplicar un parche de traducción. Los
procesadores viven en `System/Processors/<nombre>/` en la memoria (en una Raspberry Pi, en su partición de datos;
en Windows, en la carpeta de datos); para instalar uno, descomprime su carpeta ahí, y el siguiente escaneo lo
ejecutará.

**Unzip viene con AutoBleem.** Descomprime los juegos de PS1 en zip que haya en `Games/` antes de que el escaneo
los lea, y las ROM en zip de una en una; los sets de recreativa se quedan en zip, porque así es como los leen los
núcleos de recreativas. Al actualizar AutoBleem también se actualiza Unzip, y si lo habías desactivado, sigue
desactivado.

Un procesador hace su trabajo una sola vez: cuando ya se ha ocupado de un juego, no vuelve a ejecutarse con él
hasta que el juego cambie. Mientras un procesador trabaja, la burbuja de arriba a la derecha muestra lo que hace,
y si hay un aviso o un fallo aparece en la línea de debajo; los detalles están en `processors.log`, en la carpeta
de registros. Arrancar un juego o RetroArch detiene un procesador que modifica archivos, para que el juego tenga
la máquina para él solo, y el siguiente escaneo termina el trabajo.

Para gestionarlos, abre el menú del sistema (**L2 + R2**) y elige *Procesadores de escaneo*. Los ves en el orden
en que se ejecutan, con una pestaña para los juegos de PS1 y otra para las ROM; L1 y R1 cambian de pestaña. El
orden importa: un procesador que descomprime tiene que ir antes que uno que parchea lo descomprimido.

| Botón | En Procesadores de escaneo |
|---|---|
| Square | Coge el procesador seleccionado, para que Arriba y Abajo lo lleven a su nuevo sitio; Square lo vuelve a soltar. |
| Cross | Desactiva el procesador, o lo vuelve a activar. |
| Triangle | Hace que el procesador vuelva a revisar todos los juegos en el siguiente escaneo, también los que ya había tratado. |
| Circle | Vuelve atrás, y lanza un escaneo si has cambiado algo. |

Un procesador hecho para otra máquina sigue en la lista, en gris, para que veas que está ahí pero que aquí no se
ejecuta.

![Procesadores de escaneo](../images/en/processors.jpg)

Si quieres escribir tu propio procesador, la página de Unzip, `https://github.com/autobleem2/proc_unzip`, explica
todo lo que tiene que hacer un procesador, y `tools/proc_check.py`, en el código fuente de AutoBleem, revisa el
tuyo antes de que lo compartas.

<!-- pagebreak -->

## 4. Pantallas

### 4.1 Administrador de Juegos

El Administrador de Juegos es donde pones orden en tu biblioteca de PS1. Úsalo cuando quieras quitar un juego al
que ya no juegas, abrir los ajustes de un juego sin buscarlo antes en la estantería o hacer que AutoBleem vuelva a
buscar todas las carátulas. Se abre desde el menú del sistema (L2 + R2, *Administrador de Juegos*). Mientras hay
un escaneo en marcha aparece en gris, y espera a que el escaneo termine.

La pantalla se titula *Administrador de juegos - Elige juego*. A la izquierda ves todos tus juegos de PS1 en una
lista de títulos por orden alfabético; a la derecha, la carátula del juego seleccionado con su editorial, su año,
su número de serie y la carpeta en la que está. Arriba a la derecha se muestra el espacio libre que queda en la
unidad, para que veas cuánto sitio recuperas al borrar. Arriba y Abajo recorren la lista, L2 / R2 pasan página y
L1 / R1 saltan al primer o al último juego.

- **Cross** abre el juego seleccionado en el editor de juego, el mismo que abre el icono Juego en la estantería
  (sección 3.7). Al salir, vuelves al mismo juego de la lista.
- **Square borra el juego.** AutoBleem te pregunta primero y luego elimina la carpeta entera del juego. Si sus
  estados guardados y su tarjeta de memoria no los usa ningún otro juego, te hace una segunda pregunta: si
  quieres borrarlos también. Di que no si crees que algún día querrás recuperar el juego con tus partidas.
- **Triangle borra todas las carátulas** (PNG o JPEG) que haya junto a tus juegos, tras preguntarte. Viene bien
  cuando has ido juntando carátulas que no te gustan: el siguiente escaneo vuelve a sacarlas de las bases de datos
  de carátulas.

Al final de la lista, después de los juegos, puede que veas carpetas marcadas como *No añadido*. Son carpetas de
`Games` que el escaneo revisó pero no pudo convertir en un juego. Selecciona una y la parte derecha te dirá dónde
está y por qué no se añadió; por ejemplo, porque le falta el archivo cue (capítulo 7). Square borra esa carpeta,
tras preguntarte. Si sales con Circle después de haber cambiado algo, AutoBleem vuelve a escanear los juegos.

![El Administrador de Juegos: la lista de juegos a la izquierda, y la carátula y los datos del juego seleccionado a la derecha](../images/en/game-manager.jpg)

### 4.2 Información de hardware

Información de hardware es la página que tienes que mirar cuando quieres saber qué máquina tienes y qué ve:
cuánto espacio queda en la memoria, qué dirección de red tiene, qué controladores de vídeo y de audio usa y qué
mandos hay conectados. Es la misma página en todas las plataformas, incluida la consola. Se abre desde el menú
del sistema (L2 + R2, *Información de hardware*); Circle te devuelve al menú del sistema.

La página muestra el sistema, el hardware, el almacenamiento con su espacio libre, las direcciones de red, los
controladores de vídeo y de audio y los mandos conectados. Lo vuelve a leer todo cada segundo, así que puedes
dejarla abierta mientras conectas un mando o un cable y ver cómo aparece el cambio. Solo muestra información: para
configurar la red o un mando, usa *Red y mandos* (PSC-Bios, capítulo 6).

La parte de los mandos responde a la pregunta "¿qué mando es cada jugador?". Los dos primeros mandos aparecen como
*Jugador 1* y *Jugador 2*, los puertos que les da el emulador de PS1. Cualquier mando más aparece como *no
utilizado por el emulador de PS1*. RetroArch reparte los puertos según sus propios ajustes, así que en un juego de
RetroArch el orden puede ser otro. No hace falta que abras esta página cada vez: siempre que conectas o
desconectas un mando, el lanzador te muestra un momento cuál es ahora el jugador 1 y cuál el jugador 2.

![Información de hardware: los datos de la máquina y los mandos conectados](../images/en/hardware-info.jpg)

### 4.3 La guía de botones

Si no recuerdas para qué sirve un botón en algún sitio, pulsa **Triangle** en la estantería. La guía de botones
muestra todos los botones de todas las pantallas en una sola página, para que lo consultes sin salir del
lanzador. Si hay un teclado USB conectado, o se ha usado uno, una columna *Teclado* muestra la tecla que
corresponde a cada botón del mando.

La guía también te recuerda lo único que conviene tener presente en cualquier juego: cómo salir de él. Mantén
Select + Start, o Home, durante 2 segundos para volver a AutoBleem; una pulsación corta abre, en cambio, el menú
del emulador.

![La guía de botones: los botones de cada pantalla, con las teclas al lado](../images/en/button-guide.jpg)

### 4.4 El teclado en pantalla

Siempre que AutoBleem necesita que escribas algo (el nombre de un conjunto de tarjetas de memoria, el título de un
juego, una contraseña de WiFi, la dirección de una fuente de la Tienda), aparece el mismo teclado en pantalla,
para que puedas escribir solo con el mando. Está distribuido como el teclado de un móvil. Además de las letras,
tiene una página de símbolos, con `/ \ : ? & = % @ #` y el resto de lo que hace falta para una dirección o una
contraseña, y dos páginas de letras con tilde y otros acentos. En la fila de abajo están Mayús, la tecla que
cambia de página, Espacio, Borrar y Confirmar.

Muévete por las teclas con las direcciones y pulsa **Cross** para escribir la que está bajo el cursor.
**Triangle** borra una letra y **Square** escribe un espacio. **L1** es Mayús; púlsalo dos veces para bloquear
las mayúsculas. **R1** pasa a la siguiente página de teclas, y **L2 / R2** mueven el cursor dentro del texto.
**Start** confirma lo que has escrito y **Circle** lo cancela. Si hay un teclado USB conectado, puedes escribir
con él en cualquier momento: Intro confirma y Esc cancela.

![El teclado en pantalla](../images/en/keyboard.jpg)

### 4.5 Mando virtual

Las aplicaciones (los programas del conjunto Aplicaciones, como Doom o Quake) no leen tu mando por sí mismas. Un
pequeño programa auxiliar, el demonio del mando virtual, lee los mandos reales y le da a cada aplicación un mando
que entiende. Esta página te muestra qué mandos ve ese programa y cómo los lee. Mírala cuando una aplicación no
responde a tu mando o tiene los botones cambiados. Se abre desde el menú del sistema (L2 + R2, *Mando virtual*);
Circle te devuelve al menú del sistema.

En *Mandos que ve el demonio* aparece cada mando con un número y su nombre. Al lado puedes leer tres cosas: si el
programa ha podido abrir el mando (*conectado*) o no (*no se puede leer*); el controlador por el que llegó el
mando; y de dónde sale la distribución de sus botones. *de la base de datos de mandos* quiere decir que el mando es
conocido y sus botones están donde deben; *adivinado por el demonio* quiere decir que no lo es y que el programa
ha hecho lo que ha podido. Si en una aplicación los botones parecen estar mal, lo más probable es que la
distribución sea adivinada.

El programa auxiliar solo funciona mientras hay una aplicación en marcha, así que la página le pregunta una vez
al abrirse. Si conectas un mando con la página abierta, pulsa **Cross** (*Buscar de nuevo*) para volver a
preguntar. En Windows no existe ese programa, y la página dice *No está en esta versión*.

![Mando virtual: los mandos que ve el programa auxiliar de las aplicaciones](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. En el PC

### 5.1 UpdateRoms: poner al día la memoria de la consola

En una Raspberry Pi, un PC o Windows, el escaneo del lanzador ordena tus juegos de RetroArch en listas y descarga
sus carátulas por su cuenta. La PlayStation Classic no puede hacerlo, porque no tiene red propia. **UpdateRoms**
hace ese trabajo en tu PC con Windows: usa la red del PC, pero lo escribe todo con las rutas que espera la
consola, de modo que, cuando vuelves a conectar la memoria, la consola arranca y lo encuentra todo en su sitio.
Pásalo cada vez que añadas o quites juegos de RetroArch en la memoria de una consola.

1. Copia tus ROM en la memoria, dentro de `RetroArch/roms/<sistema>/` (sección 3.10). Los nombres de las
   carpetas tienen que ser los de las bases de datos de RetroArch; el instalador ya ha creado los más comunes.
2. Abre **`UpdateRoms\UpdateRoms.exe` desde la propia memoria**; el instalador lo dejó ahí. Averigua por sí solo
   en qué memoria está. Mientras trabaja, ves una línea que dice lo que está haciendo, una barra de progreso y un
   registro.
   - Si la memoria todavía no tiene la base de datos de RetroArch, primero descarga el paquete de bases de datos
     de RetroArch. Luego identifica con él cada ROM, para que un juego que la base de datos conoce reciba su
     nombre correcto.
   - Escribe una lista de reproducción por sistema en `RetroArch/bin/playlists/`, con las rutas de la consola. Lo
     que el propio RetroArch hubiera añadido a esas listas se conserva.
   - Para cada ROM sin carátula, descarga una de los servidores de miniaturas de libretro en
     `RetroArch/bin/thumbnails/`.
3. Extrae la memoria de forma segura y vuelve a conectarla a la consola. La pestaña RetroArch del selector de
   conjuntos muestra ahora todos los sistemas que tienen juegos.

Puedes pasarlo tantas veces como quieras: se salta las carpetas en las que no ha cambiado nada, así que una
segunda pasada es rápida. Si algo sale mal, el registro está en `System/Logs/updateroms.log`, en la memoria. La
tarjeta de una Raspberry Pi metida en un lector de tarjetas se puede poner al día igual, con
`UpdateRoms.exe <unidad> --target rpi`, aunque una Pi lo hace sola cuando tiene red.

### 5.2 LAN Share: tus juegos y discos en el servidor de tu red

La Tienda puede instalar juegos desde un servidor de tu propia red doméstica (sección 3.13). **LAN Share** es el
programa de Windows que llena ese servidor desde tu PC: sube al servidor los juegos de PS1 que tienes en el PC, y
también puede leer un disco de PS1 en la unidad de CD/DVD del PC y llevarlo allí. El servidor es un `abstored`
que funciona en una Raspberry Pi, un NAS u otro PC. Cuando un juego está en él, la Tienda de la consola, de la Pi
o del PC puede instalarlo desde ahí.

`LanShare.exe` lo tienes en la página de la Tienda, en su pestaña **LAN server**. No hay nada que instalar:
ábrelo, y guardará sus ajustes en `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![La ventana de LAN Share: los juegos del servidor a la izquierda, los de este PC a la derecha](../images/en/lanshare.jpg)

1. **Conéctate al servidor.** Escribe su dirección tal como la tiene la Tienda, `http://<su dirección>:<puerto>`,
   y pulsa **Connect**. A la izquierda aparecen los juegos que ya están en el servidor y cualquier problema que
   haya encontrado su propio escaneo. Para subir juegos al servidor, LAN Share necesita una de estas dos vías de
   acceso:
   - **Share** es la carpeta de juegos del servidor tal como se comparte en tu red (Samba), por ejemplo
     `\\raspberrypi\games`. LAN Share copia los juegos en ella y le pide al servidor que escanee; el servidor
     sigue limitándose a leer su carpeta.
   - **Token** es para un servidor arrancado con `--allow-uploads`. Escribe su token: el servidor lo muestra al
     arrancar y lo guarda en `<state>/upload-token`. LAN Share sube entonces los juegos por HTTP, y una subida
     que se corta a medias continúa desde donde se quedó.
2. **Publica los juegos de tu PC.** Elige la carpeta en la que están tus juegos (una carpeta por juego), marca los
   que quieras y pulsa **Publish the ticked games**. **On the server** te indica si el servidor ya tiene un juego
   (compara el número de serie, o el título si no hay número de serie), y un juego que el servidor ya tiene no se
   envía nunca dos veces. **Tick those not on the server** marca por ti todos los demás.
3. **Publica un disco.** Mete un disco de PS1 en la unidad del PC y pulsa **Read a disc and publish it**. LAN
   Share lee el disco entero y lo guarda como `.bin` + `.cue`, con el título del juego como nombre. En un juego
   con LibCrypt escribe también el archivo `.sbi`, si la unidad puede leer el subcanal. Si has elegido las bases
   de datos (más abajo), comprueba la copia comparándola con el volcado bueno conocido. Después publica el juego.
   Para un juego de varios discos, marca antes **The game has more than one disc**: LAN Share te irá pidiendo cada
   disco siguiente y los publicará juntos como un solo juego.
4. **Quita juegos del servidor.** Selecciónalos y pulsa **Remove from the server...**. No se borra nada: cada
   juego se mueve a una carpeta `.removed` junto a los juegos del servidor, y si lo vuelves a mover, vuelve a
   estar disponible.

Las **Databases** son opcionales. Si le indicas a LAN Share la carpeta de carátulas de AutoBleem
(`coversU/P/J.db`) y el `Sony - PlayStation.rdb` de RetroArch, las usa para poner nombre a los juegos y para
comprobar un disco que ha leído.

Si prefieres no copiar nada, marca **Also share the games on this PC with the Store** (viene desactivado): LAN
Share sirve entonces directamente a la Tienda la carpeta de juegos de tu PC. La primera vez que lo hagas, Windows
te preguntará por su cortafuegos; permite solo las redes privadas.

<!-- pagebreak -->

## 6. Las herramientas de la consola (PlayStation Classic)

Con la memoria de una PlayStation Classic vienen dos herramientas que te ayudan a sacarle a la consola más de lo
que trae de fábrica. Las dos tienen el mismo aspecto que el resto del lanzador, con su tema y su idioma, y se
manejan con el mando; el asistente de mandos, también con los botones frontales de la consola. **PSC-Bios** es
una extensión que viene con el paquete de la consola: la abre la opción *Red y mandos* del menú rápido y del menú
del sistema, y también la encuentras en la lista de Extensiones. **ABFlashKit** es una aplicación, dentro del
conjunto Aplicaciones.

### 6.1 PSC-Bios

PSC-Bios es donde conectas la máquina con el mundo: tu red WiFi, la zona horaria, los mandos Bluetooth y la
distribución de botones de un mando que AutoBleem no conoce. Viene con el paquete de la consola y también está en
una Raspberry Pi y en la memoria USB para PC. Se abre con *Red y mandos* en el menú del sistema (o en el menú
rápido), o desde la lista de Extensiones. Si la extensión está instalada pero desactivada, la opción *Red y
mandos* aparece en gris y dice que *está desactivada - actívala en Extensiones*; pulsa Cross sobre ella y la lista
de Extensiones se abre en PSC-Bios, para que puedas volver a activarla.

La primera pantalla te da una visión de conjunto: la hora y la zona horaria, los adaptadores de red (WiFi,
Ethernet, Bluetooth) con sus direcciones y todos los mandos conectados, con una nota que indica si tienen
asignación de botones. En la consola, las partes de red y de Bluetooth necesitan el kernel de AutoBleem (sección
6.2); en una Raspberry Pi o en la memoria USB para PC usan las herramientas propias del sistema. El asistente de
mandos funciona en todas partes.

![PSC-Bios: el centro de Red y mandos](../images/en/pscbios-main.jpg)

Desde la primera pantalla, cada parte está a un botón de distancia:

| Botón | Qué abre |
|---|---|
| Select | **Wi-Fi Network** te conecta a tu WiFi (a través del kernel, o de NetworkManager en una Pi o un PC): escribe el nombre de la red o elígela de una búsqueda, introduce la contraseña, elige el modo del controlador y pulsa *Apply / Restart Network*. Aquí también se fija la zona horaria, y una vez conectado ves la dirección IP de la consola. |
| Square | **Bluetooth Controllers** busca mandos Bluetooth como el DualShock 4, para que puedas emparejar uno nuevo o quitar uno que ya no usas. |
| L1 | **DualShock 3 Pairing** conecta tu primer DualShock 3, que para esto tiene que estar enchufado por USB, a través del plugin sixaxis del kernel. |
| R1 | **Controller Mapping** abre el asistente de mandos, que te explicamos a continuación. |
| Triangle | **About** te cuenta qué es PSC-Bios. |
| Circle | **Back** te saca de PSC-Bios y te devuelve al lanzador. |

**El asistente de mandos.** Úsalo cuando un mando no hace nada en AutoBleem o tiene los botones en el sitio
equivocado. Muestra el mando conectado tal como es en realidad (cada eje, botón y cruceta como números) y un
dibujo de un DualShock que se ilumina según pulsas. Como todavía no te puedes fiar del mando que estás probando,
el asistente se maneja con los **botones frontales** de la consola: **RESET** pasa al siguiente mando, **OPEN**
empieza la asignación y **POWER** cancela o sale. Durante la asignación, el asistente te va pidiendo los botones
uno tras otro: pulsa el que está iluminado en el dibujo, u OPEN si tu mando no tiene ese botón. Una pulsación
corta se asigna de la forma habitual.

También puedes salir desde el mando: mantén Circle 2 segundos; una barra se va llenando y el pie de la pantalla
dice *Hold 2 s: Exit*. Mientras el mando todavía no tiene asignación, mantener cualquier botón 2 segundos hace lo
mismo (*Hold any button 2 s: Exit*). En un teclado, Esc, Espacio e Intro hacen de POWER, RESET y OPEN.

Al final, la nueva asignación se pone en uso para que puedas probarla, y OPEN la guarda con el nombre que elijas.
A partir de ahí, el lanzador la carga siempre.

![PSC-Bios: el asistente de asignación de mandos](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit: el kernel de AutoBleem

El kernel de AutoBleem sustituye al kernel de Linux original de la consola, y es opcional. Te interesa si quieres
sacarle más partido a la consola: le da un reloj que funciona, hace funcionar los adaptadores USB de WiFi y de
Bluetooth (para PSC-Bios y los mandos Bluetooth) y añade el soporte de los botones frontales que usa el emulador
para los puntos de reanudación. ABFlashKit es la herramienta que lo instala. Antes de nada hace una copia de
seguridad de la consola, y también puede devolverla a su estado original mediante la recuperación propia de Sony.

> **Esta herramienta escribe en la memoria flash de la consola.** Si la escritura se interrumpe (se va la luz o
> se saca la memoria USB), puede que la consola no vuelva a arrancar; además, instalar un kernel modificado anula
> su garantía. Mantén la consola enchufada y la memoria puesta hasta que la consola se reinicie sola. ABFlashKit
> se abre con esta advertencia: *I understand* continúa y *Quit* sale.

![El menú de ABFlashKit](../images/en/abflashkit-menu.jpg)

ABFlashKit tiene tres acciones:

- **Flash Kernel** instala el kernel. Si en la memoria todavía no hay una copia de recuperación, primero hace una
  de las particiones de la consola (`LBOOT.EPB`). Comprueba la copia y la imagen del kernel, escribe el kernel y
  los archivos de sistema de AutoBleem y reinicia la consola. Cuando diga *All done - when the screen goes black
  replace power cord*, espera a que la pantalla se quede en negro, desenchufa el cable de alimentación de la
  consola y vuelve a enchufarlo.
- **Full backup** guarda las cuatro particiones de la consola en `LBOOT.EPB`, para que puedas restaurarlas más
  adelante. Si ya hay una copia, te pregunta antes de sobrescribirla.
- **Restore Mode** es el camino de vuelta al firmware original. Comprueba que la copia que hay en la memoria sea
  de una consola original, activa el indicador de recuperación y reinicia en la recuperación de Sony, que
  restaura la consola a partir de `LBOOT.EPB`.

Bajo cada paso, una barra de progreso te muestra cómo va. ABFlashKit no instala nada en una consola que tenga otro
firmware modificado, como BleemSync o Project Eris: primero devuelve esa consola a su estado original.

**Entrar desde un PC.** Si sabes de Linux y quieres ver la consola por dentro, puedes entrar en ella desde un PC
con un cable USB. Para esto hace falta el kernel de AutoBleem; en una consola de serie no funciona.

1. Conecta el puerto micro-USB de la consola al PC con un cable USB. El PC ve la consola como un adaptador de red
   nuevo, y la dirección de la consola la encuentras en los ajustes de ese adaptador en el PC.
2. Entra con `ssh root@<dirección de la consola>`. La contraseña por defecto es `autobleem`.

En lugar de la contraseña puedes usar una clave. Pon tu clave pública en el archivo `System/ssh/authorized_keys`
de la memoria y reinicia la consola: en el siguiente arranque se añade a la cuenta root. Actualizar o reinstalar
el lanzador no la quita.

> **La contraseña por defecto es la misma en todas las consolas**, así que cualquiera que pueda conectar un cable
> a la tuya puede entrar como root. Usa una clave siempre que puedas, y no dejes una consola con la contraseña por
> defecto al alcance de otros.

<!-- pagebreak -->

## 7. Si algo va mal

La mayoría de los problemas tienen una causa sencilla. Cada uno de los que siguen empieza por lo que ves, explica
por qué pasa y luego qué hacer. Si necesitas pedir ayuda, lo primero que te van a pedir son los registros, así
que empezamos por ahí.

**Dónde están los registros.** Mientras funciona, AutoBleem guarda sus registros en memoria, para no estar
escribiendo todo el rato en la memoria USB. Solo llegan a `System/Logs/` en la memoria, en la tarjeta o en la
carpeta de datos cuando algo ha ido mal: si el lanzador, un juego de PS1 o RetroArch se cierran de forma
inesperada, los registros se guardan en `System/Logs/crash-<n>/` (se conservan los de los tres últimos cierres),
y el lanzador te avisa una vez cuando vuelve. Si estás persiguiendo un problema que no es un cierre inesperado,
conserva todos los registros: activa Opciones → *Diagnóstico* → *Conservar los registros en el USB* (funciona a
partir del siguiente arranque), o crea desde un PC un archivo vacío `System/Logs/keep`. *Información de hardware*
(sección 4.2) también te dice dónde están los registros, y Square guarda ahí los actuales en
`System/Logs/saved-<n>/`.

Estos son los archivos que vas a encontrar:

| Archivo | Qué te cuenta |
|---|---|
| `autobleem.log` | Lo que ha hecho el propio lanzador. |
| `launch.log`, `pcsx.log` | Cómo se arrancó un juego de PS1 y lo que dijo el emulador mientras funcionaba. |
| `retroarch.log` | Lo que dijo RetroArch mientras funcionaba. |
| `update.log` | Cómo fue una actualización en línea; se guarda siempre en la memoria. |
| `updateroms.log` | Cómo fue UpdateRoms en el PC (capítulo 5); se guarda siempre en la memoria. |

**Una imagen te pide que conectes la memoria, o la consola se ha quedado en reposo.** AutoBleem no encuentra su
memoria: no estaba puesta al arrancar la consola, o se ha sacado. Conéctala a cualquier puerto USB (mejor a uno
frontal, sección 2.1) antes de que pasen los 5 minutos, o pulsa Power. Si la memoria no se quitó como es debido,
AutoBleem la revisa primero; espera a que termine la barra de progreso.

**RetroArch dice que *necesita una biblioteca del sistema más reciente que la de esta consola*.** Ese RetroArch se
compiló para un sistema más nuevo que el de la consola, así que en ella no puede funcionar. Usa el RetroArch que
viene con AutoBleem.

**Un juego dice que *está protegido por su licencia de PSN y no se puede iniciar*.** Los juegos comprados en la
PlayStation Network están atados a su licencia, y AutoBleem no puede ejecutarlos. No tiene arreglo.

**Un juego no aparece en la estantería.** Lo normal es que su carpeta no esté organizada como espera el escaneo.
Comprueba que cada juego tenga su propia carpeta y esté en uno de los formatos de la sección 3.10. El
*Administrador de Juegos* (sección 4.1) muestra después de los juegos las carpetas que el escaneo ha rechazado,
marcadas como *No añadido*, y te dice por qué se rechazó cada una; Square borra esa carpeta. Cuando hayas
arreglado una carpeta, *Reescanear juegos* en el menú del sistema vuelve a lanzar el escaneo.

**Los juegos no tienen carátula.** O bien no se instalaron las bases de datos de carátulas (vuelve a pasar el
instalador con ellas marcadas), o bien, si son juegos de RetroArch en una consola, todavía no has pasado
UpdateRoms en el PC (capítulo 5).

**Un mando no hace nada, o tiene los botones cambiados.** AutoBleem no conoce la distribución de ese mando. En una
consola, asígnalo con el asistente de mandos de PSC-Bios (sección 6.1). En una Pi o en un PC, la página
Información de hardware (sección 4.2) te muestra lo que el sistema ve del mando, lo que te ayuda a saber si lo
detecta o no.

**La pantalla se queda en negro después de un juego en la consola.** La imagen del lanzador no ha vuelto al
terminar el juego. AutoBleem reconstruye su ventana por su cuenta, hasta tres veces. Si aun así la pantalla sigue
en negro, mantén pulsado el botón Power y vuelve a encender la consola.

**En una Raspberry Pi** puedes asomarte detrás del lanzador cuando lo necesites: `Alt+F2` te da un inicio de
sesión en la segunda consola, y SSH está activado desde el primer arranque. `sudo journalctl -u autobleem` muestra
lo que ha hecho el servicio del lanzador, y `sudo systemctl restart autobleem` lo reinicia. Si el primer arranque
no pudo terminar por falta de red, lo vuelve a intentar en el siguiente.

**En Windows**, `Esc` cierra el lanzador. Tu carpeta de datos es la que elegiste durante la instalación
(`Documents\AutoBleem` si no la cambiaste), y los registros están en su carpeta `System\Logs`.

**La consola se reinicia una y otra vez después de una actualización en línea (memoria formateada en ext4).** Hay
quien formatea la memoria en ext4, el sistema de archivos de Linux, en lugar de en FAT32 o exFAT. Hasta la próxima
versión de AutoBleem, una actualización en línea en una memoria así descomprime todos los archivos sin el permiso
que les permite ejecutarse como programas. Entonces AutoBleem no puede arrancar, y la consola se reinicia sin
parar. Las memorias en FAT32 y exFAT no se ven afectadas. Hay dos formas de arreglarlo.

**Solución A**: necesitas un PC con Linux. Conecta la memoria y vuelve a hacer ejecutables los programas de
AutoBleem. Cambia `/media/USER/STICK` por la ruta en la que se monte tu memoria; la última línea solo hace falta
si tienes RetroArch instalado:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Solución B**: vuelve a instalar en la memoria la versión más reciente de AutoBleem, como en la sección 2.1. El
instalador necesita un PC que pueda leer la memoria. Si no puede leer la tuya, primero hay que formatearla, lo que
borra todo lo que contiene, así que copia antes tus juegos a otro sitio.

> Para evitarlo, usa **FAT32** (una consola de serie solo lee FAT32; exFAT necesita el kernel de AutoBleem,
> capítulo 6). La próxima versión conserva los permisos, y AutoBleem los repara en cada arranque.

AutoBleem es software libre (GNU GPL v3 o posterior) y no tiene ninguna garantía. Para soporte y novedades, únete
al servidor de Discord que encontrarás enlazado en la pantalla Sobre, o visita https://autobleem.retromenele.pl/.
