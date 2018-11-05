node('master') 
{
     
    stage('ContinuousDownload-sprint1') 
    {
       git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('ContinuousBuild-sprint1')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment-sprint1')
    {
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.0.0.5:/var/lib/tomcat7/webapps/qaenv.war'
    }
    stage('ContinuousTesting-sprint1')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'

    }
    stage('ContinuousDelivery-sprint1')
    {
        input message: 'Waiting for approval from the DM',submitter: 'Ravi'
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war vagrant@10.0.0.6:/var/lib/tomcat7/webapps/prodenv.war'
    }
}

