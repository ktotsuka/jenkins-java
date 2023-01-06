/* Requires the Docker Pipeline plugin */
pipeline {
    agent { docker { image 'maven:3.8.7-eclipse-temurin-11' } }
    stages {
        stage('build') {
            steps {
                sh 'javac example.java'
            }
        }
    }
    post {
        success {
            mail to: 'kenji.totsuka@gmail.com',
                subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                body: "Build succeeded for ${env.BUILD_URL}"
        }
        failure {
            mail to: 'kenji.totsuka@gmail.com',
                subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                body: "Something is wrong with ${env.BUILD_URL}"
        }
}
}
