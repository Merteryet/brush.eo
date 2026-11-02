# Kısa karar günlüğü

“Karar” kullanıcı tarafından belirlenen yönü; “öneri” henüz onaylanmamış teknik yaklaşımı; “açık” seçim bekleyen konuyu belirtir. Uygulama durumu ayrıca kanıtlanır.

| ID | Tarih | Durum | Karar / gerekçe | Sonuç |
| --- | --- | --- | --- | --- |
| ADR-001 | 2026-11-02 | Karar | Öncelikli ürün EduCore V1 modüler elektronik/otomasyon eğitim platformu | Depo odağı EduCore; SmartBox kapsam dışında |
| ADR-002 | 2026-11-02 | Karar | docs, hardware, firmware, software, safety, tests sorumluluklarını ayır | Her dizinde amacını anlatan README bulunur |
| ADR-003 | 2026-11-02 | Öneri | İlk dikey teslimat tek buton → LED | Küçük, gözlemlenebilir giriş/çıkış deneyinden başla |
| ADR-004 | 2026-11-02 | Öneri | Çevrimdışı deney kartı; ilk teslimatta hesap ve bulut yok | Donanım öğrenme akışı uygulama geliştirmeye bağımlı olmaz |
| ADR-005 | 2026-11-02 | Öneri | D01 yalnız düşük gerilim DC; 3,3 V mantık adayı; enerjisiz modül değişimi | Kart/veri sayfası ve güvenlik incelemesi olmadan enerji verilmez |
| ADR-006 | 2026-11-02 | Açık | Kart, besleme, koruma, konektör ve pinler | Şema ve firmware bunlar belirlenince uygulanır |
| ADR-007 | 2026-11-02 | Açık | Firmware dili, araç zinciri ve sabitlenmiş sürümler | Kart seçimi sonrası tekrarlanabilir derleme belgelenir |
| ADR-008 | 2026-11-02 | Açık | Kod, donanım ve içerik lisansları | Bu başlangıç çalışmasında lisans seçilmez |

## Yeni kayıt biçimi

ID; tarih; durum; bağlam; değerlendirilen alternatifler; seçim ve gerekçesi; üretici/teknik kaynaklar; etkilenen dosyalar; ilişkili issue/PR; doğrulama kanıtı. Karar değişirse eski kaydı silmek yerine “yerine geçti” ilişkisi ekle.

Teknik önerinin kabul edilmesi donanımın güvenli veya testin başarılı olduğunu göstermez. Bu iddialar ayrı inceleme ve test kaydı gerektirir.
