pipeline {
    agent any

    stages {

        stage('Git Checkout') {
            steps {
                  dir('back'){
                git branch :'main' , url: 'https://github.com/amaltrabelsi/DEVOPS.git'}
             }
        }

         // stage('Backend') {
             //steps {
                // Étape de compilation du backend
               //  sh 'mvn clean package'
              //}
          //}
         stage('Backend Compilation and Package') {
    steps {
        dir('back') {
            sh 'mvn clean compile package'
        }
    }
}

Cela ajoutera une étape pour la compilation (mvn clean compile) et l'emballage (mvn package) de votre projet Maven situé dans le répertoire "back".

Assurez-vous de personnaliser davantage le Jenkinsfile en fonction de vos besoins spécifiques. Ensuite, enregistrez le Jenkinsfile dans votre référentiel Git et configurez votre pipeline Jenkins pour qu'il l'utilise.

N'oubliez pas de configurer les variables d'environnement, les plugins et les outils requis pour que votre pipeline fonctionne correctement, en fonction de votre infrastructure Jenkins et de vos besoins de construction.

          stage('Test') {
            steps {
                dir('back'){
               sh 'mvn test'}
            }
          }
          stage('MVN COMPILE') {
                      steps {
                      dir('back'){

                         sh 'mvn compile'}
                     }
                  }
        /*stage('Frontend') {
            steps {
                // Étape de compilation du frontend
               // sh 'ng build'
            }
        }

        stage('Nexus') {
            steps {
                // Étape de déploiement du backend vers Nexus Repository Manager
                // Utilisez les configurations Nexus et Maven appropriées
            }
        }

        stage('Junit') {
            steps {
              dir('back'){
                // Étape de tests unitaires du backend
               sh 'mvn test'}
            }
        }*/

stage('SonarQube Analysis') {
steps {
dir('back') {
withSonarQubeEnv('sonarserver') {
sh 'mvn sonar sonar- Dsonar.java.binaries=target/classes'
}

                   
               }
            }
        }

    /*    stage('Docker Image') {
            steps {
                // Étape de création d'images Docker pour le backend et le frontend
                // Utilisez les Dockerfiles appropriés
            }
        }

        stage('Docker Hub') {
            steps {
                // Étape de publication des images Docker sur Docker Hub
                // Utilisez les informations d'identification Docker Hub
            }
        }

        stage('Docker Compose') {
            steps {
                // Étape de déploiement avec Docker Compose
                // Utilisez un fichier Docker Compose pour spécifier les services et les configurations
            }
        }

        stage('Email') {
            steps {
                // Étape d'envoi de notifications par courrier électronique
                // Utilisez la configuration du serveur de messagerie et envoyez des e-mails
            }
        }

        stage('Grafana & Prometheus') {
            steps {
                // Étape de déploiement de Grafana et Prometheus
                // Utilisez les fichiers Docker Compose appropriés pour le déploiement
            }

    }


      post {
        always {
            emailext subject: 'Results for Jenkins',
                body: 'success.',
                to: 'amal.trabelsi@esprit.tn',
                recipientProviders: [culprits(), developers(), brokenBuildSuspects()]
        }
      }*/

   }
}

