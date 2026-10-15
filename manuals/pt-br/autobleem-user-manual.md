# Manual do usuário do AutoBleem 2

O AutoBleem 2 é um launcher de jogos feito para o **PlayStation Classic** que, desde a versão 2, roda também em
um **Raspberry Pi**, em um **PC iniciado por um pendrive** e no **Windows**. Ele mostra seus jogos de PS1 como uma
prateleira de capas, com a arte e as informações de cada um, abre os jogos no emulador PCSX que vem junto e, se
você instalar o RetroArch ao lado dele, também roda jogos de outros sistemas. Neste manual você vai ver como
instalar o AutoBleem em cada plataforma, como usá-lo no dia a dia e para que servem as ferramentas que vêm com
ele.

> Todos os downloads ficam em **https://autobleem.retromenele.pl/**, separados por plataforma. O que você baixa
> é o painel *Install* de cada uma; os *Build inputs* logo abaixo são os arquivos que os instaladores já baixam
> sozinhos.

## 1. O que você ganha

Com o AutoBleem, o seu PlayStation Classic (ou um Raspberry Pi, um PC antigo ou o seu computador com Windows)
vira um pequeno videogame com um menu de verdade para os seus próprios jogos. Veja o que vem no pacote:

- **O launcher.** É o que aparece quando você liga o aparelho: uma prateleira de capas que você vai passando, com
  as informações de cada jogo ao lado. É dali que você abre os jogos, separa a coleção em conjuntos (PlayStation,
  RetroArch, Apps), muda as configurações, cuida dos cartões de memória e dos save states e baixa apps e jogos na
  Loja. A aparência e o funcionamento são os mesmos em todas as plataformas.
- **Dois emuladores de PS1.** O `pcsx-abnxt` é o atual e o padrão; o `pcsx-ab` é o emulador clássico que o
  AutoBleem sempre trouxe. Você escolhe entre os dois nas opções. Os dois usam as mesmas configurações e os
  mesmos cartões de memória, então dá para trocar quando quiser sem perder nada.
- **RetroArch**, se você também quiser jogar outros sistemas: NES, SNES, Mega Drive, Game Boy, fliperamas e
  muitos outros. Ele é opcional em todas as plataformas. Você copia suas ROMs e o AutoBleem organiza tudo em
  listas e abre cada jogo com o núcleo certo. Os jogos de PlayStation também podem rodar no RetroArch: o núcleo
  *PlayStation 1* fica no topo da lista de núcleos (seção 3.9). Jogos como Doom rodam com os seus próprios
  arquivos do jogo, guardados em uma pasta `Packages` (seção 3.10).
- **As ferramentas do console.** O *PSC-Bios*, que nos menus se chama *Rede e controles*, configura o WiFi, o
  relógio, os controles Bluetooth e o mapeamento dos botões, tanto no console quanto em um Raspberry Pi e no
  pendrive de PC. O *ABFlashKit* instala o kernel do AutoBleem em um PlayStation Classic (capítulo 6).
- **UpdateRoms** para Windows. O PlayStation Classic não tem rede própria, então este programa de PC atualiza as
  listas do RetroArch e baixa as capas para o pendrive do console enquanto ele está ligado no seu computador.

![O launcher: a prateleira de capas, as informações do jogo selecionado e as dicas de botões](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Instalação

### 2.1 PlayStation Classic

O AutoBleem roda inteiro a partir de um pendrive, e nada dentro do console é alterado: tirou o pendrive, o
console volta a funcionar exatamente como antes. Você só precisa de um PC com Windows, um pendrive (USB 2.0, de
8 GB ou mais) e o console.

O pendrive não precisa estar vazio, e ele **não é formatado** a não ser que você peça. O AutoBleem é instalado
ao lado do que já estiver lá, e um pendrive que você já usa com o AutoBleem 1.0 é atualizado no lugar (veja mais
abaixo). Em um console original, o pendrive precisa estar em **FAT32**, porque o kernel do próprio console não
lê exFAT. Depois que o kernel do AutoBleem estiver instalado (ABFlashKit, capítulo 6), o console passa a
iniciar também por um pendrive em exFAT, e você se livra do limite de 4 GB por arquivo do FAT32.

1. Baixe o **AutoBleemInstaller-<version>.zip** no painel PlayStation Classic do site e descompacte onde quiser.
   Dentro dele estão o `AutoBleemInstaller.exe` e o README. O AutoBleem em si é baixado durante a instalação,
   então o PC precisa estar conectado à internet.
2. Conecte o pendrive e abra o `AutoBleemInstaller.exe`. Escolha o **canal**: *Release* é a versão testada e a
   escolha certa para quase todo mundo, *Testing* é a próxima versão enquanto ainda está em teste, e *Nightly* é
   a build de desenvolvimento mais recente, que pode não funcionar. Depois escolha a unidade do pendrive. A linha
   logo abaixo mostra qual versão do AutoBleem você vai instalar e o que existe no pendrive agora: *a fresh
   install* (uma instalação nova; os outros arquivos do pendrive ficam onde estão) ou *AutoBleem <version> is on
   this stick: it will be updated* (a versão que já está lá vai ser atualizada, e seus jogos, saves, cartões de
   memória e configurações continuam lá).
   **Não é preciso formatar.** O botão **Format** ao lado da unidade serve só para um pendrive novo, ainda sem
   sistema de arquivos, para um que o console não consegue ler (em NTFS, por exemplo) ou para um que você queira
   zerar. Ele pede confirmação primeiro e depois apaga tudo o que houver no pendrive. Escolha FAT32 ali, a não
   ser que o console já tenha o kernel do AutoBleem.
   Em seguida, marque o que você quer instalar:
   - **Cover databases**: as capas e descrições de toda a biblioteca de PS1, para que seus jogos ganhem capa
     sozinhos (já vem marcado; cerca de 300 MB).
   - **RetroArch**: o RetroArch com seus núcleos, aplicativos extras (Doom, Quake, Amiga...) e os recursos do
     libretro, para jogos de outros sistemas. Vem desmarcado; dá para adicionar depois rodando o instalador de
     novo.
   - **BIOS files**: os arquivos de BIOS que alguns núcleos do RetroArch precisam para iniciar (só junto com o
     RetroArch).
   - **Sample games**: alguns jogos homebrew gratuitos, para a prateleira não ficar vazia na primeira vez que
     você ligar.
3. Clique em **Install** e aguarde. As barras de progresso e o log mostram cada etapa. No final, o pendrive passa
   a se chamar `SONY` e recebe uma cópia do `UpdateRoms` (veja o capítulo 5).
4. Remova o pendrive com segurança, conecte-o à **segunda porta USB da frente** do console (a da direita, do
   jogador 2), deixando a primeira livre para o seu controle, e ligue o console. No lugar do menu original, o
   AutoBleem é que vai aparecer. Para um segundo controle, use um hub USB na porta da frente ou um controle
   Bluetooth.

**Ligar e desligar.** Com o pendrive conectado, o console liga, pisca a luz por alguns segundos enquanto detecta o
AutoBleem e entra em espera antes de aparecer qualquer coisa na tela. Isso é normal: o AutoBleem inicia pelo
próprio mecanismo de atualização do console, e é assim que esse mecanismo funciona. Aperte **Power** uma vez e o
launcher aparece.

Quando você escolhe *Desligar* no menu do sistema, ou aperta o botão Power do console, ele entra no **modo de
espera do AutoBleem**: primeiro o AutoBleem desconecta o pendrive com segurança, depois a luz fica **laranja**, o
sinal de que deu tudo certo. Na próxima vez que você apertar Power, o launcher volta em poucos segundos.
**Enquanto a luz estiver laranja, você pode tirar o pendrive** e colocá-lo no PC; o Windows não vai pedir para
verificá-lo, porque ele foi desconectado do jeito certo. Coloque-o de volta antes de apertar Power. Se você tirar
o cabo de energia do console da tomada, na próxima vez ele passa de novo pela espera da inicialização. Luz
**vermelha** quer dizer que o console está realmente desligado.

**A porta de trás.** A porta micro-USB de trás é a entrada de alimentação do console. Com o kernel do AutoBleem
ela também aceita um dispositivo USB, mas o lugar do pendrive é numa porta da frente.

**Se o pendrive não estiver lá.** Se o console ligar sem o pendrive, ou se você tirar o pendrive com o AutoBleem
rodando, aparece uma imagem pedindo para você colocá-lo, em qualquer porta USB. O AutoBleem espera 5 minutos e
depois põe o console em espera; se quiser que ele entre em espera na hora, aperte Power.

![A imagem que pede o pendrive](../images/en/insert-stick.jpg)

**Quando o pendrive é verificado.** Se o pendrive não foi desconectado do jeito certo (você o tirou com o
AutoBleem rodando, ou faltou luz), o AutoBleem procura erros nele antes de usá-lo de novo: ao iniciar, ao sair da
espera ou quando você o conecta outra vez. Uma barra de progresso mostra o andamento da verificação. Em um
pendrive grande isso pode levar um tempo; deixe terminar e não desligue o console enquanto isso.

![A verificação do pendrive](../images/en/stick-check.jpg)

**Atualizar.** Para atualizar um pendrive, rode o instalador nele de novo; agora o botão diz *Update*. Ele instala
a versão mais recente do canal que você escolher: seus jogos, saves, configurações e o conteúdo do RetroArch
continuam lá, e só os arquivos do próprio AutoBleem são substituídos. Um console com o kernel do AutoBleem e WiFi
também consegue se atualizar sozinho (seção 3.12).

**Vindo do AutoBleem 1.0 (ou do AutoBleem-NG).** Você usa o mesmo instalador no mesmo pendrive, sem formatar:

1. Antes de tudo, copie o pendrive inteiro para o PC como backup, só por garantia.
2. Conecte o pendrive, abra o `AutoBleemInstaller.exe` e escolha o canal e a unidade. **Não** clique em Format.
3. Clique em **Install**. O instalador passa a organização antiga para a nova: o RetroArch, as ROMs e os temas vão
   para onde o AutoBleem 2 espera encontrá-los, e as pastas antigas de ROMs (`nes`, `snes`...) recebem os nomes de
   sistema do RetroArch. Seus jogos, save states, cartões de memória, ROMs e saves do RetroArch continuam lá, e o
   `config.ini` também; a única mudança nele é que o emulador de PS1 passa a ser o pcsx-abnxt.
4. Coloque o pendrive de volta no console. A primeira varredura reconstrói a lista de jogos e as playlists. Para
   ter as capas dos seus jogos do RetroArch, rode o UpdateRoms no PC (capítulo 5).

> O console original não tem relógio nem rede. As datas só aparecem depois que o kernel do AutoBleem é instalado
> (capítulo 6), e as capas dos jogos do RetroArch vêm do UpdateRoms, no PC (capítulo 5).

Seus jogos de PS1 vão na pasta `Games` do pendrive, cada um na sua própria pasta; a seção 3.10 explica como
organizar.

### 2.2 Raspberry Pi

Com o AutoBleem, um Raspberry Pi vira um pequeno videogame: ele inicia direto no launcher, sem nenhuma área de
trabalho no meio. O site oferece duas imagens de cartão prontas, de 32 e de 64 bits, e também um pacote para
instalar em um Raspberry Pi OS Lite que você já tenha.

| Modelo | Imagem de 32 bits | Imagem de 64 bits | Observações |
|---|---|---|---|
| Raspberry Pi 5 | sim | sim | |
| Raspberry Pi 4 Model B, Pi 400 | sim | sim | |
| Raspberry Pi 3 Model B / B+ / A+ | sim | sim | dá conta do launcher e do PS1 |
| Raspberry Pi Zero 2 W | sim | sim | 512 MB de RAM: o PS1 roda, os núcleos mais pesados do RetroArch não |
| Raspberry Pi 2 Model B | sim | só a v1.2 | lento para qualquer coisa em 3D |
| Raspberry Pi 1, Zero, Zero W | não | não | ARMv6: nenhuma das duas imagens roda |

**Para jogos de PS1, fique com a imagem de 32 bits.** O recompilador ARM rápido do `pcsx-ab` clássico só existe
em 32 bits, então os jogos de PS1 rodam mais devagar na versão de 64 bits. A imagem de 64 bits tem mais núcleos do
RetroArch; escolha ela se os outros sistemas forem mais importantes para você do que o PS1.

**Com o Raspberry Pi Imager:**

1. Instale o Raspberry Pi Imager (raspberrypi.com/software). Em *Choose OS*, escolha *Use custom* e o arquivo
   `autobleem-<version>-rpi-armhf.img.xz` (32 bits) ou `-arm64.img.xz` (64 bits) que você baixou. Outra opção é
   adicionar a URL de um repositório nas configurações do programa e escolher o AutoBleem na lista. Existe uma
   por canal: `https://autobleem.retromenele.pl/rpi-imager/os_list.json` para a última versão lançada,
   `.../os_list-testing.json` para a que está em teste e `.../os_list-nightly.json` para a build de
   desenvolvimento mais recente. A aba Raspberry Pi da página de downloads lista as que existem, cada uma com um
   botão *Copy*.
2. Na tela de personalização do Imager (a engrenagem, ou a pergunta que aparece depois de *Next*), defina **o nome
   de usuário e a senha, a rede WiFi e o país, e ative o SSH**. O AutoBleem precisa de rede na primeira
   inicialização.
3. Grave o cartão, coloque no Pi com uma tela e um teclado ou controle conectados e ligue.

**A primeira inicialização** leva de 5 a 25 minutos, e a tela vai mostrando o que está acontecendo. Se não houver
rede, ele pede uma: escolha o seu WiFi na lista e digite a senha. Depois ele pergunta se deve instalar o
RetroArch; se você não responder em um minuto, ele instala. Em seguida, aumenta a partição do sistema, transforma
o resto do cartão na partição `AUTOBLEEM` para os seus jogos, instala o RetroArch com seus núcleos, os pacotes de
BIOS e os jogos de exemplo, e reinicia já no launcher.

Se preferir que a primeira inicialização não faça perguntas, deixe as respostas prontas antes em
**`autobleem.txt`**, na partição de boot do cartão; qualquer PC consegue abrir e editar esse arquivo:

| Chave | Padrão | Significado |
|---|---|---|
| `root_gib` | 8 | O tamanho da partição do sistema em GiB; o resto vira a partição de jogos. |
| `hdmi_mode` | 1920x1080@60 | O modo de tela de toda a inicialização (`1280x720@60` para uma TV mais antiga). |
| `retroarch` | (perguntado) | `yes` / `no`: RetroArch e os outros sistemas, ou só PS1. |
| `thumbnails` | none | `boxarts` baixa o conjunto completo de capas para uso offline (cerca de 9000 arquivos). |
| `bios`, `downloads`, `samples` | yes | Use `no` para pular os pacotes de BIOS, todos os downloads ou os jogos de exemplo. |

**Em um Raspberry Pi OS Lite que você já tem** (Bookworm ou Trixie): copie o `autobleem-rpi.tar.gz` (ou o de
arm64) para o Pi, descompacte e rode `sudo bash install.sh`. Ele faz as mesmas perguntas, abre espaço para a
partição de dados encolhendo a partição do sistema na próxima inicialização (`--shrink-root <GiB>`) e coloca o
launcher no primeiro console.

Depois da instalação, você enche a **partição `AUTOBLEEM`** do cartão (em exFAT) com os seus jogos: tire o
cartão e abra em qualquer PC, ou copie pela rede (o SSH vem ativado). Os jogos de PS1 vão em `Games/`, as ROMs
de outros sistemas em `RetroArch/roms/<sistema>/`, a BIOS do PS1 em `System/Bios/` (seção 3.11) e os temas em
`Themes/`.

### 2.3 Pendrive de PC

A mesma ideia, para qualquer PC que consiga iniciar por USB: o pendrive inicia o PC direto no AutoBleem e não
mexe no disco do computador. É um sistema de 32 bits, então funciona também em máquinas antigas.

1. Grave a imagem em um pendrive de 8 GB ou mais. **No Windows**, use o **AutoBleemFlasher** (painel PC do site):
   descompacte e abra o `AutoBleemFlasher.exe`. Ele pede permissão de administrador, porque grava um disco
   inteiro. Escolha o canal e o pendrive, clique em *Write* e confirme duas vezes: ele baixa a imagem, confere,
   grava e lê tudo de volta para verificar. Só aparecem pendrives e cartões SD, nunca o disco onde o Windows está
   rodando, e **tudo o que houver no pendrive escolhido é apagado**. No Linux ou no macOS, baixe o
   `autobleem-<version>-pcusb-i386.img.xz` no painel PC e grave com
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` (ou com o balenaEtcher).
2. Inicie o PC pelo pendrive (com a tecla do menu de boot do seu PC: F12, F8, Esc...). Funciona tanto com BIOS
   quanto com UEFI; **o Secure Boot precisa estar desativado**.
3. A primeira inicialização é como a do Pi: pede uma rede se não houver cabo conectado, pergunta sobre o
   RetroArch, instala tudo (cerca de oito minutos com rede cabeada) e reinicia no launcher.

Depois disso, o pendrive tem uma partição `AUTOBLEEM` para os seus jogos. Conecte o pendrive a um PC com
Windows 10 (versão 1903 ou mais nova) já ligado e ele aparece como uma segunda unidade, para onde você pode copiar
jogos. O `autobleem.txt` fica na primeira partição, com as mesmas chaves do Pi (menos `hdmi_mode`: um PC sempre
usa o modo nativo da tela).

### 2.4 Windows

Se você quer o AutoBleem no seu computador com Windows, ele também roda como um programa comum: em tela cheia, e
com os emuladores e o RetroArch abrindo como programas separados.

1. Baixe o **AutoBleemSetup-<version>.exe** e execute. A instalação é por usuário, sem precisar de
   administrador: o programa vai para `%LOCALAPPDATA%\Programs\AutoBleem`, e os dados (jogos, configurações,
   temas, RetroArch) para uma pasta que você escolhe, por padrão `Documents\AutoBleem`.
2. Marque os componentes (os bancos de capas, o RetroArch na versão oficial para Windows com seus núcleos, os
   arquivos de BIOS e os jogos de exemplo) e deixe o assistente baixar tudo.
3. Abra o AutoBleem pelo menu Iniciar ou pela área de trabalho. No PC, o teclado funciona como controle
   (seção 3.2).

Para atualizar, rode um instalador mais novo por cima: o programa é substituído e a sua pasta de dados fica como
está. O launcher também consulta o site uma vez por dia e oferece a atualização quando houver uma (seção 3.12).

<!-- pagebreak -->

## 3. Usando o AutoBleem

### 3.1 O launcher

O launcher é onde você escolhe o que vai jogar. Ele mostra seus jogos como uma prateleira de capas, do jeito que
você veria as caixas em uma estante de verdade, e você vai passando até achar o que quer. Todo o resto do
AutoBleem (as configurações, os cartões de memória, a Loja) abre a partir daqui, e é para cá que você volta quando
sai de um jogo.

O jogo selecionado fica no meio da prateleira, com um reflexo suave embaixo. Ao lado aparecem as informações dele
em uma pequena grade: a publicadora, o ano, o número de série, a região, para quantos jogadores ele é e quando você
jogou pela última vez. Quando o AutoBleem não sabe alguma dessas informações, ele tira a linha em vez de deixá-la
vazia. Ao lado das informações há um botão de jogar. Um jogo sem imagem de capa aparece como um disco na bandeja
preta de uma caixa vazia, para que ele também tenha seu lugar na prateleira.

A aparência do launcher vem do tema. O tema padrão é o **ab2.0.0**: uma instalação nova já usa ele, e uma
atualização que o traz também troca para ele, mas só uma vez; se depois você escolher outro tema (seção 3.6), é
esse que fica.

**A barra de dicas**, na parte de baixo da tela, mostra o que cada botão faz naquele momento. Ela tem duas linhas
de quatro espaços cada. A primeira linha fala do jogo selecionado: jogar, jogar no RetroArch, abrir a fileira de
ícones embaixo dele ou abrir o menu rápido. A segunda nunca muda: Select escolhe o conjunto, Start sorteia um jogo,
Triangle mostra o guia de botões e L2 + R2 abre o menu do sistema. Quando um botão não tem nada para fazer, a dica
dele fica apagada.

**Ele encontra os jogos novos sozinho.** Toda vez que o launcher inicia, ele faz uma varredura na sua pasta de
jogos em segundo plano, então um jogo que você copiou com a máquina desligada aparece sem você fazer nada.
Enquanto a varredura roda, um balão no canto superior direito mostra o andamento, e os jogos novos vão aparecendo
na prateleira conforme são encontrados. Dá para continuar navegando enquanto isso.

**Uma instalação nova** ainda não tem jogos. Em vez de uma prateleira vazia, aparece um cartão de boas-vindas,
*Olá, e bem-vindo ao AutoBleem!*, que pede para você colocar seus jogos em `Games` e escolher *Reescanear jogos*.
Ele diz onde fica esse lugar na sua plataforma: no seu pendrive (PlayStation Classic, pendrive de PC), no seu
cartão SD (Raspberry Pi) ou na sua pasta do AutoBleem (Windows). O cartão some assim que uma varredura encontra o
primeiro jogo.

**As notificações** são os balões no canto superior direito. Elas deixam você por dentro sem atrapalhar: o
andamento da varredura, o nome do conjunto para o qual você acabou de mudar (*Mostrando: ...*), um controle com
bateria fraca, um aviso depois de um travamento, um processador de varredura trabalhando e um download da Loja. O
balão de um download mostra a velocidade e o tempo que falta, por exemplo `1.4 MB/s · 0:42`. Quanto tempo os
balões informativos ficam na tela é você quem decide, em Opções → *Duração do aviso:*.

**A bateria dos controles.** No console, em um Raspberry Pi e no pendrive de PC (não no Windows), cada controle
sem fio que informa a bateria aparece como um pequeno ícone com a porcentagem, na sua própria plaquinha, uma
embaixo da outra a partir do canto superior esquerdo. Um controle que joga como jogador 1 ou jogador 2 leva a
etiqueta P1 ou P2, de acordo com a opção *Trocar jogador 1 / jogador 2 (emuladores PS1):* (seção 3.6); um controle
que não está ligado a nenhum jogador, ou um terceiro controle, fica sem etiqueta. Quando a bateria de um controle
fica fraca, uma notificação avisa uma vez, com o nome do controle e a porcentagem.

**A etiqueta do canal.** Se você está usando uma build que não é uma versão final, uma pequena etiqueta embaixo da
plaquinha das baterias, no canto superior esquerdo, lembra você disso. É um selo com o canal e, ao lado, a versão
abreviada: `ALPHA`, `BETA` ou `RC` para uma pré-versão, `TESTING` para qualquer outra pré-versão, `NIGHTLY` para
uma build noturna e `DEV` para uma build feita à mão (no caso de `DEV`, a versão é o commit a partir do qual ela
foi compilada). Uma versão lançada não mostra etiqueta.

![O seletor de conjuntos: três abas, e os grupos da aba atual com a quantidade de jogos](../images/en/set-picker.jpg)

### 3.2 Controles

O AutoBleem foi feito para ser usado só com o controle, e os botões querem dizer a mesma coisa em todas as telas:
Cross confirma, Circle volta e Triangle ajuda. Se você esquecer o que um botão faz, a barra de dicas na parte de
baixo da tela mostra, e Triangle na prateleira abre o guia de botões, com todos os botões de todas as telas (seção
4.3). Na prateleira, os botões fazem o seguinte:

| Botão | Na prateleira |
|---|---|
| Esquerda / Direita | Vai para o jogo anterior ou para o próximo; segure para continuar passando. |
| L1 / R1 | Pula para a letra inicial anterior ou seguinte dos títulos, para atravessar rápido uma prateleira grande. Em uma prateleira vazia com uma unidade USB conectada, R1 abre *Disco* (seção 3.9a). |
| Cross | Abre o jogo selecionado: um jogo de PS1 no emulador de PS1, um jogo do RetroArch no seu núcleo e um app depois de mostrar o leia-me dele. |
| Square | Abre o jogo de PS1 selecionado no RetroArch. Quando o selecionado é um disco em uma unidade USB, ele copia o disco (*Copiar disco*, seção 3.9a). |
| Circle | Leva você de volta à tela do disco quando há um disco na unidade (seção 3.9a). |
| Triangle | Abre o guia de botões. |
| Start | Sorteia um jogo do conjunto atual, para quando você não consegue decidir. |
| Select | Abre o seletor de conjuntos, onde você escolhe quais jogos a prateleira mostra (seção 3.3). |
| Cima | Abre o menu rápido (seção 3.4). |
| Baixo | Abre a fileira de ícones embaixo do jogo (*CONFIGURAÇÕES*, *Jogo*, *CARTÃO DE MEMÓRIA*, *CONTINUAR*); Cima fecha de novo. |
| L2 + R2 | Abre o menu do sistema (seção 3.5). |

**Com teclado.** Em um PC sem controle, ou com um teclado USB no console, em um Pi ou no pendrive de PC, as teclas
fazem o papel dos botões. As setas são o direcional, Enter é Cross, Esc ou Backspace é Circle, Tab é Triangle e a
barra de espaço é Square. F1 e F2 são Select e Start, Page Up e Page Down são L1 e R1, Home e End são L2 e R2, e
F10 abre o menu do sistema. Em uma máquina de desenvolvimento, Esc fecha o programa e a barra de espaço é Start.

**Em todas as listas e menus** os movimentos são os mesmos: Cima e Baixo movem o cursor, L2 e R2 viram a página,
L1 e R1 pulam para a primeira ou para a última linha, Cross seleciona e Circle volta. Você nunca precisa procurar
um botão de salvar: uma tela de configurações salva tudo quando você sai dela com Circle.

**Sair de um jogo ou de um app.** Segure Start + Select, ou Home, por 2 segundos e você volta para o AutoBleem.
Isso funciona em qualquer controle: o do console, um USB ou um Bluetooth. Um toque curto nesses mesmos botões abre
o menu do emulador. Um app não tem esse menu, então nele só o toque longo faz alguma coisa.

![A fileira de ícones embaixo do jogo selecionado](../images/en/launcher-icons.jpg)

### 3.3 Os conjuntos

Uma biblioteca grande fica mais fácil de navegar em partes. Os conjuntos deixam na prateleira um só tipo de jogo
(só os favoritos, só os de Super Nintendo, só os de uma pasta), para você não ter que passar por centenas de capas
até achar a que procura.

Aperte **Select** e o seletor de conjuntos abre. Ele tem três abas, PlayStation, RetroArch e Apps: L1 e R1 trocam
de aba, Cima e Baixo passam pelos grupos da aba (L2 e R2, uma página por vez) e Cross mostra na prateleira o grupo
escolhido. Circle (*Voltar*) fecha o seletor sem mudar nada. O rodapé também mostra essas teclas. Cada linha diz
quantos itens o grupo tem. Um grupo vazio abre uma prateleira vazia, onde a fileira de ícones só oferece
*CONFIGURAÇÕES*.

**A aba PlayStation.** Em um PlayStation Classic ela começa com *Todos os jogos* e *Jogos internos* (os vinte jogos
que vêm no console), seguidos de *Jogos USB*, que é tudo o que está em `Games/`, e de um grupo para cada pasta que
você criou ali dentro, então um jogo em uma subpasta pertence ao grupo dessa pasta. Depois vêm *Jogos favoritos*,
*Histórico de jogos* e, assim que você tiver marcado pelo menos um jogo como jogo de pistola, *Jogos de pistola*.
Um Raspberry Pi, um pendrive de PC e o Windows não têm jogos internos, então neles a lista começa em *Jogos USB*,
que é a sua biblioteca inteira.

**A aba RetroArch** só aparece onde o RetroArch está instalado. Ela tem um grupo para cada sistema do qual você tem
jogos, mais os Favoritos e o Histórico do próprio RetroArch.

**A aba Apps** separa os aplicativos por tipo: *Todos os apps*, e depois *Jogos*, *Emuladores*, *Ferramentas*,
*Mídia* e *Outros*. O grupo de cada app é definido no arquivo `app.ini` dele. Essa aba também lista os **apps
PE**, programas de Windows executados pelo PE runner; um que o console não consegue abrir aparece marcado como *não
pode rodar neste console*. Onde o launcher mostra, há também uma linha *Pacotes* na lista (seção 3.10).

### 3.4 O menu rápido

O menu rápido é uma lista curta com o que você mais usa enquanto navega pelos jogos, para não precisar cavar o menu
do sistema inteiro atrás disso. Ele abre com **Cima** na prateleira ou com o **ícone de engrenagem** na fileira de
ícones (a que tem *CONFIGURAÇÕES*, *Jogo*, *CARTÃO DE MEMÓRIA* e *CONTINUAR*).

Cima e Baixo passam pelos itens (do último, o cursor volta para o primeiro), Cross escolhe um e Circle fecha o
menu. Uma linha embaixo do menu descreve o item selecionado. Estes são os itens:

- *Reescanear jogos* procura na hora jogos novos, alterados ou removidos; útil quando você acabou de copiar jogos e
  não quer esperar.
- *Loja* abre a Loja do AutoBleem, onde você navega e instala jogos, apps e extensões (seção 3.13).
- *Núcleos do RetroArch*, onde o RetroArch está instalado, deixa você escolher qual núcleo roda cada sistema.
- *Rede e controles* abre as telas de Wi-Fi, de pareamento Bluetooth e de mapeamento de controles (capítulo 6).
  Ele só aparece quando uma extensão instalada oferece essas telas, como o PSC-Bios faz no console, em um Raspberry
  Pi e no pendrive de PC. Se essa extensão estiver instalada mas desligada, o item fica cinza e a descrição dele
  diz para ativá-la em Extensões; aí Cross abre a lista de Extensões direto nela.
- *Reiniciar o launcher* fecha o AutoBleem e abre de novo (só no console, em um Raspberry Pi e no pendrive de PC).
- *Menu do sistema...* abre o menu do sistema completo, com todo o resto: Opções, Gerenciador de Jogos, Desligar e
  mais (seção 3.5).

Tudo o que está aqui, menos a Loja, os núcleos do RetroArch e Reiniciar o launcher, também está no menu do sistema.

![O menu rápido](../images/en/quick-menu.jpg)

### 3.5 O menu do sistema

O menu do sistema reúne tudo o que o AutoBleem faz além de jogar: as configurações, as ferramentas para a sua
biblioteca e para os cartões de memória, as informações sobre a máquina e a forma de desligar. Aperte **L2 + R2**
juntos (em qualquer ordem) e ele abre por cima da prateleira. Os itens ficam agrupados sob os títulos
*Biblioteca*, *Sistema* e *Sair*, com os dois mais usados no topo. Uma linha na parte de baixo do menu descreve o
item selecionado, então dá para dar uma olhada antes de escolher.

| Seção | Item | O que faz |
|---|---|---|
| (topo) | *Reescanear jogos* | Procura agora jogos novos, alterados ou removidos. A varredura já vigia a pasta sozinha, então você só precisa disso quando não quer esperar. |
| | *Extensões* | Lista as extensões do pendrive, como a Loja do AutoBleem, para você abri-las ou desligá-las (seção 3.13). |
| *Biblioteca* | *Gerenciador de Jogos* | Mostra os jogos de PS1 em uma lista com as pastas deles, onde você pode apagar um jogo ou limpar as capas (seção 4.1). Não abre enquanto uma varredura está rodando. |
| | *Cartões de memória* | Cuida dos seus conjuntos de cartões de memória compartilhados (seção 3.8). |
| | *Processadores de varredura* | Define a ordem dos programas que toda varredura roda primeiro, e liga ou desliga cada um (seção 3.14). Não abre enquanto uma varredura está rodando. |
| *Sistema* | *Opções* | Abre as configurações do AutoBleem (seção 3.6). |
| | *Rede e controles* | Abre as telas de Wi-Fi, de pareamento de controles Bluetooth, de configuração do DualShock 3 e de mapeamento de controles (capítulo 6). Só aparece quando uma extensão oferece essas telas; veja abaixo. |
| | *Informações de hardware* | Mostra os dados da máquina (sistema, CPU, armazenamento, interfaces de rede, fuso horário, tela e os controles com seus mapeamentos), na mesma página em todas as plataformas (seção 4.2). Circle traz você de volta ao menu do sistema. |
| | *Gamepad virtual* | Mostra os controles que os apps recebem e os controles que o daemon enxerga, o que ajuda quando um controle não funciona em um app (seção 4.5). Circle traz você de volta ao menu do sistema. |
| | *Atualização de software* | Procura agora no site uma versão mais nova do AutoBleem ou do RetroArch, sem esperar a verificação diária (seção 3.12). Quando o launcher já sabe de uma, a linha diz *Atualização disponível*. Em um PlayStation Classic, isso precisa do kernel do AutoBleem e de uma rede Wi-Fi. |
| | *Sobre* | Mostra os créditos e a licença. |
| *Sair* | *RetroArch* | Sai do launcher para o menu do próprio RetroArch, com as configurações e as listas de conteúdo dele; quando você fecha o RetroArch, volta ao launcher. Só aparece onde o RetroArch está instalado. |
| | *Desligar* | Desliga a máquina depois de pedir confirmação (veja abaixo). |

**Rede e controles** só aparece quando uma extensão instalada oferece a entrada `network`, que a extensão declara
com `Provides=network` no seu `extension.ini`. O PSC-Bios faz isso no console, em um Raspberry Pi e no pendrive de
PC. Se essa extensão estiver instalada mas desligada, o item continua no menu, em cinza, e a descrição dele diz
para ativá-la em Extensões; Cross sobre ele abre a lista de Extensões direto nessa extensão.

**Desligar** faz o que combina com cada máquina. No console, ele entra no modo de espera do AutoBleem: o pendrive
é desconectado, a luz fica laranja e o Power traz o launcher de volta em poucos segundos (seção 2.1). Em um
Raspberry Pi ou em um PC, a máquina desliga.

![O menu do sistema](../images/en/system-menu.jpg)

### 3.6 Opções

Opções é onde você deixa o AutoBleem do seu jeito: a imagem na sua tela, a aparência do launcher, o idioma, o som
e o emulador de PS1 que roda seus jogos. Você abre pelo menu do sistema (*Opções*) ou pelo ícone *CONFIGURAÇÕES*
embaixo de um jogo. Normalmente você ajusta a tela e o idioma uma vez e só volta quando alguma coisa fica estranha
em uma TV específica ou quando dá vontade de mudar.

As configurações ficam separadas em grupos, cada um com um título. Cima e Baixo passam de uma linha para outra, e
Esquerda e Direita mudam o valor da linha em que você está: um toque anda um passo, e segurar o botão continua
andando. L1 e R1 pulam para a primeira ou para a última linha, e L2 e R2 viram a página. Em uma linha com uma lista
de temas, músicas ou fontes, Start escolhe um aleatório. Uma configuração de ligar e desligar mostra **ON** ou
**OFF**. Você vê cada mudança na hora, e Circle sai da tela e salva tudo; não há mais nada para confirmar. A única
exceção é o modo de tela, que é testado quando você sai de Opções (veja *Tela:* mais abaixo).

Algumas linhas só aparecem onde fazem sentido: as de CRT só com uma imagem 4:3, as do RetroArch só onde o RetroArch
está instalado e a dos jogos internos só em um PlayStation Classic.

| Grupo / configuração | Para que serve |
|---|---|
| *Interface*: *Tela:* | Define a resolução da tela, para o launcher e para o emulador de PS1. *Auto* usa o modo nativo da tela e mostra qual é, por exemplo *Auto (1920x1080)*; você também pode escolher qualquer modo que a tela ofereça. O console oferece 720p, 1080p e *CRT 4:3* (720x480), o modo para uma TV de tubo antiga ou uma placa de captura 4:3. Mude quando a imagem não couber na sua TV ou ficar borrada. Essa linha não aparece quando o AutoBleem roda em uma janela em uma máquina de desenvolvimento. |
| *Margem CRT:* | Encolhe tudo um pouco, de 0 a 10 % em passos de 1 %, porque as TVs antigas cortam as bordas da imagem. Aumente até a barra de dicas e os cantos aparecerem inteiros. Só aparece em uma saída 4:3, vale na hora e é aplicada até antes da tela de abertura. |
| *Altura da imagem:* | Deixa a imagem mais alta ou mais baixa, de -40 a +40 em passos de 2, em qualquer saída 4:3: *CRT 4:3*, ou um modo 4:3 em uma saída VGA ou de PC. Use quando, em uma TV antiga, a imagem aparecer achatada ou passar das bordas de cima e de baixo. Vale na hora, e a imagem dos jogos no RetroArch acompanha. |
| *Escala da tela do emulador:* | Decide como o emulador de PS1 encaixa a imagem do jogo na sua tela. *1x1* mostra os pixels do próprio PlayStation, pequenos e exatos; *2x (inteira)* e *4:3 (inteira)* só aumentam em múltiplos inteiros, o que dá a imagem mais nítida; *4:3* mantém o formato original da imagem; *Tela cheia* estica a imagem pela tela toda. Substitui a antiga chave de tela widescreen. O `pcsx-ab` clássico e o RetroArch só conhecem tela cheia e 4:3. |
| *Halo da tela:* | Com ON, as faixas vazias ao lado da imagem do jogo (onde ela não preenche a tela) são preenchidas com um brilho suave da própria imagem, em vez de preto. Funciona com o `pcsx-abnxt`. |
| *Tema do AutoBleem:* | Muda a aparência do launcher. Os temas ficam em `Themes/`, e o zip de um tema colocado ali também aparece na lista pelo nome. Os temas que vêm com o AutoBleem são renovados a cada atualização, então, se quiser personalizar um, copie com outro nome antes. O padrão é o **ab2.0.0**. |
| *Estilo da capa:* | Escolhe a moldura de caixa de CD desenhada em volta das capas de PS1. |
| *Brilho da capa:* | Faz um brilho atravessar a capa selecionada toda vez que a prateleira para. |
| *Idioma:* | Define o idioma do launcher; são 17, e a troca é imediata. |
| *Duração do aviso:* | Define quanto tempo os balões informativos (*Mostrando: ...*, o resumo da varredura) ficam na tela, de 0 a 20 segundos; em 0 aparece *Desligado* e eles não são mostrados. As mensagens de erro têm um tempo fixo próprio, para você nunca perder nenhuma. |
| *Tela de abertura:* | Mostra a imagem do AutoBleem enquanto o launcher inicia; desligue para ir direto para a prateleira. |
| *Animações:* | Anima a passagem de uma tela para outra; desligue se preferir que cada tela apareça na hora. |
| *Fontes*: *Usar a fonte padrão:* | Com ON, o launcher usa a fonte dele (Red Hat Text); desligue para usar a fonte escolhida na linha seguinte. |
| *Fonte:* | Escolhe uma fonte sua: qualquer arquivo `.ttf` ou `.otf` em `resources/fonts`, `RetroArch/fonts` ou na pasta do tema. A linha mostra o nome da fonte que está realmente em uso. |
| *Som*: *Música:*, *Música de fundo:* | *Música:* escolhe a faixa que toca no launcher: a do tema ou um arquivo de `resources/music`. *Música de fundo:* decide se toca música ou não. |
| *Emulação*: *Emulador PS1:* | Escolhe o emulador em que seus jogos de PS1 abrem: o `pcsx-abnxt`, o padrão (o PCSX-ReARMed atual com os acréscimos do AutoBleem), ou o `pcsx-ab`, o clássico. Experimente o outro quando um jogo não rodar bem. Um ponto de retomada salvo por um continua no outro, a não ser que o jogo tenha rodado sem arquivo de BIOS. |
| *Trocar jogador 1 / jogador 2 (emuladores PS1):* | Troca qual dos dois primeiros controles é o jogador 1 e qual é o jogador 2, nos dois emuladores de PS1; uma mão na roda quando os controles estão ligados "ao contrário". Só faz diferença com dois ou mais controles conectados; com um só, você sempre joga como jogador 1. O RetroArch não é afetado. Se o emulador de PS1 em uso ainda não souber fazer a troca, o AutoBleem avisa. |
| *Jogue todos os jogos PSX com RA:*, *Atualizar config do RA:*, *Manter config. do RetroArch:* | Essas três só aparecem onde o RetroArch está instalado. A primeira abre todos os jogos de PS1 no núcleo de PS1 do RetroArch (*PlayStation 1*; no PC é o SwanStation). A segunda deixa o AutoBleem gravar as configurações dele na configuração do RetroArch quando abre um jogo por lá. A terceira mantém, quando o RetroArch fecha, uma mudança que você fez no menu do próprio RetroArch. |
| *Biblioteca*: *Mostrar jogos internos:* | Mostra os jogos que vêm no console nas listas de PlayStation (só no PlayStation Classic). |
| *Nomes de jogos limpos:* | Com ON (o padrão), as listas de jogos do RetroArch mostram nomes limpos, sem etiquetas entre parênteses ou colchetes como (USA), (Rev 1) ou [!]; com OFF aparecem os nomes dos arquivos. O nome do arquivo continua nas informações do jogo. Os jogos de PS1 não são afetados, porque os títulos deles vêm do banco de dados. |
| *Buscar capas online:* | Deixa a varredura baixar as capas que faltam dos servidores do libretro (Raspberry Pi, PC, Windows). |
| *Atualizações*: *Atualizações:* | Escolhe quais atualizações o launcher procura (seção 3.12): `release` (a versão testada), `testing` (a próxima versão, em teste), `nightly` (a build de desenvolvimento mais recente) ou `off`. O padrão acompanha a versão que você instalou. Não aparece em uma máquina de desenvolvimento. |
| *Diagnóstico*: *Manter os logs no pendrive:* | A partir da próxima inicialização, guarda todos os logs no pendrive, e não só depois de um travamento; ligue quando estiver caçando um problema (capítulo 7). |
| *Mostrar desempenho:* | Mostra no canto inferior esquerdo um painel com a taxa de quadros, o uso da CPU, as threads e a memória; dentro de um jogo, o emulador mostra também o FPS e a CPU dele. |

**Mudar o modo de tela.** Quando você sai de Opções com um modo novo em *Tela:*, o AutoBleem muda para ele e
pergunta *Manter este modo de tela?*. Se a imagem estiver boa, confirme. Se a TV não mostrar nada, espere: sem
confirmação, o AutoBleem volta ao modo anterior depois de uma contagem regressiva.

**Temas em uma tela 4:3.** No modo *CRT 4:3*, a lista de temas mostra só os que têm um layout 4:3. Se o tema que
você usa não tiver, o tema padrão entra no lugar dele assim que você confirma o modo (e a cada inicialização nesse
modo), e um aviso conta isso para você: *Tema alterado para o padrão (CRT 4:3)*.

![As opções, separadas em grupos](../images/en/options.jpg)

![O grupo Tela: Margem CRT e Altura da imagem](../images/en/options-display.jpg)

![O aviso depois de mudar para CRT 4:3 com um tema sem layout 4:3](../images/en/crt43-theme-notice.jpg)

### 3.7 As configurações de um jogo

Cada jogo pode ter as suas próprias configurações. A maioria roda bem do jeito que está, mas de vez em quando um
precisa de uma ajudinha (uma imagem mais nítida ou mais suave, pular um quadro para manter a fluidez, outro cartão
de memória), ou você quer marcá-lo como favorito. O editor do jogo é onde você muda essas coisas só para aquele
jogo, sem mexer em nenhum outro.

Com um jogo selecionado, aperte **Baixo** para abrir a fileira de ícones embaixo dele. São quatro ícones:
*CONFIGURAÇÕES* (as opções da seção 3.6), *Jogo* (as configurações deste jogo), *CARTÃO DE MEMÓRIA* (o cartão de
memória dele) e *CONTINUAR* (os save states dele). Vá até um e aperte Cross para abrir.

**O editor do jogo** (o ícone *Jogo*) mostra à direita as informações do jogo (o título, a publicadora, o ano, o
número de jogadores, a pasta e o cartão de memória) e à esquerda as configurações. Cima e Baixo passam de uma
configuração para outra e Esquerda e Direita mudam o valor, como em Opções; segurar um botão repete o movimento.
Quando terminar, Circle salva as mudanças e volta. Um jogo que não tem título nos dados aparece com o nome da pasta
dele.

As configurações ficam em quatro grupos:

- **Jogo** é sobre como o AutoBleem trata o jogo. *Favorito:* coloca o jogo no grupo *Jogos favoritos* do seletor
  de conjuntos. *Trancar dados:* diz à varredura para deixar o título, o número de série e a lista de discos
  exatamente como você definiu, para que uma varredura posterior não apague suas mudanças. *Retomar:* decide o que
  acontece quando você abre um jogo que tem pontos de retomada: *Perguntar* mostra o seletor de slots, *Último
  slot* continua na hora a partir do slot mais recente, e *Nunca* sempre começa o jogo do início. Onde o RetroArch
  está instalado, há mais duas linhas. *Jogo Lightgun:* é para jogos de pistola: o jogo entra no grupo *Jogos de
  pistola* e sempre roda no RetroArch, porque o núcleo de PS1 do RetroArch tem a GunCon (ligar essa opção também
  liga a linha seguinte). *Jogar usando RA:* roda só este jogo no RetroArch em vez do emulador de PS1.
- **Tela** é sobre a aparência da imagem. *Resolução:* desenha o jogo em 1x ou 2x (na GPU interna), e *Remover
  costuras:*, que só funciona em 2x, esconde as linhas finas que podem aparecer entre partes da imagem nesse
  tamanho. *Dithering:* (*Desligado*, *Ligado*, *Sempre*) controla o padrão fino de pontinhos que o PlayStation usa
  para misturar cores, e *Suavização:* escolhe um dos filtros de suavização do emulador. *Filtro:* decide como a
  imagem é ampliada para a tela: *Mais próximo* mostra os pixels puros, *Linear* suaviza, *Nítido* e *Nítido
  (simples)* mantêm os pixels definidos sem tremular, e há também o *Quilez*. Os filtros CRT, *CRT (fast)*, *CRT
  (raster)* e *CRT-Pi*, imitam uma TV antiga e desenham as próprias scanlines, então as linhas de scanlines ficam
  cinza enquanto um deles estiver escolhido. Fora isso, *Scanlines:* acrescenta as linhas escuras de uma TV antiga,
  e *Brilho das scanlines:* define o quanto elas escurecem. *Resolução*, *Remover costuras*, *Dithering*,
  *Suavização* e os filtros que não sejam *Linear* e *Mais próximo* são para o `pcsx-abnxt`; o `pcsx-ab` clássico
  e o RetroArch mostram qualquer outro filtro como *Mais próximo*.
- **Renderização** tem o *Plugin:* de GPU e o *Pular frame:* (*Auto*, *Desligado*, ou de 1 a 3 quadros). Pular
  quadros ajuda um jogo que está lento demais a manter a velocidade, ao custo de uma imagem menos fluida.
- **Emulador** tem *SpeedHack:*, a *Frequência:* da CPU, *Interpolação Spu:* (como o som é suavizado), *Logo de
  inicialização:* e, com o `pcsx-abnxt`, *Hacks da Sony:*. Desligue *Logo de inicialização:* para pular a tela da
  BIOS; você vai precisar disso em um disco homebrew cujo logo próprio impede o jogo de iniciar.

O formato da imagem e a resolução da tela não são definidos por jogo, e sim para todos de uma vez, em Opções
(*Escala da tela do emulador:* e *Tela:*).

**Outros botões do editor.** Triangle renomeia o jogo, com o teclado na tela. Square dá ao jogo outro cartão de
memória (*Trocar cartão de memória*). Enquanto o jogo ainda usa o cartão próprio, Start transforma esse cartão em
um novo conjunto compartilhado, para que outros jogos também possam usá-lo (*Compartilhar cartão de memória*,
seção 3.8). Esses dois não aparecem para os jogos internos do console. Segurar Esquerda / Direita ou Cima / Baixo
repete o movimento aqui, e também nas telas de opções de jogo e de núcleos do RetroArch.

Cada jogo guarda as configurações no seu próprio arquivo `pcsx.cfg`. Todo jogo do pendrive tem um, porque a busca
o cria. Já um disco original numa unidade USB (seção 3.9a) só ganha a sua pasta com um `pcsx.cfg` na primeira vez
que você o inicia; até lá, uma mudança feita no editor não pode ser guardada, e o editor avisa *Não salvo: este
jogo não tem pcsx.cfg*. Então inicie o disco uma vez - daí em diante as configurações dele ficam guardadas como
as de qualquer outro jogo. Um disco que pertence a um jogo que já está na sua coleção usa a pasta e as
configurações desse jogo desde o começo.

Para um **disco na unidade** (seção 3.9a), algumas configurações não fazem sentido, então o editor deixa essas
linhas em cinza, e a linha de baixo diz *Indisponível para um disco na unidade* quando você passa por uma delas.

![O editor do jogo para um disco na unidade](../images/en/game-editor-disc.jpg)

**Configurações salvas no emulador.** Você também pode ajustar um jogo enquanto joga: o menu do próprio emulador
tem *Save settings for this game* (seção 3.9). Quando um jogo tem configurações salvas ali, são elas que valem. O
editor do jogo passa então a mostrar as linhas de Tela, Renderização e Emulador em cinza, com os valores salvos,
sob o título *Salvo no emulador*: dá para ler, mas não para mudar. Se você preferir voltar a usar as configurações
do editor, escolha *Desbloquear as configurações* e confirme: as configurações que o emulador salvou são apagadas,
e as linhas voltam a poder ser alteradas. Os dois emuladores, `pcsx-ab` e `pcsx-abnxt`, leem e gravam as mesmas
configurações salvas, então não importa qual deles salvou.

![O editor do jogo](../images/en/game-editor.jpg)

### 3.8 Cartões de memória e save states

Em um PlayStation de verdade, você dividia um ou dois cartões de memória entre todos os jogos, e uma hora o espaço
acabava. No AutoBleem, cada jogo de PS1 tem, por padrão, o seu próprio cartão de memória, então você nunca precisa
se preocupar com espaço nem com qual cartão guarda qual save. O cartão fica junto com os save states do jogo, em
`Games/!SaveStates/<pasta do jogo>/`.

**Conjuntos de cartões compartilhados.** Às vezes um jogo precisa enxergar o save de outro: uma continuação que lê
o save do primeiro jogo, por exemplo, ou os jogos de uma série que você quer em um cartão só. Para isso você cria
um conjunto compartilhado, um cartão usado por vários jogos. Os conjuntos ficam em `Games/!MemCards/`, e você cuida
deles em *Cartões de memória*, no menu do sistema. Square cria um conjunto novo (você digita o nome com o teclado
na tela), Cross renomeia o selecionado e Triangle apaga, depois de perguntar. Para colocar um jogo em um conjunto,
use *Trocar cartão de memória* no editor do jogo (seção 3.7) ou o ícone *CARTÃO DE MEMÓRIA* dele.

**O editor de cartões de memória** abre pelo ícone *CARTÃO DE MEMÓRIA* de um jogo. Ele mostra o cartão do jogo e
um segundo cartão lado a lado, com o ícone e o título de cada save, como a tela de cartões de memória do console
original. Square copia o save selecionado para o outro cartão, Triangle apaga, e Select desfragmenta um cartão,
juntando os blocos livres para que um save grande volte a caber. Start deixa você escolher qual conjunto aparece à
direita, e Cross recarrega os dois cartões do pendrive. Um cartão em que o jogo ainda não gravou nada (um jogo em
que você ainda não salvou) está vazio e mostra *ainda sem cartão* ao lado do nome. Se você fez mudanças, o
AutoBleem pergunta *Deseja salvar os dados dos cartões de memória?* antes de sair do editor, de recarregar os
cartões ou de mostrar outro conjunto.

![O editor de cartões de memória](../images/en/memory-card-editor.jpg)

**Pontos de retomada.** Muitos jogos de PS1 só deixam salvar em certos lugares, e nem sempre você chega a um antes
de precisar parar. Os pontos de retomada resolvem isso: quando você sai de um jogo de PS1 pelo botão Reset do
console (ou pelo menu do emulador em um Pi ou em um PC), o AutoBleem guarda um save state exatamente do ponto onde
você estava. Enquanto ele grava, na saída do jogo, o emulador mostra *Please wait...*. Na próxima vez, você
continua daquele momento.

Você encontra esses pontos no ícone *CONTINUAR* do jogo. Um jogo com ponto de retomada mostra uma miniatura dele
no ícone; um jogo sem nenhum fica com o ícone em cinza. O seletor de slots tem quatro, mostrados como cartões com
moldura, cada um com uma imagem do momento, o número do slot e a data. O mais recente leva a marca **MAIS
RECENTE**, e um slot que ainda não foi usado diz *Sem ponto de retomada*. Cross continua o jogo a partir do slot
selecionado, e Triangle apaga o slot. Se o seletor aparece ou não quando você abre o jogo depende da configuração
*Retomar:* do jogo (seção 3.7).

Os jogos de PS1 que você joga no RetroArch também têm slots de retomada. Cada slot leva um selo, o logo do
AutoBleem 2 ou o do RetroArch, para você saber qual emulador o gravou.

![O seletor de slots de retomada](../images/en/resume-picker.jpg)

### 3.9 Abrindo jogos, RetroArch e apps

Abrir um jogo é o que você mais vai fazer, então basta um botão: selecione o jogo na prateleira e aperte
**Cross**. Um jogo de PS1 abre em tela cheia no emulador de PS1 que você escolheu em Opções (seção 3.6) e roda até
você sair. Se preferir jogar um jogo de PS1 no RetroArch (porque ele roda melhor lá, ou porque você gosta das
opções do RetroArch), aperte **Square**.

**Sair de um jogo.** No PlayStation Classic, os botões do próprio console fazem o que você espera. **Reset**, na
frente, leva você de volta ao launcher e guarda um ponto de retomada de onde você estava, para continuar depois
(seção 3.8); funciona até com o menu do jogo aberto. **Power** desliga o console. Um Raspberry Pi ou um PC não têm
esses botões, então neles você sai pelo menu do emulador, explicado mais abaixo.

Existe também uma saída que funciona igual em qualquer controle, seja o do console, um USB ou um Bluetooth:
**segure Start + Select, ou Home, por 2 segundos** e você volta para o AutoBleem. Um toque curto nesses mesmos
botões abre o menu do emulador. O launcher lembra você das duas coisas nas dicas dele (*Segure Select+Start ou Home
por 2 segundos: voltar ao AutoBleem* e *Toque curto em Select+Start ou Home: o menu do emulador*). Um app não tem
menu de emulador, então nele só o toque longo faz alguma coisa. No console, o Reset também sempre fecha um app.

**O menu do jogo.** Com o `pcsx-abnxt`, o emulador tem um menu próprio para o que você precisa durante o jogo:
salvar, trocar de disco, ajustar a imagem, escolher os controles. Aperte o botão de menu (Home em um controle que
tenha, **Select + Start** em um que não tenha, ou **Esc** no teclado) e o jogo pausa atrás do menu, com a última
imagem dele ao fundo. Segurar o botão de menu por 2 segundos faz o mesmo que o Reset: sai do jogo. O menu tem três
abas, e L1 e R1 passam de uma para outra. Ele lembra onde você estava, então da próxima vez abre na mesma aba e na
mesma linha.

- A aba **Jogo** é sobre o jogo em si. *Voltar ao jogo* fecha o menu e deixa você seguir jogando. Em
  *Salvamentos*, *Salvamento rápido* guarda o momento em que você está e *Carregamento rápido* traz esse momento de
  volta. *Carregar salvamento automático* volta o jogo para como ele estava até 30 segundos atrás: o emulador
  mantém essa cópia na memória enquanto você joga, e ela salva você de um erro que não dá para desfazer. Em *Disco
  CD*, *Trocar de disco* serve para um jogo de vários discos quando ele pede o próximo, e *Reiniciar o jogo*
  começa tudo de novo. *Salvar configurações para este jogo* guarda as configurações que você escolheu só para
  este jogo (seção 3.7). *Menu PCSX* abre as páginas do próprio PCSX-ReARMed, com as opções, os cheats e o Sobre
  dele, e *Sair* leva você de volta ao AutoBleem.
- A aba **Imagem** deixa você mudar a aparência do jogo enquanto assiste: *Tela*, *Resolução* (1x ou 2x),
  *Remover costuras*, *Dithering*, *Escala*, *Halo da tela*, *Suavização*, *Filtro*, *Máscara CRT*, *Scanlines* e
  *Brilho das scanlines*. São as mesmas configurações do editor do jogo (seção 3.7), e cada linha tem à direita
  uma linha de ajuda que explica para que ela serve. *Tela* é a resolução da tela; no console ela é escolhida em
  Opções, e aqui só aparece. *Halo da tela* é para as faixas escuras que sobram dos lados de uma imagem 4:3 numa TV
  widescreen: ele preenche essas faixas com as bordas da própria imagem, espelhadas e escurecidas, e assim o jogo
  parece se espalhar por elas em vez de ficar espremido entre duas barras pretas. *Máscara CRT* coloca sobre a
  imagem o padrão de fósforo de um tubo antigo - *Abertura* dá as listras finas de um Trinitron, *Fenda* e *Delta*
  os pontinhos de outros tubos; ela só existe com o filtro CRT (raster). O filtro CRT-Pi é pesado demais para o
  console em 1080p. Uma linha que não se aplica fica em cinza, e a linha de ajuda diz por quê.
- A aba **Controles** decide o que está ligado nas duas portas do PlayStation, *Controle 1* e *Controle 2*:
  um controle padrão (digital), um controle analógico (DualShock), uma pistola ou nada. Alguns jogos só funcionam
  com um tipo de controle. A mudança vale quando você volta para o jogo.

O menu usa o mesmo visual ab2.0.0 do launcher, para não parecer outro programa, e mostra a bateria dos seus
controles e a imagem do seu último quick save.

**Jogos do RetroArch.** Um jogo de outro sistema abre no RetroArch, com o núcleo que o launcher escolheu para
aquele sistema. Quando terminar, *Close Content* ou *Quit RetroArch* no menu do RetroArch trazem você de volta ao
launcher. Se quiser mudar qual núcleo roda um sistema, abra *Núcleos do RetroArch* no menu rápido (seção 3.4); a
lista abre com o núcleo *PlayStation 1* no topo. E se quiser o menu do próprio RetroArch (o XMB), com as
configurações e as listas de conteúdo dele, escolha *RetroArch* no menu do sistema: o RetroArch abre sem nada
carregado.

![A janela de núcleos do RetroArch, com o núcleo PlayStation 1 no topo](../images/en/retroarch-cores.jpg)

**Apps.** Apps são programas, não jogos: as ferramentas do console e, no console, os aplicativos extras que vêm no
pacote do RetroArch, como Doom, Quake, Amiga e outros. Você encontra os apps no conjunto Apps. Antes de um app
abrir, o AutoBleem mostra o leia-me dele, para você saber o que é e como se controla. Cross abre o app, e Circle
leva você de volta à prateleira.

![O leia-me de um app, mostrado antes de o app abrir](../images/en/app-start.jpg)

**As configurações de um app.** Muitos apps foram feitos para um controle específico, então você pode mudar como
eles enxergam o seu. Selecione o app, abra a fileira de ícones e escolha *Jogo*: abrem as *Configurações do jogo*
do app (*Change how this program is started*). *Modo do controle:* decide qual controle o app acha que tem.
*Automático* usa o que o próprio app pede; *Controle PSC* e *Controle Xbox 360* apresentam o seu controle como o do
console ou como um de Xbox 360, e *Controle PSC (sistema)* e *Controle Xbox 360 (sistema)* fazem o mesmo através do
próprio sistema. Experimente outro modo quando um app não responder ao seu controle como deveria. *Direcional como
analógico:* deixa o direcional mover o analógico, para um app que só escuta o analógico, e *Analógico como
direcional:* faz o contrário.

Alguns apps fazem uma pergunta na primeira vez que você os abre. Um quer saber *Quais comandos o seu controle
tem?*, para configurar os comandos dele: responda *Um direcional* para um controle que só tem o direcional, ou
*Analógicos*. Um app que roda o Windows pergunta *O que você quer fazer?* e oferece rodar o Windows, instalar,
rodar o DOS ou desinstalar o Windows. Quando um app deixa você definir uma tecla, ele pede *Pressione um dos
botões.*

![As configurações de jogo de um app](../images/en/app-game-settings.jpg)

Um programa de Windows executado pelo PE runner (um app PE, seção 3.3) conversa com você pelas telas do próprio
AutoBleem: uma mensagem que ele quer mostrar aparece como *Mensagem*, e uma pergunta com opções como *Escolha uma
opção*, cada uma com o nome do app como título.

![Uma pergunta de um app PE, mostrada como uma tela do AutoBleem](../images/en/pe-dialog.jpg)

### 3.9a Um disco em uma unidade USB

Você pode ligar um drive de CD/DVD USB comum ao console, a um Raspberry Pi ou a um PC iniciado pelo pendrive do
AutoBleem e jogar direto de um disco original de PlayStation, sem copiar nada. O disco que você coloca aparece no
launcher como mais um jogo. Isso não funciona no Windows.

**Copiar um disco para o pendrive.** Se você quer ter o jogo sempre à mão, sem o disco, aperte Square (*Copiar
disco*). O AutoBleem primeiro pergunta se deve copiar o jogo e quanto espaço ele vai ocupar, depois grava o jogo na
pasta `Games` como um único arquivo CHD (um jogo de vários discos ganha também um arquivo `.m3u`, para a troca de
disco funcionar dentro do jogo). Durante a cópia você vê a velocidade e o tempo que falta, e *Interromper* para a
cópia. Quando termina, o jogo está na prateleira como qualquer outro. O AutoBleem não copia um jogo que já está em
`Games`, nem um que não cabe; nesse caso ele diz quanto espaço precisa. Um disco riscado também pode ser copiado:
as partes que não puderam ser lidas são preenchidas com zeros, e o AutoBleem diz quantas foram. Uma cópia assim
pode funcionar ou não.

Square oferece a cópia para qualquer disco de jogo de PlayStation na tela do disco, mesmo um que os bancos de capas
não conheçam. Um jogo que os bancos conhecem é copiado com o título dele; para um jogo de vários discos, copie os
discos um depois do outro, e o `.m3u` lista todos em ordem, começando pelo disco 1. Um disco que os bancos não
conhecem recebe como nome o número de série, é copiado como um disco só e fica sem capa na prateleira. A janela de
cópia, *Copiando o disco*, fica na tela até a cópia terminar ou ser interrompida (o launcher espera enquanto isso)
e mostra a velocidade como um múltiplo de um drive de CD comum. Se a cópia falhar, o AutoBleem diz por quê.

![Copiando um disco](../images/en/disc-copy.jpg)

**Jogar direto do disco.** Quando você coloca um disco, a **tela do disco** abre sozinha assim que o disco é lido.
Ela mostra a capa do disco (dos bancos de capas ou baixada da internet) com o número de série e o título, e Cross
abre o jogo. Um jogo de PS1 jogado direto do disco guarda os pontos de retomada e os saves em uma pasta própria,
então você pode parar e continuar depois, como com um jogo do pendrive. Depois do jogo, ou depois de passar pelas
opções ou pelas configurações de uma extensão, você volta para a tela do disco. Se sair dela com Circle para ver
seus outros jogos, o disco continua na unidade e Circle na prateleira traz a tela de volta; em uma prateleira
vazia, R1 (*Disco*) também abre a tela. Em uma prateleira com jogos, R1 continua com a função de sempre, de pular
entre as letras iniciais. Quando você tira o disco, a tela do disco fecha.

![A tela do disco](../images/en/disc-view.jpg)

**O indicador da unidade**, no alto da tela, mostra o que a unidade está fazendo, para você saber se precisa
esperar. Sem unidade conectada, não aparece nada. Uma unidade sem disco mostra um ícone de disco apagado. Enquanto
um disco está sendo lido, o ícone pisca e diz *Lendo o disco...*, e quando o disco está pronto o ícone acende com o
título do disco. Se você colocar um disco que não é nem um jogo de PlayStation nem um CD de áudio, o indicador diz
*Este não é um disco PlayStation*, e se a unidade não conseguir ler o disco naquele momento, ele diz *O disco não
pode ser lido agora*.

![O indicador da unidade](../images/en/disc-chip.jpg)

**CDs de áudio.** A unidade também toca CDs de música. Um CD de áudio abre o **CD player** em vez da tela do disco.
Ele mostra o disco como *CD de áudio*, com a lista de faixas e a duração total, e a linha de baixo diz qual é a
faixa selecionada e se a repetição e o modo aleatório estão ligados. Um disco que o player não consegue tocar fica
marcado como *Este disco não pode ser reproduzido*. Estes são os botões dele:

| Botão | No CD player |
|---|---|
| Cross | Toca a faixa selecionada. |
| Start | Pausa a música e volta a tocar. |
| Square | Para a música. |
| L1 / R1 | Vão para a faixa anterior ou para a próxima. |
| L2 / R2 | Voltam ou avançam dentro da faixa, cinco segundos por vez. |
| Triangle | Muda o que se repete: nada, o disco inteiro ou a faixa atual. |
| Select | Liga ou desliga o modo aleatório, para as faixas tocarem em ordem sorteada. |
| Circle | Sai do CD player. |

![O CD player](../images/en/cd-player.jpg)

**Discos com LibCrypt.** Alguns jogos de PlayStation, a maioria europeus, têm uma proteção contra cópia chamada
LibCrypt. Para rodá-los, o emulador precisa de um pequeno arquivo `.sbi` com os dados dessa proteção. O AutoBleem
baixa esse arquivo do site sozinho antes de um disco desses rodar e quando você o copia, e o arquivo é copiado
junto com o jogo. Para isso ele precisa de rede: em um Raspberry Pi ou em um PC, a que eles já têm; no console, o
Wi-Fi que você configurou no PSC-Bios.

Para um disco na unidade, algumas configurações do jogo não fazem sentido, então o editor do jogo deixa essas
linhas em cinza (seção 3.7).

### 3.10 Adicionando jogos

O AutoBleem encontra seus jogos sozinho, desde que eles estejam no lugar certo. Esta seção mostra onde vai cada
tipo, para que toda varredura coloque os jogos na prateleira com nome e capa.

**Os jogos de PS1** vão na pasta `Games`, **cada um na sua própria pasta**, com o nome do jogo. Você também pode
agrupar jogos em pastas suas, e cada uma dessas pastas vira um grupo no seletor de conjuntos (seção 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                uma pasta de jogos: um grupo próprio no seletor de conjuntos
    Klonoa/                   Klonoa.pbp
```

O AutoBleem lê os formatos de imagem de disco mais comuns: `.cue` com o `.bin` (ou `.img`), `.pbp`, `.chd`
(inclusive os comprimidos com zstd), `.iso` e `.ecm`, que a varredura decodifica para você. Um jogo zipado também
funciona: o processador **Unzip** descompacta o jogo antes de a varredura lê-lo (seção 3.14).

Você não precisa ser organizado. Um jogo de vários discos fica em uma pasta só, com todos os discos, mas se você
copiar pastas chamadas `Game (Disc 1)`, `Game (Disc 2)` e assim por diante, a varredura junta tudo em uma única
pasta `Game`. Jogos jogados soltos direto em `Games/` também são separados em pastas próprias pela varredura.

**Nomes e capas** vêm sozinhos. A varredura lê o número de série de cada disco e pega o título, a publicadora, o
ano, o número de jogadores e a região no banco de dados de PlayStation do RetroArch ou nos bancos de capas. Se
quiser uma capa sua, coloque um PNG ou um JPEG ao lado da imagem do jogo, com o mesmo nome. Sem isso, a capa vem
dos bancos de capas ou, com o RetroArch instalado, das miniaturas do libretro; em um Raspberry Pi, um PC ou no
Windows, uma capa que falta é baixada da internet (Opções → *Buscar capas online*). Se a varredura errar alguma
coisa, corrija no editor do jogo e ligue *Trancar dados*, para que a próxima varredura mantenha a sua correção.

**Os jogos de outros sistemas** vão em `RetroArch/roms/`, **uma pasta por sistema, com o nome que os bancos de
dados do RetroArch dão a ele**: por exemplo `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo
Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` ou `FBNeo - Arcade Games` (ou
`Arcade`). As pastas já vêm criadas, e as ROMs podem continuar zipadas. Em um Raspberry Pi, um PC ou no Windows, a
varredura lê as ROMs sozinha e grava as playlists do RetroArch. O pendrive de um console não consegue fazer isso
sozinho, então ali você roda o **UpdateRoms** no PC (capítulo 5).

**Os apps** vão em `Apps/<nome>/`, cada um com um `app.ini` (o nome, o ícone e o que executar) e um `run.sh`.

**Pacotes.** Alguns apps são motores de jogo: eles precisam dos dados de um jogo que você tem para poder rodá-lo.
Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, jogos de DOS e
outros funcionam assim. Coloque os arquivos do jogo em uma pasta `Packages` no pendrive, uma pasta por jogo (por
exemplo `Packages/Doom/DOOM2.WAD`), e o AutoBleem reconhece os arquivos por uma tabela que vem com ele
(`rc/packages.ini`). Em uma pasta que ele reconhece, os arquivos de jogo soltos são pacotes por conta própria. O
AutoBleem só lê os seus arquivos e nunca os altera. Um pacote também pode vir da Loja (seção 3.13).

Onde o launcher mostra, a linha *Pacotes* da aba Apps (seção 3.3) lista os dados de jogo encontrados. Cross em um
item abre o **Package info** dele: o que os dados contêm, uma descrição, onde estão os arquivos e de onde eles
vieram (dos seus próprios arquivos, da Loja, de um mod, ou de arquivos que vêm dentro de um app), se são shareware
ou livres, e qual app instalado roda esses dados. Se nada do que você tem instalado conseguir rodá-los, o Package
info avisa.

Quando você abre um app de motor, o AutoBleem procura dados de jogo que ele consiga rodar. Com um conjunto de
dados só, o jogo abre na hora. Com vários, uma lista (*Escolher os dados do jogo*) pergunta qual você quer jogar, e
ela abre no que você escolheu da última vez. Se não houver nenhum, o AutoBleem diz quais dados o app precisa e onde
colocá-los, e nada abre.

**Seus próprios jogos.** Quando o AutoBleem não reconhece algum dado, o Package info dele diz *Não reconhecido. Se
for um jogo, veja o manual: Seus próprios jogos.* A tabela só conhece os jogos para os quais foi feita. Para um
outro, escreva uma linha para ele em um `packages.ini` seu dentro da pasta `Packages`: o AutoBleem lê o seu
primeiro, então as suas linhas têm prioridade.

![O seletor de pacotes, onde você escolhe com quais dados de jogo começar](../images/en/packages-picker.jpg)

![Package info](../images/en/package-info.jpg)

**Varrer só uma parte.** Se você só adicionou jogos a um conjunto ou a uma pasta, *Reescanear jogos* pode varrer
só essa parte, o que é mais rápido do que varrer tudo, e o balão dela some quando termina.

**Os temas** vão em `Themes/<nome>/`, com o `theme.json` e as imagens deles; ou coloque o zip do tema em `Themes/`
do jeito que ele veio.

### 3.11 A BIOS do PS1

A BIOS é o programa de inicialização do próprio PlayStation, e o emulador roda os jogos com mais fidelidade usando
a BIOS original. Em um **PlayStation Classic** você não precisa fazer nada: o emulador usa a BIOS do próprio
console. Em um **Raspberry Pi, um PC ou no Windows**, coloque os seus próprios arquivos de BIOS do PS1 em
`System/Bios/`: `romw.bin` (a SCPH-5501/5502 americana/europeia) e `romJP.bin` (a SCPH-5500 japonesa, usada para os
jogos japoneses). Os instaladores preenchem esses arquivos com os pacotes de BIOS do RetroArch, a não ser que os
seus já estejam lá; eles nunca substituem os seus. Sem esses arquivos, o emulador roda com a BIOS HLE embutida, uma
substituta que muitos jogos aceitam e alguns não; então, se um jogo não iniciar, a primeira coisa a conferir é se
falta a BIOS.

### 3.12 Atualizações

O AutoBleem se mantém atualizado sozinho, então você ganha recursos novos e correções sem reinstalar nada. Quando o
launcher inicia, e depois uma vez por dia, ele consulta o site atrás de uma versão nova no seu **canal**. Você
escolhe o canal em Opções → *Atualizações*: `release`, `testing`, `nightly`, ou `off` se não quiser que ele procure
nada. Se não quiser esperar a verificação diária, *Atualização de software* no menu do sistema verifica na hora.

Quando há uma versão nova, o AutoBleem pergunta o que fazer. *Atualizar agora* baixa e instala a versão, o que leva
alguns minutos. *Lembrar amanhã* pergunta de novo no dia seguinte, e *Pular esta versão* não pergunta mais sobre
essa versão. Seja qual for a sua escolha, seus jogos, saves e configurações sempre continuam lá; depois de uma
atualização, o launcher varre seus jogos mais uma vez. A etiqueta do canal no canto superior esquerdo (seção 3.1)
mostra qual build você tem.

Como a atualização é instalada depende da máquina:

- Em um **Raspberry Pi** e no **pendrive de PC**, o instalador roda de novo depois do download, com a mesma tela de
  progresso da primeira inicialização, e oferece também um RetroArch mais novo. Depois o launcher volta.
- No **Windows**, o instalador baixado abre, instala a versão nova e abre o novo launcher.
- Em um **PlayStation Classic**, só um console com o **kernel do AutoBleem** (ABFlashKit, seção 6.2) e uma **rede
  Wi-Fi** configurada no PSC-Bios (seção 6.1) consegue se atualizar sozinho; um console original não tem rede,
  então o launcher nem procura. Depois de *Atualizar agora*, o launcher fecha e a imagem do AutoBleem fica na tela
  enquanto o pendrive é atualizado, o que leva alguns minutos; depois o novo launcher abre. Sem rede, *Atualização
  de software* avisa *Não conectado*. Qualquer pendrive de console também pode ser atualizado a partir de um PC com
  o `AutoBleemInstaller.exe` (seção 2.1).

### 3.13 Extensões e a Loja do AutoBleem

**As extensões** acrescentam coisas novas ao launcher, com telas e recursos próprios, sem mudar o AutoBleem em si.
A Loja do AutoBleem e o PSC-Bios são extensões. Uma extensão mora em `Extensions/<nome>/` no pendrive (em um
Raspberry Pi, na partição de dados; no Windows, na pasta de dados); para instalar uma, descompacte o zip dela ali.

Para vê-las, abra o menu do sistema (**L2 + R2**) e escolha *Extensões*. As que vêm da equipe do AutoBleem ficam no
topo, e as outras vêm depois, sob *Extensões de terceiros*. Cross abre a selecionada, e Triangle desliga a extensão
ou liga de novo. O PSC-Bios no console é a exceção: é com ele que você configura o Wi-Fi, os controles e o relógio,
então ali ele não pode ser desligado. Quando uma extensão não consegue rodar, a linha dela diz por quê: ela precisa
de rede e não há, não foi feita para este sistema, foi feita para outra versão do AutoBleem e precisa de
atualização, ou não pôde ser carregada. Se alguma vez uma extensão derrubar o launcher, o AutoBleem desliga essa
extensão e a lista avisa; você pode ligá-la de novo aqui.

![A lista de extensões](../images/en/extensions.jpg)

**A Loja do AutoBleem** é a primeira extensão: um lugar para ver apps e jogos e instalá-los com um toque, em todos
os sistemas em que o AutoBleem roda. Um PlayStation Classic precisa do kernel do AutoBleem para ela, porque o
Wi-Fi vem com o kernel. Você abre a Loja pelo menu rápido (*Loja*, seção 3.4). Ela tem quatro abas, e L1 e R1
passam de uma para outra.

As abas **Apps** e **Games** listam o que as fontes oferecem, cada item com a imagem, a versão, o tamanho e o
pequeno ícone da fonte de onde vem. A aba Apps também lista apps PE, com a licença e a origem deles, e pacotes de
dados de jogo (seção 3.10). O que você já instalou leva um selo *Installed*. A barra de dicas mostra os botões que
valem para a linha selecionada:

| Botão | Nas abas Apps e Games |
|---|---|
| Cross | Instala o item; ou atualiza, tenta de novo depois de uma falha, ou cancela um download que está esperando ou em andamento. |
| Triangle | Remove algo que a Loja instalou. |
| Square | Atualiza as listas a partir das fontes. |
| L2 / R2 | Pulam para a letra inicial anterior ou seguinte. |
| Select | Mostra uma fonte por vez, quando você quer ver o que uma única fonte oferece. |
| Start | Pesquisa nos títulos. |

As imagens ficam guardadas depois de carregadas, então as listas aparecem rápido da próxima vez, e uma imagem que
não carregou pode ser tentada de novo.

A aba **Downloads** mostra o que está baixando, esperando, o que falhou e o que já foi instalado, com uma barra de
progresso que anda de forma contínua. Você não precisa ficar olhando: os downloads continuam em segundo plano,
mesmo depois que você sai da Loja, e enquanto você está em outra parte do launcher um balão mostra o download em
andamento com a velocidade e o tempo que falta (por exemplo `1.4 MB/s · 0:42`). Abrir um jogo ou desligar só pausa
os downloads, e um download interrompido continua de onde parou. Se a rede cair, o item diz *Waiting for the
network* e continua de onde estava quando a rede voltar; depois de 30 minutos sem rede, ele desiste. Downloads de
mais de 2 GB funcionam em todas as plataformas, inclusive nas builds de 32 bits. Um jogo que você instala aparece
na prateleira depois da próxima varredura, com a imagem da Loja como capa.

A aba **Sources** mostra de onde vêm as listas, cada uma com o seu ícone: o catálogo do próprio AutoBleem, qualquer
lista TSV colocada em `System/Extensions/store/sources/` e os endereços que você mesmo adiciona com *Add a source
URL*. Cross em uma fonte que você adicionou deixa você renomeá-la, mudar o endereço, trocar entre `http://` e
`https://` ou removê-la.

![A aba Apps da Loja](../images/en/store-apps.jpg)

![O menu de uma fonte que você adicionou](../images/en/store-source-menu.jpg)

O que o catálogo do próprio AutoBleem oferece também aparece no site de downloads, em
`https://autobleem.retromenele.pl/store/`. Uma fonte que você mesmo adiciona é outra história: **você é
responsável pelo que as fontes que você adiciona contêm.**

**Seus próprios jogos na sua rede.** Se você guarda seus jogos de PS1 em outro computador da casa, o `abstored`, o
servidor de rede local da Loja, pode oferecê-los à Loja pela sua rede, para você instalá-los como qualquer outro
item. Ele roda em qualquer máquina Linux (um Raspberry Pi, um servidor caseiro) e só lê a pasta, sem nunca
alterá-la. Inicie com `abstored <pasta de jogos>` e abra `http://<essa máquina>:8124/` em um navegador: a página
mostra o que ele está servindo e qualquer problema que tenha encontrado. Na Loja, adicione
`http://<essa máquina>:8124/store.tsv` como fonte. Programas prontos para Linux e Windows estão na página da Loja,
na aba **LAN server**, e o `INSTALL-linux.md` (`ext_store/server/` no código-fonte) explica como configurá-lo como
serviço. O **LAN Share** (seção 5.2) coloca jogos e discos de um PC em um servidor desses.

### 3.14 Processadores de varredura

Os processadores de varredura preparam seus jogos antes de o AutoBleem lê-los. Um processador é um programinha que
toda varredura roda primeiro. Ele pode transformar um formato que o AutoBleem não lê em um que ele lê (descompactar
um jogo zipado, por exemplo) ou mudar os dados de um jogo, como aplicar um patch de tradução. Os processadores
moram em `System/Processors/<nome>/` no pendrive (em um Raspberry Pi, na partição de dados; no Windows, na pasta de
dados); para instalar um, descompacte a pasta dele ali, e a próxima varredura já roda o processador.

**O Unzip vem com o AutoBleem.** Ele descompacta os jogos de PS1 zipados em `Games/` antes de a varredura lê-los, e
as ROMs zipadas uma de cada vez; os sets de fliperama continuam zipados, porque é assim que os núcleos de
fliperama os leem. Atualizar o AutoBleem atualiza também o Unzip, e se você o desligou, ele continua desligado.

Um processador faz o trabalho dele uma vez só: depois de cuidar de um jogo, ele não roda de novo nesse jogo até o
jogo mudar. Enquanto um processador trabalha, o balão no canto superior direito mostra o que ele está fazendo, e
um aviso ou uma falha aparece na linha de baixo; o `processors.log`, na pasta de logs, tem os detalhes. Abrir um
jogo ou o RetroArch interrompe um processador que altera arquivos, para que o jogo fique com a máquina só para
ele, e a próxima varredura termina o trabalho.

Para gerenciar os processadores, abra o menu do sistema (**L2 + R2**) e escolha *Processadores de varredura*. Você
vê os processadores na ordem em que rodam, com uma aba para os jogos de PS1 e outra para as ROMs; L1 e R1 trocam
de aba. A ordem importa: um processador que descompacta precisa vir antes de um que aplica patch no que foi
descompactado.

| Botão | Em Processadores de varredura |
|---|---|
| Square | Pega o processador selecionado, para Cima e Baixo levarem ele ao novo lugar; Square solta de novo. |
| Cross | Desliga o processador, ou liga de novo. |
| Triangle | Faz o processador olhar todos os jogos de novo na próxima varredura, inclusive os que ele já tratou. |
| Circle | Volta, e inicia uma varredura se você mudou alguma coisa. |

Um processador feito para outra máquina continua na lista, em cinza, para você ver que ele está lá, mas que não
roda aqui.

![Processadores de varredura](../images/en/processors.jpg)

Se você quiser escrever um processador seu, a página do Unzip, `https://github.com/autobleem2/proc_unzip`, explica
tudo o que um processador precisa fazer, e o `tools/proc_check.py`, no código-fonte do AutoBleem, confere o seu
antes de você compartilhá-lo.

<!-- pagebreak -->

## 4. Telas

### 4.1 Gerenciador de Jogos

O Gerenciador de Jogos é onde você arruma a sua biblioteca de PS1. Use quando quiser tirar um jogo que você não
joga mais, abrir as configurações de um jogo sem procurá-lo na prateleira, ou fazer o AutoBleem buscar todas as
capas de novo. Ele abre pelo menu do sistema (L2 + R2, *Gerenciador de Jogos*). Enquanto uma varredura roda, ele
fica cinza e espera a varredura terminar.

A tela tem o título *Gerenciador de jogos - selecionar jogo*. À esquerda você vê todos os seus jogos de PS1 em uma
lista de títulos em ordem alfabética; à direita, a capa do jogo selecionado com a publicadora, o ano, o número de
série e a pasta em que ele está. O espaço livre que sobra na unidade aparece no canto superior direito, para você
ver quanto espaço recupera ao apagar algo. Cima e Baixo passam pela lista, L2 / R2 viram a página e L1 / R1 pulam
para o primeiro ou para o último jogo.

- **Cross** abre o jogo selecionado no editor do jogo, o mesmo do ícone Jogo na prateleira (seção 3.7). Quando
  você sai dele, volta para o mesmo jogo na lista.
- **Square apaga o jogo.** O AutoBleem pergunta primeiro e depois remove a pasta inteira do jogo. Se os save
  states e o cartão de memória do jogo não forem usados por nenhum outro jogo, ele faz uma segunda pergunta: se
  deve apagar esses também. Responda que não se você acha que pode querer o jogo de volta mais tarde, com os seus
  saves.
- **Triangle apaga todas as imagens de capa** (PNG ou JPEG) que estão ao lado dos seus jogos, depois de uma
  pergunta. Isso é útil quando você juntou capas de que não gosta: a próxima varredura pega as capas dos bancos de
  capas de novo.

No fim da lista, depois dos jogos, podem aparecer pastas marcadas como *Não adicionado*. São pastas de `Games` que a
varredura examinou mas não conseguiu transformar em jogo. Selecione uma e o lado direito mostra onde ela está e por
que não foi adicionada; por exemplo, por falta do arquivo cue (capítulo 7). Square apaga uma pasta dessas, depois
de uma pergunta. Quando você sai com Circle depois de ter mudado alguma coisa, o AutoBleem varre os jogos de novo.

![O Gerenciador de Jogos: a lista de jogos à esquerda, a capa e as informações do jogo selecionado à direita](../images/en/game-manager.jpg)

### 4.2 Informações de hardware

Informações de hardware é a página para olhar quando você quer saber que máquina é a sua e o que ela enxerga:
quanto espaço sobra no pendrive, qual endereço de rede ela tem, quais drivers de vídeo e de áudio ela usa e quais
controles estão conectados. É a mesma página em todas as plataformas, inclusive no console. Ela abre pelo menu do
sistema (L2 + R2, *Informações de hardware*); Circle leva você de volta ao menu do sistema.

A página mostra o sistema, o hardware, o armazenamento com o espaço livre, os endereços de rede, os drivers de
vídeo e de áudio e os controles conectados. Ela lê tudo de novo a cada segundo, então você pode deixá-la aberta
enquanto conecta um controle ou um cabo e ver a mudança aparecer. Ela só mostra as coisas; para configurar a rede
ou um controle, use *Rede e controles* (PSC-Bios, capítulo 6).

A parte dos controles responde à pergunta "qual controle é qual jogador?". Os dois primeiros controles aparecem
como *Jogador 1* e *Jogador 2*, as portas que o emulador de PS1 dá a eles. Qualquer controle a mais aparece como
*não utilizado pelo emulador de PS1*. O RetroArch distribui as portas pelas configurações dele, então em um jogo do
RetroArch a ordem pode ser outra. Você não precisa abrir esta página toda vez: sempre que um controle é conectado
ou desconectado, o launcher mostra rapidamente qual controle agora é o jogador 1 e qual é o jogador 2.

![Informações de hardware: os dados da máquina e os controles conectados](../images/en/hardware-info.jpg)

### 4.3 O guia de botões

Se você esquecer o que um botão faz em algum lugar, aperte **Triangle** na prateleira. O guia de botões mostra todos
os botões de todas as telas em uma página só, para você consultar sem sair do launcher. Se um teclado USB estiver
conectado, ou já tiver sido usado, uma coluna *Teclado* mostra a tecla correspondente ao lado de cada botão do
controle.

O guia também lembra você da única coisa que vale a pena guardar de cabeça para qualquer jogo: como sair dele.
Segure Select + Start, ou Home, por 2 segundos para voltar ao AutoBleem; um toque curto abre o menu do emulador.

![O guia de botões: os botões de cada tela, com as teclas do teclado ao lado](../images/en/button-guide.jpg)

### 4.4 O teclado na tela

Sempre que o AutoBleem precisa que você digite alguma coisa (o nome de um conjunto de cartões de memória, o título
de um jogo, uma senha de WiFi, o endereço de uma fonte da Loja), aparece o mesmo teclado na tela, para você
digitar só com o controle. Ele é organizado como o teclado de um celular. Além das letras, tem uma página de
símbolos, com `/ \ : ? & = % @ #` e o resto do que um endereço ou uma senha pedem, e duas páginas de letras
acentuadas. A fileira de baixo tem Shift, a tecla que troca de página, Espaço, Apagar e Confirmar.

Ande pelas teclas com as direções e aperte **Cross** para digitar a que está sob o cursor. **Triangle** apaga uma
letra e **Square** digita um espaço. **L1** é o Shift; aperte duas vezes para o Caps Lock. **R1** vai para a
próxima página de teclas, e **L2 / R2** movem o cursor dentro do texto. **Start** confirma o que você digitou e
**Circle** cancela. Se um teclado USB estiver conectado, você pode digitar nele a qualquer momento: Enter confirma
e Esc cancela.

![O teclado na tela](../images/en/keyboard.jpg)

### 4.5 Gamepad virtual

Os apps (os programas do conjunto Apps, como Doom ou Quake) não leem o seu controle sozinhos. Um pequeno programa
auxiliar, o daemon do gamepad virtual, lê os controles de verdade e entrega a cada app um controle que ele entende.
Esta página mostra quais controles esse auxiliar enxerga e como ele os lê. Olhe aqui quando um app não responder
ao seu controle ou estiver com os botões trocados. Ela abre pelo menu do sistema (L2 + R2, *Gamepad virtual*);
Circle leva você de volta ao menu do sistema.

Em *Controles que o daemon vê*, cada controle aparece com um número e o nome. Ao lado você lê três coisas: se o
auxiliar conseguiu abrir o controle (*conectado*) ou não (*ilegível*); o driver por onde o controle chegou; e de
onde vem o layout dos botões dele. *do banco de dados de controles* quer dizer que o controle é conhecido e os
botões estão onde deveriam; *adivinhado pelo daemon* quer dizer que ele não é conhecido e o auxiliar fez o melhor
palpite que pôde. Se os botões em um app parecerem errados, o motivo provável é um layout adivinhado.

O auxiliar só roda enquanto um app está rodando, então a página pergunta a ele uma vez, quando abre. Se você
conectar um controle com a página aberta, aperte **Cross** (*Procurar de novo*) para perguntar de novo. No Windows
não existe esse auxiliar, e a página diz *Não está nesta versão*.

![Gamepad virtual: os controles que o auxiliar dos apps enxerga](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. No PC

### 5.1 UpdateRoms: atualizando o pendrive do console

Em um Raspberry Pi, um PC ou no Windows, a varredura do launcher organiza seus jogos do RetroArch em listas e
baixa as capas sozinha. O PlayStation Classic não consegue fazer isso, porque não tem rede própria. O
**UpdateRoms** faz esse trabalho no seu PC com Windows: ele usa a rede do PC, mas grava tudo com os caminhos que o
console espera, então, quando você coloca o pendrive de volta, o console inicia e encontra tudo no lugar. Rode o
UpdateRoms sempre que adicionar ou remover jogos do RetroArch no pendrive de um console.

1. Copie suas ROMs para o pendrive, em `RetroArch/roms/<sistema>/` (seção 3.10). Os nomes das pastas precisam ser
   os nomes dos bancos de dados do RetroArch; o instalador já criou os mais comuns.
2. Abra o **`UpdateRoms\UpdateRoms.exe` a partir do pendrive**; o instalador deixou ele lá. Ele descobre sozinho
   em qual pendrive está. Enquanto trabalha, você vê uma linha dizendo o que ele está fazendo, uma barra de
   progresso e um log.
   - Se o pendrive ainda não tem o banco de dados do RetroArch, ele baixa primeiro o pacote de bancos de dados do
     RetroArch. Depois identifica cada ROM com ele, para que um jogo que o banco conhece receba o nome certo.
   - Ele grava uma playlist por sistema em `RetroArch/bin/playlists/`, com os caminhos do console. Tudo o que o
     próprio RetroArch tiver adicionado a essas listas é mantido.
   - Para cada ROM sem capa, ele baixa uma capa dos servidores de miniaturas do libretro para
     `RetroArch/bin/thumbnails/`.
3. Remova o pendrive com segurança e coloque de volta no console. A aba RetroArch do seletor de conjuntos agora
   lista todos os sistemas que têm jogos.

Você pode rodá-lo quantas vezes quiser: uma pasta em que nada mudou é pulada, então uma segunda rodada é rápida. Se
algo der errado, o log é o `System/Logs/updateroms.log` no pendrive. O cartão de um Raspberry Pi em um leitor de
cartões pode ser atualizado do mesmo jeito, com `UpdateRoms.exe <unidade> --target rpi`, embora um Pi faça isso
sozinho quando tem rede.

### 5.2 LAN Share: seus jogos e discos no servidor da sua rede

A Loja pode instalar jogos de um servidor na sua própria rede de casa (seção 3.13). O **LAN Share** é o programa de
Windows que abastece esse servidor a partir do seu PC: ele coloca no servidor os jogos de PS1 que você tem no PC, e
também consegue ler um disco de PS1 no drive de CD/DVD do PC e mandar para lá. O servidor é um `abstored` rodando
em um Raspberry Pi, em um NAS ou em outro PC. Quando um jogo está nele, a Loja do console, do Pi ou do PC pode
instalá-lo de lá.

O `LanShare.exe` está na página da Loja, na aba **LAN server**. Não há nada para instalar: abra o programa, e ele
guarda as configurações em `%LOCALAPPDATA%\AutoBleem LAN Share\`.

![A janela do LAN Share: os jogos do servidor à esquerda, os jogos deste PC à direita](../images/en/lanshare.jpg)

1. **Conecte ao servidor.** Digite o endereço dele do jeito que a Loja usa, `http://<endereço dele>:<porta>`, e
   clique em **Connect**. À esquerda aparecem os jogos que já estão no servidor e qualquer problema que a
   varredura do próprio servidor tenha encontrado. Para colocar jogos no servidor, o LAN Share precisa de um de
   dois caminhos de acesso:
   - **Share** é a pasta de jogos do servidor do jeito que ela é compartilhada na sua rede (Samba), por exemplo
     `\\raspberrypi\games`. O LAN Share copia os jogos para ela e pede ao servidor que faça uma varredura; o
     servidor em si continua só lendo a pasta dele.
   - **Token** é para um servidor iniciado com `--allow-uploads`. Digite o token dele: o servidor mostra o token
     quando inicia e guarda em `<state>/upload-token`. Aí o LAN Share envia por HTTP, e um envio que para no meio
     continua de onde parou.
2. **Publique os jogos do seu PC.** Escolha a pasta onde estão seus jogos (uma pasta por jogo), marque os que você
   quer e clique em **Publish the ticked games**. **On the server** mostra se o servidor já tem um jogo (ele compara
   o número de série, ou o título quando não há número de série), e um jogo que o servidor já tem nunca é enviado
   duas vezes. **Tick those not on the server** marca todos os outros para você.
3. **Publique um disco.** Coloque um disco de PS1 no drive do PC e clique em **Read a disc and publish it**. O LAN
   Share lê o disco inteiro para um `.bin` + `.cue`, com o nome do título do jogo. Para um jogo com LibCrypt, ele
   grava também o arquivo `.sbi`, quando o drive consegue ler o subcanal. Se você escolheu os bancos de dados (veja
   abaixo), ele confere a cópia com o dump bom conhecido. Depois publica o jogo. Para um jogo de vários discos,
   marque antes **The game has more than one disc**: o LAN Share pede cada próximo disco e publica todos juntos como
   um jogo só.
4. **Tire jogos do servidor.** Selecione os jogos e clique em **Remove from the server...**. Nada é apagado: cada
   jogo é movido para uma pasta `.removed` ao lado dos jogos do servidor, e movê-lo de volta o coloca de volta.

Os **Databases** são opcionais. Se você apontar o LAN Share para a pasta de capas do AutoBleem (`coversU/P/J.db`) e
para o `Sony - PlayStation.rdb` do RetroArch, ele usa esses arquivos para dar nome aos jogos e para conferir um
disco que leu.

Se preferir não copiar nada, marque **Also share the games on this PC with the Store** (vem desmarcado): o LAN
Share passa a servir a pasta de jogos do seu PC direto para a Loja. Na primeira vez que você fizer isso, o Windows
pergunta sobre o firewall; permita só redes privadas.

<!-- pagebreak -->

## 6. As ferramentas do console (PlayStation Classic)

Duas ferramentas vêm com o pendrive de um PlayStation Classic e ajudam você a configurar o console além do que ele
faz de fábrica. As duas têm a cara do resto do launcher, com o tema e o idioma dele, e você usa as duas com o
controle; no assistente de controles, também com os botões da frente do console. O **PSC-Bios** é uma extensão
que vem com o pacote do console: o item *Rede e controles* do menu rápido e do menu do sistema abre ele, e você
também o encontra na lista de Extensões. O **ABFlashKit** é um app, no conjunto Apps.

### 6.1 PSC-Bios

O PSC-Bios é onde você conecta a máquina ao mundo: a sua rede WiFi, o fuso horário, os controles Bluetooth e o
layout dos botões de um controle que o AutoBleem não conhece. Ele vem com o pacote do console e também está
disponível em um Raspberry Pi e no pendrive de PC. Abra com *Rede e controles* no menu do sistema (ou no menu
rápido), ou pela lista de Extensões. Se a extensão estiver instalada mas desligada, o item *Rede e controles* fica
cinza e diz que *está desligada - ative-a em Extensões*; aperte Cross nele e a lista de Extensões abre no
PSC-Bios, para você ligá-lo de novo.

A primeira tela dá um panorama: a hora e o fuso horário, os adaptadores de rede (WiFi, Ethernet, Bluetooth) com
seus endereços e todos os controles conectados, com uma observação dizendo se cada um tem mapeamento de botões. No
console, as partes de rede e de Bluetooth precisam do kernel do AutoBleem (seção 6.2); em um Raspberry Pi ou no
pendrive de PC, elas usam as ferramentas do próprio sistema. O assistente de controles funciona em todo lugar.

![PSC-Bios: a central de Rede e controles](../images/en/pscbios-main.jpg)

Da primeira tela, cada parte fica a um botão de distância:

| Botão | O que abre |
|---|---|
| Select | **Wi-Fi Network** conecta você ao seu WiFi (pelo kernel, ou pelo NetworkManager em um Pi ou PC): digite o nome da rede ou escolha em uma busca, digite a senha, escolha o modo do driver e aperte *Apply / Restart Network*. O fuso horário também é definido aqui, e depois de conectado você vê o endereço IP do console. |
| Square | **Bluetooth Controllers** procura controles Bluetooth como o DualShock 4, para você parear um novo ou remover um que não usa mais. |
| L1 | **DualShock 3 Pairing** conecta o seu primeiro DualShock 3, que para isso precisa estar ligado por USB, pelo plugin sixaxis do kernel. |
| R1 | **Controller Mapping** abre o assistente de controles, explicado abaixo. |
| Triangle | **About** mostra o que é o PSC-Bios. |
| Circle | **Back** tira você do PSC-Bios, de volta ao launcher. |

**O assistente de controles.** Use quando um controle não faz nada no AutoBleem ou está com os botões nos lugares
errados. Ele mostra o controle conectado do jeito que ele realmente é (cada eixo, botão e direcional como números)
e um desenho de DualShock que acende conforme você aperta. Como ainda não dá para confiar no controle que você está
testando, o assistente é comandado pelos **botões da frente** do console: **RESET** passa para o próximo controle,
**OPEN** começa o mapeamento e **POWER** cancela ou sai. Durante o mapeamento, o assistente pede um botão depois do
outro: aperte o botão que está aceso no desenho, ou OPEN se o seu controle não tiver esse botão. Um toque curto é
mapeado normalmente.

Você também pode sair pelo controle: segure Circle por 2 segundos; uma barra vai enchendo e o rodapé diz *Hold 2 s:
Exit*. Enquanto o controle ainda não tem mapeamento, segurar qualquer botão por 2 segundos faz o mesmo (*Hold any
button 2 s: Exit*). No teclado, Esc, Espaço e Enter fazem o papel de POWER, RESET e OPEN.

No final, o novo mapeamento entra em uso para você testar, e OPEN salva o mapeamento com um nome que você escolhe.
A partir daí, o launcher carrega esse mapeamento sempre.

![PSC-Bios: o assistente de mapeamento de controles](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit: o kernel do AutoBleem

O kernel do AutoBleem substitui o kernel Linux original do console, e é opcional. Ele vale a pena se você quer
tirar mais do console: dá a ele um relógio que funciona, faz funcionar adaptadores USB de WiFi e de Bluetooth (para
o PSC-Bios e os controles Bluetooth) e acrescenta o suporte aos botões da frente que o emulador usa para os pontos
de retomada. O ABFlashKit é a ferramenta que instala esse kernel. Antes de tudo, ele faz um backup do console, e
também consegue devolver o console ao estado original pela recuperação da própria Sony.

> **Esta ferramenta grava na memória flash do console.** Se a gravação for interrompida (a energia cai ou o
> pendrive é retirado), o console pode não ligar mais, e instalar um kernel personalizado anula a garantia dele.
> Mantenha o console ligado na tomada e o pendrive conectado até o console reiniciar sozinho. O ABFlashKit abre com
> este aviso: *I understand* segue em frente, *Quit* sai.

![O menu do ABFlashKit](../images/en/abflashkit-menu.jpg)

O ABFlashKit tem três ações:

- **Flash Kernel** instala o kernel. Se ainda não houver um backup de recuperação no pendrive, ele primeiro faz um
  das partições do console (`LBOOT.EPB`). Ele confere o backup e a imagem do kernel, grava o kernel e os arquivos de
  sistema do AutoBleem e reinicia o console. Quando aparecer *All done - when the screen goes black replace power
  cord*, espere a tela ficar preta, depois tire o cabo de energia do console e coloque de volta.
- **Full backup** salva as quatro partições do console em `LBOOT.EPB`, para você poder restaurá-las depois. Se já
  houver um backup, ele pergunta antes de sobrescrever.
- **Restore Mode** é o caminho de volta ao firmware original. Ele confere se o backup no pendrive é de um console
  original, liga a flag de recuperação e reinicia na recuperação da Sony, que restaura o console a partir do
  `LBOOT.EPB`.

Uma barra de progresso embaixo de cada etapa mostra o andamento. O ABFlashKit não grava em um console que roda
outro firmware personalizado, como o BleemSync ou o Project Eris: devolva esse console ao estado original primeiro.

**Entrando pelo PC.** Se você conhece Linux e quer olhar o console por dentro, pode entrar nele a partir de um PC
por um cabo USB. Isso precisa do kernel do AutoBleem; não funciona em um console original.

1. Ligue a porta micro-USB do console ao PC com um cabo USB. O PC enxerga o console como um novo adaptador de rede,
   e você encontra o endereço do console nas configurações desse adaptador no PC.
2. Entre com `ssh root@<endereço do console>`. A senha padrão é `autobleem`.

Em vez da senha, você pode usar uma chave. Coloque a sua chave pública no arquivo `System/ssh/authorized_keys` do
pendrive e reinicie o console: na próxima inicialização ela é adicionada à conta root. Atualizar ou reinstalar o
launcher não remove a chave.

> **A senha padrão é a mesma em todos os consoles**, então qualquer pessoa que consiga ligar um cabo no seu pode
> entrar como root. Use uma chave sempre que puder, e não deixe um console com a senha padrão ao alcance de
> outras pessoas.

<!-- pagebreak -->

## 7. Se algo der errado

A maioria dos problemas tem uma causa simples. Abaixo, cada um começa pelo que você vê, explica por que acontece e
depois diz o que fazer. Se você precisar pedir ajuda, os logs são a primeira coisa que vão pedir, então eles vêm
primeiro.

**Encontrando os logs.** O AutoBleem guarda os logs na memória enquanto roda, para não ficar gravando no pendrive o
tempo todo. Eles só chegam a `System/Logs/`, no pendrive, no cartão ou na pasta de dados, quando algo deu errado:
quando o launcher, um jogo de PS1 ou o RetroArch travam, os logs são salvos em `System/Logs/crash-<n>/` (os dos três
últimos travamentos ficam guardados), e o launcher avisa uma vez quando volta. Se você está caçando um problema que
não é um travamento, guarde todos os logs: ligue Opções → *Diagnóstico* → *Manter os logs no pendrive* (vale a
partir da próxima inicialização), ou crie pelo PC um arquivo vazio `System/Logs/keep`. *Informações de hardware*
(seção 4.2) também mostra onde ficam os logs, e Square ali salva os atuais em `System/Logs/saved-<n>/`.

Estes são os arquivos que você vai encontrar:

| Arquivo | O que ele conta |
|---|---|
| `autobleem.log` | O que o próprio launcher fez. |
| `launch.log`, `pcsx.log` | Como um jogo de PS1 foi aberto e o que o emulador disse enquanto rodava. |
| `retroarch.log` | O que o RetroArch disse enquanto rodava. |
| `update.log` | Como foi uma atualização online; esse fica sempre guardado no pendrive. |
| `updateroms.log` | Como foi o UpdateRoms no PC (capítulo 5); esse fica sempre guardado no pendrive. |

**Uma imagem pede para você colocar o pendrive, ou o console entrou em espera.** O AutoBleem não encontra o
pendrive dele: nenhum estava conectado quando o console ligou, ou ele foi retirado. Coloque-o em qualquer porta USB
(de preferência uma da frente, seção 2.1) antes de os 5 minutos acabarem, ou aperte Power. Se o pendrive não foi
retirado do jeito certo, o AutoBleem verifica ele primeiro; espere a barra de progresso terminar.

**O RetroArch diz que *precisa de uma biblioteca do sistema mais nova do que a deste console*.** Esse RetroArch foi
compilado para um sistema mais novo que o do console, então não consegue rodar nele. Use o RetroArch que acompanha
o AutoBleem.

**Um jogo diz que *é protegido pela licença PSN e não pode ser iniciado*.** Jogos comprados na PlayStation Network
ficam presos à licença, e o AutoBleem não consegue rodá-los. Não há o que consertar.

**Um jogo não aparece na prateleira.** Normalmente a pasta dele não está organizada como a varredura espera. Confira
se cada jogo tem a sua própria pasta e está em um dos formatos da seção 3.10. O *Gerenciador de Jogos* (seção 4.1)
lista, depois dos jogos, as pastas que a varredura recusou, marcadas como *Não adicionado*, e diz por que cada uma
foi recusada; Square apaga uma pasta dessas. Depois de arrumar uma pasta, *Reescanear jogos* no menu do sistema roda
a varredura de novo.

**Os jogos estão sem capa.** Ou os bancos de capas não foram instalados (rode o instalador de novo com eles
marcados), ou, no caso de jogos do RetroArch em um console, o UpdateRoms ainda não foi rodado no PC (capítulo 5).

**Um controle não faz nada, ou está com os botões trocados.** O AutoBleem não conhece o layout desse controle. No
console, mapeie o controle com o assistente de controles do PSC-Bios (seção 6.1). Em um Pi ou em um PC, a página
Informações de hardware (seção 4.2) mostra o que o sistema enxerga do controle, o que ajuda a saber se ele está
sendo detectado.

**A tela fica preta depois de um jogo no console.** A imagem do launcher não voltou quando o jogo terminou. O
AutoBleem reconstrói a janela dele sozinho, até três vezes. Se mesmo assim a tela continuar preta, segure o botão
Power e ligue o console de novo.

**Em um Raspberry Pi**, você pode ir para trás do launcher quando precisar: `Alt+F2` abre um login no segundo
console, e o SSH vem ativado desde a primeira inicialização. `sudo journalctl -u autobleem` mostra o que o serviço
do launcher fez, e `sudo systemctl restart autobleem` reinicia o serviço. Se a primeira inicialização não conseguiu
terminar por falta de rede, ela tenta de novo na próxima inicialização.

**No Windows**, `Esc` fecha o launcher. A sua pasta de dados é a que você escolheu na instalação
(`Documents\AutoBleem`, se você não mudou), e os logs ficam na pasta `System\Logs` dela.

**O console reinicia sem parar depois de uma atualização online (pendrive formatado em ext4).** Algumas pessoas
formatam o pendrive em ext4, o sistema de arquivos do Linux, em vez de FAT32 ou exFAT. Até a próxima versão do
AutoBleem, uma atualização online em um pendrive desses descompacta todos os arquivos sem a permissão que deixa
cada um rodar como programa. Aí o AutoBleem não consegue iniciar, e o console reinicia sem parar. Pendrives em
FAT32 e exFAT não são afetados. Há dois jeitos de resolver.

**Solução A**: precisa de um PC com Linux. Conecte o pendrive e torne os programas do AutoBleem executáveis de
novo. Troque `/media/USER/STICK` pelo caminho onde o seu pendrive está montado; a última linha só é necessária se o
RetroArch estiver instalado:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**Solução B**: instale de novo a versão mais recente do AutoBleem no pendrive, como na seção 2.1. O instalador
precisa de um PC que consiga ler o pendrive. Se ele não conseguir ler o seu, o pendrive precisa ser formatado
primeiro, o que apaga tudo o que há nele; copie seus jogos para outro lugar antes.

> Para evitar isso, use **FAT32** (um console original só lê FAT32; o exFAT precisa do kernel do AutoBleem,
> capítulo 6). A próxima versão mantém as permissões, e o AutoBleem as conserta a cada inicialização.

O AutoBleem é software livre (GNU GPL v3 ou posterior) e vem sem nenhuma garantia. Para suporte e novidades, entre
no servidor do Discord que tem o link na tela Sobre, ou visite https://autobleem.retromenele.pl/.
