pipeline {
    agent { docker { image 'gitguardian/ggshield:latest' } }
        
    stages {
        stage('GitGuardian Scan') {
            environment {
                CI = 'true'
            }
            steps {
                echo "Starting analysis with GitGuardian"
                withCredentials([string(credentialsId: 'gitguardian-api-key', variable: 'GITGUARDIAN_API_KEY')]) {
                    sh 'ggshield scan -v ci'
                }
            }
        }
    }
}
