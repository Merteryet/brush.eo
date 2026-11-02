# D01 doğrulama planı

Durum: **hiçbir donanım testi çalıştırılmadı**. Plan veya boş şablon başarılı test değildir.

## Ön koşullar

[Güvenlik kapısı](../safety/README.md) geçmiş olmalı. Kart, şema, besleme sınırları, pinler ve firmware commit'i belirlenmeli. 100 ms tepki süresi ve kısa geçişler gözle tahmin edilmez; uygun kayıt/zaman ölçüm aracı seçilip yöntem kaydedilir.

| ID | Deneme | Kabul ölçütü | Kanıt |
| --- | --- | --- | --- |
| T01 | Temiz ortamda derle ve yükle | Belgelenen sürüm/komutlar başarılı; doğru pin eşlemesi | Komutlar, sürümler, derleme/yükleme çıktısı |
| T02 | 5 açılış + 5 reset | LED kapalı; istenmeyen açılış darbesi yok | Gözlem ve açılış sinyal kaydı |
| T03 | Bas/bırak 20 döngü | Her geçişte doğru LED durumu; tepki ≤100 ms | Giriş/çıkış zaman kaydı ve döngü sayısı |
| T04 | Debounce mantığı | <30 ms geçişleri reddet; ≥30 ms kararlı durumu kabul et | Karttan bağımsız mantık kontrolü ve güvenli kart ölçümü |
| T05 | Girişi enerjisiz sök, yeniden başlat | Tasarlanan bias ile LED kapalı; pin boşta değil | Şema/bias incelemesi ve gözlem |
| T06 | LED modülünü enerjisiz sök, yeniden başlat | Beklenmedik ısınma veya akım artışı yok; hata algılama iddiası yok | Onaylı limitlere karşı akım ölçümü |
| T07 | Normal çalışma, basılı ve bırakılmış | Besleme/GPIO/LED akımı onaylı sınırlar içinde; anormal ısınma yok | Sayısal sınırlar ve ölçülen değerler |
| T08 | Enerji kes ve tekrar başlat | Enerjisiz LED kapalı; yeniden başlatmada T02 davranışı | Gözlem/kayıt |
| T09 | Deney kartını yeni kişi veya ayrı oturum takip etsin | Gerekli tüm adımlar tamam; belirsizlikler giderilmiş | Kişi/oturum, süre, takılmalar ve düzeltmeler |

T05/T06 yalnız ön incelemede güvenli bulunduğunda çalıştırılır. Engellenen test “geçti” olarak yazılmaz; neden ve düzeltme işi açılır. T01 tamamlanmadan T02–T08; güvenlik kapısı tamamlanmadan enerjili testler başlatılmaz.

## Sonuç kaydı

[Şablonu](templates/test-record.md) kopyalayarak `tests/results/` altında tarihli bir kayıt oluştur. Zaman ölçümü, akım ve fotoğraf/log dosyalarını aynı revizyona bağla. Tüm zorunlu testler geçmeden ve kritik kusurlar kapanmadan D01 tamamlanmaz.
