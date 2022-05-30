pipeline {
    agent any

    tools {
        
        maven "maven-3.8.5"
    }

    stages {
        stage('Build') {
            steps {
               
                git branch: 'main', url: 'https://github.com/vytec-ordermgt/trace.git'

                
                sh "mvn -Dmaven.test.failure.ignore=true clean install"

               
            }

            post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}
