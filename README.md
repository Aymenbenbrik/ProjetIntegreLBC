# Projet Intégré — Analyse et Prédiction du Churn Client

> **École** : ESPRIT School of Business
> **Programme** : Licence 3 : Business Computing BI
> **Tuteurs du projet** : Aymen Ben Brik et Hela Hammami
> **Année** : 2026

Bienvenue. Ce dossier contient l'ensemble des supports nécessaires pour réaliser le projet.

## Par où commencer

1. Lisez les documents du dossier **`00_documentation/`** dans l'ordre :
   - `1_description_projet.md` — ce qu'on vous demande de faire et les livrables attendus.
   - `2_description_donnees.md` — la structure des données fournies.
   - `3_timeline.md` — les 5 jalons, du 9/11 au 7/12/2026.
   - `4_guide_etudiant.md` — le socle obligatoire, les bonus et les outils, étape par étape.
2. Placez les fichiers de données qui vous seront remis par les tuteurs dans le dossier **`data/`** (ce dossier est ignoré par Git, voir `.gitignore`).
3. Travaillez dans les dossiers numérotés correspondants à chaque phase.

## Structure du dossier

| Dossier | Contenu attendu |
|---|---|
| `00_documentation/` | Documents fournis par les tuteurs (ne pas modifier) |
| `01_etl/` | Analyse des données et jobs Talend exportés (extraction, nettoyage, transformation) |
| `02_data_warehouse/` | Scripts SQL PostgreSQL, modèle dimensionnel, contrôles de chargement |
| `03_power_bi/` | Captures d'écran et documentation des mesures DAX (`.pbix` remis hors GitHub) |
| `04_machine_learning/` | Notebooks de série temporelle (LSTM/RNN) et de churn (modèles hors dépôt) |
| `05_web_app/` | Code de l'application web, diagrammes UML et instructions de déploiement |
| `06_rapport/` | Sources du rapport (Word, LaTeX, etc.) et version PDF finale |
| `07_presentation/` | Slides de présentation |
| `data/` | Données brutes (**ne sera pas versionnée**) |

## Règles à respecter

- **Données confidentielles** : aucun fichier de données ne doit être commité sur GitHub. Le dossier `data/` est exclu via `.gitignore`.
- **Non-réidentification** : n'essayez pas d'identifier l'établissement, une agence ou un client, et ne faites aucune hypothèse sur l'origine des données dans vos livrables.
- **Application publique** : uniquement des agrégats et des profils fictifs, jamais de ligne client.
- **Versioning régulier** : chaque membre de l'équipe doit commiter régulièrement, sur sa branche.
- **Reproductibilité** : votre code doit pouvoir être ré-exécuté à partir des instructions de ce README et du `requirements.txt`.

## Installation

```bash
# 1. Cloner le dépôt
git clone <url-de-votre-depot>
cd <nom-du-depot>

# 2. Créer un environnement virtuel
python -m venv venv
source venv/bin/activate   # Linux / macOS
venv\Scripts\activate      # Windows

# 3. Installer les dépendances
pip install -r requirements.txt

# 4. Placer les fichiers de données dans data/
# (les fichiers vous seront fournis séparément)
```

## Livrables finaux

À la fin du projet, vous devez fournir :

1. **Le lien vers votre dépôt GitHub** (propre, documenté, sans aucune donnée).
2. **Le rapport PDF** (dans `06_rapport/`).
3. **Les slides de présentation** (dans `07_presentation/`).
4. **L'URL** de votre application web déployée (mentionnée dans ce README).
5. **Les diagrammes UML** : cas d'utilisation global, une séquence, classes.

## Composition de l'équipe

| Nom | Rôle principal | Email |
|---|---|---|
| _À compléter_ | _À compléter_ | _À compléter_ |
| _À compléter_ | _À compléter_ | _À compléter_ |
| _À compléter_ | _À compléter_ | _À compléter_ |

## Contact tuteurs

- Aymen Ben Brik — aymen.benbrik@esprit.tn
- Hela Hammami — hela.hammami@esprit.tn
