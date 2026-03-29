# T-Sharp (T#) Teknik Dokümantasyon ve Eğitim Rehberi

![Lisans](https://img.shields.io/badge/Lisans-GNU_AGPL_v3-red.svg)
![Sürüm](https://img.shields.io/badge/Sürüm-v4.1-blue.svg)
![Statü](https://img.shields.io/badge/Kapsam-Dokümantasyon-green.svg)
![Geliştirici](https://img.shields.io/badge/Geliştirici-Talha_Berk_Arslan-orange.svg)

---

## Dokümantasyon Hakkında

T-Sharp (T#) v4.1 ekosistemi, sadece bir dilden ibaret değil, aynı zamanda kapsamlı bir eğitim materyali setidir. Bu sayfa, dilin tüm yeteneklerini, modül yapılarını ve öğrenim sürecini destekleyen sınav/cevap anahtarı kaynaklarını listeler. TSharp, karmaşık Python kütüphanelerini Türkçe sözdizimi ile soyutlayarak, profesyonel projelerin ana dilde geliştirilmesine olanak tanır.

| Geliştirici | Katkı Oranı | Portfolyo |
| :--- | :---: | :--- |
| [**Talha Berk Arslan**](https://github.com/Codertalha5524) | %100 | Baş Geliştirici / Yazılım Mimarı |

---

## Teknik Modül Rehberi (Docs)

Aşağıdaki liste, TSharp'ın çekirdek yeteneklerini ve bu yeteneklerin hangi modüller üzerinden yönetildiğini açıklamaktadır.

### 01. Temel Kavramlar ve Algoritma
Değişken tanımlama, matematiksel işlemler, koşullu dallanmalar (eğer/ise) ve döngü yapılarını kapsar. TSharp'ın çekirdek yorumlayıcısının çalışma mantığı ve bellek yönetimi bu bölümde detaylandırılmıştır.

### 02. Dosya İşlemleri (I/O)
Yerel depolama birimleri üzerinde veri okuma, yazma, güncelleme ve silme (CRUD) operasyonlarını yönetir. Dosya sistemine erişim protokolleri ve veri güvenliği önlemleri anlatılır.

### 03. Ağ (Network) İşlemleri
HTTP protokolü üzerinden veri transferi, web servislerinden (API) veri çekme ve veri çekme operasyonlarını içerir. Özellikle internet üzerindeki bir URL'den görsel çekme mekanizması bu modülün bir parçasıdır.

### 04. Şifreleme ve Hash (Kriptografi)
Veri güvenliği ve bütünlüğü için kullanılan Hashlib ve HMAC altyapısını açıklar. SHA256, MD5 ve SHA512 gibi algoritmaların TSharp syntax yapısı ile nasıl entegre edileceğini öğretir. Sabit zamanlı karşılaştırma teknikleri ile güvenlik standartları vurgulanır.

### 05. Tkinter GUI (Giriş Seviyesi Arayüz)
Hızlı prototipleme ve hafif siklet masaüstü uygulamaları için sunulan görsel arayüz modülüdür. Standart form bileşenleri ve mesaj kutularının yönetimini kapsar.

### 06. PySide6 GUI (Profesyonel Arayüz)
Qt6 mimarisi üzerine kurulu, modern ve yüksek performanslı arayüz geliştirme rehberidir. Karmaşık widget yapıları, yerleşim yönetimi ve sinyal-slot mekanizmalarını içerir.

### 07. Pygame (Oyun ve Multimedya)
2D oyun geliştirme, ses yönetimi, koordinat düzlemi işlemleri ve çarpışma algoritmalarını kapsayan modüldür. Grafik işlem birimi ile yazılım arasındaki bağı açıklar.

### 08. Raspberry Pi ve GPIO (Donanım Kontrolü)
TSharp'ın fiziksel dünya ile etkileşime girdiği donanım katmanıdır. Sensör verisi okuma, motor kontrolü ve GPIO pin yönetimi ile IoT (Nesnelerin İnterneti) projelerinin kurgulanmasını anlatır.

---

## Eğitim Kaynakları ve Sınav Sistematiği

Öğrenim sürecini pekiştirmek amacıyla her modül için özel sınavlar ve PDF formatında cevap anahtarları sunulmaktadır.

| Konu Başlığı | Sınav Materyali | Cevap Anahtarı | Format |
| :--- | :--- | :--- | :---: |
| Temel Kavramlar | [Sınav Görüntüle](./Eğitim-Kaynakları/01_TEMEL_KAVRAMLAR_SINAV.md) | [Cevapları Gör](./Eğitim-Kaynakları/01_TEMEL_KAVRAMLAR_CEVAP.md) | MD / PDF |
| Dosya İşlemleri | [Sınav Görüntüle](./Eğitim-Kaynakları/02_DOSYA_ISLEMLERI_SINAV.md) | [Cevapları Gör](./Eğitim-Kaynakları/02_DOSYA_ISLEMLERI_CEVAP.md) | MD / PDF |
| Ağ İşlemleri | [Sınav Görüntüle](./Eğitim-Kaynakları/03_AG_ISLEMLERI_SINAV.md) | [Cevapları Gör](./Eğitim-Kaynakları/03_AG_ISLEMLERI_CEVAP.md) | MD / PDF |
| Şifreleme ve Hash | [Sınav Görüntüle](./Eğitim-Kaynakları/04_SIFRELE_HASH_SINAV.md) | [Cevapları Gör](./Eğitim-Kaynakları/04_SIFRELE_HASH_CEVAP.md) | MD / PDF |
| Tkinter GUI | [Sınav Görüntüle](./Eğitim-Kaynakları/05_TKINTER_GUI_SINAV.md) | [Cevapları Gör](./Eğitim-Kaynakları/05_TKINTER_GUI_CEVAP.md) | MD / PDF |
| PySide6 GUI | [Sınav Görüntüle](./Eğitim-Kaynakları/06_PYSIDE6_GUI_SINAV.md) | [Cevapları Gör](./Eğitim-Kaynakları/06_PYSIDE6_GUI_CEVAP.md) | MD / PDF |
| Pygame | [Sınav Görüntüle](./Eğitim-Kaynakları/07_PYGAME_SINAV.md) | [Cevapları Gör](./Eğitim-Kaynakları/07_PYGAME_CEVAP.md) | MD / PDF |
| Raspberry Pi GPIO | [Sınav Görüntüle](./Eğitim-Kaynakları/08_RASPBERRYPI_GPIO_SINAV.md) | [Cevapları Gör](./Eğitim-Kaynakları/08_RASPBERRYPI_GPIO_CEVAP.md) | MD / PDF |

---

## Derleme ve Dağıtım: TCompile

TSharp projeleri, dökümantasyonda anlatılan tüm modüllerle birlikte **TCompile** (PyInstaller tabanlı) teknolojisi kullanılarak tek bir dosyaya derlenebilir. Bu, eğitim sonunda ortaya çıkan projelerin gerçek bir yazılım ürünü olarak dağıtılabilmesini sağlar.

1. **Taşınabilirlik:** Hiçbir Python kurulumu gerektirmeden çalışabilen .exe veya ELF çıktıları.
2. **Kütüphane Entegrasyonu:** PySide6, Requests ve Pygame gibi bileşenlerin otomatik paketlenmesi.
3. **Güvenlik:** Kaynak kodun korunması ve binary formatta dağıtım.

---

## Lisans Bilgisi

Bu dokümantasyon ve beraberindeki tüm kod kaynakları **GNU Affero General Public License v3.0 (AGPL-3.0)** altında korunmaktadır. 

Bu lisans, özgür yazılımın gücünü internet üzerinden sunulan servislerde de korumayı amaçlar. Yazılımı veya dokümantasyonu geliştirerek kullanan tüm taraflar, bu değişiklikleri topluluğa geri kazandırmakla yükümlüdür.

---
**T-Sharp: Teknolojiyi kendi dilinde anlayanların, geleceği kendi elleriyle inşa etmesi için.**
