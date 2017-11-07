#!groovy

stage 'Dev Build'
node {  
    try{
      sbt 'clean'
    }catch(Exception e){
        //emailext subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} "+"Build Failed", to: "aaa.email.com",body: "..."
    }
}

stage 'Static Code Analysis - Sonar'
node {
    try{
        def sonarqubeScannerHome = tool name: 'SonarQubeScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
        sh "${sonarqubeScannerHome}/bin/sonar-scanner -e -Dsonar.host.url=http://52.91.254.81:9000/sonar:9000 -Dsonar.projectName=spark -Dsonar.projectVersion=1.0 -Dsonar.projectKey=scala -Dsonar.sources=.src/main/scala"
      
    }catch(Exception e){
        //emailext subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} "+"Sonar Analysis Failed.", to: "Mukunthan.Govindaraj@aexp.com",body: "..."
        exit
    }
   
}

def sbt(args) {
    def sbtHome = tool 'default-sbt'
    def SBT = "${sbtHome}/bin/sbt -Dsbt.log.noformat=true"
}

