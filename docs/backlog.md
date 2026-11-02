# Öncelikli başlangıç işleri

Tarih: 2 Kasım 2026. Tüm işler açık; uygulama ve donanım doğrulaması bekleniyor.
P0: sonraki tasarım/enerji verme adımlarını açan kararlar. P1: seçilen tasarımı uygulama ve doğrulama.

| Sıra | İş | Öncelik | Bağımlılık | Somut çıktı |
| --- | --- | --- | --- | --- |
| 1 | [EC-01: D01 kullanıcı akışını ve V1 kapsamını kesinleştir](https://github.com/Merteryet/brush.eo/issues/1) | P0 | Yok | Kabul edilmiş D01 kapsamı ve güncellenmiş karar günlüğü. |
| 2 | [EC-02: Denetleyici kartını ve elektriksel modül arayüzünü seç](https://github.com/Merteryet/brush.eo/issues/2) | P0 | EC-01 | Kart karşılaştırması, üretici kaynakları ve revizyonlu elektriksel arayüz tablosu. |
| 3 | [EC-03: D01 şema/BOM paketini ve enerji verme incelemesini hazırla](https://github.com/Merteryet/brush.eo/issues/3) | P0 | EC-02 | Kaynak şema + görüntülenebilir çıktı, BOM, direnç hesabı ve imzalı/tarihli inceleme kaydı. |
| 4 | [EC-04: Tek buton → LED firmware'ini ve tekrarlanabilir derlemeyi uygula](https://github.com/Merteryet/brush.eo/issues/4) | P1 | EC-02 | Kaynak firmware, sabitlenmiş araç sürümleri, derleme/yükleme yönergesi ve mantık kontrolü kanıtı. |
| 5 | [EC-05: D01 çevrimdışı öğrenci deney kartını yaz](https://github.com/Merteryet/brush.eo/issues/5) | P1 | EC-01, EC-03 | software/experiments/ECV1-D01.md içinde uygulanabilir öğrenci yönergesi. |
| 6 | [EC-06: D01 masaüstü testlerini çalıştır ve kanıtlarla teslimatı doğrula](https://github.com/Merteryet/brush.eo/issues/6) | P1 | EC-03, EC-04, EC-05 | tests/results/ altında revizyonlara bağlı test raporu ve açık kusur listesi. |

## Uygulama sırası

EC-01 → EC-02. Ardından EC-03 şema/güvenlik çalışması ve EC-04 firmware'in enerjisiz geliştirilmesi ilerleyebilir. EC-04'ün karta yükleme adımı EC-03 kapısına bağlıdır. EC-05 onaylı şema ve güvenlik adımlarını kullanır. EC-06 bütün teslim parçaları ve enerji verme kapısı hazır olduğunda başlar.

## Kabul ölçütleri

### EC-01

- [ ] Hedef öğrenci ve öğrenme çıktısı bir cümleyle tanımlı.
- [ ] Buton → LED akışı, dahil/dışarıda listesi ve D01 kabul ölçütleri incelendi.
- [ ] ADR-003/004 önerileri kabul edildi veya gerekçeyle değiştirildi; ürün sahibi kararı kaydedildi.
- [ ] SmartBox kapsam dışında; tamamlanmış prototip/test iddiası yok.

### EC-02

- [ ] En az iki kart maliyet, erişilebilirlik, GPIO ve araç desteğiyle karşılaştırıldı.
- [ ] Tek kart seçimi ve veri sayfası/revizyon kaynakları kaydedildi.
- [ ] Besleme, GPIO eşikleri/azami değerleri, akım bütçesi, pin/polarite ve konektör kararı açık.
- [ ] Buton bias yapısı, kopuk giriş davranışı ve tek besleme/geri besleme yaklaşımı belirli.
- [ ] ADR-005/006 güncellendi; 3,3 V adayının kesin durumu kaydedildi.

### EC-03

- [ ] LED seri direnci ve GPIO akımları seçilen parça/veri sayfasına göre hesaplandı.
- [ ] BOM adet/model bilgileri ile pin/konektör etiketleri tutarlı.
- [ ] Kaynak gerilimi, akım sınırı ve korumaları sayısal değerlerle tanımlı.
- [ ] Kısa devre ön kontrolü, geri besleme ve açılış durumu riskleri incelendi.
- [ ] Güvenlik kapısının tüm maddeleri için kanıt var; inceleyen/tarih ve enerji verme kararı kayıtlı.
- [ ] Şebeke/24 V/röle/motor kapsam dışı; kasıtlı kısa devre testi yok.

### EC-04

- [ ] Pin/polarite eşlemesi tek yerde; pressed → led_on dönüşümü açık.
- [ ] Başlangıç/algılanabilir başlatma hatasında çıktı kapalı tutuluyor.
- [ ] 30 ms debounce ve ≤100 ms tepki hedefi için mantık kontrolleri var.
- [ ] Temiz ortamda derleme komutları ve bağımlılık sürümleri belgelendi.
- [ ] ADR-007 güncellendi; T01 çıktısı kaydedildi.
- [ ] Gerçek karta enerji/yükleme EC-03 güvenlik kapısı geçildikten sonra; T02–T08 başarı iddiası ayrı ölçüme bağlı.

### EC-05

- [ ] Amaç, ön bilgi, onaylı parça/şema ve enerjisiz bağlantı adımları var.
- [ ] Basılı/bırakılmış davranış tablosu ve tahmin/gözlem sorusu var.
- [ ] Ön kontrol, hata giderme, fiziksel enerji kesme ve deney sonu adımları var.
- [ ] Hesap, ağ veya ayrı uygulama gerekmiyor.
- [ ] Güvenlik belgesiyle tutarlı; belirsiz pin/gerilim tarifi yok.

### EC-06

- [ ] T01–T09 gerçek sonuçlarla kaydedildi; çalıştırılmayan/engelli testler açıkça işaretli.
- [ ] 5 açılış + 5 reset ve 20 bas/bırak döngüsü tamamlandı.
- [ ] 30 ms debounce ve ≤100 ms tepki uygun zaman ölçümüyle kanıtlandı.
- [ ] Besleme/GPIO/LED değerleri onaylı sınırlara karşı sayısal ölçüldü.
- [ ] İkinci kişi veya ayrı oturum deney kartını tekrar uyguladı.
- [ ] Her sonuç kart/şema/firmware revizyonu ve kanıt dosyasına bağlı; başarısızlık için düzeltme işi var.
- [ ] D01 yalnız tüm zorunlu ölçütler geçtiğinde tamamlandı; sonraki modül ayrı kararla seçiliyor.

## Tamamlanma kuralı

Başlangıç PR'ı bu işleri kapatmaz. Her issue ilgili dosya/PR ve doğrulama kanıtı ile değerlendirilir. Donanım kanıtı bulunmayan işler “test edildi” sayılmaz. D01 sonrası yeni modül ve lisans kararları ayrıca açılır; SmartBox iş listesine alınmaz.
