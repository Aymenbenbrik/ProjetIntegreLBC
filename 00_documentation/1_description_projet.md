# Projet Intégré — Analyse et Prédiction du Churn Client

> **École** : ESPRIT School of Business
> **Programme** : Licence 3 : Business Computing BI
> **Tuteurs du projet** : Aymen Ben Brik et Hela Hammami
> **Année** : 2026

## 1. Contexte

Un établissement financier met à votre disposition un jeu de données anonymisé et généralisé décrivant des clients, leurs comptes et leurs produits. La fidélisation client (lutte contre l'attrition, ou *churn*) est un enjeu majeur du secteur : acquérir un nouveau client coûte plusieurs fois plus cher que d'en conserver un existant.

Votre mission est de concevoir, de bout en bout, une **solution décisionnelle complète** permettant de comprendre, mesurer et anticiper le churn, puis de mettre ces analyses à disposition des décideurs métier via une interface web.

## 2. Objectifs pédagogiques

Ce projet vous permet de mettre en pratique l'ensemble de la chaîne décisionnelle :

- Comprendre et qualifier des données (analyse univariée, valeurs manquantes, outliers).
- Concevoir un entrepôt de données et ses flux d'alimentation (modélisation dimensionnelle, ETL).
- Produire des indicateurs métier et des tableaux de bord avec Power BI et DAX.
- Modéliser l'évolution d'un KPI dans le temps (série temporelle, Deep Learning) et prédire le churn (Machine Learning).
- Concevoir et livrer une interface web documentée par des diagrammes UML.
- Travailler en équipe avec une démarche projet structurée (versioning, livrables, présentation).

## 3. Périmètre fonctionnel

Le projet est structuré en **cinq phases successives**. Chaque phase comporte un socle **obligatoire** et des **bonus** optionnels. Traitez toujours le socle obligatoire avant d'aborder un bonus.

| Phase | Intitulé | Échéance | Obligatoire | Bonus |
|--|---|--|-----|-----|
| 1 | Collecte et compréhension des données | Semaine du 9/11 | Analyse univariée ; décompte des outliers et des valeurs manquantes | Web scraping (Beautiful Soup, Playwright, Scrapy) ; analyse bivariée |
| 2 | Conception du DWH et ETL | Semaine du 16/11 | Talend + PostgreSQL administré avec pgAdmin | SSIS ; Databricks (bronze / silver / gold) ; SCD de type 2 ; Python |
| 3 | Reporting et dashboard | 23/11 | Power BI ; DAX pour les KPI | Visualisation avec Databricks ; interface JavaScript |
| 4 | Modèles prédictifs | 1/12 | Fixer un KPI ; analyse de sa série temporelle ; modèle de série temporelle en Deep Learning (LSTM / RNN) ; Machine Learning pour le churn | Traiter plusieurs KPI |
| 5 | Déploiement | 7/12 | Interface web ; diagrammes UML : cas d'utilisation global, une séquence, classes | DevOps : tests ; application mobile |

### 3.1 Phase 1 — Collecte et compréhension des données
- Charger les fichiers fournis et vérifier leur intégrité.
- Réaliser l'**analyse univariée** de chaque variable utile (distribution, tendance centrale, dispersion, modalités).
- Produire le **décompte des valeurs manquantes** et le **décompte des outliers** par variable, en précisant la méthode retenue (IQR, z-score, etc.).
- *Bonus* : enrichir le contexte par **web scraping** ; réaliser une **analyse bivariée**.

### 3.2 Phase 2 — Conception du DWH et ETL
- Concevoir un modèle dimensionnel en étoile (faits + dimensions) et justifier le grain.
- Implémenter les flux d'alimentation avec **Talend**.
- Créer et administrer l'entrepôt sous **PostgreSQL** avec **pgAdmin**.
- *Bonus* : version **SSIS** ; architecture **Databricks** en médaillon (bronze / silver / gold) ; historisation **SCD de type 2** ; traitements en **Python**.

### 3.3 Phase 3 — Reporting et dashboard
- Produire un rapport **Power BI** connecté à l'entrepôt.
- Écrire les KPI en **DAX** et permettre une exploration interactive (filtres, drill-down).
- Au minimum : vue d'ensemble, analyse du churn, segmentation client.
- *Bonus* : visualisation avec **Databricks** ; restitution dans une **interface JavaScript**.

### 3.4 Phase 4 — Modèles prédictifs
- **Fixer un KPI** et justifier son intérêt métier (exemple : nombre hebdomadaire de clôtures de comptes).
- Analyser sa **série temporelle** : tendance, saisonnalité, ruptures, pics.
- Construire un modèle de série temporelle en **Deep Learning (LSTM ou RNN)**, comparé à une référence simple.
- Construire un modèle de **Machine Learning** de prédiction du churn et l'évaluer avec des métriques adaptées.
- *Bonus* : appliquer la démarche à **plusieurs KPI**.

### 3.5 Phase 5 — Déploiement
- Développer une **interface web** exposant les prédictions et les indicateurs de synthèse.
- Livrer trois **diagrammes UML** : cas d'utilisation **global**, **une seule** séquence, classes.
- *Bonus* : démarche **DevOps** avec tests automatisés ; **application mobile**.

## 4. Livrables attendus

Trois livrables sont attendus à la fin du projet, en plus du rendu de chaque phase :

| Livrable | Format | Contenu attendu |
|---|---|---|
| **Code source** | Dépôt GitHub, sans aucune donnée | Notebooks, jobs Talend exportés, scripts SQL, mesures DAX, code ML, application web, diagrammes UML, README détaillé, instructions d'installation et d'exécution |
| **Présentation orale** | Slides (PPT/PDF), 20 min + 10 min de questions | Démonstration de l'application, présentation de la démarche, principaux résultats |
| **Rapport** | PDF, 25–40 pages | Document professionnel décrivant la démarche, l'architecture, les choix techniques, les résultats, les limites et les perspectives |

## 5. Modalités

- **Composition des équipes** : 3 à 4 étudiants par groupe.
- **Durée** : cinq jalons, de la semaine du 9/11 au 7/12/2026, à temps partagé avec les autres cours.
- **Encadrement** : un point d'avancement à chaque jalon avec les tuteurs.
- **Outils** : les outils marqués *obligatoire* sont imposés. Les autres restent libres dans le respect du guide étudiant (document 4).

## 6. Critères d'évaluation

| Critère | Pondération |
|---|---|
| Compréhension des données (analyse univariée, manquants, outliers) | 10 % |
| Qualité du DWH et de l'ETL (Talend, PostgreSQL) | 20 % |
| Pertinence du reporting (Power BI, DAX) | 15 % |
| Rigueur des modèles prédictifs (série temporelle, churn) | 25 % |
| Interface web et diagrammes UML | 15 % |
| Qualité du code, du rapport et de la présentation orale | 15 % |

Les **bonus** sont évalués en plus du socle et ne compensent pas une partie obligatoire absente.

## 7. Règles importantes

- **Confidentialité** : les données sont confidentielles et remises hors de GitHub. Aucune donnée, même partielle ou agrégée à la ligne, ne doit être publiée (dépôt, application, capture d'écran, modèle embarquant des lignes). Seul le code peut être partagé.
- **Non-réidentification** : toute tentative d'identifier l'établissement, une agence ou un client est **interdite**, y compris par recoupement ou web scraping. Si vous pensez reconnaître l'une de ces informations, n'en parlez pas dans vos livrables et prévenez immédiatement les tuteurs.
- **Anonymat** : ne formulez aucune hypothèse sur l'origine des données, ni dans le code, ni dans le rapport, ni dans la présentation.
- **Application publique** : l'interface déployée n'affiche que des agrégats et des profils fictifs. Toute liste de clients reste derrière une authentification et n'est jamais incluse dans le dépôt.
- **Versioning** : le dépôt GitHub doit montrer un historique régulier de commits par chaque membre de l'équipe.
- **Reproductibilité** : tout doit pouvoir être ré-exécuté par un tiers à partir du README.
