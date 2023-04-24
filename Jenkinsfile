pipeline {
    agent any 
    stages {
        stage('Complie & Clean') { 
            steps {
                sh "mvn clean compile"
            }
        }
        stage('Test') { 
            steps {
                sh "mvn test"
            }
            post { 
               always { 
                junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'
              }
            }    
        }
        stage('Deploy') { 
            steps {
                sh "mvn package" 
            }
        }
        stage('Archiving') { 
            steps {
                archiveArtifacts '**/target/*.jar' 
            }
        }
    }
}
