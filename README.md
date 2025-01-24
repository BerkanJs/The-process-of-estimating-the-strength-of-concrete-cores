### Name -- Data Type -- Measurement -- Description

- Cement (component 1) -- quantitative -- kg in a m3 mixture -- Input Variable

- Blast Furnace Slag (component 2) -- quantitative -- kg in a m3 mixture -- Input Variable

- Fly Ash (component 3) -- quantitative -- kg in a m3 mixture -- Input Variable

- Water (component 4) -- quantitative -- kg in a m3 mixture -- Input Variable

- Superplasticizer (component 5) -- quantitative -- kg in a m3 mixture -- Input Variable

- Coarse Aggregate (component 6) -- quantitative -- kg in a m3 mixture -- Input Variable

- Fine Aggregate (component 7) -- quantitative -- kg in a m3 mixture -- Input Variable

- Age -- quantitative -- Day (1~365) -- Input Variable

- Concrete compressive strength -- quantitative -- MPa -- Output Variable



### Source:
Original Owner and Donor
Prof. I-Cheng Yeh
Department of Information Management
Chung-Hua University,
Hsin Chu, Taiwan 30067, R.O.C.
e-mail:icyeh '@' chu.edu.tw
TEL:886-3-5186511

Date Donated: August 3, 2007

From: https://archive.ics.uci.edu/ml/datasets/Concrete+Compressive+Strength




1. İş Problemi 

•	Amaç: Beton karotlarının dayanımını tahmin etmek.

•	İş Modeli: Beton üretimindeki bileşenlerin (çimento, su, agregalar, katkı maddeleri vb.) miktarları ile betonun dayanımını (csMPa) ilişkilendirerek tahmin yapmak.

•	Sonuç: Dayanım tahminini doğru yapabilen bir model geliştirmek, beton üretiminde kaliteyi artırmaya ve maliyetleri optimize etmeye yardımcı olabilir.

2. Veri Anlaması

•	Veri Seti Boyutu: 1030 satır, sayısal verilerden oluşan 9 değişken içeriyor.

•	Değişkenler:

o	Girdi Değişkenleri: çimento, slag, flyash, su, süperplastikleştirici, kaba agregat, ince agregat, yaş (age)

o	Hedef Değişken: Beton dayanımı (csMPa)

•	Veri Durumu:

o	Veriler normal dağılımdan uzak ve çeşitli değişkenlerde sağa çarpıklık gözlemlenmiştir.

o	Aykırı değerler (outlier) bulunmakta, özellikle age ve csMPa değişkenlerinde bu durum dikkat çekmiştir.

•	Veri Temizliği ve Ön İşlemler:

o	Veri Dönüşümleri: Yeo-Johnson dönüşümü ile bazı değişkenlerde normal dağılıma yaklaşmaya çalışılmıştır ancak başarılı olamamıştır.

o	Ölçekleme: Veriler StandardScaler ve MinMaxScaler kullanılarak ölçeklendirilmiştir.

o	Aykırı Değerler: Aykırı değerler belirli ölçüde tespit edilse de, age ve csMPa değişkenlerinde bu durumu iyileştirmek zor olmuştur.

3. Veri Hazırlığı

•	Özellik Seçimi ve Dönüşümü: Verilerdeki bazı özellikler (özellikle age ve csMPa) çarpık ve uç değerlere sahip olduğu için dönüşüm ve normalizasyon yapılmıştır. Ancak bu değişkenlerdeki aykırı değerleri tamamen ortadan kaldırmak mümkün olmamıştır.

•	Veri Dönüşümü ve Standartlaştırma:

o	StandardScaler: Verilerin ortalama 0 ve standart sapma 1 olacak şekilde standardize edilmesi sağlanmıştır.

o	MinMaxScaler: Verilerin 0 ile 1 arasında normalize edilmesi yapılmıştır.

4. Modelleme

•	Model Seçimi:

o	Yapay Sinir Ağları MLP regresyon modeli ,

o	XGBoost (Extreme Gradient Boosting) regresyon modeli ,

o KNN Regressor modeli kullanılmıştır. Bu modeller, büyük veri setlerinde ve karmaşık ilişkilerde başarılı sonuçlar verir.

•	Hiperparametre Optimizasyonu: Modelin başarısını artırmak için Grid Search ile hiperparametre optimizasyonu yapılmıştır.

o	En İyi Parametreler:

	learning_rate: 0.2

	max_depth: 3

	n_estimators: 200

•	Model Performansı (Başlangıç Sonuçları):

o	RMSE: 0.2778

o	R²: 0.9165

o	MAE: 0.1809

o	MSE: 0.0772

•	Model Performansı (Hiperparametre Optimizasyonu Sonrası):

o	MSE: 0.0695

o	R²: 0.9247

6. Değerlendirme

•	Modelin Başarısı:

o	XGBoost modeli, R² skoru 0.92'nin üzerinde bir performans sergileyerek dayanım tahminlerinde oldukça başarılı sonuçlar elde etmiştir. Bu, modelin veriyi %92.47 oranında açıklayabildiğini gösterir.

o	MSE ve RMSE gibi hata metrikleri, modelin tahmin hatalarının düşük olduğunu ve genel performansının yüksek olduğunu göstermektedir.

•	Aykırı Değerlerin Etkisi: Aykırı değerler ve verilerin çarpıklığına rağmen, modelin sonuçları oldukça tatmin edicidir. XGBoost, özellikle aykırı değerlere karşı dayanıklı bir modeldir.

7. İş İçin Anlamı

•	Beton Dayanımının Tahmin Edilmesi:

o	Beton karotlarının dayanımını doğru tahmin etmek, üretim sürecindeki kalite kontrolünü iyileştirebilir. Bu, inşaat sektöründe daha dayanıklı ve güvenli yapılar inşa edilmesini sağlar.

o	Üretim sırasında hangi bileşenlerin betonun dayanımını daha fazla etkilediği analiz edilebilir, böylece daha verimli ve maliyet etkili bir beton üretimi sağlanabilir.

•	Verimlilik ve Maliyet:

o	Beton karotlarının dayanımını tahmin etmek, fazla çimento veya katkı maddesi kullanımını engelleyerek maliyetleri düşürmeye yardımcı olabilir.

o	Optimum malzeme kullanımı sayesinde çevresel etkiler de azaltılabilir.

8. Sonuç ve Öneriler

•	Sonuç: XGBoost modeli, beton dayanımını tahmin etmede oldukça başarılıdır. Hiperparametre optimizasyonu sonrası performans önemli ölçüde artmıştır. R² skoru 0.92'nin üzerine çıkmış ve modelin doğruluğu artmıştır.

•	Öneriler:

o	Modelin Genellemesi: Test verisi üzerinde modelin doğruluğu kontrol edilmelidir.

o	Alternatif Modeller: XGBoost dışında, karar ağaçları, rastgele ormanlar gibi alternatif modellerle karşılaştırma yapılabilir.

o	Veri Zenginleştirme: Veriye daha fazla özellik eklemek, modelin başarısını artırabilir.






