# Proiect 1 - Seoul Bike Sharing

ITSchool - Machine Learning. [Date UCI](https://archive.ics.uci.edu/dataset/560/seoul+bike+sharing+demand), CC BY 4.0: 8.760 ore, 14 coloane, 01.12.2017-30.11.2018; fără valori lipsă. Ținta este `Rented Bike Count`. Notebook: `proiect.ipynb`; date: `SeoulBikeData.csv`. 

1. **Ce problemă și ce eroare costă?** Regresie: estimăm închirierile pe oră. Subestimarea poate duce la insuficiența bicicletelor disponibile; costurile reale nu sunt incluse în date. Zero-urile din orele fără funcționare sunt valide.
2. **De ce split înainte de scalare?** Pentru a exclude statisticile testului din învățare. Train cronologic: 7.008 ore până pe 18.09.2018; test: ultimele 1.752 ore. Pipeline învață imputarea și one-hot pe train; standardizăm numerele pentru OLS, fără ca aceasta să fie obligatorie.
3. **Ce scor are baseline-ul?** DummyRegressor prezice mediana train, 449. MAE este 537.26 închirieri/oră; mediană aleasă pentru metrica absolută.
4. **Care model și de ce?** Regresia liniară are MAE 235.14, față de 308.35 la pădure. Relațiile aditive pot generaliza mai bine pe această perioadă; complexitatea mai mare nu garantează performanță superioară.
5. **De ce MAE?** Arată eroarea medie în închirieri/oră. Raportăm și RMSE, sensibilă la erori mari, și R². Predicțiile sunt limitate la minimum zero, fără rotunjire înainte de evaluare.
6. **Recomandare și limitare:** Regresia liniară în această comparație; MAE scade cu 302.13 închirieri/oră (56.23%) față de baseline. Limitări: un an, test de toamnă, vreme observată și lipsa unei evaluări independente după alegerea modelului.

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| DummyRegressor | 537.26 | 686.32 | -0.252 |
| Regresie liniară | 235.14 | 327.38 | 0.715 |
| Random Forest | 308.35 | 435.28 | 0.496 |

**Utilizarea AI:**

- Am folosit AI pentru explicații despre cod, modele și metrici.
