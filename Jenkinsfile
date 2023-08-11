pipeline {
    agent { label 'maven'
    }
    stages {
         stage('checkout') {
             steps {
                cleanWs()
              git 'https://github.com/prasannakumar241994/ravdy-hello-world.git'
             }
         }
        stage('compile') {
            steps {
                sh 'mvn clean install'
            }
       }
       stage('tomcat image') {
           steps {
               sh "docker stop 6865615e7bda"
               sh "docker rmi tomcat:1.0"
               sh "docker build -t tomcat:2.0 -f Dockerfile ."
       }
   }   
     stage('tomcat container') {
         steps {
             sh "sudo chmod 666 /var/run/docker.sock "
             sh "docker rm tomcat_cont1"
             sh "docker run -i --name tomcat_cont1 -p 8080:8080 tomcat:1.0"
             sh "docker ps"
         }
     }
   }
}
