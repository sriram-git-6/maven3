node('master') 
{
    stage('continous download') 
    {
    git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('continous build')
    {
    sh 'mvn package'
    }
    stage('continous deployment')
    {
    input message: 'waiting for appproval from DM', submitter: 'sriram'
    sh 'scp /home/ubuntu/.jenkins/workspace/scripted/webapp/target/webapp.war ubuntu@172.31.0.13:/var/lib/tomcat8/webapps'
    }
    stage('continous testing')
    {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git' 
       sh 'java -jar /home/ubuntu/.jenkins/workspace/scripted/testing.jar'
    }
    stage('continous delivery')
    {
     sh 'scp /home/ubuntu/.jenkins/workspace/scripted/webapp/target/webapp.war ubuntu@172.31.12.198:/var/lib/tomcat8/webapps'
    }
}

