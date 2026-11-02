# Mimari ve modül sınırları

Durum: D01 için teknik öneri. Elektriksel arayüz onaylanana kadar üretim veya bağlantı talimatı değildir.

| Modül | Sahip olduğu sorumluluk | Dışarıda bıraktığı sorumluluk |
| --- | --- | --- |
| Temel kart / güç | Denetleyici, kararlı besleme, güvenli açılış, programlama bağlantısı | Şebeke ve 24 V saha kontrolü |
| Giriş modülü | Tek buton; tanımlı boşta durum; mantıksal giriş | Güç anahtarlama ve çıkış sürme |
| Çıkış modülü | LED, hesaplanmış seri direnç, tanımlı polarite | Motor/röle/yük sürme |
| Firmware | Giriş okuma, debounce, durum eşleme, çıktı başlatma | Donanım koruması, her bağlantı hatasını algılama |
| Eğitim içeriği | Kurulum, tahmin, gözlem, hata giderme ve kapatma | Hesap/bulut veya zorunlu PC uygulaması |
| Test kayıtları | Revizyon, beklenen/gerçek sonuç, ölçüm ve kusur takibi | Kanıtsız başarılı durum işaretleme |

## D01 arayüz önerisi

- Tek mantık gerilimi alanı: **3,3 V nominal aday**. Kart seçilince GPIO sınırları, eşikler, akımlar ve toleranslar üretici belgelerinden alınır. 5 V toleransı varsayılmaz.
- Besleme adayı: onaylı 5 V DC kaynak → seçilen kartın uygun güç girişi/regülatörü. GPIO'ya 5 V uygulanmaz. Kaynak, kablo ve akım sınırı kart/veri sayfasıyla birlikte karara bağlanır.
- Giriş: tek dijital sinyal; aktif seviye, bias direnci ve pin eşlemesi donanım kararında belirlenir. Fiziksel değer firmware'de `pressed` mantıksal değerine dönüştürülür.
- Çıkış: tek dijital LED kontrolü; akım bütçesi, polarite ve seri direnç hesabı şemada gösterilir. `led_on = pressed`.
- Konektör: anahtarlı/etiketli öneri; kesin model ve pin sırası açık karardır. Enerjiliyken takıp çıkarma desteklenmez.
- USB yalnızca seçilen kartın belgelenmiş programlama/besleme işlevi içindir. İki kaynaktan eşzamanlı besleme, geri besleme analizi yapılmadan yasaktır.
- Hata durumları ve sınırlar [ilk teslimatta](first-deliverable.md), enerji verme kapısı [güvenlik belgesinde](../safety/README.md) tanımlıdır.

## Değişiklik kuralı

Besleme, pin, polarite veya konektör değişikliği; şema, firmware eşlemesi, deney kartı, risk kaydı ve test planını birlikte günceller. Gerçek sonuçlar kullanılan revizyona bağlanır. Yeni analog/sensör modülü ayrı arayüz kararı ve test planı gerektirir.

## Açık teknik seçimler

Kart/MCU, GPIO pinleri, besleme kaynağı ve korumaları, akım limiti, LED/direnç, buton bias yapısı, konektör, firmware dili/araç zinciri ve lisans henüz belirlenmedi. Seçimler [karar günlüğünde](decisions.md) gerekçeleri ve kaynaklarıyla kaydedilir.
