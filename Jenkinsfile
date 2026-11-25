
pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                bat 'node -v'
                bat 'npm -v'
                bat 'npm ci'
            }
        }

        stage('Test') {
            steps {
                bat 'npm test'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                if exist "C:\\JenkinsDeploy\\React-Jenkins-CICD" (
                    rmdir /s /q "C:\\JenkinsDeploy\\React-Jenkins-CICD"
                )

                mkdir "C:\\JenkinsDeploy\\React-Jenkins-CICD"

                xcopy /E /I /Y "build\*" "C:\JenkinsDeploy\React-Jenkins-CICD\"

                if errorlevel 2 exit /b 1
                '''
            }
        }
    }
}
 