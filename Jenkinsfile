pipeline {
    agent {
        node 'maven-slave'
    }

environment{
    PATH = "/opt/apache-maven-3.9.4/bin:$PATH"
}
    stages {
        stage("echo"){
            steps {
                echo 'Hello World' 
            }
        }
        stage("Build"){
            steps {
                sh 'mvn clean deploy'
            }
        }
    }
}