pipeline {
    agent any
     environment {
            CI = 'true'
        }
    stages {
        agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }


        // stage('Test') {
        //             steps {
        //                 sh "chmod -R +x ./jenkins/scripts/"
        //                 sh './jenkins/scripts/test.sh'
        //             }
        //         }
        //         stage('Deliver') {
        //                     steps {
                               
        //                         sh './jenkins/scripts/deliver.sh'
        //                         input message: 'Finished using the web site? (Click "Proceed" to continue)'
        //                         sh './jenkins/scripts/kill.sh'
        //                     }
        //                 }

        }
    post {
        always {
            archiveArtifacts artifacts: 'build/libs/', fingerprint: true
            // junit 'build/reports/**/*.xml'
        }
    }
    
}
