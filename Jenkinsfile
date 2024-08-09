pipeline{

    agent any

    stages{

        stage('Build Jar'){
            steps{
                sh "mvn clean package -DskipTests"
            }
        }
        stage('Build Image'){
            steps{
                sh "docker build -t=olekg/selenium:latest ."
            }
        }
        stage('Push Image'){
            steps{
                sh "docker push olekg/selenium:latest"
                sh "docker tag olekg/selenium:latest olekg/selenium:${env.BUILD_NUMBER}"
                sh "docker push olekg/selenium:${env.BUILD_NUMBER}"
            }
        }
    }

}
