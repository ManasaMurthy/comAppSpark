#!groovy

stage 'Dev Build'
node {  
    try{
      sbt 'clean'
    }catch(Exception e){
        //emailext subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} "+"Build Failed", to: "aaa.email.com",body: "..."
    }
}

node {
  
  stage('SonarQube analysis') {
    // requires SonarQube Scanner 2.8+
    def scannerHome = tool 'SonarQube Scanner 2.6.1';
    withSonarQubeEnv('My SonarQube Server') {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}

def sbt(args) {
    def sbtHome = tool 'default-sbt'
    def SBT = "${sbtHome}/bin/sbt -Dsbt.log.noformat=true"
}

