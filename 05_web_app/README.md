# 05 — Application Web

Placez ici le code de l'**interface web** et les instructions de déploiement.

## Fonctionnalités minimales attendues

1. **Prédiction individuelle** : un formulaire pour saisir un profil fictif et obtenir un score de churn.
2. **Prévision du KPI** : affichage de la prévision produite par le modèle LSTM/RNN.
3. **KPI de synthèse** : indicateurs agrégés affichés sur la page d'accueil.

## Diagrammes UML obligatoires

- Cas d'utilisation **global**.
- **Une seule** séquence.
- Classes.

Placez-les dans `docs/uml/`.

## Protection des données

L'application et son dépôt ne contiennent **aucune donnée** : ni ligne client, ni identifiant, ni export. Une liste de comptes à risque n'est permise que sur des profils fictifs ou derrière une authentification, sur un serveur non public.

## Bonus

- **DevOps** : tests automatisés et intégration continue.
- **Application mobile**.

## Déploiement

L'application doit être **déployée** et accessible aux tuteurs. L'URL doit figurer dans le README principal du projet.

Suggestions d'hébergement gratuit : Streamlit Community Cloud, Hugging Face Spaces, Render, Railway.

## Structure suggérée (Streamlit)

```
05_web_app/
├── app.py               # point d'entrée Streamlit
├── pages/               # pages additionnelles (Streamlit multi-pages)
├── utils/
│   ├── model.py         # chargement et inférence du modèle
│   └── preprocessing.py
├── assets/              # logos, captures
├── docs/uml/            # diagrammes UML
├── tests/               # bonus DevOps
├── requirements.txt     # dépendances spécifiques à l'app
├── DEPLOY.md            # procédure de déploiement
└── README.md
```
