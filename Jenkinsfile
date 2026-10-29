
@Library('Shared') _

pipeline {
    agent { label 'mehboob' }

    stages {
        stage('Hello') {
            steps {
                script {
                    hello()
                }
            }
        }

        stage('Code') {
            steps {
                script {
                    clone(
                        'https://github.com/Mehboob0462/django-notes-app.git',
                        'main'
                    )
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    docker_build('django-notes-app', 'latest', 'mehboob0462')
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker_push('django-notes-app', 'latest', 'mehboob0462')
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application'
                sh 'docker compose down && compose up -d'
            }
        }
    }
}
