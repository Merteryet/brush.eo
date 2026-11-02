# Donanım

Durum: planlama. Şema, PCB veya onaylı BOM henüz yok.

D01 kapsamı: bir denetleyici kartı, bir buton giriş modülü, bir LED çıkış modülü ve onaylanacak düşük gerilim DC besleme. [Mimari](../docs/architecture.md) elektriksel adayları ve açık seçimleri tanımlar.

## İlk uygulanacak paket

1. Kart adaylarını erişilebilirlik, maliyet, GPIO sınırları ve üretici dokümanlarıyla karşılaştır.
2. Seçilen kartın revizyonunu ve üretici bağlantılarını kaydet.
3. Besleme/GPIO sınırları, pin tablosu, LED seri direnç hesabı ve buton bias yapısını hazırla.
4. Konektör yönü, etiketler, geri besleme ve akım sınırlamayı incele.
5. Kaynak şema, görüntülenebilir şema çıktısı ve adet/model/satıcı bilgili BOM ekle.
6. [Güvenlik kapısı](../safety/README.md) geçilmeden enerji verme.

Dosya hedefleri: `schematics/`, `bom/`, `interfaces/` ve gerekiyorsa `pcb/`. Gerçek içerik oluştuğunda bu alt dizinler açılır. Bir bağlantı fotoğrafı şema ve elektriksel inceleme yerine geçmez.
