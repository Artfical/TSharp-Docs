# T-Sharp (T#) — Tkinter GUI Sınavı
## CEVAP ANAHTARI

---

### Soru 1 — (5 puan)
**Cevap: c) `kullan gui`**

---

### Soru 2 — (5 puan)
**Cevap: b)** Widget'ın mevcut değerini bir değişkene okur.

---

### Soru 3 — (5 puan)
**Komut:** `pencere_goster`  
**Otomatik değişkenler:** `<ad>` (BooleanVar nesnesi) ve `<ad>_widget` (widget nesnesinin kendisi)

---

### Soru 4 — (5 puan)
- `etiket` üzerinde: etiketin metnini değiştirir  
- `ilerleme_cubugu` üzerinde: doluluk yüzdesini (0–100) ayarlar

---

### Soru 5 — (10 puan)
**Hata:** `kullan gui` satırı eksik.

**Düzeltilmiş hali:**
```tsharp
kullan gui

pencere ana "Uygulama" 400 300
etiket lbl "Merhaba!" ana
buton btn "Tıkla" ana
pencere_goster ana
```

---

### Soru 6 — (10 puan)
**Sorun:** `fonksiyon goster()` içinde `giris_degeri` değişkeni tanımlanmamış. Giriş kutusunun değeri `widget_deger giris giris_degeri` ile okunmalı. Ayrıca değer `yazdır` ile terminale değil `widget_ayarla` ile etikete yazılmalı.

**Düzeltilmiş hali:**
```tsharp
kullan gui

fonksiyon goster():
    widget_deger giris giris_degeri
    widget_ayarla lbl giris_degeri
son

pencere ana "Test" 300 200
giriskutusu giris ana
etiket lbl "Sonuç:" ana
buton btn "Göster" ana goster
pencere_goster ana
```

---

### Soru 7 — (10 puan)
```tsharp
kullan gui

fonksiyon topla():
    widget_deger sayi1_giris s1
    widget_deger sayi2_giris s2
    degisken sonuc = sayiya(s1) + sayiya(s2)
    widget_ayarla sonuc_lbl "Toplam: " + yaziya(sonuc)
son

pencere ana "Hesap Makinesi" 300 200
etiket lbl1 "Birinci sayı:" ana
giriskutusu sayi1_giris ana
etiket lbl2 "İkinci sayı:" ana
giriskutusu sayi2_giris ana
buton btn "Topla" ana topla
etiket sonuc_lbl "Toplam: " ana
pencere_goster ana
```

---

### Soru 8 — (10 puan)
```tsharp
kullan gui

fonksiyon durumu_goster():
    widget_deger bildirim_cb durum
    eger durum:
        mesaj_kutusu "Durum", "Bildirimler etkin."
    degilse:
        mesaj_kutusu "Durum", "Bildirimler kapalı."
    son
son

pencere ana "Ayarlar" 300 200
onay_kutusu bildirim_cb "Bildirimleri etkinleştir" ana
buton btn "Durumu Göster" ana durumu_goster
pencere_goster ana
```

---

### Soru 9 — (20 puan)
```tsharp
kullan gui

fonksiyon kaydet():
    widget_deger metin_alani icerik
    dosya_ekle("notlar.txt", icerik + "\n")
    mesaj_kutusu "Başarılı", "Not kaydedildi."
son

fonksiyon temizle():
    widget_ayarla metin_alani ""
    mesaj_kutusu "Temizlendi", "Metin alanı temizlendi."
son

pencere ana "Not Defteri" 500 400
metin_alani metin_alani ana 15 60
buton btn_kaydet "Kaydet" ana kaydet
buton btn_temizle "Temizle" ana temizle
pencere_goster ana
```
*Puanlama: Metin alanı 5p, kaydet fonksiyonu 5p, temizle fonksiyonu 5p, mesaj kutuları 5p*

---

### Soru 10 — (20 puan)
```tsharp
kullan gui

liste tum_notlar []

fonksiyon ekle():
    widget_deger ad_giris ogrenci_adi
    widget_deger not_kaydirici not_degeri
    liste satir [ogrenci_adi, yaziya(sayiya(not_degeri))]
    tablo_satir not_tablosu satir
    ekle(tum_notlar, sayiya(not_degeri))
son

fonksiyon ortalama_goster():
    eger uzunluk(tum_notlar) esittir 0:
        mesaj_kutusu "Uyarı", "Henüz not girilmedi."
    degilse:
        degisken ort = yuvarla(ortalama(tum_notlar), 2)
        mesaj_kutusu "Ortalama", "Not ortalaması: " + yaziya(ort)
    son
son

pencere ana "Not Takip" 500 450
etiket lbl1 "Öğrenci Adı:" ana
giriskutusu ad_giris ana
etiket lbl2 "Not (0-100):" ana
kaydirici not_kaydirici ana 0 100
buton btn_ekle "Ekle" ana ekle
tablo not_tablosu ana
tablo_sutun not_tablosu "Ad" 200
tablo_sutun not_tablosu "Not" 100
buton btn_ort "Ortalamayı Göster" ana ortalama_goster
pencere_goster ana
```
*Puanlama: Tablo ve sütunlar 5p, ekle fonksiyonu 5p, kaydırıcı 5p, ortalama 5p*
