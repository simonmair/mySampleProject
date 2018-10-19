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
    }
}
