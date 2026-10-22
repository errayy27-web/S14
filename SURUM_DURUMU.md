# SS OIL - yeni proje kontrol notu

- Codemagic için kök dizine `codemagic.yaml` eklendi. GitHub deposuna ZIP içindeki klasörün *içeriği* yüklenmeli; `pubspec.yaml` ve `codemagic.yaml` depo kökünde olmalı.
- AndroidManifest'e yerel HTTP API için cleartext izni ekleniyor (hem Codemagic hem GitHub Actions).
- Dopuna `txes(date, amount, statusId)` ve `00` durumundan, kuruş / 100 hesaplanıyor. MTEL=Local2, AERO=Local.
- Nakit: Gotovina - Povracaj + başarılı MTEL + AERO; kart Kartica. İade ayrı ekranda gösterilmiyor.
- Stok ekranında kalan miktar artık ART.Kolicina değil; kaydedilmiş stok bazından sonra ölçülen satış farkı.
- Son 7 gün kaydı telefonun yerel verisinde tutulur; 7 günden eski tarihler silinir. Uygulama kapalıyken geçmişte hangi gün satış yapıldığı bu sayaçtan belirlenemez; bu nedenle tarihsel raporun doğruluğu PC'den gün gün kayda bağlıdır.
- Ürün fotoğrafları yerel telefonda saklanır, bulut fotoğraf eşitlemesi henüz uygulanmamıştır.
- Yakıt/market ürün ayrımı için yakıt Art_ID eşleştirmesi gerekir; ürün adına göre tahmin güvenilir değildir.
- Bu kaynak proje Flutter/Android gerçek derleme ve cihaz testi yapılmadan 'hatasız APK' sayılmaz.
