# 🚀 NEXUS EXPLORERS  
## Plateforme Full-Stack de Prédiction d’Exoplanètes par Intelligence Artificielle

🌐 **Application en ligne :**  
👉 https://nexus-explorer-v10.vercel.app/

---

# 🌌 Explorer l’univers grâce à la puissance du Full-Stack & de l’IA

NEXUS EXPLORERS n’est pas un simple projet web.  
C’est une plateforme complète, moderne et intelligente, conçue pour exploiter des données astronomiques réelles (NASA – mission Kepler) afin de prédire l’existence d’exoplanètes à l’aide de modèles avancés de Machine Learning.

Ce projet démontre une maîtrise totale :

- 🎨 Frontend moderne, immersif et performant  
- ⚙️ Backend robuste et structuré  
- 🧠 Intelligence Artificielle complète avec gestion dynamique des modèles  
- 🚀 Déploiement réel et accessible en ligne  

---

# ✨ Pourquoi ce projet est unique ?

Contrairement à une simple application de démonstration :

✅ Nous avons conçu une architecture Full-Stack complète  
✅ Nous avons intégré plusieurs modèles ML réels  
✅ Nous avons implémenté un système de création et de réentraînement dynamique  
✅ Nous avons pensé l’expérience utilisateur du début à la fin  
✅ Nous avons déployé une version en production  

---

# 🎨 FRONTEND — Une expérience immersive et moderne

Le frontend de NEXUS EXPLORERS a été pensé comme un produit premium.

## 🛠 Stack technique

- **Next.js 15 (App Router)**
- **React 18**
- **TypeScript**
- **Tailwind CSS**
- **Radix UI**
- **Three.js**
- Déploiement sur **Vercel**

## 🌠 Une expérience immersive

Nous avons intégré Three.js pour offrir :

- Visualisation 3D spatiale
- Expérience interactive
- Identité visuelle forte
- Sensation d’exploration réelle

L’objectif était clair :  
Créer une interface qui donne l’impression d’explorer l’univers, pas simplement de consulter des données.

## 🧭 Double parcours utilisateur

L’application propose deux expériences distinctes :

### 🔹 Regular User
- Interface simplifiée
- Parcours guidé
- Approche pédagogique

### 🔹 Advanced User
- Accès aux modèles
- Gestion des prédictions
- Vision plus technique et détaillée

Cette séparation montre une réflexion UX avancée.

## 📐 Architecture claire et scalable

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

Résultat :

- Code maintenable
- Composants réutilisables
- Évolution facile
- Structure professionnelle

## ⚡ Performance & qualité

Grâce à Next.js :

- Optimisation du rendu
- Performance élevée
- Build production optimisé
- Déploiement CI/CD automatique

---

# ⚙️ BACKEND — Une API robuste et professionnelle

Le backend a été conçu pour être fiable, évolutif et structuré.

## 🛠 Stack backend

- **FastAPI 0.103**
- **Python 3.10+**
- **Uvicorn**
- **Pydantic v2**
- **Scikit-learn**
- **XGBoost**
- **Pandas / NumPy**
- Sérialisation via **Joblib**

## 🔥 Pourquoi FastAPI ?

- Performance élevée (ASGI)
- Validation automatique des données
- Documentation interactive (/docs)
- Architecture propre et moderne

## 🧱 Architecture backend

```
api/
├── main.py
├── models/
├── data/
├── metrics/
└── requirements.txt
```

Cette structure garantit :

- Séparation claire des responsabilités
- Maintenance simplifiée
- Évolutivité future

---

# 🔌 API REST — Un système complet

## ✅ Liste des modèles
`GET /api/list-models`

Retourne tous les modèles disponibles avec leurs caractéristiques.

## ✅ Prédiction
`POST /api/predict`

- Validation stricte des 20 features
- Prédiction multi-classe
- Retour probabiliste

Exemple de réponse :

```json
{
  "prediction": 2,
  "prediction_label": "Confirmed",
  "probabilities": [0.05, 0.25, 0.70]
}
```

Ce choix d’un retour probabiliste démontre une vraie maturité IA.

## ✅ Création dynamique de modèles
`POST /api/create-model`

Fonctionnalité avancée :

- Choix du type de modèle
- Configuration des hyperparamètres
- Entraînement automatique
- Évaluation
- Sauvegarde
- Historisation des métriques

Ce n’est pas une simple API de prédiction.  
C’est une mini plateforme ML intégrée.

## ✅ Réentraînement
`POST /api/retrain`

- Fusion nouvelles données
- Nettoyage
- Nouveau split train/test
- Réentraînement
- Mise à jour des métriques

Le système devient évolutif.

---

# 🧠 INTELLIGENCE ARTIFICIELLE — Le cœur du projet

NEXUS EXPLORERS utilise des données issues de la mission Kepler (NASA) pour classifier des signaux astronomiques.

## 🎯 Objectif

Classifier en 3 catégories :

- False Positive
- Candidate
- Confirmed (Exoplanète)

## 🤖 Modèles implémentés

- KNN
- RandomForest
- SVM
- XGBoost
- LogisticRegression

Chaque modèle est :

- Entraîné
- Évalué
- Sérialisé
- Réutilisable
- Réentraînable

## 📊 Pipeline ML

1. Chargement dataset
2. Split train/test
3. Entraînement
4. Évaluation
5. Sauvegarde
6. Stockage des métriques

## 📈 Suivi des performances

Les métriques sont enregistrées :

- Accuracy
- Precision
- Recall
- F1-score

Stockées dans :

```
metrics/custom_models_metrics.json
metrics/retrained_models_metrics.json
```

Cela permet :

- Comparaison
- Optimisation
- Traçabilité

---

# 🚀 Déploiement

Frontend déployé sur Vercel :

👉 https://nexus-explorer-v10.vercel.app/

Avantages :

- CI/CD automatique
- Build optimisé
- Performance Edge
- Scalabilité mondiale

Backend prêt pour :

- Render
- Railway
- Heroku
- Docker

---

# 🏗 Structure globale du projet

```
nasa-project/
├── frontEnd/
├── api/
├── backEnd/
├── package.json
├── next.config.mjs
├── vercel.json
└── README.md
```

---

# 🌟 Ce que démontre ce projet

Ce projet met en lumière :

✅ Maîtrise Full-Stack complète  
✅ Intégration IA avancée  
✅ Architecture propre  
✅ Gestion dynamique des modèles  
✅ Expérience utilisateur moderne  
✅ Déploiement réel  
✅ Vision produit  

Il combine :

- Software Engineering
- Data Science
- UX Design
- Cloud Deployment

---

# 🌐 Accès direct

🚀 Essayez l’application ici :  
https://nexus-explorer-v10.vercel.app/

---

# 🪐 Conclusion

NEXUS EXPLORERS est bien plus qu’une application.

C’est la démonstration d’une capacité à :

- Concevoir un système intelligent complet
- Structurer une architecture propre
- Intégrer plusieurs modèles ML réels
- Déployer un produit moderne
- Offrir une expérience immersive

Nous n’avons pas seulement développé une application.  
Nous avons construit une plateforme intelligente prête à évoluer.

---

**Développé avec passion pour l’exploration spatiale et l’innovation technologique.**
