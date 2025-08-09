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
                // sh 'echo "Using credentials: $MY_APP_CRED"'
                // sh 'echo "Using credentials: $MY_APP_CRED_USR"'
                // sh 'echo "Using credentials: $MY_APP_CRED_PWD"'
            }
            withCredentials([usernamePassword(credentialsId: 'expired-cred-admin', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                sh 'echo "Username: $USERNAME"'
                sh 'echo "Password: $PASSWORD"'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                // sh('echo "Using credentials: $MY_APP_CRED"')
                // sh 'echo "Using credentials: $MY_APP_CRED_USR"'
                // sh 'echo "Using credentials: $MY_APP_CRED_PWD"'
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