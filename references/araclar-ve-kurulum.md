# Araç seçimi, kullanım ve güvenli kurulum

## Genel kurallar

Önce bu oturumda gerçekten kullanılabilen dosya/görsel/ses yeteneklerini ve terminal erişimi varsa gerekli aracın kurulu olup olmadığını kontrol et. Aynı işi yerleşik özellik yapabiliyorsa yeni araç kurma. Araç yalnızca eksik bir yetenek için, analiz kalitesine anlamlı katkı sağlayacaksa önerilir. Bu analiz için kullanıcıdan bilgisayarına uzaktan bağlanma veya ekran kontrolü izni isteme; böyle bir erişim, standart analiz ön koşulu değildir. Dosya bu çalışma alanında görünmüyorsa kullanıcıdan dosyayı `assets/` klasörüne koymasını veya sohbete yüklemesini iste.

İndirme, kurulum, derleme, bağımlılık veya büyük model dosyası indirmeden önce kullanıcıya şu bilgileri ver ve açık onayını bekle:

- Hangi analizi mümkün kılacağı ve neden gerekli olduğu.
- Resmi kaynak ve indirilecek program/model.
- İşletim sistemine göre gereken adımlar, izinler ve yaklaşık disk/RAM ihtiyacı biliniyorsa bunlar.
- Dosyaların yerel mi kalacağı yoksa bulut servisine mi gönderileceği.
- Kurulum yapılmazsa hangi analizin yapılamayacağı.

Kurulum ancak ilgili araca açık onaydan sonra ve mevcut ortamın izin verdiği ölçüde yapılır. Kullanıcının onayı, ortamın ayrıca gösterebileceği işletim sistemi/uygulama izinlerini atlatma yetkisi vermez. İndirme sayfasındaki OS talimatlarını kullan; rastgele “codec pack”, FFmpeg'i taklit eden indirme sayfası, doğrulanmamış tek satırlık kurulum betiği veya gereksiz yönetici izni kullanma. Resmi proje sayfasının yönlendirdiği indirme kaynağını tercih et; yayımlanmışsa imza/hash doğrula. Mümkünse yönetici izni ve sistem PATH değişikliği gerektirmeyen, yalnızca bu analizde kullanılan yerel/taşınabilir kurulumu seç. Kurulum sonrasında sürümü ve gerçek işlevi doğrula. Kurulum ortamda mümkün değilse bunu açıkça söyle; bilgisayara bağlanmayı isteme, kullanıcıya resmi yönergeyi sun veya ilgili varlığı yüklemesini iste. Diğer analiz adımlarını etkilenmeyen alanlarda sürdür.

Windows App Control, Smart App Control veya kurum politikası bir aracı engellerse korumayı kapatma, dosyayı yeniden adlandırarak/başka klasöre taşıyarak atlatma ya da rastgele istisna ekleme önerme. Engelin hangi güvenlik katmanından geldiği belli değilse tam uyarı metnini ve indirme kaynağını sor. Kurum tarafından yönetilen cihazda kullanıcıyı BT yöneticisine yönlendir. Kişisel cihazda da engeli aşmaya çalışma; modelin doğrudan medya desteğini, kullanıcının sağlayacağı temsilî kareleri veya izinli başka bir yöntemi öner.

“Ücretsiz” olması lisans, gizlilik veya güvenilirlik değerlendirmesini ortadan kaldırmaz. Kullanıcı adına internet hesabına giriş yapma ve kimlik bilgisi isteme.

## Video: FFmpeg ve ffprobe

**Ne sağlar:** `ffprobe` video/ses akışları, süre, çözünürlük ve kare hızı gibi teknik bilgileri okuyabilir. FFmpeg videodan örnek kareler çıkarabilir, ses akışını ayrı dosyaya aktarabilir veya uyumlu biçime dönüştürebilir. Bu araçlar videoyu bir yapay zekâya kendi başına izletmez; görüntüleri modelin okuyabileceği karelere dönüştürür.

**Önerilen akış:**

1. Önce modelin dosyayı doğrudan destekleyip desteklemediğini ve videoya gerçekten erişip erişmediğini kontrol et.
2. Destek yoksa ve terminal erişimi varsa sistemde `ffmpeg`/`ffprobe` olup olmadığını kontrol et. Terminal erişimi yoksa aracı kurulu varsayma veya bilgisayara bağlanmayı isteme.
3. Araç mevcutsa videonun teknik bilgisini oku; kısa reklamlarda açılış, ana mesaj ve kapanış/CTA'yı temsil eden kareler seç. Daha uzun videolarda tüm sahneleri temsil edecek sınırlı örnek kullan ve örneklenen aralıkları kaydet.
4. Kareleri gerçekten görüntüle ve incele. Kare oluşturulamadıysa veya görsel yetenek yoksa görsel analiz yapıldığını söyleme.
5. Ses akışını ancak ses iş akışında FFmpeg gerekiyorsa çıkar. FFmpeg'in eksikliği video görsel incelemesini ses analizine bağlamaz.

**Kurulum kaynağı:** [FFmpeg resmi indirme sayfası](https://ffmpeg.org/download.html), [FFmpeg/ffprobe belgeleri](https://ffmpeg.org/ffprobe.html). FFmpeg resmi sayfası kaynak kodunu yayımlar ve hazır Windows yürütülebilir dosyaları için Gyan.dev ile BtbN bağlantılarını listeler; işletim sistemine göre yalnızca bu resmi sayfadaki güncel yönlendirmeyi kullan. Dosya bütünlüğü doğrulanamıyorsa çalıştırma. Mümkünse taşınabilir arşivi proje içindeki geçici/yerel araç klasörüne çıkar; PATH'i veya sistem ayarlarını değiştirme. `ffmpeg -version` ve `ffprobe -version` ile çalıştığını doğrula.

**FFmpeg yoksa karar:** Video model tarafından doğrudan incelenemiyor ve temsilî kare çıkarmak için FFmpeg gerekiyorsa, kullanıcıya ne kurulacağını ve kaynağını açıklayıp kurulum için Evet/Hayır sor. Evet denirse yalnızca mevcut terminal/kurulum yetkileri elveriyorsa devam et. Hayır denirse kullanıcıdan videonun açılış, ana mesaj ve kapanışını temsil eden birkaç ekran görüntüsünü yüklemesini iste; bunlar da yoksa yalnızca video görsel analizini U/D bırak ve diğer kanallara devam et. FFmpeg'in yokluğu tüm raporu durdurmaz.

## Ses: yerleşik ses yeteneği, whisper.cpp ve Audacity

Önce ortamın yüklenen sesi doğrudan dinleyip çözümleyebilmesini kontrol et. Yapay zekâ arayüzü sesi destekliyorsa ek yazılım gerekmeyebilir. Ses desteklenmiyorsa şu iki farklı ihtiyacı ayır:

### Konuşma içeriğini anlamak

`whisper.cpp`, uyumlu ses dosyasını yerel makinede konuşmadan metne çevirmek için kullanılabilecek açık kaynak bir seçenektir. Proje kaynağı [ggml-org/whisper.cpp](https://github.com/ggml-org/whisper.cpp); yönergeler derleme ve ayrıca model indirme gerektirebilir. Donanım ve seçilen model boyutu işlem süresi, bellek ve disk kullanımını etkiler. Türkçe içerik için Türkçeyi destekleyen çok dilli bir model seç. Önce resmi README'deki güncel gereksinimleri incele; model dosyası indirilmeden ve yazılım kurulmadan kullanıcı onayı al.

**Business Care için zorunlu bekleme noktası:** Video/ses varlığında konuşma analizi anlamlıysa, model sesi doğrudan işleyemiyorsa ve `whisper.cpp` veya Türkçe modeli eksikse, `Talimatlar.md` içindeki Evet/Hayır sorusunu sor ve kullanıcı yanıt verene kadar raporlamaya geçme. Evet yanıtı, önceden açıklanan Whisper kurulumu/model indirmesi ve ses çıkarma için gerekiyorsa FFmpeg bağımlılığına onaydır; ortamın erişim/kurulum izinlerini atlatmaz. Evet denmesine rağmen kurulum yapılamıyorsa sebebini açıkla, ses analizini atlama seçeneğini tekrar sun ve onay gelmeden bu kısmı atlanmış sayma. Hayır yanıtında yalnızca ses transkripsiyonunu atla; görsel video analizini ve diğer kanalları sürdürebilirsin. Ses olmadığı veya konuşma analizi gerekmiyorsa bu bekleme noktasını kullanma.

Whisper videoyu/sesi “dinleyip yorumlayan” bir pazarlama uzmanı değildir; konuşma içeriğini metne dönüştürür. Transkript otomatik tahmindir; özellikle Türkçe özel isimler, düşük ses, müzik altındaki konuşma ve reklam iddialarında metni mümkünse orijinal sesle kontrol et. Transkript, tonlama, telaffuz, ses seviyesi dengesi veya müzik kalitesini ölçmez.

### Dinleme ve sesin niteliğini incelemek

Modelin sesi dinleme yeteneği yoksa konuşma tonu, anlaşılabilirlik, müzik/efekt dengesi veya ses miksine ilişkin kesin pazarlama yorumu yapma. Kullanıcı manuel bir ses düzenleyici istiyorsa resmi kaynaktan edinilebilen [Audacity](https://www.audacityteam.org/download/) dalga biçimi ve spektrogram üzerinden temel incelemeye yardımcı olabilir; fakat görsel dalga/spektrum tek başına “iyi reklam sesi” hükmü vermez. Bu da kullanıcı bilgisayarında ayrıca kurulması gereken bir masaüstü yazılımıdır; onay al.

## Web sitesi: PageSpeed Insights ve Lighthouse

### PageSpeed Insights — varsayılan

[PageSpeed Insights](https://pagespeed.web.dev/) web arayüzü ücretsizdir, yerel kurulum istemez. Ana sayfayı mobil ve masaüstü test et; e-ticarette erişilebilen ürün veya sepet sayfası için de ölçüm al. URL, cihaz ve tarihi raporla. PSI Lighthouse laboratuvar testini ve varsa Chrome User Experience Report (CrUX) alan verisini ayırır. Saha verisi yoksa laboratuvar sonucu gerçek kullanıcı deneyimi değildir. Tek test değişebilir ve puan satış/dönüşüm metriği değildir. [Google'ın PSI açıklaması](https://developers.google.com/speed/docs/insights/v5/about).

### Lighthouse — isteğe bağlı ek inceleme

Lighthouse performans, erişilebilirlik, en iyi uygulamalar ve SEO denetimleri verebilir. Önce Chrome DevTools'taki hazır Lighthouse yolunu tercih et; bu masaüstü testinde ayrıca CLI kurulumunu gerektirmez. Otomatik veya tekrarlı yerel denetim gerekiyorsa [resmi Chrome for Developers belgelerini](https://developer.chrome.com/docs/lighthouse) takip ederek CLI seçeneğini değerlendir. Node.js/npm veya yeni bağımlılık kurmadan önce kullanıcı onayı al. Lighthouse bulguları otomatik kontrol ipuçlarıdır; manuel tasarım ve pazarlama değerlendirmesinin yerine geçmez.

Sepet/ödeme akışını gözle incele; gerçek sipariş verme, ödeme gönderme veya kullanıcı hesabı oluşturma.

## Meta Pixel: web sitesi ölçüm kurulumu kontrolü

Web sitesi olan her işletmede, aktif Meta reklamı verip vermediğinden bağımsız olarak tarayıcı Pixel'ini kontrol et. Meta Pixel tarayıcı üzerinden web olayları gönderir; Conversions API ise olayları sunucudan gönderebilir. Bu nedenle herkese açık web sitesi kontrolü tarayıcı Pixel'ini doğrulayabilir, ama sunucu tarafı CAPI'yi kanıtlayamaz. Meta'nın [Pixel ve Conversions API açıklaması](https://developers.facebook.com/docs/facebook-business-extension/fbe/guides/pixel-events).

### Varsayılan salt-okunur doğrulama

1. Web sayfasını incelemeden önce cookie/consent ekranı varsa mevcut seçimi not et; pazarlama çerezlerini otomatik kabul etme veya reddetme.
2. Sayfa kaynağında veya erişilebilir çalışma zamanı bilgilerinde Meta Pixel kurulum izlerini ara. Kod bulunması tek başına çalıştığını kanıtlamaz; GTM veya başka etiket yöneticisi Pixel'i sonradan yükleyebilir.
3. Tarayıcı geliştirici araçları güvenli biçimde kullanılabiliyorsa Network/ağ panelinde Meta Pixel'in yüklenip yüklenmediğini ve `PageView` olayının gönderilip gönderilmediğini gözle. Ad blocker, tarayıcı gizlilik koruması, consent tercihi veya bölgesel kısıtlar sonucu etkileyebilir.
4. Kullanıcı onayı olmadan consent seçimini değiştirme. Consent sonrası test gerekiyorsa kullanıcıya, sayfayı açmanın işletmenin analitiğinde bir `PageView` olarak sayılabileceğini bildir ve onay al. Testte kişisel bilgi girme; form, randevu, sepete ekleme, ödeme veya satın alma olayı tetikleme.
5. Bir Pixel ve başarılı `PageView` gözlemlenirse “tarayıcı Pixel'i ve PageView doğrulandı” yaz. Kod bulunup olay gözlemlenemediğinde “kod bulundu, olay doğrulanamadı” yaz. Hiç bulunmadığında “bu tarayıcı testinde Pixel tespit edilmedi” de; GTM/consent/CAPI veya test kısıtlarını belirt.
6. Meta Events Manager içindeki Test Events, sunucu olayları, pixel sahipliği veya dönüşüm olaylarının tam doğruluğu için kullanıcının yetkili hesabı gerekir. Şifre/kod isteme. Gerekirse kullanıcının paylaşacağı, kişisel verileri kapatılmış ekran görüntüsü veya olay durumu özetiyle devam et.

### Meta Ads Data Advisor uzantısı

[Meta Ads Data Advisor (eski Meta Pixel Helper)](https://developers.facebook.com/documentation/meta-pixel/support/meta-ads-data-advisor) Pixel ve olayları tarayıcıda inceleyebilir. Güncel uzantı Google Chrome/Edge'de çalışır; tüm web sitelerindeki verileri okuma/değiştirme ve sayfa hata ayıklama izinleri isteyebilir, ayrıca otomatik kurulum/düzeltme akışları sunar. Bu yüzden varsayılan Business Care akışında uzantıyı yükleme veya bu otomasyonları başlatma. Kullanıcı uzantıyı zaten kurmuşsa yalnızca görüntülenen tanılama/olayları oku; “fix/setup” eylemi seçme. Uzantı kurulumu özellikle istenirse izin kapsamını önceden açıkla ve kullanıcı onayı al.

### Meta Pixel kriterinde puanlama

`references/puanlama-olcutleri.md` içindeki %10 site ölçüm kriterini uygula. Pixel görünmüyor diye sunucu tarafı ölçümün de olmadığı sonucuna atlama. Test yapılamadıysa U/D puanla. E-ticaret/lead/randevu dönüşüm olaylarını kamusal sitede işlem tamamlayarak test etme.

## Rapor görselleştirme

Rapor dili ve görsel düzen için `references/rapor-dili-ve-grafik-tasarimi.md` standardını uygula. Dosya çıktısı üretilebiliyorsa Markdown raporuna ek olarak standarttaki tek dosyalı HTML arayüzünü üret. HTML içinde harici kütüphane kurmadan CSS/SVG ile modern, anlaşılır puan kartları ve karşılaştırmalı çubuk grafikler hazırla. Her grafikte puanlanan ölçüt sayısı, U/D kapsamı ve puanın gerçek performans metriği olmadığı belirtilmeli. Farklı kapsamları yanıltıcı biçimde tek grafikte kıyaslama; gözlem cümlelerine sahte sayı verme.

Süreç/müşteri yolculuğu diyagramı için görüntülenecek ortam destekliyorsa [Mermaid](https://mermaid.js.org/intro/getting-started) metin tabanlı diyagramı kullanılabilir; çoğu Markdown ortamında ayrıca kurulum gerekmez, fakat her okuyucu Mermaid'i render etmez. Destek yoksa düz metin/Markdown kullan.

PowerPoint/PDF çıktısı özellikle istenirse bu ayrı çıktı türüdür. Gerekli kütüphane veya uygulama ortamda yoksa önce gerekli kurulumu ve alternatif HTML çıktısını açıkla; onay olmadan paket kurma. Grafik ve slaytları yalnızca gerçekten ölçülmüş veya açıkça rubrik puanı olarak tanımlanmış verilerle üret.

## Kaynak kontrolü ve raporlama

Bir aracı kullandığını raporda ancak gerçekten çalıştırıp çıktısını incelediysen söyle. Araç çıktısının bağlantısını, tarihi, URL/cihaz/model gibi gerekli kapsam bilgilerini kaydet. Kurulum mümkün olmadıysa veya kullanıcı onay vermediyse “araç çalıştırılmadı” de; sonucu tahmin etme.
