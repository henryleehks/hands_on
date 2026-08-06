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

        stage('Deploy') {
            steps {
                sh '''
                    sudo mkdir -p /opt/spring-boot-hello-world-main/henry
                    sudo cp spring-boot-hello-world-main/target/*.jar \
                            /opt/spring-boot-hello-world-main/henry/
                '''
            }
        }
    }
}