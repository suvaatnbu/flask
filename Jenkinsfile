pipeline {
    agent any

    environment {
        VENV_DIR = 'venv'
    }

    stages {
        stage('Build') {
            steps {
                echo '🔧 Installing dependencies...'
                sh '''
                    python3 -m venv $VENV_DIR
                    . $VENV_DIR/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running unit tests...'
                sh '''
                    . $VENV_DIR/bin/activate
                    pytest || true  # Replace with your actual test logic
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying to staging...'
                sh '''
                    echo "Deployment simulated."
                '''
            }
        }
    }

    post {
        success {
            mail to: 'suvaatnbu@gmail.com',
                 subject: "✅ Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Build passed: ${env.BUILD_URL}"
        }
        failure {
            mail to: 'suvaatnbu@gmail.com',
                 subject: "❌ Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Build failed: ${env.BUILD_URL}"
        }
    }
}

