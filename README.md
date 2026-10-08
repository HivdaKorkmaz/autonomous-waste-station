# ♻️ Akıllı Otonom Atık Ayrıştırma İstasyonu (Smart Waste Sorting Station)

Bu depo, bilgisayarlı görü (YOLOv8) ve gömülü sistemler (Arduino) kullanılarak geliştirilmiş, gerçek zamanlı çalışan tam otonom bir atık ayrıştırma prototipinin kaynak kodlarını içermektedir. Lisans Bitirme Tezi kapsamında geliştirilmiştir.

## 🚀 Proje Özeti
Geleneksel atık yönetimindeki biyolojik riskleri ve sınıflandırma maliyetlerini kaynağında çözmek amacıyla geliştirilen bu sistem; atıkları (Tıbbi Atık, Plastik, Cam, Metal, Kağıt) kameradan gerçek zamanlı olarak algılar ve otonom servo motorlar yardımıyla doğru hazneye yönlendirir.

## ✨ Temel Özellikler
* **Özgün Veri Seti:** Çevresel koşullar (ışık, deformasyon, açı) simüle edilerek sıfırdan hazırlanan 2701 görsellik özel atık veri seti (Roboflow).
* **Gerçek Zamanlı Tespit:** YOLOv8n mimarisi ile 21 ms gecikme süresi (~47 FPS) ve %90 F1-Skoru doğruluğu.
* **Donanım Kararlılığı:** Sensör yanılmalarını ve motor titremelerini %100 engelleyen özgün "20 Karelik İstikrar Filtresi (Debounce Logic)".
* **Yazılım-Donanım Entegrasyonu:** Python üzerinden Arduino Uno'ya UART (Seri Port) ile milisaniyelik komut aktarımı ve servo motor kontrolü.
* **Asenkron Arayüz (GUI):** Multithreading destekli PyQt6 masaüstü uygulaması, canlı sayaçlar ve anlık `.csv` veri loglama özelliği.

## 🛠️ Kullanılan Teknolojiler
* **Yapay Zeka & Görüntü İşleme:** Python, YOLOv8, OpenCV
* **Gömülü Sistem (Donanım):** Arduino Uno, C++, Servo Motorlar (SG90/MG996R)
* **Arayüz (GUI):** PyQt6
* **Veri Seti Yönetimi:** Roboflow

## ⚙️ Nasıl Çalışır?
1. Web kamerası, atık haznesine giren nesnenin görüntüsünü anlık olarak alır.
2. Arka planda koşan YOLOv8 modeli nesnenin türünü ve güven skorunu tespit eder.
3. Tespit edilen nesne, "İstikrar Filtresi"nden geçerek kararlılığı doğrulanır.
4. Python, seri port üzerinden Arduino'ya hedeflenen atık sınıfının sinyalini gönderir.
5. Arduino sinyali işler, ilgili servo motoru tetikler ve atık doğru kutuya düşer.
