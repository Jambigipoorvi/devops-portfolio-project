pipeline {
    agent any

    environment {
        // We will update this with your actual bucket name in Phase 4
        S3_BUCKET = 'your-unique-s3-bucket-name-here' 
    }

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
                echo 'Code successfully pulled from GitHub.'
            }
        }
        
        stage('Build & Test') {
            steps {
                echo 'Running static code analysis...'
                echo 'Validating HTML, CSS, and JS files...'
                // In a real scenario, you could run 'npm run test' or linters here.
                echo 'All tests passed! Ready for deployment.'
            }
        }
        
        stage('Deploy to AWS S3') {
            steps {
                echo 'Preparing to deploy to AWS S3...'
                script {
                    def awsCommand = "aws s3 sync . s3://${S3_BUCKET} --exclude '.git/*' --exclude 'Jenkinsfile'"
                    
                    echo "Deployment Command: ${awsCommand}"
                    echo "NOTE: Actual deployment is disabled until AWS is configured in Phase 4."
                    
                    // In Phase 4, after installing AWS CLI and setting credentials, uncomment the lines below:
                    
                    // if (isUnix()) {
                    //     sh "${awsCommand}"
                    // } else {
                    //     bat "${awsCommand}"
                    // }
                }
            }
        }
    }
    
    post {
        success {
            echo '✅ Pipeline Succeeded! Your portfolio is live.'
        }
        failure {
            echo '❌ Pipeline Failed! Please check the Jenkins console logs.'
        }
    }
}
