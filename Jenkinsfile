pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "clients-api"
        REGISTRY = "docker.io/yourusername"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/your-org/clients-api.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t $REGISTRY/$DOCKER_IMAGE:$BUILD_NUMBER .'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test' // adjust based on project
            }
        }

        stage('Push Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'echo $PASSWORD | docker login -u $USERNAME --password-stdin'
                    sh 'docker push $REGISTRY/$DOCKER_IMAGE:$BUILD_NUMBER'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
    }
}
