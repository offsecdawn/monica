pipeline .
{
    agent any
    stages {
        stage('SCM') {
            steps {
                git url: 'https://github.com/offsecdawn/monica.git'
            }
        }
        stage('build && SonarQube analysis') 
        {
            steps
            {
            script
            {
                scannerHome = tool 'SonarQubeScanner_4.7.0.2747'
            }
            withSonarQubeEnv('SonarQube') // the SonarQube server name comes from jenkins->manage jenkins-> sonarQube servers
            {
                sh "${scannerHome}/bin/sonar-scanner"
            }
            }
        }
    }
}