pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                echo 'Cleaning up old containers...'
                script {
                    // Failsafe cleanup
                    sh 'docker stop samplerunning || true'
                    sh 'docker rm samplerunning || true'
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image...'
                // Hier roepen we jouw sample-app.sh aan
                sh 'bash sample-app.sh'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application...'
                // Check of app draait
                sh 'sleep 5' // even wachten tot container draait
                sh 'curl -f http://localhost:5050 || exit 1'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Application successfully deployed!'
            }
        }
    }
}
