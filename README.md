# EuroSAT-Classification-Project
Akbank Derin Öğrenme Bootcamp Projesi: EuroSAT Veri Seti ile Görüntü Sınıflandırması
# Akbank Derin Öğrenme Bootcamp Projesi: EuroSAT Arazi Görüntüleri Sınıflandırma

Bu proje, Akbank & Global AI Hub iş birliğiyle düzenlenen Derin Öğrenme Bootcamp'i kapsamında hazırlanmıştır. Projede, EuroSAT uydu görüntüleri veri seti kullanılarak arazi kullanımı sınıflandırması yapan derin öğrenme modelleri geliştirilmiş ve karşılaştırılmıştır.

## Projenin Amacı
Projenin temel amacı, sıfırdan bir Evrişimli Sinir Ağı (CNN) modeli ile Transfer Learning yaklaşımını (MobileNetV2) kullanarak çok sınıflı bir görüntü sınıflandırma problemini çözmek, bu iki modelin performansını karşılaştırmak ve model yorumlanabilirliği tekniklerini uygulamaktır.

## Veri Seti
Projede **EuroSAT** veri seti kullanılmıştır.
- Veri seti, Sentinel-2 uydusundan alınmış görüntülerden oluşur.
- Toplam 10 farklı sınıf içerir: `AnnualCrop`, `Forest`, `HerbaceousVegetation`, `Highway`, `Industrial`, `Pasture`, `PermanentCrop`, `Residential`, `River`, `SeaLake`.
- Toplam 27,000 adet 64x64 piksel boyutunda görüntü bulunmaktadır.
- Veri setine [bu linkten](https://www.kaggle.com/datasets/apollo2506/eurosat-dataset) ulaşılabilir.

## Kullanılan Yöntemler
- **Veri Ön İşleme:** Görüntülerin 0-1 arasına ölçeklendirilmesi ve `ImageDataGenerator` ile okunması.
- **Veri Çoğaltma (Data Augmentation):** Overfitting'i önlemek amacıyla eğitim verisine döndürme, yakınlaştırma, kaydırma gibi teknikler uygulanmıştır.
- **Özel CNN Mimarisi:** `Conv2D`, `MaxPooling2D`, `Dropout` ve `Dense` katmanlarından oluşan temel bir CNN modeli oluşturulmuştur.
- **Transfer Learning:** ImageNet üzerinde önceden eğitilmiş `MobileNetV2` modeli, temel katmanları dondurularak kullanılmıştır.
- **Model Değerlendirmesi:** Modellerin performansı Doğruluk/Kayıp Grafikleri, Sınıflandırma Raporu ve Karışıklık Matrisi ile ölçülmüştür.
- **Model Yorumlanabilirliği:** Modelin karar mekanizmasını anlamak için **Grad-CAM** tekniği ile ısı haritaları oluşturulmuştur.

## Elde Edilen Sonuçlar
İki farklı model geliştirilmiş ve performansları karşılaştırılmıştır:
- **Özel CNN Modeli:** Doğrulama seti üzerinde **%81.28** doğruluk elde etmiştir.
- **Transfer Learning Modeli:** Doğrulama seti üzerinde **%91.56** doğruluk elde etmiştir.

Sonuç olarak, Transfer Learning yaklaşımının bu problem için daha az eğitim süresiyle daha yüksek bir başarı oranı sunduğu ve daha verimli olduğu tespit edilmiştir. Grad-CAM analizleri de Transfer Learning modelinin, ilgili sınıfa ait nesnelere daha doğru odaklandığını göstermiştir.

## Kaggle Notebook
Projenin tüm kodlarını ve çıktılarını içeren Kaggle Notebook'una aşağıdaki linkten ulaşabilirsiniz:

**https://www.kaggle.com/code/mrvdmrc/arazisiniflandirmasi**
