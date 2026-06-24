# UrbanFlow AI: Büyük Veri Destekli Taksi Talebi Tahmini ve ROI Optimizasyonu

UrbanFlow AI, New York sarı taksi yolculuk verilerini, taksi bölge sözlüğü ve saatlik hava durumu verisiyle birleştirerek bölge-saat düzeyinde yüksek taksi talebi tahmini yapan büyük veri destekli bir veri bilimi projesidir.

Projenin amacı yalnızca yüksek doğruluk oranına sahip bir makine öğrenmesi modeli geliştirmek değil, model çıktısını operasyonel ve finansal bir karar destek mekanizmasına dönüştürmektir. Modelin ürettiği yüksek talep tahminleri, taksi işletmesi için ek araç yönlendirme kararı olarak yorumlanmış ve farklı karar eşikleri için net fayda ve ROI hesaplanmıştır.

## Proje Kapsamı

Bu projede aşağıdaki adımlar uygulanmıştır:

* NYC Yellow Taxi Trip Data, Taxi Zone Lookup ve saatlik hava durumu verilerinin birleştirilmesi
* Spark Connect ile büyük veri işleme süreci
* HDFS üzerinde Bronze, Silver ve Gold veri katmanlarının oluşturulması
* Gold veri setinin Hive External Table olarak kaydedilmesi
* Bölge-saat bazında yüksek talep sınıflandırması
* İş mantığına dayalı feature engineering
* Logistic Regression, Random Forest ve HistGradientBoosting modellerinin karşılaştırılması
* Time-based validation ile Ocak 2024 eğitim, Şubat 2024 test doğrulaması
* SHAP ile model açıklanabilirliği
* ROI ve threshold optimizasyonu
* Kafka alarm simülasyonu

## Kullanılan Veri Kaynakları

* NYC Yellow Taxi Trip Data
* Taxi Zone Lookup
* NYC Historical Weather Data

## Kullanılan Teknolojiler

* Python
* PySpark / Spark Connect
* HDFS
* Hive
* Kafka
* Pandas
* Scikit-learn
* SHAP
* Matplotlib

## Model Sonuçları

En iyi model HistGradientBoostingClassifier olmuştur.

Random train-test split sonuçları:

* Accuracy: 0.9907
* Precision: 0.9474
* Recall: 0.9583
* F1-score: 0.9529
* ROC-AUC: 0.9992

Time-based validation sonuçları:

* Accuracy: 0.9890
* Precision: 0.9451
* Recall: 0.9482
* F1-score: 0.9466
* ROC-AUC: 0.9989

## Finansal Simülasyon

Model çıktıları, taksi işletmesi için ek araç yönlendirme kararına dönüştürülmüştür. Farklı threshold değerleri test edilmiş ve en yüksek ROI değeri 0.75 karar eşiğinde elde edilmiştir.

* En iyi threshold: 0.75
* Net fayda: 307.705
* ROI: 3.122

## Açıklanabilir Yapay Zeka

SHAP analizi sonucunda modelin kararlarında en etkili değişkenlerin geçmiş talep göstergeleri olduğu görülmüştür. Özellikle son 1 saatteki talep, önceki gün aynı saatteki talep, 24 saatlik hareketli ortalama ve saat bilgisi yüksek talep tahminlerinde belirleyici rol oynamıştır.

## Proje Yapısı

```text
UrbanFlow_AI_Final_Teslim/
│
├── proje_aciklamali_ciktili.ipynb
├── veri_kaynaklari.txt
├── data/
│   └── raw/
├── figures/
│   ├── eda_hourly_demand.png
│   ├── eda_top_zones.png
│   ├── xai_shap_summary.png
│   └── roi_threshold_curve.png
└── model_outputs/
    ├── model_comparison.csv
    ├── roi_threshold_optimization.csv
    ├── time_based_validation_metrics.csv
    └── management_summary.json
```

## Sonuç

UrbanFlow AI, veri harmanlama, büyük veri işleme, makine öğrenmesi, açıklanabilir yapay zeka ve finansal simülasyonu birleştiren uçtan uca bir veri bilimi projesidir. Proje, taksi talebi tahminini yalnızca teknik bir sınıflandırma problemi olarak değil, işletme açısından ölçülebilir finansal değer üreten bir karar destek sistemi olarak ele almaktadır.
