# Description des Données

Les données mises à votre disposition sont issues d'un système d'information bancaire. Elles ont été **anonymisées et généralisées** : identifiants aléatoires, libellés neutres, regroupements, dates et montants arrondis. Elles conservent leur cohérence d'ensemble, mais ne décrivent plus aucune personne ni aucun site de façon exploitable.

> **À retenir** : les dates ont été volontairement **décalées** et les montants **arrondis et plafonnés**. Ils ne doivent pas être rapprochés d'un calendrier ou d'une source externe. Raisonnez sur des durées, des évolutions et des ordres de grandeur.

## 1. Vue d'ensemble

Le jeu de données est composé de :

- **1 fichier principal** `data_churn.csv` (~75 Mo, 483 536 lignes, 32 colonnes) ;
- **5 fichiers de référence** au format Excel (`.xlsx`) qui donnent le libellé associé aux codes du fichier principal.

Il décrit 363 024 clients et 410 309 comptes. Une ligne correspond à un **rapprochement client / compte / produit** : un client ou un compte peut donc apparaître plusieurs fois, et environ 9 % des lignes correspondent à des clients sans compte renseigné. Définissez clairement votre grain avant tout calcul.

Pour les plus gros clients, le nombre de lignes a été plafonné à 100. **Les totaux ne représentent donc pas un encours réel** : utilisez-les pour comparer, pas comme des montants absolus.

## 2. Fichier principal — Description des colonnes

### 2.1 Identifiants
| Colonne | Type | Description |
|-----|---|---------|
| `CUSTOMER_NO` | Code (`K…`) | Identifiant aléatoire du client |
| `ACCOUNT_NO` | Code (`X…`) | Identifiant aléatoire du compte |
| `BRANCH_GROUP` | Code (`AG01` à `AG20`) | Regroupement anonyme d'agences, sans signification géographique. `AG00` = masqué |

### 2.2 Informations client
| Colonne | Type | Description |
|-----|---|---------|
| `NATIONALITY_REGION` | Texte | Zone de nationalité : `LOCAL`, `EUROPE`, `AFRIQUE_MO`, `AMERIQUES`, `ASIE_OCEANIE`, `AUTRE` |
| `RESIDENCE_REGION` | Texte | Zone de résidence (mêmes modalités) |
| `MARITAL_STATUS` | Code | Statut marital (C = célibataire, M = marié(e), D = divorcé(e), V = veuf/veuve) |
| `BIRTH_PERIOD` | Année | Début de la tranche de naissance de 5 ans (`1980` = 1980–1984). Dernière tranche basse : `1935` et avant |
| `CUST_OPENING_DATE` | Date (YYYYMMDD) | Entrée en relation : début de trimestre, d'année ou de période de 5 ans selon le client |
| `NATURE_CLIENT` | Code | Type de client : `PPH` (personne physique), `PM` (personne morale), `PRO` (professionnel), `TRPP` et `TRPM` (autres catégories) |
| `PARTYCLASS` | Texte | Classe commerciale : `Retail`, `Premium`, `Corporate Small`, `Corporate` |
| `LOB` | Code | Ligne métier (FK vers `TARGET.xlsx`) |
| `SCORE_KYC` | Code | Score de connaissance client (Know Your Customer) |
| `COMPLETED_FILE` | YES / vide | Dossier client complet |
| `LAST_REVIEW_DATE` | Date (YYYYMMDD) | Dernière revue du dossier, ramenée au mois |
| `NEXT__REVIEW_DATE` | Date (YYYYMMDD) | Prochaine revue prévue, ramenée au mois |
| `INDUSTRY` | Code (A à Z) | Section d'activité (FK vers `INDUSTRY.xlsx`) |
| `SALARY` | Numérique | Revenu déclaré, arrondi à 1 chiffre significatif et plafonné |

### 2.3 Informations compte
| Colonne | Type | Description |
|-----|---|---------|
| `ACCOUNT_STATUS` | Texte | `Active` ou `Closed` — **base de la variable cible** |
| `ACCT_OPENING_DATE` | Date (YYYYMMDD) | Ouverture du compte, ramenée au lundi de la semaine |
| `ACCT_CLOSE_DATE` | Date (YYYYMMDD) | Clôture du compte, ramenée au lundi de la semaine |
| `ACCOUNT_CATEGORY` | Code (`CAT…`) | Famille de comptes (FK vers `ACCOUNT_CATEGORY.xlsx`) |
| `ACCOUNT_TYPE_DESC` | Texte | Libellé de la famille de comptes |
| `CURRENCY` | Code | Devise (FK vers `CURRENCY.xlsx`) |
| `CLOSURE_REASON` | Code (`RSN…`) | Motif de clôture (FK vers `CLOSURE_REASON.xlsx`) |
| `ACCT_BALANCE` | Numérique | Solde arrondi à 2 chiffres significatifs et plafonné |

### 2.4 Informations produit
| Colonne | Type | Description |
|-----|---|---------|
| `PRODUCT_GROUP` | Texte | Groupe de produits générique |
| `PRODUCT_LINE` | Texte | Ligne de produits |
| `STARTDATE` | Date (YYYYMMDD) | Début du produit, ramené au mois |
| `MATURITYDATE` | Date (YYYYMMDD) | Échéance, ramenée au mois |
| `AMOUNT` | Numérique | Montant du produit, arrondi à 2 chiffres significatifs et plafonné |
| `FIXEDRATE` | Numérique | Taux fixe, arrondi au demi-point |
| `PRODUCT_STATUS` | Texte | Statut du produit |

## 3. Fichiers de référence

| Fichier | Clé | Contenu |
|------|---|-------|
| `ACCOUNT_CATEGORY.xlsx` | `CATEGORY_ID` | Familles de comptes |
| `CLOSURE_REASON.xlsx` | `REASON_ID` | Motifs de clôture |
| `CURRENCY.xlsx` | `CURRENCY_CODE` | Devises (`LCY` = monnaie locale, `LCC` = monnaie locale convertible) |
| `INDUSTRY.xlsx` | `INDUSTRY_CODE` | Sections d'activité |
| `TARGET.xlsx` | `TARGET_CODE` | Lignes métier |

Le calendrier n'est pas fourni : il est à construire vous-même.

## 4. Définition de la variable cible (churn)

Le **churn** se définit ici comme la **clôture d'un compte** :

```
churn = 1  si  ACCOUNT_STATUS = "Closed"
churn = 0  si  ACCOUNT_STATUS = "Active"
ligne exclue si ACCOUNT_STATUS est vide
```

Une définition plus fine est possible (par exemple : churn d'un client = clôture de **tous** ses comptes), à justifier dans le rapport. Le taux dépend fortement du grain : environ **40 %** des lignes, **36 %** des comptes et **32 %** des clients. Le déséquilibre reste donc modéré : vérifiez-le et justifiez toute technique de rééquilibrage.

## 5. Variables pour la prédiction

### 5.1 Attention à la fuite de cible

Le fichier est une **photographie** prise après les clôtures : certaines colonnes révèlent le résultat au lieu de le prédire. **À ne pas utiliser comme variables explicatives** :

- `ACCT_CLOSE_DATE` et `CLOSURE_REASON` : renseignées uniquement pour les comptes clos.
- `ACCT_BALANCE` **et sa valeur manquante** : le solde est vide pour environ 68 % des comptes clos et n'est jamais vide pour les comptes actifs. Toute variable dérivée de ce vide trahit la cible.
- La famille de compte, la devise et le montant : leur disponibilité peut suivre le même schéma, à contrôler.
- `PRODUCT_STATUS` : certaines modalités correspondent à la fermeture.

Un score proche de 100 % signale presque toujours une fuite, pas un bon modèle. Le rapport doit présenter ce contrôle.

### 5.2 Pistes de variables

- **Démographiques** : tranche d'âge, statut marital, zone de nationalité ou de résidence.
- **Ancienneté** : ancienneté du client et du compte, à calculer depuis leurs dates d'ouverture.
- **Comportementales** : nombre de comptes par client, diversité des produits, secteur, segment commercial.
- **Conformité** : score KYC, dossier complet, ancienneté de la dernière revue.

## 6. Séries temporelles — points d'attention

`ACCT_CLOSE_DATE` et `ACCT_OPENING_DATE` permettent de construire des séries **hebdomadaires**. La granularité mensuelle ne suffit pas : la période de clôtures couvre environ 47 mois, soit trop peu de points pour un LSTM.

- La série des clôtures compte environ **200 semaines**, dont une dizaine sans aucune clôture : ces semaines valent **0** et doivent être ajoutées.
- **Cinq semaines concentrent environ la moitié des clôtures** : ce sont des opérations de masse. Elles doivent être identifiées et traitées (variable d'intervention, série corrigée, modèle robuste), puis ce choix doit être justifié.
- Comptez la série au grain **compte** après déduplication, sinon les lignes multiples la déforment.
- Le découpage entraînement / test doit **respecter l'ordre du temps**. Aucun mélange aléatoire.

## 7. Qualité des données

Le jeu conserve des défauts à traiter dans vos phases d'analyse et d'ETL :

- **Valeurs manquantes** nombreuses : plus de 85 % sur `MATURITYDATE`, `FIXEDRATE`, `STARTDATE`, `PRODUCT_STATUS` ; environ 70 % sur `SALARY`. Certains vides sont **volontaires** et viennent de l'anonymisation.
- **Doublons** : plusieurs milliers de lignes strictement identiques, et bien plus au grain compte.
- **Dates numériques** au format `YYYYMMDD` à convertir. La précision de `CUST_OPENING_DATE` varie selon les clients.
- **Soldes négatifs** et **montants extrêmes** : environ 32 % des soldes sortent des bornes IQR. Les comptes débiteurs expliquent une partie de ces valeurs, qu'il faut interpréter avant de les exclure.
- **Valeurs plafonnées** : un pic sur la valeur maximale d'un montant vient du plafonnement, pas d'un phénomène métier.

## 8. Précautions

- **Ne pas publier les données**, sur GitHub ou tout autre service.
- **Ne pas chercher** à identifier l'établissement, une agence ou un client.
- Utiliser un `.gitignore` qui exclut au minimum : `data/`, `*.csv`, `*.xlsx`, `*.pkl`, `*.pbix`.
- Ne pas envoyer les données à un service externe (assistant en ligne, outil de profilage hébergé) sans l'accord des tuteurs.
