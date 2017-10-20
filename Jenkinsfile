pipeline {
    agent any 

    stages {
        stage('Build') { 
            steps { 
                sh 'mvn clean -DskipTests package -U' 
            }
        }
        stage('Test'){
            steps {
                sh 'mvn test pmd:pmd'
                junit 'target/surefire-reports/*.xml' 
                pmd canRunOnFailed: true, pattern: 'target/pmd.xml'
                
            }
            step([$class: 'PmdPublisher', pattern: '**/target/pmd.xml', unstableTotalAll:'0'])
        }
        stage('Deploy') {
            steps {
                sh 'echo "No docker, no cry ;)"'
            }
        }
    }
    post {
        always {
            archive 'target/*.jar'
        }
    }
}
