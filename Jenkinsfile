pipeline {
  agent any
    stages{
        stage('SonarQube Analysis')
      // {
      //   agent{
      //     label 'main'
      //   }
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

