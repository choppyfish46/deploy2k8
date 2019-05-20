node {

    def gitRepo = 'http://repositoryurl.git'
    def DOCKER_IMAGE_NAME

    stage('Clone repository') {
        try {
            checkout scm
        } catch (e) {
            notify("Something failed while trying to clone the repository")
            throw e;
        } 
    }

    

    stage('Kubernetes Setup'){
        try{
            sh("kubectl create -f app-deployment.yml -v=8")
        } catch(e) {
            notify("Something failed Kubernetes Setup")
            throw e;
        }
    }

    notify("Process finish")
}

def notify(String message) {
  slackSend (color: '#FFFF00', message: "${message}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
}
