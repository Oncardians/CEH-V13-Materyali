# Bilgi Güvenliğine Genel Bakış (Information Security Overview)

## Bilgi Güvenliği (Information Security)

* Bilgiyi ve bilgi sistemlerini koruma sürecidir.
* Bilgiyi korumak amacıyla gerçekleştirilen süreç ve faaliyetler bütününü tanımlar.
* Temel amacı, yetkisiz kullanıcıların bilgiyi veya hizmetleri çalmasını ve kötüye kullanmasını önlemektir.
  * Hassas bilgilerin yanlış ellere geçmesi durumunda şu alanlarda büyük kayıplar yaşanabilir:
    * Finansal varlıklar, marka itibarı ve müşteri güveni.

---

## Temel Kavramlar (Essential Terms)

### Hack Değeri (Hack Value)

* Saldırganların bir hedefin saldırıya değer veya ilgi çekici olup olmadığına dair yaptığı değerlendirmedir.
* **Yüksek hack değeri örnekleri:**
  * Maddi kazanç sağlayabileceği için kişilerin kredi kartı bilgilerine erişmek.
  * Zorlu bir görevin başarılabileceğini kanıtlamak amacıyla kişilerin isim listelerine erişmek.

### Zafiyet (Vulnerability)

* Sistemi tehlikeye atabilecek ve olası bir saldırı için kullanılabilecek zayıflıktır.
* **Örnekler:**
  * **Politika eksiklikleri:** Örneğin, personelin şirket dizüstü bilgisayarlarına USB bellek takıp takamayacağını düzenleyen kuralların olmaması.
  * **Tasarım/uygulama hataları:** Örneğin, Linux, macOS ve Windows sistemlerinin, kendisini klavye olarak tanıtan ve bilgisayarda yüksek yetki elde eden kötü amaçlı bir USB belleğe (BadUSB) karşı savunmasız olması.

### İstismar (Exploit)

* Tespit edilen zafiyetler üzerinden sisteme sızma eylemidir.
* Aynı zamanda belirlenen zafiyetlerden faydalanmayı sağlayan yazılımları veya kod parçacıklarını ifade eder.
* **Örnek:** Kötü amaçlı bir USB cihazını hedef sisteme bağlamak.

### Yük (Payload)

* [Zararlı yazılımın](../07-zararli-yazilimlar/zararli-yazilimlara-genel-bakis.md.txt) veya istismar (exploit) kodunun asıl zararlı işlevi yerine getiren parçasıdır.
* **Kullanım amaçları:**
  * Kurbanın makinesinde arka kapı (**backdoor**) oluşturmak.
  * Dosyalara zarar vermek veya silmek.
  * Veri sızdırmak veya değiştirmek.
  * Bilgisayarın kontrolünü ele geçirmek.
* **Örnek:** Kötü amaçlı bir USB'nin sisteme yüklediği bir tuş kaydedici (**keylogger**) veya Uzaktan Yönetim Aracı (**RAT** - Remote Administration Tool).

### Sıfırıncı Gün Saldırısı (Zero-Day Attack)

* Diğer adları: ***zero-day attack*** • ***0-day attack*** • ***0 day attack***
* Henüz güvenlik yaması (**patch**) yayınlanmamış, önceden bilinmeyen zafiyetlerin istismar edilmesidir.
* **Sıfırıncı Gün Zafiyeti (Zero-Day Vulnerability):**
  * Yazılımda bulunan ve şu iki durumdan birine uyan güvenlik açığıdır:
    * Zafiyeti gidermekle yükümlü tarafça (örneğin üretici/vendor) henüz bilinmemektedir.
    * Bilinmektedir ancak henüz bir yaması geliştirilmemiştir.
  * Hedefli saldırılar (**targeted attacks**) sıklıkla zero-day zafiyetlerini kullanır.
  * ❗ Bir zafiyet kamuya açıklandıktan ve yaması yayınlandıktan sonra artık "zero-day" olarak adlandırılmaz.
* **Sıfırıncı Gün İstismarı (Zero-Day Exploit):**
  * Zero-day zafiyetlerinden faydalanma eylemidir ve genellikle zararlı yazılımlar aracılığıyla gerçekleştirilir.
* **Süreç Akışı (Flow):**
  1. Saldırgan zafiyeti keşfeder.
  2. Saldırgan zafiyeti istismar eder.
  3. Saldırı gerçekleşir (bu aşamaya **Day Zero** denir).
  4. Üretici firma (vendor) zafiyetten haberdar olur.
  5. Yama (patch) oluşturulur.
     * *Not:* Yazılım eski ise veya desteği sona ermişse üretici yama yayınlamayabilir.
  6. Yama sistemlere uygulanır.
     * ❗ Bazen yamalar kullanıcılar tarafından uygulanmaz! (Örneğin; internet servis sağlayıcıları kurulumdan sonra genellikle yapılandırma güncellemesi yapmadığı için ev yönlendiricilerinde/router yıllardır bilinen zafiyetler kalabilir.)
     * 💡 Yamanın oluşturulması ile sistemlere uygulanması arasındaki zaman dilimi, kötü niyetli hackerlar tarafından maksimum düzeyde kullanılır. Kurumların yama uygulamada yavaş kalması ciddi zararlara yol açar.
* **Zafiyet Penceresi (Window of Vulnerability - WOV):**
  * Bir zafiyetin keşfedilmesinden, savunmasız sistemlerin çoğunun yamalanmasına kadar geçen süredir.
  * Genellikle gün cinsinden ölçülür (örneğin 28 gün).
* **Örnekler:** [Spectre](../06-sistem-hackleme/yetki-yukseltme.md.txt) ve [Meltdown](../06-sistem-hackleme/yetki-yukseltme.md.txt)
  * AMD ve Intel işlemcilerindeki donanım tabanlı zafiyetlerdir.
  * Sistemde yetki yükseltmek (**privilege escalation**) için istismar edilebilirler.
  * Günümüzde hala varlıklarını sürdürseler de yamaları yayınlandığı için artık zero-day değillerdir; tüm bulut sağlayıcılarını etkilemiş ve donanım yazılımı (firmware) güncellemeleri nedeniyle gecikmelere yol açmışlardır.

### Zincirleme Saldırı (Daisy Chaining)

* Saldırganların bir ağa veya cihaza erişim sağladıktan sonra, bu erişimi basamak olarak kullanarak diğer ağlara ve cihazlara sıçradığı saldırı yöntemidir.
* **Aşamaları:**
  1. Saldırganlar ağınızdaki bir cihaza (örneğin akıllı saat, akıllı buzdolabı veya kişisel bilgisayar) erişim sağlar.
  2. Bu cihaz üzerinden ağdaki bir sonraki cihaza, oradan da diğerlerine geçerek ilerler.
  3. Nihayetinde saldırgan tüm ağın kontrolünü ele geçirebilir.
* 🤗 **Gerçek Hayat Senaryosu (Banka veya Kurum Hackleme Örneği):**
  1. Kurumda en yüksek erişim yetkisine sahip kişi hedef seçilir.
  2. Saldırı vektörü (**attack vector**) olarak bu kişinin ev yönlendiricisi (router) hacklenir.
     * Kurumsal ağlarda güvenlik duvarları, IT ekipleri ve sıkı politikalar varken; ev router'ları nadiren güncellenir, zafiyetlerle doludur ve genellikle küçültülmüş bir Linux işletim sistemi çalıştırır.
     * **Saldırı Vektörü (Attack Vector):** Bir hacker'ın hedef sisteme erişmek veya sızmak için kullandığı yöntem veya yoldur.
  3. Router'a bağlı cihazlar taranır.
     * İletişim şifreli olsa bile kullanılan portlar, URL'ler ve IP adresleri her zaman görülebilir (kişinin bilgisayarı, eşinin bilgisayarı, akıllı TV, cep telefonları vb.).
  4. Farklı saldırı vektörleri uygulanır:
     * DNS ayarları değiştirilerek saldırgan kendi sunucusunu DNS olarak atar.
     * Hedef bilgisayar **DMZ** (arındırılmış bölge) içine alınarak dış dünyadan erişime açık hale getirilir.
     * Cihazların işletim sistemlerine yönelik oltalama (**phishing**) veya exploit saldırıları düzenlenir.
     * Sistemlerden birine (örneğin bir süre sonra güncelleme almayan bir Android telefona) sızılır. Cihazların aşırı ısınma gibi tasarım sınırlarını aşmasıyla oluşan donanım hataları bile [Bitsquatting](https://en.wikipedia.org/wiki/Bitsquatting) gibi istismar edilebilir yazılım saldırılarına yol açabilir.
  5. **Sonuç:** Banka hesaplarına ve kredi kartı bilgilerine erişilir; enfekte edilen mobil cihaz kurumsal banka ağına bağlandığında saldırgan banka içindeki diğer sistemlere sıçrar.

### İfşa Etme (Doxing)

* Bir kişinin kişisel olarak tanımlanabilir bilgilerini (**PII** - Personally Identifiable Information) kötü niyetli amaçlarla bulma ve kamuya açık şekilde yayınlama eylemidir.
* **Örnekler:** Bireylerin tam adları, e-posta adresleri, ev adresleri veya bir kurumun gizli verilerinin sızdırılması.
* **Aşamaları:**
  1. Kişi veya kurum hakkında özel ve değerli bilgiler (fotoğraflar, kimlik numaraları, sosyal medya hesapları, adresler vb.) toplanır ve sosyal medya üzerinden hedef profili çıkarılır.
  2. Toplanan bilgiler kimlik hırsızlığı, finansal dolandırıcılık veya hedefi istemediği bir şeyi yapmaya zorlama (şantaj) amacıyla kötüye kullanılır.

### Bot

* İngilizce "robot" kelimesinin kısaltmasıdır.
* Önceden tanımlanmış görevleri otomatik olarak yerine getirmek üzere uzaktan kontrol edilebilen yazılımdır.
* Saldırganlar tarafından virüs bulaştırılmış (enfekte) makineleri kötü amaçlarla yönetmek için kullanılır.
* **Kullanım Senaryoları:**
  * Ele geçirilen bilgisayarı kullanarak diğer sistemlere saldırılar düzenlemek.
  * Çok sayıda makineye bulaşarak zombi bilgisayar ağları (**botnet**) oluşturmak.


