pipeline 
{
    agent any
    environment 
    {
      SEMGREP_APP_TOKEN = ""
      SEMGREP_REPO_URL = env.GIT_URL.replaceFirst(/^(.*).git$/,'$1')
      SEMGREP_BRANCH = "${GIT_BRANCH}"
      SEMGREP_JOB_URL = "${BUILD_URL}"
      SEMGREP_REPO_NAME = env.GIT_URL.replaceFirst(/^https:\/\/github.com\/(.*).git$/, '$1')
      SEMGREP_COMMIT = "${GIT_COMMIT}"
      SEMGREP_PR_ID = "${env.CHANGE_ID}"
    }
    stages 
    {
        stage('Semgrep-Scan') 
        {
            steps 
            {
                sh 'printenv'
                sh 'pip3 install semgrep'
                // sh 'semgrep ci' 
                // /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin
                sh 'semgrep ci'

            }
        }
        stage('SonarQube analysis') 
        {
            //requires SonarQube Scanner 2.8+  
            steps
	        {
		        script
		        {
			        //requires SonarQube Scanner 2.8+
			        scannerHome = tool 'SonarQubeScanner_4.7'
		        }       
		        withSonarQubeEnv('SonarQube') // the SonarQube server name comes from jenkins->manage jenkins-> sonarQube servers
		        {
		        	sh "${scannerHome}/bin/sonar-scanner -X"
		        }
	        } 
        }        
    }   
}
