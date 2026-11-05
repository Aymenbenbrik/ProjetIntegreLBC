# data/

Ce dossier contient le **jeu de données anonymisé** du projet.

## Contenu

| Fichier | Format | Description |
|---|---|---|
| `data_churn.csv` | CSV (~75 Mo) | Données principales : 483 536 lignes, 32 colonnes |
| `ACCOUNT_CATEGORY.xlsx` | Excel | Familles de comptes |
| `CLOSURE_REASON.xlsx` | Excel | Motifs de clôture |
| `CURRENCY.xlsx` | Excel | Devises |
| `INDUSTRY.xlsx` | Excel | Sections d'activité |
| `TARGET.xlsx` | Excel | Lignes métier |

La description détaillée des colonnes figure dans `00_documentation/2_description_donnees.pdf`.

## Protection appliquée

- Identifiants remplacés par des codes aléatoires, sans lien avec un ordre d'origine.
- Agences fondues dans des regroupements anonymes.
- Libellés remplacés par des familles génériques.
- Dates décalées et généralisées ; montants arrondis et plafonnés.
- k-anonymat contrôlé sur les caractéristiques des clients (k ≥ 5).
- Comptes institutionnels retirés et fichiers Excel recréés sans métadonnées.

## Règles d'usage

- Ces données sont fournies **pour un usage pédagogique uniquement**.
- Ne les recopiez pas dans vos propres dépôts et ne les déposez sur aucun service externe.
- N'essayez pas d'identifier l'établissement, une agence ou un client. Si vous pensez reconnaître l'un d'eux, prévenez les tuteurs sans le mentionner dans vos livrables.
