pipeline {
    agent any
    stages {
        stage('input required') {
            steps {
                sh '-R | grep "^[.]/" | sed -e "s/:$//" -e "s/[^/]*[/]/--/g" -e "s/^/   |/"'
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
            mail to: 'spencer.c.mulligan@ey.com',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}
