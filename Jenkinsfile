pipeline {
   agent any
   stages {
        stage('Git clone') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/dev']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'github-password', url: 'https://github.com/balavenkateshnp/test-react.git']]])

            }
        }  
        
        
       stage ('dev codes receiving!') {
            steps{
                sshagent(credentials : ['elk-server']) {
                sh 'ssh -o StrictHostKeyChecking=no root@103.77.232.85 git -C /var/www/html/test-react/ pull'
                 }
                 }
                         }   
           }
           }
