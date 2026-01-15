pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/YOUR_USERNAME/two-tier-flask-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'python3 -m py_compile app.py'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                pkill -f app.py || true
                nohup python3 app.py > app.log 2>&1 &
                '''
            }
        }
    }
}
