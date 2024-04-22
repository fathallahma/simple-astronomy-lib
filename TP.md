# Résumé du pipeline Jenkins

Ce pipeline Jenkins est conçu pour automatiser le processus de construction, de test et de génération de package du projet SimpleAstronomy à partir de notre github cloné.

## Étapes du pipeline :

### Étape 1: Build

**Objectif :** Récupérer le code source depuis GitHub et le construire. URL : https://github.com/fathallahma/simple-astronomy-lib.git

**Actions :** git 'https://github.com/fathallahma/simple-astronomy-lib.git'
- Cloner le dépôt GitHub du projet. 
- Exécuter les commandes de build nécessaires pour compiler le code.

**Résultats :**
- Le code source est récupéré avec succès.
- La compilation est réussie.

### Étape 2: Tests

**Objectif :** Exécuter les tests unitaires pour vérifier la qualité du code. 

**Actions :** 
- Lancer les tests unitaires à l'aide de Maven. 
  sh "mvn test"
- Collecter et analyser les résultats des tests.

**Résultats :**
- Les tests unitaires sont exécutés avec succès.
- Les résultats des tests sont enregistrés pour évaluation.

### Étape 3: Package

**Objectif :** Générer le package du projet pour une distribution ultérieure.

**Actions :** 
- Créer un package (jar) à partir des fichiers compilés. 
  sh "mvn package"
- Si Maven a pu exécuter les tests, enregistrer les résultats des tests et archiver 
  success {
            junit 'target/surefire-reports/*.xml'
            archiveArtifacts 'target/*.jar'
        }

**Résultats :**
- Le package est généré avec succès.
- Le package est archivé et prêt à être distribué.

Last Successful Artifacts
SimpleAstronomyLib-0.3.0-javadoc.jar	160,88 KiB	view
SimpleAstronomyLib-0.3.0-sources.jar	13,85 KiB	view
SimpleAstronomyLib-0.3.0.jar	13,95 KiB	view


