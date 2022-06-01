pipeline{
    agent('jdk-11-mvn')
    stages{
        stage('source'){
            steps{
                    git branch: 'declarative_varma', url: 'https://github.com/vishnu6035/simple-java-maven-app.git'
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage('archive'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}