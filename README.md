# car_price_prediction_with_random_forest_regressor
Predicting car prices using real data with Random Forest Regressor

# Avtomobil Qiymət Proqnozu (Random Forest)

# Layihənin qısa təsviri
Bu layihə avtomobillərin xüsusiyyətlərinə əsaslanaraq onların bazar qiymətini proqnozlaşdırır. 
İstifadə edilən xüsusiyyətlərə mühərrik gücü, buraxılış ili, yürüş, marka, model, ban növü, sürətlər qutusu, rəng və mühərrik yanacağı daxildir. 
Proqnoz **Random Forest Regressor** modeli ilə aparılır və hyperparameter tuning ilə dəqiqliyi artırılır.

---

## Dataset
- Layihədə Turbo.az saytından toplanmış məlumatlar istifadə olunub.  
- Datasetdə avtomobil elanlarına aid mühərrik göstəriciləri, yürüş, model, ban növü, sürətlər qutusu, rəng, yanacaq növü və qiymət mövcuddur.  
- İstifadə olunan CSV fayllar:  
  - `turbo_az_20_pages_full_data.csv` – modelin öyrədilməsi üçün  
  - `turbo_az_10_pages_full_data.csv` – test üçün

---

## İş prosesi (Workflow)

1. **Məlumatların təmizlənməsi və preprocessing**  
   - Missing dəyərlər moda əsasən dolduruldu.  
   - Mühərrik sütunu üç hissəyə ayrıldı: mühərrik həcmi, gücü və yanacaq növü.  
   - Yürüş və qiymət sütunları rəqəmlərə çevrildi.  
   - Kateqorial dəyişənlər `LabelEncoder` ilə kodlaşdırıldı.

2. **Xüsusiyyətlərin seçimi (Feature Selection)**  
   - Seçilmiş xüsusiyyətlər: `Mühərrik gücü(a.g)`, `Buraxılış ili`, `Marka`, `Yürüş(km)`, `Mühərrik həcmi(L)`, `Model`, `Ban növü`, `Sürətlər qutusu`, `Rəng`, `Mühərrik yanacağı`.

3. **Modelin öyrədilməsi (Model Training)**  
   - Random Forest Regressor istifadə edildi.  
   - Hyperparameter tuning üçün `RandomizedSearchCV` tətbiq olundu.

4. **Proqnozlaşdırma (Prediction)**  
   - Öyrədilmiş model test datasetində avtomobil qiymətlərini proqnozlaşdırır.

---

## Modelin hyperparametrləri

RandomizedSearchCV ilə aşağıdakı parametrlər optimallaşdırıldı:  
- `n_estimators`  
- `max_depth`  
- `max_features`  
- `min_samples_split`  
- `min_samples_leaf`  
- `bootstrap`  

  - Web tətbiqi şəklində real vaxt qiymət proqnozu təqdim etmək

