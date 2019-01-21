pipeline {
    agent any
    stages {
        stage('input required') {
            steps {
                #!/bin/sh

                java -Xms1500m -Xmx1500m -server -Djava.awt.headless=true -Xdebug \
                -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=4509 \
                -XX:NewRatio=1 -XX:+UseConcMarkSweepGC -XX:ParallelGCThreads=2 -Djackrabbit.maxQueuedEvents=1000000 \
                -DauthEnabled=true \
                -jar cq-publish-4503.jar  \
                -r publish,local,dynamicmedia -v -nofork -ll 3

                #  1>/dev/null 2>/dev/null &

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
