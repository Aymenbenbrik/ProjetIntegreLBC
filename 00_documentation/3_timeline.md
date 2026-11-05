# Timeline du Projet — 5 Jalons

Le projet se déroule du **9/11 au 7/12/2026** et s'organise en **cinq phases**. Chaque phase se termine par un jalon qui correspond à un point de suivi avec les tuteurs. L'organisation interne reste libre, mais les échéances sont fermes.

## Vue d'ensemble

| Phase | Échéance | Objectif principal | Rendu du jalon |
|---|---|---|---|
| **1. Données** | Semaine du 9/11 | Comprendre et qualifier les données | Notebook d'analyse univariée + décompte des manquants et des outliers |
| **2. DWH / ETL** | Semaine du 16/11 | Concevoir et alimenter l'entrepôt | Modèle en étoile + jobs Talend + base PostgreSQL alimentée |
| **3. Reporting** | 23/11 | Restituer les KPI | Rapport Power BI + mesures DAX documentées |
| **4. Prédiction** | 1/12 | Prévoir un KPI et prédire le churn | KPI fixé + modèle LSTM/RNN + modèle de churn évalué |
| **5. Déploiement** | 7/12 | Livrer l'application | Interface web + diagrammes UML + rapport et présentation |

---

## Phase 1 — Collecte et compréhension des données (semaine du 9/11)

### À réaliser
- Constituer l'équipe, créer le dépôt GitHub sans données, préparer l'environnement.
- Charger les fichiers et comprendre le grain, les clés et les fichiers de référence.
- Définir le churn et le grain d'analyse.
- Réaliser l'**analyse univariée**.
- Produire le **décompte des valeurs manquantes** et des **outliers**.

### Bonus
- **Web scraping** avec Beautiful Soup, Playwright ou Scrapy.
- **Analyse bivariée**.

### Rendu
- Notebook documenté et tableau de synthèse par variable : type, % de manquants, nombre d'outliers, méthode, décision proposée.

---

## Phase 2 — Conception du DWH et ETL (semaine du 16/11)

### À réaliser
- Concevoir le modèle en étoile : faits, dimensions, grain, dimension temps.
- Créer le schéma sous **PostgreSQL** avec **pgAdmin**.
- Développer les jobs **Talend** : extraction, nettoyage, jointures, chargement.
- Contrôler la cohérence entre la source et l'entrepôt.

### Bonus
- **SSIS** ; **Databricks** en architecture bronze / silver / gold ; **SCD de type 2** ; **Python**.

### Rendu
- Diagramme en étoile, scripts SQL, jobs Talend exportés, requêtes de contrôle.

---

## Phase 3 — Reporting et dashboard (pour le 23/11)

### À réaliser
- Connecter **Power BI** à l'entrepôt.
- Écrire les KPI en **DAX**.
- Construire au moins trois pages : vue d'ensemble, analyse du churn, segmentation client.

### Bonus
- Visualisation avec **Databricks** ; **interface JavaScript**.

### Rendu
- Fichier `.pbix` remis aux tuteurs hors GitHub, captures sans ligne client et liste des mesures DAX documentées dans le dépôt.

---

## Phase 4 — Modèles prédictifs (pour le 1/12)

### À réaliser
- **Fixer un KPI** et construire sa série temporelle.
- **Analyser la série** : tendance, saisonnalité, pics, stationnarité.
- Entraîner un modèle **LSTM ou RNN** et le comparer à une référence simple.
- Entraîner et comparer des modèles de **Machine Learning** pour le churn, après contrôle de la fuite de cible.

### Bonus
- Appliquer la démarche à **plusieurs KPI**.

### Rendu
- Notebooks complets, modèles sauvegardés hors du dépôt et tableaux comparatifs.

---

## Phase 5 — Déploiement (pour le 7/12)

### À réaliser
- Développer et déployer l'**interface web**.
- Produire les **diagrammes UML** : cas d'utilisation global, une séquence, classes.
- Finaliser le rapport, les slides et le dépôt GitHub.

### Bonus
- **DevOps** : tests automatisés ; **application mobile**.

### Rendu
- URL de l'application, dépôt finalisé, rapport PDF (25–40 pages) et slides.

---

## Recommandations transverses

- **Traitez le socle d'abord** : un bonus ne remplace pas une partie obligatoire.
- **Commits réguliers** : chaque membre commit sur sa branche tout au long du projet.
- **Branches Git** : utilisez `main` pour le code stable et des branches `feature/...` par tâche.
- **Documentation au fil de l'eau** : rédigez le rapport à chaque jalon, pas à la fin.
- **Marge de déploiement** : la phase 4 et la phase 5 sont rapprochées. Testez un premier déploiement avant le 1/12.
