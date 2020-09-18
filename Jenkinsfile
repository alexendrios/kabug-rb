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
                sh 'rm -f Gemfile.lock'
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
                cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: '**/*.json', jsonReportDirectory: 'logs', pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1
            }
        }
        stage('Prod'){
            steps{
                echo 'WebApp is Read'
            }
        }
    }
}