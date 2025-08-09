pipeline {
    agent any
    stages {
        stage('Build') {
            when {
                expression {
                    env.BRANCH_NAME == 'develop' || env.BRANCH_NAME == 'main'
                } 
            }
            steps {
                echo 'Building..'
                sh 'echo "Building on branch: $(which docker)"'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying..'
            }
        }
        stage('Deploy to Production') {
            when {
                expression {
                    BRANCH_NAME == "release"
                }
            }
            steps {
                echo 'Deploying..'
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if the pipeline succeeds'
        }
        failure {
            echo 'This will run only if the pipeline fails'
        }
    }
}