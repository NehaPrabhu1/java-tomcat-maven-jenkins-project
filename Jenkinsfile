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
            steps{
                echo "Deploying at staging level"
                build job: 'Deploy_App_Staging_Env'
            } 
        }
        stage('Production'){
            steps{
                timeout(5, unit:'DAYS'){
                    input message: 'Approve Prodution Deployment ?'
                }
                echo "Deploying at production level"
            }
        }
    }
}      
