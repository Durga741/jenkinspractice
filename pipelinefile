pipeline{
    agent any
    stages
    {
        stage('continous download')
        {
            steps{git 'https://github.com/Durga741/dev.git'}
        }

         stage('continous build')
        {
            steps{sh 'mvn package'}
        }
         stage('continous delpoy')
        {
            steps{deploy adapters: [tomcat9(credentialsId: '4135eced-c942-4bbb-9eb7-4e60f2822659', path: '', url: 'http://172.31.10.37:8080')], contextPath: 'testapp', war: '**/*.war'}
        }

         stage('continous test')
        {
            steps{git 'https://github.com/Durga741/testing.git'
            
            sh 'java -jar /var/lib/jenkins/workspace/development/testing.jar'}
        }
         stage('continous devlivery')
        {
            steps{deploy adapters: [tomcat9(credentialsId: '4135eced-c942-4bbb-9eb7-4e60f2822659', path: '', url: 'http://172.31.5.15:8080')], contextPath: 'prodapp', war: '**/*.war'}
        }
       
        }
        }

