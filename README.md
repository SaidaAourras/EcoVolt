# 📊 Prédiction de la Consommation Électrique – LSTM (EcoVolt)

## 🧠 À propos du projet

Ce projet utilise un modèle LSTM (Long Short-Term Memory) pour prédire la consommation électrique de l'heure suivante à partir des 24 heures précédentes. Dans le contexte d'un réseau électrique intelligent (Smart Grid), cette anticipation permet d'éviter les pics de consommation et les surcharges du réseau.

### 🎯 Objectifs

- Prédire la consommation électrique à l'heure t+1
- Anticiper les pics de charge
- Améliorer la stabilité du réseau électrique

## 📁 Dataset

Le dataset contient des données horaires avec les colonnes suivantes :

- **DateTime** : date et heure de la mesure
- **Consumption** : consommation électrique totale (MW)
- **Production** : production totale (MW)
- **Sources de production** : Nuclear, Wind, Hydroelectric, Oil and Gas, Coal, Solar, Biomass

Toutes les valeurs sont numériques et exprimées en mégawatts (MW).

## ⚙️ Méthodologie

### 1. Préparation des données
- Conversion de `DateTime` en format temporel
- Tri chronologique des données
- Utilisation de `DateTime` comme index

> ⚠️ Le respect de l'ordre temporel est essentiel pour éviter toute fuite de données.

### 2. Normalisation
- Application d'un MinMaxScaler pour mettre à l'échelle les données entre 0 et 1
- La normalisation assure un apprentissage stable du LSTM

### 3. Création des séquences
- Fenêtre glissante de 24 heures
- Chaque entrée du modèle contient 24 pas de temps
- La sortie correspond à la consommation de l'heure suivante

### 4. Séparation Train / Test
- Split temporel : 80% entraînement / 20% test
- Aucune permutation aléatoire des données

### 5. Architecture du modèle LSTM
- 1 couche LSTM (64 unités)
- Dropout pour limiter le surapprentissage
- Couche Dense finale pour la prédiction

### 6. Entraînement
- **Optimiseur** : Adam
- **Fonction de perte** : MSE (Mean Squared Error)
- Suivi des courbes `loss` et `val_loss`

### 7. Évaluation
- Comparaison entre valeurs réelles et prédites
- Visualisation graphique des résultats

## 📈 Résultats

Le modèle démontre sa capacité à :
- Suivre la tendance globale de la consommation
- Anticiper les variations horaires
- Fournir des prédictions cohérentes pour la gestion du réseau

## 🛠️ Technologies utilisées

- **Langage** : Python
- **Manipulation de données** : Pandas, NumPy
- **Machine Learning** : Scikit-learn, TensorFlow / Keras
- **Visualisation** : Matplotlib
- **Environnement** : Jupyter Notebook

## ▶️ Exécution du projet

1. Ouvrir le notebook Jupyter
2. Exécuter les cellules dans l'ordre
3. Visualiser les résultats à la fin du notebook

## 📌 Conclusion

Ce projet illustre l'application pratique d'un modèle LSTM pour résoudre un problème réel de séries temporelles dans le domaine des réseaux électriques intelligents. Il met en évidence l'importance du prétraitement des données, du respect de la dimension temporelle et du choix d'une architecture adaptée aux prédictions de séries chronologiques.
