pipeline {
    agent any
    stages {
        stage('Git-checkout') {
            steps {
                echo "Checking out from Git repo";
                git 'https://github.com/duongvuong2610/scripted_pipeline.git'
            }
        }
        stage('Build') {
            steps {
                echo "Building the check-out project";
                bat 'build.bat'
            }
        }
        stage('Unit test') {
            steps {
                echo "Running JUnit tests";
                bat 'junit.bat'
            }
        }
        stage('Quality-Gate') {
            steps {
                echo "Verifying Quality Gates";
                bat 'quality.bat'
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying to Stage Enviroment for more tests";
                bat 'deploy.bat'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
