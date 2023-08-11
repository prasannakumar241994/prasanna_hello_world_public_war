pipeline{
    agent { label 'maven'
          }
    stages{
        stage('checkout'){
           steps{
               git branch: 'main', url: 'https://github.com/prasannakumar241994/prasanna_hello_world_public_war.git'
           } 
        }
        
        stage('create binaries'){
            steps{
                sh "mvn clean install"
                }
        }
        stage('create docker image'){
            steps{
                sh "docker build -t prasanna:latest ."
                sh "docker tag prasanna:latest prasannakumar24/prasanna:test-deploy_${BUILD_NUMBER}"
                sh "docker push prasannakumar24/prasanna:test-deploy_${BUILD_NUMBER}"
            }
        }
    }
}
