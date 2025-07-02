pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/bhikshu/AWSTUT.git', branch: 'dev1' // Replace with your repo details
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("bhikshu010/awsdevops:testimage_${env.BUILD_NUMBER}", '.') // Build with tag based on build number
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'Dockerhubids') { // Replace with your registry URL and credentials
                        docker.image("bhikshu010/awsdevops:testimage_${env.BUILD_NUMBER}").push()
                    }
                }
            }
        }
    }
}
