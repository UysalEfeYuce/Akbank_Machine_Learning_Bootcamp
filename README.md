

# Giriş
Bu projede 2020 yılına ait ve eksik değer içermeyen bir kalp hastalığı veri seti kullandım. Amacım, bireylerin kalp hastalığı riski taşıyıp taşımadığını makine öğrenimi modelleriyle tahmin etmekti. Ana model olarak XGBoost algoritmasını tercih ettim. Veri setinde sayısal ve kategorik değişkenler olduğu için uygun ön işleme adımları uyguladım. Binary ve çok kategorili sütunlara label encoding işlemi uyguladım.

Veri dengesizliği problemi nedeniyle SMOTE yöntemiyle azınlık sınıfı örneklerini artırmayı denedim. Ancak bu yöntem modelin performansında beklediğim iyileşmeyi sağlamadı. Aksine, özellikle F1-score ve genel doğruluk gibi metriklerde düşüşe neden olduğunu gözlemledim. Bu nedenle SMOTE yöntemi bu proje özelinde etkili bir çözüm sunmadı.

# Metrikler
Farklı makine öğrenmesi modellerini karşılaştırdım ve aşağıdaki sonuçları elde ettim:

| Model                  | Cross-Validation Accuracy | Test Accuracy |
|------------------------|---------------------------|---------------|
| Gradient Boosting      | 0.9155                    | 0.9142        |
| AdaBoost               | 0.9148                    | 0.9130        |
| SVC                    | 0.9144                    | 0.9131        |
| Logistic Regression    | 0.9142                    | 0.9142        |
| XGBoost                | 0.9129                    | 0.9117        |
| KNN                    | 0.9072                    | 0.9040        |
| Decision Tree          | 0.8636                    | 0.8609        |
| Naive Bayes            | 0.8463                    | 0.8407        |


Accuracy değerleri oldukça yakın olmasına rağmen XGBoost modelini tercih ettim. Çünkü Pozitif sınıf için  daha yüksek recall değeri sağladı.Veri setim dengesiz olduğu için recall accuracyden daha kritik bir metrikti.
Sonra SMOTE kullanmadan Sınıflandırma Raporu aldım sonuçlar aşağıdaki gibi

SMOTE öncesi test set skoru: 0.38


              precision    recall  f1-score   support
           0       0.96      0.86      0.91     18263
           1       0.29      0.57      0.38      1737

    accuracy                           0.84     20000



Bir de SMOTE kullandığım sınıfladırma raporuna bakalım

SMOTE sonrası test set skoru: 0.26


              precision    recall  f1-score   support
           0       0.93      0.93      0.93     18263
           1       0.26      0.27      0.26      1737

    accuracy                           0.87     20000



Sınıflandırma raporlarını karşılaştırdığımda SMOTE’un modeli zayıflattığını gördüm. Bu yüzden en sonunda  SMOTE kullanmamaya karar verdim.
Amacım pozitif sınıfı kaçırmamak olduğu için recallın düşmesi benim için kritik bir eksiydi.

# Sonuç ve Gelecek Çalışmalar

Kalp hastalığı riskini tahmin etmeye yönelik bir makine öğrenmesi sistemi geliştirdim. Veri seti üzerinde  ön işleme adımları uyguladım ve XGBoost gibi güçlü bir model kullanarak sınıflandırma işlemlerini gerçekleştirdim. Ayrıca veri dengesizliği problemini çözmek amacıyla SMOTE tekniğini denedim. Ancak bu yöntemin her zaman metriklerde iyileşme sağlamadığını ve bazı durumlarda performansı olumsuz etkileyebildiğini gözlemledim. Bu da bana, dengesiz veri probleminin yalnızca yeniden örnekleme ile değil, daha gelişmiş modelleme teknikleriyle de ele alınması gerektiğini gösterdi.

İlerleyen süreçte modelimi daha dengeli ve daha doğru tahminler yapabilecek hale getirmeyi hedefliyorum. Bunun için daha güncel ve detaylı veri setleri kullanmayı düşünüyorum.


# Link
https://www.kaggle.com/code/uysalefeyuce/akbank-bootcamp-proje
