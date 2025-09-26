## Safety Helmet Detection (Bootcamp)

### Proje Özeti
Bu proje, inşaat sahalarında iş güvenliği için çalışanların kask (helmet) takıp takmadığını otomatik olarak tespit eden bir derin öğrenme modelinin geliştirilmesini amaçlamaktadır. Çalışma Kaggle ortamında geliştirilmiş olup GitHub üzerinde paylaşılmaktadır.

### Veri Seti
- **Kaynak:** Hard Hat Detection Dataset (Kaggle)  
- **Boyut:** ~5000 görsel (4581 helmet, 419 no_helmet)  
- **Format:** XML formatında anotasyonlar; görseller `images/` klasöründe  

### Yöntem ve Adımlar
- Veri Hazırlığı: XML → DataFrame, class weight hesaplama, stratified split  
- Data Augmentation: Rotation, flip, zoom, brightness (ImageDataGenerator)  
- Baseline CNN: L2 regularization + Dropout + class_weight  
- Performans Değerlendirme: Precision, Recall, F1-Score, Confusion Matrix  
- Transfer Learning: MobileNetV2 + üst katman eğitimi + fine-tuning  
- Grad-CAM: Modelin odaklandığı bölgelerin görselleştirilmesi  
- (Bonus) TensorBoard: `/kaggle/working/logs/` dizinine yazdırılarak eğitim sürecinin grafiklerle izlenmesi  

### Metrikler ve Sonuçlar
- Baseline Model: Macro F1 ≈ 0.21 (dengesiz veri nedeniyle düşük)  
- Transfer Learning Model: Macro F1 ≈ 0.88, Accuracy ≈ 95.8%  
- Helmet sınıfı: F1 ≈ 0.97  
- No_helmet sınıfı: F1 ≈ 0.78  
- Confusion Matrix: CSV olarak kaydedildi ve görselleştirildi  
- Grad-CAM: Modelin kask tespitinde kafa bölgesine odaklandığı doğrulandı  

### Nasıl Çalıştırılır?
- Kaggle’da GPU (T4) ile “Copy & Edit Notebook” → **Save & Run All** adımlarını izleyin.  
- Ortam: Python 3.10+, TensorFlow 2.x (Kaggle imajı yeterli).  
- Notebook’un tüm çıktıları ve markdown hücreleri görünürdür.  

### Sonuç ve Gelecek Çalışmalar
Bu model temel bir örnek olarak geliştirilmiştir. Daha büyük ve dengeli veri setleriyle yeniden eğitildiğinde performansı artabilir. İlerleyen süreçte basit bir kullanıcı arayüzü eklenerek proje genişletilebilir.

### Bağlantılar
- [Kaggle Notebook Linki](https://www.kaggle.com/code/ouzhanevci/safety-helmet-detection-bootcamp)
