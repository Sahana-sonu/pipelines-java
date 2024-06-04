pipeline {
    agent {
    node {
      label 'agent_dev1'
    }
  }

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the project...'
                    sh 'mvn clean package' // Example Maven build command
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                    sh 'mvn test' // Example Maven test command
                }
            }
        }

        stage('Install') {
            steps{
                script {
                    echo 'Installing JAR to local Maven repository...'
                    sh 'mvn install' // Example Maven install command for dev branch
                }
            }
        }      
    }
}
