node('master') 
{
     
    stage('ContinuousDownload') 
    {
       git 'https://github.com/selenium-saikrishna/maven.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline
		       /webapp/target/webapp.war vagrant@10.0.0.5:/var/lib
			                              /tomcat7/webapps/qaenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/Functional
		                                                 Testing.git'

    }
    stage('ContinuousDelivery')
    {
        input message: 'Waiting for approval from the DM', 
		                                          submitter: 'Ravi'
        sh 'scp /home/vagrant/.jenkins/workspace/ScriptedPipeline
		         /webapp/target/webapp.war vagrant@10.0.0.6:/var/lib
				                         /tomcat7/webapps/prodenv.war'
    }
}



