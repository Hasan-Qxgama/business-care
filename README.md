# Business Care

Business Care, işletmenin herkese açık dijital varlıklarını profesyonel dijital pazarlama bakışıyla inceleyen bir yapay zekâ çalışma klasörüdür. Instagram, Facebook, Google İşletme Profili, web sitesi ve kullanıcının sağladığı reklam görseli/video/ses dosyalarında güçlü yönleri, olası eksikleri ve uygulanabilir fırsatları değerlendirir.

## Tek promptla edinme ve başlatma

Yeni bir Codex veya Claude Code çalışma alanında aşağıdaki prompt depoyu klonlatır ve analizi başlatır:

> `https://github.com/Hasan-Qxgama/business-care` deposunu geçerli çalışma alanıma klonla. Projede paket kurulumu gerekmediğini doğrula. Klonladıktan sonra AGENTS.md oku, Talimatlar.md ve skills/business-care-audit/SKILL.md dosyalarını oku ve yönergeleri uygula. İşletme analizini başlat; Talimatlar.md'daki ilk başlangıç sorusunu sor ve yanıtımı bekle. Depo çalışma alanında zaten varsa yeniden klonlama.

İncelenecek reklam dosyaları `assets/` klasörüne eklenebilir; bu klasöre eklenen dosyalar Git'e dahil edilmez.

## Ayrıca Kullanım

1. Depoyu bilgisayarınıza alın: `git clone https://github.com/Hasan-Qxgama/business-care.git`
2. `business-care` klasörünü Claude Code veya Codex'te proje olarak açın. Projede harici paket kurulum adımı yoktur.
3. İncelenecek reklam görsel/video/ses dosyalarını isteğe bağlı olarak `assets/` klasörüne ekleyin.
4. Asistana şu isteği verin:

   **Business Care analizini başlat. Önce Talimatlar.md dosyasındaki başlangıç sorularını sırayla ve tek tek sor; sonra projedeki beceri ve raporlama yönergelerini uygula.**

4. Asistan işletme bilgilerini Talimatlar.md'daki sırayla sorar; ardından reklam kreatifi planı, aktif Google/Instagram reklam durumu ve `assets` klasörünü sorup erişilebilen dijital varlıkları inceler.

Claude Code için `CLAUDE.md` ve `.claude/skills/` yönergeleri; Codex için `AGENTS.md` ve `skills/` içindeki ortak beceri kullanılır. Platformun açık internet erişimi veya ilgili dosya görüntüleme araçları yoksa analiz kapsamı buna göre sınırlanır. PageSpeed Insights ve reklam kütüphaneleri herkese açık/ücretsiz araçlardır; bu sitelerden gerçek hesap performansına erişilmez.

Araç erişimi Claude Code ve Codex oturumlarında farklı olabilir. Bilgisayara uzaktan bağlanma analiz için ön koşul değildir. FFmpeg/Whisper gerekirse güvenli kurulum ve izin akışı için `references/araclar-ve-kurulum.md`; beklenen sınır davranışları için `references/test-senaryolari.md` kullanılır.

## Raporun kapsamı

Rapor, dışarıdan görülebilen dijital varlıkların pazarlama açısından niteliğini değerlendirir. Yetkili analitik veya reklam hesabı verileri sağlanmadıkça gerçek erişim, satış, dönüşüm ya da reklam getirisi ölçümü yapmaz. Erişilemeyen alanlar raporda açıkça belirtilir.

İlk standart puanlama modeli `references/puanlama-olcutleri.md` içinde **Business Care v0.1** olarak tutulur. Kanal puanları ve genel dijital vitrin puanı ayrı hesaplanır; reklam kreatif puanları genel puana eklenmez. Aktif reklam kullanmamak genel puanı düşürmez; bunun için ayrı bir rekabet riski uyarısı gösterilir. Web sitesi varsa Meta Pixel tarayıcı kurulumu doğrulanmaya çalışılır.
