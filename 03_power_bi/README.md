# 03 — Power BI

Placez ici les livrables Power BI :

- Le fichier `.pbix` : **jamais dans le dépôt**, il est remis aux tuteurs hors GitHub.
- Des captures d'écran des pages du rapport, sans ligne client.
- La documentation des KPI et des mesures **DAX** (obligatoire).

## Contenu minimum attendu

Au moins **3 pages** dans le rapport Power BI :
1. **Vue d'ensemble** — KPIs clés, taux de churn global.
2. **Analyse du churn** — segmentation par âge, secteur, ancienneté, produit.
3. **Segmentation client** — profils et valeur client.

*Bonus* : visualisation avec Databricks ; interface JavaScript.

## Structure suggérée

```
03_power_bi/
├── rapport.pbix         # local uniquement, NE JAMAIS COMMITER
├── screenshots/
│   ├── page1_overview.png
│   ├── page2_churn.png
│   └── page3_segments.png
├── measures_dax.md      # documentation des mesures
└── README.md
```
