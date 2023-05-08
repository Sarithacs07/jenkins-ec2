pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], 
                          userRemoteConfigs: [[url: 'https://github.com/Meenakshi0812/jenkins-ec2.git']]])
            }
        }
        stage('Deploy') {
            environment {
                SSH_KEY = credentials('ssh-cred')
                HOST = 'ec2-user@ec2-54-167-35-145.compute-1.amazonaws.com'
            }
            steps {
                sshagent(credentials: ['ssh-key']) {
                    sh "scp -r ./<path-to-your-php-code>/* ec2-user@${HOST}:/var/www/html/"
                }
            }
        }
    }
}
