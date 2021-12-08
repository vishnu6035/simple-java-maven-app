pipeline{
    agent (label 'openjdk-11-maven3.8.4')
    stages{
        stage('git'){
            steps{
                git url: 'https://github.com/vishnu6035/simple-java-maven-app.git', branch: 'declarative'
            }
        }    
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
        }    
    }
}