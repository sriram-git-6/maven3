pipeline
{
    agent any
    stages
    {
        stage ('continous download')
        {
        steps
        {
        git 'https://github.com/intelliqittrainings/maven.git'
        }
      }
        stage('continous build')
        {
        steps
        {
            sh 'mvn package'
        }
        }
        stage('continous deployment')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/dc-pipeline/webapp/target/webapp.war ubuntu@172.31.0.13:/var/lib/tomcat8/webapps/'
            }
        }
        stage('continous testing')
        {
         steps
         {
             git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
             sh 'java -jar /home/ubuntu/.jenkins/workspace/dc-pipeline/testing.jar'
         }
        }
        stage('continous delivery')
        {
            steps
            {
                sh 'scp /home/ubuntu/.jenkins/workspace/dc-pipeline/webapp/target/webapp.war ubuntu@172.31.12.198:/var/lib/tomcat8/webapps/'
            }
        }
        }
    }


