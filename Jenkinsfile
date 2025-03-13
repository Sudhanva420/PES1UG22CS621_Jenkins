pipeline {
    agent any
    stages {
        stage('Clone repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    useRemoteConfigs: [[url: 'https://github.com/Sudhanva420/PES1UG22CS621_Jenkins.git']]
                ])
            }
        }
        stage('Build') {
            steps {
                build 'PES1UG22CS621-1'
                sh 'g++ main/new.cpp -o output'
            }
        }
        /* Wrong output code
        stage('Test') {
            steps {
                sh './wrong_output'  // This file does not exist!
            }
        }
        */

        /* Correct test code */
        stage('Test') {
            steps {
                sh './output'
            }
        }

        stage('Deploy') {
            steps {
                echo 'deploy'
            }
        }
    }
    post {
        failure {
            error 'Pipeline failed'
        }
    }
}
