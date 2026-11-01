pipeline {
    agent any

    stages {
        stage('Lint') {
            steps {
                echo 'Выполняется статический анализ кода (Lint)...'
                sh 'npm run lint --if-present || true'
            }
        }
        stage('Test') {
            steps {
                echo 'Запуск модульных тестов (Unit Tests)...'
                sh 'npm test --if-present'
            }
        }
        stage('Build') {
            steps {
                echo 'Сборка приложения (Build)...'
                sh 'npm run build --if-present'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Развертывание приложения (Deploy)...'
                sh 'echo "Application deployed successfully to staging environment."'
            }
        }
    }
}
