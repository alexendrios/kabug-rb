pipeline {
    agent {
        docker {
            image 'qaninja/rubywd'
        }
    }
    
    stages{
        stage('Build'){
            steps{
                echo 'Building or Resolve Depencencies'
                sh 'bundle install'
            }
        }
        stage('Test'){
            steps{
                echo 'Running regression tests'
                sh 'bundle exec cucumber -p ci'
            }
        }
        stage('UAT'){
            steps{
                echo 'Wait for use Acceptance'
            }
        }
        stage('Prod'){
            steps{
                echo 'WebApp is Read'
            }
        }
    }
}