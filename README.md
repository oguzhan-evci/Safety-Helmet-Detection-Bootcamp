# Safety Helmet Detection (Bootcamp)

## Proje Özeti  
Bu proje, inşaat sahalarında iş güvenliği için çalışanların kask (helmet) takıp takmadığını otomatik olarak tespit eden bir derin öğrenme modelinin geliştirilmesini amaçlamaktadır. Çalışma Kaggle ortamında geliştirilmiş olup, GitHub üzerinde README.md dosyası ve notebook bağlantısı ile birlikte sunulmuştur.

## Hedefler  
- İş güvenliği denetimini otomatikleştirmek  
- Dengesiz veri setlerinde (helmet vs. no_helmet) yüksek F1-Score elde etmek  
- Transfer Learning ve Grad-CAM ile model performansını ve yorumlanabilirliğini artırmak  
- TensorBoard entegrasyonu ile eğitim sürecini canlı takip etmek  

## Veri Seti  
- Kaynak: Hard Hat Detection Dataset (Kaggle)  
- Boyut: ~5000 görsel (4581 helmet, 419 no_helmet)  
- Format: XML formatında anotasyonlar; görseller `images/` klasöründe  

## Yöntem ve Adımlar  
- Veri Hazırlığı: XML → DataFrame dönüşümü, class weight hesaplama, stratified split  
- Data Augmentation: Rotation, flip, zoom, brightness (RAM dostu ImageDataGenerator)  
- Baseline CNN: L2 regularization + Dropout + class_weight  
- Performans Değerlendirme: Precision, Recall, F1-Score, Confusion Matrix (hem text hem DataFrame/heatmap)  
- Transfer Learning: MobileNetV2 + üst katman eğitimi + fine-tuning  
- Grad-CAM: Modelin odaklandığı bölgelerin görselleştirilmesi (2×2 ve 2×4 grid)  
- Demo / İnferans: Tüm tahminlerin CSV çıktısı + örnek Grad-CAM grid  
- TensorBoard: `/kaggle/working/logs/` dizinine yazdırılarak eğitim sürecinin grafiklerle izlenmesi  

## Sonuçlar  
- Baseline Model: Macro F1 ≈ 0.21 (dengesiz veri nedeniyle düşük)  
- Transfer Learning Model: Macro F1 ≈ 0.88, Accuracy ≈ 95.8%  
- Helmet sınıfı: F1 ≈ 0.97  
- No_helmet sınıfı: F1 ≈ 0.78  
- Confusion Matrix: Her iki sınıf için doğru/yanlış tahminlerin görsel tablosu üretildi ve CSV olarak kaydedildi  
- Grad-CAM: Modelin kask tespitinde kafa bölgesine odaklandığı doğrulandı  
- TensorBoard: Eğitim sırasında loss/accuracy grafiklerini interaktif olarak inceleme imkânı sağlandı  

## Önemli Çıktılar  
- `/kaggle/working/demo_predictions.csv`  
- `/kaggle/working/demo_mistakes.csv`  
- `/kaggle/working/confusion_matrix.csv` ve `/kaggle/working/confusion_matrix_tl.csv`  
- `/kaggle/working/gradcam_grid_*_TALL.png`  
- `/kaggle/working/demo_grid_2x2_BIG.png`  

## Notebook Linki  
Projenin Kaggle Notebook’una buradan ulaşabilirsiniz:  
[Safety Helmet Detection (Bootcamp) Kaggle Notebook](https://www.kaggle.com/code/ouzhanevci/safety-helmet-detection-bootcamp)  

## Geliştirme Önerisi  
Model daha büyük ve dengeli bir veri setiyle tekrar eğitilerek daha yüksek performans elde edilebilir.
