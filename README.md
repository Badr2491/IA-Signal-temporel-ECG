---

# Projet de Détection des Anomalies Cardiaques avec ECG

Ce projet permet de détecter automatiquement les anomalies cardiaques dans des signaux ECG à l'aide d'un modèle d'apprentissage automatique (Random Forest). L'objectif est de fournir une solution légère et rapide pour la détection des anomalies cardiaques, en temps réel ou en différé, afin d'améliorer la réactivité du personnel médical.

## Téléchargement des données

Les données utilisées pour entraîner et tester le modèle proviennent de la base de données **MIT-BIH Arrhythmia Database** disponible sur **PhysioNet**. Pour pouvoir utiliser ce projet, vous devez télécharger les données et les importer dans votre environnement.

### Étape 1 : Téléchargement de la base de données

1. Rendez-vous sur le site de PhysioNet : [MIT-BIH Arrhythmia Database](https://physionet.org/static/published-projects/mitdb/mitdb-1.0.0.zip)
2. Téléchargez le fichier `mitdb-1.0.0.zip`.

### Étape 2 : Importer les données dans Google Colab

Une fois le fichier téléchargé, vous pouvez l'importer sur Google Colab pour l'utiliser dans le projet. Voici les étapes à suivre :

1. Ouvrez votre [Google Colab](https://colab.research.google.com/).
2. Allez dans le menu "Fichier" > "Téléverser" et sélectionnez le fichier `mitdb-1.0.0.zip` que vous avez téléchargé.
3. Une fois le fichier téléchargé, vous pouvez l'extraire directement dans Google Colab en exécutant le code suivant :

```python
import zipfile

# Décompresser le fichier zip
with zipfile.ZipFile('mitdb-1.0.0.zip', 'r') as zip_ref:
    zip_ref.extractall('/content/mitdb')
```

Cela extraira le contenu de la base de données dans le répertoire `/content/mitdb`, ce qui vous permettra de l'utiliser dans votre projet.

### Étape 3 : Vérification du contenu

Une fois le fichier extrait, vous pouvez vérifier son contenu en utilisant la commande suivante :

```python
!ls /content/mitdb
```

Vous devriez voir des fichiers comme `100.atr`, `100.dat`, et `100.hea`, qui correspondent à un enregistrement spécifique de la base de données.

## Utilisation du modèle

Ce projet utilise un modèle de **Random Forest** pour détecter les anomalies cardiaques dans les signaux ECG. Le modèle est entraîné sur les données de la base MIT-BIH Arrhythmia, et peut être utilisé pour prédire des anomalies dans des signaux ECG de nouveaux enregistrements.

### Étape 1 : Préparation des données

Assurez-vous d'extraire les battements ECG à l'aide des fichiers d'annotations associés, puis de les préparer sous forme de vecteurs à utiliser pour l'entraînement et la prédiction.

### Étape 2 : Entraînement du modèle

Entraînez le modèle Random Forest en utilisant les battements extraits et étiquetés comme normaux ou anormaux. Vous pouvez ajuster les paramètres du modèle selon vos besoins.

### Étape 3 : Prédiction des anomalies

Utilisez la fonction `predict_ecg()` pour charger un enregistrement ECG, extraire les battements, appliquer le modèle, et visualiser les anomalies détectées.

Voici un exemple de code pour effectuer une prédiction :

```python
predict_ecg('100', clf)  # '100' fait référence à un enregistrement spécifique
```

### Étape 4 : Visualisation

Le modèle colorie les battements détectés comme normaux en vert et ceux détectés comme anormaux en rouge. Vous pouvez visualiser les résultats à l'aide de matplotlib.

## Prérequis

Avant de lancer le projet, assurez-vous d'avoir installé les bibliothèques suivantes :

* `wfdb` : pour lire et manipuler les fichiers ECG
* `scikit-learn` : pour entraîner et utiliser le modèle Random Forest
* `matplotlib` : pour la visualisation des résultats

Vous pouvez installer ces bibliothèques avec pip :

```bash
pip install wfdb scikit-learn matplotlib
```
