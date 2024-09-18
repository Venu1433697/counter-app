pipeline{
  agent any

  stages
  {
    stage('Install npm'){
      steps{
        sh 'npm install'    
      }
    }

    stage('build the project'){
      steps{
        sh 'npm run build'
      }
    }
    stage('Deploy through Jenkins'){
      steps{
        withCredentials([sshUserPrivateKey(credentialsId: 'CounterApp', keyFileVariable: 'SSH_KEY', usernameVariable: 'SSH_USER' )]){
            sh '''
              npm run deploy
              mkdir -p ~/.ssh
              ssh-keyscan -H $SSH_HOST >> ~/.ssh/known_hosts
              scp -i $SSH_KEY -r build/* $SSH_USER@$SSH_HOST:/home/ec2-user/CounterApp
              ssh -i $SSH_KEY $SSH_USER@  'sudo systemctl restart httpd'
            '''
        }
      }
    }
  }
}
