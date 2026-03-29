# T-Sharp (T#) — Dosya İşlemleri Sınavı
## CEVAP ANAHTARI

---

### Soru 1 — (5 puan)

**Cevap: b)**

`dosya_ekle()` mevcut içeriği koruyarak sona ekler; `dosya_yaz()` dosyayı tamamen sıfırlayarak yeniden yazar.

---

### Soru 2 — (5 puan)

**Cevap: c)**

`hic` döner, terminale hata mesajı yazılır ancak program çökmez ve devam eder.

---

### Soru 3 — (5 puan)

**Cevap: `Üçüncü\n`**

Açıklama: İlk `dosya_yaz` "Birinci" yazar. `dosya_ekle` sonuna "İkinci" ekler. İkinci `dosya_yaz` dosyayı sıfırlar ve yalnızca "Üçüncü" yazar.

---

### Soru 4 — (5 puan)

**Cevap:** Dosyanın ZIP arşivi içindeki adıdır. Kaynak dosyanın yolu farklı olsa bile arşivde bu isimle görünür.

---

### Soru 5 — (10 puan)

**Sorun:** `dosya_yaz()` her çağrısında dosyayı sıfırdan yazar. Yani her satır bir öncekini siler. Sonuçta dosyada yalnızca son satır kalır. Birikimli log için `dosya_ekle()` kullanılmalıdır.

**Düzeltilmiş hali:**
```tsharp
dosya_ekle("log.txt", "Kullanıcı giriş yaptı.\n")
dosya_ekle("log.txt", "İşlem başladı.\n")
dosya_ekle("log.txt", "İşlem tamamlandı.\n")
```

---

### Soru 6 — (10 puan)

**Sorun:** Dosyanın sonundaki boş satır (trailing newline) nedeniyle `bol()` son eleman olarak `""` döndürür. Bu boş satır için `bol("", ",")` çalıştırılır ve `kolonlar[0]` boş string olur. Bazı durumlarda bu hata verebilir.

**Düzeltilmiş hali:**
```tsharp
degisken icerik = dosya_oku("veri.csv")
liste satirlar = bol(icerik, "\n")

degisken i = 1
dongu i kucuktur uzunluk(satirlar):
    eger uzunluk(satirlar[i]) buyuktur 0:
        liste kolonlar = bol(satirlar[i], ",")
        yazdır kolonlar[0]
    son
    i += 1
son
```

---

### Soru 7 — (10 puan)

**Örnek doğru cevap:**
```tsharp
eger dosya_var_mi("ogrenciler.txt"):
    degisken icerik = dosya_oku("ogrenciler.txt")
    yazdır icerik
degilse:
    dosya_yaz("ogrenciler.txt", "Kayıt yok")
    yazdır "Dosya oluşturuldu."
son
```

---

### Soru 8 — (10 puan)

**Örnek doğru cevap:**
```tsharp
liste isimler ["Ali", "Veli", "Ayşe", "Fatma"]

her isim icinde isimler:
    dosya_ekle("isimler.txt", isim + "\n")
son

yazdır "İsimler dosyaya yazıldı."
```

---

### Soru 9 — (20 puan)

**Örnek doğru cevap:**
```tsharp
fonksiyon log_yaz(seviye, mesaj):
    degisken satir = "[" + seviye + "] " + mesaj + "\n"
    dosya_ekle("uygulama.log", satir)

    eger seviye esittir "HATA":
        dosya_ekle("hatalar.log", satir)
    son
son

log_yaz("BİLGİ", "Program başladı.")
log_yaz("UYARI", "Disk doluluk oranı yüksek.")
log_yaz("HATA", "Veritabanına bağlanılamadı.")
```

*Puanlama: Fonksiyon tanımı 5p, birikimli yazma 5p, HATA ayrımı 10p*

---

### Soru 10 — (20 puan)

**Örnek doğru cevap:**
```tsharp
liste dosyalar ["a.txt", "b.txt", "c.txt"]

dosya_yaz("birlesik.txt", "")

her dosya_adi icinde dosyalar:
    eger dosya_var_mi(dosya_adi):
        degisken baslik = "=== " + dosya_adi + " ===\n"
        dosya_ekle("birlesik.txt", baslik)
        degisken icerik = dosya_oku(dosya_adi)
        dosya_ekle("birlesik.txt", icerik + "\n\n")
        yazdır dosya_adi "eklendi."
    degilse:
        yazdır "UYARI:" dosya_adi "bulunamadı, atlandı."
    son
son

yazdır "Birleştirme tamamlandı."
```

*Puanlama: Döngü 5p, dosya varlık kontrolü 5p, başlık ekleme 5p, uyarı mesajı 5p*
