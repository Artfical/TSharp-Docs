# T-Sharp (T#) — Temel Kavramlar Sınavı
## CEVAP ANAHTARI

---

### Soru 1 — (5 puan)

**Cevap: b) 25**

Açıklama: `3 ** 2 = 9`, `4 ** 2 = 16`, `9 + 16 = 25`

---

### Soru 2 — (5 puan)

**Cevap: c) `["b", "c", "d"]`**

Açıklama: `dilimleme` bitis indeksini dahil etmez. İndeks 1, 2, 3 → "b", "c", "d"

---

### Soru 3 — (5 puan)

**Cevap: `"T-Sharp-4-1"`**

---

### Soru 4 — (5 puan)

**Cevap: 120**

Açıklama: `1*2*3*4*5 = 120` (faktöriyel hesabıdır)

---

### Soru 5 — (10 puan)

**Hatalar:**
1. `fonksiyon fibonacci(n)` satırının sonunda `:` eksik
2. `eger n kucuktur 2` satırının sonunda `:` eksik
3. `eger` bloğu `son` ile kapatılmamış

**Düzeltilmiş hali:**
```tsharp
fonksiyon fibonacci(n):
    eger n kucuktur 2:
        dondur n
    son
    dondur fibonacci(n-1) + fibonacci(n-2)
son
```

*Puanlama: Her hata 3 puan, düzeltilmiş kod doğruysa +1 puan*

---

### Soru 6 — (10 puan)

**Sorun:** `toplam = not` yerine `toplam += not` olmalıdır. Her iterasyonda toplam sıfırlanıp sadece son elemana eşitlenmektedir. Son çıktı 85 (son eleman) olur, 355 değil.

**Düzeltilmiş hali:**
```tsharp
liste notlar [60, 75, 90, 45, 85]
degisken toplam = 0

her not icinde notlar:
    toplam += not
son

yazdır "Toplam:" toplam
```

---

### Soru 7 — (10 puan)

**Örnek doğru cevap:**
```tsharp
girdi sayi_metin "Bir tam sayı girin: "
degisken sayi = sayiya(sayi_metin)
degisken asal_mi = dogru

eger sayi kucuk_esit 1:
    asal_mi = yanlis
degilse:
    degisken bolen = 2
    dongu bolen kucuktur sayi:
        eger sayi mod bolen esittir 0:
            asal_mi = yanlis
            dur
        son
        bolen += 1
    son
son

eger asal_mi:
    yazdır sayi "bir asal sayıdır."
degilse:
    yazdır sayi "asal sayı değildir."
son
```

---

### Soru 8 — (10 puan)

**Örnek doğru cevap:**
```tsharp
liste baslangic [-3, 5, -1, 8, 0, 12, -7, 4]
liste pozitifler []

her sayi icinde baslangic:
    eger sayi buyuktur 0:
        ekle(pozitifler, sayi)
    son
son

yazdır pozitifler
```

---

### Soru 9 — (20 puan)

**Örnek doğru cevap:**
```tsharp
liste orjinal [1, 2, 3, 4, 5]
liste ters []
degisken i = uzunluk(orjinal) - 1

dongu i buyuk_esit 0:
    ekle(ters, orjinal[i])
    i -= 1
son

yazdır ters
```

*Puanlama: Döngü mantığı doğruysa 10p, çıktı doğruysa +10p*

---

### Soru 10 — (20 puan)

**Örnek doğru cevap:**
```tsharp
liste notlar []
degisken i = 1

dongu i kucuk_esit 5:
    girdi not_metin yaziya(i) + ". notu girin: "
    degisken not = ondalikliya(not_metin)
    ekle(notlar, not)
    i += 1
son

degisken ort = ortalama(notlar)
yazdır "Ortalama:" yuvarla(ort, 2)

eger ort buyuk_esit 90:
    yazdır "Harf Notu: AA"
degilse:
    eger ort buyuk_esit 75:
        yazdır "Harf Notu: BA"
    degilse:
        eger ort buyuk_esit 60:
            yazdır "Harf Notu: BB"
        degilse:
            eger ort buyuk_esit 50:
                yazdır "Harf Notu: CC"
            degilse:
                yazdır "Harf Notu: FF"
            son
        son
    son
son
```

*Puanlama: Döngüyle not toplama 5p, ortalama 5p, harf notu koşulları 10p*
