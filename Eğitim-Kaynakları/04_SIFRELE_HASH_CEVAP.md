# T-Sharp (T#) — Şifreleme ve Hash Sınavı
## CEVAP ANAHTARI

---

### Soru 1 — (5 puan)
**Cevap: b)**  
Tek yönlüdür; hash'ten orijinal metne geri dönülemez.

---

### Soru 2 — (5 puan)
**Cevap: b)**  
XOR bir anahtar kullanır ve gerçek anlamda şifreleme yapar. Base64 yalnızca veriyi farklı bir formata kodlar; anahtar gerektirmez ve kolayca tersine çevrilebilir.

---

### Soru 3 — (5 puan)
**Cevap:** `kullan sifrele` — `kullan hash`

---

### Soru 4 — (5 puan)
**Cevap:** `hash_dogrula` sabit zamanlı karşılaştırma (constant-time comparison) kullanır. Normal `==` karşılaştırmasında karakterler farklı bulununca hemen durulur; bu süre farkı "timing attack" adı verilen bir saldırı yöntemiyle şifre tahminine olanak tanır. `hash_dogrula` bunu engeller.

---

### Soru 5 — (10 puan)
**Hata:** `xor_sifrele` komutu `kullan sifrele` modülünde yer alır, ancak kodda yalnızca `kullan hash` aktive edilmiş.

**Düzeltilmiş hali:**
```tsharp
kullan hash
kullan sifrele

sha256 sifre_hash "kullanici_sifresi"
yazdır sifre_hash

xor_sifrele sifreli "gizli mesaj" "anahtar123"
yazdır sifreli
```

---

### Soru 6 — (10 puan)
**Sorun:** Kullanıcıdan `sifre` değişkenine alınan şifre, `sifreli_yaz` içinde kullanılmıyor; sabit `"123"` anahtarı kullanılıyor. Bu kritik bir güvenlik açığıdır — her kullanıcı aynı anahtarla korunur.

**Düzeltilmiş hali:**
```tsharp
kullan sifrele

girdi sifre "Şifrenizi girin: "
girdi yeni_not "Notunuz: "

sifreli_yaz "notlar.enc" yeni_not sifre
yazdır "Not kaydedildi."
```

---

### Soru 7 — (10 puan)
```tsharp
kullan hash

girdi metin1 "Bir metin girin: "
sha256 hash1 metin1
yazdır "SHA256:" hash1

girdi metin2 "Doğrulamak için tekrar girin: "
hash_dogrula eslesme metin2 hash1 "sha256"

eger eslesme:
    yazdır "Eşleşti! Metinler aynı."
degilse:
    yazdır "Eşleşmedi. Metinler farklı."
son
```

---

### Soru 8 — (10 puan)
```tsharp
kullan sifrele

girdi mesaj "Mesajı girin: "
girdi anahtar "Anahtarı girin: "

xor_sifrele sifreli mesaj anahtar
yazdır "Şifreli mesaj:" sifreli

xor_coz cozulmus sifreli anahtar
yazdır "Çözülen mesaj:" cozulmus

eger cozulmus esittir mesaj:
    yazdır "Doğrulama başarılı: mesaj bütünlüğü korunmuş."
degilse:
    yazdır "HATA: Mesaj bozulmuş!"
son
```

---

### Soru 9 — (20 puan)
```tsharp
kullan hash

degisken kullanici_dosyasi = "kullanicilar.txt"

fonksiyon kayit_ol(kullanici_adi, sifre):
    sha256 sifre_hash sifre
    degisken kayit = kullanici_adi + ":" + sifre_hash
    dosya_ekle kullanici_dosyasi kayit + "\n"
    yazdır "Kayıt başarılı:" kullanici_adi
son

fonksiyon giris_yap(kullanici_adi, sifre):
    eger degil dosya_var_mi(kullanici_dosyasi):
        yazdır "Kullanıcı bulunamadı."
        dondur yanlis
    son

    degisken icerik = dosya_oku(kullanici_dosyasi)
    liste satirlar = bol(icerik, "\n")

    her satir icinde satirlar:
        eger uzunluk(satir) buyuktur 0:
            liste parcalar = bol(satir, ":")
            eger parcalar[0] esittir kullanici_adi:
                hash_dogrula eslesme sifre parcalar[1] "sha256"
                eger eslesme:
                    yazdır "Giriş başarılı! Hoş geldin," kullanici_adi
                    dondur dogru
                degilse:
                    yazdır "Hata: Yanlış şifre."
                    dondur yanlis
                son
            son
        son
    son

    yazdır "Kullanıcı bulunamadı:" kullanici_adi
    dondur yanlis
son

kayit_ol("talha", "guvenli_sifre_123")
giris_yap("talha", "guvenli_sifre_123")
giris_yap("talha", "yanlis_sifre")
```
*Puanlama: kayit_ol fonksiyonu 8p, giris_yap fonksiyonu 8p, kullanım 4p*

---

### Soru 10 — (20 puan)
```tsharp
kullan hash

liste dosyalar ["ana.tsharp", "ayarlar.txt", "veri.csv"]
degisken hash_dosyasi = "hashler.txt"

fonksiyon hashleri_kaydet():
    dosya_yaz hash_dosyasi ""
    her dosya icinde dosyalar:
        eger dosya_var_mi(dosya):
            dosya_sha256 h dosya
            dosya_ekle hash_dosyasi dosya + ":" + h + "\n"
            yazdır "Hash kaydedildi:" dosya
        degilse:
            yazdır "Bulunamadı:" dosya
        son
    son
son

fonksiyon hashleri_dogrula():
    eger degil dosya_var_mi(hash_dosyasi):
        yazdır "Hash dosyası yok. Önce hashleri_kaydet() çalıştırın."
        dondur
    son

    degisken kayitlar = dosya_oku(hash_dosyasi)
    liste satirlar = bol(kayitlar, "\n")

    her satir icinde satirlar:
        eger uzunluk(satir) buyuktur 0:
            liste parcalar = bol(satir, ":")
            degisken dosya_adi = parcalar[0]
            degisken kayitli_h = parcalar[1]

            eger dosya_var_mi(dosya_adi):
                dosya_sha256 mevcut_h dosya_adi
                eger mevcut_h esittir kayitli_h:
                    yazdır "TEMIZ:" dosya_adi
                degilse:
                    yazdır "DEĞİŞTİRİLMİŞ:" dosya_adi
                son
            degilse:
                yazdır "SİLİNMİŞ:" dosya_adi
            son
        son
    son
son

hashleri_kaydet()
yazdır
hashleri_dogrula()
```
*Puanlama: hashleri_kaydet 8p, hashleri_dogrula 8p, raporlama 4p*
