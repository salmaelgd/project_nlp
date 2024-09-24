# project_nlp
# Analyse des Sentiments des Tweets

##  Prétraitement des Données

###  Description de la Base de Données
Le projet utilise le **Sentiment140 dataset** de Kaggle, contenant **1,6 million de tweets** pour l'analyse des sentiments sur les médias sociaux, notamment Twitter. Chaque tweet est annoté avec une polarité (0 pour négatif, 4 pour positif).

| Sentiment | Nombre de lignes |
|-----------|------------------|
| Positif   | 800,000          |
| Négatif   | 800,000          |

#### Colonnes de la Base de Données :
- **target** : polarité du tweet
- **ids** : identifiants uniques des tweets
- **date** : date et heure de publication (UTC)
- **flag** : origine de la requête
- **user** : nom de l'utilisateur
- **text** : contenu du tweet (utilisé pour l'analyse des sentiments)

###  Prétraitement de la Base de Données
- **Nettoyage du Texte** :
  - Suppression des liens et mentions
  - Uniformisation (minuscules)
  - Élimination des mots vides (stop words)
  - Application de la lemmatisation
  - Suppression de mots spécifiques sans signification pour l'analyse

###  Visualisation des Données
- Analyse des Mots Fréquents avec CountVectorizer
- Histogramme des 20 mots les plus fréquents
- Nuages de mots pour sentiments positifs et négatifs
- Visualisation temporelle du nombre de tweets

## Modèle CNN pour l'Analyse des Sentiments

### Préparation des Données pour le Modèle
- Division des données : 60% entraînement, 20% validation, 20% test

| Données         | Taille  |
|------------------|---------|
| Entraînement      | 960,000 |
| Validation        | 320,000 |
| Test              | 320,000 |

### Hyperparamètres
- **Fonction d'activation** : ReLU et Sigmoïde
- **Fonction de perte** : Binary Crossentropy
- **Optimiseur** : Adam
- **Taille des lots** : définie selon la taille de l'ensemble de données
- **Époques** : 25

### Architecture du Modèle
- Couche d'Embedding
- Trois couches de convolution 1D
- Couche GlobalMaxPooling1D
- Trois couches Dense

### Entraînement et Évaluation du Modèle
- Matrice de confusion pour mesurer l'exactitude, la précision, le rappel, et le score F1

| Données          | Accuracy | Recall | Precision | F1-score |
|------------------|----------|--------|-----------|----------|
| Train data       | 0.9741   | 0.9771 | 0.9708    | 0.9739   |
| Validation data   | 0.7297   | 0.7324 | 0.7251    | 0.7279   |
| Test data         | 0.7293   | 0.7310 | 0.7260    | 0.7219   |

## Analyse des Tendances

### Le Modèle LDA
- Utilisation de Latent Dirichlet Allocation (LDA) pour l'analyse des tendances

### Exploration des Résultats
- Extraction et affichage des mots clés pour chaque topic
- Visualisation graphique de la distribution des topics

| Topic | Mots clés                             |
|-------|---------------------------------------|
| 1     | wow, tonight, looking, just, thank    |
| 2     | today, days, bed, school, got         |
| 3     | birthday, sure, cool, sick, need      |
| 4     | hair, cute, check, www, hot           |
| 5     | sleep, need, yeah, don, new           |

### Analyse des Topics par Classe
- Répartition des topics en fonction des classes de sentiments (positif et négatif)
