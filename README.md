# 🚚 Mini-Dump: ESP32 Controlled RC Dump Truck

Bu proje, ESP32 mikrodenetleyici kullanılarak geliştirilmiş, çok fonksiyonlu bir uzaktan kumandalı mini çöp kamyonu (Mini-Dump) projesidir. Proje; **PS3 Kolu**, **Web Arayüzü (Wi-Fi)** ve **Modern Gamepadler (Bluepad32)** ile kontrol edilebilen esnek bir yazılım altyapısına sahiptir.

## ✨ Öne Çıkan Özellikler
* **Çoklu Kontrol Desteği:** PS3 DualShock 3, Web Tarayıcı ve Bluepad32 uyumlu tüm kollar (PS4, PS5, Xbox).
* **Hassas Sürüş:** Diferansiyel sürüş sistemi ve Servo motorlu direksiyon kontrolü.
* **Fonksiyonel Mekanizma:** Damper kaldırma/indirme ve aydınlatma sistemleri.
* **Web Arayüzü:** ESP32 üzerinden yayınlanan özelleştirilmiş HTML5 kontrol paneli.

## 🛠️ Donanım Yapılandırması (Pinout)

Sistemdeki bileşenlerin ESP32 üzerindeki bağlantı noktaları şöyledir:

| Bileşen | Pin No | Fonksiyon |
| :--- | :--- | :--- |
| **Direksiyon Servosu** | 23 | Ön tekerlek yön kontrolü |
| **Yardımcı Servo** | 22 | Ekstra mekanizma kontrolü |
| **Sol Motor (L0/L1)** | 33, 32 | Sol motor ileri/geri PWM |
| **Sağ Motor (R0/R1)** | 21, 19 | Sağ motor ileri/geri PWM |
| **Damper (Aux 2/3)** | 18, 17 | Boşaltma mekanizması çıkışları |
| **Işıklar (Aux 0/1)** | 25, 26 | Kabin ve dış aydınlatma |

## 🕹️ Kontrol Modları

### 1. PS3 Controller (`MiniDump_PS3_Controller.ino`)
* **Sol Analog:** Hız ve İleri/Geri (Throttle).
* **Sağ Analog:** Direksiyon (Steering).
* **D-Pad Up/Down:** Damper mekanizmasını hareket ettirir.
* **R3 Butonu:** Araç ışıklarını açar/kapatır.

### 2. Wi-Fi Web Panel (`MiniDump_wifi2.0.ino`)
ESP32 **"MegaDump"** adında bir Wi-Fi ağı oluşturur. `192.168.4.1` adresine girerek şu kontrollere erişebilirsiniz:
* Dokunmatik sliderlar ile hız ve yön yönetimi.
* Web üzerinden "Trim" ayarı ile direksiyon kalibrasyonu.
* Işık ve Damper butonları.

### 3. Evrensel Gamepad (`MiniDump_Bluepad2.0.ino`)
Bluepad32 kütüphanesi sayesinde modern oyun kollarını destekler. 
* **L1 / R1:** Direksiyon ince ayarı (Trim).
* **D-Pad:** Damper yatağı kontrolü.

## 🚀 Kurulum ve Kullanım

1.  **Kütüphaneleri Yükleyin:** * Arduino IDE'ye `Ps3Controller`, `ESP32Servo`, `Bluepad32` ve `ESPAsyncWebSrv` kütüphanelerini ekleyin.
2.  **Kart Seçimi:** `Tools > Board > ESP32 Dev Module` seçeneğini belirleyin.
3.  **Yükleme:** Hangi kontrol modunu kullanmak istiyorsanız ilgili `.ino` dosyasını ESP32'ye yükleyin.
4.  **Eşleştirme (PS3 için):** `Ps3.begin("8c:7c:b5:fc:3b:39")` satırındaki MAC adresini kendi kolunuzun adresiyle güncelleyin.

## 📂 Dosya Yapısı
* `MiniDump_wifi2.0.ino`: Web server ana kodları.
* `HTML.ino`: Web arayüzü tasarımı (PROGMEM).
* `MiniDump_PS3_Controller.ino`: PS3 Bluetooth bağlantı mantığı.
* `MiniDump_Bluepad2.0.ino`: Modern gamepad destek katmanı.

---
*Bu proje akademik/hobi amaçlı geliştirilmiş olup, tüm donanım ve yazılım hakları saklıdır.*
