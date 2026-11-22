# Business Care puanlama modeli v0.1

Bu model, dışarıdan görülebilen dijital varlıkların kalitesini tutarlı biçimde puanlamak için hazırlanmış ilk sürümdür. Gerçek erişim, satış, reklam getirisi veya dönüşüm performansını ölçmez. Ağırlıklar Business Care'in başlangıç varsayımlarıdır; farklı sektörlerde örnek denetimlerle kalibre edilmelidir.

## Puanlama birimi ve 0–4 ölçeği

Her kriter için yalnızca gözlemlenebilir kanıta dayalı bir tam sayı kullan:

| Puan | Standart tanım | Yorumlama ölçütü |
|---:|---|---|
| **0** | Yok, çalışmıyor veya açıkça yanlış | Bu kriter işletme için uygulanabilir ve açıkça eksik/bozuk/yanıltıcı. |
| **1** | Çok zayıf | Mevcut olsa da müşteri için büyük ölçüde belirsiz, zor veya kullanışsız. |
| **2** | Kısmi/temel | Bazı ihtiyacı karşılıyor; belirgin eksik veya sürtünme var. |
| **3** | İyi | İhtiyacı açık ve tutarlı şekilde karşılıyor; küçük iyileştirmeler kalmış. |
| **4** | Çok güçlü | Müşteri ihtiyacına göre açık, doğru, erişilebilir ve özenle uygulanmış. |
| **U/D** | Ulaşılamadı | İçerik görünmüyor, test yapılamadı veya kanıt yetersiz. Puan değil. |
| **U/G** | Uygulanamaz | Kriter bu işletme/kanal için mantıken geçerli değil. Puan değil. |

**0 ile U/D'yi karıştırma:** “Yok” cevabı veya doğrulanmış eksiklik uygulanabilir bir kriterde 0 olabilir. Sayfa açılmıyor ya da bilgi görülemiyorsa U/D kullan. Sırf bir işletme belli bir özelliği kullanmıyor diye U/G seçme; gerçekten sektöre/iş modeline uygun olmaması gerekir.

## Hesaplama

### Kanal puanı

Her kanal içindeki kriterlerin ağırlıkları, U/G olanlar hariç, toplamda %100'dür. `U/D` kriterlerinin ağırlığı kapsam hesabında kalır ama puan ortalamasına girmez.

**Kanal puanı (0–100)** = `100 × Σ(kriter ağırlığı × kriter puanı) / (4 × puanlanan kriter ağırlığı toplamı)`

**Kanal kapsamı (%)** = `100 × puanlanan kriter ağırlığı toplamı / U/G olmayan kriter ağırlığı toplamı`

- Kanal kapsamı **%60'ın altındaysa**, 0–100 kanal puanı verme; `U/D — yetersiz kapsam` ve kapsam yüzdesini yaz.
- Bir platformun mevcut olmadığı kullanıcı tarafından açıkça doğrulanmış ve o kanal işletme türü için anlamlıysa kanal puanı **0/100, kapsam %100**: dijital varlık yokluğu görünürlük açığıdır.
- Kanal işletme türüne uygun değilse U/G olarak dışarıda bırak ve gerekçeyi yaz.
- Kanal bağlantısı var ama açılamıyorsa 0 verme; kapsamı düşürerek U/D işaretle.

### Genel dijital vitrin puanı

Genel puan, kanal ağırlıkları işletme türüne göre seçilebiliyorsa verilir. Varsayılan matris:

| İşletme arketipi | Instagram | Facebook | Google İşletme Profili | Web sitesi |
|---|---:|---:|---:|---:|
| **Yerel, müşterinin ziyaret ettiği işletme** | 25% | 15% | 35% | 25% |
| **E-ticaret / çevrimiçi mağaza** | 25% | 15% | 10%* | 50% |
| **Hizmet / uzmanlık işletmesi** | 25% | 15% | 25%* | 35% |

`*` Google İşletme Profili yalnızca Google'ın uygunluk koşullarına uyan, müşteriyi yüz yüze kabul eden veya müşteriye giden işletmeler için puanlanır. Sadece çevrimiçi hizmet veren ve uygun olmayan işletmede U/G seçilir; kalan kanal ağırlıkları oransal biçimde yeniden ölçeklenir.

İşletme birden fazla arketipe uyuyorsa müşteri yolunu en iyi temsil edeni seç ve raporda adını yaz. Arketip net değilse genel puan verme; yalnızca kanal puanlarını göster veya puanlamadan önce kullanıcıya iş modelini sor. Facebook/Instagram'ın hiç bulunmaması otomatik olarak U/G değildir; tüketici kanalının stratejik olarak uygun olup olmadığı gerekçelendirilir. İşletme kanalı açıkça kullanmıyorsa, arketipteki ağırlığı varsa 0 olarak puanlanır.

Genel puanı yalnızca arketipe göre **uygulanabilir kanal ağırlığının en az %70'inde** yeterli kanıt varsa göster. Kısmi kanıtın etkisini kapsama yansıt:

**Genel kapsam (%)** = `Σ(kanal arketip ağırlığı × kanal kapsamı) / Σ(uygulanabilir kanal arketip ağırlıkları) × 100`

**Genel puan** = `Σ(kanal arketip ağırlığı × kanal kapsamı × kanal puanı) / Σ(kanal arketip ağırlığı × kanal kapsamı)`; bu hesapta yalnızca kanal kapsamı en az %60 olup puanı hesaplanabilen kanalları kullan. Genel kapsam hesabında ise tüm uygulanabilir kanallar yer alır; böylece düşük kapsamlı kanal genel puanda saklanmaz ve %70 eşiğini düşürür.

Bu puan “dijital vitrinin gözlemlenebilen hazırlık puanı”dır. Reklam kütüphanesi ve reklam kreatif puanları bu toplama **eklenmez**; ücretli reklam vermemek tek başına zayıflık değildir.

### Reklam vermeme ve rekabet riski uyarısı

İşletme Google veya Instagram'da aktif reklam vermediğini söylediyse uygun platform için raporda uyarı göster. Bu uyarı **genel puana dahil değildir**. Reklam vermemenin bazı pazarlarda, özellikle rakipler aynı kanalda görünür biçimde reklam verirken, erişim ve müşteri kazanımında dezavantaj riski yaratabileceğini söyle. Kütüphane incelemesi rakiplerin aktif reklamını gösterebilir, ancak rakiplerin sonuçlarını veya işletmenin “müşterilerinin çoğunu kaybettiğini” kanıtlamaz. Uyarı kesin kayıp değil, ayrıca doğrulanması gereken rekabet riskidir.

Önerilen standart ifade: “Şu anda [Google/Instagram] reklamı vermediğinizi belirttiniz. Özellikle rakipler bu kanalda aktifse dijital görünürlükte geride kalma ve potansiyel müşterilerinizin önemli bir bölümünün rakiplere yönelmesi riski var. Bu dışarıdan yapılan analiz, müşterilerinizin çoğunu kaybettiğinizi veya kaybın büyüklüğünü kanıtlamaz; bunu doğrulamak için pazar, rakip ve kendi dönüşüm verilerinizi incelemek gerekir.”

### Puan aralıkları

| Puan | Etiket |
|---:|---|
| 0–39 | Öncelikli iyileştirme gerekiyor |
| 40–59 | Belirgin geliştirme alanları var |
| 60–74 | Temel düzeyde hazır |
| 75–89 | Güçlü dijital sunum |
| 90–100 | Çok güçlü ve tutarlı dijital sunum |

Etiketler Business Care'in iç rubriğidir; sektör benchmark'ı, Google/Meta puanı veya gelir tahmini değildir. Her puanın yanında kapsamı ve kanıt kaynağını göster.

## Kanal kriterleri ve ağırlıklar

### Instagram — profil puanı

En yeni 15 gönderiyi içerik örneklemi olarak kullan. Puan kapsamına profilin görünen durumu ve bu örnek dahil; geçmiş tüm gönderileri tarama.

| Kriter | Ağırlık | Kanıt/puanlama odağı |
|---|---:|---|
| Profil görseli ve marka tanınabilirliği | 15% | Logo kadrajı, netlik, küçük görünümde tanınma. |
| Biyografi ve konumlandırma | 20% | Kim, ne sunuyor, kime; sektör diline uygun açıklık. |
| İletişim ve sonraki adım | 15% | Çalışan bağlantı/iletişim/konum veya uygun müşteri aksiyonu. |
| Sabit hikâyelerin faydası | 10% | Hizmet, süreç, sık soru, konum veya güven kanıtı; yalnızca ilgiliyse. |
| Son 15 gönderinin pazarlama niteliği | 30% | Hedef müşteriyle ilgi, görsel/video kalite, mesaj netliği, içerik amacı ve uygun çeşitlilik. |
| Açıklama, tutarlılık ve güven | 10% | Caption katkısı/CTA ve temel bilgilerin diğer kanallarla uyumu. |

Bir kriterin alt göstergeleri puanlanırken ilgili gözlemleri not et. Sırf video yok diye 0 veya ağır ceza verme; format karışımı başarının garantisi değildir. İnsan yüzü zorunlu kriter değildir. Sabit hikâyeler işletme için uygun değil veya görünür değilse sırasıyla U/G ya da U/D uygula.

### Facebook — sayfa puanı

Son 15 gönderiyi incele; daha geriye gitme.

| Kriter | Ağırlık | Kanıt/puanlama odağı |
|---|---:|---|
| Profil görseli ve sayfa tanınabilirliği | 10% | Logo/görsel netliği ve işletmeyle eşleşme. |
| Banner/kapak | 10% | Kalite, doğru kırpılma, mobil/masaüstü okunabilirlik ve güncellik. |
| Açıklama ve konumlandırma | 20% | Kim, ne sunuyor, kime; kategori/açıklama tutarlılığı. |
| İletişim ve müşteri aksiyonu | 15% | Uygun telefon, adres/hizmet alanı, saat, mesaj/rezervasyon/bağlantı. |
| Son 15 gönderinin pazarlama niteliği | 30% | Hedef müşteriyle ilgi, mesaj, görsel/video kalitesi ve amaca uygun çeşitlilik. |
| Caption, CTA ve bilgi tutarlılığı | 15% | Açıklamaların yararı, sonraki adım ve işletme bilgilerinin tutarlılığı. |

### Google İşletme Profili — profil puanı

Yalnızca işletme Google profil açmaya uygunsa puanla. Yerel sonuç sırası veya özel profil metriklerini dışarıdan puanlama.

| Kriter | Ağırlık | Kanıt/puanlama odağı |
|---|---:|---|
| İşletme adı ve kategori | 20% | Gerçek hayattaki ad; ana faaliyeti doğru ve özgül anlatan kategori; gereksiz anahtar kelime yok. |
| Adres/hizmet alanı ve saatler | 20% | İş modeline uygun doğru konum biçimi ve güncel müşteri saatleri. |
| Telefon, site ve aksiyon bağlantıları | 15% | Çalışan, doğru ve müşteri için uygun sonraki adım. |
| Açıklama ve hizmet/ürün bilgisi | 10% | Doğru, faydalı ve işletmeye özgü bilgiler. |
| Fotoğraf/video sunumu | 10% | Gerçek, net, güncel ve müşteri kararına yardımcı içerik. |
| Yorum temaları ve işletme yanıtları | 15% | Görünen örneklerde tekrar eden temalar; yanıtların profesyonel ve ilgili olması. |
| Diğer kanallarla tutarlılık | 10% | Ad, telefon, konum/saat, hizmet ve web sitesi uyumu. |

Profil şartlarına uygun değilse kanalı U/G olarak işaretle. Adres, saat veya fotoğrafı her işletmede aynı biçimde şart koşma. Görünen yorum sayısı veya puanını işletme kalitesinin kesin ölçüsü sayma.

### Web sitesi — site puanı

| Kriter | Ağırlık | Kanıt/puanlama odağı |
|---|---:|---|
| İlk ekran ve değer önerisi | 15% | İşletmenin ne sunduğu, kime ve faydasının ne olduğu; görsel ve başlığın açıklığı. |
| Menü, gezinme ve mobil kullanım | 15% | Önemli bilgiye ulaşma, anlaşılır etiket ve mobil kullanılabilirlik. |
| İçerik ve görsel hiyerarşi | 10% | Taranabilir metin, uygun bilgi yoğunluğu, net/ilgili görseller; ham kelime sayısı değil. |
| Dönüşüm/iletişim akışı | 20% | CTA, iletişim/randevu/teklif veya ürün keşfinden sonraki adıma kadar işlev. |
| Güven, destek ve karar soruları | 15% | Uygun iletişim, teslimat/iade/gizlilik vb. açıklamalar ve müşterinin sık sorularının yanıtlanması. |
| Hız ve teknik performans | 10% | PageSpeed Insights mobil/masaüstü sonuçları; laboratuvar/CrUX ayrımı. |
| Bağlantı ve form işlevselliği | 5% | Görünen önemli bağlantı, iletişim formu ve sayfa hatalarının gözlemi. |
| Meta Pixel tarayıcı ölçümü | 10% | Pixel ve PageView'in gerçekten tespit edilmesi; izin/çerez durumu ve doğrulama sınırları. |

E-ticaret alt modülü, dönüşüm akışı içinde değerlendirilir: ürün bilgisi, fiyat/ek masraflar, teslimat/iade, sepet/ödeme, hata geri bildirimi ve mobil akış. Misafir alışverişi varsa olumlu; yoksa yalnızca hesap zorunluluğunun bu işletmede yaratabileceği sürtünmeyi puanla. İşlem yapma veya ödeme tamamlama. E-ticaret değilse sepet/ödeme U/G; bunun yerine temel iletişim/randevu/teklif akışını puanla. SSS veya referansların yokluğu tek başına 0 değildir; yanıtlanmayan önemli karar sorusu varsa ilgili kriteri düşür.

**PageSpeed alt puan eşlemesi (hız kriteri içinde):** Lighthouse mobil performans skoru 0–49 → 0; 50–69 → 1; 70–89 → 2; 90–94 → 3; 95–100 → 4. Masaüstü skorunu ayrıca raporla, ancak web puanında mobil skor kullanılır. PSI çalıştırılmadıysa hız kriteri U/D; CrUX alan verisi yoksa Lighthouse skoru yerine uydurma saha puanı verme. Lighthouse/PSI anlık performans ve kullanıcı deneyiminin tamamı değildir.

**Meta Pixel puanlama alt kuralı:** 4 = ana sayfa ve iş modeline uygun en az bir önemli sayfada `PageView` doğrulandı; 3 = ana sayfada `PageView` doğrulandı fakat diğer önemli sayfalar kontrol edilmedi; 2 = Pixel yükleniyor ancak `PageView`/yinelenme davranışı tutarsız; 1 = Pixel kodu var ama temel olay çalışmıyor veya belirgin hata var; 0 = yeterli ve izin uyumlu canlı kontrolde ilgili sayfalarda tarayıcı Pixel'i tespit edilmedi (yalnızca *tarayıcı Pixel'i yok* olarak adlandır). Kaynak koduna erişim yok, consent nedeniyle test yapılamadı veya sonuç belirsizse U/D. Conversions API'nin sunucu tarafında çalışıp çalışmadığı kamusal kontrolle doğrulanamaz; kullanıcı/Events Manager kanıtı olmadan “hiç Meta ölçümü yok” deme. Meta Pixel yokluğu site puanının bu %10'luk ölçüm kriterini etkiler; aktif reklam vermemek kendi başına bu kriterin 0 olduğu anlamına gelmez.

### Aktif reklamlar — ücretli kreatif puanı (genel puana eklenmez)

Yalnızca kullanıcı ilgili kanalda aktif reklam verdiğini belirtiyorsa ve kütüphanede doğru reklamveren eşleşmesi doğrulanabiliyorsa uygula. Reklam kütüphanesinde eşleşme yoksa “0” değil U/D.

| Kriter | Ağırlık | Kanıt/puanlama odağı |
|---|---:|---|
| Reklamveren/marka eşleşmesi | 10% | Reklamın gerçekten bu işletmeye ait olduğunun doğrulanması. |
| Mesaj ve farkındalık aşaması | 20% | Mesajın sorun/çözüm/ürün/karar aşamasına uygunluğu. |
| Teklif ve kanıt | 15% | Fayda, teklif ve iddiaların açıklığı/doğrulanabilirliği. |
| Kreatif uygulama | 20% | Görsel/video kalitesi, okunabilirlik, açılış ve marka tutarlılığı. |
| Metin ve CTA | 15% | Başlık/açıklama netliği ve uygun sonraki adım. |
| Açılış sayfası uyumu | 20% | Reklam vaadi, hedef URL ve sayfanın sonraki adımının tutarlılığı. |

Kütüphanede görülen reklamların sayısı, uzun süre aktif kalması veya tekrar etmesi başarı/harcama/dönüşüm kanıtı değildir. Hedefleme, bütçe ve sonuçları puanlama.

### Assets klasöründeki kreatif — dosya başına puan

Her dosyayı ayrı puanla, sonra incelenen dosyaların basit ortalamasını “örnek kreatif puanı” olarak göster. Dosya türüne uymayan kriterleri U/G olarak çıkar ve ağırlıkları yeniden ölçekle.

| Kriter | Ağırlık |
|---|---:|
| Mesaj, hedef müşteri ve farkındalık aşaması | 20% |
| İlk dikkat/hook ve ana faydanın açıklığı | 15% |
| Görsel/video/ses uygulama kalitesi | 25% |
| Metin/altyazı/ses anlaşılabilirliği | 15% |
| CTA/sonraki adım | 10% |
| Marka ve vaat tutarlılığı | 15% |

Ses doğrudan dinlenmediyse ses niteliğini U/D bırak; transkript yalnızca söylenen içeriğe kanıt olabilir. Videonun tümü izlenmediyse örnek kare/kesitleri belirt. Otomatik transkripti kesin alıntı gibi sunma.

## Öncelik ve kalibrasyon

P1/P2/P3 öncelikleri puandan bağımsızdır: P1 müşteri aksiyonunu engeller; P2 güven/deneyimi anlamlı geliştirir; P3 daha küçük fırsattır. Düşük puan otomatik olarak en yüksek öncelik değildir; iş etkisini ayrıca gerekçelendir.

Bu v0.1 ağırlıkları başlangıç standardıdır, kanıtlanmış sektör benchmark'ı değildir. Gerçek işletme örnekleriyle pilot yapılınca puanlayıcılar arası farklar ve sektör uygunluğu gözden geçirilmeli; değişiklik yapılırsa modeli v0.2 olarak sürümle ve eski raporların hangi sürümle puanlandığını sakla.
