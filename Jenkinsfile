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
    sh "${scannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://52.91.254.81:9000/sonar -Dsonar.projectKey=elevate -Dsonar.projectName=spark -Dsonar.projectVersion=1.0 -Dsonar.sources=src/main/scala"
}

def sbt(args) {
    def sbtHome = tool 'default-sbt'
    def SBT = "${sbtHome}/bin/sbt -Dsbt.log.noformat=true"
}

