pipeline{
    agent any

    stages{
        stage("verification"){
            steps
            {
            sh 'helm version'
            }
        }
        stage("helm deploy"){
            steps{
                sh 'helm upgrade --install springapp $WORKSPACE --namespace springapp --values $WORKSPACE/values-dev.yaml'
            }
        }

    }
    post {
        always{
            emailext body: '''Hi,

     The jenkins has been failed . please check it.

     Thanks
     Devops Team''', subject: 'testing jenkins pipeline: $JOB_URL', to: 'malleshdevops2021@outlook.com'
        }
    }
}

