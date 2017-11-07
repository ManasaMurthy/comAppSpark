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

stage 'sonar'
node {  
    def scannerHome = tool 'sonarqubescanner';
    sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=spark -Dsonar.sources=src/main/scala -Dsonar.host.url=http://52.91.254.81:9000/sonar"
}

stage 'Artifact Upload'

node
    s3Upload(file:'comappspark_2.11-0.1.jar', bucket:'testelevate', path:'target/scala-2.11/comappspark_2.11-0.1.jar')
}

def sbt(args) {
    def sbtHome = tool 'sbt'
    def SBT = "${sbtHome}/bin/sbt -Dsbt.log.noformat=true"
}

