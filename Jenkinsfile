pipeline{
    agent{
        label "nodejs"
            }
          
        stages{
        stage('Checkout') {
            git credentialsId: GITHUB_TOKEN
        }
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
