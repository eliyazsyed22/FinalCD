node {
    def app

    stage('Git Checkout') {
      

        checkout scm
    }

    stage('Update GITHUB') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                   
   
                    withCredentials([gitUsernamePassword(credentialsId: 'classictoken', gitToolName: 'Default')]) {
                        
                        sh "git config user.email eliyazsyed22@gmail.com"
                        sh "git config user.name eliyazsyed22"
                        sh "cat eks-deployment.yaml"
                        sh "sed -i 's+public.ecr.aws/p5u5p5h0/buchananecr.*+public.ecr.aws/p5u5p5h0/buchananecr:${DOCKERTAG}+g' eks-deployment.yaml"
                        sh "cat eks-deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job update manifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://github.com/eliyazsyed22/FinalCD.git HEAD:main"
                        
                        
                    }
                }
            }
        }
}
