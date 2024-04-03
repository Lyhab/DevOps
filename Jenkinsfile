// pipeline {
//     agent any // windows agent, Jenkins-Laravel (other machine)
    
//     stages {
//         stage('Fetch from GitHub') { // build steps
//             steps {
//                 echo 'Fetching from GitHub'
//                 git branch: 'TP03', url:'https://github.com/Lyhab/DevOps.git'
//             }
//         }
//         stage('Build using Tools') {
//             steps {
//                 echo 'Compiling code...'
//                 sh 'cp .env.example .env'
//                 sh 'composer install && php artisan key:generate && npm install && npm run build'
//             }
//         }
//         stage('Test the app') {
//             steps {
//                 echo 'Testing unit tests...'
//                 echo 'Testing features...'
//                 sh 'php artisan test'
//             }
//         }
//     }
// }

pipeline {
    agent any // windows agent, Jenkins-Laravel (other machine)
    environment {
        BOT_TOKEN = '7018569543:AAGkRz4Tov0rYreb1a6g9r5WTakEFg8JxZs'
        CHAT_ID = '832992624'
    }


    stages {
        stage('Fetch from GitHub') { // build steps
            steps {
                echo 'Fetching from GitHub'
                git branch: 'TP03', url:'https://github.com/Lyhab/DevOps.git'
            }
        }
        stage('Build using Tools') {
            steps {
                echo 'Compiling code...'
                sh 'cp .env.example .env'
                sh 'composer install && php artisan key:generate && npm install && npm run build'
            }
        }
        stage('Test the app') {
            steps {
                echo 'Testing unit tests...'
                echo 'Testing features...'
                sh 'php artisan test'
            }
        }
    }
    post {
        success {
            script {
                sh "bash scripts/deployment.sh SUCCESS"
            }
        }
        failure {
            script {
                sh "bash scripts/deployment.sh FAILED"
            }
        }
    }
}