pipeline {
    agent any
    environment {
       IMG_NAME = 'lachgharhub28/my-nx'
    }
    stages {
        stage('build') {
            steps {
                script {
                        sh 'docker build -t ${IMG_NAME} .' 
                       //lachgharhub28/my-nx:tagname
                       // sh 'docker tag ${IMG_NAME} ${DOCKER_REPO}'
                }
            }
        }
        stage('push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'DockerHub-LG1', passwordVariable: 'PSWD', usernameVariable: 'LOGIN')]) {
                    script {
                        sh 'echo ${PSWD} | docker login -u ${LOGIN} --password-stdin'
                        sh 'docker push ${IMG_NAME}:latest'
                    }
                }
            }
        }
    }
}
