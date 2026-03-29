# T-Sharp (T#) — PySide6 GUI Sınavı
## CEVAP ANAHTARI

---

### Soru 1 — (5 puan)
**Cevap: c) `kullan gui6`**

---

### Soru 2 — (5 puan)
**Cevap: b) Layout'a**

---

### Soru 3 — (5 puan)
**Otomatik değişken:** `ana_merkez`  
**`qt_calistir` konumu:** Her zaman dosyanın **en son satırı** olmalıdır.

---

### Soru 4 — (5 puan)
- `dikey` → Widget'ları üst üste dizer (VBoxLayout)  
- `yatay` → Widget'ları yan yana dizer (HBoxLayout)  
- `grid` → Izgara düzeni (GridLayout)  
- `form` → Etiket-giriş çiftleri için (FormLayout)

---

### Soru 5 — (10 puan)
**Hata:** Widget'lar `ana` yerine `ana_merkez` parent'ına bağlanmalı ve layout tanımlanmalı.

**Düzeltilmiş hali:**
```tsharp
kullan gui6

qt_pencere ana "Uygulama" 400 300
qt_layout yl dikey ana_merkez
qt_etiket lbl "Merhaba!" ana_merkez
qt_buton btn "Tıkla" ana_merkez
qt_pencere_goster ana
qt_calistir
```

---

### Soru 6 — (10 puan)
**Sorun:** Layout tanımlanmamış. Widget'lar `ana_merkez`'e bağlanmış ama bu merkez widget'a herhangi bir layout eklenmediğinden widget'lar görünmez.

**Düzeltilmiş hali:**
```tsharp
kullan gui6

qt_pencere ana "Test" 300 200
qt_layout yl dikey ana_merkez
qt_etiket lbl "Başlık" ana_merkez
qt_buton btn "Tamam" ana_merkez
qt_pencere_goster ana
qt_calistir
```

---

### Soru 7 — (10 puan)
```tsharp
kullan gui6

fonksiyon topla():
    widget_deger sayi1_giris s1
    widget_deger sayi2_giris s2
    degisken sonuc = sayiya(s1) + sayiya(s2)
    widget_ayarla sonuc_lbl "Toplam: " + yaziya(sonuc)
son

qt_pencere ana "Hesap Makinesi" 300 250
qt_layout yl dikey ana_merkez
qt_etiket lbl1 "Birinci sayı:" ana_merkez
qt_giriskutusu sayi1_giris ana_merkez
qt_etiket lbl2 "İkinci sayı:" ana_merkez
qt_giriskutusu sayi2_giris ana_merkez
qt_buton btn "Topla" ana_merkez topla
qt_etiket sonuc_lbl "Toplam: " ana_merkez
qt_pencere_goster ana
qt_calistir
```

---

### Soru 8 — (10 puan)
```tsharp
kullan gui6

fonksiyon degeri_goster():
    widget_deger slider deger
    qt_mesaj_kutusu "Değer" "Kaydırıcı değeri: " + yaziya(sayiya(deger)) "bilgi"
son

qt_pencere ana "Kaydırıcı" 350 200
qt_layout yl dikey ana_merkez
qt_kaydirici slider ana_merkez "yatay" 0 100
qt_buton btn "Değeri Göster" ana_merkez degeri_goster
qt_pencere_goster ana
qt_calistir
```

---

### Soru 9 — (20 puan)
```tsharp
kullan gui6

degisken secili_dosya = ""

fonksiyon dosya_sec():
    qt_dosya_dialog secili_dosya "ac"
    eger uzunluk(secili_dosya) buyuktur 0:
        degisken icerik = dosya_oku(secili_dosya)
        eger icerik degildir hic:
            widget_ayarla metin_alani icerik
        degilse:
            qt_mesaj_kutusu "Hata" "Dosya okunamadı." "uyari"
        son
    son
son

fonksiyon kaydet():
    eger uzunluk(secili_dosya) esittir 0:
        qt_mesaj_kutusu "Hata" "Önce bir dosya seçin." "uyari"
    degilse:
        widget_deger metin_alani icerik
        degisken basarili = dosya_yaz(secili_dosya, icerik)
        eger basarili:
            qt_mesaj_kutusu "Başarılı" "Dosya kaydedildi." "bilgi"
        degilse:
            qt_mesaj_kutusu "Hata" "Dosya kaydedilemedi." "hata"
        son
    son
son

qt_pencere ana "Dosya Görüntüleyici" 600 400
qt_layout yl dikey ana_merkez
qt_metin_alani metin_alani ana_merkez
qt_buton btn_sec "Dosya Seç" ana_merkez dosya_sec
qt_buton btn_kaydet "Kaydet" ana_merkez kaydet
qt_pencere_goster ana
qt_calistir
```
*Puanlama: Dosya seçme 5p, okuma ve gösterme 5p, kaydetme 5p, hata yönetimi 5p*

---

### Soru 10 — (20 puan)
```tsharp
kullan gui6

fonksiyon kaydet():
    widget_deger kullanici_giris kullanici_adi
    widget_deger tema_combo tema
    widget_deger sunucu_giris sunucu
    widget_deger port_spin port
    yazdır "Kullanıcı:" kullanici_adi
    yazdır "Tema:" tema
    yazdır "Sunucu:" sunucu
    yazdır "Port:" port
son

qt_pencere ana "Ayarlar" 400 350
qt_layout yl dikey ana_merkez
qt_sekme_widget sekmeler ana_merkez

notebook_sekme sekmeler genel_sekme "Genel"
qt_etiket lbl1 "Kullanıcı Adı:" genel_sekme
qt_giriskutusu kullanici_giris genel_sekme
qt_etiket lbl2 "Tema:" genel_sekme
qt_combo_kutu tema_combo genel_sekme

notebook_sekme sekmeler ag_sekme "Ağ"
qt_etiket lbl3 "Sunucu Adresi:" ag_sekme
qt_giriskutusu sunucu_giris ag_sekme
qt_etiket lbl4 "Port:" ag_sekme
qt_spin_kutu port_spin ag_sekme 1 65535

qt_buton btn_kaydet "Kaydet" ana_merkez kaydet
qt_pencere_goster ana
qt_calistir
```
*Puanlama: Sekmeli yapı 5p, Genel sekmesi 5p, Ağ sekmesi 5p, Kaydet fonksiyonu 5p*
