# SS OIL – Sıfırdan Flutter uygulaması

Bu proje önceki `lib/main.dart` üzerine yama yapılmadan, yeni kodla oluşturuldu. Yalnızca eski sunucunun okuma arayüzü ve GitHub Actions derleme yaklaşımı referans alındı.

## Derleme
GitHub deposuna proje kökündeki dosyaları yükleyin; Actions > SS OIL Yeni APK > Run workflow. Derleme `SS-OIL-Yeni-APK` adlı artifact üretir. Bu çalışma ortamında Flutter SDK olmadığı için derleme ve telefon testi yapılmadı.

## Çalışma mantığı
- Stok Güncelle: `/snapshot` ve `/sales` ile yeni ART stok/fiyat ve toplam satış sayaçları alınır, stok başlangıç anındaki satış sayacı ayrı kaydedilir.
- Satışları Al: Son kaydedilen toplam satış sayaçlarıyla fark alınır, yalnızca yeni fark o günün yerel kaydına eklenir. En fazla 7 günlük günlük kova tutulur. Uygulama birden çok gün kapalı kalırsa aradaki satışların kesin tarihleri bilinemeyeceğinden ilk tekrar bağlandığı güne yazılır; gerçek gün ayrımı için PC tarafında günlük zamanlanmış snapshot gerekir.
- Kasa: `/kasa` nakit, kart ve Dopuna sonuçlarını okur. Yakıt/market ayrımı için Ayarlar'da yakıt ART_ID listesi tanımlanır; satış tutarları yerel günlük miktar x güncel fiyat tahminidir, geçmiş gerçek fiş fiyatı değildir.
- Dopuna: Sunucuda yapılandırılan MTEL/AERO veritabanlarından PC tarihine göre alınır. Kaynak veritabanları salt okunur.
- Siparişler, ürün fotoğrafları, tedarikçiler, minimum stok ve etiket listesi telefon içinde saklanır.
- Etiket Yok: Ürün detayından Etiket Yok ile etiket listesine eklenir. PDF'de ürün adı, Sifra, Cijena ve Code128 barkod basılır.
- Yerel sunucu çalışıyorsa yerel bağlantı, çalışmıyorsa ayarlanmış bulut API URL denenir. Bulut sunucusu kurulmadan internet üzerinden otomatik veri alınamaz.

## Bilinen sınırlar
Gerçek veritabanında fiş tarihi olmayan `SmP_S` satırlarından gün gün geçmişi kesin yeniden oluşturmak mümkün değildir. Yakıt `Art_ID` listesi ve fiş fiyatı doğrulanmadan kesin yakıt/market ciro raporu verilemez. Coffee To Go henüz bağlı değildir. Bu kaynak kod gerçek Android cihazda test edilmemiştir.
