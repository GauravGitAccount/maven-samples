pipeline {
    agent {
        label 'docker'
    }
    
    options { 
        skipDefaultCheckout() 
    }
    
    stages {
        stage('Build') {
            steps {
                script {
                    sh "git clone https://github.com/GauravGitAccount/maven-samples"
                    sh "cd ./maven-samples"
                    //echo sh(script:'env|sort',returnStdout:true)
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
