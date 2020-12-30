pipeline{
    agent any
    stages{
        stage('SCM'){
            steps{
                git credentialsId: 'github', url: 'https://github.com/devaramane/JavaHome'
            }
        }
        stage('Maven_Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage(Tomcat_Deploy){
            steps{
               sh "mv target/myweb*.war target/myweb.war"
                sshagent(['slave-1']) {
                    sh "scp -o StrictHostKeyChecking=no target/myweb.war ec2-user@172.31.38.248:/opt/tomcat8/webapps"
                
}
            }
        }
        }
    }
