# Erişim ve platform kısıtları

Bu dosya, herkese açık dijital varlık incelemesinde doğrulanması gereken sınırları tanımlar. Platformların erişim yöntemleri zamanla değişebileceği için işlem sırasında mevcut arayüz ve resmi kaynaklar esas alınmalıdır.

- Bir bağlantı açılmıyorsa, giriş istiyorsa, coğrafi olarak kısıtlıysa veya içerik yüklenmiyorsa bunu raporla; başka bir hesaba girmeye veya korumaları aşmaya çalışma.
- Instagram biyografisi, hikâye sabitleri ve bazı içerikler oturum, uygulama veya hesap görünürlüğü gerektirebilir. Görülmeyen içeriği tahmin etme.
- Facebook sayfaları, yorumlar veya paylaşımlar bölge, oturum ve sayfa ayarlarına göre farklı görünebilir. Erişim kapsamını yaz.
- Google İşletme Profili herkese açık temel bilgileri gösterebilir; performans istatistikleri ve yönetim araçları profil sahibinin yetkili erişimini gerektirebilir. Bu projede parola talep edilmez.
- Google Ads Transparency Center ve Meta Reklam Kütüphanesi herkese açık reklam örneklerini aramaya yarar; bunlar reklam hesabının performans raporu değildir. İsim veya alan adıyla eşleşme bulunamaması reklam verilmediğini kesinleştirmez. Reklamverenin işletmeye ait olduğu doğrulanamıyorsa kreatifi atfetme.
- Meta, reklamların ilk gösteriminden veya düzenlenmesinden sonra kütüphanede görünmesi/güncellenmesinin 24 saate kadar sürebileceğini bildirir. İnceleme tarihini ve olası gecikmeyi not et.
- Google PageSpeed Insights'ta Lighthouse laboratuvar verisi ile CrUX saha verisini ayır. Saha verisi yeterli kullanıcı verisi yoksa bulunmayabilir; laboratuvar puanı gerçek ziyaretçi ölçümü değildir.
- Instagram ve Facebook içerik incelemesi en son 15 gönderiyle sınırlandırılır. Bu örneklem tüm hesabı veya geçmiş performansı temsil etmeyebilir.
- Son 15 gönderide video bulunmaması tek başına ciddi performans kaybını kanıtlamaz. Format, reklam hedefi ve kreatif kalitesiyle birlikte yorumlanır.
- SSS'nin yokluğu, misafir ödemenin olmaması veya insan yüzü kullanılan video bulunmaması da her işletme için otomatik olumsuzluk değildir; iş modeline göre değerlendirilir.
- FFmpeg/ffprobe teknik bilgiyi ve örnek kareleri çıkarmaya yarar; yapay zekânın videonun her karesini gördüğü anlamına gelmez. Yalnızca oluşturulup gerçekten görüntülenen örnek kareleri incele.
- Business Care analizi için bilgisayara uzaktan bağlanma/ekran kontrolü standart gereksinim değildir. Yalnızca bu oturumda sunulan dosya, terminal ve tarayıcı yeteneklerini kullan. Dosyaya erişilemiyorsa kullanıcıdan `assets/` klasörüne koymasını veya sohbete yüklemesini iste; erişilemeyen içeriği incelemiş gibi yazma.
- FFmpeg yokluğu bütün analizi durdurmaz. Yerleşik video inceleme yoksa ve kare çıkarmak için FFmpeg gerekiyorsa kurulum için kullanıcıdan açık onay al; onay/kurulum yoksa kullanıcıdan temsilî kareler iste veya sadece video görsel bölümünü U/D bırak.
- FFmpeg indirmesinde yalnızca [resmi FFmpeg indirme sayfasındaki](https://ffmpeg.org/download.html) işletim sistemi yönlendirmelerini kullan. Resmi sayfa hazır Windows yapıları için Gyan.dev ve BtbN bağlantılarını listeler. Rastgele paket/ayna, codec paketi veya doğrulanmamış kurulum betiği kullanma; doğrulanabilir imza/hash varsa doğrula. Mümkünse taşınabilir/yerel kullan, yönetici izni veya sistem PATH değişikliği gerektirme.
- Windows App Control/Smart App Control veya kurum ilkesi FFmpeg'i engellerse güvenlik özelliğini kapatma ve engeli başka klasör/isim/istisna ile aşmaya çalışma. Uyarının kaynağını belirsizse kullanıcıdan tam metin veya ekran görüntüsüyle doğrula; yönetilen cihazda BT yöneticisine yönlendir. Analizi doğrudan video desteği, kullanıcıdan temsilî kare isteme veya ilgili medya bölümünü U/D bırakma yoluyla sürdür.
- whisper.cpp otomatik transkript üretir; bu transkript otomatik doğrulanmış değildir. Ses tonu, miks veya müzik kalitesini transkriptten çıkarma. Model sesi doğrudan dinleyemiyorsa bu alanı değerlendirilemedi olarak işaretle.
- PageSpeed/Lighthouse puanları ve otomatik uyarılar tek başına pazarlama başarısı ya da dönüşüm kanıtı değildir.
- Meta Pixel'in sayfa kaynağında bulunmaması, GTM/consent sonrası yükleme, tarayıcı engelleri veya sunucu tarafı Conversions API ihtimali nedeniyle tek başına işletmede hiçbir Meta ölçümü olmadığını kanıtlamaz. “Tarayıcı Pixel'i tespit edilmedi” ile “Meta ölçümü hiç yok” ifadelerini ayır.
- Meta Pixel doğrulama ziyareti, consent verilmişse işletme analitiğinde PageView olarak görünebilir. Kullanıcıya önceden bildir; consent'i değiştirme ve test için form/lead/sepet/satın alma işlemi yapma.
- Meta Events Manager/Test Events veya sunucu tarafı CAPI doğrulaması işletmenin yetkili erişimini gerektirebilir. Parola/kod isteme; hassas bilgileri kapatılmış ekran görüntüsü veya olay özeti iste.
- Meta Ads Data Advisor (eski Pixel Helper) uzantısı bütün web sitelerinde okuma/değiştirme izni isteyebilir ve otomatik kurulum/düzeltme yapabilir. Varsayılan olarak kurma; zaten varsa yalnızca tanılama sonuçlarını oku ve kurulum/düzeltme akışını başlatma.
- Aktif Google veya Instagram reklamı olmadığını söyleyen işletmeye rekabet riski uyarısı ver; bu uyarı genel puanı düşürmez ve müşteri kaybını kanıtlamaz. Rakiplerin kütüphanede görünmesi yalnızca aktif reklam örneğine kanıttır, başarı veya pazar payına değil.
- Grafikler yalnızca gerçek ölçüm veya tanımı açık rubrik puanlarından türetilir. Rubrik puanını gerçek reklam/site performansı gibi sunma; kıyaslamada U/D alanlarını ve kapsam farkını göster.
- Web sitesi incelemesi, tek başına ziyaretçi davranışı, satış dönüşümü veya arama sırası verisi sağlamaz.
- Sosyal platformların şartlarını, erişim kısıtlarını veya robots/erişim kontrollerini atlatma. Kullanıcı adına otomatik etkileşim, paylaşım veya değişiklik yapma.
- Araç veya kurulum önerilecekse resmi proje/üretici kaynağını kullan. İndirilen dosyayı çalıştırma veya sistem ayarlarını değiştirme adımını kullanıcıya açıkça anlat; otomatik kurulum varsayma.
- Analiz zamanı, açılabilen bağlantılar, okunabilen içerik ve başarısız erişim denemeleri raporun kapsam notuna girer.
