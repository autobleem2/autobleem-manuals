# AutoBleem 2 Kullanım Kılavuzu

AutoBleem 2, **PlayStation Classic** için yazılmış bir oyun başlatıcısıdır. 2. sürümden bu yana bir
**Raspberry Pi**'de, **USB bellekten açılan bir PC**'de ve **Windows**'ta da çalışıyor. PS1 oyunlarınızı kutu
kapakları ve bilgileriyle birlikte bir raf hâlinde dizer, onları beraberinde gelen PCSX emülatöründe açar; yanına
RetroArch'ı da kurarsanız başka sistemlerin oyunlarını da oynatır. Bu kılavuzda AutoBleem'i her platforma nasıl
kuracağınızı, günlük kullanımını ve onunla gelen araçları bulacaksınız.

> Bütün platformların indirmeleri **https://autobleem.retromenele.pl/** adresinde. Sayfa platformlara göre
> bölünmüştür: her platformun *Install* panelinde indirmeniz gereken dosya durur; altındaki *Build inputs* ise
> kurulum programlarının kendi kendine indirdiği parçalardır.

## 1. Neler geliyor

AutoBleem, PlayStation Classic'inizi - ya da bir Raspberry Pi'yi, eski bir PC'yi veya Windows bilgisayarınızı -
kendi oyunlarınız için düzgün bir menüsü olan küçük bir oyun konsoluna çevirir. Paketin içinden şunlar çıkar:

- **Başlatıcı.** Cihazı açınca karşınıza çıkan ekran budur: kapakların arasında gezindiğiniz bir raf ve yanında
  seçili oyunun bilgileri. Oyunları buradan başlatır, setlere (PlayStation, RetroArch, Uygulamalar) ayırır,
  ayarları değiştirir, hafıza kartlarınızla ve durum kayıtlarınızla ilgilenir, Mağaza'dan uygulama ve oyun
  indirirsiniz. Her platformda aynı görünür, aynı şekilde çalışır.
- **İki PS1 emülatörü.** `pcsx-abnxt` güncel olanıdır ve varsayılan olarak o kullanılır; `pcsx-ab` ise
  AutoBleem'in baştan beri getirdiği klasik emülatördür. Hangisini kullanacağınızı seçeneklerden belirlersiniz.
  İkisi de aynı ayarları ve aynı hafıza kartlarını kullandığı için istediğiniz an, hiçbir şey kaybetmeden
  değiştirebilirsiniz.
- **RetroArch** - başka sistemlerin oyunlarını da oynamak isterseniz: NES, SNES, Mega Drive, Game Boy, atari
  salonu makineleri ve daha pek çoğu. Hiçbir platformda zorunlu değildir. ROM'larınızı kopyalarsınız, AutoBleem
  onları listelere ayırır ve her oyunu doğru çekirdekle açar. PlayStation oyunları da RetroArch'ta çalışabilir;
  onun *PlayStation 1* çekirdeği, çekirdek listesinin en başında durur (bölüm 3.9). Doom gibi oyunlar ise kendi
  oyun dosyalarınızla, bir `Packages` klasöründen çalışır (bölüm 3.10).
- **Konsol araçları.** *PSC-Bios* - menülerde adı *Ağ ve Kumandalar* olarak geçer - Wi-Fi'yi, saati, Bluetooth
  kumandaları ve tuş eşlemesini ayarlar; bunu konsolda olduğu gibi Raspberry Pi'de ve PC belleğinde de yapar.
  *ABFlashKit* ise PlayStation Classic'e AutoBleem kernel'ini kurar (bölüm 6).
- **UpdateRoms** (Windows için). PlayStation Classic'in kendi ağ bağlantısı yoktur. Bu PC programı, konsolun USB
  belleği bilgisayarınıza takılıyken RetroArch listelerini yeniler ve kutu kapaklarını indirir.

![Başlatıcı: kapak rafı, seçili oyunun bilgileri, düğme ipuçları](../images/en/launcher.jpg)

<!-- pagebreak -->

## 2. Kurulum

### 2.1 PlayStation Classic

AutoBleem tamamen bir USB bellekten çalışır, konsolun içinde hiçbir şeye dokunmaz: belleği çıkardığınızda konsol
eskisi gibi çalışmaya devam eder. Gereken tek şey bir Windows PC, bir USB bellek (USB 2.0, en az 8 GB) ve
konsolun kendisi.

Belleğin boş olması gerekmez ve siz istemedikçe **biçimlendirilmez**: AutoBleem, bellekte ne varsa onun yanına
kurulur. AutoBleem 1.0 ile kullandığınız bir bellek de olduğu yerde yükseltilir (aşağıya bakın). Hiç
dokunulmamış bir konsolda bellek **FAT32** olmalıdır, çünkü konsolun kendi kernel'i exFAT okuyamaz. AutoBleem
kernel'ini kurduktan sonra (ABFlashKit, bölüm 6) konsol exFAT bir bellekten de açılır; böylece FAT32'nin dosya
başına 4 GB sınırından da kurtulursunuz.

1. Sitenin PlayStation Classic panelinden **AutoBleemInstaller-<sürüm>.zip** dosyasını indirip istediğiniz bir
   yere açın. İçinden `AutoBleemInstaller.exe` ve onun README dosyası çıkar. AutoBleem'in kendisi kurulum
   sırasında indirildiği için PC'nin internete bağlı olması gerekir.
2. Belleği takın ve `AutoBleemInstaller.exe`'yi çalıştırın. Önce **kanalı** seçin: *Release* denenmiş
   sürümdür ve çoğu kişi için doğru seçim budur; *Testing* henüz denenmekte olan bir sonraki sürümdür;
   *Nightly* ise en yeni geliştirme derlemesidir ve çalışmayabilir. Ardından belleğin sürücüsünü seçin. Hemen
   alttaki satır, hangi AutoBleem sürümünü kurmak üzere olduğunuzu ve bellekte şu an ne olduğunu söyler: ya
   *a fresh install* (yeni kurulum; bellekteki diğer dosyalara dokunulmaz) ya da *AutoBleem <version> is on
   this stick: it will be updated* (bellekte zaten AutoBleem var ve güncellenecek; oyunlarınız, kayıtlarınız,
   hafıza kartlarınız ve ayarlarınız yerinde kalır).
   **Biçimlendirmeniz gerekmez.** Sürücünün yanındaki **Format** düğmesi yalnızca hiç dosya sistemi olmayan
   yepyeni bir bellek, konsolun okuyamadığı bir bellek (örneğin NTFS) ya da tamamen silmek istediğiniz bir
   bellek içindir. Önce onay ister, sonra bellekteki her şeyi siler. Konsolda AutoBleem kernel'i yoksa orada
   FAT32'yi seçin.
   Son olarak neyin kurulacağını işaretleyin:
   - **Cover databases** - bütün PS1 kütüphanesinin kapakları ve açıklamaları; oyunlarınızın kapakları böylece
     kendiliğinden gelir (varsayılan olarak işaretlidir; yaklaşık 300 MB).
   - **RetroArch** - çekirdekleri, ek uygulamaları (Doom, Quake, Amiga, ...) ve libretro'nun dosyalarıyla
     birlikte RetroArch; başka sistemlerin oyunları için. Varsayılan olarak kapalıdır; kurulum programını
     yeniden çalıştırıp sonradan ekleyebilirsiniz.
   - **BIOS files** - bazı RetroArch çekirdeklerinin açılmak için ihtiyaç duyduğu BIOS dosyaları (yalnızca
     RetroArch ile birlikte).
   - **Sample games** - birkaç ücretsiz homebrew oyun; ilk açılışta raf boş kalmasın diye.
3. **Install**'a basıp bekleyin. İlerleme çubukları ve günlük, her adımı gösterir. İş bittiğinde belleğin adı
   `SONY` olur ve üzerine bir `UpdateRoms` kopyası konur (bkz. bölüm 5).
4. Belleği güvenli şekilde çıkarın ve konsolun **öndeki ikinci USB girişine** (sağdaki, 2. oyuncununki) takın;
   birinci giriş kumandanız için boş kalır. Sonra konsolu açın: alışık olduğunuz menünün yerine AutoBleem
   açılır. İkinci bir kumanda için öndeki girişe bir USB çoklayıcı takın ya da Bluetooth kumanda kullanın.

**Açma ve kapatma.** Bellek takılıyken konsol açılır, AutoBleem'i fark ederken ışığı birkaç saniye yanıp söner
ve ekranda daha hiçbir şey görünmeden bekleme moduna geçer. Bu normaldir: AutoBleem konsolun kendi güncelleme
mekanizması üzerinden başlar ve o mekanizma böyle çalışır. **Power**'a bir kez basın, başlatıcı gelir.

Sistem menüsünde *Kapat*'ı seçtiğinizde ya da konsolun Power düğmesine bastığınızda konsol **AutoBleem'in bekleme
moduna** geçer: AutoBleem önce belleği güvenli şekilde ayırır, sonra ışık **turuncu** yanar. Turuncu ışık her şeyin
olması gerektiği gibi gittiğini gösterir. Power'a bir daha bastığınızda başlatıcı birkaç saniye içinde geri gelir.
**Işık turuncuyken belleği çıkarıp** PC'nize takabilirsiniz; düzgün ayrıldığı için Windows onu taramayı teklif
etmez. Power'a basmadan önce belleği yerine takmayı unutmayın. Konsolun elektrik kablosunu çekerseniz, bir
sonraki açılışta ilk açılıştaki bekleme adımından yeniden geçer. **Kırmızı** ışık, konsolun gerçekten kapalı
olduğu anlamına gelir.

**Arkadaki giriş.** Konsolun arkasındaki micro-USB girişi onun güç girişidir. AutoBleem kernel'i varken buraya bir
USB aygıtı da takılabilir, ama belleğin yeri öndeki girişlerdir.

**Bellek takılı değilse.** Konsol belleksiz açılırsa ya da AutoBleem çalışırken belleği çekerseniz, ekrana
belleği takmanızı isteyen bir resim gelir; herhangi bir USB girişi olur. AutoBleem 5 dakika bekler, sonra konsolu
uyku moduna alır. Hemen uyusun istiyorsanız Power'a basın.

![Belleği takmanızı isteyen resim](../images/en/insert-stick.jpg)

**Bellek ne zaman denetlenir.** Bellek düzgün ayrılmadıysa - AutoBleem çalışırken çektiyseniz ya da elektrik
kesildiyse - AutoBleem onu yeniden kullanmadan önce hatalara karşı denetler: açılışta, uykudan uyanırken ya da
belleği geri taktığınızda. Denetimin ne kadar ilerlediğini bir ilerleme çubuğu gösterir. Büyük bir bellekte bu
biraz sürebilir; bitmesini bekleyin ve bu arada konsolu kapatmayın.

![Belleğin denetlenmesi](../images/en/stick-check.jpg)

**Güncelleme.** Bir belleği güncellemek için kurulum programını onun üzerinde yeniden çalıştırın; düğmenin
üzerinde artık *Update* yazar. Program, seçtiğiniz kanalın en yeni sürümünü kurar. Oyunlarınız, kayıtlarınız,
ayarlarınız ve RetroArch içeriğiniz yerinde kalır, yalnızca AutoBleem'in kendi dosyaları değişir. AutoBleem
kernel'i ve Wi-Fi'si olan bir konsol kendini kendisi de güncelleyebilir (bölüm 3.12).

**AutoBleem 1.0'dan (ya da AutoBleem-NG'den) geçiş.** Aynı kurulum programını aynı bellek üzerinde, biçimlendirmeden
kullanırsınız:

1. Ne olur ne olmaz, önce belleğin tamamını yedek olarak PC'nize kopyalayın.
2. Belleği takın, `AutoBleemInstaller.exe`'yi çalıştırın, kanalı ve sürücüyü seçin. Format'a **basmayın**.
3. **Install**'a basın. Kurulum programı eski düzeni yenisine taşır: RetroArch, ROM'lar ve temalar AutoBleem 2'nin
   beklediği yerlere geçer, eski ROM klasörleri (`nes`, `snes`, ...) RetroArch'ın sistem adlarını alır.
   Oyunlarınız, durum kayıtlarınız, hafıza kartlarınız, ROM'larınız ve RetroArch kayıtlarınız olduğu gibi kalır;
   `config.ini` de korunur, yalnızca içindeki PS1 emülatörü pcsx-abnxt yapılır.
4. Belleği konsola geri takın. İlk tarama oyun listesini ve oynatma listelerini yeniden kurar. RetroArch
   oyunlarınızın kapakları için PC'de UpdateRoms'u çalıştırın (bölüm 5).

> Kutudan çıktığı hâliyle konsolun ne saati ne de ağı vardır. Tarihler ancak AutoBleem kernel'i kurulduktan
> sonra görünür (bölüm 6); RetroArch oyunlarının kapakları da PC'deki UpdateRoms'tan gelir (bölüm 5).

PS1 oyunlarınız belleğin `Games` klasörüne, her oyun kendi klasörüne girer; düzeni bölüm 3.10 anlatıyor.

### 2.2 Raspberry Pi

AutoBleem ile bir Raspberry Pi küçük bir konsola dönüşür: araya hiç masaüstü girmeden doğrudan başlatıcıyla açılır.
Sitede iki hazır kart görüntüsü var, biri 32 bit, biri 64 bit; ayrıca elinizde zaten kurulu olan bir Raspberry Pi OS
Lite için bir paket.

| Model | 32 bit görüntü | 64 bit görüntü | Notlar |
|---|---|---|---|
| Raspberry Pi 5 | evet | evet | |
| Raspberry Pi 4 Model B, Pi 400 | evet | evet | |
| Raspberry Pi 3 Model B / B+ / A+ | evet | evet | başlatıcı ve PS1 için yeterli |
| Raspberry Pi Zero 2 W | evet | evet | 512 MB RAM: PS1 çalışır, ağır RetroArch çekirdekleri çalışmaz |
| Raspberry Pi 2 Model B | evet | yalnızca v1.2 | 3D olan her şeyde yavaş |
| Raspberry Pi 1, Zero, Zero W | hayır | hayır | ARMv6 - iki görüntü de çalışmaz |

**PS1 oyunları için 32 bit görüntüyü seçin.** Klasik `pcsx-ab`'nin hızlı ARM yeniden derleyicisi yalnızca 32 bit
için var, bu yüzden PS1 oyunları 64 bit derlemede daha yavaş çalışır. 64 bit görüntüde daha fazla RetroArch
çekirdeği bulunur; sizin için diğer sistemler PS1'den daha önemliyse onu alın.

**Raspberry Pi Imager ile:**

1. Raspberry Pi Imager'ı kurun (raspberrypi.com/software). *Choose OS* altında *Use custom*'ı seçip indirdiğiniz
   `autobleem-<sürüm>-rpi-armhf.img.xz` (32 bit) ya da `-arm64.img.xz` (64 bit) dosyasını gösterin. Bunun yerine
   uygulamanın ayarlarına bir depo adresi ekleyip AutoBleem'i listeden de seçebilirsiniz. Her kanalın kendi adresi
   var: son sürüm için `https://autobleem.retromenele.pl/rpi-imager/os_list.json`, denenmekte olan derleme için
   `.../os_list-testing.json`, en yeni geliştirme derlemesi için `.../os_list-nightly.json`. İndirme sayfasının
   Raspberry Pi sekmesi, var olanları her birinin yanında bir *Copy* düğmesiyle listeler.
2. Imager'ın özelleştirme ekranında (dişli simgesi ya da *Next*'ten sonra gelen soru) **kullanıcı adını ve
   parolayı, Wi-Fi ağını ve ülkeyi** girin ve **SSH'yi açın**. AutoBleem'in ilk açılışta bir ağa ihtiyacı var.
3. Kartı yazdırın, Pi'ye takın, bir ekran ve bir klavye ya da kumanda bağlayıp Pi'yi çalıştırın.

**İlk açılış** 5 ile 25 dakika arası sürer; o sırada ne olduğunu ekran size söyler. Ağ yoksa bir ağ ister: listeden
Wi-Fi'nizi seçip parolasını yazarsınız. Sonra RetroArch'ı kurup kurmayacağını sorar; bir dakika içinde cevap
vermezseniz kurar. Ardından sistem bölümünü büyütür, kartın geri kalanını oyunlarınız için `AUTOBLEEM` bölümüne
çevirir, RetroArch'ı çekirdekleriyle, BIOS paketlerini ve örnek oyunları kurar, sonra yeniden başlayıp başlatıcıyı
açar.

İlk açılışta soru cevaplamakla uğraşmak istemiyorsanız cevapları önceden kartın açılış bölümündeki
**`autobleem.txt`** dosyasına yazın; bu dosyayı herhangi bir PC'de açıp düzenleyebilirsiniz:

| Anahtar | Varsayılan | Anlamı |
|---|---|---|
| `root_gib` | 8 | Sistem bölümünün GiB cinsinden boyutu; kalan alan oyun bölümü olur. |
| `hdmi_mode` | 1920x1080@60 | Açılışın tamamında kullanılacak ekran modu (eski bir televizyon için `1280x720@60`). |
| `retroarch` | (sorulur) | `yes` / `no` - RetroArch ve diğer sistemler mi, yoksa yalnızca PS1 mi. |
| `thumbnails` | none | `boxarts` verirseniz kapakların tamamı karta indirilir, kapaklar internetsiz de görünür (~9000 dosya). |
| `bios`, `downloads`, `samples` | yes | `no` yazarsanız sırasıyla BIOS paketleri, bütün indirmeler ya da örnek oyunlar atlanır. |

**Zaten kurulu bir Raspberry Pi OS Lite üzerinde** (Bookworm ya da Trixie): `autobleem-rpi.tar.gz` dosyasını (ya da
arm64 olanını) Pi'ye kopyalayın, açın ve `sudo bash install.sh` komutunu çalıştırın. Aynı soruları sorar, bir
sonraki açılışta sistem bölümünü küçülterek veri bölümüne yer açar (`--shrink-root <GiB>`) ve başlatıcıyı ilk
konsola yerleştirir.

Kurulumdan sonra oyunlarınızı kartın **`AUTOBLEEM` bölümüne** (exFAT) koyarsınız: kartı çıkarıp herhangi bir PC'de
açın ya da ağ üzerinden kopyalayın (SSH açık). PS1 oyunları `Games/` klasörüne, başka sistemlerin ROM'ları
`RetroArch/roms/<sistem>/` klasörüne, PS1 BIOS'u `System/Bios/` klasörüne (bölüm 3.11), temalar da `Themes/`
klasörüne gider.

### 2.3 PC için USB bellek

Aynı şey, USB'den açılabilen her PC için: bellek PC'yi doğrudan AutoBleem ile açar ve bilgisayarın kendi
diskine dokunmaz. 32 bitlik bir sistem olduğu için eski makinelerde de çalışır.

1. Görüntüyü en az 8 GB'lık bir belleğe yazın. **Windows'ta** bunun için **AutoBleemFlasher**'ı kullanın (sitenin
   PC panelinde; zip'i açıp `AutoBleemFlasher.exe`'yi çalıştırın - bütün bir diske yazdığı için yönetici izni
   ister). Kanalı ve belleği seçin, *Write*'a basın ve iki kez onaylayın: program görüntüyü indirir, denetler,
   yazar ve yazdığını geri okuyarak doğrular. Listede yalnızca USB bellekler ve SD kartlar çıkar, Windows'un
   çalıştığı disk asla çıkmaz. **Seçtiğiniz bellekteki her şey silinir.** Linux'ta ya da macOS'ta PC panelinden
   `autobleem-<sürüm>-pcusb-i386.img.xz` dosyasını indirip
   `xzcat autobleem-*.img.xz | sudo dd of=/dev/sdX bs=4M status=progress` ile (ya da balenaEtcher ile) yazın.
2. PC'yi bellekten açın (bilgisayarınızın açılış menüsü tuşuyla - F12, F8, Esc...). Hem BIOS hem UEFI ile açılır;
   **Secure Boot kapalı olmalıdır**.
3. İlk açılış Pi'dekinin aynısıdır: kablo takılı değilse bir ağ ister, RetroArch'ı sorar, her şeyi kurar -
   kablolu ağla yaklaşık sekiz dakika - ve yeniden başlayıp başlatıcıyı açar.

Bundan sonra bellekte oyunlarınız için bir `AUTOBLEEM` bölümü olur. Belleği çalışan bir Windows 10 PC'ye (1903 ya
da daha yeni sürüm) taktığınızda ikinci bir sürücü olarak görünür ve oyunları oraya kopyalayabilirsiniz.
`autobleem.txt` ilk bölümde durur ve Pi'dekiyle aynı anahtarları alır (`hdmi_mode` hariç - PC her zaman ekranın
kendi modunu kullanır).

### 2.4 Windows

AutoBleem'i Windows bilgisayarınızda kullanmak isterseniz sıradan bir program olarak da çalışır: tam ekran açılır,
emülatörler ve RetroArch ayrı programlar olarak başlar.

1. **AutoBleemSetup-<sürüm>.exe** dosyasını indirip çalıştırın. Yönetici izni istemeden yalnızca sizin kullanıcınız
   için kurulur: program `%LOCALAPPDATA%\Programs\AutoBleem` altına, veriler (oyunlar, ayarlar, temalar,
   RetroArch) sizin seçtiğiniz bir klasöre gider - varsayılan olarak `Documents\AutoBleem`.
2. Kurulacak parçaları işaretleyin - kapak veritabanları, RetroArch (resmi Windows derlemesi ve çekirdekleri), BIOS
   dosyaları, örnek oyunlar - ve kurulum yardımcısının onları indirmesini bekleyin.
3. AutoBleem'i Başlat menüsünden ya da masaüstünden açın. PC'de klavye kumanda yerine geçer (bölüm 3.2).

Güncellemek için daha yeni bir kurulum dosyasını eskisinin üzerine çalıştırın: program yenilenir, veri klasörünüz
olduğu gibi kalır. Başlatıcı ayrıca günde bir kez siteye bakar ve yeni bir sürüm varsa güncellemeyi önerir
(bölüm 3.12).

<!-- pagebreak -->

## 3. AutoBleem'in kullanımı

### 3.1 Başlatıcı

Ne oynayacağınızı başlatıcıda seçersiniz. Oyunlarınızı, gerçek bir raftaki kutular gibi bir kapak rafında dizer;
siz de aradığınızı bulana kadar raf boyunca kaydırırsınız. AutoBleem'in geri kalan her şeyi - ayarlar, hafıza
kartları, Mağaza - buradan açılır ve bir oyundan çıktığınızda yine buraya dönersiniz.

Seçili oyun rafın ortasında durur, altında hafif bir yansımayla. Yanında küçük bir tablo hâlinde bilgileri
görürsünüz: yayıncı, yıl, seri numarası, bölge, kaç kişiyle oynandığı ve en son ne zaman oynadığınız. AutoBleem bu
bilgilerden birini bilmiyorsa o satırı boş göstermek yerine hiç göstermez. Bilgilerin yanında bir oynat düğmesi
vardır. Kapak resmi olmayan bir oyun, boş bir kutunun siyah tepsisinde duran bir disk olarak görünür; böylece
rafta onun da bir yeri olur.

Başlatıcının görünüşü temasından gelir. Varsayılan tema **ab2.0.0**'dır. Yeni bir kurulum bu temaya geçer, onu
getiren bir güncelleme de öyle - ama yalnızca bir kez: sonradan başka bir tema seçerseniz (bölüm 3.6) o tema kalır.

Ekranın altındaki **ipucu çubuğu** düğmelerin o an ne işe yaradığını söyler. Dörder yerli iki satırdan oluşur. İlk
satır seçili oyunla ilgilidir: oyunu açmak, RetroArch'ta açmak, altındaki simge sırasını açmak ya da Hızlı menüyü
açmak. İkinci satır hiç değişmez: Select seti seçer, Start rastgele bir oyun bulur, Triangle düğme kılavuzunu
gösterir, L2 + R2 sistem menüsünü açar. Düğmesinin o an yapacak bir işi yoksa ipucu soluk görünür.

**Yeni oyunları kendisi bulur.** Başlatıcı her açıldığında oyun klasörünüzü arka planda tarar; cihaz kapalıyken
kopyaladığınız bir oyun, siz hiçbir şey yapmadan rafa gelir. Tarama sürerken sağ üstteki bir baloncuk ne kadar
ilerlediğini gösterir, bulunan yeni oyunlar da hemen rafta belirir. Bu arada gezinmeye devam edebilirsiniz.

**Yeni kurulumda** henüz hiç oyun yoktur. Boş bir raf yerine bir karşılama kartı görürsünüz: *Merhaba, AutoBleem'e hoş
geldin!*. Kart, oyunlarınızı `Games` klasörüne atıp *Oyunları yeniden tara*'ya basmanızı söyler ve bu klasörün
platformunuzda nerede olduğunu da belirtir: belleğinizde (PlayStation Classic, PC belleği), SD kartınızda (Raspberry
Pi) ya da AutoBleem klasörünüzde (Windows). Tarama ilk oyunu bulduğu anda kart kaybolur.

**Bildirimler** sağ üstte çıkan baloncuklardır. Sizi rahatsız etmeden olan biteni haber verirler: taramanın gidişatı,
az önce geçtiğiniz setin adı (*Gösteriliyor: ...*), pili azalan bir kumanda, bir çökmeden sonra bir not, çalışan bir
tarama işlemcisi ya da Mağaza'dan bir indirme. İndirme baloncuğu hızı ve kalan süreyi gösterir, örneğin
`1.4 MB/s · 0:42`. Bilgi baloncuklarının ekranda ne kadar kalacağını siz belirlersiniz: Seçenekler → *Bildirim
süresi:*.

**Kumanda pilleri.** Konsolda, Raspberry Pi'de ve PC belleğinde (Windows'ta değil), pil durumunu bildiren her kablosuz
kumanda sol üst köşeden aşağı doğru dizilen kendi küçük levhasında, yüzdesiyle birlikte küçük bir simge olarak
görünür. 1. ya da 2. oyuncu olarak oynayan kumandanın üzerinde P1 ya da P2 etiketi bulunur; bu etiket
*Oyuncu 1 / oyuncu 2'yi değiştir (PS1 emülatörleri):* seçeneğine göre belirlenir (bölüm 3.6). Bir oyuncuya
eşlenmemiş kumandada ya da üçüncü bir kumandada etiket olmaz. Bir kumandanın pili azaldığında, adını ve yüzdesini
söyleyen bir bildirim bir kez çıkar.

**Kanal etiketi.** Kesin bir sürüm olmayan bir derleme kullanıyorsanız, sol üst köşede kumanda pili levhasının altında
küçük bir etiket bunu size hatırlatır. Bu etiket kanalın adını ve yanında kısa sürüm numarasını taşır: ön sürümler
için `ALPHA`, `BETA` ya da `RC`, diğer ön sürümler için `TESTING`, gece derlemesi için `NIGHTLY`, elle yapılmış bir
derleme için `DEV` (`DEV`'de sürüm yerine derlemenin yapıldığı commit yazar). Kesin sürümlerde etiket görünmez.

![Set seçici: üç sekme ve açık sekmenin grupları, oyun sayılarıyla](../images/en/set-picker.jpg)

### 3.2 Kontroller

AutoBleem yalnızca kumandayla kullanılmak üzere yapılmıştır ve düğmeler her ekranda aynı anlama gelir: Cross onaylar,
Circle geri götürür, Triangle yardım eder. Bir düğmenin ne yaptığını unutursanız ekranın altındaki ipucu çubuğu
söyler; raftayken Triangle'a basarsanız da her ekranın bütün düğmelerini gösteren düğme kılavuzu açılır (bölüm 4.3).
Rafta düğmeler şöyle çalışır:

| Düğme | Raftayken |
|---|---|
| Left / Right | Önceki ya da sonraki oyuna geçer; basılı tutarsanız kaydırmaya devam eder. |
| L1 / R1 | Oyun adlarının bir önceki ya da bir sonraki baş harfine atlar; uzun bir rafta hızlıca ilerlemenizi sağlar. Raf boşsa ve bir USB sürücü bağlıysa R1 *Disk*'i açar (bölüm 3.9a). |
| Cross | Seçili oyunu başlatır: PS1 oyununu PS1 emülatöründe, RetroArch oyununu kendi çekirdeğinde, bir Uygulamayı ise önce tanıtım metnini gösterdikten sonra. |
| Square | Seçili PS1 oyununu bunun yerine RetroArch'ta başlatır. USB sürücüdeki bir disk seçiliyse diski kopyalar (*Diski kopyala*, bölüm 3.9a). |
| Circle | Sürücüde disk varsa sizi disk görünümüne geri götürür (bölüm 3.9a). |
| Triangle | Düğme kılavuzunu açar. |
| Start | Açık setten rastgele bir oyun seçer; karar veremediğiniz anlar için. |
| Select | Rafta hangi oyunların görüneceğini seçtiğiniz set seçiciyi açar (bölüm 3.3). |
| Up | Hızlı menüyü açar (bölüm 3.4). |
| Down | Oyunun altındaki simge sırasını açar (*AYARLAR*, *Oyun*, *HAFIZA KARTI*, *DEVAM ET*); Up ile yeniden kapanır. |
| L2 + R2 | Sistem menüsünü açar (bölüm 3.5). |

**Klavyeyle.** Kumandası olmayan bir PC'de ya da konsola, Pi'ye veya PC belleğine takılmış bir USB klavyeyle tuşlar
düğmelerin yerini tutar. Ok tuşları yön tuşlarıdır, Enter Cross'tur, Esc ya da Backspace Circle'dır, Tab Triangle,
Space de Square'dir. F1 ile F2 Select ve Start, Page Up ile Page Down L1 ve R1, Home ile End L2 ve R2 olur; F10
sistem menüsünü açar.

Windows'ta birkaç tuş farklı çalışır. Orada Esc AutoBleem'i kapatır (bölüm 7); bu yüzden Circle yalnızca
Backspace'tir, Space Start, S de Square olur. Ayrıca harf tuşları kumandanın tamamının yerini tutabilir, böylece
ok tuşlarına uzanmanız gerekmez: X, O, S ve T Cross, Circle, Square ve Triangle; I, J, K ve L yön tuşları
(yukarı, sol, aşağı, sağ); B Select; Q ve E L1 ve R1; 1 ve 2 de L2 ve R2'dir.

**Bütün liste ve menülerde** aynı hareketler geçerlidir: Up ve Down imleci oynatır, L2 ve R2 sayfa çevirir, L1 ve R1
ilk ya da son satıra atlar, Cross seçer, Circle geri götürür. Hiçbir yerde bir Kaydet düğmesi aramanıza gerek yok:
ayar içeren bir ekran, siz Circle ile çıkarken ayarları kendisi kaydeder.

**Bir oyundan ya da Uygulamadan çıkmak.** Start + Select'i ya da Home'u 2 saniye basılı tutun, AutoBleem'e
dönersiniz. Bu her kumandada çalışır - konsolun kendi kumandasında, USB kumandada ya da Bluetooth kumandada. Aynı
düğmelere kısa basarsanız bunun yerine emülatörün menüsü açılır. Uygulamaların böyle bir menüsü olmadığından orada
yalnızca uzun basış bir şey yapar.

![Seçili oyunun altındaki simge sırası](../images/en/launcher-icons.jpg)

### 3.3 Setler

Büyük bir kütüphanede parça parça gezinmek daha kolaydır. Setler rafı tek bir oyun türüne indirmenizi sağlar -
yalnızca favorileriniz, yalnızca Super Nintendo oyunları, yalnızca bir klasördeki oyunlar - böylece aradığınızı
bulmak için yüzlerce kapağın önünden geçmeniz gerekmez.

**Select**'e basınca set seçici açılır. Üç sekmesi vardır: PlayStation, RetroArch ve Apps. L1 ve R1 sekmeler arasında
geçer, Up ve Down sekmenin grupları arasında dolaşır (L2 ve R2 sayfa sayfa), Cross da seçtiğiniz grubu rafa getirir.
Circle (*Geri*) hiçbir şeyi değiştirmeden seçiciyi kapatır. Bu tuşları alt bilgi satırı da gösterir. Her satır
içinde kaç öğe olduğunu yazar. İçi boş bir grup boş bir rafla açılır; orada simge sırasında yalnızca *AYARLAR* olur.

**PlayStation sekmesi.** PlayStation Classic'te en başta *Tüm oyunlar* ve *Dahili oyunlar* (konsolun içinde gelen
yirmi oyun) durur. Ardından `Games/` klasöründeki her şeyi içeren *USB oyunları* gelir; onun altında açtığınız her
klasör için de ayrı bir grup vardır, yani alt klasördeki bir oyun o klasörün grubuna girer. Sonra *Favori oyunlar*,
*Oyun geçmişi* ve - en az bir oyunu ışıklı silah oyunu olarak işaretlediyseniz - *Işıklı silah oyunları* gelir.
Raspberry Pi'de, PC belleğinde ve Windows'ta dahili oyun olmadığından liste *USB oyunları* ile başlar; bu da sizin
bütün kütüphanenizdir.

**RetroArch sekmesi** yalnızca RetroArch kurulu olan yerlerde görünür. Oyununuz olan her sistem için bir grup, bir de
RetroArch'ın kendi Favorites ve History listelerini içerir.

**Apps sekmesi** uygulamaları türlerine göre ayırır: *Tüm uygulamalar*, ardından *Oyunlar*, *Emülatörler*, *Araçlar*,
*Medya* ve *Diğer*. Bir uygulamanın hangi gruba gireceği, onun `app.ini` dosyasında yazar. Bu sekmede ayrıca
**PE uygulamaları** da listelenir; bunlar PE çalıştırıcısının açtığı Windows programlarıdır. Konsolun açamayacağı
bir tanesinin yanında *bu konsolda çalışamaz* yazar. Başlatıcı gösteriyorsa listede bir de *Paketler* satırı bulunur
(bölüm 3.10).

### 3.4 Hızlı menü

Hızlı menü, oyunlarınız arasında gezinirken en sık ihtiyaç duyduğunuz şeylerin kısa bir listesidir; onlar için
koca sistem menüsünü karıştırmanız gerekmez. Rafta **Up** ile ya da simge sırasındaki (*AYARLAR*, *Oyun*,
*HAFIZA KARTI* ve *DEVAM ET*'in bulunduğu sıra) **dişli simgesiyle** açılır.

Up ve Down öğeler arasında dolaşır (sonuncudan sonra imleç başa döner), Cross birini seçer, Circle menüyü kapatır.
Menünün altındaki satır seçili öğenin ne işe yaradığını anlatır. Öğeler şunlardır:

- *Oyunları yeniden tara* yeni, değişmiş ya da silinmiş oyunları hemen arar. Oyunları az önce kopyaladıysanız ve
  beklemek istemiyorsanız işinize yarar.
- *Mağaza* AutoBleem Mağazası'nı açar; orada oyunlara, uygulamalara ve eklentilere göz atıp onları kurarsınız
  (bölüm 3.13).
- *RetroArch çekirdekleri*, RetroArch kuruluysa her sistemi hangi çekirdeğin oynatacağını seçmenizi sağlar.
- *Ağ ve Kumandalar* Wi-Fi, Bluetooth eşleştirme ve kumanda eşleme ekranlarını açar (bölüm 6). Yalnızca bu ekranları
  getiren bir eklenti kuruluysa görünür; konsolda, Raspberry Pi'de ve PC belleğinde bunu PSC-Bios yapar. Eklenti
  kurulu ama kapalıysa öğe soluk görünür ve açıklaması onu Eklentiler'den açmanızı söyler; bu durumda Cross,
  Eklentiler listesini doğrudan o eklentinin üzerinde açar.
- *Başlatıcıyı yeniden başlat* AutoBleem'i kapatıp yeniden açar (yalnızca konsolda, Raspberry Pi'de ve PC
  belleğinde).
- *Sistem menüsü...* geri kalan her şeyin bulunduğu tam sistem menüsünü açar - Seçenekler, Oyun Yöneticisi, Kapat ve
  daha fazlası (bölüm 3.5).

Mağaza, RetroArch çekirdekleri ve Başlatıcıyı yeniden başlat dışında buradaki her şey sistem menüsünde de bulunur.

![Hızlı menü](../images/en/quick-menu.jpg)

### 3.5 Sistem menüsü

Sistem menüsünde AutoBleem'in oyun oynatmak dışında yapabildiği her şey toplanmıştır: ayarlar, kütüphaneniz ve
hafıza kartlarınız için araçlar, makineyle ilgili bilgiler ve kapatma. **L2 + R2**'ye birlikte basın (hangisine önce
bastığınız fark etmez), menü rafın üzerinde açılır. Öğeleri *Kütüphane*, *Sistem* ve *Çıkış* başlıkları altında
toplanmıştır; en sık kullanılan iki öğe en üsttedir. Menünün altındaki satır seçili öğeyi anlatır, böylece bir şey
seçmeden önce etrafa göz atabilirsiniz.

| Bölüm | Öğe | Ne yapar |
|---|---|---|
| (en üst) | *Oyunları yeniden tara* | Yeni, değişmiş ya da silinmiş oyunları hemen arar. Tarama klasörü zaten kendiliğinden izler; buna yalnızca beklemek istemediğinizde ihtiyaç duyarsınız. |
| | *Eklentiler* | Bellekteki eklentileri, örneğin AutoBleem Mağazası'nı listeler; buradan onları çalıştırabilir ya da kapatabilirsiniz (bölüm 3.13). |
| *Kütüphane* | *Oyun Yöneticisi* | PS1 oyunlarını klasörleriyle birlikte liste hâlinde gösterir; buradan bir oyunu silebilir ya da kapakları temizleyebilirsiniz (bölüm 4.1). Tarama sürerken açılamaz. |
| | *Hafıza kartları* | Paylaşılan hafıza kartı setlerinizi yönetir (bölüm 3.8). |
| | *Tarama işlemcileri* | Her taramanın önce çalıştırdığı programların sırasını belirler, onları açıp kapatır (bölüm 3.14). Tarama sürerken açılamaz. |
| *Sistem* | *Seçenekler* | AutoBleem'in ayarlarını açar (bölüm 3.6). |
| | *Ağ ve Kumandalar* | Wi-Fi, Bluetooth kumanda eşleştirme, DualShock 3 kurulumu ve kumanda eşleme ekranlarını açar (bölüm 6). Yalnızca bunları getiren bir eklenti varsa görünür - aşağıya bakın. |
| | *Donanım bilgisi* | Makinenin bilgilerini gösterir - sistem, işlemci, depolama, ağ arayüzleri, saat dilimi, ekran ve eşlemeleriyle birlikte kumandalar; her platformda aynı sayfadır (bölüm 4.2). Circle sizi sistem menüsüne geri götürür. |
| | *Sanal oyun kumandası* | Uygulamalara verilen kumandaları ve arka plan yardımcısının (daemon) gördüğü kumandaları gösterir; bir kumanda bir Uygulamada çalışmadığında işe yarar (bölüm 4.5). Circle sizi sistem menüsüne geri götürür. |
| | *Yazılım güncellemesi* | Günlük denetimi beklemeden, sitede daha yeni bir AutoBleem ya da RetroArch olup olmadığına hemen bakar (bölüm 3.12). Başlatıcı zaten yeni bir sürümden haberdarsa satırda *Güncelleme mevcut* yazar. PlayStation Classic'te bunun için AutoBleem kernel'i ve bir Wi-Fi ağı gerekir. |
| | *Hakkında* | Emeği geçenleri ve lisansı gösterir. |
| *Çıkış* | *RetroArch* | Başlatıcıdan çıkıp RetroArch'ın kendi menüsüne, onun ayarlarına ve içerik listelerine geçer; RetroArch'ı kapattığınızda başlatıcıya dönersiniz. Yalnızca RetroArch kuruluysa görünür. |
| | *Kapat* | Onayınızı aldıktan sonra makineyi kapatır (aşağıya bakın). |

**Ağ ve Kumandalar** yalnızca kurulu bir eklenti `network` girişini sağlıyorsa görünür; eklenti bunu kendi
`extension.ini` dosyasında `Provides=network` satırıyla bildirir. Konsolda, Raspberry Pi'de ve PC belleğinde bunu
PSC-Bios yapar. Eklenti kurulu ama kapalıysa öğe menüde soluk olarak kalır ve açıklaması onu Eklentiler'den açmanızı
söyler; üzerine Cross'a basarsanız Eklentiler listesi tam o eklentinin üzerinde açılır.

**Kapat** makineye uygun olanı yapar. Konsolda onu AutoBleem'in bekleme moduna alır: bellek ayrılır, ışık turuncu
yanar ve Power başlatıcıyı birkaç saniyede geri getirir (bölüm 2.1). Raspberry Pi'de ya da PC'de makine kapanır.

![Sistem menüsü](../images/en/system-menu.jpg)

### 3.6 Seçenekler

Seçenekler, AutoBleem'i kendinize göre ayarladığınız yerdir: ekrandaki görüntü, başlatıcının görünüşü, dil, ses,
PS1 oyunlarınızın hangi emülatörde açılacağı. Sistem menüsünden (*Seçenekler*) ya da bir oyunun altındaki *AYARLAR*
simgesiyle açılır. Ekranı ve dili genellikle bir kez ayarlarsınız; belli bir televizyonda bir şey tuhaf göründüğünde
ya da canınız bir değişiklik istediğinde geri gelirsiniz.

Ayarlar her biri kendi başlığı altında gruplara ayrılmıştır. Up ve Down satırdan satıra geçer, Left ve Right de
bulunduğunuz satırın değerini değiştirir: bir kez basmak bir adım ilerletir, basılı tutmak devam ettirir. L1 ve R1
ilk ya da son satıra atlar, L2 ve R2 sayfa çevirir. Tema, müzik ya da yazı tipi seçilen bir satırda Start rastgele
birini seçer. Açılıp kapanan bir ayar **AÇIK** ya da **KAPALI** gösterir. Her değişikliği anında görürsünüz;
Circle ekrandan çıkarken her şeyi kaydeder, ayrıca onaylanacak bir şey yoktur. Tek istisna ekran modudur: o,
Seçenekler'den çıktığınızda denenir (aşağıda *Ekran:*'a bakın).

Bazı satırlar yalnızca anlamlı oldukları yerde görünür: CRT satırları yalnızca 4:3 görüntüde, RetroArch satırları
yalnızca RetroArch kuruluysa, dahili oyunlar yalnızca PlayStation Classic'te.

| Grup / ayar | Ne işe yarar |
|---|---|
| *Arayüz*: *Ekran:* | Başlatıcının ve PS1 emülatörünün ekran çözünürlüğünü belirler. *Otomatik* ekranın kendi modunu kullanır ve hangisi olduğunu da yazar, örneğin *Otomatik (1920x1080)*; ekranın sunduğu modlardan birini kendiniz de seçebilirsiniz. Konsol 720p, 1080p ve *CRT 4:3* (720x480) sunar; sonuncusu eski bir tüplü televizyon ya da 4:3 bir görüntü yakalama cihazı içindir. Görüntü televizyonunuza sığmıyorsa ya da bulanıksa bunu değiştirin. AutoBleem bir geliştirme makinesinde pencere içinde çalışıyorsa bu satır görünmez. |
| *CRT kenar boşluğu:* | Eski televizyonlar görüntünün kenarlarını kestiği için her şeyi biraz küçültür; %0'dan %10'a kadar, %1'lik adımlarla. İpucu çubuğu ve köşeler tamamen görünene kadar artırın. Yalnızca 4:3 çıkışta görünür, hemen etkili olur ve daha açılış ekranından önce uygulanır. |
| *Görüntü yüksekliği:* | Her 4:3 çıkışta - *CRT 4:3* ya da VGA veya PC çıkışındaki bir 4:3 mod - görüntüyü -40 ile +40 arasında, 2'şer adımla uzatır ya da kısaltır. Eski bir televizyonda görüntü basık duruyorsa ya da üstten ve alttan taşıyorsa bunu kullanın. Hemen etkili olur; RetroArch'taki oyun görüntüsü de buna uyar. |
| *Emülatör ekran ölçekleme:* | PS1 emülatörünün oyunun görüntüsünü ekranınıza nasıl sığdıracağını belirler. *1x1* PlayStation'ın kendi piksellerini küçük ve birebir gösterir; *2x (tam sayı)* ve *4:3 (tam sayı)* yalnızca tam katlarla büyütür, en keskin görüntüyü bunlar verir; *4:3* görüntünün asıl oranını korur; *Tam ekran* görüntüyü bütün ekrana yayar. Eski Widescreen anahtarının yerini almıştır. Klasik `pcsx-ab` ve RetroArch yalnızca tam ekranı ve 4:3'ü bilir. |
| *Ekran halesi:* | AÇIK olduğunda, oyun görüntüsünün ekranı doldurmadığı yerlerde yanında kalan boş şeritler siyah yerine görüntünün kendi yumuşak ışıltısıyla dolar. `pcsx-abnxt` ile çalışır. |
| *AutoBleem teması:* | Başlatıcının görünüşünü değiştirir. Temalar `Themes/` klasöründe durur; oraya bırakılan bir tema zip'i de adıyla listede çıkar. AutoBleem'le gelen temalar her güncellemede yenilenir; birini değiştirmek istiyorsanız önce başka bir adla kopyalayın. Varsayılan tema **ab2.0.0**'dır. |
| *Kapak stili:* | PS1 kapaklarının çevresine çizilen CD kutusu çerçevesini seçer. |
| *Kapak parıltısı:* | Raf her durduğunda seçili kapağın üzerinden bir parıltı geçer. |
| *Dil:* | Başlatıcının dilini belirler; 17 dil vardır ve değişiklik anında olur. |
| *Bildirim süresi:* | Bilgi baloncuklarının (*Gösteriliyor: ...*, taramanın özeti) ekranda ne kadar kalacağını belirler; 0 ile 20 saniye arası. 0'da *Kapalı* yazar ve baloncuklar hiç çıkmaz. Hata mesajlarının kendi sabit süresi vardır, böylece hiçbirini kaçırmazsınız. |
| *Açılış ekranı:* | Başlatıcı açılırken AutoBleem resmini gösterir; doğrudan rafa gitmek için kapatın. |
| *Animasyonlar:* | Bir ekrandan diğerine geçişi canlandırır; her ekranın anında gelmesini tercih ediyorsanız kapatın. |
| *Yazı tipleri*: *Varsayılan yazı tipini kullan:* | AÇIK olduğunda başlatıcı kendi yazı tipini (Red Hat Text) kullanır; bir sonraki satırda seçilen yazı tipini kullanmak için kapatın. |
| *Yazı tipi:* | Kendi yazı tipinizi seçer: `resources/fonts`, `RetroArch/fonts` ya da temanın klasöründeki herhangi bir `.ttf` veya `.otf` dosyası. Satır, gerçekten kullanılan yazı tipinin adını gösterir. |
| *Ses*: *Müzik:*, *Arka plan müziği:* | *Müzik:* başlatıcıda çalan parçayı seçer - temanın kendi müziğini ya da `resources/music` klasöründen bir dosyayı. *Arka plan müziği:* müzik çalıp çalmayacağına karar verir. |
| *Emülasyon*: *PS1 emülatörü:* | PS1 oyunlarınızın hangi emülatörde açılacağını seçer: varsayılan `pcsx-abnxt` (AutoBleem'in eklemeleriyle güncel PCSX-ReARMed) ya da klasik `pcsx-ab`. Bir oyun iyi çalışmıyorsa ötekini deneyin. Birinin kaydettiği devam noktası, oyun BIOS dosyası olmadan çalışmadıysa, ötekinde de kaldığı yerden sürer. |
| *Oyuncu 1 / oyuncu 2'yi değiştir (PS1 emülatörleri):* | İki PS1 emülatöründe de ilk iki kumandadan hangisinin 1. oyuncu, hangisinin 2. oyuncu olacağını değiştirir - kumandalar "ters" takılıysa işe yarar. Yalnızca iki ya da daha fazla kumanda bağlıyken önemlidir; tek kumandayla her zaman 1. oyuncu olursunuz. RetroArch bundan etkilenmez. Kullanılan PS1 emülatörü henüz yer değiştiremiyorsa AutoBleem bunu size söyler. |
| *Tüm PSX oyunlarını RA ile oyna:*, *RA yapılandırmasını güncelle:*, *RetroArch ayarlarını koru:* | Bu üçü yalnızca RetroArch kuruluysa görünür. İlki bütün PS1 oyunlarını RetroArch'ın PS1 çekirdeğinde (*PlayStation 1*; PC'de bu SwanStation'dır) açar. İkincisi, AutoBleem'in bir oyunu RetroArch'ta açarken kendi ayarlarını RetroArch'ın yapılandırmasına yazmasına izin verir. Üçüncüsü, RetroArch'ın kendi menüsünde yaptığınız bir değişikliğin RetroArch kapanırken korunmasını sağlar. |
| *Kütüphane*: *Dahili oyunları göster:* | Konsolun içinde gelen oyunları PlayStation listelerinde gösterir (yalnızca PlayStation Classic). |
| *Temiz oyun adları:* | AÇIK olduğunda (varsayılan) RetroArch oyun listeleri (USA), (Rev 1) ya da [!] gibi parantezli etiketler olmadan, derli toplu adlar gösterir; KAPALI dosya adlarını gösterir. Dosya adı oyunun bilgilerinde her zaman durur. PS1 oyunları etkilenmez, çünkü onların adları veritabanından gelir. |
| *Kapak resimlerini çevrimiçi al:* | Taramanın eksik kapakları libretro'nun sunucularından indirmesine izin verir (Raspberry Pi, PC, Windows). |
| *Güncellemeler*: *Güncellemeler:* | Başlatıcının hangi güncellemelere bakacağını seçer (bölüm 3.12): `release` (denenmiş sürüm), `testing` (denenmekte olan bir sonraki sürüm), `nightly` (en yeni geliştirme derlemesi) ya da `off`. Varsayılan değer, kurduğunuz sürüme göre belirlenir. Geliştirme makinesinde görünmez. |
| *Tanılama*: *Günlükleri USB bellekte tut:* | Bir sonraki açılıştan itibaren, yalnızca bir çökmeden sonra değil, her günlüğü bellekte tutar; bir sorunun peşindeyseniz açın (bölüm 7). |
| *Performansı göster:* | Sol alt köşede kare hızını, işlemci yükünü, iş parçacıklarını ve belleği gösteren bir katman açar; oyun sırasında emülatör de kendi FPS'ini ve işlemci yükünü gösterir. |

**Ekran modunu değiştirmek.** Seçenekler'den yeni bir *Ekran:* moduyla çıktığınızda AutoBleem o moda geçer ve *Bu ekran
modu korunsun mu?* diye sorar. Görüntü düzgünse onaylayın. Televizyonunuzda hiçbir şey görünmüyorsa bekleyin: onay
gelmezse AutoBleem bir geri sayımdan sonra önceki moda döner.

**4:3 ekranda temalar.** *CRT 4:3* modunda tema listesi yalnızca 4:3 yerleşimi olan temaları gösterir. Kullandığınız
temanın böyle bir yerleşimi yoksa, modu onayladıktan sonra (ve o modda her açılışta) onun yerine varsayılan tema
gelir ve bir bildirim bunu söyler: *Tema varsayılan temaya değiştirildi (CRT 4:3)*.

![Gruplar hâlinde seçenekler](../images/en/options.jpg)

![Arayüz grubu: CRT kenar boşluğu ve Görüntü yüksekliği](../images/en/options-display.jpg)

![4:3 yerleşimi olmayan bir temayla CRT 4:3'e geçince çıkan bildirim](../images/en/crt43-theme-notice.jpg)

### 3.7 Bir oyunun kendi ayarları

Her oyunun kendine ait ayarları olabilir. Çoğu oyun olduğu gibi sorunsuz oynanır, ama arada bir tanesinin biraz
yardıma ihtiyacı olur - daha keskin ya da daha yumuşak bir görüntü, akıcı kalsın diye atlanan bir kare, başka bir
hafıza kartı - ya da onu favori olarak işaretlemek istersiniz. Oyun düzenleyicisi, bunları başka hiçbir oyuna
dokunmadan yalnızca o oyun için değiştirdiğiniz yerdir.

Bir oyun seçiliyken **Down**'a basınca altındaki simge sırası açılır. Dört simge vardır: *AYARLAR* (bölüm 3.6'daki
seçenekler), *Oyun* (bu oyunun kendi ayarları), *HAFIZA KARTI* (onun hafıza kartı) ve *DEVAM ET* (durum kayıtları).
Birinin üzerine gelip Cross'a basarak açarsınız.

**Oyun düzenleyicisi** (*Oyun* simgesi) sağda oyunun bilgilerini gösterir - adı, yayıncısı, yılı, oyuncu sayısı,
klasörü ve hafıza kartı - solda da ayarlarını. Seçenekler'deki gibi Up ve Down ayarlar arasında gezer, Left ve Right
onları değiştirir; düğmeyi basılı tutmak hareketi tekrarlar. İşiniz bitince Circle değişikliklerinizi kaydedip sizi
geri götürür. Verilerinde adı olmayan bir oyun, klasörünün adıyla görünür.

Ayarlar dört grupta toplanır:

- **Oyun** grubu AutoBleem'in oyuna nasıl davrandığıyla ilgilidir. *Favori:* oyunu set seçicideki *Favori oyunlar*
  grubuna koyar. *Veriyi kilitle:* tarayıcıya oyunun adına, seri numarasına ve disk listesine tam sizin
  bıraktığınız gibi dokunmamasını söyler; böylece sonraki bir tarama değişikliklerinizin üzerine yazmaz. *Devam:*
  devam noktaları olan bir oyunu başlattığınızda ne olacağını belirler: *Sor* devam yuvası seçicisini gösterir,
  *Son slot* hemen en yeni yuvadan devam eder, *Asla* ise oyunu her zaman baştan başlatır. RetroArch kuruluysa iki
  satır daha vardır. *Işıklı silah oyunu:* ışıklı tabancayla oynanan oyunlar içindir: oyun *Işıklı silah oyunları*
  grubuna girer ve her zaman RetroArch'ta açılır, çünkü GunCon desteği RetroArch'ın PS1 çekirdeğindedir (bunu
  açmak bir sonraki satırı da açar). *RA ile oyna:* yalnızca bu oyunu PS1 emülatörü yerine RetroArch'ta açar.
- **Ekran** grubu görüntünün nasıl göründüğüyle ilgilidir. *Çözünürlük:* oyunu 1x ya da 2x çizer (yerleşik GPU ile);
  yalnızca 2x ile çalışan *Dikişleri kaldır:* ise bu boyutta görüntünün parçaları arasında beliren ince çizgileri
  gizler. *Dithering:* (*Kapalı*, *Açık*, *Her zaman*) PlayStation'ın renkleri karıştırmak için kullandığı ince nokta
  desenini yönetir; *Yumuşatma:* emülatörün yumuşatma ölçekleyicilerinden birini seçer. *Filtre:* görüntünün
  ekrana nasıl büyütüleceğine karar verir: *En yakın* düz pikseller gösterir, *Doğrusal* onları yumuşatır, *Keskin*
  ve *Keskin (basit)* pikselleri titreşim olmadan net tutar, bir de *Quilez* vardır. *CRT (hızlı)*, *CRT (raster)*
  ve *CRT-Pi* filtreleri eski bir televizyonu taklit eder ve tarama çizgilerini kendileri çizer; bu yüzden
  bunlardan biri seçiliyken tarama satırı ayarları soluklaşır. Öteki filtrelerde *Tarama satırları:* eski
  televizyonların koyu çizgilerini ekler, *Tarama satırı parlaklığı:* da ne kadar koyu olacaklarını ayarlar.
  *Çözünürlük*, *Dikişleri kaldır*, *Dithering*, *Yumuşatma* ve *Doğrusal* ile *En yakın* dışındaki filtreler
  `pcsx-abnxt` içindir; klasik `pcsx-ab` ve RetroArch başka bir filtreyi *En yakın* olarak gösterir.
- **İşleme** grubunda GPU *Eklenti:* ayarı ve *Kare atlama:* (*Otomatik*, *Kapalı* ya da 1 ile 3 kare) bulunur. Kare
  atlamak, fazla yavaş çalışan bir oyunun hızını korumasına yardım eder; bedeli daha az akıcı bir görüntüdür.
- **Emülatör** grubunda *Hız hilesi:*, işlemcinin *Saat hızı:*, *SPU interpolasyonu:* (sesin nasıl yumuşatılacağı),
  *Açılış logosu:* ve `pcsx-abnxt` ile *Sony düzeltmeleri:* vardır. *Açılış logosu:*'nu kapatırsanız BIOS ekranı
  atlanır; özel logosu yüzünden açılmayan bir homebrew diski için buna ihtiyacınız olur.

Görüntünün oranı ve ekranın çözünürlüğü oyun başına değil, hepsi için birden Seçenekler'de ayarlanır
(*Emülatör ekran ölçekleme:* ve *Ekran:*).

**Düzenleyicideki diğer düğmeler.** Triangle ekran klavyesiyle oyunun adını değiştirir. Square oyuna başka bir hafıza
kartı verir (*Hafıza kartını değiştir*). Oyun hâlâ kendi kartını kullanıyorsa Start o kartı yeni bir paylaşılan sete
çevirir, böylece başka oyunlar da onu kullanabilir (*Hafıza kartını paylaş*, bölüm 3.8). Bu ikisi konsolun dahili
oyunlarında sunulmaz. Left / Right ya da Up / Down'ı basılı tutmak burada da, RetroArch'ın oyun seçenekleri ve
çekirdek ekranlarında da hareketi tekrarlar.

Bir oyun ayarlarını kendi `pcsx.cfg` dosyasında saklar. USB bellekteki her oyunun böyle bir dosyası vardır,
çünkü taramada oluşturulur. USB sürücüdeki orijinal bir disk (bölüm 3.9a) ise kendi klasörünü ve `pcsx.cfg`
dosyasını ancak onu ilk kez başlattığınızda alır; o zamana kadar düzenleyicide yaptığınız bir değişiklik
saklanamaz ve düzenleyici *Kaydedilmedi: bu oyunun pcsx.cfg dosyası yok* der. Bu yüzden diski bir kez başlatın -
o andan itibaren ayarları her oyununki gibi saklanır. Koleksiyonunuzda zaten bulunan bir oyuna ait bir disk, en
baştan o oyunun klasörünü ve ayarlarını kullanır.

**Sürücüdeki bir disk** (bölüm 3.9a) için bazı ayarların anlamı yoktur; düzenleyici bu satırları soluk gösterir ve
birinin üzerine geldiğinizde alttaki satırda *Sürücüdeki disk için kullanılamaz* yazar.

![Sürücüdeki bir diskin oyun düzenleyicisi](../images/en/game-editor-disc.jpg)

**Emülatörde kaydedilen ayarlar.** Bir oyunu oynarken de ince ayar yapabilirsiniz: emülatörün kendi menüsünde
*Ayarları bu oyun için kaydet* bulunur (bölüm 3.9). Bir oyunun orada kaydedilmiş ayarları varsa oyun artık onlarla
oynanır. Oyun düzenleyicisi o zaman Ekran, İşleme ve Emülatör satırlarını kaydedilmiş değerleriyle, *Emülatörde
kaydedildi* başlığı altında soluk gösterir: okuyabilirsiniz ama değiştiremezsiniz. Yeniden oyun düzenleyicisinin
ayarlarını kullanmak isterseniz *Ayarların kilidini aç*'ı seçip onaylayın: emülatörün kaydettiği ayarlar silinir ve
satırlar yeniden değiştirilebilir olur. İki emülatör de, `pcsx-ab` ve `pcsx-abnxt`, aynı kayıtlı ayarları okuyup
yazar; hangisinin kaydettiği fark etmez.

![Oyun düzenleyicisi](../images/en/game-editor.jpg)

### 3.8 Hafıza kartları ve durum kayıtları

Gerçek bir PlayStation'da bir ya da iki hafıza kartını bütün oyunlarınız arasında paylaştırırdınız ve er geç yeriniz
biterdi. AutoBleem'de ise her PS1 oyununun varsayılan olarak kendi hafıza kartı vardır; ne boş yer derdi çekersiniz
ne de bir kaydın hangi kartta olduğunu düşünürsünüz. Kart, oyunun durum kayıtlarıyla birlikte
`Games/!SaveStates/<oyun klasörü>/` içinde saklanır.

**Paylaşılan hafıza kartı setleri.** Bazen oyunların birbirinin kayıtlarını görmesi gerekir - örneğin ilk oyunun
kaydını okuyan bir devam oyunu ya da aynı kartta durmasını istediğiniz bir serinin diskleri. Bunun için paylaşılan
bir set oluşturursunuz: birkaç oyunun birlikte kullandığı tek bir kart. Setler `Games/!MemCards/` içinde durur;
onları sistem menüsündeki *Hafıza kartları* ile yönetirsiniz. Square yeni bir set oluşturur (adını ekran
klavyesiyle yazarsınız), Cross seçili seti yeniden adlandırır, Triangle ise önce sorup onu siler. Bir oyunu bir sete
bağlamak için oyun düzenleyicisinde *Hafıza kartını değiştir*'i (bölüm 3.7) ya da oyunun *HAFIZA KARTI* simgesini
kullanın.

**Hafıza kartı düzenleyicisi** bir oyunun *HAFIZA KARTI* simgesinden açılır. Asıl konsolun hafıza kartı ekranındaki
gibi, oyunun kartını ve ikinci bir kartı yan yana, her kaydın simgesi ve adıyla gösterir. Square seçili kaydı öteki
karta kopyalar, Triangle onu siler, Select ise bir kartı birleştirir: boş blokları bir araya toplar, böylece büyük
bir kayıt yeniden sığar. Start sağda hangi setin görüneceğini seçmenizi sağlar, Cross da iki kartı bellekten yeniden
yükler. Oyunun henüz hiç yazmadığı bir kart - içinde hiç kayıt yapmadığınız bir oyunun kartı - boştur ve adının
yanında *henüz kart yok* yazar. Bir şey değiştirdiyseniz AutoBleem düzenleyiciden çıkmadan, kartları yeniden
yüklemeden ya da başka bir set göstermeden önce *Hafıza kartı verilerini kaydetmek istiyor musunuz?* diye sorar.

![Hafıza kartı düzenleyicisi](../images/en/memory-card-editor.jpg)

**Devam noktaları.** Pek çok PS1 oyunu yalnızca belli yerlerde kayıt yapmaya izin verir ve bırakmanız gerektiğinde
her zaman bu yerlerden birine yetişemezsiniz. Devam noktaları bu sorunu çözer: bir PS1 oyunundan konsolun Reset
düğmesiyle (Pi'de ya da PC'de emülatörün menüsünden) çıktığınızda AutoBleem tam kaldığınız yerin bir durum kaydını
alır. Oyundan çıkarken bunu yazdığı sırada emülatör *Lütfen bekleyin...* gösterir. Bir dahaki sefere o andan devam
edersiniz.

Devam noktalarını oyunun *DEVAM ET* simgesinin altında bulursunuz. Devam noktası olan bir oyunun simgesinde o anın
küçük bir resmi görünür; hiç olmayanın simgesi soluktur. Devam yuvası seçicisinde çerçeveli kartlar hâlinde dört
yuva vardır; her birinde o anın resmi, yuva numarası ve tarihi bulunur. En yenisi **EN YENİ** olarak işaretlenir,
kullanılmamış bir yuvada ise *Sürdürme noktası yok* yazar. Cross oyunu seçili yuvadan sürdürür, Triangle onu siler.
Oyunu başlattığınızda seçicinin çıkıp çıkmayacağı, oyunun *Devam:* ayarına bağlıdır (bölüm 3.7).

RetroArch'ta oynadığınız PS1 oyunlarının da devam yuvaları vardır. Her yuvanın üzerinde bir rozet - AutoBleem 2 logosu
ya da RetroArch logosu - bulunur, böylece onu hangi emülatörün yazdığını görürsünüz.

![Devam yuvası seçicisi](../images/en/resume-picker.jpg)

### 3.9 Oyunları, RetroArch'ı ve Uygulamaları başlatmak

En sık yapacağınız şey bir oyunu başlatmak olduğu için bu iş tek düğmeyle olur: oyunu rafta seçip **Cross**'a basın.
PS1 oyunu, Seçenekler'de seçtiğiniz PS1 emülatöründe tam ekran açılır (bölüm 3.6) ve siz çıkana kadar oynar. Bir PS1
oyununu RetroArch'ta oynamayı tercih ederseniz - orada daha iyi çalıştığı için ya da RetroArch'ın seçeneklerini
sevdiğiniz için - bunun yerine **Square**'e basın.

**Oyundan çıkmak.** PlayStation Classic'te konsolun kendi düğmeleri beklediğiniz işi yapar. Öndeki **Reset** sizi
başlatıcıya döndürür ve kaldığınız yerde bir devam noktası bırakır, böylece sonra devam edebilirsiniz (bölüm 3.8);
oyun içi menü açıkken bile çalışır. **Power** konsolu kapatır. Raspberry Pi'de ya da PC'de böyle düğmeler olmadığından
oradan aşağıda anlatılan oyun içi menüyle çıkarsınız.

Her kumandada aynı şekilde çalışan bir çıkış yolu daha var - konsolun kendi kumandasında, USB kumandada ya da Bluetooth
kumandada: **Start + Select'i ya da Home'u 2 saniye basılı tutun**, AutoBleem'e dönersiniz. Aynı düğmelere kısa
basarsanız bunun yerine emülatörün menüsü açılır. Başlatıcı ipuçlarında ikisini de hatırlatır (*Select+Start veya Home
tuşunu 2 saniye basılı tut: AutoBleem'e dön* ve *Select+Start veya Home kısa basış: emülatör menüsü*). Uygulamaların
emülatör menüsü olmadığından orada yalnızca uzun basış bir şey yapar. Konsolda Reset bir Uygulamayı da her zaman
durdurur.

**Oyun içi menü.** `pcsx-abnxt` ile emülatörün, oynarken ihtiyaç duyduğunuz şeyler için kendi menüsü vardır: kayıt
yapmak, disk değiştirmek, görüntüyü ayarlamak, kumandaları seçmek. Menü düğmesine basın - kumandanızda varsa Home'a,
yoksa **Select + Start**'a, klavyede **Esc**'ye - oyun menünün arkasında, son karesi arka planda kalacak şekilde
durur. Menü düğmesini 2 saniye basılı tutmak Reset ile aynı işi görür: oyundan çıkar. Menünün üç sekmesi vardır,
aralarında L1 ve R1 ile geçersiniz. Menü nerede kaldığınızı hatırlar, bir dahaki sefere aynı sekmede ve aynı satırda
açılır.

- **Oyun** sekmesi oyunun kendisiyle ilgilidir. *Oyuna devam et* menüyü kapatır ve oynamaya devam edersiniz.
  *Kayıtlar* altında *Hızlı kayıt* o anı saklar, *Hızlı yükleme* onu geri getirir. *Otomatik kaydı yükle* sizi oyunun
  en fazla 30 saniye önceki hâline götürür - emülatör oynarken bu kopyayı bellekte tutar ve geri alamayacağınız bir
  hatadan sizi kurtarır. *CD disk* altında *Disk değiştir*, birkaç diskli bir oyun bir sonraki diski istediğinde
  içindir; *Oyunu sıfırla* oyunu baştan başlatır. *Ayarları bu oyun için kaydet* yalnızca bu oyun için seçtiğiniz
  ayarları saklar (bölüm 3.7). *PCSX menüsü* PCSX-ReARMed'in kendi sayfalarını - seçeneklerini, hilelerini ve
  Hakkında sayfasını - açar; *Çık* ise sizi AutoBleem'e döndürür.
- **Görüntü** sekmesinde oyunun görünüşünü izlerken değiştirirsiniz: *Ekran*, *Çözünürlük* (1x ya da 2x), *Dikişleri
  kaldır*, *Dithering*, *Ölçekleme*, *Ekran halesi*, *Yumuşatma*, *Filtre*, *CRT maskesi*, *Scanlines* ve
  *Scanline parlaklığı*. Bunlar oyun düzenleyicisindeki ayarların aynısıdır (bölüm 3.7) ve her satırın sağında ne
  işe yaradığını anlatan bir yardım satırı vardır. *Ekran* ekranın çözünürlüğüdür; konsolda onu Seçenekler'de
  seçersiniz, burada yalnızca gösterilir. *Ekran halesi*, geniş bir televizyonda 4:3 görüntünün yanlarında kalan
  karanlık şeritler içindir: onları görüntünün kendi kenarlarıyla, aynalanmış ve karartılmış olarak doldurur;
  böylece oyun iki siyah bant arasına sıkışmış durmaz, sanki şeritlere doğru taşar. *CRT maskesi* görüntünün
  üzerine eski bir tüpün fosfor desenini serer - *Açıklık* bir Trinitron'un ince şeritlerini, *Yarık* ve *Delta*
  diğer tüplerin noktalarını verir; bu satır yalnızca CRT (raster) filtresiyle vardır. CRT-Pi filtresi 1080p'de konsol için fazla ağırdır. Geçerli olmayan bir satır soluk görünür ve yardım satırı
  nedenini söyler.
- **Kontrolcüler** sekmesi PlayStation'ın iki girişine, *Kontrolcü 1* ve *Kontrolcü 2*'ye, ne takılı olduğuna karar
  verir: standart (dijital) bir kumanda, analog bir kumanda (DualShock), bir tabanca ya da hiçbir şey. Bazı oyunlar
  yalnızca belli bir kumanda türüyle çalışır. Değişiklik oyuna döndüğünüzde geçerli olur.

Menü başlatıcının kendi ab2.0.0 görünüşüyle çizilir, böylece başka bir programmış gibi durmaz; kumanda pillerinizi ve
son hızlı kaydınızın resmini de gösterir.

**RetroArch oyunları.** Başka bir sistemin oyunu, başlatıcının o sistem için seçtiği çekirdekle RetroArch'ta açılır.
İşiniz bitince RetroArch menüsündeki *Close Content* ya da *Quit RetroArch* sizi başlatıcıya geri getirir. Bir sistemi
hangi çekirdeğin oynatacağını değiştirmek isterseniz Hızlı menüden *RetroArch çekirdekleri*'ni açın (bölüm 3.4);
listenin en üstünde *PlayStation 1* çekirdeği durur. RetroArch'ın kendi menüsünü (XMB) - ayarları ve kendi içerik
listeleri için - istiyorsanız sistem menüsünden *RetroArch*'ı seçin: RetroArch o zaman hiçbir şey yüklenmeden açılır.

![RetroArch çekirdekleri penceresi; en üstte PlayStation 1 çekirdeği](../images/en/retroarch-cores.jpg)

**Uygulamalar.** Uygulamalar oyun değil, programdır: konsol araçları ve konsolda RetroArch paketiyle gelen ek
uygulamalar - Doom, Quake, Amiga ve daha fazlası. Onları Apps setinde bulursunuz. Bir Uygulama açılmadan önce
AutoBleem onun tanıtım metnini gösterir; böylece ne olduğunu ve nasıl kullanıldığını bilirsiniz. Cross onu başlatır,
Circle sizi rafa geri götürür.

![Bir Uygulamanın, açılmadan önce gösterilen tanıtım metni](../images/en/app-start.jpg)

**Bir Uygulamanın ayarları.** Pek çok Uygulama belli bir kumanda için yazılmıştır; bu yüzden sizin kumandanızı nasıl
gördüklerini değiştirebilirsiniz. Uygulamayı seçin, simge sırasını açın ve *Oyun*'u seçin: Uygulamanın *Oyun
ayarları* açılır (*Bu programın nasıl başlatılacağını değiştir*). *Kumanda modu:* Uygulamaya hangi kumandanın takılı
olduğunun söyleneceğini belirler. *Otomatik* Uygulamanın kendi istediğini kullanır; *PSC kumandası* ve *Xbox 360
kumandası* kumandanızı konsolun kumandası ya da bir Xbox 360 kumandası olarak tanıtır; *PSC kumandası (sistem)* ve
*Xbox 360 kumandası (sistem)* aynı şeyi sistemin kendisi üzerinden yapar. Bir Uygulama kumandanıza olması gerektiği
gibi tepki vermiyorsa başka bir mod deneyin. *Yön tuşları çubuk gibi:* yalnızca analog çubuğu dinleyen bir Uygulama
için yön tuşlarının çubuğu oynatmasını sağlar; *Çubuk yön tuşları gibi:* bunun tersini yapar.

Bazı Uygulamalar ilk açılışta size bir soru sorar. Biri, kontrollerini ayarlayabilmek için *Kumandanızda hangi
kontroller var?* diye sorar: yalnızca yön tuşları olan bir kumanda için *Tek yön tuşu*, öbür durumda *Analog
çubuklar* deyin. Windows çalıştıran bir Uygulama *Ne yapmak istiyorsunuz?* diye sorup Windows'u çalıştırmayı, kurmayı,
DOS çalıştırmayı ya da Windows'u kaldırmayı önerir. Bir tuş atamanıza izin veren Uygulama da *Düğmelerden birine
basın.* der.

![Bir Uygulamanın oyun ayarları](../images/en/app-game-settings.jpg)

PE çalıştırıcısıyla açılan bir Windows programı (bir PE uygulaması, bölüm 3.3) sizinle AutoBleem'in kendi ekranları
üzerinden konuşur: göstermek istediği bir mesaj *Mesaj* olarak, seçenekli bir soru da *Bir seçenek seçin* olarak
çıkar; ikisinin de başlığında Uygulamanın adı yazar.

![Bir PE uygulamasının sorusu, AutoBleem ekranı olarak](../images/en/pe-dialog.jpg)

### 3.9a USB sürücüdeki bir disk

Konsola, bir Raspberry Pi'ye ya da AutoBleem belleğinden açılmış bir PC'ye sıradan bir USB CD/DVD sürücüsü bağlayıp
hiçbir şey kopyalamadan doğrudan orijinal bir PlayStation diskinden oynayabilirsiniz. Taktığınız disk başlatıcıda bir
oyun daha gibi görünür. Bu Windows'ta çalışmaz.

**Diski belleğe kopyalamak.** Oyun disk olmadan da hep elinizin altında olsun istiyorsanız Square'e basın (*Diski
kopyala*). AutoBleem önce oyunu kopyalamak isteyip istemediğinizi sorar ve ne kadar yer kaplayacağını söyler, sonra
oyunu `Games` klasörüne tek bir CHD dosyası olarak kaydeder (birkaç diskli bir oyun ayrıca bir `.m3u` dosyası alır,
böylece oyunda disk değiştirmek çalışır). Kopyalama sırasında hızı ve kalan süreyi görürsünüz; *Durdur* kopyalamayı
keser. İş bitince oyun rafta diğerleri gibi durur. AutoBleem `Games` klasöründe zaten bulunan bir oyunu ya da yer
olmayan bir oyunu kopyalamaz; ikinci durumda ne kadar yere ihtiyacı olduğunu söyler. Çizik bir disk de kopyalanabilir:
okunamayan kısımlar sıfırla doldurulur ve AutoBleem bunlardan kaç tane olduğunu söyler. Böyle bir kopya çalışabilir
de, çalışmayabilir de.

Square, disk görünümündeki her PlayStation oyun diski için kopyalamayı önerir; kapak veritabanlarının tanımadığı
diskler için de. Veritabanlarının tanıdığı bir oyun kendi adıyla kopyalanır; birkaç diskli bir oyunda diskleri
birbiri ardına kopyalayın, `.m3u` onları sırayla, 1. disk başta olacak şekilde listeler. Veritabanlarının tanımadığı
bir disk ise seri numarasıyla adlandırılır, tek disk olarak kopyalanır ve rafta kapağı olmaz. Kopyalama penceresi,
*Disk kopyalanıyor*, kopyalama bitene ya da durdurulana kadar ekranda kalır - başlatıcı bu arada bekler - ve hızı
sıradan bir CD sürücüsünün katı olarak gösterir. Kopyalama başarısız olursa AutoBleem nedenini söyler.

![Bir diskin kopyalanması](../images/en/disc-copy.jpg)

**Diskten oynamak.** Bir disk taktığınızda, disk okunur okunmaz **disk görünümü** kendiliğinden açılır. Diskin
kapağını - kapak veritabanlarından ya da internetten indirilmiş olarak - seri numarası ve adıyla birlikte gösterir;
Cross oyunu başlatır. Diskten oynanan bir PS1 oyunu devam noktalarını ve kayıtlarını kendine ait bir klasörde tutar;
böylece bellekteki bir oyunda olduğu gibi bırakıp sonra devam edebilirsiniz. Oyundan sonra ya da seçeneklere veya
bir eklentinin ayarlarına girip çıktıktan sonra disk görünümüne dönersiniz. Diğer oyunlarınıza göz atmak için
Circle ile çıkarsanız disk sürücüde kalır ve raftayken Circle görünümü geri getirir; boş bir rafta R1 (*Disk*) de
onu açar. Oyunların olduğu bir rafta R1 baş harfler arasında atlama işini yapmaya devam eder. Diski çıkardığınızda
disk görünümü kapanır.

![Disk görünümü](../images/en/disc-view.jpg)

**Sürücü göstergesi** ekranın üst kısmında sürücünün ne yaptığını gösterir; böylece beklemeniz gerekip gerekmediğini
bilirsiniz. Bağlı bir sürücü yoksa hiçbir şey görünmez. İçinde disk olmayan bir sürücü soluk bir disk simgesiyle
görünür. Disk okunurken simge yanıp söner ve *Disk okunuyor...* yazar; disk hazır olunca simge, diskin adıyla
birlikte yanar. PlayStation oyunu ya da müzik CD'si olmayan bir disk takarsanız göstergede *Bu bir PlayStation diski
değil* yazar; sürücü diski o an okuyamıyorsa *Disk şu anda okunamıyor* yazar.

![Sürücü göstergesi](../images/en/disc-chip.jpg)

**Müzik CD'leri.** Sürücü müzik CD'si de çalar. Bir müzik CD'si disk görünümü yerine **CD çaları** açar. Disk, parça
listesi ve toplam süresiyle birlikte *Ses CD'si* olarak görünür; altındaki satır seçili parçanın adını yazar ve
tekrar ile karışık çalmanın açık olup olmadığını söyler. Çaların çalamadığı bir diskte *Bu disk çalınamıyor*
yazar. Düğmeler şöyledir:

| Düğme | CD çalarda |
|---|---|
| Cross | Seçili parçayı çalar. |
| Start | Müziği duraklatır, sonra yeniden başlatır. |
| Square | Müziği durdurur. |
| L1 / R1 | Önceki ya da sonraki parçaya geçer. |
| L2 / R2 | Parçada beşer saniye geri ya da ileri sarar. |
| Triangle | Neyin tekrarlanacağını değiştirir: hiçbir şey, bütün disk ya da çalan parça. |
| Select | Karışık çalmayı açıp kapatır; açıkken parçalar rastgele sırayla çalar. |
| Circle | CD çalardan çıkar. |

![CD çalar](../images/en/cd-player.jpg)

**LibCrypt diskleri.** Çoğu Avrupa'da çıkmış bazı PlayStation oyunlarında LibCrypt adlı bir kopya koruması vardır.
Emülatörün bunları çalıştırabilmesi için korumanın verilerini taşıyan küçük bir `.sbi` dosyasına ihtiyacı vardır.
AutoBleem bu dosyayı, böyle bir disk oynanmadan önce ve siz onu kopyalarken siteden kendisi indirir; dosya oyunla
birlikte kopyalanır. Bunun için ağ gerekir: Raspberry Pi'de ya da PC'de zaten bağlı olduğu ağ, konsolda ise
PSC-Bios'ta kurduğunuz Wi-Fi.

Sürücüdeki bir disk için bir oyunun bazı ayarlarının anlamı yoktur; bu yüzden oyun düzenleyicisi o satırları soluk
gösterir (bölüm 3.7).

### 3.10 Oyun eklemek

Oyunlarınız doğru yerde olduğu sürece AutoBleem onları kendisi bulur. Bu bölüm her oyun türünün nereye gittiğini
anlatıyor; böylece her tarama onları adlarıyla ve kapaklarıyla rafa koyar.

**PS1 oyunları** `Games` klasörüne, **her oyun kendi klasörüne**, oyunun adıyla gider. Oyunları kendi açtığınız
klasörlerde de toplayabilirsiniz; böyle her klasör set seçicide bir grup olur (bölüm 3.3):

```
Games/
  Crash Bandicoot/            Crash Bandicoot.cue + Crash Bandicoot.bin
  Final Fantasy VII/          Final Fantasy VII (Disc 1).chd, (Disc 2).chd, (Disc 3).chd
  Platformers/                bir oyun klasörü: set seçicide kendi grubu olur
    Klonoa/                   Klonoa.pbp
```

AutoBleem bilinen disk görüntüsü biçimlerini okur: `.bin` (ya da `.img`) dosyasıyla birlikte `.cue`, `.pbp`,
`.chd` (zstd ile sıkıştırılmış olanlar da), `.iso` ve taramanın sizin için açtığı `.ecm`. Zip'lenmiş bir oyun da
olur: **Unzip** işlemcisi onu tarama okumadan önce açar (bölüm 3.14).

Çok düzenli olmanıza gerek yok. Birkaç diskli bir oyun bütün diskleriyle tek bir klasöre konur, ama `Game (Disc 1)`,
`Game (Disc 2)` gibi adlarla klasörler kopyalarsanız tarama onları tek bir `Game` klasöründe birleştirir. Doğrudan
`Games/` içine tek tek dosya olarak atılan oyunları da tarama kendi klasörlerine yerleştirir.

**Adlar ve kapaklar** kendiliğinden gelir. Tarama her diskin seri numarasını okur; adı, yayıncıyı, yılı, oyuncu
sayısını ve bölgeyi RetroArch'ın PlayStation veritabanından ya da kapak veritabanlarından alır. Kendi kapağınızı
kullanmak istiyorsanız oyunun görüntü dosyasının yanına aynı adla bir PNG ya da JPEG koyun. Böyle bir dosya yoksa kutu
kapağı kapak veritabanlarından ya da, RetroArch kuruluysa, libretro'nun küçük resim setinden gelir; Raspberry Pi'de,
PC'de ya da Windows'ta eksik bir kapak internetten indirilir (Seçenekler → *Kapak resimlerini çevrimiçi al:*).
Tarama bir şeyi yanlış bulursa oyun düzenleyicisinde düzeltin ve *Veriyi kilitle:*'yi açın; bir sonraki tarama
değişikliğinize dokunmaz.

**Başka sistemlerin oyunları** `RetroArch/roms/` altına, **her sistem için bir klasöre, RetroArch'ın veritabanlarının
o sisteme verdiği adla** gider - örneğin `Nintendo - Nintendo Entertainment System`, `Nintendo - Super Nintendo
Entertainment System`, `Sega - Mega Drive - Genesis`, `Nintendo - Game Boy Advance` ya da `FBNeo - Arcade Games`
(veya `Arcade`). Klasörler sizin için hazırlanmıştır; ROM'lar zip hâlinde kalabilir. Raspberry Pi'de, PC'de ya da
Windows'ta tarama onları kendisi okur ve RetroArch'ın oynatma listelerini yazar. Konsol belleği bunu tek başına
yapamaz; orada PC'de **UpdateRoms**'u çalıştırırsınız (bölüm 5).

**Uygulamalar** `Apps/<ad>/` altına gider; her birinde bir `app.ini` - adı, simgesi ve neyin çalıştırılacağı - ve
bir `run.sh` bulunur.

**Paketler.** Bazı Uygulamalar oyun motorudur: bir oyunu oynatabilmeleri için sizde olan o oyunun verilerine
ihtiyaç duyarlar. Doom, Quake, OpenArena, Heretic, Hexen, Strife, Duke Nukem 3D, Shadow Warrior, Theme Hospital, DOS
oyunları ve daha fazlası böyle çalışır. Oyunun dosyalarını bellekteki bir `Packages` klasörüne, her oyun için bir
klasör olacak şekilde koyun - örneğin `Packages/Doom/DOOM2.WAD` - AutoBleem onları beraberinde gelen bir tablo
(`rc/packages.ini`) sayesinde tanır. Tanıdığı bir klasördeki ayrı ayrı oyun dosyaları da kendi başlarına birer
pakettir. AutoBleem dosyalarınızı yalnızca okur, hiçbir zaman değiştirmez. Bir paket Mağaza'dan da gelebilir
(bölüm 3.13).

Başlatıcı gösteriyorsa Apps sekmesindeki *Paketler* satırı (bölüm 3.3) bulunan oyun verilerini listeler. Bir girişin
üzerinde Cross onun **paket bilgisini** açar: verinin ne içerdiği, bir açıklama, dosyaların nerede durduğu ve nereden
geldiği (kendi dosyalarınız, Mağaza, bir mod ya da bir Uygulamanın içinde gelen dosyalar), shareware mi yoksa ücretsiz
mi olduğu ve onu hangi kurulu Uygulamanın çalıştırdığı. Kurduklarınızdan hiçbiri onu çalıştıramıyorsa bilgi ekranı
bunu söyler.

Bir motor Uygulamasını başlattığınızda AutoBleem onun çalıştırabileceği oyun verilerini arar. Tek bir veri seti
varsa oyun hemen açılır. Birkaç tane varsa bir liste (*Oyun verisini seç*) hangisini oynamak istediğinizi sorar ve
geçen sefer seçtiğinizin üzerinde açılır. Hiç yoksa AutoBleem Uygulamanın hangi verilere ihtiyaç duyduğunu ve onları
nereye koymanız gerektiğini söyler, hiçbir şey açılmaz.

**Kendi oyunlarınız.** AutoBleem bir veriyi tanımazsa paket bilgisinde *Tanınmadı. Bu bir oyunsa kılavuza bakın:
Kendi oyunlarınız.* yazar. Tablo yalnızca kendisi için hazırlandığı oyunları bilir. Başka bir oyun için `Packages`
klasöründeki kendi `packages.ini` dosyanıza o oyunun satırını yazın: AutoBleem önce sizinkini okur, yani sizin
satırlarınız geçerli olur.

![Paket seçici: hangi oyun verisiyle başlanacağını seçtiğiniz yer](../images/en/packages-picker.jpg)

![Paket bilgisi](../images/en/package-info.jpg)

**Yalnızca bir bölümü taramak.** Oyunları yalnızca bir sete ya da bir klasöre eklediyseniz *Oyunları yeniden tara*
sadece o bölümü tarayabilir; bu, her şeyi taramaktan daha hızlıdır ve baloncuğu iş bitince kaybolur.

**Temalar** `theme.json` dosyaları ve resimleriyle birlikte `Themes/<ad>/` altına gider - ya da temanın zip'ini
olduğu gibi `Themes/` içine bırakın.

### 3.11 PS1 BIOS'u

BIOS, PlayStation'ın kendi açılış programıdır ve emülatör oyunları en doğru şekilde gerçek BIOS ile oynatır. **PlayStation
Classic**'te hiçbir şey yapmanız gerekmez: emülatör konsolun kendi BIOS'unu kullanır. **Raspberry Pi'de, PC'de ve
Windows'ta** kendi PS1 BIOS dosyalarınızı `System/Bios/` içine koyun: `romw.bin` (ABD/Avrupa SCPH-5501/5502) ve
`romJP.bin` (Japon oyunları için kullanılan Japon SCPH-5500). Kurulum programları bunları RetroArch BIOS paketlerinden
doldurur, ama sizin dosyalarınız zaten oradaysa dokunmaz - sizinkilerin yerine asla başkasını koymazlar. Bu dosyalar
olmadan emülatör yerleşik HLE BIOS'uyla çalışır. Bu yedek BIOS'u pek çok oyun kabul eder, bazıları etmez; bir oyun
açılmıyorsa ilk bakacağınız şey eksik bir BIOS'tur.

### 3.12 Güncellemeler

AutoBleem kendini güncel tutar; yeni özellikleri ve düzeltmeleri hiçbir şeyi yeniden kurmadan alırsınız. Başlatıcı
açılırken ve sonra günde bir kez, kendi **kanalında** yeni bir sürüm olup olmadığına sitede bakar. Kanalı Seçenekler
→ *Güncellemeler:*'de seçersiniz: `release`, `testing`, `nightly` ya da hiç bakmasını istemiyorsanız `off`. Günlük
denetimi beklemek istemiyorsanız sistem menüsündeki *Yazılım güncellemesi* hemen bakar.

Yeni bir sürüm varsa AutoBleem ne yapacağınızı sorar. *Şimdi güncelle* onu indirip kurar; bu birkaç dakika sürer.
*Yarın hatırlat* bir gün sonra yeniden sorar, *Bu sürümü atla* ise bu sürüm için bir daha sormaz. Ne seçerseniz seçin
oyunlarınız, kayıtlarınız ve ayarlarınız hep yerinde kalır; güncellemeden sonra başlatıcı oyunlarınızı bir kez daha
tarar. Hangi derlemeyi kullandığınızı sol üst köşedeki kanal etiketi gösterir (bölüm 3.1).

Güncellemenin nasıl kurulacağı makineye göre değişir:

- **Raspberry Pi**'de ve **PC belleğinde** kurulum programı indirmeden sonra ilk açılıştakiyle aynı ilerleme
  ekranıyla yeniden çalışır ve daha yeni bir RetroArch varsa onu da önerir. Sonra başlatıcı geri gelir.
- **Windows**'ta indirilen kurulum dosyası açılır, yeni sürümü kurar ve yeni başlatıcıyı açar.
- **PlayStation Classic**'te yalnızca **AutoBleem kernel'i** (ABFlashKit, bölüm 6.2) kurulu olan ve PSC-Bios'ta bir
  **Wi-Fi ağı** ayarlanmış (bölüm 6.1) bir konsol kendini güncelleyebilir; kutudan çıktığı hâliyle konsolun ağı
  olmadığı için başlatıcı hiç bakmaz. *Şimdi güncelle*'den sonra başlatıcı kapanır ve bellek güncellenirken ekranda
  AutoBleem resmi kalır; bu birkaç dakika sürer, ardından yeni başlatıcı açılır. Ağ yoksa *Yazılım güncellemesi*
  *Bağlı değil* der. Her konsol belleği PC'den `AutoBleemInstaller.exe` ile de güncellenebilir (bölüm 2.1).

### 3.13 Eklentiler ve AutoBleem Mağazası

**Eklentiler** AutoBleem'in kendisini değiştirmeden başlatıcıya yeni şeyler - kendi ekranlarını ve özelliklerini -
ekler. AutoBleem Mağazası da PSC-Bios da birer eklentidir. Bir eklenti bellekte `Extensions/<ad>/` içinde durur
(Raspberry Pi'de veri bölümünde, Windows'ta veri klasöründe); bir eklenti kurmak için zip'ini oraya açın.

Onları görmek için sistem menüsünü açın (**L2 + R2**) ve *Eklentiler*'i seçin. AutoBleem ekibinden gelenler en
üsttedir, diğerleri *Üçüncü taraf eklentiler* başlığı altında gelir. Cross seçili eklentiyi çalıştırır, Triangle
onu kapatır ya da yeniden açar. Konsoldaki PSC-Bios bunun istisnasıdır: Wi-Fi'yi, kumandaları ve saati onunla
ayarladığınız için orada kapatılamaz. Bir eklenti çalışamıyorsa satırı nedenini söyler: ağa ihtiyacı vardır ve ağ
yoktur, bu sistem için yapılmamıştır, AutoBleem'in başka bir sürümü için yapılmıştır ve güncellenmesi gerekir ya da
yüklenemedi. Bir eklenti başlatıcıyı durdurursa AutoBleem onu kapatır ve liste bunu size bildirir; buradan yeniden
açabilirsiniz.

![Eklentiler listesi](../images/en/extensions.jpg)

**AutoBleem Mağazası** ilk eklentidir: AutoBleem'in çalıştığı her sistemde Uygulamalara ve oyunlara göz atıp tek
tuşla kurabileceğiniz bir yer. PlayStation Classic'te bunun için AutoBleem kernel'i gerekir, çünkü Wi-Fi kernel'le
gelir. Mağaza'yı Hızlı menüden açarsınız (*Mağaza*, bölüm 3.4). Dört sekmesi vardır, aralarında L1 ve R1 ile
geçersiniz.

**Apps** ve **Games** sekmeleri kaynakların sunduklarını listeler; her öğenin resmi, sürümü, boyutu ve geldiği
kaynağın küçük simgesi yanında durur. Apps sekmesi ayrıca lisansları ve kaynaklarıyla birlikte PE uygulamalarını ve
oyun verisi paketlerini (bölüm 3.10) listeler. Zaten kurduğunuz şeylerin üzerinde bir *Installed* rozeti olur. İpucu
çubuğu seçili satırda geçerli olan düğmeleri gösterir:

| Düğme | Apps ve Games sekmelerinde |
|---|---|
| Cross | Öğeyi kurar - ya da günceller, bir hatadan sonra yeniden dener veya bekleyen ya da süren bir indirmeyi iptal eder. |
| Triangle | Mağaza'nın kurduğu bir şeyi kaldırır. |
| Square | Listeleri kaynaklardan yeniler. |
| L2 / R2 | Önceki ya da sonraki baş harfe atlar. |
| Select | Tek bir kaynağın neler sunduğunu görmek istediğinizde kaynakları birer birer gösterir. |
| Start | Adlar arasında arama yapar. |

Resimler bir kez yüklendikten sonra saklanır, böylece listeler bir dahaki sefere hızlı açılır; yüklenemeyen bir resim
yeniden denenebilir.

**Downloads** sekmesi inen, bekleyen, başarısız olan ya da kurulmuş olanları, düzgün ilerleyen bir çubukla gösterir.
Başında beklemeniz gerekmez: indirmeler arka planda, Mağaza'dan çıktıktan sonra da sürer; siz başlatıcıda başka bir
yerdeyken bir baloncuk süren indirmeyi hızı ve kalan süresiyle gösterir (örneğin `1.4 MB/s · 0:42`). Bir oyunu
başlatmak ya da cihazı kapatmak indirmeleri yalnızca duraklatır; duran bir indirme kaldığı yerden devam eder. Ağ
giderse öğede *Waiting for the network* yazar ve ağ geri geldiğinde kaldığı yerden sürer; 30 dakika ağsız kalırsa
vazgeçer. 2 GB'tan büyük indirmeler, 32 bit derlemeler de dahil her platformda çalışır. Kurduğunuz bir oyun bir sonraki
taramadan sonra, kapağı Mağaza'daki resmi olarak rafta belirir.

**Sources** sekmesi listelerin nereden geldiğini her birinin simgesiyle gösterir: AutoBleem'in kendi kataloğu,
`System/Extensions/store/sources/` içine bırakılmış her TSV listesi ve *Add a source URL* ile kendi eklediğiniz
adresler. Kendi eklediğiniz bir kaynağın üzerinde Cross ile onu yeniden adlandırabilir, adresini değiştirebilir,
`http://` ile `https://` arasında geçirebilir ya da kaldırabilirsiniz.

![Mağaza'nın Apps sekmesi](../images/en/store-apps.jpg)

![Kendi eklediğiniz bir kaynağın menüsü](../images/en/store-source-menu.jpg)

AutoBleem'in kendi kataloğunun sundukları indirme sitesinde de, `https://autobleem.retromenele.pl/store/`
adresinde listelenir. Kendi eklediğiniz bir kaynak ise başka bir konudur: **eklediğiniz kaynakların içeriğinden siz
sorumlusunuz.**

**Evdeki ağınızda kendi oyunlarınız.** PS1 oyunlarınızı evdeki başka bir bilgisayarda tutuyorsanız Mağaza'nın yerel ağ
sunucusu `abstored` onları ağınız üzerinden Mağaza'ya sunabilir; siz de onları diğer öğeler gibi kurarsınız. Herhangi
bir Linux makinesinde - bir Raspberry Pi'de, bir ev sunucusunda - çalışır ve klasörü yalnızca okur, hiç değiştirmez.
`abstored <oyun klasörü>` ile başlatın, sonra bir tarayıcıda `http://<o makine>:8124/` adresini açın: sayfa neyi
sunduğunu ve bulduğu sorunları gösterir. Mağaza'da kaynak olarak `http://<o makine>:8124/store.tsv` adresini ekleyin.
Linux ve Windows için hazır programlar Mağaza'nın sayfasında, **LAN server** sekmesinde bulunur; onu bir hizmet olarak
nasıl kuracağınızı `INSTALL-linux.md` (kaynak kodda `ext_store/server/`) anlatır. **LAN Share** (bölüm 5.2) bir
PC'deki oyunları ve diskleri böyle bir sunucuya koyar.

### 3.14 Tarama işlemcileri

Tarama işlemcileri oyunlarınızı AutoBleem onları okumadan önce hazırlar. Bir işlemci, her taramanın önce çalıştırdığı
küçük bir programdır. AutoBleem'in okumadığı bir biçimi okuduğu bir biçime çevirebilir - örneğin zip'lenmiş bir oyunu
açarak - ya da bir oyunun verisini değiştirebilir, örneğin bir çeviri yaması uygulayarak. İşlemciler bellekte
`System/Processors/<ad>/` içinde durur (Raspberry Pi'de veri bölümünde, Windows'ta veri klasöründe); birini kurmak
için klasörünü oraya açın, bir sonraki tarama onu çalıştırır.

**Unzip, AutoBleem'le birlikte gelir.** `Games/` içindeki zip'lenmiş PS1 oyunlarını tarama onları okumadan önce,
zip'lenmiş ROM'ları da birer birer açar. Atari salonu setleri zip'li kalır, çünkü atari çekirdekleri onları böyle
okur. AutoBleem güncellenince Unzip de güncellenir; onu kapattıysanız kapalı kalır.

Bir işlemci işini bir kez yapar: bir oyunla işi bittikten sonra, oyun değişmedikçe onun üzerinde yeniden çalışmaz.
Bir işlemci çalışırken sağ üstteki baloncuk ne yaptığını gösterir, bir uyarı ya da hata da altındaki satırda çıkar;
ayrıntılar günlük klasöründeki `processors.log` dosyasındadır. Bir oyunu ya da RetroArch'ı başlatmak dosyaları
değiştiren bir işlemciyi durdurur, böylece makine tamamen oyuna kalır; işi bir sonraki tarama bitirir.

İşlemcileri yönetmek için sistem menüsünü açın (**L2 + R2**) ve *Tarama işlemcileri*'ni seçin. Onları çalıştıkları
sırayla görürsünüz; PS1 oyunları için bir, ROM'lar için bir sekme vardır, aralarında L1 ve R1 ile geçersiniz. Sıra
önemlidir: dosya açan bir işlemci, açılanı yamalayan bir işlemciden önce gelmelidir.

| Düğme | Tarama işlemcilerinde |
|---|---|
| Square | Seçili işlemciyi yerinden alır; Up ve Down ile yeni yerine taşırsınız, Square onu yeniden bırakır. |
| Cross | İşlemciyi kapatır ya da yeniden açar. |
| Triangle | Bir sonraki taramada işlemcinin, daha önce işlediği oyunlar dahil, bütün oyunlara yeniden bakmasını sağlar. |
| Circle | Geri çıkar; bir şey değiştirdiyseniz bir tarama başlatır. |

Başka bir makine için derlenmiş bir işlemci listede soluk olarak kalır; orada olduğunu görürsünüz ama bu makinede
çalışmaz.

![Tarama işlemcileri](../images/en/processors.jpg)

Kendi işlemcinizi yazmak isterseniz Unzip'in sayfası, `https://github.com/autobleem2/proc_unzip`, bir işlemcinin
yapması gereken her şeyi anlatır; AutoBleem'in kaynak kodundaki `tools/proc_check.py` de sizinkini paylaşmadan önce
denetler.

<!-- pagebreak -->

## 4. Ekranlar

### 4.1 Oyun Yöneticisi

Oyun Yöneticisi, PS1 kütüphanenizi topladığınız yerdir. Artık oynamadığınız bir oyunu kaldırmak, bir oyunun
ayarlarını rafta onu aramadan açmak ya da AutoBleem'in bütün kapakları yeniden getirmesini sağlamak istediğinizde
onu kullanın. Sistem menüsünden açılır (L2 + R2, *Oyun Yöneticisi*). Tarama sürerken soluk görünür ve tarama
bitene kadar bekler.

Ekranın başlığı *Oyun yöneticisi - Oyun seçin*'dir. Solda bütün PS1 oyunlarınızı alfabetik sırayla bir ad listesi
olarak görürsünüz; sağda seçili oyunun kapağı, yayıncısı, yılı, seri numarası ve içinde durduğu klasör. Sağ üstte
sürücüde kalan boş alan yazar; böylece bir silme işleminin ne kadar yer açacağını görürsünüz. Up ve Down listede
gezer, L2 / R2 sayfa çevirir, L1 / R1 ilk ya da son oyuna atlar.

- **Cross** seçili oyunu oyun düzenleyicisinde açar - raftaki *Oyun* simgesiyle açılan düzenleyicinin aynısında
  (bölüm 3.7). Çıktığınızda listede aynı oyunun üzerine dönersiniz.
- **Square oyunu siler.** AutoBleem önce sorar, sonra oyunun bütün klasörünü kaldırır. Oyunun durum kayıtlarını ve
  hafıza kartını başka hiçbir oyun kullanmıyorsa ikinci bir soru sorar: bunlar da silinsin mi? Oyunu ileride
  kayıtlarınızla birlikte geri isteyebilirseniz hayır deyin.
- **Triangle oyunlarınızın yanında duran bütün kapak resimlerini** (PNG ya da JPEG) bir soru sorduktan sonra siler.
  Beğenmediğiniz kapaklar biriktiyse işe yarar: bir sonraki tarama kapakları yeniden kapak veritabanlarından alır.

Listenin sonunda, oyunlardan sonra *Eklenmedi* işaretli klasörler görebilirsiniz. Bunlar `Games` içinde taramanın
baktığı ama oyuna çeviremediği klasörlerdir. Birini seçtiğinizde sağ taraf onun nerede olduğunu ve neden eklenmediğini
söyler - örneğin eksik bir cue dosyası (bölüm 7). Square böyle bir klasörü bir soru sorduktan sonra siler. Bir şey
değiştirdikten sonra Circle ile çıktığınızda AutoBleem oyunları yeniden tarar.

![Oyun Yöneticisi: solda oyun listesi, sağda seçili oyunun kapağı ve bilgileri](../images/en/game-manager.jpg)

### 4.2 Donanım bilgisi

Makinenizin ne olduğunu ve neyi gördüğünü bilmek istediğinizde bakacağınız sayfa budur: bellekte ne kadar yer kaldığı,
hangi ağ adresinin olduğu, hangi ekran ve ses sürücülerini kullandığı ve hangi kumandaların bağlı olduğu. Konsol dahil
her platformda aynı sayfadır. Sistem menüsünden açılır (L2 + R2, *Donanım bilgisi*); Circle sizi sistem menüsüne geri
götürür.

Sayfa sistemi, donanımı, boş alanıyla birlikte depolamayı, ağ adreslerini, ekran ve ses sürücülerini ve bağlı
kumandaları gösterir. Her şeyi saniyede bir yeniden okur; bu yüzden sayfayı açık bırakıp bir kumanda ya da kablo
takabilir ve değişikliğin belirmesini izleyebilirsiniz. Yalnızca bilgi gösterir; ağı ya da bir kumandayı ayarlamak
için *Ağ ve Kumandalar*'ı (PSC-Bios, bölüm 6) kullanın.

Kumandalar kısmı "hangi kumanda hangi oyuncu?" sorusunu cevaplar. İlk iki kumanda *Oyuncu 1* ve *Oyuncu 2* olarak
görünür - PS1 emülatörünün onlara verdiği girişler. Bunların dışındaki kumandalar *PS1 emülatörü tarafından
kullanılmıyor* olarak görünür. RetroArch girişleri kendi ayarlarına göre dağıtır, dolayısıyla bir RetroArch oyununda
sıra farklı olabilir. Bu sayfayı her seferinde açmanız gerekmez: bir kumanda takıldığında ya da çıkarıldığında
başlatıcı hangi kumandanın artık 1. oyuncu, hangisinin 2. oyuncu olduğunu kısaca gösterir.

![Donanım bilgisi: makinenin bilgileri ve bağlı kumandalar](../images/en/hardware-info.jpg)

### 4.3 Düğme kılavuzu

Bir yerde bir düğmenin ne yaptığını unutursanız rafta **Triangle**'a basın. Düğme kılavuzu her ekranın bütün düğmelerini
tek sayfada gösterir; böylece başlatıcıdan çıkmadan bakabilirsiniz. Bir USB klavye bağlıysa ya da kullanıldıysa bir
*Klavye* sütunu her kumanda düğmesinin yanında karşılık gelen tuşu gösterir.

Kılavuz her oyun için hatırlamaya değer tek şeyi de hatırlatır: oyundan nasıl çıkılacağını. AutoBleem'e dönmek için
Select + Start'ı ya da Home'u 2 saniye basılı tutun; kısa basış bunun yerine emülatörün menüsünü açar.

![Düğme kılavuzu: her ekranın düğmeleri, yanlarında klavye tuşları](../images/en/button-guide.jpg)

### 4.4 Ekran klavyesi

AutoBleem sizden bir şey yazmanızı istediğinde - bir hafıza kartı setinin adı, bir oyunun adı, bir Wi-Fi parolası, bir
Mağaza kaynağının adresi - hep aynı ekran klavyesi çıkar; böylece yalnızca kumandayla yazabilirsiniz. Bir telefon
klavyesi gibi dizilmiştir. Harflerin yanı sıra `/ \ : ? & = % @ #` ve bir adresin ya da parolanın gerektirdiği diğer
işaretlerin bulunduğu bir sembol sayfası ile iki sayfa aksanlı harf vardır. En alt sırada Shift, sayfayı değiştiren
tuş, Space, Backspace ve Confirm bulunur.

Tuşların üzerinde yön tuşlarıyla gezinin ve imlecin altındakini yazmak için **Cross**'a basın. **Triangle** bir harf
siler, **Square** boşluk koyar. **L1** Shift'tir; iki kez basarsanız büyük harf kilidi açılır. **R1** bir sonraki tuş
sayfasına geçer, **L2 / R2** de imleci metnin içinde oynatır. **Start** yazdığınızı onaylar, **Circle** vazgeçer. Bir
USB klavye bağlıysa istediğiniz an onunla da yazabilirsiniz: Enter onaylar, Esc vazgeçer.

![Ekran klavyesi](../images/en/keyboard.jpg)

### 4.5 Sanal oyun kumandası

Uygulamalar - Apps setindeki Doom ya da Quake gibi programlar - kumandanızı kendileri okumaz. Sanal kumanda daemon'u
denen küçük bir yardımcı program gerçek kumandaları okur ve her Uygulamaya onun anlayacağı bir kumanda verir. Bu sayfa,
bu yardımcının hangi kumandaları gördüğünü ve onları nasıl okuduğunu gösterir. Bir Uygulama kumandanıza tepki
vermiyorsa ya da düğmeleri karışıksa buraya bakın. Sistem menüsünden açılır (L2 + R2, *Sanal oyun kumandası*); Circle
sizi sistem menüsüne geri götürür.

*Daemon'ın gördüğü kumandalar* altında her kumanda bir numara ve adıyla listelenir. Yanında üç şey okursunuz:
yardımcının kumandayı açıp açamadığı (*bağlı*) ya da açamadığı (*okunamıyor*); kumandanın hangi sürücü üzerinden
geldiği; ve düğme düzeninin nereden geldiği. *kumanda veritabanından* kumandanın bilindiği ve düğmelerinin olması
gereken yerde olduğu anlamına gelir; *daemon tarafından tahmin edildi* ise bilinmediği ve yardımcının elinden gelen en
iyi tahmini yaptığı anlamına gelir. Bir Uygulamada düğmeler yanlış geliyorsa sebebi büyük ihtimalle tahmin edilmiş
bir düzendir.

Yardımcı yalnızca bir Uygulama çalışırken çalışır; bu yüzden sayfa açılırken ona bir kez sorar. Sayfa açıkken bir
kumanda takarsanız yeniden sormak için **Cross**'a (*Tekrar bak*) basın. Windows'ta böyle bir yardımcı yoktur ve
sayfada *Bu sürümde yok* yazar.

![Sanal oyun kumandası: Uygulamaların yardımcısının gördüğü kumandalar](../images/en/virtual-gamepad.jpg)

<!-- pagebreak -->

## 5. PC'de

### 5.1 UpdateRoms - konsol belleğini yenilemek

Raspberry Pi'de, PC'de ya da Windows'ta başlatıcının taraması RetroArch oyunlarınızı listelere ayırır ve kapaklarını
kendisi indirir. PlayStation Classic'in kendi ağı olmadığı için bunu yapamaz. Bu işi onun yerine Windows PC'nizde
**UpdateRoms** yapar: PC'nin ağını kullanır ama her şeyi konsolun beklediği yollarla yazar; belleği geri taktığınızda
konsol açılır ve her şeyi yerinde bulur. Bir konsol belleğine RetroArch oyunu eklediğiniz ya da sildiğiniz her
seferde onu çalıştırın.

1. ROM'larınızı bellekte `RetroArch/roms/<sistem>/` altına kopyalayın (bölüm 3.10). Klasör adları RetroArch'ın
   veritabanı adları olmalıdır; sık kullanılanları kurulum programı zaten açmıştır.
2. **`UpdateRoms\UpdateRoms.exe`'yi bellekten** çalıştırın - kurulum programı onu oraya koymuştur. Hangi bellekte
   olduğunu kendisi anlar. Çalışırken ne yaptığını söyleyen bir satır, bir ilerleme çubuğu ve bir günlük görürsünüz.
   - Bellekte henüz RetroArch veritabanı yoksa önce RetroArch'ın veritabanı paketini indirir. Sonra her ROM'u onunla
     tanır; böylece veritabanının bildiği bir oyun doğru adını alır.
   - Her sistem için `RetroArch/bin/playlists/` içine konsolun yollarıyla bir oynatma listesi yazar. RetroArch'ın
     kendisinin bu listelere eklediği her şey korunur.
   - Kapağı olmayan her ROM için libretro'nun küçük resim sunucularından `RetroArch/bin/thumbnails/` içine bir kapak
     indirir.
3. Belleği güvenli şekilde çıkarın ve konsola geri takın. Set seçicinin RetroArch sekmesi artık oyunu olan her
   sistemi listeler.

İstediğiniz kadar sık çalıştırabilirsiniz: hiçbir şeyin değişmediği bir klasör atlanır, bu yüzden ikinci çalıştırma
hızlıdır. Bir şey ters giderse günlük, bellekteki `System/Logs/updateroms.log` dosyasıdır. Kart okuyucuya takılı bir
Raspberry Pi kartı da aynı şekilde, `UpdateRoms.exe <sürücü> --target rpi` ile yenilenebilir; gerçi ağı olan bir Pi bunu
kendisi yapar.

### 5.2 LAN Share - oyunlarınız ve diskleriniz ağınızdaki sunucuda

Mağaza, evinizdeki ağda duran bir sunucudan oyun kurabilir (bölüm 3.13). **LAN Share**, o sunucuyu PC'nizden dolduran
Windows programıdır: PC'nizdeki PS1 oyunlarını sunucuya koyar, PC'nin CD/DVD sürücüsündeki bir PS1 diskini okuyup onu
da oraya koyabilir. Sunucu, bir Raspberry Pi'de, bir NAS'ta ya da başka bir PC'de çalışan bir `abstored`'dur. Bir oyun
sunucuya geçtikten sonra konsoldaki, Pi'deki ya da PC'deki Mağaza onu oradan kurabilir.

`LanShare.exe`'yi Mağaza'nın sayfasından, **LAN server** sekmesinden alırsınız. Kurulacak bir şey yok: çalıştırın,
ayarlarını `%LOCALAPPDATA%\AutoBleem LAN Share\` içinde saklar.

![LAN Share penceresi: solda sunucudaki oyunlar, sağda bu PC'deki oyunlar](../images/en/lanshare.jpg)

1. **Sunucuya bağlanın.** Adresini Mağaza'daki gibi, `http://<adresi>:<port>` biçiminde girip **Connect**'e basın.
   Sunucuda zaten bulunan oyunlar ve sunucunun kendi taramasının bulduğu sorunlar solda görünür. Sunucuya oyun
   koyabilmek için LAN Share'in iki giriş yolundan birine ihtiyacı vardır:
   - **Share**, sunucunun oyun klasörünün ağınızda (Samba ile) paylaşılmış hâlidir, örneğin `\\raspberrypi\games`.
     LAN Share oyunları buraya kopyalar ve sunucudan bir tarama yapmasını ister; sunucunun kendisi klasörünü yine
     yalnızca okur.
   - **Token**, `--allow-uploads` ile başlatılmış bir sunucu içindir. Onun anahtarını girin - sunucu başlarken onu
     ekrana yazar ve `<state>/upload-token` içinde saklar. LAN Share o zaman HTTP üzerinden yükler; yarıda kalan bir
     yükleme kaldığı yerden sürer.
2. **PC'nizdeki oyunları yayımlayın.** Oyunlarınızın bulunduğu klasörü seçin (her oyun kendi klasöründe), istediklerinizi
   işaretleyin ve **Publish the ticked games**'e basın. **On the server** sütunu bir oyunun sunucuda zaten olup
   olmadığını söyler - seri numarasını, seri numarası yoksa adı karşılaştırır - ve sunucuda olan bir oyun asla iki
   kez gönderilmez. **Tick those not on the server** geri kalan hepsini sizin yerinize işaretler.
3. **Bir disk yayımlayın.** PC'nin sürücüsüne bir PS1 diski takıp **Read a disc and publish it**'e basın. LAN Share
   diskin tamamını oyunun adıyla bir `.bin` + `.cue` olarak okur. Bir LibCrypt oyununda, sürücü alt kanalı
   okuyabiliyorsa `.sbi` dosyasını da yazar. Veritabanlarını seçtiyseniz (aşağıya bakın) kopyayı bilinen sağlam
   dökümle karşılaştırır. Sonra oyunu yayımlar. Birkaç diskli bir oyun için önce **The game has more than one disc**'i
   işaretleyin: LAN Share her bir sonraki diski ister ve hepsini tek bir oyun olarak birlikte yayımlar.
4. **Oyunları sunucudan kaldırın.** Seçip **Remove from the server...**'a basın. Hiçbir şey silinmez: her oyun
   sunucunun oyunlarının yanındaki bir `.removed` klasörüne taşınır; geri taşırsanız geri gelir.

**Databases** isteğe bağlıdır. LAN Share'e AutoBleem'in kapak klasörünü (`coversU/P/J.db`) ve RetroArch'ın
`Sony - PlayStation.rdb` dosyasını gösterirseniz oyunlara ad vermek ve okuduğu bir diski denetlemek için onları
kullanır.

Hiçbir şey kopyalamak istemiyorsanız **Also share the games on this PC with the Store**'u işaretleyin (varsayılan
olarak kapalıdır): LAN Share o zaman PC'nizdeki oyun klasörünü doğrudan Mağaza'ya sunar. Bunu ilk yaptığınızda Windows
güvenlik duvarını sorar; yalnızca özel ağlara izin verin.

<!-- pagebreak -->

## 6. Konsol araçları (PlayStation Classic)

Bir PlayStation Classic belleğiyle iki araç gelir; konsolu kutudan çıktığı hâlinin ötesine taşımanıza yardım ederler.
İkisi de başlatıcının geri kalanıyla aynı görünür, onun temasını ve dilini kullanır; ikisini de kumandayla
kullanırsınız - kumanda sihirbazında konsolun öndeki düğmeleriyle de. **PSC-Bios** konsol paketiyle gelen bir
eklentidir: Hızlı menüdeki ve sistem menüsündeki *Ağ ve Kumandalar* öğesi onu açar, Eklentiler listesinde de bulunur.
**ABFlashKit** ise Apps setinde duran bir Uygulamadır.

### 6.1 PSC-Bios

PSC-Bios makineyi dünyaya bağladığınız yerdir: Wi-Fi ağınız, saat diliminiz, Bluetooth kumandalar ve AutoBleem'in
tanımadığı bir kumandanın düğme düzeni. Konsol paketiyle gelir; Raspberry Pi'de ve PC belleğinde de bulunur. Sistem
menüsünde (ya da Hızlı menüde) *Ağ ve Kumandalar* ile ya da Eklentiler listesinden açılır. Eklenti kurulu ama
kapalıysa *Ağ ve Kumandalar* öğesi soluk görünür ve yanında *kapalı - Eklentiler'den açın* yazar; üzerinde Cross'a
basarsanız Eklentiler listesi PSC-Bios'un üzerinde açılır ve onu yeniden açabilirsiniz.

İlk ekran size genel bir bakış sunar: saat ve saat dilimi, adresleriyle birlikte ağ bağdaştırıcıları (Wi-Fi, Ethernet,
Bluetooth) ve bağlı her kumanda, yanında düğme eşlemesi olup olmadığına dair bir notla. Konsolda ağ ve Bluetooth
kısımları için AutoBleem kernel'i gerekir (bölüm 6.2); Raspberry Pi'de ya da PC belleğinde sistemin kendi araçları
kullanılır. Kumanda sihirbazı her yerde çalışır.

![PSC-Bios: Ağ ve Kumandalar ana ekranı](../images/en/pscbios-main.jpg)

İlk ekrandan her bölüme tek bir düğmeyle geçersiniz:

| Düğme | Ne açar |
|---|---|
| Select | **Wi-Fi Network** sizi Wi-Fi'nize bağlar (kernel üzerinden, Pi'de ya da PC'de NetworkManager ile): ağın adını yazın ya da bir taramadan seçin, parolayı girin, sürücü modunu seçin ve *Apply / Restart Network*'e basın. Saat dilimini de burada ayarlarsınız; bağlandıktan sonra konsolun IP adresini görürsünüz. |
| Square | **Bluetooth Controllers** DualShock 4 gibi Bluetooth kumandaları arar; yeni birini eşleştirebilir ya da artık kullanmadığınızı kaldırabilirsiniz. |
| L1 | **DualShock 3 Pairing** ilk DualShock 3'ünüzü kernel'in sixaxis eklentisi üzerinden bağlar; bunun için kumandanın USB ile takılı olması gerekir. |
| R1 | **Controller Mapping** aşağıda anlatılan kumanda sihirbazını açar. |
| Triangle | **About** PSC-Bios'un ne olduğunu gösterir. |
| Circle | **Back** sizi PSC-Bios'tan çıkarıp başlatıcıya döndürür. |

**Kumanda sihirbazı.** Bir kumanda AutoBleem'de hiçbir şey yapmıyorsa ya da düğmeleri yanlış yerdeyse bunu kullanın.
Sihirbaz bağlı kumandayı gerçekte olduğu gibi - her ekseni, düğmeyi ve yön tuşunu sayılar hâlinde - ve siz bastıkça
yanan bir DualShock resmi gösterir. Denediğiniz kumandaya henüz güvenilemeyeceği için sihirbazı konsolun **öndeki
düğmeleriyle** yönetirsiniz: **RESET** bir sonraki kumandaya geçer, **OPEN** eşlemeyi başlatır, **POWER** vazgeçer ya
da çıkar. Eşleme sırasında sihirbaz düğmeleri birer birer ister: resimde yanan düğmeye basın, kumandanızda öyle bir
düğme yoksa OPEN'a basın. Kısa basış her zamanki gibi eşlenir.

Kumandadan da çıkabilirsiniz: Circle'ı 2 saniye basılı tutun - bir çubuk dolar ve alt satırda *Hold 2 s: Exit* yazar.
Kumandanın henüz bir eşlemesi yoksa herhangi bir düğmeyi 2 saniye basılı tutmak da aynı işi görür (*Hold any button
2 s: Exit*). Klavyede Esc, Space ve Enter, POWER, RESET ve OPEN'ın yerini tutar.

Sonunda yeni eşleme denemeniz için hemen kullanıma alınır; OPEN onu seçtiğiniz bir adla kaydeder. Bundan sonra
başlatıcı onu her seferinde yükler.

![PSC-Bios: kumanda eşleme sihirbazı](../images/en/pscbios-wizard.jpg)

### 6.2 ABFlashKit - AutoBleem kernel'i

AutoBleem kernel'i konsolun kendi Linux kernel'inin yerini alır ve isteğe bağlıdır. Konsoldan daha fazlasını
istiyorsanız işinize yarar: konsola çalışan bir saat verir, USB Wi-Fi ve Bluetooth adaptörlerini çalıştırır (PSC-Bios
ve Bluetooth kumandalar için) ve emülatörün devam noktaları için kullandığı ön düğme desteğini ekler. Onu kuran araç
ABFlashKit'tir. Önce konsolun yedeğini alır; konsolu Sony'nin kendi kurtarma sistemiyle fabrika hâline de
döndürebilir.

> **Bu araç konsolun flaş belleğine yazar.** Yazma yarıda kesilirse - elektrik giderse ya da bellek çekilirse -
> konsol bir daha açılmayabilir; özel bir kernel kurmak da garantiyi geçersiz kılar. Konsol kendiliğinden yeniden
> başlayana kadar elektriği kesmeyin, belleği çıkarmayın. ABFlashKit bu uyarıyla açılır: *I understand* devam eder,
> *Quit* çıkar.

![ABFlashKit'in menüsü](../images/en/abflashkit-menu.jpg)

ABFlashKit'in üç işlevi vardır:

- **Flash Kernel** kernel'i kurar. Bellekte henüz bir kurtarma yedeği yoksa önce konsolun bölümlerinin yedeğini alır
  (`LBOOT.EPB`). Yedeği ve kernel görüntüsünü denetler, kernel'i ve AutoBleem'in sistem dosyalarını yazar ve konsolu
  yeniden başlatır. *All done - when the screen goes black replace power cord* dediğinde ekranın kararmasını bekleyin,
  sonra konsolun elektrik kablosunu çekip yeniden takın.
- **Full backup** konsolun dört bölümünün hepsini `LBOOT.EPB` içine kaydeder; böylece onları sonra geri
  yükleyebilirsiniz. Zaten bir yedek varsa üzerine yazmadan önce sorar.
- **Restore Mode** fabrika yazılımına dönüş yoludur. Bellekteki yedeğin fabrika yedeği olduğunu denetler, kurtarma
  işaretini koyar ve Sony'nin kurtarma sistemine yeniden başlar; o da konsolu `LBOOT.EPB`'den geri yükler.

Her adımın altındaki bir ilerleme çubuğu ne kadar ilerlediğini gösterir. ABFlashKit, BleemSync ya da Project Eris gibi
başka bir özel yazılım çalıştıran bir konsola yazmaz: o konsolu önce fabrika hâline döndürün.

**PC'den oturum açmak.** Linux biliyorsanız ve konsolun içine bakmak istiyorsanız bir USB kablosuyla PC'den ona oturum
açabilirsiniz. Bunun için AutoBleem kernel'i gerekir; fabrika hâlindeki bir konsolda çalışmaz.

1. Konsolun micro-USB girişini bir USB kablosuyla PC'ye bağlayın. PC konsolu yeni bir ağ bağdaştırıcısı olarak görür;
   konsolun adresini PC'de o bağdaştırıcının ayarlarında bulursunuz.
2. `ssh root@<konsolun adresi>` ile oturum açın. Varsayılan parola `autobleem`'dir.

Parola yerine bir anahtar da kullanabilirsiniz. Açık anahtarınızı bellekteki `System/ssh/authorized_keys` dosyasına
koyup konsolu yeniden başlatın: bir sonraki açılışta root hesabına eklenir. Başlatıcıyı güncellemek ya da yeniden
kurmak onu silmez.

> **Varsayılan parola her konsolda aynıdır**; sizinkine kablo takabilen herkes root olarak oturum açabilir. Mümkün
> olan yerde anahtar kullanın ve varsayılan parolası değiştirilmemiş bir konsolu başkalarının erişebileceği yerde
> bırakmayın.

<!-- pagebreak -->

## 7. Bir şeyler ters giderse

Sorunların çoğunun basit bir nedeni vardır. Aşağıda her biri gördüğünüz şeyle başlar, neden olduğunu açıklar ve ne
yapmanız gerektiğini söyler. Yardım istemeniz gerekirse herkesin ilk soracağı şey günlüklerdir; bu yüzden onlarla
başlıyoruz.

**Günlükleri bulmak.** AutoBleem çalışırken günlüklerini bellekte (RAM'de) tutar, böylece USB belleğe sürekli
yazılmaz. Günlükler `System/Logs/` klasörüne - bellekte, kartta ya da veri klasöründe - yalnızca bir şey ters
gittiğinde ulaşır: başlatıcı, bir PS1 oyunu ya da RetroArch çöktüğünde günlükler `System/Logs/crash-<n>/` içine
kaydedilir (son üç çökme saklanır) ve başlatıcı geri geldiğinde bunu bir kez söyler. Çökme olmayan bir sorunun
peşindeyseniz bütün günlükleri saklayın: Seçenekler → *Tanılama* → *Günlükleri USB bellekte tut:*'u açın (bir sonraki
açılıştan itibaren geçerlidir) ya da bir PC'den boş bir `System/Logs/keep` dosyası oluşturun. *Donanım bilgisi* (bölüm
4.2) de günlüklerin nerede olduğunu gösterir; orada Square o anki günlükleri `System/Logs/saved-<n>/` içine kaydeder.

Bulacağınız dosyalar şunlardır:

| Dosya | Ne anlatır |
|---|---|
| `autobleem.log` | Başlatıcının kendisinin ne yaptığını. |
| `launch.log`, `pcsx.log` | Bir PS1 oyununun nasıl başlatıldığını ve emülatörün çalışırken neler söylediğini. |
| `retroarch.log` | RetroArch'ın çalışırken neler söylediğini. |
| `update.log` | Bir çevrimiçi güncellemenin nasıl geçtiğini; her zaman bellekte saklanır. |
| `updateroms.log` | UpdateRoms'un PC'de nasıl geçtiğini (bölüm 5); her zaman bellekte saklanır. |

**Ekranda belleği takmanızı isteyen bir resim var ya da konsol uykuya geçti.** AutoBleem belleğini bulamıyor: konsol
açıldığında bellek takılı değildi ya da çekildi. 5 dakika dolmadan onu herhangi bir USB girişine takın (en iyisi
öndekilerden biri, bölüm 2.1) ya da Power'a basın. Bellek düzgün çıkarılmadıysa AutoBleem önce onu denetler; ilerleme
çubuğunun bitmesini bekleyin.

**RetroArch *bu konsolda bulunandan daha yeni bir sistem kitaplığı gerektiriyor* diyor.** O RetroArch konsolunkinden
daha yeni bir sistem için derlenmiş, bu yüzden konsolda çalışamaz. AutoBleem'le gelen RetroArch'ı kullanın.

**Bir oyun *PSN lisansıyla korunuyor ve başlatılamıyor* diyor.** PlayStation Network'ten satın alınan oyunlar
lisanslarına kilitlidir ve AutoBleem onları çalıştıramaz. Düzeltilecek bir şey yok.

**Bir oyun rafta yok.** Genellikle klasörü taramanın beklediği gibi düzenlenmemiştir. Her oyunun kendi klasöründe
olduğundan ve bölüm 3.10'daki biçimlerden birinde olduğundan emin olun. *Oyun Yöneticisi* (bölüm 4.1) taramanın
reddettiği klasörleri oyunlardan sonra, *Eklenmedi* işaretiyle listeler ve her birinin neden reddedildiğini söyler;
Square böyle bir klasörü siler. Bir klasörü düzelttikten sonra sistem menüsündeki *Oyunları yeniden tara* taramayı
yeniden çalıştırır.

**Oyunların kapağı yok.** Ya kapak veritabanları kurulmamıştır - kurulum programını onları işaretleyerek yeniden
çalıştırın - ya da konsoldaki RetroArch oyunları için PC'de henüz UpdateRoms çalıştırılmamıştır (bölüm 5).

**Bir kumanda hiçbir şey yapmıyor ya da düğmeleri karışık.** AutoBleem o kumandanın düzenini bilmiyor. Konsolda onu
PSC-Bios'un kumanda sihirbazıyla eşleyin (bölüm 6.1). Pi'de ya da PC'de Donanım bilgisi sayfası (bölüm 4.2) sistemin
kumandadan ne gördüğünü gösterir; bu da kumandanın tanınıp tanınmadığını anlamanıza yardım eder.

**Konsolda bir oyundan sonra ekran siyah kalıyor.** Oyun bittiğinde başlatıcının görüntüsü geri gelmedi. AutoBleem
penceresini kendisi, üç kereye kadar yeniden kurar. Ekran yine de siyah kalırsa Power düğmesini basılı tutun ve
konsolu yeniden açın.

**Raspberry Pi'de** gerektiğinde başlatıcının arkasına geçebilirsiniz: `Alt+F2` ikinci konsolda bir oturum açma ekranı
getirir, SSH de ilk açılıştan beri açıktır. `sudo journalctl -u autobleem` başlatıcının hizmetinin ne yaptığını
gösterir, `sudo systemctl restart autobleem` onu yeniden başlatır. İlk açılış ağ olmadığı için tamamlanamadıysa bir
sonraki açılışta yeniden dener.

**Windows'ta** `Esc` başlatıcıdan çıkar. Veri klasörünüz kurulum sırasında seçtiğiniz klasördür (değiştirmediyseniz
`Documents\AutoBleem`); günlükler onun `System\Logs` klasöründedir.

**Çevrimiçi bir güncellemeden sonra konsol durmadan yeniden başlıyor (ext4 biçimli bellek).** Bazıları belleği FAT32
ya da exFAT yerine Linux dosya sistemi ext4 ile biçimlendirir. Bir sonraki AutoBleem sürümüne kadar, böyle bir bellekte
çevrimiçi güncelleme her dosyayı program olarak çalışmasını sağlayan izin olmadan açar. AutoBleem o zaman başlayamaz
ve konsol tekrar tekrar yeniden başlar. FAT32 ve exFAT bellekler bundan etkilenmez. Düzeltmenin iki yolu vardır.

**A yolu** için bir Linux PC gerekir. Belleği takın ve AutoBleem programlarını yeniden çalıştırılabilir yapın.
`/media/USER/STICK` yerine kendi bağlama yolunuzu yazın; son satıra yalnızca RetroArch kuruluysa ihtiyacınız var:

```
chmod +x /media/USER/STICK/Autobleem/*.sh /media/USER/STICK/Autobleem/rc/*.sh
chmod +x /media/USER/STICK/Autobleem/bin/autobleem/* /media/USER/STICK/Autobleem/bin/emu*/pcsx-ab /media/USER/STICK/Autobleem/bin/abpad/abpadd
chmod +x /media/USER/STICK/RetroArch/bin/retroarch
```

**B yolu**: en yeni AutoBleem sürümünü bölüm 2.1'deki gibi belleğe yeniden kurun. Kurulum programı için belleği
okuyabilen bir PC gerekir. Sizinkini okuyamıyorsa bellek önce biçimlendirilmelidir; bu da üzerindeki her şeyi siler -
bunu yapmadan önce oyunlarınızı başka yere kopyalayın.

> Bunun önüne geçmek için **FAT32** kullanın (fabrika hâlindeki konsol yalnızca FAT32 okur; exFAT için AutoBleem
> kernel'i gerekir, bölüm 6). Bir sonraki sürüm izinleri korur ve AutoBleem her açılışta onları onarır.

AutoBleem özgür yazılımdır (GNU GPL v3 ya da sonrası) ve hiçbir garanti olmadan gelir. Destek ve haberler için Hakkında
ekranında bağlantısı bulunan Discord sunucusuna katılın ya da https://autobleem.retromenele.pl/ adresini ziyaret edin.
