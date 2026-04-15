pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage ('Checkout'){
            steps {
                git branch: 'master', url:"https://github.com/rochith11/test.git"
            }
        }
        stage ('Build')
        {
            steps {
                sh 'mvn clean install'
            }
        }
       stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn clean package'
            }
        }   
    }
    post {
        success {
            echo "Build Successful"
        }
        failure {
            echo "Build Unsuccessful"
        }
    }
}