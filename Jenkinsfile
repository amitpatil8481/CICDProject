pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'cd webspp && mvn deploy'
      }
    }

    stage('deploy') {
      steps {
        sh '''cd /root/apache-tomcat-9.0.60/bin && ./shutdown.sh

cd /root/apache-tomcat-9.0.60/webapps
wget http://192.168.1.21:10010/repository/maven-snapshots/com/learnwell/app/webspp/1.0-SNAPSHOT/webspp-1.0-20220320.065251-1.war

cd /root/apache-tomcat-9.0.60/bin && ./startup.sh'''
      }
    }

  }
}