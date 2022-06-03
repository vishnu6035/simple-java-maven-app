pipeline{
    agent{label'jdk-11-mvn'}
    parameters{
        choice(name: 'BRANCH_TO_BUILD', choices: ['master','declarative_varma','scripted'], description: 'select the branch' )
        choice(name: 'MAVEN_GOAL', choices: ['clean','compile','test','clean package'], description: 'select the maven goal to perform' )
    }
    stages{
        stage('source'){
            steps{
                mail from:"devops_test@jenkins.com",
                 to:"qt@jenkins.com",
                 subject:"Cloning of the code  ${env.JOB_NAME} started",
                 body: "${env.BUILD_URL}"

                    git branch: "${params.BRANCH_TO_BUILD}", url: 'https://github.com/vishnu6035/simple-java-maven-app.git'
            }
        }
        stage('build'){
            steps{
                mail from:"devops_test@jenkins.com",
                 to:"qt@jenkins.com",
                 subject:"building of the code  ${env.JOB_NAME} started",
                 body: "${env.BUILD_URL}"

                sh "mvn ${params.MAVEN_GOAL}"
            }
        }
        stage('archive'){
            steps{
                mail from:"devops_test@jenkins.com",
                 to:"qt@jenkins.com",
                 subject:"archiving the artifacts  ${env.JOB_NAME} started",
                 body: "${env.BUILD_URL}"

                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
    post{
        always{
             emailext attachLog: true,
                body: """<p> Executed: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER}\'
                </b></p><p>View console outpe at "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}
                </a>"</p> <p><i>Build log is attached </i> </p>""",
                compressLog: true,
                replyTo: "do-not-reply@jenkins.com",
                to: "qtdevops@gmail.com",
                subject: "${env.JOB_NAME} - Build ${env.BUILD_NUMBER} -Status ${currentBuild.result}"
        }
    }
}