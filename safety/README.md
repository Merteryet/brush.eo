# Güvenli deney yaklaşımı — D01

Durum: ön risk planı. **Donanım güvenlik incelemesi yapılmadı; enerji verme onayı yok.** Bu dosya sertifikasyon, uygunluk beyanı veya onaylı bağlantı şeması değildir.

D01 yalnız onaylanacak düşük gerilim DC buton/LED deneyini kapsar. Şebeke, açılmış adaptör, 24 V PLC hattı, röle, motor, lityum hücre/şarj devresi ve yüksek akımlı yükler kapsam dışıdır.

## Enerji verme kapısı

Aşağıdakiler tamamlanmadan fiziksel deney başlatılmaz:

- [ ] Kart/veri sayfası revizyonu, GPIO sınırları ve seçilen besleme doğrulandı.
- [ ] Şema, BOM, LED direnci/akımı ve buton boşta durumu incelendi.
- [ ] Kaynağın akım sınırı ve korumaları gerekçeli sayısal değerlerle belgelendi.
- [ ] USB/harici kaynak geri beslemesi ve olası çift besleme önlendi.
- [ ] Enerji kesikken polarite, bağlantı yönü, açık iletken ve kısa devre ön kontrolü geçti.
- [ ] Yazılım yükleme ve açılış/reset sırasında çıkış davranışı için test düzeni hazır.
- [ ] Kaynağı fiziksel ayırma yöntemi erişilebilir; ilk çalışma gözetimli.
- [ ] İnceleyen kişi, tarih, şema/kart revizyonu ve gerekçe kaydedildi.

## Başlangıç risk kaydı

| Risk | Önlem | Doğrulama |
| --- | --- | --- |
| Yanlış gerilim / polarite | Tek tanımlı güç girişi; etiket/yön; besleme kontrolü | Kaynak çıkışını ve kart girişini yük öncesi kontrol et |
| GPIO aşırı akımı / kısa devre | Seri direnç hesabı; akım bütçesi; uygun kaynak koruması | Akım hesabı ve normal çalışmada ölçüm; kasıtlı kısa devre yapma |
| Boşta giriş / LED beklenmedik yanması | Bias ve kapalı çıktı tasarımı | Açılış, reset ve enerjisiz sökülmüş girişle kontrollü yeniden başlatma testi |
| USB/harici besleme geri beslemesi | Aynı anda çift kaynak kullanma; onaylı tek yol | Şema ve besleme senaryosu incelemesi |
| Isınma / hasarlı kablo | Görsel kontrol; akım sınırlama; gözetimli ilk test | Akım ve sıcaklık gözlemi; limitler şemayla birlikte belirlenir |
| Enerjiliyken modül değişimi | Önce enerjiyi fiziksel ayır | Deney kartı ve uygulama kontrolü |

## Durdurma koşulları

Beklenmedik ısınma, koku, duman, hasarlı kablo, kararsız besleme veya tanımsız çıkış görülürse enerjiyi fiziksel kaynaktan kes. Tekrar enerji vermeden nedeni incele ve kayıt aç. Bilinmeyen bağlantıyı deneme-yanılma ile enerjilendirme.

Arıza testleri önce enerji kesilerek hazırlanır; yalnız incelemede güvenli olduğu belirlenen senaryolar çalıştırılır. Korumanın çalıştığını görmek için bilerek kısa devre/ters gerilim uygulanmaz.

## İnceleme kaydı

Her donanım revizyonu için tarih, inceleyen, kullanılan üretici kaynakları, ölçüm araçları, besleme/akım sınırı, açık riskler ve “enerji verilebilir / engelli” kararı eklenir. İlk değerler seçilene kadar ilgili sayısal sınırlar açık kalır ve kapı geçilmiş sayılmaz.
