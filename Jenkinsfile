pipeline {
  agent none
    // environment {
      // SEMGREP_BASELINE_REF = "main"

      // SEMGREP_APP_TOKEN = credentials('SEMGREP_APP_TOKEN')
      // SEMGREP_REPO_URL = env.GIT_URL.replaceFirst(/^(.*).git$/,'$1')
      // SEMGREP_BRANCH = "${GIT_BRANCH}"
      // SEMGREP_JOB_URL = "${BUILD_URL}"
      // SEMGREP_REPO_NAME = env.GIT_URL.replaceFirst(/^https:\/\/github.com\/(.*).git$/, '$1')
      // SEMGREP_COMMIT = "${GIT_COMMIT}"
      // SEMGREP_PR_ID = "${env.CHANGE_ID}"

      // SEMGREP_TIMEOUT = "300"
    // }
    stages{
        stage('SonarQube Analysis')
      {
        agent{
          label 'main'
        }
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
    
  //   stages {
  //     stage('Semgrep-Scan') {
  //       steps {
  //         //sh 'pip3 install semgrep'
  //         //sh 'python3 -V'
  //         //sh 'pip3 install semgrep'
  //         //sh 'semgrep ci --config auto'
  //         sh 'rm -rf $HOME/monica'
  //         sh 'cd $HOME && git clone https://github.com/offsecdawn/monica.git && cd monica && git clone https://github.com/returntocorp/semgrep-rules.git && docker run --rm -v "${PWD}:/src" returntocorp/semgrep semgrep --config "/src/semgrep-rules/php"'
         
  //     }
  //   }
  // }
}
