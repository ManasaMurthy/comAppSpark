#!groovy

stage 'Dev Build'
node {  
    try{
      sbt 'clean'
    }catch(Exception e){
        //emailext subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} "+"Build Failed", to: "aaa.email.com",body: "..."
    }
}

stage 'sonar'
node {  
    def scannerHome = tool 'sonarqubescanner';
    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=spark -Dsonar.sources=src/main/scala -Dsonar.host.url=http://52.91.254.81:9000/sonar"
}

def sbt(args) {
    def sbtHome = tool 'sbt'
    def SBT = "${sbtHome}/bin/sbt -Dsbt.log.noformat=true"
}

