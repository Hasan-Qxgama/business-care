---
name: business-care-audit
description: Bir işletmenin Instagram, Facebook, Google İşletme Profili, web sitesi ve sağlanan reklam varlıklarını sektöre duyarlı biçimde inceleyip kanıta dayalı dijital varlık ve pazarlama görünürlüğü raporu hazırlar. İşletme dijital varlıklarını denetleme, güçlü ve eksik yönleri bulma veya pazarlama iyileştirmeleri istemlerinde kullan.
---

# Business Care denetim becerisi

1. `Talimatlar.md` içindeki on başlangıç sorusunu ve iş akışını sırayla uygula.
2. `references/puanlama-olcutleri.md` içindeki Business Care v0.1 modelini aynen uygula. Sektör arketipini gerekçelendir; uygun değil/U/D ölçütlerini kurala göre ayır; ağırlıkları değiştirme.
3. Instagram ve Facebook'ta tüm içeriği değil en yeni 15 gönderiyi incele. Google İşletme Profili ve web sitesi ölçütlerini iş modeline göre uygula.
4. Web sitesi varsa araç rehberine göre tarayıcı Meta Pixel'ini doğrulamaya çalış. Pixel yokluğu %10'luk site ölçüm kriterinde değerlendirilir; test yapılamıyorsa U/D yaz. CAPI'yi kamusal kaynaktan doğrulanmış sayma.
5. Kullanıcı aktif Google/Instagram reklamı verdiğini söylediyse ilgili resmi reklam kütüphanesinde doğru işletme/reklamvereni doğrula. Aktif reklam vermediğini söylediyse rekabet riski uyarısını ekle ama genel puanı düşürme.
6. `references/araclar-ve-kurulum.md` ve `references/platform-kisitlari.md` güvenlik/erişim kurallarını uygula. Bilgisayara bağlanmayı isteme; yalnızca oturumda gerçekten görünür dosyaları incele. Kullanıcı “Evet” dediyse `assets/` klasöründeki gerçek dosyaları kontrol et.
7. Bulguları `templates/performans-raporu.md` biçiminde yaz. Her önemli bulgu için kanıt/kaynak, iş etkisi, öneri, öncelik ve güven düzeyini belirt.
8. Özel analitik veya reklam hesabı verileri yoksa raporu görünürlük ve kalite değerlendirmesi olarak adlandır. Erişilemeyen metrikleri sayısallaştırma.
9. Raporun sonuna şablondaki Hasan Wflow imza/CTA bloğunu aynen ekle; bağlantı önizlemesinin her Markdown görüntüleyicisinde çıkacağını garanti etme.
10. Ses için Whisper/model/FFmpeg eksikse Talimatlar.md'daki Evet/Hayır kararını sor ve yanıt gelene kadar sonraki aşamaya geçme. Kullanıcı Evet derse kurulumu yalnızca mevcut ortam izin verdiği ölçüde, araç rehberindeki resmi ve asgari izinli yöntemle yap; ortam izinlerini atlatma. Hayır derse ses analizini atla ve diğer analizlere devam et. FFmpeg'in yalnızca video kareleri için gerektiği durumda, kurulum reddedilirse kare yükleme seçeneğini sun ve diğer analizlere devam et.

## Güven düzeyi

- **Yüksek:** Sayfada veya dosyada doğrudan gözlemlendi.
- **Orta:** Birden fazla gözlemle desteklenen, ancak doğrulanması gereken çıkarım.
- **Düşük:** Sınırlı görünürlük veya eksik bağlam nedeniyle doğrulanamayan olasılık.

Kullanıcı adına harici sistemlerde değişiklik yapma. Kurulum için ilgili açık onay gerekir ve mevcut ortamın izinleri ayrıca geçerlidir. Gerekli araç yoksa önce bunu belirt; güvenli ve resmi kurulum bilgisini sun, Evet yanıtından sonra yalnızca ortam izin veriyorsa kurulumu gerçekleştir. Bilgisayara bağlanmayı standart çözüm olarak isteme.
