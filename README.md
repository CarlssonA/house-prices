# House Prices - Advanced Regression Project #
*Ein Machine-Leaning-Projekt mit Feature Engineering, Modellvergleich, SHAP-Interpretation und Residuenanalyse.*

### **1. Projektübersicht** ###

Dieses Projekt analysiert den bekannten *Hose Prices-Datensatz* von Kaggle und entwickelt ein Regressionsmodell zur Vorhersage von Immobilienpreisen. Das Projekt umfasst:
- Explorative Datenanalyse (EDA)
- Systematische Feature Engineering
- Vergleich von Gradient-Boosting-Modelle
- Modellinterpretation mit SHAP
- Residuenanalyse
- Finales Modell (CatBoost)

### **2. Datensatz** ###

Der verwendete Datensatz besteht aus:
1. **train.csv**: enthält Features und Zielvariable **SalePrice**
2. **test.csv**: enthält nur Features
FÜr das Portfolio-Projekt wird ausschließlich der Train-Datensatz verwendet, das nur dieser Labels enthält und somit EDA, Modelltraining und Residuenanalyse ermöglicht

### **3. Vorgehensweise** ###
1. Explorative Datenanalyse
   - Verteilung der Zielvariable
   - Korrelation zwischen numerischen Features
   - Analyse wichtiger Qualitäts- und Flächenmerkmale
   - Identifikation von Ausreißern und fehlenden Werten
2. Feature Engineering
Folgende neue Features wurdene rstellt, um die Modellleistung zu verbessern:
   - **TotalSF** - Gesamtwohnfläche
   - **HouseAge** - Alter des Hauses
   - **RemodAge**  - Zeit seit letzter Renovierung
   - **QualityIndex** - Kombination aus OverallQual * OverallCond 
   - **TotalBath** - Gesamtanzahl der Bäder
   - **PorchSF** - gesamte Porch-Fläche
   - **GarageScore** - GarageCars * GarageArea
Diese Features basieren auf Domain-Wissen und Kaggle-Best Practices.
3. Preprocessing
   - Imputation fehlender Werte
   - One-Hot-Encoding kategorialer Variablen
   - Log-Transformation der Zielvariable
   - Train/Test-Split

### **4. Modellierung** ###

Verglichene Modelle
- XGBoost
- LightGBM
- CatBoost

| Modell | RMSE | R² |
|--------|-------|------|
| XGBoost | 0.1249 | 0.9012 |
| LightGBM | 0.1327 | 0.8886 |
| CatBoost | 0.1214 | 0.9067 |

### **5. Modellinterpretation (SHAP)** ### 

Mit SHAP wurden die wichtigsten Einflussfaktoren identifiziert:
- **GrLivArea** - Wohnfläche
- **OverallQual** - Bauqualität
- **TotalBsmtSF** - Kellerfläche
- **1stFlrSF** - Fläche des Erdgeschosses
- **YearRemodAdd** - Renovierungsjahr

Die SHAP-Plots zeigen, dass hohe Qualität, große Fläche und neue Häuser für einen höheren Preis stehen.

### **6. Residuenanalyse** ###
- keine systematischen Verzerrungen
- leichte Streuung bei hohen Preisen 
- Residuen sind nicht normalverteilt
- Modell ist gut kalibriert und generalisiert stabil

### **7. Finales Modell**
Das finale Modell ist ein CatBoostRegressor mit optimierten Hyperparametern und wurde gespeichert unter: models/catboost_final_model.cbm

