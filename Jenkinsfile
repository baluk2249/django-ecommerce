pipeline{
    agent any
    environment {
        DOCKER_IMAGE ='baluk2249/django-ecommerce'
        BUILD_NUMBER ='v2'
    }
    stages{

        stage ('checout'){
            steps {
                git 'https://github.com/baluk2249/django-ecommerce.git'
            }
        }
        stage('Build'){
            steps{
                script{
                    docker.build("${env.DOCKER_IMAGE}:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Push Docker Image')
        {
            steps {
                script{
                    docker.image("${env.DOCKER_IMAGE}:${env.BUILD_NUMBER}").push()
                }
            }
        }
    }

    post{
        always {
            cleanWs()
        }
    }
}