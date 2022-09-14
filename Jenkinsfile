pipeline {
    agent any
    stages {
        stage('Build Application') {
            steps {
                sh 'mvn -f pom.xml clean package'
            }
            post {
                success {
                    echo "Now Archiving the Artifacts...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('QA Staging'){
            echo "Deploying at staging level"
            build 'Deploy_App_Staging_Env'

        }
        stage('Production'){
            echo "Deploying at production level"

        }
    }
}      
