pipeline{
  agent any

  stages
  {
    stage('Install npm'){
      steps{
        bat 'npm install'    
      }
    }

    stage('build the project'){
      steps{
        bat 'npm run build'
      }
    }
    stage('Deploy through Jenkins'){
      steps{
        withCredentials([sshUserPrivateKey(credentialsId: 'CounterApp', keyFileVariable: 'SSH_KEY', usernameVariable: 'SSH_USER' )]){
            bat '''
              git config --global user.email "canikissu687@gmail.com"
              git config --global user.name "Venu1433697"
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
