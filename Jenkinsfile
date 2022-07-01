pipeline {
    agent any
    stages {
        // stage('SCM') {
        //     steps {
        //         git url: 'https://github.com/offsecdawn/monica.git'
        //     }
        // }
        stage('build && SonarQube analysis') {
            steps {
                script
		        {
                    //requires SonarQube Scanner 2.8+
                    scannerHome = tool 'SonarQubeScanner_2.8'
		        }
                withSonarQubeEnv('My SonarQube Server') {
                    // // Optionally use a Maven environment you've configured already
                    // withMaven(maven:'Maven 3.5') {
                    //     sh 'mvn clean package sonar:sonar'
                    // }
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
        // stage("Quality Gate") {
        //     steps {
        //         timeout(time: 1, unit: 'HOURS') {
        //             // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
        //             // true = set pipeline to UNSTABLE, false = don't
        //             waitForQualityGate abortPipeline: true
        //         }
        //     }
        // }
    }
}