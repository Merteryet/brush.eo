# ECV1-D01 — Butondan LED'e

Durum: **tanımlandı; uygulanmadı ve donanım üzerinde doğrulanmadı**.

## Öğrenme çıktısı

Öğrenci fiziksel bir girdiyi mantıksal durumla ilişkilendirir: butona basıldığında LED yanar, bırakıldığında söner. Beklenen davranışı tahmin eder, bağlantıyı kontrol eder ve gözlemini kaydeder. Endüstriyel PLC yerine bir mikrodenetleyiciyle temel giriş/çıkış mantığı öğretilir.

## Kullanıcı akışı

1. Deney kartından amaç, parça listesi ve güvenlik koşullarını oku.
2. Enerji kapalıyken onaylanmış şema ve pin tablosuyla buton/LED modüllerini bağla.
3. Polarite, LED seri direnci, pinler, ortak referans ve kısa devre kontrolünü yap; ön kontrolü kaydet.
4. Gözetimli ilk testte onaylı beslemeyi bağla. Başlangıçta LED sönük olmalı.
5. Butona bas ve bırak; beklenen/gerçek durumları karşılaştır.
6. LED yanmıyorsa enerjiyi kes, şema ve bağlantıları kontrol et. Enerjiliyken modül değiştirme.
7. Ölçümü ve sonucu kaydet; deney sonunda enerjiyi kes ve bağlantıyı sök.

## Teslim paketi

| Çıktı | Asgari içerik |
| --- | --- |
| Donanım paketi | Bir kart seçimi; üretici kaynağı; pin tablosu; revizyonlu şema; hesaplanmış LED direnci; BOM ve besleme sınırları |
| Firmware | Tek buton → tek LED; mantıksal polarite; debounce; başlangıçta kapalı çıktı; derleme/yükleme talimatı ve sürümler |
| Deney kartı | Amaç, ön bilgi, bağlantı adımları, davranış tablosu, gözlem sorusu, hata giderme ve kapatma |
| Güvenlik incelemesi | Riskler, kontrol önlemleri, enerji verme kararı ve inceleyen/tarih |
| Doğrulama kaydı | Kart/şema/firmware revizyonu, testler, ölçümler, kanıt ve açık kusurlar |

Kart modeli, konektör, pinler, besleme ve araç zinciri henüz seçilmemiştir. Bu belge bağlanabilir bir şema değildir.

## Davranış sözleşmesi (öneri)

| Durum | Beklenen davranış |
| --- | --- |
| Açılış/reset | Çıkış ilk kontrol edilebilir anda kapalı; donanım açılış geçişleri ayrıca ölçülür |
| Geçerli bırakılmış buton | LED kapalı |
| 30 ms boyunca kararlı basılı buton | LED açık |
| 30 ms boyunca kararlı bırakılmış buton | LED kapalı |
| 30 ms'den kısa geçiş | Son kararlı durum korunur |
| Kararlı durum değişimi | LED en geç 100 ms içinde yeni duruma geçer |
| Enerji kesilmesi | LED enerjisiz; yeniden başlatmada aynı açılış kuralı |
| Algılanabilir yazılım başlatma hatası | Çıktı kapalı tutulur; yeniden deneme için enerji kesilir |

30 ms/100 ms değerleri prototip için kabul hedefidir; test sonucu değildir. Kopuk girişin bırakılmış okunması donanım bias tasarımında doğrulanmalıdır. Firmware her kablo kopuğunu, yanlış bağlantıyı veya kısa devreyi algılayamaz; elektriksel koruma ve ön kontrol zorunludur.

## D01 tamamlanma ölçütleri

- [ ] Kart, besleme, pin ve konektör kararı kaydedildi.
- [ ] Şema/BOM ve risk incelemesi geçti; enerji verme kaydı var.
- [ ] Firmware belgelenen sürümlerle temiz ortamda derlenip karta yüklendi.
- [ ] Çevrimdışı deney kartı tek başına takip edilebiliyor.
- [ ] Test planındaki tüm zorunlu testler geçti; ölçüm ve kanıtlar eklendi.
- [ ] Kritik açık kusur yok; tekrarlayan kişi/ikinci oturum sonucu kaydedildi.

## Sonraki doğrulama sırası

Kart/veri sayfası incelemesi → elektriksel arayüz kararı → şema/BOM → güvenlik kapısı → firmware ve deney kartı → enerjili masaüstü testleri → bağımsız tekrar → sonraki modül kararı. Başlangıç dokümanlarının birleştirilmesi bu kutuları otomatik tamamlamaz.
