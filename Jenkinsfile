pipeline {
    agent any

    environment {
        AWS_DEFAULT_REGION = 'us-east-1'
    }

    stages {
        stage('Build') {
            steps {
                script {
                    def awsCredentials = credentials('your-aws-credentials-id')  // Replace with your actual credentials ID

                    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: awsCredentials.id]]) {
                        sh '''
                        terraform init -upgrade
                        terraform apply -auto-approve
                        '''
                    }
                }
            }
        }
    }
}
