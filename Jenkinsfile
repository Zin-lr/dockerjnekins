pipeline {
    agent any
    environment {
        IMG_NAME = 'my-nx'
        DOCKER_REPO = 'joska99/labs-images'
    }
    stages {
        stage('build') {
            steps {
                script {
                        sh 'docker build -t ${IMG_NAME} .'
                        sh 'docker tag ${IMG_NAME} ${DOCKER_REPO}:${IMG_NAME}'
                }
            }
        }
        stage('push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHub-LG1', passwordVariable: 'lachgharhub@28', usernameVariable: 'lachgharhub28')]) {
                    script {
                        sh 'echo ${PSWD} | docker login -u ${LOGIN} --password-stdin'
                        sh 'docker push ${DOCKER_REPO}:${IMG_NAME}'
                    }
                }
            }
        }
    }
}
