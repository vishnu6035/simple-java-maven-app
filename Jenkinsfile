pipeline{
    agent{label'jdk11-mvn'}
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
                withSonarQubeEnv('sonar_jdk11_mvn') {
                    sh "mvn ${params.MAVEN_GOAL}"
                    sh "mvn sonar:sonar -Dsonar.login=b587bc27e05e3ea3b6c64357f3008b697d7f7b0d"
                }
                

            }
        }
        stage('archive'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}