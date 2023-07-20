pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Meenakshi0812/jenkins-ec2.git'
            }
        }
       
        stage('Deploy') {
            steps {
                sshagent(['ssh-public-key']) {
                    sh """
                        ssh -o StrictHostKeyChecking=no -i /Users/sarithagannapaneni/Downloads/saritha_accessKeys.csv ec2-user@ec2-3-80-189-132.compute-1.amazonaws.com
                        sudo cp -r  /home/ec2-user/jenkins-ec2/date.php  /var/www/htm
                    """
                }
            }
        }
    }
}
