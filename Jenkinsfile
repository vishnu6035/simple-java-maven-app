pipeline{
    agent{label 'openjdk-11-maven3.8.4'}
    stages{
        stage('Source'){
            steps{
                git 'https://github.com/vishnu6035/simple-java-maven-app.git'
            }
        }
        stage('Build'){
            steps{
                sh '/usr/local/apache-maven-3.8.4/bin/mvn clean package'
            }
        }
    }
}