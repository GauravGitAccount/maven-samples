pipeline {
    agent {
        label 'docker'
    }
    stages {
        stage('Checkout') {
            steps {
                git credentialsId: '4fbc3666-dac6-48ff-aec5-310096b93f6f', url: 'https://github.com/GauravGitAccount/maven-samples.git'
                checkout scm
            }
        }
        stage('Git Checkout') { 
          steps {
              sh "which git"
            checkout(
                [$class: 'GitSCM', 
                branches: [[name: '*/dev']], 
                doGenerateSubmoduleConfigurations: false,
                extensions: [], 
                submoduleCfg: [], 
                userRemoteConfigs: [[credentialsId:'4fbc3666-dac6-48ff-aec5-310096b93f6f',
                                    url:'https://github.com/GauravGitAccount/maven-samples.git']]]
            )
           }
        }  
        /*stage('Build') {
            steps {
                script {
                    echo sh(script:'env|sort',returnStdout:true)
                    sh "mvn clean package"    
                }
                
            }

            post {
                 If Maven was able to run the tests, even if some of the test
                 failed, record the test results and archive the jar file.
                success {
                    junit '**///target/surefire-reports/TEST-*.xml'
                /*}
            }
        }*/
    }
}
