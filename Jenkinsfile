pipeline{
    agent any
    tools{ nodejs "nodejs" }
          
        stages{
                  
        stage('Install dependencies'){
            steps{
                sh 'npm ci'
            }
        }

        stage('Check Style'){
            steps{
                sh 'npm run lint'
            }
        }

        stage('Test'){
            steps{
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {

               sh '''
                oc whoami
                oc project xudlbs-deploy-strategies
                oc start-build greeting-service --follow --wait
                '''
            }
        }
    }
}
