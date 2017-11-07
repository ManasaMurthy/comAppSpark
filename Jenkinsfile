#!groovy

stage 'Dev Build'
node {
    try{
       sbt 'clean compile test package'
    }catch(Exception e){
        //emailext subject: "${env.JOB_NAME} - Build # ${env.BUILD_NUMBER} "+"Build Failed", to: "aaa.email.com",body: "..."
    }
}

