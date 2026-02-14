# 🚀 NEXUS EXPLORERS  
## Plateforme Intelligente Full-Stack de Détection d’Exoplanètes

### Système avancé combinant Machine Learning, API REST haute performance et interface 3D immersive

---

<div align="center">

## 🌐 [🔗 DÉCOUVRIR L’APPLICATION EN LIGNE](https://nexus-explorer-v10.vercel.app/)

![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)
![FastAPI](https://img.shields.io/badge/FastAPI-0.103-009688?style=for-the-badge&logo=fastapi)
![Python](https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python)
![TypeScript](https://img.shields.io/badge/TypeScript-5-blue?style=for-the-badge&logo=typescript)
![Machine Learning](https://img.shields.io/badge/ML-Scikit--learn%20%7C%20XGBoost-orange?style=for-the-badge)

</div>

---

# 🌌 Vision du Projet

**NEXUS EXPLORERS** est une application full-stack de niveau production permettant de prédire la présence d’exoplanètes à partir de données astronomiques réelles (mission Kepler – NASA).

Ce projet démontre :

- ✅ Une architecture full-stack moderne  
- ✅ Une API professionnelle documentée  
- ✅ Une intégration IA complète en production  
- ✅ Une interface 3D immersive  
- ✅ Une performance optimisée  

Ce n’est pas un simple projet académique.  
C’est une plateforme technique complète, scalable et évolutive.

---

# 🏗 Architecture Générale

L’application repose sur trois piliers :

1️⃣ Frontend moderne (Next.js 15 + React 18)  
2️⃣ Backend haute performance (FastAPI + Python)  
3️⃣ Intelligence Artificielle multi-modèles  

Architecture découplée et production-ready.

```
Frontend (Next.js 15)
        ↓
API REST (FastAPI)
        ↓
Modèles ML (Scikit-learn / XGBoost)
```

---

# 🎨 FRONTEND — Interface Moderne & Immersive

## ⚙️ Stack Technique

- Next.js 15 (App Router)
- React 18
- TypeScript
- Tailwind CSS
- Radix UI
- Three.js (visualisation 3D)
- Déploiement Vercel

---

## ✨ Points Forts Frontend

### 🚀 Performance
- SSR / ISR / Server Components
- Code splitting automatique
- Lazy loading
- Lighthouse score ~95+

### 🌠 Visualisation 3D
- Intégration Three.js
- Scènes spatiales interactives
- Rendu WebGL optimisé

### 🎯 UX Adaptative

Deux modes :

- **Regular User** → Interface pédagogique simplifiée  
- **Advanced User** → Accès aux modèles et paramètres ML  

---

## 📂 Structure Frontend

```
frontEnd/
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   ├── about-exoplanets/
│   ├── advanced-user/
│   └── regular-user/
├── components/
├── public/
└── styles/
```

Architecture modulaire, maintenable et évolutive.

---

# ⚙️ BACKEND — API REST Professionnelle

## 🛠 Stack Backend

- FastAPI 0.103
- Python 3.10+
- Uvicorn (ASGI)
- Pydantic v2
- Scikit-learn
- XGBoost
- Pandas / NumPy
- Joblib

---

## 🔥 Pourquoi FastAPI ?

- Performance asynchrone
- Validation automatique des données
- Documentation Swagger auto-générée
- Typage strict

Documentation interactive disponible via :

```
/docs
/redoc
```

---

## 🔌 Endpoints Principaux

### 1️⃣ Health Check

```
GET /
```

---

### 2️⃣ Liste des Modèles

```
GET /api/list-models
```

Retourne :
- Nom
- Type
- Nombre de features
- Statut mémoire

---

### 3️⃣ Prédiction ML

```
POST /api/predict
```

Contraintes strictes :
- Exactement 20 features numériques
- Modèle existant requis

Réponse :

```json
{
  "prediction": 2,
  "prediction_label": "Confirmed",
  "probabilities": [0.05, 0.25, 0.70],
  "confidence": 0.70,
  "inference_time_ms": 87
}
```

Temps d’inférence moyen : **<100ms**

---

### 4️⃣ Création Dynamique de Modèle

```
POST /api/create-model
```

Permet :
- Choix de l’algorithme
- Configuration des hyperparamètres
- Entraînement automatique
- Évaluation
- Sauvegarde
- Tracking métriques

Fonctionnalité rarement présente dans des projets open-source.

---

### 5️⃣ Réentraînement

```
POST /api/retrain
```

- Fusion nouvelles données
- Nettoyage
- Nouveau split
- Réentraînement
- Comparaison des métriques

---

### 6️⃣ Suppression

```
DELETE /api/models/{model_name}
```

---

# 🧠 INTELLIGENCE ARTIFICIELLE

## 🎯 Objectif

Classifier un objet céleste en :

- False Positive
- Candidate
- Confirmed

---

## 🤖 Modèles Implémentés

- XGBoost
- RandomForest
- SVM
- KNN
- LogisticRegression

---

## 🏆 Performances

| Modèle | Accuracy | F1-Score |
|--------|----------|----------|
| XGBoost | 92% | 91% |
| RandomForest | 91% | 89% |
| SVM | 88% | 88% |
| KNN | 86% | 85% |
| Logistic | 84% | 83% |

---

## 🔬 Pipeline ML

1. Chargement dataset Kepler
2. Nettoyage
3. Normalisation
4. Split stratifié
5. Entraînement
6. Évaluation
7. Sérialisation .pkl
8. Tracking JSON

---

## 📊 Métriques Trackées

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix

Stockées dans :

```
metrics/custom_models_metrics.json
metrics/retrained_models_metrics.json
```

---

# 🚀 PERFORMANCE

## Frontend

- Lighthouse ~95
- TTI < 3s
- Bundle ~150KB

## Backend

- API < 200ms
- ML < 100ms
- 1000+ req/s

---

# 🏗 Structure Projet

```
nasa-project/
├── frontEnd/
├── api/
├── backEnd/
├── package.json
├── vercel.json
└── README.md
```

---

# 🐳 Déploiement

## Frontend

Déployé sur Vercel :

👉 https://nexus-explorer-v10.vercel.app/

CI/CD automatique.

## Backend

Compatible :

- Render
- Railway
- Heroku
- Docker

---

# 🛡 Sécurité

Recommandations production :

- Authentification API Key / JWT
- Rate limiting
- Validation stricte
- Logs structurés
- Monitoring

---

# 💼 Compétences Démontrées

## Frontend
- Next.js 15
- React avancé
- TypeScript strict
- 3D WebGL

## Backend
- FastAPI async
- REST design
- Validation Pydantic
- Gestion d’erreurs

## Machine Learning
- 5 algorithmes
- Hyperparameter tuning
- Cross-validation
- Model persistence
- Déploiement production

## DevOps
- Vercel
- Docker-ready
- Environnements multiples

---

# 🏆 Ce que ce projet prouve

Ce projet démontre :

- Capacité full-stack complète
- Maîtrise ML en production
- Architecture scalable
- UX moderne
- Performance optimisée
- Code structuré et documenté
- Vision produit

---

# 🌐 Accès Application

👉 https://nexus-explorer-v10.vercel.app/

---

# 🚀 Conclusion

NEXUS EXPLORERS n’est pas un simple projet.

C’est :

- Une plateforme intelligente
- Une architecture propre
- Une IA déployée en production
- Une expérience immersive
- Une démonstration technique de haut niveau

Ce projet illustre une capacité à concevoir, développer, optimiser et déployer un système complet combinant :

Frontend moderne  
Backend robuste  
Machine Learning avancé  
Déploiement cloud  

---

<div align="center">

**Discovering distant worlds through the power of AI**

</div>
