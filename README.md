# BRUSH.EO — EduCore V1

BRUSH EduCore, elektronik ve otomasyon öğrenimini küçük, ölçülebilir deneyler üzerinden ilerleten modüler bir eğitim platformudur. Hedef kullanıcılar elektronik/otomasyon öğrencileri, bireysel öğrenenler ve eğitim laboratuvarlarıdır.

**Öncelikli ürün: EduCore V1. SmartBox kapsam dışıdır.**

## Doğrulanmış durum — 2 Kasım 2026

Başlangıçta depoda yalnızca `.gitkeep` vardı. Bu paket ürün kapsamı, arayüz önerileri ve doğrulama planını oluşturur. Çalışan firmware, uygulama, şema/PCB, fiziksel prototip veya başarılı donanım testi henüz yoktur. Aşağıdaki teknik seçimler aksi belirtilmedikçe öneridir.

## V1 hedefi ve sınırları

V1 hedefi: bir temel denetleyici ve değiştirilebilir eğitim modülleriyle giriş/çıkış mantığını, ölçüm yapmayı ve hata ayıklamayı öğretmek. İlk dikey teslimat **ECV1-D01: Butondan LED'e** deneyidir.

| Dahil | V1 dışında |
| --- | --- |
| Yerel ve çevrimdışı deney yönergesi | Hesap, bulut, sosyal özellikler, mobil/web uygulama |
| Tek buton girdisi, tek LED çıktısı | Şebeke gerilimi, motor, röle, yüksek akım yükleri |
| Güvenli başlatma, hata ve enerji kesme akışı | Endüstriyel PLC/24 V saha bağlantısı |
| Modül arayüz belgesi ve ölçümlü test kaydı | SmartBox ve ticari ürün/sertifikasyon iddiası |

V1'in sonraki modülleri ayrı kararlarla seçilecektir; D01'in tamamlanması bütün V1'in tamamlandığı anlamına gelmez.

## Başlangıç noktaları

1. [İlk teknik teslimat ve kullanıcı akışı](docs/first-deliverable.md)
2. [Mimari ve modül sınırları](docs/architecture.md)
3. [Güvenli deney yaklaşımı](safety/README.md)
4. [Karar günlüğü](docs/decisions.md)
5. [Öncelikli işler ve bağımlılıklar](docs/backlog.md)
6. [Doğrulama planı](tests/README.md)

## Depo yapısı

| Yol | Sorumluluk |
| --- | --- |
| [docs/](docs/) | Kapsam, teslimat, arayüzler, kararlar, iş listesi |
| [hardware/](hardware/) | Kart seçimi, pin eşlemesi, şema, BOM, bağlantı ve revizyon kayıtları |
| [firmware/](firmware/) | Buton okuma, LED sürme, hata/başlatma davranışı |
| [software/](software/) | Öğrenci yönergeleri; ileride gerekirse yerel araçlar |
| [safety/](safety/) | Risk kaydı, enerji verme koşulları ve durdurma kuralları |
| [tests/](tests/) | Kabul planı ve gerçek ölçümlere dayalı deney kayıtları |

## Nasıl ilerlenir?

Önce kart ve elektriksel arayüz kararını ver, ardından şema/BOM ve güvenlik incelemesini tamamla. Firmware ve çevrimdışı deney kartını hazırla; yalnızca inceleme geçildikten sonra kontrollü masaüstü testi yap. Her adımın çıkışı ve kabul ölçütü [backlog](docs/backlog.md) içinde tanımlıdır.

Şu anda derlenecek veya çalıştırılacak uygulama yoktur. İlk firmware teslimatında kurulum, derleme, yükleme ve bağımlılık sürümleri `firmware/README.md` dosyasına eklenecektir.

## Katkı ve ilerleme kaydı

Her değişiklik ilgili işi, etkilenen belgeyi ve doğrulama kanıtını içeren bir pull request ile sunulur. Bir iş yalnızca kabul ölçütleri kanıtlandığında tamamlandı sayılır. Fotoğraf, ölçüm, derleme çıktısı veya test sonucu yoksa sonuç “planlandı / çalıştırılmadı” olarak kalır. Tasarım kararları [karar günlüğüne](docs/decisions.md) işlenir.
