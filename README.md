# 🚀 NEXUS EXPLORERS - Plateforme IA de Détection d'Exoplanètes

**Système full-stack combinant Machine Learning, API REST et interface 3D pour la prédiction d'exoplanètes**

<div align="center">

## 🌐 **[DÉCOUVRIR L'APPLICATION](https://nexus-explorer-v10.vercel.app/)** 🌐

[![Vercel](https://img.shields.io/badge/Deployed-Vercel-black?style=for-the-badge)](https://vercel.com/)
[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.103-009688?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python)](https://www.python.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
</div>

---
**NEXUS EXPLORERS** est une plateforme web complète permettant de prédire la présence d’exoplanètes à partir de données astronomiques réelles issues de la mission Kepler (NASA).

Ce projet combine :

- 🧠 Intelligence Artificielle multi-modèles
- ⚙️ API REST professionnelle avec FastAPI
- 🎨 Interface moderne Next.js 15
- 🌌 Visualisation 3D interactive
- 🚀 Déploiement cloud prêt pour la production

C’est une architecture full-stack complète démontrant des compétences avancées en développement logiciel moderne et en Machine Learning en production.

---

# ✨ Fonctionnalités principales

## 1️⃣ Prédiction d’Exoplanètes via Machine Learning

- 🤖 5 modèles ML entraînés :
  - XGBoost
  - RandomForest
  - SVM
  - KNN
  - Logistic Regression
- 📊 Prédictions probabilistes multi-classes :
  - False Positive
  - Candidate
  - Confirmed
- ⚡ Temps d’inférence < 100ms
- 📈 Accuracy jusqu’à 92%

---

## 2️⃣ API REST Professionnelle (FastAPI)

- 🚀 Architecture asynchrone haute performance
- 📄 Documentation interactive Swagger automatique
- 🔍 Validation stricte des données avec Pydantic
- 📦 Sérialisation des modèles via Joblib
- 🔄 Création dynamique de nouveaux modèles

### Endpoints principaux :

```
GET    /                      → Health check
GET    /api/list-models       → Liste des modèles
POST   /api/predict           → Prédiction
POST   /api/create-model      → Création d’un modèle personnalisé
POST   /api/retrain           → Réentraînement
DELETE /api/models/{name}     → Suppression
```

Documentation interactive disponible via :

```
/docs
/redoc
```

---

## 3️⃣ Création Dynamique de Modèles

L’API permet :

- 🔧 Configuration d’hyperparamètres personnalisés
- 🧠 Entraînement automatique
- 📊 Calcul des métriques
- 💾 Sauvegarde automatique
- 📈 Tracking des performances

Fonctionnalité rarement présente dans des projets standards.

---

## 4️⃣ Réentraînement Incrémental

- 📥 Ajout de nouvelles données
- 🔄 Fusion intelligente
- 📊 Comparaison métriques avant / après
- 📈 Amélioration continue des performances

---

## 5️⃣ Interface Utilisateur Moderne (Next.js 15)

- ⚛️ React 18 + TypeScript strict
- 🎨 Tailwind CSS + Radix UI
- 🌌 Visualisations 3D avec Three.js
- 📱 Design responsive
- ⚡ Optimisation SSR / ISR / Server Components

---

## 6️⃣ Expérience Utilisateur Adaptative

Deux modes :

### 🎓 Regular User
Interface simplifiée, pédagogique et guidée.

### ⚙️ Advanced User
- Contrôle des hyperparamètres
- Analyse détaillée des probabilités
- Gestion des modèles ML

---

## 7️⃣ Performance et Optimisation

### Frontend
- Lighthouse score ~95+
- Bundle optimisé (~150KB gzipped)
- Lazy loading dynamique

### Backend
- Réponse API < 200ms
- Inference ML < 100ms
- 1000+ requêtes / seconde

---

# 🛠 Technologies utilisées

| Technologie | Utilisation |
|-------------|------------|
| **Next.js 15** | Framework React moderne |
| **React 18** | Interface utilisateur |
| **TypeScript** | Typage strict |
| **Tailwind CSS** | Styling |
| **Three.js** | Visualisation 3D |
| **FastAPI** | API REST asynchrone |
| **Python 3.10+** | Backend |
| **Scikit-learn** | Algorithmes ML |
| **XGBoost** | Gradient Boosting |
| **Pandas / NumPy** | Traitement données |
| **Joblib** | Sérialisation modèles |
| **Vercel** | Déploiement frontend |

---

# 🧠 Pipeline Machine Learning

1. 📥 Chargement dataset Kepler
2. 🧹 Nettoyage des données
3. 📊 Normalisation
4. 🔀 Split stratifié train/test
5. 🤖 Entraînement multi-modèles
6. 📈 Évaluation (Accuracy, Precision, Recall, F1)
7. 💾 Sauvegarde des modèles
8. 🚀 Déploiement via API

---

# 📊 Performances des Modèles

| Modèle | Accuracy | F1-score |
|--------|----------|----------|
| XGBoost | 92% | 91% |
| RandomForest | 91% | 89% |
| SVM | 88% | 88% |
| KNN | 86% | 85% |
| Logistic Regression | 84% | 83% |

---

# 📂 Structure du projet

```
nasa-project/
├── frontEnd/
│   ├── app/
│   ├── components/
│   └── styles/
│
├── api/
│   ├── main.py
│   ├── models/
│   ├── data/
│   └── metrics/
│
├── backEnd/
├── package.json
├── vercel.json
└── README.md
```

---

# 🚀 Installation

## 1️⃣ Cloner le dépôt

```bash
git clone https://github.com/Ayman-cell/nasa-project.git
cd nasa-project
```

---

## 2️⃣ Installation Frontend

```bash
npm install
npm run dev
```

---

## 3️⃣ Installation Backend

```bash
python -m venv .venv
source .venv/bin/activate   # macOS/Linux
# ou
.\.venv\Scripts\activate    # Windows

pip install -r api/requirements.txt
uvicorn main:app --reload --port 8000
```

---

# 🐳 Déploiement

## Frontend

Déployé sur Vercel :

👉 https://nexus-explorer-v10.vercel.app/

CI/CD automatique à chaque push.

## Backend

Compatible avec :

- Render
- Railway
- Docker
- AWS / Azure

---

# 🔒 Sécurité

Recommandations production :

- 🔐 Authentification JWT
- ⏱️ Rate limiting
- 📊 Monitoring
- 🛡 Validation stricte des entrées

---

# 💼 Cas d’usage

- 🔬 Recherche astronomique
- 🎓 Projet académique avancé
- 📊 Démonstration ML en production
- 💡 Prototype SaaS scientifique
- 🚀 Portfolio technique full-stack

---

# 🎯 Compétences démontrées

## Frontend
- Architecture moderne Next.js
- Optimisation performance
- Visualisation 3D WebGL

## Backend
- API REST professionnelle
- Validation robuste
- Gestion des erreurs avancée

## Machine Learning
- Multi-modèles
- Hyperparameter tuning
- Cross-validation
- Déploiement production

## DevOps
- Vercel
- Docker-ready
- Gestion environnements

---

# 📝 Licence

Licence MIT.

---

# 👨‍💻 Auteur

**Ayman**

- GitHub : https://github.com/Ayman-cell
- Application : https://nexus-explorer-v10.vercel.app/

---

# 🚀 Conclusion

NEXUS EXPLORERS n’est pas un simple projet.

C’est :

- Une architecture complète
- Une IA déployée en production
- Une interface immersive
- Une API professionnelle
- Une démonstration technique avancée

Un projet qui illustre la capacité à concevoir, développer, optimiser et déployer un système full-stack intelligent moderne.

---

**Discovering distant worlds through the power of AI**
