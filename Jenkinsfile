pipeline {
  agent {
    label 'master'
  }
  stages {
    stage('Build') {
      steps {
        sh 'cd webspp && mvn deploy'
      }
    }

    stage('deploy') {
      steps {
        sh '''
cd /root/apache-tomcat-9.0.60/webapps
export artifact_version=`wget -O - -o /dev/null http://192.168.1.21:10010/repository/maven-snapshots/com/learnwell/app/webspp/1.0-SNAPSHOT/maven-metadata.xml | grep value | uniq | grep -Po \'<.*?>\\K.*?(?=<.*?>)\'`
wget -O webspp-1.0-snapshot.war http://192.168.1.21:10010/repository/maven-snapshots/com/learnwell/app/webspp/1.0-SNAPSHOT/webspp-$artifact_version.war

sleep 15
ps -ef | grep tomcat'''
      }
    }

  }
}