pipeline {
    agent any
       tools{
        nodejs "npm"
    }

    stages {
        
        stage('checkout'){
            steps {
                dir('back'){
                checkout scm }}
        }
        stage('git') {
            steps {
                dir('back'){
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
             post {
        failure {
            script {
                emailext(
                    subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                    body: "The pipeline has failed. Please check the console output for details.",
                    to: 'amaltr21@gmail.com',
                    attachLog: true,
                )
            }
        }
        
        success {
            script {
                emailext(
                    subject: "Pipeline Succeeded: ${currentBuild.fullDisplayName}",
                    body: "The pipeline has succeeded. You can view the results at ${BUILD_URL}",
                    to: 'amaltr21@gmail.com',
                    attachLog: true,
                )
            }
        }
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
        stage('Nexus') {
                           
            steps {
                 dir('back'){
              sh 'mvn deploy'
            }
               
            }
               
            }
     stage("docker image back "){
            steps {
                  dir('back'){
                script{
                    sh 'docker build -t devops . '
                    sh'docker tag devops amal/devops'

                }}
               
            }
           
        }
            stage("docker image front "){
            steps {
                  dir('front'){
                script{
                    sh 'docker build -t devopsfront . '
                    sh'docker tag devops amal/devops'

                }}
               
            }
           
        }
      
     
        


       /* stage('Build Angular App') {
    
            steps {
                dir('front'){
                   sh ' rm -rf node_modules'
                    sh 'npm install'
                    
                   sh' npm install @angular-devkit/build-angular --force'

                   
                        sh 'npm run build'}
            }
        }

        stage('Archive Artifacts') {
               
            steps {
                  dir('front'){
                archiveArtifacts artifacts: 'dist/*', allowEmptyArchive: true
            }}
        
    

    post {
        success {
            echo 'Build and archiving successful!'
        }
    }
        }*/
       
        //
      // stage('Déploiement') {
      //       steps {
      //           // Déployer votre application sur un serveur ou une plateforme spécifique
      //           sh 'mvn deploy'
      //       }
      //   }
    }
}

