node('openjdk-11-maven3.8.4'){
    stage('Source'){
        git 'https://github.com/vishnu6035/simple-java-maven-app.git'
    }
    stage("Build"){
        sh 'mvn clean package'
    }
}