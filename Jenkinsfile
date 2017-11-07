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
  
    def scannerHome = tool 'SonarQube Scanner 2.6.1';
withEnv(["PATH=/usr/bin: ..."]) {
  withSonarQubeEnv('My SonarQube Server') {
    sh "${scannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://52.91.254.81:9000/sonar"
  }
}
}

def sbt(args) {
    def sbtHome = tool 'default-sbt'
    def SBT = "${sbtHome}/bin/sbt -Dsbt.log.noformat=true"
}

