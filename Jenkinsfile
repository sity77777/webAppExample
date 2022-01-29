pipeline{
    agent any
     tools {
        maven 'Maven' 
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
               
            }
        }
        stage("Build"){
            steps{
                // mvn package
                sh "mvn package"
                
            }
        }
        stage("deploy to test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcat0details', path: '', url: 'http://13.232.192.101:8080')], contextPath: '/app', war: '**/*.war'
                
            }
        }
        stage("deploy to prod"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'asdfasd', path: '', url: 'http://3.108.237.183:8080')], contextPath: '/app', war: '**/*.war'
                
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
