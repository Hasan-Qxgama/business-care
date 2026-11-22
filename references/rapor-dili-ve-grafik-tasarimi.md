# Rapor anlatımı ve grafik tasarım standardı

Bu standart, Business Care raporlarını uzman değerlendirmesi taşıyan ama işletme sahibinin ilk okumada anlayacağı sadelikte tutar.

## Anlatım dili

- Türkçe, doğrudan ve profesyonel yaz. Uzman özgüveni göster; kesin olmayan iddiada kesin konuşma.
- Önce en önemli sonucu söyle, sonra kısa kanıtı ve öneriyi ver.
- Cümleleri kısa tut; her paragraf tek bir ana fikir taşısın. Gereksiz pazarlama jargonu, İngilizce kısaltma ve uzun açıklama kullanma.
- Teknik terim gerekliyse ilk kullanımda Türkçe karşılığını veya bir cümlelik açıklamasını ekle. Örneğin “LCP (ana içeriğin ekranda görünme süresi)”. Sonraki kullanımlarda kısaltma yeterli.
- “Dönüşüm”, “piksel”, “farkındalık aşaması” gibi pazarlama kavramlarını işletme sahibinin anlayacağı örnekle açıkla; teknik terimleri vitrin dili olarak kullanma.
- Her bulguyu şu sırada yaz: **Ne gördük? → İşletme için neden önemli? → Ne yapılmalı?** Bir bulguyu tek paragraf veya kısa kartta anlat.
- Genel klişelerden kaçın. “Daha iyi içerik üretin” yerine içerik türünü/alanını ve yapılacak adımı belirt.
- Sonuçları, satış veya müşteri kaybı gibi ölçülmemiş gerçeklere dönüştürme. Gözlem, çıkarım ve belirsizliği ayrı tut.
- Yönetici özetinde en önemli 3 bulgu ve ilk 3 eylem yeterlidir. Aynı öneriyi raporun birçok yerinde tekrarlama.

## Rapor çıktısı

Mümkün olduğunda raporu iki dosya olarak üret: okunabilir ve yazdırılabilir `performans-raporu.md` ile görsel özeti gösteren bağımsız `performans-raporu.html`. HTML; tek dosya, mobil uyumlu, çevrimdışı açılabilir ve harici JavaScript/kütüphane yüklemeden çalışmalıdır. Sadece sohbet yanıtı verilebiliyorsa aynı görsel hiyerarşiyi Markdown başlıkları, kısa puan satırları ve tablolarla taklit et.

## Görsel arayüz hiyerarşisi

1. **Üst başlık:** Business Care etiketi, işletme adı, sektör ve analiz tarihi.
2. **Genel görünüm kartı:** Genel puan varsa büyükçe `0–100` puanı, kısa seviye etiketi ve yanında ondan ayrı **kapsam yüzdesi**. Puan olmayan durumda “Yeterli veri yok” göster; sayı üretme.
3. **Öncelik kartları:** En fazla üç P1/P2 öneri; her kartta kısa başlık, kanıt/etki özeti ve tek uygulanabilir ilk adım.
4. **Kanal puanları:** Instagram, Facebook, Google profili ve web sitesi için aynı ölçekli yatay çubuklar. Her satırda `puan / 100`, kapsam yüzdesi ve durum metni yer almalı. U/D ve U/G kanallarında puan çubuğu yerine açık durum etiketi göster.
5. **Kanıtlı ayrıntılar:** Kanal notları, PageSpeed sonuçları, Meta Pixel durumu ve reklam kütüphanesi bulguları kendi kısa bölümlerinde.
6. **Kapsam ve sınırlar:** Erişilemeyen veriler, incelenen son 15 gönderi sınırı, PageSpeed test tipi ve özel metriklerin mevcut olup olmadığı.
7. **Kapanış CTA'sı:** Rapor şablonundaki sabit “Bir Uzmanla Birlikte Eksikleri Düzelt.” bloğu.

## Grafik kuralları

- Grafik yalnızca gerçek ölçümden veya tanımı açık rubrik puanından üretilir. Gözlemsel bulgulara sayı uydurma.
- Kanal puanı ile kapsamı ayrı göster; 70/100 puan ile %70 kapsam aynı şey değildir.
- Bütün kanal çubuklarında aynı 0–100 eksenini kullan. Kırpılmış eksen veya karşılaştırmayı abartan görsel kullanma.
- U/D, U/G ve “reklam vermiyor” durumlarını sıfır puan gibi çizme. Durum etiketlerini metinle de göster.
- Renk tek başına anlam taşımasın. Her durumu sözcük, ikon veya desenle destekle; renk körlüğü ve kontrastı gözet.
- Basit puan karşılaştırmasında yatay çubuk kullan; radar/spider chart, gösterge kadranı ve gereksiz pasta grafiği kullanma.
- Her grafiğe kısa başlık, bir cümlelik açıklama, birim, ölçek ve gerekiyorsa tarih/örneklem ekle.
- Tasarım modern ve ferah olsun: net başlık hiyerarşisi, tutarlı boşluk, okunabilir satır uzunluğu, sınırlı renk paleti. İşletmenin sitesindeki marka renkleri gerçekten görülebiliyorsa küçük vurgu olarak kullan; okunabilirliği düşürüyorsa kullanma.
- Renk başlangıç paleti: koyu lacivert `#16324F`, teal `#1F7A72`, sıcak amber `#E7A94B`, kırık beyaz `#F6F8FA`, metin `#243447`. Kontrastı ve metin okunabilirliğini koru; başarıyı yalnızca yeşil, sorunu yalnızca kırmızıyla anlatma.
- Mobilde tek sütuna düş, puan etiketlerini görünür tut ve yatay taşma oluşturma. Yazdırmada arka plan gerektirmeyen açık düzen kullan.

## HTML uygulama sınırları

- CSS ve SVG'yi HTML içine göm. Grafik için dışarıdan paket, CDN, font, izleme pikseli veya uzak görsel çağırma.
- Anlamlı puan/kapsam verisini HTML içindeki metinle de göster; ekran okuyucu ve yazdırma çıktısı grafiği kaybetmesin.
- İçeriği doğrudan HTML'e aktarırken web sayfasından alınmış metni kod gibi çalıştırma; kullanıcıya ait web metnini HTML olarak escape et.
- İçerik yoksa kartı gizle veya “incelenmedi” yaz. Boş grafik, varsayılan `0` puan ya da örnek veri bırakma.

Bu görsel standart raporun sunum biçimini düzenler; puanlama ağırlıklarını değiştirmez. Puanlama için `references/puanlama-olcutleri.md` dosyası geçerlidir.
