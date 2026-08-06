pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                dir('spring-boot-hello-world-main') {
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                dir('spring-boot-hello-world-main') {
                    sh 'mvn test'
                }
            }
        }

        stage('Copy JAR') {
            steps {
                sh '''
                    mkdir -p spring-boot-hello-world-main/henry
                    cp spring-boot-hello-world-main/target/*.jar /tmp/henry
                '''
            }
        }
    }
}