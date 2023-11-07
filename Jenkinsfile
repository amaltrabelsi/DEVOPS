pipeline {
    agent any

    stages {
        stage('checkout'){
            steps {
                dir('back'){
                checkout scm }}
        }
        stage('git') {
            steps {
                  dir('back'){
                // Cloner le référentiel depuis votre système de contrôle de version
                  git branch: 'main', url : 'https://github.com/amaltrabelsi/DEVOPS.git'}
                  }
        }
        stage('Construction') {
            steps {
                  dir('back'){
                // Exécuter votre processus de construction (par exemple, Maven, Gradle, etc.)
                sh 'mvn clean package'}
            }
        }
        stage('Tests') {
            steps {
                  dir('back'){
                // Exécuter vos tests unitaires ou tests d'intégration
                sh 'mvn test'}
            }
        }
       stage('sonarqube') {
           steps {
                 dir('back'){
           withSonarQubeEnv('sonarserver') {
                                      sh 'mvn sonar:sonar -Dsonar.java.binaries=target/classes'}
           }
           }
       }
        //
      // stage('Déploiement') {
      //       steps {
          dir('back'){
      //           // Déployer votre application sur un serveur ou une plateforme spécifique
      //           sh 'mvn deploy' }
      //       }
      //   }
    }
}
