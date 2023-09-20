pipeline {
    
    agent any

        environment {
        CATALINA_HOME = "D:\\jenkins_agent\\Tomcat-9.0.75"
        JAVA_HOME = "D:\\Tools\\jdk1.8.0_332"
        JRE_HOME = "D:\\Tools\\jdk1.8.0_332\\jre"
        Ant_Home = "D:\\Tools\\Ant"
    }
 
stages{

        stage('Removing tmp dir'){
            steps {
                bat 'if exist "D:\\jenkins_agent\\Tomcat-9.0.75\\work" rmdir /s /q "D:\\jenkins_agent\\Tomcat-9.0.75\\work"' // /s to delete recursively and /q to suppress any prompt of warning 
                bat 'if exist "D:\\jenkins_agent\\Tomcat-9.0.75\\temp" rmdir /s /q "D:\\jenkins_agent\\Tomcat-9.0.75\\temp"' 
                //bat 'if exist "D:\\Tools\\jenkins-agent\\workspace\\autoupdate\\build.xml" del /q "D:\\Tools\\jenkins-agent\\workspace\\autoupdate\\build.xml"' 
                //bat 'xcopy /Y D:\\Tools\\MasterScriptJobFiles\\build.xml D:\\Tools\\jenkins-agent\\workspace\\autoupdate'  // /Y overwrite the file if already exists
            }
        }

    }

    post {
        success {
            emailext to: 'taimoor.ahmed@globalnorthstar.com, ali.muhammad@globalnorthstar.com, hammad.ali@globalnorthstar.com, syed.sauman@globalnorthstar.com, mohammad.ali@globalnorthstar.com', from: 'taimoor.ahmed@globalnorthstar.com',
                subject: "Build Success at 192.168.7.199| Deployment for ${env.JOB_NAME}",
                body: "Job has been successfully completed - \"${env.JOB_NAME}\" build: ${env.BUILD_NUMBER}\n\nView the log at:\n ${env.BUILD_URL}"
        }
        failure {
            emailext to: 'taimoor.ahmed@globalnorthstar.com, ali.muhammad@globalnorthstar.com, hammad.ali@globalnorthstar.com, syed.sauman@globalnorthstar.com, mohammad.ali@globalnorthstar.com', from: 'taimoor.ahmed@globalnorthstar.com',
                subject: "Build Failure at 192.168.7.199 | Deployment for ${env.JOB_NAME}",
                body: "Job has failed, please check logs - \"${env.JOB_NAME}\" build: ${env.BUILD_NUMBER}\n\nView the log at:\n ${env.BUILD_URL}"
        }
    }
}
