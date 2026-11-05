# 04 — Machine Learning

Placez ici les **modèles prédictifs** de la phase 4 :

- Le **KPI fixé**, sa justification et l'analyse de sa série temporelle.
- Le modèle de série temporelle en **Deep Learning (LSTM / RNN)**, comparé à une référence simple.
- Les notebooks de **Machine Learning pour le churn**.
- Le contrôle de la **fuite de cible** (voir `00_documentation/2_description_donnees.md`, section 5.1).
- Le tableau comparatif des modèles et l'interprétabilité (importance des variables, SHAP).
- *Bonus* : plusieurs KPI.

Les modèles sauvegardés restent **hors du dépôt** : certains peuvent contenir des données d'entraînement.

## Contenu minimum attendu

- **Série temporelle** : LSTM ou RNN évalué sur la fin de la série, avec MAE et RMSE, contre une prévision naïve.
- **Churn** : au moins 3 modèles comparés (par ex. : régression logistique, Random Forest, XGBoost).
- Métriques churn : precision, recall, F1, ROC-AUC, PR-AUC, avec un découpage par client.
- Justification du modèle final retenu.

## Structure suggérée

```
04_machine_learning/
├── notebooks/
│   ├── 01_kpi_serie_temporelle.ipynb
│   ├── 02_lstm_rnn.ipynb
│   └── 03_churn_ml.ipynb
├── src/
│   └── train.py
├── models/
│   └── model_final.pkl   # local uniquement, jamais commité
├── comparison.md         # tableau comparatif des modèles
└── README.md
```
