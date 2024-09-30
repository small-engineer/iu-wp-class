pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('my-wordpress-app')
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    docker.withRegistry('', 'docker-credentials') {
                        docker.image('my-wordpress-app').push('latest')
                    }
                }
            }
        }

        stage('Clean up') {
            steps {
                script {
                    docker.image('my-wordpress-app').remove()
                }
            }
        }
    }
}

