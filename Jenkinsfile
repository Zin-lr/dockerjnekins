pipeline {
    agent any
    environment {
       IMG_NAME = 'my-nx'
       REPO_NAME = 'lachgharhub28'
       TAG_NAME =  'latest'
    }
    stages {
        stage('build') {
            steps {
                script {
                        sh 'docker build -t ${REPO_NAME}/${IMG_NAME} .' 
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
                        sh 'docker push ${REPO_NAME}/${IMG_NAME}:${TAG_NAME}'
                    }
                }
            }
        }
    }
}
