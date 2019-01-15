pipeline {
    agent any
    stages {
        stage('input required') {
            steps {
                sh 'ls'
            }
        }
        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
                echo "Looks not ok to me"
            }
        }
    }
    post {
        always {
            mail to: 'spencer.c.mulligan@ey.com',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}
