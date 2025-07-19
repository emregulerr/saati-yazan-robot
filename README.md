# Arduino ile Saat Yazan Robot (PlotClock) 🕚

2019 yılı Mayıs ayında yaptığım bu proje; servo motorlarla kontrol edilen bir robot kolun, üzerine bağlı bir kalem aracılığıyla mevcut saati küçük bir yazı tahtasına yazması prensibine dayanır.

![Projenin Çalışma Anı](https://i.imgur.com/O6tCg4N.gif)
*(Öneri: `demo.mov` videonuzu bir GIF'e dönüştürüp bu şekilde ekleyebilir veya YouTube'a yükleyip bağlantısını paylaşabilirsiniz.)*

---

## 📜 Proje Hakkında

Bu projenin temel amacı, Arduino ve servo motorlar kullanarak zamanı fiziksel olarak yazabilen bir çizim robotu (plotter) oluşturmaktır. Robot kol, iki ana servo motor ile X ve Y eksenlerinde hareket ederken, üçüncü bir servo motor kalemi kağıda indirme ve kaldırma işlevini yerine getirir.

Arduino içerisindeki kod, `TimeLib.h` kütüphanesi aracılığıyla zamanı takip eder. Belirlenen her dakika, robot kol eski saati siler ve yeni saati yazar. Kolun hassas hareketleri, servo motorların doğru açılarla konumlandırılması için gereken **ters kinematik hesaplamalarına** dayanmaktadır.

---

## 🛠️ Kullanılan Malzemeler ve Teknolojiler

### Donanım
* **Mikrodenetleyici:** Arduino UNO (veya benzeri)
* **Motorlar:** 3 adet Tower Pro SG90 Mikro Servo Motor
* **Güç Kaynağı:** Harici 5V Adaptör (Servo motorların akım ihtiyacını karşılamak için)
* **Gövde:** 3D yazıcı ile basılmış robot kol ve gövde parçaları
* **Diğer:** Mini yazı tahtası, silinebilir tahta kalemi, Jumper kablolar

### Yazılım ve Kütüphaneler
* **Platform:** Arduino IDE
* **Kütüphaneler:**
    * `Servo.h`: Servo motorları kontrol etmek için.
    * `TimeLib.h`: Zaman bilgisini yönetmek için.

---

## ⚙️ Kurulum ve Çalıştırma

1.  **Montaj:** Projenin 3D model dosyalarını kullanarak parçaları basın ve servo motorlarla birlikte montajı tamamlayın.
2.  **Devre Bağlantısı:** Servo motorları ve güç kaynağını şemaya uygun olarak Arduino'ya bağlayın.
3.  **Kodu Yükleme:** `sketch_may12a.ino` dosyasını Arduino IDE ile açın ve kartınıza yükleyin. Kod, başlangıçta seri monitör üzerinden mevcut saati girmenizi isteyecektir.
4.  **Çalıştırma:** Kodu yükledikten sonra robot kol kendini kalibre edecek ve ayarlanan saati yazmaya başlayacaktır.

---

## 🔬 Karşılaşılan Sorunlar ve Geliştirme Önerileri

### Karşılaşılan Sorunlar
* **Güç Yönetimi:** Prototip aşamasında pillerin 3 servo motoru aynı anda çalıştırmak için yetersiz kaldığı gözlemlenmiştir. Bu sorun, harici bir 5V adaptöre geçilerek çözülmüştür.
* **RTC Modülü Entegrasyonu:** Başlangıçta zamanı otomatik olarak almak için bir RTC (Gerçek Zamanlı Saat) modülü kullanılması hedeflenmiş, ancak kütüphane uyumluluğu ve entegrasyon zorlukları nedeniyle bu özellikten vazgeçilmiştir. Mevcut sistem, başlangıçta saatin manuel olarak ayarlanmasını gerektirmektedir.

### Geliştirme Önerileri
* **Mekanik Stabilite ve Yazı Kalitesinin Artırılması:**
    * **Donanım:** Daha hassas ve torku yüksek dijital veya metal dişli servolar kullanarak titreşimi (jitter) ve mekanik boşluğu (backlash) azaltmak. Robot kol parçalarını daha sert malzemelerle (örneğin PETG, ABS veya alüminyum) üreterek mekanik esnemeyi en aza indirmek.
    * **Yazılım:** Rakamların kavisli kısımlarını daha pürüzsüz çizmek için doğrusal interpolasyon yerine Bezier eğrileri gibi algoritmalar kullanmak. Hareket başlangıç ve bitişlerine ivmelenme/yavaşlama (easing) profilleri ekleyerek daha akıcı çizimler elde etmek.

* **Stabil RTC Entegrasyonu:** Projeye daha stabil çalışan bir RTC modülü (örneğin DS3231) entegre edilerek saatin manuel ayarlanma ihtiyacı ortadan kaldırılabilir.

* **PCB Tasarımı:** Jumper kablolar yerine projeye özel bir PCB (Baskı Devre Kartı) tasarlanarak daha stabil ve güvenilir bir elektronik devre yapısı oluşturulabilir.

* **Silme Mekanizmasının İyileştirilmesi:** Yazıyı silme işlemi için daha verimli ve temiz sonuç veren bir mekanizma (örneğin keçeli özel bir silgi parçası) geliştirilebilir.

* **Kablosuz Kontrol:** Projeye bir Bluetooth (HC-05) veya Wi-Fi (ESP8266) modülü eklenerek saat ayarının bir mobil uygulama veya web arayüzü üzerinden kablosuz olarak yapılması sağlanabilir.

---

## 📚 Kaynaklar ve Referanslar

Bu projenin geliştirilmesinde aşağıdaki kaynaklardan ilham alınmıştır:
* [Thingiverse - Plotclock by joo](https://www.thingiverse.com/thing:248009)
* [Instructables - Plot Clock for Dummies](https://www.instructables.com/id/Plot-Clock-for-dummies/)
* [Proje Hocam - Arduino Saati Yazan Kol](https://www.projehocam.com/arduino-saati-yazan-kol-plotclock/)
