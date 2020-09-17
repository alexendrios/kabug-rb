pipeline {
    agent {
        docker {
            image 'ruby'
        }
    }
    
    stages{
        stage('Build'){
            steps{
                echo 'Building or Resolve Depencencies'
            }
        }
        stage('Test'){
            steps{
                echo 'Running regression tests'
                sh 'bundle install'
            }
        }
        stage('UAT'){
            steps{
                echo 'Wait for use Acceptance'
                input(message: 'Go to production?', ok: 'Yes')
            }
        }
        stage('Prod'){
            steps{
                echo 'WebApp is Read'
            }
        }
    }
}