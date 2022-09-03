pipeline {

    agent {
        node {
            label 'master'
        }
    }

    options {
        buildDiscarder logRotator(
                daysToKeepStr: '16',
                numToKeepStr: '10'
        )
    }

    environment {
        user = 'admin'
        password = 'rj2slcxjexa3n5v5rssw'
        env = 'smsoft'
    }

    stages {

        stage('Publish') {
            steps {
                bat '''
                    apictl login ${env} -u ${user} -p ${password} -k
                    apictl vcs deploy -e env
                '''
            }
        }


    }
    post {
        bat '''
                    apictl logout
                '''
    }
}