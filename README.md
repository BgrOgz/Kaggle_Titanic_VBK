# Kaggle_Titanic_VBK Bugra Oguz
 Titanic veri setinde hayatta kalma tahmini — veri analizi, görselleştirme ve Logistic Regression modeli ile sınıflandırma.
# 🚢 Titanic Hayatta Kalma Tahmini – Logistic Regression ile Makine Öğrenmesi Uygulaması

### 🎯 Proje Amacı  
Amaç, **Kaggle’ın klasik Titanic veri seti** üzerinden yolcuların hayatta kalma durumunu makine öğrenmesi modelleriyle tahmin etmektir.  
Projeyi yaparken veri analizi, görselleştirme ve model kurma adımlarını baştan sona öğrenmek hedeflenmiştir.  
Bu çalışma, hem **Python veri bilimi araçlarını öğrenme** hem de **makine öğrenmesine giriş** niteliğindedir.

---

### 🧠 Veri Seti Hakkında
Titanic veri seti, 1912 yılında batan Titanic gemisindeki yolculara ait demografik bilgileri içerir.  
Her satır bir yolcuyu temsil eder ve modelin tahmin etmesi gereken hedef değişken **"Survived" (hayatta kalma durumu)** sütunudur.

| Sütun | Açıklama |
|--------|-----------|
| **PassengerId** | Yolcu kimlik numarası |
| **Survived** | 0 = Hayatta kalmadı, 1 = Hayatta kaldı |
| **Pclass** | Bilet sınıfı (1 = 1. sınıf, 3 = 3. sınıf) |
| **Name** | Yolcunun adı |
| **Sex** | Cinsiyet |
| **Age** | Yaş |
| **SibSp** | Gemideki kardeş/eş sayısı |
| **Parch** | Gemideki ebeveyn/çocuk sayısı |
| **Ticket** | Bilet numarası |
| **Fare** | Bilet ücreti |
| **Cabin** | Kabin numarası |
| **Embarked** | Biniş limanı (C = Cherbourg, Q = Queenstown, S = Southampton) |

---

### 📊 1. Keşifsel Veri Analizi (EDA)
Projenin ilk aşamasında veri seti incelenmiş, veri türleri ve eksik değerler analiz edilmiştir.

Yapılan adımlar:
- `data.info()` ve `data.describe()` ile veri yapısının incelenmesi  
- Eksik değerlerin (`Age`, `Cabin`, `Embarked`) tespiti  
- Sayısal değişkenlerin ortalama, medyan, min ve max değerlerinin çıkarılması  
- Cinsiyet, bilet sınıfı ve biniş limanlarının dağılım grafikleri (`countplot`)  
- Yaş dağılımı (`histplot`) ve korelasyon ısı haritası (`heatmap`)

Bu aşamada **verinin yapısını anlamak** ve **ön işleme süreci için strateji belirlemek** hedeflendi.

---

### 🧹 2. Veri Ön İşleme
Modelin doğru çalışabilmesi için verideki eksik veya kategorik alanlar düzenlendi:
- `Age` ve `Fare` sütunlarındaki eksikler **medyan değerle dolduruldu**.  
- `Embarked` sütunundaki boş alanlar **“U” (Unknown)** olarak tanımlandı.  
- `Sex` ve `Embarked` sütunları **LabelEncoder** kullanılarak sayısal değerlere dönüştürüldü.  
- Kullanılmayan sütunlar (`Name`, `Ticket`, `Cabin`, `PassengerId`) kaldırıldı.

Bu adımlar sayesinde modelin öğrenebileceği **temiz ve sayısal** bir veri kümesi oluşturuldu.

---

### 🤖 3. Modelleme: Logistic Regression
Bu proje için **Logistic Regression** modeli seçilmiştir çünkü:
- Problem **ikili sınıflandırma (binary classification)** problemidir: 0 veya 1  
- Logistic Regression, **olası sonuçları (probabilistic)** tahmin edebilir  
- Yeni başlayanlar için **anlaşılması kolay** ve **yorumlanabilir** bir modeldir  

Modelleme süreci:
```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, precision_score, recall_score

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
model = LogisticRegression(max_iter=1000)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

**Model Performansı:**
| Metrik | Değer |
|---------|--------|
| Accuracy | 0.78 |
| Precision | 0.74 |
| Recall | 0.70 |

Bu sonuçlar, modelin verideki genel örüntüleri iyi yakaladığını göstermektedir.

---

### 📈 4. Sonuçların Yorumlanması
- Kadın yolcuların hayatta kalma oranı erkeklere göre çok daha yüksektir.  
- 1. sınıfta seyahat eden yolcuların kurtulma ihtimali yüksektir.  
- Genç yolcuların (özellikle çocukların) hayatta kalma oranı daha fazladır.  
- Bilet ücreti arttıkça hayatta kalma ihtimali de artmaktadır.  

**Genel Değerlendirme:**  
Bu proje sayesinde veri ön işleme, görselleştirme ve modelleme konularında temel bir anlayış kazanıldı.  
Logistic Regression modeli, veri bilimi projelerine giriş için uygun bir başlangıç modelidir.

---

### 💡 5. Öğrenilenler ve Geliştirme Fikirleri
Bu çalışmada:
- Pandas ile veri okuma, düzenleme ve analiz yapma  
- Seaborn & Matplotlib ile veri görselleştirme  
- Scikit-learn ile model kurma ve metrik değerlendirmesi  
adımları uygulandı.

Geliştirme önerileri:
- **RandomForest** veya **XGBoost** gibi daha güçlü modeller denenebilir  
- **Feature engineering** ile yeni sütunlar üretilebilir (örneğin “Aile Büyüklüğü”, “Title”)  
- Modelin genellenebilirliğini artırmak için **cross-validation** kullanılabilir  

---

### 👨‍💻 Hazırlayan
**Buğra Oğuz**  

💼 Proje:  Titanic Survival Prediction  


---
