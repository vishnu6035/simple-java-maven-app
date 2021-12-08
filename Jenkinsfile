pipeline{
    agent{label 'openjdk-11-maven3.8.4'}
    triggers{
        cron('45 23 * * 1-5')
        pollSCM('*/5 * * * *')
    }
    parameters{
        string(name: 'MAVEN-GOAL', defaultvalue: 'package', description: 'this is maven goal')
        choice(name: 'BRANCH-TO-BUILD', choices: ['master','declarative'], description: 'slect the branch' )
    }
    }
    stages{
        stage('Source'){
            steps{
                git url: 'https://github.com/vishnu6035/simple-java-maven-app.git', branch: "${params.BRANCH-TO-BUILD}"
            }
        }
        stage('Build'){
            steps{
                sh "/usr/local/apache-maven-3.8.4/bin/mvn ${params.MAVEN-GOAL}"
            }
        }
    }
}