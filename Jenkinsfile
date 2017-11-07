#!groovy

stage 'Dev Build'
node {  
    try{
       checkout scm
      sbt 'clean compile package'
    }catch(Exception e){
        //emailext subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} "+"Build Failed", to: "aaa.email.com",body: "..."
    }
}

stage 'Sonar Analysis'
node {  
    def scannerHome = tool 'sonarqubescanner';
    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=spark -Dsonar.sources=src/main/scala -Dsonar.host.url=http://52.91.254.81:9000/sonar"
}

stage 'Artifact Upload'


def sbt(args) {
    def sbtHome = tool 'sbt'
    def SBT = "${sbtHome}/bin/sbt -Dsbt.log.noformat=true"
}

