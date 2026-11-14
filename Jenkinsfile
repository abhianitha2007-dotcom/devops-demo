pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'chmod +x mvnw'
                sh '''
                    export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
                    export PATH=$JAVA_HOME/bin:$PATH
                    java -version
                    ./mvnw clean verify
                '''
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            echo 'Build completed successfully!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
