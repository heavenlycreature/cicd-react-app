pipeline{
    agent{
        docker{
            image 'node:16-buster-slim'
            args '-p 3000:3000'
        }
    }
    stages{
        stage('build') {
            steps {
                sh 'npm install'
            }
        }
        stage('test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('deploy'){
            steps{
            sh './jenkins/scripts/deliver.sh'
            input message: 'Sudah selesai menggunakan app? (Klik "Proceed" untuk mengakhiri)'
            sh './jenkins/scripts/kill.sh'
            }
        }
    }
}