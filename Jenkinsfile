def registry = 'https://spidy03.jfrog.io'
def imageName = 'spidy03.jfrog.io/spidy-docker/ttrend'
def version   = '2.1.3'

pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.7/bin:$PATH"	// we have setup mvn in path variable, so calling full path.
}
        stages{
        stage("build"){
            steps {
                 echo "----------- build started ----------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                 echo "----------- build complted ----------"
            }
        }
        stage("test"){
            steps{
                echo "----------- unit test started ----------"
                sh 'mvn surefire-report:report'
                 echo "----------- unit test Complted ----------"
            }
        }
        stage("trivy scan"){
            steps{
                sh "trivy image uday1011/app-myname:latest "
            }
        }
    }

}
