node('jdk-11-mvn'){
    stage('Source'){
       git branch: 'scripted', url: 'https://github.com/vishnu6035/simple-java-maven-app.git'
    }
    stage("Build"){
        sh 'mvn clean package'
    }
    stage('archive'){
        archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
    }
}