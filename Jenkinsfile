pipeline{
    agent{label'jdk-11-mvn'}
    parameters{
        choice(name: 'BRANCH_TO_BUILD', choices: ['master','declarative_varma','scripted'], description: 'select the branch' )
        choice(name: 'MAVEN_GOAL', choices: ['clean','compile','test','clean package'], description: 'select the maven goal to perform' )
    }
    stages{
        stage('source'){
            steps{
                    git branch: "${params.BRANCH_TO_BUILD}", url: 'https://github.com/vishnu6035/simple-java-maven-app.git'
            }
        }
        stage('build'){
            steps{
                sh "mvn ${params.MAVEN_GOAL}"
            }
        }
        stage('archive'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}