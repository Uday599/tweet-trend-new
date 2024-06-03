pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.7/bin:$PATH"  // we have setup mvn in path variable, so calling full path.
}
    stages {
        stage("Checkout"){
            steps{
                git branch: 'main', url: 'https://github.com/Uday599/tweet-trend-new.git'
            }       // use this syntax only to clone git
        }
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
    }
}
