pipeline {
    agent any
    stages {
        stage('Récupération du code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Colin-baz/landing-page-example'
            }
        }
        stage('Déploiement') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'alwaysdata-ssh',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    sh '''
                        sshpass -p "$PASS" scp -o StrictHostKeyChecking=no -r index.html $USER@ssh-colin.alwaysdata.net:~/www
                    '''
                }
            }
        }
    }
}
