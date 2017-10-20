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
                sh 'mvn test'
                junit 'target/surefire-reports/*.xml' 
            }
        }
        stage('CodeAnalysis') {
            steps {
                sh 'mvn pmd:pmd'
                step([$class: 'hudson.plugins.pmd.PmdPublisher', checkstyle: '**/target/pmd.xml'])
            }
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
