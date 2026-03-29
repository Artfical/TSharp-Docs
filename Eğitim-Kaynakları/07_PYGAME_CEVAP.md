# T-Sharp (T#) — Pygame Sınavı
## CEVAP ANAHTARI

---

### Soru 1 — (5 puan)
**Cevap: b) `kullan oyun`**

---

### Soru 2 — (5 puan)
**Cevap: b)** Oyun döngüsünü saniyede 60 kareye kilitler.

---

### Soru 3 — (5 puan)
**Pencere kapatma sabiti:** `CIKIS`  
**Hizalama:** `metin_yaz` metni x koordinatına göre **ortalanmış** olarak çizer.

---

### Soru 4 — (5 puan)
- `tus_basili_mi` → Tuş **sürekli basılı** tutulduğunda her karede tetiklenir; hareket ettirme için kullanılır  
- `olay_kontrol KLAVYE_ASAGI` → Tuşa **bir kez basıldığında** tek seferlik tetiklenir; zıplama, atış gibi tek eylemler için kullanılır

---

### Soru 5 — (10 puan)
**Hata:** `saat_olustur` çağrısı yapılmamış ve döngü içinde `saat_tikla` komutu eksik. FPS kontrolü olmadan döngü CPU'yu maksimum kullanır.

**Düzeltilmiş hali:**
```tsharp
kullan oyun

oyun_baslat
oyun_ekran ekran 800 600
saat_olustur saat

degisken oyun_devam = dogru
dongu oyun_devam:
    olaylari_isle
    olay_kontrol cikis_olaylari CIKIS
    eger uzunluk(cikis_olaylari) buyuktur 0:
        degisken oyun_devam = yanlis
    son
    ekran_doldur ekran SIYAH
    ekran_guncelle
    saat_tikla saat 60
son

oyun_kapat
```

---

### Soru 6 — (10 puan)
**Sorun:** `tus_basili_mi` ile tuş durumu okunuyor ama sonuca göre `top_x` değeri güncellenmiyor. Hareket gerçekleşmiyor.

**Düzeltilmiş hali:**
```tsharp
kullan oyun

oyun_baslat
oyun_ekran ekran 800 600
saat_olustur saat

degisken top_x = 400
degisken top_y = 300

degisken oyun_devam = dogru
dongu oyun_devam:
    olaylari_isle
    olay_kontrol cikis_olaylari CIKIS
    eger uzunluk(cikis_olaylari) buyuktur 0:
        degisken oyun_devam = yanlis
    son

    tus_basili_mi sola K_SOL
    tus_basili_mi saga K_SAG

    eger sola:
        top_x -= 5
    son
    eger saga:
        top_x += 5
    son

    ekran_doldur ekran SIYAH
    ciz_dolu_cember ekran KIRMIZI top_x top_y 20
    ekran_guncelle
    saat_tikla saat 60
son
oyun_kapat
```

---

### Soru 7 — (10 puan)
```tsharp
kullan oyun

oyun_baslat
oyun_ekran ekran 800 600
saat_olustur saat
yazi_tipi_yukle buyuk_font "Arial" 72

degisken sayac = 0
degisken oyun_devam = dogru

dongu oyun_devam:
    olaylari_isle
    olay_kontrol cikis_olaylari CIKIS
    eger uzunluk(cikis_olaylari) buyuktur 0:
        degisken oyun_devam = yanlis
    son

    sayac += 1
    eger sayac buyuktur 180:
        degisken oyun_devam = yanlis
    son

    ekran_doldur ekran SIYAH
    metin_yaz ekran "OYUN" BEYAZ 400 300 buyuk_font
    ekran_guncelle
    saat_tikla saat 60
son

oyun_kapat
```
*Açıklama: 60 FPS × 180 kare = 3 saniye*

---

### Soru 8 — (10 puan)
```tsharp
kullan oyun

oyun_baslat
oyun_ekran ekran 800 600
saat_olustur saat
ekran_doldur ekran SIYAH

degisken oyun_devam = dogru
dongu oyun_devam:
    olaylari_isle
    olay_kontrol cikis_olaylari CIKIS
    eger uzunluk(cikis_olaylari) buyuktur 0:
        degisken oyun_devam = yanlis
    son

    olay_kontrol fare_tiklamalari FARE_ASAGI
    her tiklama icinde fare_tiklamalari:
        fare_konum konum
        degisken r = rastgele_sayi(0, 255)
        degisken g = rastgele_sayi(0, 255)
        degisken b = rastgele_sayi(0, 255)
        renk_olustur rastgele_renk r g b
        ciz_dolu_cember ekran rastgele_renk konum_x konum_y 20
    son

    ekran_guncelle
    saat_tikla saat 60
son

oyun_kapat
```

---

### Soru 9 — (20 puan)
```tsharp
kullan oyun

oyun_baslat
oyun_ekran ekran 800 600
saat_olustur saat
yazi_tipi_yukle yazi "Arial" 20

degisken top_x = 400
degisken top_y = 300
degisken yari = 20

degisken oyun_devam = dogru
dongu oyun_devam:
    olaylari_isle
    olay_kontrol cikis_olaylari CIKIS
    eger uzunluk(cikis_olaylari) buyuktur 0:
        degisken oyun_devam = yanlis
    son

    tus_basili_mi sola K_SOL
    tus_basili_mi saga K_SAG
    tus_basili_mi yukari K_YUKARI
    tus_basili_mi asagi K_ASAGI

    eger sola ve top_x - yari buyuktur 0:
        top_x -= 5
    son
    eger saga ve top_x + yari kucuktur 800:
        top_x += 5
    son
    eger yukari ve top_y - yari buyuktur 0:
        top_y -= 5
    son
    eger asagi ve top_y + yari kucuktur 600:
        top_y += 5
    son

    ekran_doldur ekran SIYAH
    ciz_dolu_cember ekran KIRMIZI top_x top_y yari
    degisken koord = "X: " + yaziya(top_x) + "  Y: " + yaziya(top_y)
    metin_yaz ekran koord BEYAZ 400 30 yazi
    ekran_guncelle
    saat_tikla saat 60
son

oyun_kapat
```
*Puanlama: Hareket 5p, sınır kontrolü 7p, koordinat yazısı 4p, döngü yapısı 4p*

---

### Soru 10 — (20 puan)
```tsharp
kullan oyun

oyun_baslat
oyun_ekran ekran 800 600
saat_olustur saat
yazi_tipi_yukle yazi "Arial" 18
ekran_doldur ekran SIYAH

degisken oyun_devam = dogru
dongu oyun_devam:
    olaylari_isle
    olay_kontrol cikis_olaylari CIKIS
    eger uzunluk(cikis_olaylari) buyuktur 0:
        degisken oyun_devam = yanlis
    son

    olay_kontrol tus_olaylari KLAVYE_ASAGI
    her tus icinde tus_olaylari:
        eger tus esittir K_ESC:
            degisken oyun_devam = yanlis
        son
        eger tus esittir K_C:
            ekran_doldur ekran SIYAH
        son
    son

    fare_dugme dugme
    eger dugme_sol:
        fare_konum konum
        ciz_nokta ekran BEYAZ konum_x konum_y
    son

    metin_yaz ekran "Sol tuş: çiz | C: temizle | ESC: çıkış" GRI 400 20 yazi
    ekran_guncelle
    saat_tikla saat 60
son

oyun_kapat
```
*Puanlama: Çizim mekaniği 5p, C tuşu temizleme 5p, ESC çıkışı 5p, bilgi yazısı 5p*
