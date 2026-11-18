# regression_air_quality
Résoudre un problème de régression pour modéliser et prédire la qualité de l'aire à l'aide des données proposées ici :  https://archive.ics.uci.edu/dataset/360/air+quality

Projet d’apprentissage statistique réalisé par **Marya Khelifa et Nour Bouabid**.

## Objectif

Prédire simultanément quatre mesures de concentration de polluants atmosphériques — `CO(GT)`, `C6H6(GT)`, `NOx(GT)` et `NO2(GT)` — à partir de mesures de capteurs et de variables météorologiques. Le projet compare des approches de régression linéaires et non linéaires.

## Données et préparation

Le notebook exploite le fichier **`AirQualityUCI.csv`** (jeu de données *Air Quality*, UCI).

- **Variables explicatives (8)** : `PT08.S1(CO)`, `PT08.S2(NMHC)`, `PT08.S3(NOx)`, `PT08.S4(NO2)`, `PT08.S5(O3)`, température (`T`), humidité relative (`RH`) et humidité absolue (`AH`).
- **Variables cibles (4)** : `CO(GT)`, `C6H6(GT)`, `NOx(GT)` et `NO2(GT)`.
- Conversion des dates et heures, tri chronologique, remplacement du code de valeur manquante `-200` par `NaN`, suppression des colonnes vides et des observations incomplètes.
- **6 941 observations conservées** après nettoyage ; séparation chronologique en **5 552 observations d’entraînement** et **1 389 observations de test**.
- Standardisation des variables explicatives à l’aide d’un `StandardScaler` ajusté sur l’entraînement.

Le notebook contient également des statistiques descriptives, histogrammes, corrélations et boxplots.

## Méthodes étudiées

1. **Régression linéaire multiple**, avec évaluation sur des découpages successifs `TimeSeriesSplit`.
2. **Régression Ridge**, avec exploration du coefficient de régularisation `alpha`.
3. **Régression à noyau RBF** (`KernelRidge`), avec recherche sur une grille de paramètres `alpha` et `gamma`.
4. **Réseau de neurones dense** (`TensorFlow/Keras`), avec essais sur la taille du réseau, le nombre d’époques et la taille des lots (*batch size*).


