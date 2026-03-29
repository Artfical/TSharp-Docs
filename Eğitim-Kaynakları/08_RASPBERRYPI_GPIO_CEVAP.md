# T-Sharp (T#) — Raspberry Pi GPIO Sınavı
## CEVAP ANAHTARI

---

### Soru 1 — (5 puan)
**Cevap: b) BCM (Broadcom) pin numaraları**

---

### Soru 2 — (5 puan)
**Cevap: b) HIGH (1)**  
Pull-up direnci pini 3.3V'a çeker. Butona basılmadığında bağlantı kesilir ve pin HIGH okunur. Butona basılınca GND'ye kısa devre olur, LOW okunur.

---

### Soru 3 — (5 puan)
**Komut:** `gpio_baslat` — `lgpio chip 0`'ı açar.  
**Neden kapatılmalı:** `gpio_kapat` çağrılmazsa pin kilitleri açık kalır; bir sonraki çalıştırmada sorun çıkabilir ve pinler istenmeyen durumda kalabilir.

---

### Soru 4 — (5 puan)
- `duty_cycle = 0` → Pin **sürekli kapalı** (0V)  
- `duty_cycle = 100` → Pin **sürekli açık** (3.3V)  
- `duty_cycle = 50` → Pin zamanın yarısında açık, yarısında kapalı → **yarı güç** (ortalama 1.65V)

---

### Soru 5 — (10 puan)
**Hata:** `gpio_baslat` çağrılmamış. GPIO komutları öncesinde sistem başlatılmalıdır.

**Düzeltilmiş hali:**
```tsharp
gpio_baslat
gpio_mod 17 cikis
gpio_yaz 17 dogru
bekleme(2)
gpio_yaz 17 yanlis
gpio_kapat
```

---

### Soru 6 — (10 puan)
**Sorun:** Giriş pinine pull-up veya pull-down direnci eklenmemiş. Butona bağlı olmayan veya açık pin "floating" (havada) kalır ve parazit nedeniyle rastgele 0 ya da 1 okuyabilir.

**Düzeltilmiş hali:**
```tsharp
gpio_baslat
gpio_mod 18 giris
gpio_asagi_cek 18

degisken oyun_devam = dogru
dongu oyun_devam:
    gpio_oku 18 deger
    eger deger esittir 1:
        yazdır "Butona basıldı!"
    son
son
```

---

### Soru 7 — (10 puan)
```tsharp
gpio_baslat
gpio_mod 17 cikis

degisken i = 0
dongu i kucuktur 5:
    gpio_yaz 17 dogru
    bekleme(0.5)
    gpio_yaz 17 yanlis
    bekleme(0.5)
    i += 1
son

gpio_kapat
yazdır "LED yanıp sönme tamamlandı."
```

---

### Soru 8 — (10 puan)
```tsharp
gpio_baslat
gpio_mod 17 cikis
gpio_mod 18 giris
gpio_asagi_cek 18

degisken calisiyor = dogru
dongu calisiyor:
    gpio_oku 18 buton
    eger buton esittir 1:
        gpio_yaz 17 dogru
    degilse:
        gpio_yaz 17 yanlis
    son
son

gpio_kapat
```

---

### Soru 9 — (20 puan)
```tsharp
gpio_baslat
pwm_baslat 12 1000 0

degisken devam = dogru
dongu devam:
    girdi prl_metin "Parlaklık (0-100, çıkmak için q): "

    eger prl_metin esittir "q":
        degisken devam = yanlis
    degilse:
        degisken prl = sayiya(prl_metin)
        eger prl kucuk_esit 0:
            prl = 0
        son
        eger prl buyuktur 100:
            prl = 100
        son
        pwm_ayarla 12 prl
        yazdır "Parlaklık ayarlandı:" prl
    son
son

pwm_durdur 12
gpio_kapat
yazdır "Program sonlandı."
```
*Puanlama: PWM başlatma 5p, döngü ve girdi 5p, sınır kontrolü 5p, temiz kapatma 5p*

---

### Soru 10 — (20 puan)
```tsharp
gpio_baslat
i2c_baslat 0x48

yazdır "Sensör okunuyor..."

degisken sayac = 0
dongu sayac kucuktur 100:
    i2c_kayit_oku 0x00 2 sensor_veri
    degisken log_satiri = "Okuma " + yaziya(sayac + 1) + ": " + yaziya(sensor_veri) + "\n"

    yazdır log_satiri
    dosya_ekle("sensor_log.txt", log_satiri)

    bekleme(5)
    sayac += 1
son

i2c_kapat
gpio_kapat
yazdır "Program sonlandı, bağlantılar kapatıldı."
```
*Not: T#'da try/except desteklenmediğinden sonsuz döngü yerine sonlu sayaç kullanılmıştır. `dongu dogru:` ile yazılırsa da kabul edilir.*  
*Puanlama: I2C bağlantısı 5p, kayıt okuma 5p, dosyaya loglama 5p, temiz kapatma 5p*
