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
    sh "${scannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://52.91.254.81:9000/sonar -sonar.projectKey=elevate -sonar.projectName=spark-sonar.projectVersion=1.0 -sonar.sources=src/main/scala"
}

def sbt(args) {
    def sbtHome = tool 'default-sbt'
    def SBT = "${sbtHome}/bin/sbt -Dsbt.log.noformat=true"
}

