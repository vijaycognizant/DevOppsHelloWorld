pipeline {
    agent any
    
    tools {
        jdk 'jdk11'
        maven 'maven3'
    }
    environment {
        CATALINA_HOME='C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0'
    }

    stages {
        // stage('Git Checkout') {
        //     steps {
        //         git branch: 'main', credentialsId: '98e2ce7d-24b8-41fa-9440-6a8f37ced8b1', url: 'https://github.com/sojutta/DevOpsCaseStudyJavaMaven'
        //     }
        // }
        stage('Build WAR') {
            steps {
                bat "mvn clean package -DskipTests"
            }
        }
        stage('Test') {
            steps {
                bat "mvn test"
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                script {
                    bat 'copy "target\\*.war" "%CATALINA_HOME%\\webapps\\"'
                    //bat 'call "%CATALINA_HOME%\\bin\\shutdown.bat"'
                    //sleep(time: 20, unit: 'SECONDS')
                    //bat 'call "%CATALINA_HOME%\\bin\\startup.bat"'
                    //sleep(time: 20, unit: 'SECONDS')
                    //bat "net stop Tomcat9"
                    //bat "net start Tomcat9"
                }
                
            }
        }
        stage('Restart Tomcat') {
            steps {
                script {
                    bat "net stop Tomcat9"
                    bat "net start Tomcat9"
                }
                
            }
        }
    }
}
