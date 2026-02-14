# Nexus Explorers — NASA Exoplanet Prediction (nasa-project)

Live app: https://nexus-explorer-v10.vercel.app/

Résumé
-------
Ce dépôt (nexus-explorers / `nasa-project`) est une application web full‑stack pour l'exploration et la prédiction d'exoplanètes. Elle combine :
- Frontend moderne en Next.js (React) avec UI Radix/Tailwind et composants 3D (three.js) ;
- Backend Python proposant des API REST pour charger, prédire, créer et réentraîner des modèles ML (FastAPI + morceaux en Flask présents dans `api/`) ;
- Composants ML / IA : modèles entraînés sérialisés (.pkl), scripts d'entraînement et utilitaires pour gérer métriques et réentraînement.

Structure du dépôt (points importants)
-------------------------------------
- `package.json` (root) : projet Next.js (`next@^15`) — frontend principal.
- `vercel.json`, `next.config.mjs` : configuration pour déploiement Vercel.
- `frontEnd/` et `app/` : pages et composants Next.js (Route App Router), styles, assets publics.
- `api/` : API Python (contient `main.py`, `index.py`, `requirements.txt`, dossiers `models`, `data`, `metrics`) — endpoints de prédiction et gestion de modèles.
- `backEnd/` : scripts et implementation FastAPI (équivalente / complémentaire à `api/`), plus modèles `.pkl`, utilitaires d'entraînement et d'évaluation.

Frontend — détails techniques
-----------------------------
- Framework: Next.js ^15 (App Router). React 18.
- UI: Radix UI primitives, Tailwind CSS, diverses bibliothèques d'UI (`geist`, `lucide-react`, `cmdk`, `sonner`) et `three` pour éléments 3D.
- TypeScript: projet typé (`typescript` en devDependencies).
- Scripts usuels:
  - `npm run dev` — démarre le frontend en mode développement (`next dev`).
  - `npm run build` — build de production (`next build`).
  - `npm start` — start (production).
- Fichiers clés:
  - `next.config.mjs` — configuration (eslint/typescript ignoreDuringBuilds, images unoptimized).
  - `app/layout.tsx`, `app/page.tsx`, et sous-dossiers (`about-exoplanets`, `advanced-user`, `regular-user`) : pages et layout.

Backend / API — détails techniques
--------------------------------
Deux couches API sont présentes :

1) `api/` — contient :
   - `requirements.txt` (dépendances Python) : scikit-learn, pandas, numpy, xgboost, joblib, flask, fastapi, uvicorn, pydantic.
   - `index.py` : implémentation Flask plus simple qui charge des modèles via `joblib` et expose endpoints `/api/predict`, `/api/models`, `/api/health`.
   - `main.py` : implémentation FastAPI plus complète (routes `/api/list-models`, `/api/predict`, `/api/create-model`, `/api/custom-models`, `/api/retrain`, `/api/retrained-models`, etc.).

2) `backEnd/` — contient des scripts utilitaires FastAPI (chargement de modèles, création de modèles custom, entraînement, métriques). On y trouve :
   - Routes FastAPI similaires — startup event charge des modèles mock et charge les `.pkl` si présents.
   - Fonctions utilitaires: `load_pkl_models()`, `create_custom_model()` (supporte RandomForest, XGBoost, SVM), `load_training_data()`, `train_and_evaluate_model()`, `save_custom_model_metrics()`.
   - Exécution: via `uvicorn main:app --reload` (port 8000 par défaut).

Endpoints principaux (FastAPI `main.py`)
- `GET /` — message de santé basique.
- `GET /api/list-models` — liste modèles disponibles (cache + `.pkl`).
- `POST /api/predict` — body: { model_name, features: [float] } — renvoie `prediction`, `prediction_label`, `probabilities`.
  - ATTENTION: le code exige 20 features (vérification `len(features) == 20`).
- `POST /api/create-model` — body: `ModelConfig` (name, type, hyperparams) — crée, entraîne et sauvegarde un modèle custom 
- `POST /api/retrain` — réentraîne un modèle en fusionnant nouvelles données et dataset original.
- `DELETE /api/models/{model_name}` — supprime modèle custom (.pkl) et nettoie métriques.

Dépendances backend (extrait de `api/requirements.txt`)
- Python packages : scikit-learn==1.3.0, pandas==2.0.3, numpy==1.24.3, xgboost==1.7.6, joblib==1.3.2, flask==2.3.3, fastapi==0.103.1, uvicorn==0.23.2, pydantic==2.0.3

IA / Modèles — détails techniques
--------------------------------
- Modèles stockés : `.pkl` (joblib/pickle) dans `api/models` ou `backEnd/models`.
- Modèles inclus/attendus par défaut : KNN, RandomForest, SVM, XGBoost, LogisticRegression (selon `index.py` map). Le `backEnd/main.py` supporte aussi la création de RandomForest/XGBoost/SVC (SVM).
- Entrées pour prédiction : vecteurs de 20 features numériques (le backend valide une taille fixe de 20).
- Probabilités : si le modèle expose `predict_proba`, l'API renvoie les probabilités par classe (ex: 3 classes: Faux Positif / Candidat / Exoplanète).
- Données d'entraînement : `data/kepler_preprocessed.csv` (utilisé pour `load_training_data()` et pour réentraîner/augmenter dataset).
- Suivi des métriques : fichiers JSON sous `metrics/` (`custom_models_metrics.json`, `retrained_models_metrics.json`) stockent métriques et méta.

Flux ML observé
- Chargement initial : `create_mock_models()` (données synthétiques) + `load_pkl_models()` si `.pkl` présents.
- Création modèle custom : `POST /api/create-model` crée le modèle via `create_custom_model`, entraîne et sauvegarde `.pkl`, met à jour `metrics/*.json`.
- Réentrainement : `POST /api/retrain` fusionne nouvelles données, nettoie, split train/test, réentraîne et sauvegarde modèle réentrainé.

Sécurité et limites
-------------------
- Pas d'authentification incluse — endpoints ouverts (prévoir JWT/clé API pour production).
- Validation minimale : le backend vérifie la longueur des features mais pas la plage/échelle. Assurez-vous d'utiliser les mêmes pré-traitements qu'à l'entraînement (scaling/normalisation si utilisé).
- Le dépôt contient du code Flask et FastAPI; il faut choisir une implémentation cohérente pour le déploiement ou garder l'une pour tests locaux.

Déploiement
-----------
- Le projet est configuré pour Vercel (`vercel.json` et `@vercel/next` build). Le frontend est déployé sur Vercel (link fourni en haut).
- Backend Python (FastAPI) peut être déployé séparément (Heroku, Railway, Render, Azure, etc.) ; Vercel ne permet pas d'héberger un serveur Python persistant par défaut — si l'API Python est montée côté Vercel, vérifier les serverless handlers (actuellement le repo contient des fichiers Python bruts, prévoir un déploiement dédié ou convertisseur serverless).

Comment exécuter localement (dev)
---------------------------------
Frontend (Node.js + npm / pnpm):
1. Installer Node.js 18+.
2. À la racine du projet (où se trouve `package.json`) :
```bash
npm install
npm run dev
```
3. Ouvrir `http://localhost:3000`.

Backend (Python, FastAPI):
1. Créer et activer un environnement virtuel Python 3.10+ :
```bash
python -m venv .venv
.
# Windows PowerShell
.\.venv\Scripts\Activate.ps1
# ou cmd
.\.venv\Scripts\activate.bat
```
2. Installer dépendances depuis `api/requirements.txt` :
```bash
pip install -r api/requirements.txt
```
3. Lancer l'API FastAPI (depuis `api/` ou `backEnd/` selon l'implémentation choisie) :
```bash
uvicorn main:app --reload --port 8000
```
4. Tester endpoints : `http://localhost:8000/api/list-models`, `POST /api/predict`.

Notes d'intégration front↔back
- Le frontend attend des endpoints REST sous `/api/*`. En dev local, ajuster les CORS (le backend autorise déjà `http://localhost:3000`).
- Exemple payload de prédiction :
```json
{
  "model_name": "XGBoost_top1",
  "features": [0.1, 0.5, 0.2, 0.3, 0.4, 0.6, 0.7, 0.8, 0.12, 0.9, 0.11, 0.13, 0.14, 0.15, 0.16, 0.17, 0.18, 0.19, 0.2, 0.21]
}
```

Contributions et bonnes pratiques
--------------------------------
- Standardiser : garder une seule implémentation API (FastAPI recommandé) et supprimer le code Flask redondant pour éviter confusion.
- Ajouter tests unitaires pour endpoints critiques (prédiction, création modèle, réentrainement).
- Ajouter authentification pour protéger endpoints création/réentrainement/suppression.
- Stockage des modèles : pour production, stocker `.pkl` dans un stockage persistant (S3, Blob) plutôt que dans le repo.

Fichiers et emplacements clés (références rapides)
- `package.json` (root) — [config Next.js et dépendances frontend].
- `next.config.mjs`, `vercel.json` — déploiement frontend.
- `frontEnd/`, `app/`, `components/` — code React/Next.
- `api/requirements.txt` — dépendances Python backend.
- `api/main.py` (FastAPI) — API principale recommandée.
- `api/index.py` (Flask) — alternative/legacy.
- `backEnd/main.py` — implémentation FastAPI plus complète/utilitaires ML.
- `api/models/` ou `backEnd/models/` — fichiers `.pkl` des modèles.
- `api/data/kepler_preprocessed.csv` — dataset utilisé pour entraînement et réentrainement.
- `metrics/*.json` — historique des métriques pour custom/retrained models.

Questions / vérifications que je peux faire pour finaliser
---------------------------------------------------------
- Voulez-vous que j'ajoute ce README directement dans la racine du repo (je peux créer un `README.md` prêt à committer) ?
- Souhaitez-vous que j'écrive un guide d'installation automatisé (scripts `Makefile` ou `setup.sh`) ou des workflows GitHub Actions pour tests/déploiement ?

Annexes techniques (rapide)
- Durée d'exécution / performance : les modèles scikit-learn/XGBoost sont CPU-bound — prévoir instances CPU ou conversion à ONNX/Triton pour haute performance.
- Compatibilité : vérifier versions Python et Node.js en environment de production.

---
Fait : inventaire initial et README détaillé généré. Dites-moi si je dois :
- l'ajouter dans la racine du dépôt `README.md` et préparer un commit ;
- créer des scripts d'installation et examples Postman / curl ;
- ouvrir un PR sur `Ayman-cell/nasa-project` si vous me donnez accès (ou je crée un patch que vous pouvez appliquer).

Auteur de l'analyse : assistant (vérification automatique des fichiers publics du repo GitHub fourni).
