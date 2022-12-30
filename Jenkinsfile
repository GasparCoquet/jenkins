node {
    def registryProjet='registry.gitlab.com/p5512/jenkins2'
    def IMAGE="${registryProjet}:version-${env.BUILD_ID}"
    stage('Clone') {
          git 'https://github.com/priximmo/jbuild.git'
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
    }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID -p 80:80") { c ->
            sh 'curl localhost'
          }
    }

    stage('Push') {
          docker.withRegistry('https://registry.gitlab.com', 'reg5') {
              img.push 'latest'
              img.push()
          }
    }


}

