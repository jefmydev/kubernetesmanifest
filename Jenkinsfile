node {
    def app

    stage('Clone repository') {
        checkout scm
    }
    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
//                         sh "cd kubernetesmanifest"
//                         set +e
//                         sh "ls"
                        sh "git config user.email jefmydev@gmail.com"
                        sh "git config user.name jefmydev"
//                         sh "git status"
//                         sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -e 'jefriekussuma/myflask-app:${DOCKERTAG}' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
      }
                    returnStatus: true
    }
  }
}
}
