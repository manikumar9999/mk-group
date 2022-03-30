pipeline {
    agent any
    tools{
       maven 'maven-3.8.4' 
    }
    stages{
        stage('git checkout'){
            steps{
              checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/manikumar9999/mk-group.git']]])  
            }
        }
        stage('mvn'){
            steps{
            sh 'mvn clean install package'    
            }
            }
            stage('deploy'){
                steps{
                   deploy adapters: [tomcat9(credentialsId: 'tom', path: '', url: 'http://18.232.149.122:8085/')], contextPath: null, war: '**/*.war' 
                }
            }
    }
}
