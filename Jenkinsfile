pipeline {
    agent any 

    stages {
        stage('Build') { 
            steps { 
                sh 'mvn clean -DskipTest -U package' 
            }
        }
        stage('Test'){
            steps {
                sh 'mvn test'
                junit 'target/surefire-reports/*.xml' 
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying artifact to Nexus Repository"'
                sh 'mvn -DskipTest deploy'
            }
        }
    }
}
