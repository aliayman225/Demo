pipeline {
    agent any
    environment {
        NODE_ENV = 'production'
        BRANCH_NAME = "${env.BRANCH_NAME}"   
      
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('build Docker Image') {
            steps {
                //sh  "docker.build ${DOCKER_REGISTRY} ${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}/${env.BRANCH_NAME}"
                //sh "docker login -u ${JFROG_USERNAME} -p ${JFROG_PASSWORD} ${DOCKER_REGISTRY}"
                //sh "docker login -u $JF_REGISTRY_USER -p $JFROG_PASSWORD"
                //sh "docker login -u admin -p password http://192.168.1.10:8082/artifactory/devops"
                sh "docker login -u admin -p Passw0rd http://192.168.146.132:8082/artifactory/test"

                //sh "docker build -f Dockerfile . -t app admin/devops:${BUILD_NUMBER}"
                  sh "docker build -f Dockerfile . -t  192.168.146.132:8082/test/app:${BUILD_NUMBER}"
                
            }
        }
        stage('Push Docker Image') {
            steps {
                //sh "docker push devops:$BUILD_NUMBER"
                sh "docker push 192.168.146.132:8082/test/app:${BUILD_NUMBER}"
                //sh "docker push 192.168.146.132:8082/test/app:${BUILD_NUMBER}"
                
                //sh  "docker.push ${DOCKER_REGISTRY}/${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}/${env.BRANCH_NAME}"
            }
        }
    }   //}
}
