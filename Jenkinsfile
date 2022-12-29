node{
    stage('Clone') {
    git 'https://github.com/priximmo/jenkins-helloworld/'
    }
    stage('Build') {
    sh 'javac Main.java'
    }
    stage('Run') {
    sh 'java Main'
    }
}
