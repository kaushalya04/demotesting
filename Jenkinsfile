pipeline {
    agent any

    stages {

        stage('Get code from GITHUB') {
            steps {
                git 'https://github.com/kaushalya04/demotesting.git'
            }
        }

        stage('Complile') {
            steps {
                sh "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/mymaven/bin/mvn compile"
            }
        }

        stage('Test') {
            steps {
                sh "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/mymaven/bin/mvn test"
            }
        }

        stage('Package') {
            steps {
                sh "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/mymaven/bin/mvn package"
            }
        }

        stage('Deploy') {
            steps {
                sh "sudo cp /var/lib/jenkins/workspace/samplejobpackage/target/addressbook.war /usr/share/tomcat/webapps/"
                sh "sudo systemctl stop tomcat"
                sh "sudo rm -rf /usr/share/tomcat/webapps/addressbook"
                sh "sudo systemctl start tomcat"
            }
        }
    }
}
