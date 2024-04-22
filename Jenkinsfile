pipeline {
    agent any


    stages {
        stage('Build') {
            steps {
                // Récupérer du code depuis un référentiel GitHub
                //git 'https://github.com/fathallahma/simple-astronomy-lib.git'
                sh "mvn compile"

                
            }

            
        }
        
        stage('Tests') {
            steps {
                // Exécuter les tests unitaires
                sh "mvn test"
            }
            
        }
        
        stage('Package') {
            steps {
                // Générer le package
                sh "mvn package"
            }
            
              post {
                // Si Maven a pu exécuter les tests, même si certains tests ont échoué,
                // enregistrer les résultats des tests et archiver le fichier jar.
                success {
                    junit 'target/surefire-reports/*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
            
        }
        
        
    }
    
  
}
