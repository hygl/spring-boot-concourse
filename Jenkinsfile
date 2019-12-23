def label = "worker-${UUID.randomUUID().toString()}"

podTemplate(label: label, containers: [
  containerTemplate(name: 'maven', image: 'maven:3.6-jdk-8', command: 'cat', ttyEnabled: true),
  ],
volumes: [
  hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock')
]) {
  node(label) {
    def myRepo = checkout scm
    def gitCommit = myRepo.GIT_COMMIT
    def gitBranch = myRepo.GIT_BRANCH
    def shortGitCommit = "${gitCommit[0..10]}"
    def previousGitCommit = sh(script: "git rev-parse ${gitCommit}~", returnStdout: true)


    stage('Build') {
      container('maven') {
        sh "mvn clean package -DskipTests=true"
        sh "mvn test"
        archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
      }
    }
  }

}