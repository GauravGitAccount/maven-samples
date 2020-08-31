pipeline {
    agent {
        label 'docker'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh "git credentialsId: '4fbc3666-dac6-48ff-aec5-310096b93f6f', url: 'https://github.com/GauravGitAccount/maven-samples.git'"
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
