pipeline{
    agent{
        label "nodejs"
        credentialsId: 'GITHUB_TOKEN'
    }
    stages{
        stage("Install dependencies"){
            steps{
                sh "npm ci"
            }
        }

        stage("Check Style"){
            steps{
                sh "npm run lint"
            }
        }

        stage("Test"){
            steps{
                sh "npm test"
            }
        }

        stage('Deploy') {
            steps {
                '''
                oc project xudlbs-greetings
                oc start-build greeting-service --follow --wait
                '''
            }
        }
    }
}
