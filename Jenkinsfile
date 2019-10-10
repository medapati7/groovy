pipeline {
    agent any
    stages {
     stage('SCM Checkout') {
         steps {
         echo "Checking out from the source Repository"
         git url: 'https://github.com/medapati7/jenkinsautomation'
     }
     }
     stage('Compile stage') {
         steps {
         echo "compiling the source"
         withMaven(maven: 'maven_new') {
            sh 'mvn compile'
}
     }
     }
     stage('Test stage') {
         steps {
         echo "Testing the source"
         withMaven(maven: 'maven_new') {
            sh 'mvn test'
}
     }
     }
     stage('Package stage') {
         steps {
         echo "Package the source"
         withMaven(maven: 'maven_new') {
            sh 'mvn package'
}
     }
     }
     stage('Deploy stage') {
         steps {
         echo "Deploy the source"
         deploy adapters: [tomcat8(credentialsId: '85b8a3ef-3d61-4e49-ba1d-098318711b08', path: '', url: 'http://13.126.41.117:9090')], contextPath: 'mvn-hello-world', war: 'target/*.war'
     }
     }
    }
}

