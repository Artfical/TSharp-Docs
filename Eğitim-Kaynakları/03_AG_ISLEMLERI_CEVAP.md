# T-Sharp (T#) — Ağ İşlemleri Sınavı
## CEVAP ANAHTARI

---

### Soru 1 — (5 puan)
**Cevap: b)**  
`json_al` yanıtı otomatik olarak sözlük ya da listeye dönüştürür. `http_get` ise ham metin olarak `_metin` değişkenine atar.

---

### Soru 2 — (5 puan)
**Cevap: c) `-1`**

---

### Soru 3 — (5 puan)
**Cevap:** `yanit_kod`

---

### Soru 4 — (5 puan)
**Cevap:** `kullan ag` — Varsayılan zaman aşımı **30 saniye**dir.

---

### Soru 5 — (10 puan)
**Hata:** Dosyanın başında `kullan ag` yazılmamış.

**Düzeltilmiş hali:**
```tsharp
kullan ag

http_get yanit "https://httpbin.org/get"
yazdır yanit_metin
```

---

### Soru 6 — (10 puan)
**Sorun:** Sunucuya ulaşılamadığında `sure` değeri `-1` olur. Kod bu durumu kontrol etmeden `sure "ms"` yazdırır → `-1 ms` çıktısı hatalıdır.

**Düzeltilmiş hali:**
```tsharp
kullan ag

liste sunucular ["https://google.com", "https://github.com"]

her sunucu icinde sunucular:
    ping sure sunucu
    eger sure esittir -1:
        yazdır sunucu "→ ERİŞİLEMİYOR"
    degilse:
        yazdır sunucu "→" yuvarla(sure, 1) "ms"
    son
son
```

---

### Soru 7 — (10 puan)
```tsharp
kullan ag

json_al veri "https://jsonplaceholder.typicode.com/todos/1"
yazdır veri["title"]
```

---

### Soru 8 — (10 puan)
```tsharp
kullan ag

girdi token "API Token'ınızı girin: "
baslik_ekle "Authorization" "Bearer " + token

http_get yanit "https://httpbin.org/bearer"

eger yanit_kod esittir 200:
    yazdır "Kimlik doğrulama başarılı!"
degilse:
    eger yanit_kod esittir 401:
        yazdır "Hata: Geçersiz token."
    degilse:
        yazdır "Beklenmeyen hata, kod:" yanit_kod
    son
son
```

---

### Soru 9 — (20 puan)
```tsharp
kullan ag

json_al kullanicilar "https://jsonplaceholder.typicode.com/users"

dosya_yaz("kullanicilar.txt", "")

her kullanici icinde kullanicilar:
    degisken satir = kullanici["name"] + " - " + kullanici["email"] + "\n"
    dosya_ekle("kullanicilar.txt", satir)
    yazdır satir
son

yazdır "Kullanıcılar dosyaya yazıldı."
```
*Puanlama: API çağrısı 5p, döngü 5p, format 5p, dosyaya yazma 5p*

---

### Soru 10 — (20 puan)
```tsharp
kullan ag

liste sunucular ["https://www.google.com", "https://www.github.com", "https://httpbin.org"]

dosya_yaz("saglik_raporu.txt", "")

her sunucu icinde sunucular:
    ping sure sunucu

    eger sure esittir -1:
        degisken durum = "ERİŞİLEMİYOR"
    degilse:
        eger sure kucuktur 300:
            degisken durum = "HIZLI"
        degilse:
            eger sure kucuktur 1000:
                degisken durum = "NORMAL"
            degilse:
                degisken durum = "YAVAŞ"
            son
        son
    son

    degisken satir = sunucu + " → " + durum + "\n"
    yazdır satir
    dosya_ekle("saglik_raporu.txt", satir)
son
```
*Puanlama: ping kontrolü 5p, hız sınıflandırması 5p, ekrana yazma 5p, dosyaya yazma 5p*
