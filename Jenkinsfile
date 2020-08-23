pipeline {
    agent {
        label 'git'
    }
    stages {
        stage('checkout') {
            steps {
                script {
                    sh "git version"
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    echo sh(script:'env|sort',returnStdout:true)
                    sh "mvn clean package"    
                }
                
            }

            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
    }
}
