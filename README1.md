
# TP Numéro 1 - Mise en Production IA

## Description
Ce TP vise à guider les étapes nécessaires pour la mise en production d'un projet d'intelligence artificielle. Il couvre le cycle complet depuis l'initiation jusqu'à la création et la gestion des API, en passant par les tests, la journalisation, et l'ingénierie des fonctions.

## Étapes de Mise en Production

### e1: Initiation Setup Cours A61
- Initialisation du projet et configuration de l'environnement de développement.

### e2: Pipeline Complet
- Mise en place d'un pipeline de traitement de données et de modélisation.

### e3: Prédiction et Test
- Développement de fonctions de prédiction et de scripts de test.

### e4: Ajout et Validation des Données
- Intégration de nouvelles données et validation de leur qualité.

### e5: Ajout Ingénierie de Fonction
- Amélioration du modèle par l'ingénierie de fonctionnalités supplémentaires.

### e6: Gestion des Versions et Journalisation
- Mise en place d'une stratégie de gestion des versions et de journalisation.

### e7: Construction des Packages
- Packaging et distribution du code.

### e8: Création des API Skeleton
- Développement de l'architecture de base des API.

### e9: Setup, Configuration et Logging
- Configuration du serveur et mise en place du système de logging.

### e10: Ajout Prédiction Test
- Intégration de tests supplémentaires pour les fonctions de prédiction.

### e11: Ajout de Version à l'API
- Versionnage de l'API pour une meilleure gestion et maintenance.

### e12: Ajout d'un Schéma de Validation
- Mise en place d'un schéma pour valider les entrées de l'API.

## Requirements

- Python Version: 3.11

#### Dépendances
numpy>=1.21.0
pandas>=2.1.4
scikit-learn==1.3.2
joblib>=1.1.1
# Testing requirements
pytest>=7.0
# Packaging
setuptools>=41.4.0,<42.0.0
wheel>=0.33.6,<0.34.0

## Problèmes rencontrés et Solutions

1. **Correction du fichier requirements.txt** - Adaptation des versions des dépendances pour assurer la compatibilité avec Python 3.11.

2. **Conversion Float à Float64** - Modification dans le fichier `preprocessors.py` sous `regression_model/procession` à la ligne 94 : conversion des types en utilisant `float64` pour une meilleure précision.

   ```python
   t = pd.Series(X[var].value_counts() / np.float64(len(X)))
   ```

3. **Changement de Valeur Assert** - Dans `tests/test_predict.py`, modification de la valeur assert pour s'aligner avec la précision accrue de `float64`.

   ```python
   assert math.ceil(subject.get('predictions')[0]) == 112512
   ```

4. **Erreurs dans predict.py** - Ajout de `StringIO` dans `packages/regression_model/regression_model/predict.py` pour la gestion des données d'entrée.

   ```python
   from io import StringIO
   data = pd.read_json(StringIO(input_data))
   ```

---

Ce README fournit un aperçu global des étapes et des défis rencontrés lors de la mise en production d'un projet IA. Pour toute question ou assistance supplémentaire, veuillez ouvrir un ticket dans l'onglet "Issues" de ce repository.
