# car-price-prediction-ivana

Predikcija cene polovnih automobila - opis projekta

Cilj projekta je razvoj modela mašinskog učenja za predviđanje cene polovnih automobila. Projekat obuhvata čišćenje podataka, dodavanje novih karakteristika, pretprocesiranje podataka, treniranje regresionih modela i njihovu evaluaciju i poređenje.

Na osnovu karakteristika automobila, kao što su godina proizvodnje, kilometraža, zapremina motora, gorivo, menjač i pogon, modeli pokušavaju da predvide cenu automobila u američkim dolarima.

Skup podataka

Projekat koristi skup podataka o automobilima koji sadrži podatke kao što su:

marka i model automobila;
cena u USD;
godina proizvodnje;
stanje automobila;
kilometraža;
tip goriva;
zapremina motora;
boja;
tip menjača;
pogonska jedinica;
segment automobila.

Tokom obrade podataka dodate su i nove karakteristike:
car_age – starost automobila;
mileage_per_year – prosečna kilometraža po godini;
engine_volume_liters – zapremina motora izražena u litrima.

Ciljna promenljiva je priceusd.

Struktura projekta

Projekat se sastoji od nekoliko skripti:
data_cleaning.py – čišćenje i standardizacija podataka;
feature_engineering.py – dodavanje novih karakteristika;
data_preprocessing.py – pretprocesiranje podataka;
model_training.py – treniranje prvog regresionog modela;
model_evaluation.py – evaluacija modela;
model_comparison.py – poređenje više regresionih algoritama.
Trenirani model se čuva u:
models/car_price_model.joblib

Kako se pokreće projekat
Potrebno je imati instaliran Python i biblioteke koje se koriste u projektu, kao što su pandas, scikit-learn i joblib.

Skripte se pokreću iz terminala, na primer:

python data_cleaning.py
python feature_engineering.py
python data_preprocessing.py
python model_training.py
python model_evaluation.py
python model_comparison.py


Pre pokretanja skripti potrebno je proveriti da su putanje do CSV fajlova ispravne.

Pretprocesiranje

Za numeričke karakteristike korišćeni su SimpleImputer i StandardScaler.
Za kategorijske karakteristike korišćeni su SimpleImputer i OneHotEncoder.

Na ovaj način nedostajuće vrednosti se obrađuju, numeričke karakteristike se standardizuju, a kategorijske vrednosti pretvaraju u format koji modeli mašinskog učenja mogu da koriste.

Testirani modeli:
U skripti model_comparison.py upoređena su četiri regresiona algoritma:
Linear Regression
Decision Tree
Random Forest
Gradient Boosting

Modeli su evaluirani pomoću sledećih metrika:
MAE – prosečna apsolutna greška predviđanja;
RMSE – koren srednje kvadratne greške, koji više kažnjava velike greške;
R² – pokazuje koliko model objašnjava varijaciju ciljne promenljive.

Rezultati:
Najbolje rezultate ostvario je Random Forest:
MAE = 1173.50 USD
RMSE = 2739.78 USD
R² = 0.8855
To znači da Random Forest u proseku greši oko 1173,50 USD pri predviđanju cene, dok R² vrednost pokazuje da model objašnjava približno 88,55% varijacije cena automobila.

Decision Tree
Decision Tree je ostvario drugi najbolji rezultat:
MAE = 1340.19 USD
RMSE = 3353.28 USD
R² = 0.8285
Model objašnjava oko 82,85% varijacije cena. U poređenju sa Random Forest modelom ima veće greške i manju R² vrednost.

Gradient Boosting
Gradient Boosting je zauzeo treće mesto:
MAE = 1690.80 USD
RMSE = 3351.80 USD
R² = 0.8287
R² vrednost je veoma slična rezultatu Decision Tree modela, ali Gradient Boosting ima veći MAE, što znači da u proseku pravi veće apsolutne greške.

Linear Regression
Linear Regression je takođe testiran kao osnovni regresioni model. Njegovi rezultati su korišćeni za poređenje sa složenijim modelima.

Izabrani model
Kao najbolji model izabran je Random Forest.
Random Forest je izabran zato što je ostvario:
najmanji MAE;najmanji RMSE;najveću R² vrednost među testiranim modelima.

Njegov rezultat pokazuje da najbolje predviđa cene automobila na test skupu od svih upoređenih modela. Zbog toga je Random Forest izabran kao konačni model projekta.

Zaključak

Projekat je obuhvatio kompletan osnovni proces mašinskog učenja: čišćenje podataka, feature engineering, pretprocesiranje, treniranje, evaluaciju i poređenje modela.

Od četiri testirana regresiona algoritma, Random Forest je ostvario najbolje rezultate, sa MAE od 1173,50 USD, RMSE od 2739,78 USD i R² od 0,8855. Na osnovu ovih rezultata izabran je kao najbolji model za predviđanje cena automobila.
