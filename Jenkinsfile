pipeline {
    agent any
    stages {
        stage('input required') {
            steps {
                sh 'cd ../ && cd ../ && cd ../ && cd ../ && find .'
            }
        }
        stage('Sanity check') {
            steps {
                input "Does the staging environment look ok?"
                echo "Change propogation check"
            }
        }
    }
    post {
        always {
            sh 'echo "This always prints"'
        }
    }
}
