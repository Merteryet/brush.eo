# Firmware

Durum: planlama. Kaynak kod, seçilmiş kart veya derleme altyapısı henüz yok.

D01 davranışı: başlangıçta LED kapalı; tek butonun kararlı durumunu LED'e aktar; debounce uygula. Fiziksel polarite tek bir kart eşleme katmanında mantıksal `pressed` değerine dönüştürülür. Kabul hedefleri [D01](../docs/first-deliverable.md) içindedir.

## Kart seçimi sonrası eklenecekler

- Kaynaklar ve tek yerde pin/polarite tanımı.
- Araç zinciri ve bağımlılık sürümleri.
- Temiz ortam kurulum, derleme, yükleme ve reset adımları.
- Açılış/başlatma hatasında kapalı çıktı ve debounce davranışı.
- Karttan bağımsız mantık kontrolleri; ardından gerçek kart testi.
- Test kaydını kaynak commit SHA'sına bağlama.

Firmware, elektriksel koruma veya acil durdurma sistemi değildir. Kısa devre/yanlış bağlantı için yazılımsal algılama varsayılmaz. GPIO açılış durumu seçilen donanım üzerinde ölçülür.
