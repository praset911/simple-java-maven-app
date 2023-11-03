node{
    checkout scm
    docker.image('maven:3.9.0').inside {
        stage('Build'){
            sh 'mvn -B -DskipTests clean package'
        }
        stage('Test'){
            sh 'mvn test'
            junit 'target/surefire-reports/*.xml'
        }
        stage('Manual Approve'){
            input message: 'Lanjutkan ke tahap deploy? (Klik "Proceed" untuk mendeploy)' 
        }
        stage('Deploy'){
            sh './jenkins/scripts/deliver.sh'
            sleep time:60
        }
    } 
}