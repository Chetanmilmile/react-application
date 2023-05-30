pipeline {
    agent any
     environment {
            CI = 'true'
        }
    stages {
        
        stage('Build') {
            agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
            steps {
                sh 'npm install'
            }
            steps {
                sh 'npm build'
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
            archiveArtifacts artifacts: 'dist/*.*', fingerprint: true
            // junit 'build/reports/**/*.xml'
        }
    }
    
}
