pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'berdmikhail/practice-app'
        DOCKER_CREDS = credentials('dockerhub-credentials')
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:${BUILD_NUMBER} -t $DOCKER_IMAGE:latest .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                sh '''
                    echo "$DOCKER_CREDS_PSW" | docker login -u "$DOCKER_CREDS_USR" --password-stdin
                    docker push $DOCKER_IMAGE:${BUILD_NUMBER}
                    docker push $DOCKER_IMAGE:latest
                '''
            }
        }
    }
    post {
        always {
            sh 'docker logout || true'
        }
    }
}
